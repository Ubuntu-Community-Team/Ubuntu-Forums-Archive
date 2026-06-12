---
title: "Wireless doesn't work!"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by marco1989 on 2008-10-09
-LAPTOP
-TOSHIBA SATELLITE A300D - 14E
-ETHERNET -> MARVELL
-WIRELESS -> ATHEROS AR9281
-S.O -> UBUNTU 8.04
-KERNEL VERSION -> 2.6.24-19generic
-DRIVER WIRELESS -> ATH9K (driver for atheros ar9281)

-Ouput of lspci
..
02:00.0 Network controller:Atheros Communications INc. Unkown device 002a (rev 01)
..



Ethernet works.
Wireless see the network wireless but doesn't connect!!
Somebody help me, please!!
If I had made some mistake, i'm sorry.. i'm Italian...

---

### Post by maligent on 2009-01-12
I had the same chipset/problem with my Qosmio, I wound up having to manually enter the AP mac address in the in the not sure your level so please don't be offended if this is elementry to you but in the terminal "sudo iwlist scanning" and it should show your router mac in the for of XX:XX:XX:XX then just enter it "iwconfig ath0 (or wlan0 whatever your adapter is) ap XX:XX:XX:XX you can also add this command in kwifimanager. 
Hope this helps

---

