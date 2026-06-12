---
title: "WPA still won't go"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by tekdata on 2007-05-17
Feisty Fawn 64-bit, Dell Inspiron 1501 turion 64 dual-core. Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01). bcm43xx chipset.

I have this card working for unencrypted and WEP with both ndiswrapper and the open-source bcm43xx driver, but no matter how much I mess with WPA, I just can not get it working. I've tried manual configurations, and letting network manager take the helm. It just will not connected to my WPA network.

On the same machine, a zw1211rw USB will connect to the WPA net just fine using network manager.

Any ideas?

---

### Post by Elliot.strumlauf on 2007-05-20
I need help with WPA, as well. I need to know how to get hooked up in general though. Any suggestions?

---

### Post by firecat53 on 2007-05-22
For the Broadcom 1390 cards you need to compile ndiswrapper from source. There are several posts on how to do this. Then it will work perfectly :)

Scott

---

