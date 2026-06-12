---
title: "Ndiswrapper &amp; kernel panic"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by matrix_83 on 2007-07-20
Hello everybody. I have an Asus A4GA, my wireless card is a WL-159g with zydas chipset. Windows driver is zd1211u.inf. I'm using Ubuntu 7.04 (kernel version 2.6.20-16-generic) and ndiswrapper 1.47 (utils version 1.9). I have a problem and I don't know how to fix it. When system is starting sometimes I have a kernel panic with (only) Caps Lock flashing; system completely frozen. I have the same problem when I plug my usb external drive. Sometimes system crashes also with no apparent cause. How I can do? Thanks!!

P.S.: this happens only if ndiswrapper module is loaded!

Asus A4GA,
Mobile Pentium 4 3.2 GHz HT
1GB DDR RAM 333
Ati mobility radeon 9700 128 MB video ram
Asus USB wireless network adapter (WL-159g) with zydas chipset

---

### Post by djdicbob on 2007-07-21
I would try compiling ndiswrapper from source.  ```
sudo apt-get install -b ndiswrapper
```
Also, look to see if there are different versions of the Windoze drivers.  Good Luck:)

---

