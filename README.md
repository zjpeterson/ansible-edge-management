# Ansible Edge Management

In this repository are examples of using Ansible to manage RHEL for Edge (rpm-ostree), and on those systems, containerized workloads running in Podman.

## Playbooks

* **playbook_os_build.yml** Creates an rpm-ostree commit using osbuild-composer. Takes a variable `blueprint` corresponding to a variable file located under `blueprints/`. In the variable file there are inputs for the [infra.osbuild](https://github.com/redhat-cop/infra.osbuild) [builder role](https://github.com/redhat-cop/infra.osbuild/tree/main/roles/builder). See `blueprints/ansible_edge.yml` for an example. The kickstart generated by the example is able to self-register with Controller.
* **playbook_os_upgrade.yml** Stages a new rpm-ostree commit while using some guardrails, and reboots to apply.
* **playbook_workload.yml** Pushes a containerized workload to be run under Podman. Takes a variable `workload` corresponding to a variable file located under `workloads/`. See `workloads/hello-app.yml` for an example. Heavily based on [something Josh Swanson wrote](https://github.com/jjaswanson4/example-device-edge-resources/blob/main/playbooks/deploy-workload.yml).

## Other
* An Ansible Execution Environment manifest for `edge-ee` which contains everyhing I use when doing edge automation
* The containerized application I use with `playbook_workload.yml` (nothing fancy, just nginx serving a webpage)
