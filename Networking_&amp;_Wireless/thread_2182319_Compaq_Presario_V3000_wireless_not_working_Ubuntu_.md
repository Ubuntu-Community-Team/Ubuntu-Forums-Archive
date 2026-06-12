---
title: "Compaq Presario V3000 wireless not working: Ubuntu 13.10; BCM4311"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by Brandon_Anderson on 2013-10-20
I'm attempting to revive an old Compaq Presario V3000 for a relative. The only thing that is holding me up is the wireless. It has a Broadcom BCM4311 chipset. I've attempted to install the drivers through Additional Drivers but it shows no proprietary (or free) drivers available. The physical switch illuminates red, in the on position instead of the regular blue (working) color. No wireless networks appear in the networking menu. I've tried going through a few tutorials and guides to no success.

I'd appreciate any help with this. 

Thanks.

---

### Post by wildmanne39 on 2013-10-20
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot

---

### Post by Brandon_Anderson on 2013-10-20
Appreciate the help, Wild Man. Still no go on the wireless. Ran both and rebooted. Wifi still doesn't show up in the networking menu and the hardware switch does not change from the off color. On a prior version (I think 12.04) of Ubuntu, I had wireless working fine. So I'm not quite sure why it doesn't anymore.

---

### Post by Hadaka on 2013-10-21
Hi,please read and do post#6 from this thread..
[http://ubuntuforums.org/showthread.php?t=2182240](http://ubuntuforums.org/showthread.php?t=2182240)
this will help the Wild Man to diagnose your problem.
thanks.

---

