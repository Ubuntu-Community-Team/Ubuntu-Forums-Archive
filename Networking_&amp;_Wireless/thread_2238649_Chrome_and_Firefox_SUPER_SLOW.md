---
title: "Chrome and Firefox SUPER SLOW"
date: 2014-08-09
forum: Networking &amp; Wireless
---

### Post by NeoX12 on 2014-08-09
I got a pretty decent internet speed at home and everything was going fine till I switched to Ubuntu lol

It takes a LONG time for firefox/chrome to load almost any webpage. Videos on youtube.. or other sites....... take forever to load.
I used to be able to stream 480p but now, I have problems streaming 360p.. I did contact my ISP and they said they triple-checked the speed from their end.


I did disable iPv6 addressing... but, no luck.

Any help would be really appreciated.


Yes I did search for similar threads. The link inside the last thread I looked up, was dead.

Thanks!

---

### Post by praseodym on 2014-08-09
Please show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
iwlist chan
sudo iwlist scan
```

---

