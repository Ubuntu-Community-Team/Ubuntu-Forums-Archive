---
title: "Problem changing to a static IP..."
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by XtremeGamer99 on 2008-02-16
This is for a Debian server. It's currently set to DHCP, which is assigned by my router (which is also my gateway, a Linksys Wireless Router). Eveytime I change it to static, it doesn't seem to work externally. Here's my /etc/network/interfaces:

```
  GNU nano 2.0.7         File: /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
    # Router's IP
gateway 192.168.1.1

# auto eth0

```

How can I set this server up to work externally with a static IP address? Thanks!

---

### Post by kagashe on 2008-02-17
I think the line "allow-hotplug eth0" is creating some problem. You can read on this [thread]("http://www.debianhelp.org/node/1715") on debianhelp.

kagashe

---

