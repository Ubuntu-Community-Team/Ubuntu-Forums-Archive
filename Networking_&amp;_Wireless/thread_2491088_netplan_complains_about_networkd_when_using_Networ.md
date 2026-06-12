---
title: "netplan complains about networkd when using NetworkManager"
date: 2023-09-25
forum: Networking &amp; Wireless
---

### Post by lnxgnome on 2023-09-25
VERSION="22.04.3 LTS (Jammy Jellyfish)"
Server install.

systemd-networkd did not have good support for InfiniBand interfaces, so it was replaced by NetworkManager.

/etc/netplan/*.yaml files were updated with new renderer.

systemd-networkd.service and systemd-networkd.socket were disabled.
networkd-dispatcher package was removed from the system.

NetworkManager was enabled and started.

Running netplan apply still generates warnings about systemd-networkd even though there is no reference in the netplan configurations.

root:~# ll /etc/netplan/
-rw-r--r--   1 root root  348 Sep 26 02:08 01-eno1.yaml
-rw-r--r--   1 root root  299 Sep 26 02:09 02-eno2.yaml
-rw-r--r--   1 root root  136 Sep 26 02:10 03-eno3.yaml
-rw-r--r--   1 root root  140 Sep 26 02:10 04-eno4.yaml
-rw-r--r--   1 root root  279 Sep 26 02:11 10-enp66s0f0.yaml
-rw-r--r--   1 root root  145 Sep 26 02:11 11-enp66s0f1.yaml
-rw-r--r--   1 root root  266 Sep 26 02:12 30-ibp68s0.yaml
-rw-r--r--   1 root root  268 Sep 26 02:12 31-ibp68s0d1.yaml
-rw-r--r--   1 root root  413 Sep 26 02:13 40-ibbond0.yaml

root:~# grep render /etc/netplan/*
/etc/netplan/01-eno1.yaml:  renderer: NetworkManager
/etc/netplan/02-eno2.yaml:  renderer: NetworkManager
/etc/netplan/03-eno3.yaml:  renderer: NetworkManager
/etc/netplan/04-eno4.yaml:  renderer: NetworkManager
/etc/netplan/10-enp66s0f0.yaml:  renderer: NetworkManager
/etc/netplan/11-enp66s0f1.yaml:  renderer: NetworkManager
/etc/netplan/30-ibp68s0.yaml:  renderer: NetworkManager
/etc/netplan/31-ibp68s0d1.yaml:  renderer: NetworkManager
/etc/netplan/40-ibbond0.yaml:  renderer: NetworkManager

A little more investigation shows that networkd is included with the systemd package, so it can't really be removed completely.

root:~# netplan apply
Failed to reload network settings: No such file or directory
Falling back to a hard restart of systemd-networkd.service

Why is it trying to start systemd-networkd ?

---

