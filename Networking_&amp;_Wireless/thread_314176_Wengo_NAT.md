---
title: "Wengo NAT"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by kvonb on 2006-12-07
I'm trying to get WengoPhone working on my Edgy system through my server which connects to the net.

Wengo works on my server (Dapper with Firestarter), but I can't get it to work on the internal network.

I've tried both the Linux and Windows versions, they can connect, but no voice or video.

I think it has something to do with NAT and I've tried forwarding all the ports to my machine but still nothing.

Any ideas?

Regards, Kev :)

---

### Post by kvonb on 2006-12-07
SOLVED:

I forwarded port 5602 (using Firestarter) to my machine (192.168.0.2) then in WengoPhone changed the SIP port to 5602 (Tools->Configuration->Advanced->Advanced configuration window:item #44 network.sip.server).

This worked on version 2.0-8523 as well as the standard v.99 from the add/remove progs in the Ubuntu menus (although the item # is 39 I think).

---

