---
title: "What is the equivalent of &quot;inet manual&quot; in NetPlan?"
date: 2022-10-25
forum: Networking &amp; Wireless
---

### Post by sevilla.larry2 on 2022-10-25
I'm studying OpenStack.  The reference guide was using Ubuntu 16.04 LTS.  It was successful.

Now I'm trying to use Ubuntu 22.04 LTS, but networking changed to NetPlan.

OpenStack documentation is not updated to use NetPlan.
[https://docs.openstack.org/install-guide/environment-networking-controller.html](https://docs.openstack.org/install-guide/environment-networking-controller.html)


In the reference guide:

/etc/network/interfaces
```
auto eth0
iface eth0 inet static
  address 10.0.0.11
  netmask 255.255.255.0
  dns-nameservers 8.8.8.8
auto eth1
iface eth1 inet manual
  up ip link set dev eth1 up
  down ip link set dev eth1 down
auto eth2
iface eth2 inet dhcp
```


The eth0 (inet static) and eth2 (inet dhcp) have documented equivalents in NetPlan.

Q: What is the equivalent of the ff (inet manual) in NetPlan?
```
auto eth1
iface eth1 inet manual
  up ip link set dev eth1 up
  down ip link set dev eth1 down
```

---

### Post by TheFu on 2022-10-25
Just disable dhcp4 and dhcp6.

Probably need to get better training materials if they are using something 2 yrs out of support.  20.04 would be the bare minimum today.  Enterprise software should be just starting to show up for the current LTS, 22.04, but sometimes that takes a year.

---

### Post by sevilla.larry2 on 2022-10-25
Is this what you mean in the .yaml file?

```
network:
  ethernets:
    ...
    eth1:
      dhcp4: false
      dhcp6: false
    ...
version: 2
```

Pls correct if I'm wrong.

---

