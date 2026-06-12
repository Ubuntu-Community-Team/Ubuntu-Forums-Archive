---
title: "Help with installing drivers for ASUS PCE-N53 (Ralink RT5592)"
date: 2015-10-27
forum: Networking &amp; Wireless
---

### Post by Spency on 2015-10-27
I'm trying to Install an ASUS PCE-N53 PCI wifi adapter. I followed this [http://ubuntuforums.org/showthread.php?t=2203226](http://ubuntuforums.org/showthread.php?t=2203226) but didn't have any luck.

---

### Post by Spency on 2015-10-27
These are the error messages I get when I make:

```
/home/family/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPIoctlShow&#8217;:/home/family/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:4896:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
 intf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, _
                                                                     ^
/home/family/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:4896:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
 , size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );

cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/family/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.o' failed
make[2]: *** [/home/family/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1398: recipe for target '_module_/home/family/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux' failed
make[1]: *** [_module_/home/family/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-16-generic'
Makefile:381: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2




```

---

### Post by Spency on 2015-10-27
Solution found: [https://bbs.archlinux.org/viewtopic.php?id=152960&p=3](https://bbs.archlinux.org/viewtopic.php?id=152960&p=3)

---

