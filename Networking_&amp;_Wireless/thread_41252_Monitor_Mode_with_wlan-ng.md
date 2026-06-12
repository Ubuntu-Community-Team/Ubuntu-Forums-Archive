---
title: "Monitor Mode with wlan-ng"
date: 2005-06-12
forum: Networking &amp; Wireless
---

### Post by SkEaToN on 2005-06-12
i installed the wlan-ng driver for my prism2.5 card, its working fine, but i can't switch to monitor mode when i type
iwconfig wlan0 mode Monitor


does anybody know if i have to take some changes in config files or how i get it working?

thx

---

### Post by sebw on 2005-06-12
You may have to patch your drivers to get monitor mode..

I retrieved the patch for my orinoco 11mbps silver here :
[http://www.kismetwireless.net/code/](http://www.kismetwireless.net/code/)

Not sure where you can find the patch for yours

---

