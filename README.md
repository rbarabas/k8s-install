# k8s-install
Ansible scripts to install and perform the initial setup of a Kubernetes environment.

# Setup
## Hosts
The initial setup assumes that you are using a lab with the following hosts:
- master1
- worker1
- worker2
- worker3

This can be easily customized by changing the hosts file that is attached to this repository or adjusting your ansible.cfg to point at the proper mechanism for host management.

## Topology
It is assumed that the install will provision a single master node with several worker nodes. The number of worker nodes is arbitrary but in the current setup the hosts file is set to use three workers.

## Supported OS
The scripts have been developed on Ubuntu Server 20.04 and it should work with most Debian derivatives.

## Access
Note that most of the playbooks assume an administrative user role (become_user: root) to perform installation. You will need to ensure that this is possible in your setup.

# Playbooks
## Check install prerequisities such as the presence of enough memory and swap disabled:
`$ ansible-playbook plays/check.yml`

## Ad-hoc playbook to disable swap in both /etc/fstab and active swap configuration:
`$ ansible-playbook plays/disable-swap.yml`

## Installation of K8s using Docker as the container runtime:
`$ ansible-playbook plays/install.yml`

## Initial setup of the K8s cluster using Calico as the CNI:
`$ ansible-playbook plays/setup.yml`

