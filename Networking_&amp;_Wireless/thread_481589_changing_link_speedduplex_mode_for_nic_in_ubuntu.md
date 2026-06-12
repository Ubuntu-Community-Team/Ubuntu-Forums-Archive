---
title: "changing link speed/duplex mode for nic in ubuntu"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by DaddyBuckshaw on 2007-06-22
I finally got the install to work (thx guys) but i am not able to establish an internet connection because i have not found a way to change the link speed/duplex mode for my nic. normally in windows, i just go to device properties and i am able to change it to half speed 10 (it is usually set to autonegotiate when first installed) since autonegotiate never seems to work with my router. im sure there is some way to do it but it involves using the terminal so i figured id ask you guys.

used this command: ethtool -s eth0 speed 10 duplex half autoneg off

---

