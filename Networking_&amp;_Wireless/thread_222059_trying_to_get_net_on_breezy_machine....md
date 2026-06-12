---
title: "trying to get net on breezy machine..."
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by mªrty on 2006-07-24
hi,

i have a machine running breezy, has a netgear wg311 v3 wifi card (apparently won't work with fresh install). i also have a netcomm usb lan key that i can't seem to get working (and hence, no wireless :( )

apparently the usb device uses the rtl8150 module, which is on the system. when connected, the '100meg' led comes on, but not the ACT led.

i'm new to ubuntu, so any suggestions are welcome. thanks.

---

### Post by mªrty on 2006-07-24
ok, the problem just got a lot simpler. usb ethernet now works.

i can't seem to install ndiswrapper. my ndiswrapper1.21 folder is on desktop. im not sure i made the links to the kernel correctly or whatever they say to do. but when i run *make uninstall* i get this:

```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper': Permission denied
make: *** [uninstall] Error 1
```

after running *make* i get:
```
make -C driver
make[1]: Entering directory `/home/tia/Desktop/ndiswrapper-1.21/driver'
Can't find kernel build files in /lib/modules/2.6.12-9-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/tia/Desktop/ndiswrapper-1.21/driver'
make: *** [all] Error 2
```

and then *make install* just gives a combination of those errors it seems.

i know i'm doing something very simple incorrectly...

---

