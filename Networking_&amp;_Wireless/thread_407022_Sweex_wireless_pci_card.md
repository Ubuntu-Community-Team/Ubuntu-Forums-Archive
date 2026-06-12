---
title: "Sweex wireless pci card"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by celticbhoy on 2007-04-11
I have a sweex wireless card that I am having trouble getting to work. Ubuntu detects the card as a prism Javelin/XBow ISL3886 chipset. When I try any how to's Iget so far and then all how to's refer to the card as wlan0 yet on my system the result of iwconfig gives the details under eth2.
the results as follows :-

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

I dont know what to try next. Any ideas ????

---

### Post by chili555 on 2007-04-11
Try this: [http://patrick.vande-walle.eu/software/intersil-isl3886-linux/](http://patrick.vande-walle.eu/software/intersil-isl3886-linux/)

---

