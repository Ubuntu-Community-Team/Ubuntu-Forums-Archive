---
title: "Ubuntu 12.04.4 Broadcom BCM4360 Wireless Adapter issue"
date: 2014-02-14
forum: Networking &amp; Wireless
---

### Post by Bondarev_Sergey on 2014-02-14
I've installed Ubuntu 12.04.4 on my macbook pro retina 13" (late 2013). It has Broadcom BCM4360 Wireless Network Adapter. In additional drivers says that it has proprietary drivers. I connected usb wifi adapter and clicked Activate it was doing something long time (I have been waiting for 3 hrs).
However it works fine on ubuntu 13.10

Please help how can I make it work?

---

### Post by chili555 on 2014-02-14
Please give us more information about your wireless card. From the terminal:```
lspci -nn | grep 0280
```Thanks.

---

### Post by Bondarev_Sergey on 2014-02-14
03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)

Thanks

---

### Post by chili555 on 2014-02-14
Please see posts 4, 5 and 6 here: [http://ubuntuforums.org/showthread.php?t=2159851](http://ubuntuforums.org/showthread.php?t=2159851)  You have the same device and should manually download the linked package and install it as noted. Please post back if you get stuck.

---

### Post by Bondarev_Sergey on 2014-02-14
It works fine! Thank you very much!!! :)

---

