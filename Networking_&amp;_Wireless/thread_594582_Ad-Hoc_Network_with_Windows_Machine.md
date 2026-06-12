---
title: "Ad-Hoc Network with Windows Machine"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Psicolonia on 2007-10-28
Hi everyone I've got a gutsy installation and I'm trying to make a Ad-Hoc network with a windows computer that connects to the internet. Windows has a wireless card and so does gutsy.

I'm able to connect windows machines to it, with a network called BBBB. it has a 13 char wep key.

So i'm sure windows is well configured because i can configure windows machines to get internet from this one through the ad-hoc network.

Every machine has a static ip adress rangin from 120.0.0.0 and netmask 255.0.0.0

here's what i'm trying on gusty (i assume there is where i'm wrong):

iwconfig wlan0 essid "BBBB"
iwconfig wlan0 rate auto
iwconfig wlan0 key XXXXXXXXXXXXX
iwconfig wlan0 mode Ad-Hoc
ifconfig wlan0 up
ifconfig wlan0 120.0.0.5 netmask 255.0.0.0
ifconfig eth0 down
route del -net default 2 > /dev/null
route add default gw 120.0.0.2

120.0.0.2 has the internet share.

what am i doing wrong???

thank you!

---

### Post by droid8622 on 2008-06-17
Try to make a network without encryption - i had the same problem with wep encryption

---

