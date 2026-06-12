---
title: "detects wireless, doesnt connect!"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by pontifex3 on 2007-06-19
hi, i have a hp pavilion dv2000, with a Broadcom 1390 WLAN wireless card, i followed this how to [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) to install the driver and the output was just how it was supposed to be, the problem is i cant connect,
if i type
iwlist scanning
it wont scan, it just repeats the output it had sort of saved of something
sudo iwlist scanning
it scans succesfully, and in the eth1 it shows my universities internet, which doesnt have a password or anything, its essid is wlab, if i type this

sudo iwconfig eth1 essid wlab

nothing happens, i used kwifimanager, and it wouldnt connect either, also with netapplet and it event though iwlist scanning shows wlab, netapplet doesnt, and if i select other and type in wlab nothing happens either

i have also tryed network-admin (also in System-Network) and i configure the wireless card, typing wlab, in the password field i leave it empty and leave it in automatic (DHCP) aand nothing happens either!!, what am i doing wrong???, i have tried the same with other places that have free internet and have had the same result!, any help appreciated!

---

### Post by tnmarktx on 2007-06-19
Is your universities wireless not encrypted?  Have you not put in like some type of wep key?

---

