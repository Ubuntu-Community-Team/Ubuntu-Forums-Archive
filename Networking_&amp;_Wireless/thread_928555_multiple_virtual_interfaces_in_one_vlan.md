---
title: "multiple virtual interfaces in one vlan"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Mcihi on 2008-09-24
hi,

i have a machine with only one physical network interface.

i know that it is possible to create virtual interfaces (eth0:1, etc.) to have multiple ip-adresses on one physical interface.

now i would need to configure vlans on this machine - no problem so far, this is my config:

```
auto vlan1012
auto vlan1001

iface vlan1012 inet dhcp
mtu 1500
vlan_raw_device eth1

iface vlan1001 inet dhcp
mtu 1500
vlan_raw_device eth1
```

that works too, i get the interfaces vlan1012 and vlan1001 and ip adresses in the corresponding subnets.

but i cant create virtual interfaces for those vlan interfaces - the problem is i would need about 10 interfaces in one vlan.

does anyone know how to do this?

---

