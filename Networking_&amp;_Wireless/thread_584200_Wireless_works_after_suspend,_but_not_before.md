---
title: "Wireless works after suspend, but not before"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by Goombie on 2007-10-20
Ok, this is an odd problem. I have a wireless card with a Broadcom 4306 chipset which I finally got set up in Gutsy, after much hair pulling and agony. Now, whenever I boot up, the network-admin program doesn't even see my wireless card. I have to suspend and then resume my computer in order to use my wireless internet! Anyone know how to fix this?
Also, I thought I had my wireless card configured as interface wlan0, but it keeps showing up as eth1 instead. When I check the dmesg output, it says that ndiswrapper changed the name from 'wlan0' to 'eth1', when I want the name to stay at 'wlan0'.
Maybe these two problems are related. Thanks to anyone who can help! :)

---

### Post by mpierce on 2007-10-20
See my post to SuperAndy re: Static IP on RT61 in Gutsy, needs networking restart to work. 

Configure /etc/network/interfaces to use eth1 as I show. This should (hopefully) fix your problem.

---

