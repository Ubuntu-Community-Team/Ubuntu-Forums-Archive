---
title: "HP Proliant DL320 and Broadcom BM5714 problem"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by rhaces on 2007-02-27
Hi, i  installed Ubuntu 6.10 Server on my new Proliant DL320 . It seems to be working everything OK but both of my integrated eth's are having problems. If im on the box, everything works great, but if im working remotely on the same LAN, al the ICMP packets pass great but tcp (ssh, apache, mysql, etc....) every once in a while dies and there is nothing that can make them come to live from remote locations (i ping my server and it answers, but if i do an ssh it dowsnt answer). If i want to bring it up live again with a simple "route" (or start downloading something from internet or do any kind of tcp connection) and everything works great for a while and then it dies again. I don't think is a hardware problem cause both of my eth (exact same model) are doing the same, it has to be some kind of driver compatibility or something. This is my configuration:

~# uname -a
Linux bowie 2.6.17-11-server #2 SMP Thu Feb 1 19:53:33 UTC 2007 i686 GNU/Linux
~# ethtool -i eth0
driver: tg3
version: 3.59.1
firmware-version: 5714-v3.24
bus-info: 0000:03:04.0
03:04.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5714 Gigabit Ethernet (rev a3)
03:04.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5714 Gigabit Ethernet (rev a3)

Any clue?
Thnks

---

