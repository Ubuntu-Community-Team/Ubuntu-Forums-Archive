---
title: "Problems with Belkin USB wireless wifi-adaptor."
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by N'Jal on 2008-11-06
I have an issue with my wireless under Ubuntu, it appears it only remains connected for so long before disconnecting, it appears to remain connected so long as I am active at the PC, but this presents issues if I try to remotely access my PC from another location or if I leave something downloading over night.

lsusb provided this information:
Bus 005 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter

this is the relevent part of /etc/network/interfaces

iface wlan0 inet dhcp
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.254
wireless-key <hidden>
wireless-essid O2wireless7E641B

auto wlan0

If there is any further information I could provide let me know, I am eager to fix this issue.

---

### Post by chkneater on 2008-11-06
Cant really help you out except to say I had the exact same issue with the same adaptor.  The only way to fix it was to unplug, close all browsers, and plug it back in.  If that didn't work, I'd have to unplug, reboot, the plug it back in.  Those are the only solutions I've found so it won't really help you remotely.

---

