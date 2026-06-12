---
title: "Exotic Router and Circonvoluted Forwarding, 3G &amp; ports &amp; p2p"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Peacepunk on 2008-09-23
Hi People

This one has me stumbled, and I'm afraid its a dirty one:

**Situation**: Small office, Cambodia, Phnom Penh. 3G (HSDPA) router *T-Mobile "web'n'walkBox"* (from Germany) as internet access point for a classic WRT linksys 4 port+wifi router. 2 desktops lan-connected, 1 to 3 laptops wlan-connected. For testing purposes, two firewalls went down, from 1 wifi laptop and one workstation, and the 3G router firewall was down too. All port forwarding was done on the Linksys router (you can't kill the firewall on these)

1. All Lan/Wlan-wise OK, ping, ssh -X, vnc/vncviewer in-(w)lan OK; 
2. Internet access from each machine OK, dns set to opendns.org since 3G provider [www.qbmore.com](www.qbmore.com) quite sluggish.
3. Port forwarding is done for 22 shh and 18967 which is a random port for p2p 

**Issues**: My IP seems to be "rotating" very fast, if I try to check with canyouseeme.org it returns a different IP each time, I suspect this prevents me from properly checking my ports and probably give me more issues. All computers here have the same issue. Whatever I do, gnutella complains being in behind bars and aMule can't connect at all at nothing.


**Objectives**:
1) connect from outside to the office; this has never worked. I should be able to take my "public" address and log to my workstation here, be it as ssh (open for testing) or sftp (closed as of now until I find my way trough this).

2) run p2p softwares, obviousy. I live quite far away you now. 

**Note**: This exotic 3G router is a real router, with WiFi access; I have obviously tried with all firewalls down, straight connected to this access point without the Linksys that I need as access point for all machines here. Gnutella still pukes.

Port forward on the 3G modem is as follow, but if the firewall is down this is surely of no use, isn't it?
> 
1 	GNU1 	tcp 	18967 	192.168.1.99 	18967
2 	GNU1 	udp 	18967 	192.168.1.99 	18967


??

---

