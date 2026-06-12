---
title: "HP dv2000 laptop - Wireless doew not work"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by guliver on 2008-05-01
I have HP DV2000 laptop, wireless does not work, I have red exclamation mark on that network manager.

Is it possible to fix this, how?

Im using latest version of Ubuntu 8.04.


Thanks

---

### Post by h4mx0r on 2008-05-01
please paste the output of lshw, lspci, lsusb, ifconfig. And maybe read the manual/printout about that laptop to see what wireless card it has if you don't know what command to enter. dv2000 has least several hundred different models of laptop each with custom choice in wireless cards. If the restricted manager doesn't show anything about wireless, and dmesg command lists nothing with it being marked as unclaimed in lshw then your only choice is to find a driver or use ndiswrapper.

---

