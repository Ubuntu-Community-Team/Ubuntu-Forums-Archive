---
title: "Ubuntu 16.04: Wifi slower after latest Intel networking update"
date: 2018-01-15
forum: Networking &amp; Wireless
---

### Post by Alex_Filonov on 2018-01-15
Before last update, I had connection speed 433 Mbit/sec. After update, it's 72.2. For comparison, my Pixel phone shows 833, my Windows 7 laptop from work: 720.

System76 Galago, Ubuntu 16.04 LTS, with lates updates. Network controller:

03:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83). 

Kernel 4.4.0-109-generic

---

### Post by Alex_Filonov on 2018-01-17
OK, today's update solved the problem. No idea how, Intel drivers were not updated. Probably something else in networking.

---

