---
title: "Wireless no startup"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by Ubimad on 2007-06-25
my wireless does not startup with the gnome desktop, lan does it, have to do a /etc/init.d/network start to bring it up. Any Idea?
thanks Tobias

cat /etc/network/interfaces:

auto lo

iface lo inet loopback


iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp
wireless-essid xxxxxxx
wireless-channel 10
wireless-key xxxxxxx
wireless-key1   xxxxxxx
wireless-key2   xxxxxxx
wireless-key3   xxxxxxx
wireless-key4   xxxxxxx

---

