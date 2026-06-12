---
title: "What Updates /etc/network/interfaces and When?"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2008-03-16
I am interested in obtaining a rough, not precise, understanding of which entities update /etc/network/interfaces, and when.

I am trying to track down why my intefaces file contained some comments followed by

auto lo
iface lo inet loopback

and was then followed by an eth0 interface. 

I cannot tell if this was written when Ubuntu 7.10 was first installed or after I tried to get a USB wireless device working. The problem is, right after installation, my laptop's built-in wireless device was not configured. I then tried a USB wireless device, but that would not work either. When I edited intefaces back to 

auto lo 
iface lo inet loopback

the internal wireless card worked fine.

---

