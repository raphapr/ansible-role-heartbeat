# Ansible Role: Heartbeat
Simple ansible role to Install and configure [Heartbeat](https://www.elastic.co/beats/heartbeat) on Linux.

## Requirements
- [Ansible >= 2.8](https://ansible.com/)
- Debian or Red Hat based system 

## Role Variables

Please look at the [defaults/main.yml](defaults/main.yml) to see all default variables.

For a simple installation and configuration, there is no mandatory variable.

## Example Playbook

```yml
---
- name: heartbeat node
  hosts: all
  vars:
    heartbeat_config_output_elasticsearch_hosts: ["https://elasticsearch.example:9243"]
    heartbeat_config_output_elasticsearch_protocol: https
    heartbeat_config_output_elasticsearch_username: elastic
    heartbeat_config_output_elasticsearch_password: xxx

    heartbeat_monitors:
      - type: http
        name: google
        timeout: 5s
        schedule: '@every 10s'
        urls:
          - "https://www.google.com"

  roles:
    - role: ansible-role-heartbeat
      tags: heartbeat
```

## Author Information
Raphael P. Ribeiro
