---
title: "Wifi adapter"
date: 2016-08-01
forum: Networking &amp; Wireless
---

### Post by carlostefano on 2016-08-01
Hello,

I am building a new PC and I would like to know what can be a good wifi adapter that can avoid compatibility issues. If it's possible I would prefer the standard AC on a PCI card. 

Thank you.

carlostefano

---

### Post by carlostefano on 2016-08-05
up

---

### Post by jeremy31 on 2016-08-05
Intel wifi chipset usually work well in Ubuntu

---

### Post by carlostefano on 2016-08-07
ok, thank you :)

---

### Post by kurt18947 on 2016-08-07
> **carlostefano said:**
> Hello,

I am building a new PC and I would like to know what can be a good wifi adapter that can avoid compatibility issues. If it's possible I would prefer the standard AC on a PCI card. 

Thank you.

carlostefano

Not inexpensive but the likelihood of the device working is pretty good. I don't see any AC devices, just N.

[https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)

It's true in my experience that Intel based wifi devices usually work.

---

### Post by carlostefano on 2016-08-07
[SIZE=1]Thanks. I think that the brand you suggested me (Penguin) is a bit difficult to get in my country. I have seen these 2 pci cards that are based on the intel chipset:

[/SIZE][h=1][SIZE=1]
[/SIZE][/h][h=1][SIZE=1]Intel model 7260HMWDTX1[/SIZE][/h][h=1][SIZE=1]Gigabyte GC-WB867D-I[/SIZE][/h][SIZE=1]

The second one is also pretty unexpensive. Probably they are both a better choice than the Asus [/SIZE][h=1][SIZE=1][FONT=inherit]PCE-AC56[/FONT][/SIZE][COLOR=#222222][FONT=Verdana] adapter. Which one do you think is the best? [/FONT][/COLOR][/h]

---

### Post by kurt18947 on 2016-08-08
Thinkpenguin isn't a brand, they're simply a reseller. If you're somewhat familiar with model designators, it's possible to determine the OEM. The Intel model you list is AC capable, the Thinkpenguin models are not.  Here's what wikidevi has to say about Intel 7260 chipsets:

[https://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_7260_(7260HMW)](https://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_7260_(7260HMW))

I couldn't find anything about the Gigabyte [SIZE=2]GC-WB867D-I chipset though I didn't spend a great deal of time looking.[/SIZE]

---

### Post by carlostefano on 2016-08-08
I have found that the Gigabyte should be based on the [COLOR=#111111][FONT=Arial] 8260 Intel, so the latest one that Intel has to offer.

[/FONT][/COLOR]http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-8260-brief.html

[https://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_8260_(8260NGW)](https://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_8260_(8260NGW))

---

### Post by Geoffrey_Arndt on 2016-08-08
Excellent choice.   Combine that with Intel HD Graphics 530 and you'll have a long term Linux Friendly PC.

---

### Post by kurt18947 on 2016-08-09
> **carlostefano said:**
> I have found that the Gigabyte should be based on the [COLOR=#111111][FONT=Arial] 8260 Intel, so the latest one that Intel has to offer.

[/FONT][/COLOR]http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-8260-brief.html

[https://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_8260_(8260NGW)](https://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_8260_(8260NGW))

I have no experience with any of those chipsets so I have no informed opinion. The only observation I would make is to generally beware of the newest hardware unless you're okay with being a beta tester. There may not have been the testing done on linux drivers and firmware prior to release that is done on Windows drivers and firmware. If these chipsets are incremental upgrades the software/firmware may be fine.

---

