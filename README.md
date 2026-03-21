Ansible Role for Java
=====================

Installs OpenJDK or Amazon Corretto on RHEL-based Linux systems.

Requirements
------------

- Ansible 2.10 or higher
- RHEL 8/9/10, Amazon Linux 2, or Amazon Linux 2023

Role Variables
--------------

| Variable | Default | Description |
|---|---|---|
| `java_versions` | `["1.8.0"]` | List of Java versions to install |
| `java_default_version` | `"1.8.0"` | Version to set as system default via alternatives |
| `java_provider` | `openjdk` | Java provider (`openjdk` or `amazon-corretto`) |
| `java_install_jre` | `True` | Install JRE packages |
| `java_install_devel` | `False` | Install JDK devel packages |
| `java_set_default_version` | `False` | Set default Java version via alternatives |

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: ansible-role-java
      java_versions:
        - "17"
      java_default_version: "17"
      java_set_default_version: True
```

Install only devel packages (e.g., Amazon Corretto 1.8.0 on EL10):

```yaml
- hosts: servers
  roles:
    - role: ansible-role-java
      java_provider: amazon-corretto
      java_versions:
        - "1.8.0"
      java_install_jre: False
      java_install_devel: True
```

License
-------

Proprietary
