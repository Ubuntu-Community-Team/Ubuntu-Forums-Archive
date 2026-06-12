---
title: "Wireless not working on 14.04LTS"
date: 2014-08-18
forum: Networking &amp; Wireless
---

### Post by agnes2 on 2014-08-18
Hello,

I've just uploaded ubuntu from 12.04 LTS to 14.04 LTS, and wireless is not working.

lspci returned

```
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)


```

I've tried it: [http://ubuntuforums.org/showthread.php?t=2221087](http://ubuntuforums.org/showthread.php?t=2221087) 
but I don't get it...

Could you help me, please?

Thank a lot!

---

### Post by chili555 on 2014-08-18
Please get a temporary wired ethernet or similar connection. Open a terminal Ctrl+Alt+t and copy and paste each command:```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet and reboot.

---

