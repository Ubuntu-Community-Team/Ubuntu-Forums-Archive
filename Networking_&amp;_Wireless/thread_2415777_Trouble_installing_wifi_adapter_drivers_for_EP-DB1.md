---
title: "Trouble installing wifi adapter drivers for EP-DB1607 on Ubuntu 18.04.2 LTS"
date: 2019-03-31
forum: Networking &amp; Wireless
---

### Post by lemonstale on 2019-03-31
I'm having trouble getting my wireless adapter to intall drivers and I'm wondering if anyone has any ideas.
Last time I tried I got:
cc1: some warnings being treated as errors
scripts/Makefile.build:332:  recipe for target  '/home/david/Desktop/wirelessadapter/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o'  failed
make[2]: ***  [/home/david/Desktop/wirelessadapter/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o]  Error 1
Makefile:1551: recipe for  target  '_module_/home/david/Desktop/wirelessadapter/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51'  failed
make[1]: ***  [_module_/home/david/Desktop/wirelessadapter/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51]  Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-46-generic'
Makefile:1551: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


Does anybody have any ideas?


Aidditional info:


Bus 003 Device 002: ID 0bda:0811 Realtek Semiconductor Corp.
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0461:4d64 Primax Electronics, Ltd
Bus 004 Device 003: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 004 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by praseodym on 2019-03-31
[https://ubuntuforums.org/showthread.php?t=2412170&p=13836896#post13836896](https://ubuntuforums.org/showthread.php?t=2412170&p=13836896#post13836896)

Try this one instead

---

### Post by lemonstale on 2019-03-31
Thank you that worked.

---

