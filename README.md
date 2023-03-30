# ansible-keepalived: Ansible role for setting up keepalived

## Dependencies

Works with centos/redhat and Debian/Ubuntu

## Example Playbooks

Simple VRRP example playbook:

```yaml
- hosts: keepalived
  roles:
    - role: brandonlamb.ansible_keepalived
      global_defs:
        notification_email:
          - email1@example.com
          - email2@example.com
        notification_email_from: 'keepalived@example.com'
      vrrp_instances:
        - name: 'VI_01'
          state: 'MASTER'
          interface: 'eth0'
          virtual_router_id: 10
          priority: 100
          smtp_alert: True
          authentication:
            auth_type: 'PASS'
            auth_pass: 'secpass'
          virtual_ipaddress:
            - '192.168.200.17/24 dev eth1'
            - '192.168.200.18/24 dev eth2 label eth2:1'
```
