---
title: "ethernet driver problems Marvell 80E8056 (sky2)"
date: 2015-06-22
forum: Networking &amp; Wireless
---

### Post by mart13 on 2015-06-22
Hi, i have a problem on my Ubuntu 14.04.
I have same problems if i run on the bootcd of Ubuntu 12.04 ; 13.10 ; 14.04 or 15.04
The problem is my ethernet driver, the sky2 sriver. (i know that because if i update it to sk98lin on Ubuntu 12.04 the issues with ethernet disappears.)
I downloaded the new driver on marvell.com (for fedora 2.6 and Linux kernel 2.4.20 or higher) but if is it possible to install the "Fedora 2.6" package on Ubuntu 12.04 ( i don't try to install the package for "Linux kernel 2.4.20 or higher" on Ubuntu 12.04 because the package for fedora 2.6 already works)it's not possible to install it on Ubuntu 14.04.
here the log :
```
root@martin-Aspire-M5100:~/Téléchargements/Linux_v10.93.3.3.tar.zip_FILES/Driver
Install# bash install.sh


Installation script for sk98lin driver.
Version 10.93.3.3 (Aug-22-2012)
(C)Copyright 2003-2012 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


1) installation          3) generate makefile
2) generate patch     4) exit
Choose your favorite installation method: 1











Please read this carefully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel 
module. This script will do this automatically per default.
 
Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) y




































IMPORTANT INFORMATION!

We found an alternative driver for your Marvell product on this system.
The alternative driver is _NOT_ directly supported by Marvell and does not
include all features provided by your device. If you want to use the
sk98lin driver developed by Marvell, you may choose either to deactivate
or remove the alternative driver.

[PRESS ANY KEY FOR FURTHER INSTRUCTIONS]















Do nothing:
  - The sk98lin will be installed
  NOTE: It may happen that the alternative driver will be loaded on 
  the next boot process. In this case the Marvell driver _WON'T_ be
  loaded.

Deactivate driver:
  - The alternative driver will be renamed to _skge.ko or _sky2.ko
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed

Remove driver (recommended):
  - The alternative driver will be removed from your system
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed


1) Do nothing
2) Deactivate diver
3) Remove driver
Action: 1

Create tmp dir (/tmp/Sk98IWgGObDVhEPCQjhMGaWmp)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (3.13.0-55-generic)                             [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (2)                                             [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check kernel gcc version (4.8.2) (Kernel:4.8.2 == gcc:4.8.2)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (/lib/modules/3.13.0-55-generic/build)     [   OK   ]
Check driver location (/lib/modules/3.13.0-55-generic/build/drivers/net/ethernet/marvell)                                                            [   OK   ]
Check sources for .config file (/lib/modules/3.13.0-55-generic/build/[   OK   ]
Copy and check .config file (done)                                   [   OK   ]
Check the mem address space (highmem64)                              [   OK   ]
Change IOMMU (enabled)                                               [   OK   ]
Create new .config file (done)                                       [   OK   ]
Execute: make oldconfig (done)                                       [   OK   ]
Check modpost availability (available)                               [   OK   ]
Unpack the sources (done)                                            [   OK   ]
Check firmware availability (done)                                   [   OK   ]
Execute: make prepare (done)                                         [   OK   ]
Check kernel header versiongrep: /lib/modules/3.13.0-55-generic/build/include/linux/version.h: Aucun fichier ou dossier de ce type
./functions: ligne 1117 : [: != : opérateur unaire attendu
grep: /lib/modules/3.13.0-55-generic/build/include/linux/version.h: Aucun fichier ou dossier de ce type
./functions: ligne 1126 : [: != : opérateur unaire attendu
 (Kernel:3.13.0 == Header:)                                          [   OK   ]
Check kernel functions (Changed: nothing)                            [   OK   ]
Compile the kernel (error)                                           [ failed ]

An error has occurred during the compile proces which prevented 
the installation from completing.                              
Take a look at the log file install.log for more informations.  
Installation of package failed.
root@martin-Aspire-M5100:~/Téléchargements/Linux_v10.93.3.3.tar.zip_FILES/Driver
Install# 
```

The problem is my kernel version how isn't compatible with the package i think, but sk98lin doesn't exist for 14.04...
Here are two another command how can help you to solve my problem :
```
martin@martin-Aspire-M5100:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.12                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.55.62                                        i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.92                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.92                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.55.62                                        i386         Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.92                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.92                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.55.62                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-55.92                                        i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
martin@martin-Aspire-M5100:~$ 
```
```
martin@martin-Aspire-M5100:~$ uname -a
Linux martin-Aspire-M5100 3.13.0-55-generic #92-Ubuntu SMP Sun Jun 14 18:33:09 UTC 2015 i686 athlon i686 GNU/Linux
martin@martin-Aspire-M5100:~$ 
```
Thanks for all of your help

EDIT : I uploaded the package here [http://www.mediafire.com/download/ls7t7n001c0bmkw/DriverInstall.tar.gz](http://www.mediafire.com/download/ls7t7n001c0bmkw/DriverInstall.tar.gz)

---

