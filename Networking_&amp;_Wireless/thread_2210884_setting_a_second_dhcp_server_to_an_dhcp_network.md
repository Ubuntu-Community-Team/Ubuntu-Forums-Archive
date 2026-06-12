---
title: "setting a second dhcp server to an dhcp network"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by noobb2 on 2014-03-13
I have an dhcp network that gives me an(automatic)  ip addr  192.168.1.101  with 255.255.255.0(through a router).

So eth0=>inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0

And i want to test this new server with a dhcp through eth1 interface.

Is this possibile?

i've tried so many ip combinations in /etc/dhcp/dhcpd.conf but the eth1 only shows me only the inet6 addr.

---

