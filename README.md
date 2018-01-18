# ocp_create_tenancy

## Description:

This role adds a tenancy (group of related projects) to an OCP cluster.

## Behaviour:

**Feature:** Create OCP tenancy

As a PaaS Operator
I want to create an OCP tenancy
so that developers can work on a set of related projects

- **Scenario:** A customer requests a tenancy
- **Given:** there is a valid service account token
- **Given:** there is a tenancy name
- **Given:** there is a list of projects to create
- **When:** the role is executed
- **Then:** the requested projects are created
- **Then:** the projects are labelled as belonging to the tenancy
 
## Configuration:

A list of the external variables used by the role.

| Variable  | Description  | Example  | Default |
|---|---|---|---|
| **tenancy**  | The name of the new tenancy |  mytenancy | (none) |
| **projects**  | List of inital projects | proj1,proj2,proj3  |  dev,test,prod |
| **ocp_token**  | Token for a serviceaccount with permission to create projects | (none)  |
| **ocp_uri**  | URI for the cluster API | https://localhost:8443/  |

## Testing and Usage:

The role can be tested using a simple playbook as follows:

```
---

- hosts: masters[0]
  name: Testing ocp_create_tenancy
  roles:
    - ocp_create_tenancy
  vars:
    - tenancy: mytenancy
    - ocp_token: eyJhbGciOiJSU...
    - projects:
      - project1
      - project2
      - project3
```
