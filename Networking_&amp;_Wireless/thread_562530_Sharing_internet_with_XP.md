---
title: "Sharing internet with XP"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by torsoboy on 2007-09-28
hi all. 

i'm trying to get Ubuntu and XP to share the same cable modem through a netgear fs6503 switch.

the internet on XP is working fine but i get an ip address conflict when i connect the ubuntu machine. 

this is what xp says

Physical Address: 00-40-2B-22-55-88
IP Address: 68.53.49.19
Subnet Mask: 255.255.252.0
Default Gateway: 68.53.48.1
DHCP Server: 68.87.68.10
Lease Obtained: 9/28/2007 9:00:02 PM
Lease Expires: 10/2/2007 7:42:06 PM
DNS Servers: 68.87.68.162, 68.87.74.162

help!

---

### Post by helgman on 2007-09-29
And what does **ifconfig** on the Ubuntu machine say?

Regards,
Helgman

---

### Post by noob12 on 2007-09-29
It looks to me like you are getting a single public IP from your modem, so what you need is probably more than a switch.  You need a home router, which will provide a private NAT-ed subnet that you can plug multiple boxes into.   Linksys, D-Link, and Netgear all have popular products in this space.

If you have a spare internet interface on your Ubuntu box, you can set it up to serve as a NAT-ing router for an internal net using firestarter or iptables.

Personal opinion: if you can spring for it, the home router is probably going to be your easiest solution and most of these boxes also have wireless support so that will give you a lot of flexibility to add more clients and wireless ones as well.

---

