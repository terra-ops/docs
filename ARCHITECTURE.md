Terra Ops Architecture
======================

Terra Ops is a "Platform Framework", meaning it is a framework for building your own platform or Platform-as-a-service.

Terra Ops is inspired by open source platforms such as Aegir, Kubernetes, Ansible Tower, as well as proprietary hosting services like Heroku, Pantheon.io and Acquia Cloud.

Terra Ops is not defined by any one specific tool, but refers to a group of tools and policies that work together to make creating and managing your own "cloud platform" easy.

This architecture document is a work in progress.

## `terra` user

- A linux user with no extra permissions on the master machine.
- Git, ansible, php-cli, composer & Terra CLI are all that is required.
- Connects to all other machines as root or a sudo user in order to provision machines.
- Only the most trusted super-system administrators should be able to login as this user.  Use SSH Key password-less authentication, or create users for your admins that can "sudo su" to the terra user.
- All `ansible` and `ansible-playbook` commands are run from this user.

## Terra Playbooks

- Users:
  - On machine verify, we must be able to create system users, give them SSH access, and sometimes, remove users.
- Machine Roles
  - Terra Ansible Roles 

## Terra Web UI

- Stores list of machines, users, roles, and apps.
- REST API provides an "Ansible Dynamic Inventory".
- Inventory provides list of machines, ansible roles, and the variables needed to provision your PaaS.

## Terra CLI

- Simplifies running playbooks and commands using Ansible, using the Terra Dynamic Inventory.

## Terra Jobs

- Scripts that reflect all needed workflow for machines, users, apps, etc.
- Jobs are analogous to Aegir Tasks: A CLI command to run, arguments, logging, timestamps, and user tracking.

## Terra Job Runner

- A Jenkins instance, pre-configured to be able to run all pertinant jobs for running a PaaS.
