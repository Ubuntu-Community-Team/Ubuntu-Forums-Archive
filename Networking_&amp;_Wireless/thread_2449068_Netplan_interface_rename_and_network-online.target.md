---
title: "Netplan interface rename and network-online.target"
date: 2020-08-19
forum: Networking &amp; Wireless
---

### Post by listener1379 on 2020-08-19
Renaming my ethernet interface via netplan set-name causes NFS to launch prematurely:

```
$ systemctl list-dependencies nfs.mount 
nfs.mount
&#9679; &#9500;&#9472;-.mount
&#9679; &#9500;&#9472;system.slice
&#9679; &#9492;&#9472;network-online.target
&#9679;   &#9492;&#9472;systemd-networkd-wait-online.service
```

netplan yaml:
```
network:
  version: 2
  renderer: networkd
  #  renderer: NetworkManager
  ethernets:
    eth0:
      match:
        macaddress: xx:xx:xx:xx:xx:xx
      set-name: eth0
      dhcp4: yes
      dhcp6: no
      accept-ra: no
      link-local: [ ]
    eth1:
      match:
        macaddress: xx:xx:xx:xx:xx:xy
      set-name: eth1
      dhcp4: no
      dhcp6: no
      accept-ra: no
      link-local: [ ]
      optional: yes
      addresses:
        - xx.xx.xx.xx/xx
```

set-name: eth0 present:
```
$ journalctl -b | grep -E 'nfs|networkd'
Aug 19 11:14:59 HOSTNAME systemd-networkd[453]: Enumeration completed
Aug 19 11:14:59 HOSTNAME systemd-networkd[453]: eno1: Interface name change detected, eno1 has been renamed to eth0.
Aug 19 11:14:59 HOSTNAME systemd-networkd[453]: eth0: Link UP
Aug 19 11:14:59 HOSTNAME systemd-networkd[453]: enp2s0: Interface name change detected, enp2s0 has been renamed to eth1.
Aug 19 11:14:59 HOSTNAME systemd[1]: nfs-config.service: Succeeded.
Aug 19 11:14:59 HOSTNAME systemd-networkd[453]: eth1: Link UP
Aug 19 11:14:59 HOSTNAME systemd[1]: Starting Dispatcher daemon for systemd-networkd...
Aug 19 11:15:00 HOSTNAME systemd[1]: nfs.mount: Directory /nfs to mount over is not empty, mounting anyway.
Aug 19 11:15:00 HOSTNAME systemd[1]: Mounting /nfs...
Aug 19 11:15:00 HOSTNAME systemd[1]: Started Dispatcher daemon for systemd-networkd.
Aug 19 11:15:00 HOSTNAME systemd[1]: nfs-config.service: Succeeded.
Aug 19 11:15:00 HOSTNAME mount[712]: mount.nfs: Network is unreachable
Aug 19 11:15:00 HOSTNAME systemd[1]: nfs.mount: Mount process exited, code=exited, status=32/n/a
Aug 19 11:15:00 HOSTNAME systemd[1]: nfs.mount: Failed with result 'exit-code'.
Aug 19 11:15:00 HOSTNAME systemd[1]: Failed to mount /nfs.
Aug 19 11:15:00 HOSTNAME systemd-networkd[453]: eth0: Gained carrier
Aug 19 11:15:00 HOSTNAME systemd-networkd[453]: eth0: DHCPv4 address xx.xx.xx.xx/xx via xx.xx.xx.xx
```

