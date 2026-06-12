---
title: "Ubuntu router"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by lucy_U on 2014-03-12
Hiya all,

I would like to set up a test system for playing around with tc. My setup looks like this.

Machine A <==Ethernet eth1 ==> ( Ubuntu box I would like to use tc on) <===== Ethernet eth0 =====>Machine B

Machine A has IP 10.0.8.2 Netmask 255.255.255.0
Machine B has IP 10.0.8.1 Netmask 255.255.255.0

Ubuntu box I configured as follows:

ifconfig eth0 10.0.8.5 netmask 255.255.255.0
ifconfig eth1 10.0.8.4 netmask 255.255.255.0

I also set ipv4 forwarding on in /etc/sysctl.conf so that cat /proc/sys/net/ipv4/ip_foward is showing 1. 
I am able to ping Machine B from the Ubuntu box and get a reply.
I am not able to ping Machine A from the Ubuntu box and get a reply.

route -n on the Ubuntu Box shows:

10.0.8.0  0.0.0.0
10.0.8.0  0.0.0.0

I would like to be able to connect Machine A to Machine B and use tc on the in between Ubuntu box.

Any suggestions on next steps? Thank you.

---

### Post by untrustytahr on 2014-03-13
> **lucy_U said:**
> 

Any suggestions on next steps? Thank you.

Learn subbnetting.  What it is and why to use it.
Learn routers.  What they are; when and why to use one.
Learn routing and how to read routing tables.

Respectfully, I understand this is a test network for learning and that's great.  I know I've learned more by tinkering/breaking and fixing things than by  “doing it right”, but tc is an advanced topic.  If you do not understand the above topics, you probably are not ready to tinker with it yet.

Hints for your example: 
1) All of your computers are in the same subnet.
2) Your routing table says: “if I receive a packet for the 10.0.8.0/24 network, send it to the default route”

---

