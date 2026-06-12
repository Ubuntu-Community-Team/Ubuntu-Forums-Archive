---
title: "DirecTV GenieGo through Ubuntu 10.04 Firewall"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by dc-spyder on 2014-02-16
I have a DirecTV GenieGO device which is supposed to give me access to my DVR's recorded programs from out and about on the internet using their GenieGO application for PC/Mac/Android/iOS.  

To get this service to work, I apparently have to open up ports 8082 and 8083 on my router/firewall.

My system is a PC with 2 NICs (eth0 for the internal LAN and eth1 for the external WAN) running Ubuntu 10.04 LTS.  I am using IPTables firewall.  Incidentally, I don't know if it makes a difference, but I also have Squid/DansGuardian running on the box as a content filter for the kids.  All services have been working (transparent proxy, browsing internet, content filtering).

I have assigned the GenieGO device a fixed IP address of 192.168.2.220 on eth0.  From within my 192.168.2.X network, it works great.  Finds the GenieGO device which connects to my DVR and displays its contents.

From the outside, however, no go.

I assumed that all I would have to do is add 2 firewall rules to the FORWARD chain that ACCEPTS packets with protocol TCP and destination port 8082 and 8083.

That didn't seem to work, so I added 2 more rules to the INPUT chain, but that also didn't change anything.

So I thought I'd "disable" the firewall by adding "ACCEPT" rules with no conditions at the top of the INPUT, FORWARD, and OUTPUT chains.  Still didn't seem to get the device to work from outside the LAN.  What else should I be looking at that might be interfering with connections to the device from the WAN?  (And does adding these 3 ACCEPT rules in-fact essentially disable the firewall?)

---

