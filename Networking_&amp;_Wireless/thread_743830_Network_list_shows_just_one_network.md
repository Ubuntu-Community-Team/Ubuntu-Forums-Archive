---
title: "Network list shows just one network"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by F35Blackbird on 2008-04-03
Hello,

On my ubuntu 7.10, I used to see all my surrounding networks in the Networksetting - but not any more. I now only see the network that I provide the information manually.

Can someone help me, so I can start seeing all my surrounding available networks?

My interfaces file look like this:
>>>>>>>>>>>>>>>>>>>>>>>
auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-key 8XX4FBXXXX
wireless-essid NETGEAR

auto eth1

iface eth0 inet dhcp

auto eth0
<<<<<<<<<<<<<<<<<<<<<<<

Thanks!

---

