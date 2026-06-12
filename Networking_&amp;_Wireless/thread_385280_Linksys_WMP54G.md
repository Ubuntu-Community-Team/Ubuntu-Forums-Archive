---
title: "Linksys WMP54G"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by ruz322 on 2007-03-15
Hey everyone. I'm sort of new to ubuntu but not linux. I just purchased a Linksys WMP54G wireless card which I know has a Ralink chipset. Upon ubuntu install, the card is detected in hardware and is picked up as interface ra0. Also when i run iwconfig it is picked up. It picks up my broadcasted ESSID and will connect to it upon entering the ip settings. I get no connection with the card though. It is reporting it is connected to my network but shows no signs of connectivity. No internet, network resources, nothing. Please help! Nobody seems to be having the same problem I am!

---

### Post by handaxe on 2007-03-15
Hi,

It is best that you report he full output of sudo iwconfig and sudo ifconfig.  Maybe also sudo lshw -C network

HA

---

