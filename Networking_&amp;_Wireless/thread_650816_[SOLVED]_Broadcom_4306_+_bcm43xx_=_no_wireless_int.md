---
title: "[SOLVED] Broadcom 4306 + bcm43xx = no wireless interface"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by alexmoon on 2007-12-26
I can't seem to get wireless working, and even the "wireless" option has disappeared from network manager.

I've spent a few days trying to get wireless working, and have tried ndiswrapper solutions and bcm43xx-fwcutter solutions, which is probably part of the problem - I suspect I've done something stupid somewhere and have lost track of it. 

Anyway, I finally managed to install bcm43xx-fwcutter with the "restricted drivers" tool - all other attempts to download drivers have stalled/not managed to connect/something.

Apart from the efforts of the last few days, I'm trying with a fresh install of gutsy. 

**Now, iwconfig gives:**

lo        no wireless extensions.

eth0      no wireless extensions.


I thought the solution might be to try **ifup eth1** (since that's what I used to use, and it gave this:
Ignoring unknown interface eth1=eth1.

I also tried editing /etc/network/interfaces according to this guide: [http://ubuntuforums.org/showthread.php?t=603154&highlight=%2Fetc%2Fnetwork%2Finterfaces](http://ubuntuforums.org/showthread.php?t=603154&highlight=%2Fetc%2Fnetwork%2Finterfaces),  but that just made the "wired" option disappear from network manager and my wired connection stopped working. Currently **/etc/network/interfaces** reads:

auto lo
iface lo inet loopback

---

### Post by alexmoon on 2007-12-29
I reinstalled from scratch and went through System -> Restricted Drivers and this time *seem* to have a working wireless and wireless option in network manager. I still can't actually detect my home wireless network, but I guess that's a whole other issue.

---

