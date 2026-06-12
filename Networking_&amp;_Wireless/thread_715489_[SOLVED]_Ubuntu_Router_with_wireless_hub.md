---
title: "[SOLVED] Ubuntu Router with wireless hub"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by Dirk_McJerk on 2008-03-04
Hello all,

I am having quite a weird problem and I can not seem to figure it out. I have a home computer network consisting of 3 XP clients and 1 Gutsy client connecting to a Linksys WRT54G wireless router. All connections are wireless except for 1 XP computer which conects directly (wired) into the router. This had been my setup for quite some time and there were no problems. All the computers were able to access each other, and most importantly access the printer which is connected to the wired XP client. 

I recently came across an extra Pentium 4 computer and decided I wanted to make a router PC. I installed a regular version of Gutsy on the computer, set the cable modem into one network card, the other card is static IP going into a regular port on the linksys. I set up dhcp and port forwarding on the server (followed this tutorial: [http://ubuntuforums.org/showthread.php?t=713874&highlight=ubuntu+router](http://ubuntuforums.org/showthread.php?t=713874&highlight=ubuntu+router)). I then turned off DHCP on the linksys router. All appeared to be working. My Ubuntu router is giving out IP addresses to all computers on the network thus giving each computer access to the internet. However the computers can not ping each other. In fact, the Ubuntu router can not ping XP clients for which it gives IP addresses to.

Essentially::
[LIST]
[*]All XP clients can ping the Ubuntu router
[*]All XP clients can ping the linksys hub
[*]All XP clients can ping the ubuntu client
[*]No XP clients can ping other XP clients
[*]Ubuntu router can ping linksys, ubuntu client, but can not ping any XP clients
[*]Ubuntu client can not ping XP clients
[/LIST]

I do not understand why the xp computers can ping the server, but the server can not ping the clients. I can not figure out if it is something to do with my linksys or something to do with network configurations. I made sure all the computers are on MSHOME workgroup.

Access to all computers is required for file sharing, and most importantly the printer. 

Any help would be greatly appreciated.

Thank you.

---

### Post by Dirk_McJerk on 2008-03-05
Turns out the problem was firewall related. The users of the XP machines had set up a firewall, and upon changing the network topology the firewall was rejecting it.

---

