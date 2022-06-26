# otshosting-unprovisioning

This is an Ansible playbook used to uninstall or rollback all the changes made from running the [DevelopersPL/otshosting-provisioning repo](https://github.com/DevelopersPL/otshosting-provisioning) or [saulmendoza/otshosting-provisioning repo](https://gitlab.com/saulmendoza/otshosting-provisioning)

Basically it will uninstall `mysql` and `nginx` packages (and services). Also it will delete the system user `otsmanager` and its directory `/home/otsmanager`.

## Quick Start

```bash
#!/bin/bash -ex
apt-get update
apt install -y -q git-core ansible

# Run from remote file
ansible-pull -i localhost, -U https://gitlab.com/saulmendoza/otshosting-uninstall.git -d /srv/otshosting-uninstall --purge -t default

# Run from local file
git clone https://gitlab.com/saulmendoza/otshosting-uninstall.git
cd otshosting-uninstall
ansible-playbook -c local -i localhost, -t default local.yml
```

## Available tags

* systemd - enables persistent journald logging (default)
* general - software & integration (default)
* mysql - MariaDB SQL server (default)
* php-fpm - PHP support for website (default)
* nginx - web server (default)
* pma - phpMyAdmin for easy administration (default)
* tfs - TFS 1.X automatically compiled and installed (default)
* tfs-old - packages ONLY to compile older versions
* wine - wine packages to run exe (engines compiled for Windows)
