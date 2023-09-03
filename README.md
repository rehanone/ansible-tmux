ansible-tmux
=========

An ansible role for managing the installation of `tmux` terminal multiplexer.

It also installs a tmux configuration profile `ohmytmux` that can be found at:

  - [https://github.com/gpakosz/.tmux](https://github.com/gpakosz/.tmux)

To use this configuation, you need to list each user account that should be provisioned for it.

Requirements
------------

This role requires `tmux`  package to be avalible in package manager on the target system.

Example Playbook
----------------

### 1. All Options

This example shows all possible options and their default values.

```yaml
- hosts: all
  roles:
    - role: rehanone.tmux
      vars:
        tmux:
          debug: true
          package:
            name: tmux
            state: present
            manage: true
          profile:
            repository: 'https://github.com/gpakosz/.tmux.git'
            revision: master
            home: '/opt/ohmytmux'
            state: present
            manage: true
          users:
          - name: ray
            state: present
            manage: true
```

### 2. Minimum Required Options

This example shows all minimum required options for using this role.

```yaml
- hosts: all
  roles:
    - role: rehanone.tmux
      vars:
        tmux:
          users:
          - name: ray
```

License
-------

Apache-2.0
