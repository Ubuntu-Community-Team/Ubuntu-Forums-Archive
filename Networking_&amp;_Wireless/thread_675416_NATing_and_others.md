---
title: "NATing and others"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by GLMnet on 2008-01-22
Hi, I have installed XUbuntu on a tiny box, a celeron 400 with 196 mb ram. I run several services there.
My network is setup with a Cisco 677 ADSL Modem a Linksis wrt54g v8 Router (which is very limited device), that linux box and my main Vista OS.
What I am trying to do here is to turn off the Linksis and use Ubuntu to do what it is doing.
I know/understand several things related this stuff, PPPoE, QoS, Nat, Port Forwarding, UDP/TCP, etc (I am a developer), but I know nothing on linux.
I been looking around IPTables but I dont wanna go that low, I just want it to work.
I was wondering what are the posibilities here? Which tool can I use to setup my linux like if it were a web based router (I already have webadmin but did not make many research) or set iup like if it were a win os (ie dialog boxes)
I want software to do advanced things like QoS, traffic monitoring, etc.
Another thing I am trying to avoid here is to install another NIC card, I have just one installed, what I have read for now tells me that Ill need to add another NIC, but I can do this with win: PPPoE and LAN on the same interface. It is unavoidable to have two nic cards?

---

### Post by ew16301 on 2008-01-22
At minimum you are going to need two NIC cards and/or a wireless card if you want to perform any type of routing functions. I not sure how exactly to setup ubuntu to function like a router, but monowall is a good FreeBSD based OS that can allow you two do many of the things you are talking about. It can be found here [http://m0n0.ch/wall/](http://m0n0.ch/wall/)

---

