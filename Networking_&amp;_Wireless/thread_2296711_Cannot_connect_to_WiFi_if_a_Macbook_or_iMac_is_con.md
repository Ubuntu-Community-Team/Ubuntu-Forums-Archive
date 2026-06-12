---
title: "Cannot connect to WiFi if a Macbook or iMac is connected to the same WiFi"
date: 2015-09-28
forum: Networking &amp; Wireless
---

### Post by J.Z. on 2015-09-28
Hi all,

I've been using Ubuntu 14.04 since a year now, and all that time I had the following problem (which is currently becoming annoying):
If, and only if, to the network I want to connect to a Macbook or iMac is connected, I won't be able to connect. 

I have had this problem with 4 different networks, and this morning I once again confirmed this problem by turning on/off a iMac on the same network (with 3 other devices connected to it), and the iMac 'kicked' me. There is no IP-adres conflict. 

As noted in the Before Posting post, I updated my machine, rebooted and ran the github script (see attachment).

What do I do now? 

Thanks in advance for all the help!

---

### Post by Bucky Ball on 2015-09-28
Welcome. If you are running a static IP on an open network which is trying to serve you an IP that will probably cause issues.

If you click the network icon> edit> wireless> edit, do you have it set to 'Infrastructure' or 'Ad-hoc'?

---

### Post by J.Z. on 2015-09-28
Thanks! It says 'Mode: Infrastructure'; should I change it to 'Ad-hoc' ?

---

