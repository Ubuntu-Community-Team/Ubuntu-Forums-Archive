---
title: "Broadcom 4400 randomly disconnects"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by jjohns63 on 2008-01-14
My Broadcom 4400 is having a really weird issue where it will disconnect from the network, seemingly at random. This problem first appeared after I installed Samba, and it seems to happen after transferring a large amount of data over the network, though there doesn't seem to be a distinct tipping point and last night when nothing was accessing it, the problem happened. Since this is a HTPC running MythTV the only way I have is to reboot by pressing the power button. I haven't been able to figure out where the problem is, does anyone has any suggestions for what logs to look in?

---

### Post by jjohns63 on 2008-01-15
OK, some more details:
[LIST][*]I downloaded the driver from the broadcom website and the problem still occurs
[*]I was able to connect a keyboard and open a terminal and use
```
sudo ifdown eth0
sudo ifup eth0
``` to correct the issue, however the connection became unresponsive again as soon as I tried to access a samba share
[*]I tried setting up a cron job to do this every 15 minutes as a quick and dirty way to have it reset however this does not properly correct the problem when it occurs[/LIST]

---

