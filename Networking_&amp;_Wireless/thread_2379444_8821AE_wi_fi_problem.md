---
title: "8821AE wi fi problem"
date: 2017-12-05
forum: Networking &amp; Wireless
---

### Post by danief. on 2017-12-05
Hi, i've just bought Lenovo idepad 310 115ikb. When im on windows 10, everythings works fine. When im on Ubuntu, i cant connect my wi fi to any AP. 
I tried everything i know, but it still doesnt work. 

As i said before i got this network adapter: Realtek 8821AE wirless Lan 802.11ac

Thank you for your time

---

### Post by ub-newbie on 2017-12-07
Please post the output from```
ifconfig
```

---

### Post by SeijiSensei on 2017-12-08
I had to compile the driver from source code for my RTL8812au.  There is now a package in the "universe" repositories called [rtl8812au-dkms]("https://packages.ubuntu.com/xenial/kernel/rtl8812au-dkms") which I believe can do that for you on Ubuntu 16.04 or later. From an earlier conversation here, that driver may work with the RTL8821 series as well.

Before that, though, have you run the "Driver Manager" application?  It may find the driver for you and install it.

You'll also find a lot of articles about this if you search Google for "[rtl8821ae linux]("https://www.google.com/search?q=rtl8821ae+linux")".

---

### Post by 88les on 2017-12-08
Thank you so much for the link attached here. Hope this could be helpful for the OP.

---

