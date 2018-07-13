# Ansible Cloud: Firewall Rule role

An Ansible role for managing firewall rules on the Cloud in an agnostic cloud provider way.

This role is part of the [ansible-cloud](https://github.com/redhat-cip/ansible-cloud) broader effort.

## Pre-requisites

Please refer to [ansible-cloud](https://github.com/redhat-cip/ansible-cloud) [README.md](https://github.com/redhat-cip/ansible-cloud/blob/master/README.md) to see how to configure your system the proper way for the provide you wish to use.


## Role Variables

| Variable name                  | Required  | Default | Type   | Description                  |
|--------------------------------|-----------|---------|--------|------------------------------|
| cloud_firewallrule_group_name  | True      | N/A     | String | Name of the security group   |
| cloud_firewallrule_protocol    | True      | N/A     | String | Protocol to use for the rule |
| cloud_firewallrule_start_port  | True      | N/A     | int    | Starting port range          |
| cloud_firewallrule_end_port    | True      | N/A     | int    | Ending port range            |
| cloud_firewallrule_remote_cidr | True      | N/A     | String | Remote CIDR range            |
| cloud_firewallrule_state       | False     | present | String | Should the rule be present   |


## Example

```
---
- hosts: localhost
  vars:
    ansible_cloud_provider: vultr
  tasks:
    - name: Create firewall rule
      include_role:
        name: cloud-firewallrule
      vars:
        cloud_firewallrule_group_name: ansiblecloud-testsecuritygroup
        cloud_firewallrule_protocol: tcp
        cloud_firewallrule_start_port: 80
        cloud_firewallrule_end_port: 81
        cloud_firewallrule_remote_cidr: 0.0.0.0/0
```


## License

Apache 2.0


## Authors Information

  - Ricardo Carrillo Cruz <ricarril@redhat.com>
  - Yanis Guenane <yguenane@redhat.com>