set-name: eth0 removed:
```
$ journalctl -b | grep -E 'nfs|networkd'
Aug 19 11:25:39 HOSTNAME systemd-networkd[457]: Enumeration completed
Aug 19 11:25:39 HOSTNAME systemd-networkd[457]: eno1: Link UP
Aug 19 11:25:39 HOSTNAME systemd-networkd[457]: enp2s0: Interface name change detected, enp2s0 has been renamed to eth1.
Aug 19 11:25:39 HOSTNAME systemd-networkd[457]: eth1: Link UP
Aug 19 11:25:39 HOSTNAME systemd[1]: nfs-config.service: Succeeded.
Aug 19 11:25:40 HOSTNAME systemd[1]: Starting Dispatcher daemon for systemd-networkd...
Aug 19 11:25:40 HOSTNAME systemd[1]: Started Dispatcher daemon for systemd-networkd.
Aug 19 11:25:40 HOSTNAME systemd-networkd[457]: eno1: Gained carrier
Aug 19 11:25:40 HOSTNAME systemd-networkd[457]: eno1: DHCPv4 address xx.xx.xx.xx/xx via xx.xx.xx.xx
Aug 19 11:25:40 HOSTNAME systemd-networkd-wait-online[458]: managing: eno1
Aug 19 11:25:40 HOSTNAME systemd[1]: nfs.mount: Directory /nfs to mount over is not empty, mounting anyway.
Aug 19 11:25:40 HOSTNAME systemd[1]: Mounting /nfs...
Aug 19 11:25:40 HOSTNAME systemd[1]: nfs-config.service: Succeeded.
Aug 19 11:25:41 HOSTNAME kernel: FS-Cache: Netfs 'nfs' registered for caching
Aug 19 11:25:41 HOSTNAME systemd[1]: Mounted /nfs.
```

Ubuntu 20.04.1 LTS

---

### Post by listener1379 on 2020-08-19
Additionally, the ethernet carrier can be flaky (switch/cable?) and NFS doesn't seem to respond robustly. Any ideas to make this work every boot? (set-name: removed)

```
Aug 19 11:00:55 HOSTNAME systemd-networkd[453]: Enumeration completed
Aug 19 11:00:55 HOSTNAME systemd-networkd[453]: eno1: Link UP
Aug 19 11:00:55 HOSTNAME systemd-networkd[453]: enp2s0: Interface name change detected, enp2s0 has been renamed to eth1.
Aug 19 11:00:55 HOSTNAME systemd-networkd[453]: eth1: Link UP
Aug 19 11:00:55 HOSTNAME systemd[1]: nfs-config.service: Succeeded.
Aug 19 11:00:55 HOSTNAME systemd[1]: Starting Dispatcher daemon for systemd-networkd...
Aug 19 11:00:56 HOSTNAME systemd[1]: Started Dispatcher daemon for systemd-networkd.
Aug 19 11:00:56 HOSTNAME systemd-networkd[453]: eno1: Gained carrier
Aug 19 11:00:56 HOSTNAME systemd-networkd[453]: eno1: DHCPv4 address xx.xx.xx.xx/xx via xx.xx.xx.xx
Aug 19 11:00:56 HOSTNAME systemd-networkd-wait-online[455]: managing: eno1
Aug 19 11:00:56 HOSTNAME systemd[1]: nfs.mount: Directory /nfs to mount over is not empty, mounting anyway.
Aug 19 11:00:56 HOSTNAME systemd[1]: Mounting /nfs...
Aug 19 11:00:57 HOSTNAME systemd[1]: nfs-config.service: Succeeded.
Aug 19 11:00:57 HOSTNAME systemd-networkd[453]: eno1: Lost carrier
Aug 19 11:00:57 HOSTNAME systemd-networkd[453]: eno1: DHCP lease lost
Aug 19 11:01:07 HOSTNAME mount[812]: mount.nfs: Network is unreachable
Aug 19 11:01:07 HOSTNAME systemd[1]: nfs.mount: Mount process exited, code=exited, status=32/n/a
Aug 19 11:01:07 HOSTNAME systemd[1]: nfs.mount: Failed with result 'exit-code'.
Aug 19 11:01:07 HOSTNAME systemd[1]: Failed to mount /nfs.
Aug 19 11:01:09 HOSTNAME systemd-networkd[453]: eno1: Gained carrier
Aug 19 11:01:12 HOSTNAME systemd-networkd[453]: eno1: DHCPv4 address xx.xx.xx.xx/xx via xx.xx.xx.xx
```

This only happens sometimes during startup, and I think it has also affected a CentOS previously connected to the same switchport.

---

### Post by listener1379 on 2020-08-19
I am trying out autofs for NFS to work around both problems. It seems to be working so far. (There are other services that want network-online.target, but they are robust enough to function having started before network is online.)

---

