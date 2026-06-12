---
title: "Netplan not adding default route"
date: 2019-01-15
forum: Networking &amp; Wireless
---

### Post by s0ftcorn on 2019-01-15
[FONT=Ubuntu]This is my netplan config:
```
network:
version: 2
renderer: networkd
ethernets:
ens3:
  dhcp4: no
  addresses: [10.0.0.7/24,129.217.211.194/27]
  gateway4: 129.211.217.222
  nameservers:
          addresses: [129.211.129.42,8.8.8.8]

```this is the output of route:
```
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 ens3
129.217.211.192 0.0.0.0         255.255.255.224 U     0      0        0 ens3

```which, as you can see, does not include a default route. Has anyone a idea how this comes?
Im using ubuntu server 18.04.1 in a KVM virtual machine.

[/FONT]

---

