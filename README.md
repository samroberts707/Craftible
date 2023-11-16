
# Craftible

## A CraftCMS project boilerplate

This is a CraftCMS project boilerplate, designed to guide people from the start of a project all the way to production deployment. Local dev will take place with Ansible/Vagrant box. Frontend files will be compiled using SCSS via NPM. Finally Ansible will be used to deploy the project to both staging and production environments.

  

## Usage

### DDEV

DDEV will be used in Local dev as a provider for PHP and MySQL.  
  

### Ansible
Ansble is used to provision and do initial deployment for Staging and Production environments. A server such a boddy.works will be used for CI/CD so this is designed to only be run on a fresh server. Current OS target is Ubuntu 22.04

**Todo before:**
- Update hosts files with either correct IP addresses or domain names
- Git URL

Once all the above items have been updated you can deploy to either Staging or Production with the following commands:

**Playbooks**
There are two different playbooks, there is some work to do between running the two playbooks which is why they need to be run separately.

    provision.yml
    
This playbook can be run straight away on a fresh server it will install as much as possible before needing external work.

    deploy.yml
    
This playbook needs to be run after the provision playbook, items like the root user public ssh key needs to be added to the Bitbucket access keys before we can bring in the repo and install the project. 

Staging:

    ansible-playbook provision.yml -i hosts/staging

Production:

    ansible-playbook provision.yml -i hosts/production
