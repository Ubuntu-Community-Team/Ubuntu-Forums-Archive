---
title: "Tenda W900U wifi dongle drivers?"
date: 2015-05-23
forum: Networking &amp; Wireless
---

### Post by ondrej-sojka on 2015-05-23
Hi, I bought one W900U AC usb dongle and it refuses to work under Xubuntu. On the CD are just Windows EXEs. Linux support is noted at the eshop I bought it at.

---

### Post by howefield on 2015-05-23
Thread moved to the "*Networking & Wireless*" forum for better chance of assistance.

---

### Post by chili555 on 2015-05-23
Please insert the device and run and post the result of:```
lsusb
```Is it, by chance 0a5c:bd1d? If so, please see: [https://wikidevi.com/wiki/Tenda_W900U](https://wikidevi.com/wiki/Tenda_W900U)> Probable Linux driver
noneYou might be able to get the device working with ndiswrapper.  It requires and only works with Windows XP driver files. Do you have or can you find them?

---

### Post by ondrej-sojka on 2015-05-24
It is that USB ID. On the CD are just exe's, dll's and one Autorun.inf (telling the system what to do when the disc is inputted). Means that I can't use it under Linux? (>returning to shop)

---

### Post by chili555 on 2015-05-24
> >returning to shopThat's what I'd do. I love adventure as much as the next guy but this would be quite a challenge that might or might not be successful in the end.

There are usually a few threads here about fully supported devices. Search and choose wisely.

---

