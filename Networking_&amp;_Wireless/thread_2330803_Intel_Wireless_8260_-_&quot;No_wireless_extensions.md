---
title: "Intel Wireless 8260 - &quot;No wireless extensions&quot;"
date: 2016-07-15
forum: Networking &amp; Wireless
---

### Post by steckzt on 2016-07-15
I just got my Dell XPS 13 Dev edition a few days ago with Linux Ubuntu 14.04 preinstalled (I'm not unfamiliar with ubuntu, as I used to run virtual machines). It worked fine for the first few days, but then after writing this line to /etc/rc.local ```
[COLOR=#111111][FONT=Consolas]rfkill block bluetooth[/FONT][/COLOR]
``` This was written with the intention of making sure the bluetooth didn't turn on automatically at startup. All was fine for about a half hour, then I was prompted to to download some updates which required a restart. After my restart, I got the dredded > No Network Devices Available.

I've ran some queries to get some data that may be useful.
```
###############lspci########################00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 0a)
00:04.0 Signal processing controller: Intel Corporation Device 1903 (rev 09)
00:14.0 USB controller: Intel Corporation Device 9d2f (rev 21)
00:14.2 Signal processing controller: Intel Corporation Device 9d31 (rev 21)
00:15.0 Signal processing controller: Intel Corporation Device 9d60 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Device 9d61 (rev 21)
00:16.0 Communication controller: Intel Corporation Device 9d3a (rev 21)
00:17.0 SATA controller: Intel Corporation Device 9d03 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Device 9d14 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Device 9d15 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Device 9d18 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d48 (rev 21)
00:1f.2 Memory controller: Intel Corporation Device 9d21 (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d70 (rev 21)
00:1f.4 SMBus: Intel Corporation Device 9d23 (rev 21)
3a:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
3b:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 525a (rev 01)
3c:00.0 Non-Volatile memory controller: Toshiba America Info Systems Device 010f (rev 01)
###############iwconfig####################
lo        no wireless extensions.
###############rfkill list#################
No result (empty)

```

I have since removed that line of code in /etc/rc.local, and have tried changing my proprietary drivers but to no avail. I have looked at all post titled similarly (3) and could only find one that was similar, but my problem was not solved.
Any suggestions? Thank you to anyone who will help. This seems to be a common issue on ubuntu, so forgive me if I'm beating a dead horse.

Things i have tried:
[https://ubuntuforums.org/showthread.php?t=2329846](https://ubuntuforums.org/showthread.php?t=2329846)
[https://ubuntuforums.org/showthread.php?t=2305117&highlight=Intel+Wireless+8260+-](https://ubuntuforums.org/showthread.php?t=2305117&highlight=Intel+Wireless+8260+-)
[http://askubuntu.com/questions/741620/what-are-the-possible-commands-to-reset-a-wifi-connection/741626#741626](http://askubuntu.com/questions/741620/what-are-the-possible-commands-to-reset-a-wifi-connection/741626#741626)
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Realtek-wireless-chipset](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Realtek-wireless-chipset)

---

### Post by steckzt on 2016-07-15
After checking out the dmesg, I am consistantly seeing > init: bluetooth main process (xxx) terminated with

---

