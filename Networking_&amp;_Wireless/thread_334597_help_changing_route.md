---
title: "help changing route"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by muu on 2007-01-09
Hello,

I need help changing a routing entry.

When I issue the route command, one of the entries is:
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
This is incorrect, as these addresses should be handled by the "default" entry
(not shown here, but correct).

When I issue:
sudo route del 192.168.0.0
I get the following error:
SIOCDELRT: No such process

](*,)
TIA!

---

### Post by fstab on 2007-01-11
This should work:

sudo route del -net 192.168.0.0 netmask 255.255.255.0 dev eth0

---

