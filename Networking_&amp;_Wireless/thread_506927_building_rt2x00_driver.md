---
title: "building rt2x00 driver"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by nickmcg on 2007-07-22
I'm trying to build the latest rt2x00 driver, sources downloaded from the daily cvs at [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

I think that I've got all the build prerequisits, but when I try to build, I get the following:
```
In file included from <command line>:1:
/home/robot/downloads/rt2x00-cvs-2007072208/rt2x00_compat.h:27:2: error: #error 802.11 wlan card support not enabled in kernel!
/home/robot/downloads/rt2x00-cvs-2007072208/rt2x00_compat.h:56:2: error: #error mac80211 debugfs support has been disabled in your kernel!
make[2]: *** [/home/robot/downloads/rt2x00-cvs-2007072208/eeprom_93cx6/eeprom_93cx6.o] Error 1
make[1]: *** [_module_/home/robot/downloads/rt2x00-cvs-2007072208] Error 2
make: *** [default] Error 2

```
Does this mean that I need to rebuild the kernel in its entirety and if so, will I need to do the same again when the next version arrives? (does update manager cope with a rebuilt kernel?)

Any advice gratefully recieved

Nick

---

