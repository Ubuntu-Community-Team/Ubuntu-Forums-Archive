---
title: "i need to have a Static ip address set on my ubuntu server"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by aten on 2007-04-03
well i have a no gui 
on my ubuntu server and i need to set a static ip address.
How do i do this?
thanks

---

### Post by evilghost on 2007-04-03
Modify the file /etc/network/interfaces

Change the device from DHCP to static, using the below template, change to suit your needs.

```

auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.254

```

Then, bring the interface down and up using "ifdown [interface] && ifup [interface]".

---

