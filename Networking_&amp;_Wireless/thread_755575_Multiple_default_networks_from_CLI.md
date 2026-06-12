---
title: "Multiple default networks from CLI"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by max.goedjen on 2008-04-15
Hey guys,
I've got a Ubuntu laptop with just a wireless card, and I want it to be able to connect to one of two default networks(whichever one's available).
Should I just set up /etc/network/interfaces to be this:

auto eth0
iface eth0 inet dhcp
wireless-essid NetworkName1
wireless-key NetworkKey1
wireless-essid NetworkName2
wireless-key NetworkKey2

Or is there some other way I'm supposed to do this?

---

