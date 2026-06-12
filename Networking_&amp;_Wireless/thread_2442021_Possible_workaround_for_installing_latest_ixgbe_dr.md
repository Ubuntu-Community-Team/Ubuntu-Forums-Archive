---
title: "Possible workaround for installing latest ixgbe drivers on Ubuntu 20?"
date: 2020-04-28
forum: Networking &amp; Wireless
---

### Post by missljud on 2020-04-28
[COLOR=#555555][FONT=intel-clear][SIZE=3][FONT=arial]Installed latest Ubuntu 20.04 the other day, and ever since my Intel X520-T2 is throwing billions of "Warning firmware error detected FWSM: 0x00000000" errors. So I thought an update from the old ixgbe 5.1.0-k that is shipped with Ubuntu to the latest ixgbe 5.6.5 were in order, but the thing is it can't be compiled. Fails with the following error:[/FONT][/SIZE]

[/FONT][/COLOR]make
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-26-generic'
CC [M] /home/max/ixgbe-5.6.5/src/ixgbe_main.o
In file included from /home/max/ixgbe-5.6.5/src/ixgbe_osdep.h:17,
from /home/max/ixgbe-5.6.5/src/ixgbe_type.h:45,
from /home/max/ixgbe-5.6.5/src/ixgbe_dcb.h:7,
from /home/max/ixgbe-5.6.5/src/ixgbe.h:24,
from /home/max/ixgbe-5.6.5/src/ixgbe_main.c:31:
/home/max/ixgbe-5.6.5/src/kcompat.h:2796:10: fatal error: linux/pci-aspm.h: No such file or directory
2796 | #include <linux/pci-aspm.h>
        | ^~~~~~~~~~~~~~~~~~
compilation terminated.
make[2]: *** [scripts/Makefile.build:275: /home/max/ixgbe-5.6.5/src/ixgbe_main.o] Error 1
make[1]: *** [Makefile:1719: /home/max/ixgbe-5.6.5/src] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-26-generic'
make: *** [Makefile:87: default] Error 2


[SIZE=3][FONT=arial][COLOR=#555555]Read that recently the linux/pci-aspm.h header file was removed from the kernel source or something, hence it's failing. Ubuntu 20 uses kernel 5.4 and latest available ixgbe drivers are supported up to kernel 5.3.[/COLOR]

[COLOR=#555555]Anyone here that can provide a quick fix for this maybe?[/COLOR]

[COLOR=#555555]Best regards, marcus![/COLOR][/FONT][/SIZE]

---

### Post by tamagochi on 2020-05-14
Hello Marcus!

Yesterday showing a new driver on [https://sourceforge.net/projects/e1000/](https://sourceforge.net/projects/e1000/) website. This release version is 5.7.1. I have compiled and installed on my system over dkms and work flawlessly over one half a day. The new Ubuntu release (20.04 LTS) using 5.4 kernel, i using instead of the older installed 5.3.0-46-generic kernel because dmesg to be filled with FIRMWARE ERRORs.

Best regards, Steve!

---

### Post by alexhaj on 2020-07-04
I compiled the 5.7.1 Intel driver on 20.04 but the device is UNCLAIMED in lshw and I'm getting "The EEPROM Checksum Is Not Valid" in dmesg.

The Intel driver page lists support for 18.04 and 19.04 but not 20.04.

How were you able to get this to work?

---

