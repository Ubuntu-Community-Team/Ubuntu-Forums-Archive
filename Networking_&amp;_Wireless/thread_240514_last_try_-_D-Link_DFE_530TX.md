---
title: "last try - D-Link DFE 530TX"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by mikeweezer on 2006-08-21
Hi all,

  I've approached the idea of moving to Linux with great enthusiasm, but it doesn't look like I can get internet on Ubuntu so its about time to try something that will work...  In my final attempt, I loaded a D-Link DFE 530TX since my VIA Rhine III is not supported.  In Windows it works and all is well.  In Ubuntu, no luck whatsoever.  I googled the driver and tried a modprobe 8139too and a modprobe via-rhine without any luck.
I'd greatly appreciate any help, but I'm thinking this is a lost cause.


mike

---

### Post by x64Jimbo on 2006-08-21
Have you tried using ndiswrapper?

---

### Post by hachaboob on 2006-08-21
What is the output of dmesg and contents of /etc/network/interfaces and output of ifconfig -a

:)

---

