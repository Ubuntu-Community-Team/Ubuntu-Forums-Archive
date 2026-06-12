---
title: "bridging via wlan"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by bbruecker on 2008-05-07
Hi!

I'm changing my network from WXP to Ubuntu 8.04. Ubuntu works properly on all machines.

This is my situation:
**WS2 [eth0] <--1GBit-Switch--> [eth0] WS1 [ath0] <--54 Mbit WLAN (WPA)--> Router (Dhcp, DNS, Gateway)**
[Look here for a detailed description.]("http://transfer.benjaminbruecker.de/public/Netzwerk.png")

I want to bridge WS2 via WS1 to WLAN and internet. 
First step is to establish the Bridge at WS1. (WLAN works fine until I connect the WS1 to 1Gbit-Switch.)

**First issue**
I decided first to bridge eth0 to br0. 
[Look here for configuration for the interface-file.](http://ubuntuusers.de/paste/212434).
I can start the network by typing this:** /etc/init.d/networking restart**. [The result looks fine to me.](http://ubuntuusers.de/paste/212446). I've got an IP-Address for br0 from my Router.
But if I restart the computer (WS1), the network is down.
I thought until today /etc/init.d/networking restart is doing the same like Ubuntu does at startup. Is my assumption wrong? How can I check my network settings properly without rebooting the computer every time?

**Second issue**
My Second step is to join eth0 to the bridge on WS1.
So I simply added this line: 
**iface eth0 inet dhcp**
and added eth0 to 
**bridge_ports ath0 eth0**
[You can look here for the complete interface-file.](http://ubuntuusers.de/paste/212443)
This attempt fails. The wlan adapter is physically linked to the wlan, but in that case ath0 and br0 get no DHCP offers.

I think the wlan adapter on WS1 is able to bridge, because it has an atheros chipset, and I've found that atheros works fine in most cases, and I was able to bridge a VMware-Box via bridge (not NAT) to wlan.

Thanks for your patience reading this. After searching for hours I found no solution.

Benjamin

---

### Post by bluefrog on 2008-05-07
wouldn't IP masquerading and IP forwarding (on WS1) and a fixed IP on WS2 do the trick for you more easily?
(have a look at [http://ubuntuforums.org/showthread.php?t=782936]("http://ubuntuforums.org/showthread.php?t=782936")

---

### Post by bbruecker on 2008-05-07
Hi bluefog,

thank you for your replay. It seesm's to me as difficult as the bridge approach. The situation is not exactly the same as described, because I think the DHCP-server is connected to the physical lan.

I'm now thinking about an other approach: routing.

But I still hope that someone can tell me whats  wrong with my bridge approve above.

Thx, Benjamin

---

