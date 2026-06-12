---
title: "What is Wifi0?"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by SDE on 2007-04-17
My Toshiba laptop has an internal 3945ABG, and I just got a Cisco Aironet 350 Series in hopes to be able to play around on my network with monitor mode and packet injection.

When put my wireless card in, I get eth0 (wired connection) eth1(3945 wireless) eth2 (aironet 350) ... then in my network manager, wifi0 shows up.  What is that and what causes that?

---

### Post by dfreer on 2007-04-17
for some reason wireless cards can appear in ifconfig with several different names depending on the driver used. I've seen ethX, authX, and wifiX myself.

---

