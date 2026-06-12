---
title: "Install Internet box (club-internet box) with Breezy"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by danschlomo on 2006-10-29
Hello
I am absolute beginner with Breezy and I have a good practice with Windows, not with Network and Web.
I have to help a friend who has Breezy. She wants to connect to WEB and has bougth an club-internet box. The hot-line said "it works with our box, but you have to set it up manually".
They gave me 2 DNS (primary & secondary).

I don't know how to begein.
Can somebody help me?

Technical matters :

AMD 64 
Link with Ethernet (no problem about WIFI). When I ping the box, I get an answer from the club-internet box.

---

### Post by mips on 2006-10-29
Can you post a link to this club-internet-box & ISP ?

You should be able to use DHCP.

Alternatively edit the /etc/resolv.conf file as route and add to lines that read:
nameserver *Pri_DNS Ip address here*
nameserver *Sec_DNS Ip address here*

---

