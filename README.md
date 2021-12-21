ansible-role-nfs_server
====

Install and configure NFS server.

Requirements
------------

* RHEL8+

Role Variables
--------------

* `nfs_server_packages` - list of nfs packages to install.
* `nfs_server_conf_path` - path to nfs.conf.
* `nfs_server_conf` - list of options to set in nfs.conf, example:

```yaml
nfs_server_conf:
  - section: mountd
    option: port
    value: 20048
```

* `nfs_server_daemon` - name of nfs server daemon.
* `nfs_server_exports` - list of entries for /etc/exports, example:

```yaml
nfs_server_exports:
  - /mnt/movies 192.168.1.2 192.168.1.3
  - /mnt/upload 192.168.1.0/24(rw)
```

* `nfs_server_exportfs_opts` - options for `exportfs` command.
* `nfs_server_enable` - boolean to enable and start nfs server daemon on boot.

Dependencies
------------

Firewall and SELinux are handled separately.

Example Playbook
----------------

```
- hosts: my_servers
  vars:
    nfs_server_exports:
      - /mnt/movies 192.168.1.2 192.168.1.3
      - /mnt/upload 192.168.1.0/24(rw)
  roles:
    - ansible-role-nfs_server
```

License
-------

GPLv3

Author Information
------------------

Vladimir Vasilev (@vladi-k)
