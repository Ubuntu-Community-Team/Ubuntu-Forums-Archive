---
title: "Bridging Network"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by mosestruong on 2008-05-21
I'm trying to setup a virtual bridge network for use with Virtualbox.

I've created a bridge by adding
```
auto br0
iface br0 inet dhcp
	bridge_ports eth0
```

And then added the virtual interface by using
```
VBoxAddIF vbox0 username br0
```

However, when I go into my Windows guest, it couldn't get the IP address from DHCP. And if I set it to static IP, it cannot ping the host.

I looked at ifconfig, and br0 has an IP address associated with it, but eth0 and vbox0 doesn't.

Does anyone know what I can do to resolve this? Thanks.

---

### Post by bluefrog on 2008-05-22
virtualbox help gives another solution for the virtual network interfaces on debian/ubuntu (6.7.1.1. Debian and Ubuntu hosts).

anyway here is a working configuration.

I assume you are bridging an ethernet card, if not refer to [http://ubuntuforums.org/showthread.php?t=782936&highlight=virtualbox+wifi](http://ubuntuforums.org/showthread.php?t=782936&highlight=virtualbox+wifi)

/etc/network/interfaces
auto lo
iface lo inet loopback

auto tap0
iface tap0 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user your-user

auto br0
#iface br0 inet dhcp
iface br0 inet static
address 192.168.1.60
netmask 255.255.255.0
#gateway 192.168.1.60
    bridge_ports eth0 tap0
    bridge_maxwait 0

auto eth0
iface eth0 inet manual

---

### Post by Peter09 on 2008-05-22
If you still have a problem post the output of 

```
ifconfig
```

here.

PC

---

### Post by Paris Heng on 2008-05-22
It is possible to use routing instead of bridging?

---

