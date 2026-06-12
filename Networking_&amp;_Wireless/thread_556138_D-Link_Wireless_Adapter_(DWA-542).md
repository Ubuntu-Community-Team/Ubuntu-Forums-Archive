---
title: "D-Link Wireless Adapter (DWA-542)"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by isaacsaidso on 2007-09-20
For whatever reason Kubuntu 7.04 does not recognize my D-Link Desktop Wireless Card (DWA-542).  Or at least i think it doesn't.  I ran the lspci command, and in the last entry it was a line that said:

Artheros Communications, device not recognized

I'm not really sure how to configure Kubuntu to get it to recognize the card.  Any help would be appreciated.  Thank you.

---

### Post by noob12 on 2007-09-21
That's ok.  Type
```

lspci -nn

```
And post the line from that for your card. The device id will usually allow people to identify the device and suggest a driver.

---

### Post by isaacsaidso on 2007-09-21
Thanks for responding noob12. I ran lspci -nn and this is what it reported:

05:0b.0 Network Controller [0280]: Atheros Communications, Inc. Unknown Device [168c:0023] (rev 01)

So are the numbers on the end of the line the most important?

---

### Post by noob12 on 2007-09-21
Yes, these are the vendor and device id for the chipset.  This determines the drivers that would support it.

This seems to be an AR 5416.  The older madwifi drivers in Ubuntu 7.04 won't support it.

It looks like the current madwifi ones do support it, but I am not certain.  You can try building them.

The ndiswrapper site makes explicit mention of the card and chipset and their wiki says that it works with current ndiswrapper and the net5416 windows driver from the accompanying CD. Note: The version of ndiswrapper in Ubuntu is not current; it is 1.38 while current is 1.48.  ([http://ndiswrapper.sourceforge.net/joomla/index.php?option=com_openwiki&Itemid=33](http://ndiswrapper.sourceforge.net/joomla/index.php?option=com_openwiki&Itemid=33))

---

### Post by isaacsaidso on 2007-09-25
I downloaded the ndiswrapper i needed from the site and followed the instructions.  When i tried to do a make uninstall, i got an error message saying that not all files had been uninstalled and to keep doing the make uninstall until all files were removed.  I kept doing it but it didn't remove everything.  From there i did the make command, and then the make install.  After i typed the make install i got the following error message: 

make -C driver install
make[1]: Entering directory `/home/ciperez/ndiswrapper/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/home/ciperez/ndiswrapper/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
echo /lib/modules/2.6.20-15-generic/misc
/lib/modules/2.6.20-15-generic/misc
mkdir -p /lib/modules/2.6.20-15-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-15-generic/misc
/sbin/depmod -a 2.6.20-15-generic -b /
make[1]: Leaving directory `/home/ciperez/ndiswrapper/ndiswrapper-1.48/driver'
make -C utils install
make[1]: Entering directory `/home/ciperez/ndiswrapper/ndiswrapper-1.48/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:

That's not the entire error message.  The whole thing is really long.  Anyways, any ideas as to what happened?

---

### Post by ANTC on 2008-01-09
Hey has is there a fix for this, i'm planing on going ubuntu 64bit and well i have this same wireless N card

---

