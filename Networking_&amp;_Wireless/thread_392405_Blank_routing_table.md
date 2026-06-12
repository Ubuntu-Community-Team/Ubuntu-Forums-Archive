---
title: "Blank routing table"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by jd47 on 2007-03-24
Hi,

I've installed xubuntu on my laptop and I'm using a ZD1211 chipset wireless card to connect to my local router. It works intermittently by using the command:

ifup eth0 --force

As I said this doesn't always work. 

From reading other posts my card can "see" the router by using the command:

iwlist scanning

This works all the time.

I can ping localhost and get replies all the time, if I ping the router 192.168.0.1 i receive the message:

connect: Network is unreachable.

When I can't connect to the router my kernel routing table is blank not sure if this is the way it should be.

Anyone have any idea's?

Thanks for your help,
Jon

---

