---
title: "Fast Ethernet 10/100 PC Card"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by Brru on 2006-09-07
Ok so I have a linksys Fast Ethernet 10/100 PC Card for my network and that s how I access my DSL modem. Unfortunately I looked it up and it is not supported by Ubuntu. This is extremely unfortunate considering I realy like Ubuntu.

So I guess to the point: Anyone know of any 3rd party drivers or any way at all of getting this to work.



Info:
Linksys Fast Ethernet 10/100 PC Card
Chpset/Driver: Axis AX88190
Auto Detected: yes
Works: No
Other: PCI connected, Works with Windows XP of course.

---

### Post by spd106 on 2006-09-08
A quick search turned up this page [http://lkml.org/lkml/2001/12/1/136](http://lkml.org/lkml/2001/12/1/136).

Does **lsmod** show that the axnet_cs.o module is loaded?

---

