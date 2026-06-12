---
title: "Can't VPN outside (PPTP)"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by marko-manchev on 2014-08-12
Hey there, 
as this is my first post, first of all I would like to just say hello to anybody and everybody out there!

Furthermore, please excuse my lack of knowledge when it comes to topics, so if this is not the right one, please move it!

My issue is as follows (I'll try to explain it as good as I can):

I have three providers in the same subnet, so three gateways, one of which is an optical PPPoE connection with a Huawei router/modem which is DMZ-d with an Ubuntu server acting as a gateway and openVPN server.

For the life of me, I cannot understand why nobody cannot connect to our other office via the Ubuntu gateway/Huawei optics. The other two provider have LinkSys routers with dd-wrt attached to them, and when my windows clients change their gateway to one of them, the connection works fine. The protocol used is PPTP.

I've tried forwarding ports 47 (GRE) and 1723 (PPTP) on the Huawei router to no avail (perhaps i don't understand how to do that so deeply), and the Ubuntu gateway has no IPtables configured whatsoever.

Wiresharking my way through, it seems that i get PPP LCF configuration requests, that don't get replies.

Again, this only happens via the Huawei router which has an Ubuntu gateway attached.

Any help/guide to possible solution would be greatly appreciated!

---

