---
title: "RT2870 drivers in ubuntu 12.04LTS"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by lucas15 on 2014-03-13
Hi , i'm new in the forum also in ubuntu (i used it but never before have installed a driver).

The problem is, i bought a USB WIFI adapter (rt2870) from ebay and i get the drivers in one cd (If someone needs it i can post here) , but i dont know what of these i should install. I see a lot of threads about this adapter with 'step by step' but i can't do nothing.

Here i attach a photo from the cd. Sorry if i posted here in the wrong subforum and thanks !

[ATTACH=CONFIG]251101[/ATTACH]

---

### Post by chili555 on 2014-03-13
First of all, the driver CD is generally too old for our rapidly changing and updated kernels, but let's see. The best way to proceed is to identify your device. Please open a terminal Ctrl+Alt+t and run and post:```
lsusb
```Thanks.

---

### Post by lucas15 on 2014-03-13
Here is the output

```

Bus 001 Device 002: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 003: ID 04cf:8819 Myson Century, Inc. USB 2.0 SD/MMC Reader
Bus 004 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 004 Device 003: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Thanks to you for the fast answer!

---

### Post by chili555 on 2014-03-13
> 148f:7601 Ralink Technology, Corp. As you might suspect, the MT7601u folder is what you want. Please double click it and see what's in it. Usually the file name gives a clue as to the version, like [COLOR="#FF0000"]2011[/COLOR]_[COLOR="#FF0000"]0719[/COLOR]_RT3070_RT8070_RT3370_RT5370_etc. or some such. Then we need to see which kernel version you have to see how close the match is:```
uname -r
```We are aiming to install the driver *mt7601Usta*. There may be a better way than the CD.

---

### Post by lucas15 on 2014-03-13
Here are the files inside the folder MT7601U

[ATTACH=CONFIG]251104[/ATTACH]

Also , output for *uname -r *is
```
3.11.0-18-generic
```

---

### Post by chili555 on 2014-03-13
That's the kernel version I have and I found an even newer version and it builds for me but with a zillion warnings. Let's try it and see what happens.

Please get version MT7601U USB version 3.0.0.4 here and download it to your desktop: [http://www.mediatek.com/en/downloads/](http://www.mediatek.com/en/downloads/)  Right-click it and select 'Extract Here.' Now back to the terminal and with a temporary wired ethernet connection:```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
make
sudo make install
sudo modprobe mt7601Usta 
```Does your wireless spring to life?

---

### Post by lucas15 on 2014-03-13
Working men! Amazing thanks you so much!

---

### Post by chili555 on 2014-03-13
Awesome! You will have helped quite a few searchers. You compiled the driver for your currently running kernel only. When Update Manager gleefully installs a later kernel version, after the reboot, you must recompile:```
cd ~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
[COLOR="#FF0000"]make clean[/COLOR]
make
sudo make install
sudo modprobe mt7601Usta
```Please retain the file and these instructions for that time. Also, please use thread tools at the top to mark Solved.

Glad it's working.

---

### Post by lucas15 on 2014-03-13
Thanks so much for the explanation. A little comment. my cd direccion is diferent (spanish ubuntu) and is 
```
cd /home/lucasgabriel/Escritorio/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
```

Also , thanks for the last comment . This is solved , thanks you very much.

---

### Post by Daniel_Burton on 2014-04-05
Created new topic as have same issue.

---

### Post by deldin on 2014-09-01
hi men

I have tue same usb adapter like lucas15 and lubuntu 12.04.
kernel version is 3.2.0-68-generic and the driver is DPA_MT7601U_LinuxSTA_3.0.0.4_20130916
when I write sudo make install I receive this 

miriam@supercomputer-di-miriam:~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916$ sudo make install
[sudo] password for miriam: 
make -C UTIL/ install
make[1]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL'
make -C /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux -f Makefile.6 install
make[2]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux'
make[2]: Makefile.6: No such file or directory
make[2]: *** No rule to make target `Makefile.6'.  Stop.
make[2]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL'
make: *** [install] Error 2

can you help me?

---

### Post by chili555 on 2014-09-01
> **deldin said:**
> hi men

I have tue same usb adapter like lucas15 and lubuntu 12.04.
kernel version is 3.2.0-68-generic and the driver is DPA_MT7601U_LinuxSTA_3.0.0.4_20130916
when I write sudo make install I receive this 

miriam@supercomputer-di-miriam:~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916$ sudo make install
[sudo] password for miriam: 
make -C UTIL/ install
make[1]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL'
make -C /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux -f Makefile.6 install
make[2]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux'
make[2]: Makefile.6: No such file or directory
make[2]: *** No rule to make target `Makefile.6'.  Stop.
make[2]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL'
make: *** [install] Error 2

can you help me?Can you confirm that you have both linux-headers-generic and build-essential installed? They are needed to compile from source:```
sudo dpkg -s build-essential
sudo dpkg -s linux-headers-generic
```Please install if missing and try again.

---

### Post by deldin on 2014-09-01
```

miriam@supercomputer-di-miriam:~$ sudo dpkg -s build-essential
[sudo] password for miriam: 
Package: build-essential
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 37
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 11.5ubuntu2.1
Depends: libc6-dev | libc-dev, gcc (>= 4:4.4.3), g++ (>= 4:4.4.3), make, dpkg-dev (>= 1.13.5)
Description: Informational list of build-essential packages
 If you do not plan to build Debian packages, you don't need this
 package.  Starting with dpkg (>= 1.14.18) this package is required
 for building Debian packages.
 .
 This package contains an informational list of packages which are
 considered essential for building Debian packages.  This package also
 depends on the packages on that list, to make it easy to have the
 build-essential packages installed.
 .
 If you have this package installed, you only need to install whatever
 a package specifies as its build-time dependencies to build the
 package.  Conversely, if you are determining what your package needs
 to build-depend on, you can always leave out the packages this
 package depends on.
 .
 This package is NOT the definition of what packages are
 build-essential; the real definition is in the Debian Policy Manual.
 This package contains merely an informational list, which is all
 most people need.   However, if this package and the manual disagree,
 the manual is correct.
Original-Maintainer: Matthias Klose <doko@debian.org>
miriam@supercomputer-di-miriam:~$ 

```

```

miriam@supercomputer-di-miriam:~$ sudo dpkg -s linux-headers-generic
Package: linux-headers-generic
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 32
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 3.2.0.68.81
Depends: linux-headers-3.2.0-68-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers
 available.
miriam@supercomputer-di-miriam:~$ 

```

---

### Post by chili555 on 2014-09-01
Please show us the result of:```
cd ~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916
make clean
make
sudo make install
```Thanks.

---

### Post by deldin on 2014-09-01
I try again but I have the same output :(

---

### Post by chili555 on 2014-09-01
I am starting my computer running the 3.2 kernel. Be back soon. Please stand by if you can.

---

### Post by deldin on 2014-09-01
```

miriam@supercomputer-di-miriam:~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916$ cd ~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916
miriam@supercomputer-di-miriam:~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916$ 

```

```

miriam@supercomputer-di-miriam:~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916$ make clean
make -C UTIL/ clean
make[1]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL'
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[2]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.cmd .*.flags .*.d
rm -f ../../os/linux/*.o *.ko *.mod.o *.mod.c
rm -f ../../os/linux/.*.cmd .*.flags .*.d
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.cmd .*.flags .*.d
rm -f ../../rate_ctrl/*.o
rm -f ../../rate_ctrl/.*.cmd .*.flags .*.d
rm -f ../../ate/common/*.o
rm -f ../../ate/common/.*.cmd .*.flags .*.d
rm -f ../../ate/chips/*.o
rm -f ../../ate/chips/.*.cmd .*.flags .*.d
rm -f ../../phy/*.o
rm -f ../../phy/.*.cmd .*.flags .*.d
rm -f ../../mac/*.o
rm -f ../../mac/.*.cmd .*.flags .*.d
rm -f ../../mcu/*.o
rm -f ../../mcu/.*.cmd .*.flags .*.d
rm -f ../../mgmt/*.o
rm -f ../../mgmt/.*.cmd .*.flags .*.d
rm -f ../../naf/*.o
rm -f ../../naf/.*.cmd .*.flags .*.d
rm -f ../../sta/*.o
rm -f ../../sta/.*.cmd .*.flags .*.d
make[2]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux'
rm -rf os/linux/Makefile
make[1]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL'
make -C MODULE/ clean
make[1]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE'
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[2]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.cmd .*.flags .*.d
rm -f ../../os/linux/*.o *.ko *.mod.o *.mod.c
rm -f ../../os/linux/.*.cmd .*.flags .*.d
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.cmd .*.flags .*.d
rm -f ../../rate_ctrl/*.o
rm -f ../../rate_ctrl/.*.cmd .*.flags .*.d
rm -f ../../ate/common/*.o
rm -f ../../ate/common/.*.cmd .*.flags .*.d
rm -f ../../ate/chips/*.o
rm -f ../../ate/chips/.*.cmd .*.flags .*.d
rm -f ../../phy/*.o
rm -f ../../phy/.*.cmd .*.flags .*.d
rm -f ../../mac/*.o
rm -f ../../mac/.*.cmd .*.flags .*.d
rm -f ../../mcu/*.o
rm -f ../../mcu/.*.cmd .*.flags .*.d
rm -f ../../mgmt/*.o
rm -f ../../mgmt/.*.cmd .*.flags .*.d
rm -f ../../naf/*.o
rm -f ../../naf/.*.cmd .*.flags .*.d
rm -f ../../sta/*.o
rm -f ../../sta/.*.cmd .*.flags .*.d
make[2]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux'
rm -rf os/linux/Makefile
make[1]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE'
make -C NETIF/ clean
make[1]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF'
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[2]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.cmd .*.flags .*.d
rm -f ../../os/linux/*.o *.ko *.mod.o *.mod.c
rm -f ../../os/linux/.*.cmd .*.flags .*.d
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.cmd .*.flags .*.d
rm -f ../../rate_ctrl/*.o
rm -f ../../rate_ctrl/.*.cmd .*.flags .*.d
rm -f ../../ate/common/*.o
rm -f ../../ate/common/.*.cmd .*.flags .*.d
rm -f ../../ate/chips/*.o
rm -f ../../ate/chips/.*.cmd .*.flags .*.d
rm -f ../../phy/*.o
rm -f ../../phy/.*.cmd .*.flags .*.d
rm -f ../../mac/*.o
rm -f ../../mac/.*.cmd .*.flags .*.d
rm -f ../../mcu/*.o
rm -f ../../mcu/.*.cmd .*.flags .*.d
rm -f ../../mgmt/*.o
rm -f ../../mgmt/.*.cmd .*.flags .*.d
rm -f ../../naf/*.o
rm -f ../../naf/.*.cmd .*.flags .*.d
rm -f ../../sta/*.o
rm -f ../../sta/.*.cmd .*.flags .*.d
make[2]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux'
rm -rf os/linux/Makefile
make[1]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF'
miriam@supercomputer-di-miriam:~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916$ 

```

```

miriam@supercomputer-di-miriam:~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916$ make
make -C UTIL/ osutil
make[1]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL'
cp -f os/linux/Makefile.6.util /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/Makefile
make -C /lib/modules/3.2.0-68-generic/build SUBDIRS=/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-68-generic'
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../common/rt_os_util.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux_symb.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_usb_util.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_usb_util.c: In function ‘rausb_autopm_put_interface’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_usb_util.c:107:7: warning: unused variable ‘pm_usage_cnt’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_usb_util.c: In function ‘rausb_autopm_get_interface’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_usb_util.c:138:7: warning: unused variable ‘pm_usage_cnt’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_usb_util.c:144:1: warning: control reaches end of non-void function [-Wreturn-type]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsUsDelay’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c:182:8: warning: unused variable ‘i’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpDrvAllRFPrint’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c:2177:4: warning: passing argument 2 of ‘file_w->f_op->write’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c:2177:4: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c:2162:22: warning: unused variable ‘macValue’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c:2162:9: warning: unused variable ‘macAddr’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRelease’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c:2298:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsFreeSpinLock’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/../../os/linux/rt_linux.c:4317:8: warning: assignment from incompatible pointer type [enabled by default]
  LD [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/mtutil7601Usta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/mtutil7601Usta.mod.o
  LD [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux/mtutil7601Usta.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-68-generic'
make[1]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL'
/bin/sh cp_util.sh

make -C MODULE/ build_tools
make[1]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE'
make -C tools
make[2]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/tools'
gcc -g bin2h.c -o bin2h
make[2]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/tools'
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/tools/bin2h
make[1]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE'
make -C MODULE/ osdrv
make[1]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE'
cp -f os/linux/Makefile.6 /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/Makefile
make -C /lib/modules/3.2.0-68-generic/build SUBDIRS=/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-68-generic'
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:131:8: warning: type defaults to ‘int’ in declaration of ‘pWirelessIWscEventText’ [-Wimplicit-int]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:132:2: warning: initialization from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:132:2: warning: (near initialization for ‘pWirelessIWscEventText[0]’) [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:133:2: warning: initialization from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:133:2: warning: (near initialization for ‘pWirelessIWscEventText[1]’) [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:134:2: warning: initialization from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:134:2: warning: (near initialization for ‘pWirelessIWscEventText[2]’) [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:135:2: warning: initialization from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:135:2: warning: (near initialization for ‘pWirelessIWscEventText[3]’) [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:136:2: warning: initialization from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:136:2: warning: (near initialization for ‘pWirelessIWscEventText[4]’) [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c: In function ‘announce_802_3_packet’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_profile.c:472:16: warning: unused variable ‘pAd’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/assoc.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/auth.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sync.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sync.c:2345:12: warning: passing argument 8 of ‘StaAddMacTableEntry’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rtmp.h:9640:9: note: expected ‘struct IE_LISTS *’ but argument is of type ‘struct BCN_IE_LIST *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sync.c:2466:13: warning: passing argument 8 of ‘StaAddMacTableEntry’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rtmp.h:9640:9: note: expected ‘struct IE_LISTS *’ but argument is of type ‘struct BCN_IE_LIST *’
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sanity.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/rtmp_data.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/rtmp_data.c:740:4: warning: passing argument 2 of ‘MacTableLookup’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rtmp.h:10236:18: note: expected ‘UCHAR *’ but argument is of type ‘UCHAR (*)[6]’
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/connect.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/wpa.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_cfg.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_cfg.c: In function ‘Set_WscUUIDE_Proc’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_cfg.c:1697:11: warning: unused variable ‘Wsc_Uuid_Str’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_cfg.c: In function ‘RTMPIoctlRF’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_cfg.c:6712:3: warning: passing argument 2 of ‘RtmpDrvAllRFPrint’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:656:6: note: expected ‘UINT32 *’ but argument is of type ‘PSTRING’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_cfg.c:6562:22: warning: unused variable ‘rf_bank’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_ioctl_siwgenie’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_cfg.c:8944:13: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/crypt_md5.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/crypt_aes.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/mlme.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/mlme.c: In function ‘AsicRxAntEvalTimeout’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/mlme.c:6340:45: warning: unused variable ‘rssi_diff’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_wep.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/action.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data.c: In function ‘CmdRspEventCallbackHandle’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data.c:3513:8: warning: unused variable ‘Ret’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data.c: In function ‘StopDmaTx’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data.c:4073:8: warning: unused variable ‘IdleNums’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data.c:4071:20: warning: unused variable ‘UsbCfg’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtmp_init.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtmp_init.c:1039:9: warning: unused variable ‘i’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtmp_init.c: In function ‘NICInitializeAdapter’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtmp_init.c:1350:22: warning: unused variable ‘GloCfg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtmp_init.c: In function ‘NICInitializeAsic’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtmp_init.c:1417:11: warning: unused variable ‘KeyIdx’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtmp_init.c:1724:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_aes.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_sync.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/eeprom.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/eeprom.c: In function ‘RtmpChipOpsEepromHook’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/eeprom.c:34:9: warning: unused variable ‘e2p_csr’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_sanity.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_sanity.c: In function ‘PeerBeaconAndProbeRspSanity_Old’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_sanity.c:902:12: warning: passing argument 5 of ‘WscGetDataFromPeerByTag’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rtmp.h:8297:9: note: expected ‘PUCHAR’ but argument is of type ‘USHORT *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_sanity.c:875:12: warning: unused variable ‘DataLen’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_sanity.c: In function ‘PeerBeaconAndProbeRspSanity’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_sanity.c:1553:11: warning: passing argument 5 of ‘WscGetDataFromPeerByTag’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rtmp.h:8297:9: note: expected ‘PUCHAR’ but argument is of type ‘USHORT *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_sanity.c:1526:11: warning: unused variable ‘DataLen’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_info.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_info.c: In function ‘Set_WscVendorPinCode_Proc’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_info.c:1295:14: warning: unused variable ‘apidx’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_cfg.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_cfg.c: In function ‘wmode_valid_and_correct’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_cfg.c:301:8: warning: unused variable ‘mode’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_cfg.c: At top level:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_cfg.c:286:16: warning: ‘wmode_valid’ defined but not used [-Wunused-function]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_radar.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/spectrum.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rt_channel.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_profile.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_profile.c: In function ‘rtmp_read_multest_from_file’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_profile.c:4983:23: warning: unused variable ‘pWdsEntry’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_asic.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/scan.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/uapsd.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/ps.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/txpower.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mac/rtmp_mac.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mgmt/mgmt_hw.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mgmt/mgmt_entrytb.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../phy/rtmp_phy.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../phy/rtmp_phy.c: In function ‘NICInitBBP’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../phy/rtmp_phy.c:39:8: warning: unused variable ‘R0’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../phy/rlt_phy.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../phy/rlt_rf.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/ba_action.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mgmt/mgmt_ht.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc.c: In function ‘WscM2DTimeOutAction’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc.c:387:16: warning: unused variable ‘pAd’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc.c: In function ‘WscBuildBeaconIE’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc.c:5337:9: warning: unused variable ‘respType’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c: In function ‘WscProcessCredential’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:472:5: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:480:5: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:487:5: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:509:7: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:509:7: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:509:7: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:509:7: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:515:7: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:515:7: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:515:7: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:515:7: warning: passing argument 1 of ‘RtmpOsGetUnaligned’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rt_os_util.h:672:8: note: expected ‘UINT16 *’ but argument is of type ‘unsigned int *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c: In function ‘BuildMessageM8’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:2317:10: warning: passing argument 3 of ‘AppendWSCTLV’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_tlv.c:178:5: note: expected ‘UCHAR *’ but argument is of type ‘USHORT *’
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/crypt_biginteger.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/crypt_dh.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/wsc_v2.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_symb.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_wpa_adhoc.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_iwsc.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_iwsc.c: In function ‘IWSC_PeerAction’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_iwsc.c:1111:13: warning: unused variable ‘len’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_iwsc.c:1182:27: warning: unused variable ‘len’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_iwsc.c: In function ‘IWSC_BuildDevQueryFrame’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../sta/sta_iwsc.c:1788:11: warning: unused variable ‘tempVal’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c: In function ‘DefaultATEAsicAdjustTxPower’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c:309:24: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c:217:21: warning: unused variable ‘TmpValue’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c:217:8: warning: unused variable ‘RFValue’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c: In function ‘ATEAsicTemperCompensation’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c:3490:3: warning: passing argument 1 of ‘pATEInfo->pChipStruct->TemperCompensation’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c:3490:3: note: expected ‘struct _RTMP_ADAPTER **’ but argument is of type ‘PRTMP_ADAPTER’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c: In function ‘Set_ATE_Load_E2P_From_Buf_Proc’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c:4309:3: warning: passing argument 2 of ‘rt_ee_write_all’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c:784:6: note: expected ‘USHORT *’ but argument is of type ‘UCHAR *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c: In function ‘Set_ATE_Cal_Free_Info_Proc’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c:4324:16: warning: unused variable ‘ret’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c: In function ‘Set_ATE_Load_E2P_Proc’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c:4284:1: warning: the frame size of 1036 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c: In function ‘Set_ATE_Read_E2P_Proc’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_ate.c:4355:1: warning: the frame size of 1028 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_qa.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_qa.c: In function ‘DO_RACFG_CMD_ATE_E2PROM_WRITE_BULK’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_qa.c:1678:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_qa.c: In function ‘DO_RACFG_CMD_ATE_E2PROM_READ_BULK’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_qa.c:1645:1: warning: the frame size of 1032 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_qa.c: In function ‘DO_RACFG_CMD_E2PROM_WRITE_ALL’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/rt_qa.c:757:1: warning: the frame size of 1032 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_mac_usb.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_mac_usb.c:550:31: warning: initialization from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_mac_usb.c: In function ‘RT28XXDMAEnable’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_mac_usb.c:1359:20: warning: unused variable ‘UsbCfg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_mac_usb.c:1358:22: warning: unused variable ‘GloCfg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_mac_usb.c: In function ‘RT28xxUsbAsicRadioOn’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_mac_usb.c:2036:22: warning: unused variable ‘GloCfg’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data_usb.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data_usb.c: In function ‘ComposeNullFrame’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data_usb.c:258:2: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data_usb.c: At top level:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/cmm_data_usb.c:201:13: warning: ‘rlt_usb_update_txinfo’ defined but not used [-Wunused-function]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtusb_io.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtusb_io.c: In function ‘RTUSBWriteEEPROM’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtusb_io.c:684:9: warning: unused variable ‘Value’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtusb_data.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtusb_bulk.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtusb_bulk.c: In function ‘RTUSBCancelPendingBulkOutIRP’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rtusb_bulk.c:1701:15: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_usb.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_usb.c: In function ‘cmd_rsp_event_tasklet’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../os/linux/rt_usb.c:560:22: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/ee_prom.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/ee_efuse.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c: In function ‘USBLoadIVB’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c:69:9: warning: unused variable ‘Temp’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c:68:9: warning: unused variable ‘Index’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c:67:9: warning: unused variable ‘Value’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c:66:9: warning: unused variable ‘i’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c: In function ‘USBLoadFirmwareToAndes’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c:106:19: warning: unused variable ‘MCtrl’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c:105:20: warning: unused variable ‘UsbCfg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c: In function ‘MCUCtrlExit’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c:600:8: warning: unused variable ‘Ret’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c: In function ‘GetCmdRspNum’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_and.c:643:16: warning: unused variable ‘IrqFlags’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCUBurstWrite’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.c:33:2: warning: passing argument 3 of ‘RTUSBMultiWrite_nBytes’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/rtmp.h:9301:10: note: expected ‘PUCHAR’ but argument is of type ‘UINT32 *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.c: In function ‘ChipOpsMCUHook’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.c:65:25: warning: assignment from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.c:72:25: warning: assignment from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.c:73:27: warning: assignment from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCURandomWrite’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.c:42:1: warning: control reaches end of non-void function [-Wreturn-type]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCUBurstWrite’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_mcu.c:34:1: warning: control reaches end of non-void function [-Wreturn-type]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mcu/rtmp_M51.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/rt_rf.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601_INIT_CAL’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:889:8: warning: unused variable ‘Temperature’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘NICInitMT7601RFRegisters’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:1007:9: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘NICInitMT7601MacRegisters’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:1045:9: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘NICInitMT7601BbpRegisters’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:1087:6: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601_ChipSwitchChannel’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:1385:3: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:1214:6: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601DisableTxRx’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:1440:3: warning: ‘return’ with no value, in function returning non-void [-Wreturn-type]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601UsbAsicRadioOff’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:1668:9: warning: unused variable ‘Value’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601UsbAsicRadioOn’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:1733:16: warning: unused variable ‘pChipOps’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:1732:22: warning: unused variable ‘GloCfg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601_ReadChannelPwr’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:1848:10: warning: unused variable ‘bUseDefault’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601AsicTemperatureCompensation’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:2225:6: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601_EnableTSSI’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:2421:9: warning: unused variable ‘ret’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:2420:15: warning: unused variable ‘BBPReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:2420:8: warning: unused variable ‘RFReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601_InitDesiredTSSITable’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:2554:16: warning: unused variable ‘offset’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:2554:9: warning: unused variable ‘index’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601_GetTssiCompensationParam’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:2625:9: warning: unused variable ‘ret’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:2624:7: warning: unused variable ‘count’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:2618:8: warning: unused variable ‘RFReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601_AsicTxAlcGetAutoAgcOffset’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:2892:8: warning: unused variable ‘BBPReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c: In function ‘MT7601_Init’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../chips/mt7601.c:3342:24: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../mac/ral_omac.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATEAsicSwitchChannel’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:58:6: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601_Set_ATE_TX_BW_Proc’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:279:4: warning: passing argument 3 of ‘MT7601_BBP_write’ makes integer from pointer without a cast [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/chip/rtmp_phy.h:624:13: note: expected ‘UCHAR’ but argument is of type ‘UCHAR *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:318:6: warning: passing argument 3 of ‘MT7601_BBP_write’ makes integer from pointer without a cast [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/include/chip/rtmp_phy.h:624:13: note: expected ‘UCHAR’ but argument is of type ‘UCHAR *’
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATEGetTssiCompensationParam’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:403:7: warning: unused variable ‘count’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:398:8: warning: unused variable ‘RFReg’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATEAsicTxAlcGetAutoAgcOffset’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:660:12: warning: unused variable ‘pATEInfo’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATEAsicAdjustTxPower’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:816:45: warning: unused variable ‘CfgOfTxPwrCtrlOverMAC’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:815:8: warning: unused variable ‘TotalDeltaPower’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:814:8: warning: unused variable ‘DeltaPowerByBbpR1’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:813:8: warning: unused variable ‘TxAgcCompensate’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:812:8: warning: unused variable ‘DeltaPwr’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601_Set_ATE_TX_FREQ_OFFSET_Proc’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:843:8: warning: unused variable ‘PreRFValue’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:841:8: warning: unused variable ‘R4’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATERxVGAInit’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:876:7: warning: unused variable ‘LNAGain’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:874:12: warning: unused variable ‘pATEInfo’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATEAsicSetTxRxPath’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:890:8: warning: unused variable ‘BbpValue’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c: At top level:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:909:2: warning: initialization from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/chips/mt7601_ate.c:909:2: warning: (near initialization for ‘MT7601ATE.TemperCompensation’) [enabled by default]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/ate_usb.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/ate_usb.c: In function ‘ATEResetBulkOut’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../ate/common/ate_usb.c:555:29: warning: initialization from incompatible pointer type [enabled by default]
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/frq_cal.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/frq_cal.c: In function ‘FrequencyCalibrationMode’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/../../common/frq_cal.c:130:9: warning: unused variable ‘PreRFValue’ [-Wunused-variable]
  LD [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/mt7601Usta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/mt7601Usta.mod.o
  LD [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE/os/linux/mt7601Usta.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-68-generic'
make[1]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/MODULE'
/bin/sh cp_module.sh

make -C NETIF/ osnet
make[1]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF'
cp -f os/linux/Makefile.6.netif /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/Makefile
make -C /lib/modules/3.2.0-68-generic/build SUBDIRS=/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-68-generic'
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/../../os/linux/usb_main_dev.o
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/../../os/linux/usb_main_dev.c: In function ‘rt2870_suspend’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/../../os/linux/usb_main_dev.c:383:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/../../os/linux/usb_main_dev.c: In function ‘rt2870_resume’:
/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/../../os/linux/usb_main_dev.c:439:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
  LD [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/mtnet7601Usta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/mtnet7601Usta.mod.o
  LD [M]  /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF/os/linux/mtnet7601Usta.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-68-generic'
make[1]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/NETIF'
miriam@supercomputer-di-miriam:~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916$ 

```

```

miriam@supercomputer-di-miriam:~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916$ sudo make install
make -C UTIL/ install
make[1]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL'
make -C /home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux -f Makefile.6 install
make[2]: Entering directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux'
make[2]: Makefile.6: No such file or directory
make[2]: *** No rule to make target `Makefile.6'.  Stop.
make[2]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL/os/linux'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/miriam/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916/UTIL'
make: *** [install] Error 2
miriam@supercomputer-di-miriam:~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916$ 


```

---

### Post by deldin on 2014-09-01
ok I'm here
thanks

---

### Post by chili555 on 2014-09-01
> **deldin said:**
> ok I'm here
thanksI've used all my magical powers and played with this for 25  minutes and all I get are errors, warnings and more errors. I can't even get the file to download from here: [http://www.mediatek.com/en/downloads/mt7601u-usb/](http://www.mediatek.com/en/downloads/mt7601u-usb/)

I tried a version on github with the same dismal result. Where did you get the file? If from the install CD, were there other files on it?

While you answer, I am going to try a 3.8 kernel.

Edit: Attempting to compile on 3.8 has the same horrible result. I regret I know of no way to get the MT7601u devices going.

Want to borrow my real big hammer? [http://ace.imageg.net/graphics/product_images/pACE3-5734467dt.jpg](http://ace.imageg.net/graphics/product_images/pACE3-5734467dt.jpg)

---

### Post by deldin on 2014-09-01
yes, I have the install CD. For linux there are 4 files DPA_MT7601U_LinuxSTA_3.0.0.4_20130916.tar.bz2, DPA_RT5572_LinuxSTA_2.6.1.4_20121211.tar.bz2, MT7601U_LinuxAP_3.0.0.1_20130802.tar.bz2, RT5572_RT5372_Linux_AP_V2.7.1.1_Beta_DPA_20121113.tar.bz2 and 3 pdf files with instructions

---

### Post by chili555 on 2014-09-01
I suggest you also try this:> MT7601U_LinuxAP_3.0.0.1_20130802.tar.bz2I'd also like to know more about you device:```
lsusb
```

---

### Post by deldin on 2014-09-02
I try MT7601U_LinuxAP_3.0.0.1_20130802.tar.bz2 

```

miriam@supercomputer-di-miriam:~/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802$ make
make -C tools
make[1]: Entering directory `/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/tools'
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/tools/bin2h
cp -f os/linux/Makefile.6 /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/Makefile
make -C /lib/modules/3.2.0-68-generic/build SUBDIRS=/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-68-generic'
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_profile.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_profile.c: In function ‘announce_802_3_packet’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_profile.c:437:16: warning: unused variable ‘pAd’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_mbss.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap.c: In function ‘APStartUp’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap.c:144:10: warning: unused variable ‘Value’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap.c:143:10: warning: unused variable ‘offset’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap.c:789:1: warning: the frame size of 1080 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_assoc.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_auth.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_connect.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_mlme.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_sanity.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_sync.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_wpa.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_data.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_autoChSel.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_qload.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c: In function ‘RTMPAPSetInformation’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:1929:6: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:1931:6: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘RTMP_OS_PID’ [-Wformat]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:1946:6: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:1948:6: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘RTMP_OS_PID’ [-Wformat]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c: In function ‘Show_Sat_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:5909:2: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘INT64’ [-Wformat]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c: In function ‘Show_Sat_Reset_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:6039:2: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘INT64’ [-Wformat]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c: In function ‘RTMPAPIoctlRF’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:7263:3: warning: passing argument 2 of ‘RtmpDrvAllRFPrint’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/include/rt_os_util.h:656:6: note: expected ‘UINT32 *’ but argument is of type ‘PSTRING’
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:7225:10: warning: unused variable ‘rfValue’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:7223:13: warning: unused variable ‘ptr’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:7220:22: warning: unused variable ‘rf_bank’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:7219:13: warning: unused variable ‘value’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:7218:13: warning: unused variable ‘this_char’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c: In function ‘Set_WscV2Support_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:9795:8: warning: unused variable ‘IsAPConfigured’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c: In function ‘Set_IappPID_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:9957:2: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c: In function ‘Set_TestTxFrameProc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:11451:9: warning: unused variable ‘TempLen’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c: In function ‘Set_TestTxFrame2Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:11708:10: warning: unused variable ‘Value1’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c: In function ‘Set_TestTxFrame3Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:11779:10: warning: unused variable ‘Value1’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c: In function ‘Set_TestTxFrame4Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:11850:10: warning: unused variable ‘Value1’ [-Wunused-variable]
In file included from /usr/src/linux-headers-3.2.0-68-generic/arch/x86/include/asm/uaccess.h:573:0,
                 from /usr/src/linux-headers-3.2.0-68-generic/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-3.2.0-68-generic/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:357,
                 from /usr/src/linux-headers-3.2.0-68-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/include/os/rt_linux.h:27,
                 from /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/include/rtmp_os.h:42,
                 from /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/include/rtmp_comm.h:66,
                 from /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/include/rt_config.h:36,
                 from /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:28:
In function ‘copy_from_user’,
    inlined from ‘RTMPAPSetInformation’ at /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:1923:23:
/usr/src/linux-headers-3.2.0-68-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
In function ‘copy_from_user’,
    inlined from ‘RTMPAPSetInformation’ at /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:1940:23:
/usr/src/linux-headers-3.2.0-68-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
In function ‘copy_from_user’,
    inlined from ‘RTMPAPSetInformation’ at /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_cfg.c:1953:25:
/usr/src/linux-headers-3.2.0-68-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/crypt_md5.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/crypt_aes.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/mlme.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_wep.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/action.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data.c: In function ‘CmdRspEventCallbackHandle’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data.c:2958:8: warning: unused variable ‘Ret’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data.c: In function ‘StopDmaTx’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data.c:3518:8: warning: unused variable ‘IdleNums’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data.c:3516:20: warning: unused variable ‘UsbCfg’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtmp_init.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtmp_init.c:1003:9: warning: unused variable ‘i’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtmp_init.c: In function ‘NICInitializeAdapter’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtmp_init.c:1209:22: warning: unused variable ‘GloCfg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtmp_init.c: In function ‘NICInitializeAsic’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtmp_init.c:1276:11: warning: unused variable ‘KeyIdx’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtmp_init.c:1563:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_aes.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_sync.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/eeprom.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/eeprom.c: In function ‘RtmpChipOpsEepromHook’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/eeprom.c:34:9: warning: unused variable ‘e2p_csr’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_info.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_info.c: In function ‘Set_DebugFunc_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_info.c:1251:2: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘const char *’ [-Wformat]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_info.c:1251:2: warning: too many arguments for format [-Wformat-extra-args]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_info.c: In function ‘set_rf’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_info.c:6047:3: warning: format ‘%x’ expects argument of type ‘unsigned int *’, but argument 5 has type ‘UCHAR *’ [-Wformat]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_cfg.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_cfg.c: In function ‘wmode_valid_and_correct’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_cfg.c:287:8: warning: unused variable ‘mode’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_cfg.c: In function ‘RT_CfgSetMbssWirelessMode’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_cfg.c:432:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘LONG’ [-Wformat]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_radar.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/spectrum.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rt_channel.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_profile.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_profile.c: In function ‘rtmp_read_multest_from_file’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_profile.c:4161:23: warning: unused variable ‘pWdsEntry’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_asic.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/scan.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/scan.c: In function ‘ScanNextChannel’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/scan.c:317:8: warning: unused variable ‘ImprovedScan_MaxScanChannelCnt’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/uapsd.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/uapsd.c: In function ‘RtmpAsicSleepHandle’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/uapsd.c:186:10: warning: unused variable ‘FlgCanAsicSleep’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/ps.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/txpower.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/txpower.c: In function ‘AsicAdjustTxPower’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/txpower.c:257:8: warning: unused variable ‘Rssi’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mac/rtmp_mac.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mgmt/mgmt_hw.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mgmt/mgmt_entrytb.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../phy/rtmp_phy.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../phy/rtmp_phy.c: In function ‘NICInitBBP’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../phy/rtmp_phy.c:39:8: warning: unused variable ‘R0’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../phy/rlt_phy.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../phy/rlt_rf.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/ba_action.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mgmt/mgmt_ht.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/wsc.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/wsc.c: In function ‘WscPBCExec’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/wsc.c:6184:8: warning: unused variable ‘CurOpMode’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/wsc.c: In function ‘WscPBCBssTableSort’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/wsc.c:6565:11: warning: unused variable ‘CurOpMode’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/wsc_tlv.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/crypt_biginteger.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/crypt_dh.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/wsc_v2.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/wsc_ufd.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c: In function ‘DefaultATEAsicAdjustTxPower’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c:309:24: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c:217:21: warning: unused variable ‘TmpValue’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c:217:8: warning: unused variable ‘RFValue’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c: In function ‘ATEAsicTemperCompensation’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c:3415:3: warning: passing argument 1 of ‘pATEInfo->pChipStruct->TemperCompensation’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c:3415:3: note: expected ‘struct _RTMP_ADAPTER **’ but argument is of type ‘PRTMP_ADAPTER’
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c: In function ‘Set_ATE_Load_E2P_From_Buf_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c:4234:3: warning: passing argument 2 of ‘rt_ee_write_all’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c:784:6: note: expected ‘USHORT *’ but argument is of type ‘UCHAR *’
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c: In function ‘Set_ATE_Cal_Free_Info_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c:4249:16: warning: unused variable ‘ret’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c: In function ‘Set_ATE_Load_E2P_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c:4209:1: warning: the frame size of 1044 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c: In function ‘Set_ATE_Read_E2P_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_ate.c:4280:1: warning: the frame size of 1028 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_qa.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_qa.c: In function ‘DO_RACFG_CMD_ATE_E2PROM_WRITE_BULK’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_qa.c:1678:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_qa.c: In function ‘DO_RACFG_CMD_ATE_E2PROM_READ_BULK’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_qa.c:1645:1: warning: the frame size of 1028 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_qa.c: In function ‘DO_RACFG_CMD_E2PROM_WRITE_ALL’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/rt_qa.c:757:1: warning: the frame size of 1032 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ap/ap_mbss_inf.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rt_os_util.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/ap_ioctl.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_linux.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsUsDelay’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_linux.c:183:8: warning: unused variable ‘i’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpDrvAllRFPrint’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_linux.c:1886:4: warning: passing argument 2 of ‘file_w->f_op->write’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_linux.c:1886:4: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_linux.c:1871:22: warning: unused variable ‘macValue’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_linux.c:1871:9: warning: unused variable ‘macAddr’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRelease’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_linux.c:2007:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_mac_usb.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_mac_usb.c:550:31: warning: initialization from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_mac_usb.c: In function ‘RT28XXDMAEnable’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_mac_usb.c:1359:20: warning: unused variable ‘UsbCfg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_mac_usb.c:1358:22: warning: unused variable ‘GloCfg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_mac_usb.c: In function ‘RT28xxUsbAsicRadioOn’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_mac_usb.c:1939:22: warning: unused variable ‘GloCfg’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data_usb.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data_usb.c: In function ‘ComposeNullFrame’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data_usb.c:222:2: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data_usb.c: At top level:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/cmm_data_usb.c:201:13: warning: ‘rlt_usb_update_txinfo’ defined but not used [-Wunused-function]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtusb_io.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtusb_io.c: In function ‘RTUSBWriteEEPROM’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtusb_io.c:684:9: warning: unused variable ‘Value’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtusb_data.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtusb_bulk.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtusb_bulk.c: In function ‘RTUSBCancelPendingBulkOutIRP’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtusb_bulk.c:1677:15: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_usb.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_usb.c: In function ‘cmd_rsp_event_tasklet’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_usb.c:552:22: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/ee_prom.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/ee_efuse.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c: In function ‘USBLoadIVB’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c:69:9: warning: unused variable ‘Temp’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c:68:9: warning: unused variable ‘Index’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c:67:9: warning: unused variable ‘Value’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c:66:9: warning: unused variable ‘i’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c: In function ‘USBLoadFirmwareToAndes’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c:106:19: warning: unused variable ‘MCtrl’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c:105:20: warning: unused variable ‘UsbCfg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c: In function ‘MCUCtrlExit’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c:600:8: warning: unused variable ‘Ret’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c: In function ‘GetCmdRspNum’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_and.c:643:16: warning: unused variable ‘IrqFlags’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCUBurstWrite’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.c:33:2: warning: passing argument 3 of ‘RTUSBMultiWrite_nBytes’ from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/include/rtmp.h:8255:10: note: expected ‘PUCHAR’ but argument is of type ‘UINT32 *’
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.c: In function ‘ChipOpsMCUHook’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.c:65:25: warning: assignment from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.c:72:25: warning: assignment from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.c:73:27: warning: assignment from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCURandomWrite’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.c:42:1: warning: control reaches end of non-void function [-Wreturn-type]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCUBurstWrite’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_mcu.c:34:1: warning: control reaches end of non-void function [-Wreturn-type]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mcu/rtmp_M51.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rt_rf.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601_INIT_CAL’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:889:8: warning: unused variable ‘Temperature’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘NICInitMT7601RFRegisters’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:1005:9: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘NICInitMT7601MacRegisters’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:1043:9: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘NICInitMT7601BbpRegisters’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:1085:6: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601_ChipSwitchChannel’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:1344:3: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:1174:6: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601DisableTxRx’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:1399:3: warning: ‘return’ with no value, in function returning non-void [-Wreturn-type]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601UsbAsicRadioOff’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:1627:9: warning: unused variable ‘Value’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601UsbAsicRadioOn’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:1692:16: warning: unused variable ‘pChipOps’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:1691:22: warning: unused variable ‘GloCfg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601_ReadChannelPwr’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:1786:10: warning: unused variable ‘bUseDefault’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601AsicTemperatureCompensation’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:2163:6: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601_EnableTSSI’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:2359:9: warning: unused variable ‘ret’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:2358:15: warning: unused variable ‘BBPReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:2358:8: warning: unused variable ‘RFReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601_InitDesiredTSSITable’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:2492:16: warning: unused variable ‘offset’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:2492:9: warning: unused variable ‘index’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601_GetTssiCompensationParam’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:2563:9: warning: unused variable ‘ret’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:2562:7: warning: unused variable ‘count’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:2556:8: warning: unused variable ‘RFReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601_AsicTxAlcGetAutoAgcOffset’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:2830:8: warning: unused variable ‘BBPReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c: In function ‘MT7601_Init’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../chips/mt7601.c:3262:24: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../mac/ral_omac.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATEAsicSwitchChannel’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:58:6: warning: unused variable ‘IdReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601_Set_ATE_TX_BW_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:280:4: warning: passing argument 3 of ‘MT7601_BBP_write’ makes integer from pointer without a cast [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/include/chip/rtmp_phy.h:624:13: note: expected ‘UCHAR’ but argument is of type ‘UCHAR *’
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:319:6: warning: passing argument 3 of ‘MT7601_BBP_write’ makes integer from pointer without a cast [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/include/chip/rtmp_phy.h:624:13: note: expected ‘UCHAR’ but argument is of type ‘UCHAR *’
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATEGetTssiCompensationParam’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:404:7: warning: unused variable ‘count’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:399:8: warning: unused variable ‘RFReg’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATEAsicTxAlcGetAutoAgcOffset’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:661:12: warning: unused variable ‘pATEInfo’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATEAsicAdjustTxPower’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:817:45: warning: unused variable ‘CfgOfTxPwrCtrlOverMAC’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:816:8: warning: unused variable ‘TotalDeltaPower’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:815:8: warning: unused variable ‘DeltaPowerByBbpR1’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:814:8: warning: unused variable ‘TxAgcCompensate’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:813:8: warning: unused variable ‘DeltaPwr’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601_Set_ATE_TX_FREQ_OFFSET_Proc’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:844:8: warning: unused variable ‘PreRFValue’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:842:8: warning: unused variable ‘R4’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATERxVGAInit’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:876:7: warning: unused variable ‘LNAGain’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:874:12: warning: unused variable ‘pATEInfo’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c: In function ‘MT7601ATEAsicSetTxRxPath’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:890:8: warning: unused variable ‘BbpValue’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c: At top level:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:909:2: warning: initialization from incompatible pointer type [enabled by default]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/chips/mt7601_ate.c:909:2: warning: (near initialization for ‘MT7601ATE.TemperCompensation’) [enabled by default]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/ate_usb.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/ate_usb.c: In function ‘ATEResetBulkOut’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../ate/common/ate_usb.c:555:29: warning: initialization from incompatible pointer type [enabled by default]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/usb_main_dev.o
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/usb_main_dev.c: In function ‘rt2870_suspend’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/usb_main_dev.c:377:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/usb_main_dev.c: In function ‘rt2870_resume’:
/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../os/linux/usb_main_dev.c:430:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/../../common/frq_cal.o
  LD [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/mt7601Uap.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/mt7601Uap.mod.o
  LD [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/mt7601Uap.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-68-generic'
cp -f /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/mt7601Uap.ko /tftpboot
cp: cannot create regular file `/tftpboot': Permission denied
make: *** [LINUX] Error 1

```

```

miriam@supercomputer-di-miriam:~/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802$ sudo make install
[sudo] password for miriam: 
make -C /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux'
rm -rf /etc/Wireless/RT2870AP
mkdir /etc/Wireless/RT2870AP
cp /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/RT2870AP.dat /etc/Wireless/RT2870AP/.
install -d /lib/modules/3.2.0-68-generic/kernel/drivers/net/wireless/
install -m 644 -c mt7601Uap.ko /lib/modules/3.2.0-68-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-68-generic
make[1]: Leaving directory `/home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux'

```

```

miriam@supercomputer-di-miriam:~/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802$ sudo modprobe mt7601Usta
FATAL: Module mt7601Usta not found.
miriam@supercomputer-di-miriam:~/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802$ 

```

---

### Post by deldin on 2014-09-02
```

miriam@supercomputer-di-miriam:~/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:7601 Ralink Technology, Corp. 
miriam@supercomputer-di-miriam:~/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802$ 

```

---

### Post by chili555 on 2014-09-02
The name of the module is...> LD [M]  /home/miriam/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802/os/linux/[COLOR="#FF0000"]mt7601Uap[/COLOR].koSo that's why it couldn't find mt7601Usta. Please try:```
sudo modprobe mt7601Uap
```I sure hope the 'ap' part doesn't mean it is written for an access point; i.e. router, and only works in Master mode.

---

### Post by deldin on 2014-09-03
```

miriam@supercomputer-di-miriam:~$ sudo modprobe mt7601Uap
[sudo] password for miriam: 
miriam@supercomputer-di-miriam:~$

```

---

### Post by deldin on 2014-09-03
it doesn't work :(

---

### Post by deldin on 2014-09-03
```

miriam@supercomputer-di-miriam:~$ iwconfig
lo        no wireless extensions.

ra0       RTWIFI SoftAP  
          
eth0      no wireless extensions.

miriam@supercomputer-di-miriam:~$

```

---

### Post by chili555 on 2014-09-03
I suspect it is, indeed, a driver for an access point and will do no good here. I suggest you remove it:```
cd ~/Scrivania/MT7601U_LinuxAP_3.0.0.1_20130802
sudo make uninstall
sudo modprobe -r  mt7601Uap
```I finally was able to download the driver from Mediatek:```
cd ~/Scrivania
wget http://www.mediatek.com/AmazonS3/Downloads/linux/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913.tar.bz2
```Once the file downloads, right-click it and select 'Extract Here.' ```
cd DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
make
sudo make install
sudo modprobe mt7601Usta
iwconfig
```

---

### Post by deldin on 2014-09-05
yesssssssss

it works   \\:D/

thank you very much

---

### Post by deldin on 2014-09-05
you are super =d>

---

### Post by chili555 on 2014-09-05
I appreciate your kind words.

You have compiled the driver for your current kernel version only. When Update Manager installs a later kernel, known in Ubuntu as linux-image, recompile:```
cd ~/Scrivania/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
make clean
make
sudo make install
sudo modprobe mt7601Usta
```This will probably not work at all for kernel versions newer than 3.2.0-xx, so be careful what you allow  Update Manager to install. If it wants to install 3.8.0-xx or some such, deny it, stop and ask here.

Please retain the file and these instructions for that time.

---

### Post by deldin on 2014-09-09
don't worry, I have saved all :)

---

### Post by woj_s on 2014-09-11
Hi !

Its my first post on this forum ... so please ..help me ;)
I have problem with MT7601 wifi usb stick.

I get newest drivers ([http://ubuntuforums.org/showthread.php?t=2210930](http://ubuntuforums.org/showthread.php?t=2210930))
and all what you wrote in this topic.

sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
make
sudo make install
sudo modprobe mt7601Usta

Its almost works ..but ...at the begining :

lsusb : Bus 002 Device 014: ID 148f:7601 Ralink Technology, Corp.
uname -r : .2.0-68-generic

make clean ; make and make install .. end without errors

iwconfig returns :

lo        no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"MT7601STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

more informations:

ra0       14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

ra0       Scan completed :
          Cell 01 - Address: <MAC C-01 >
                    Protocol:11b/g/n BW20
                    ESSID:""
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality=89/100  Signal level=-55 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK



but modprob returns no informations :
wojtek@wojtek:~/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ sudo modprobe -v mt7601Usta
wojtek@wojtek:~/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$

Network manager can see wifi card.
I can try to connect to my wifi network ...but LED doesnt blink :(

So ..I have 2 questions :
- what sould I do ..to connect to my wifi network ?
- what should I do ...to save configuration and use wifi card after reboot ?

Thanks a lot for help ;)

---

### Post by chili555 on 2014-09-11
I notice this:> ra0 Scan completed :
Cell 01 - Address: <MAC C-01 >
Protocol:11b/g/n BW20
[COLOR="#FF0000"]ESSID:""[/COLOR]
Mode:Managed
Frequency:2.452 GHz (Channel 9)
Quality=89/100 Signal level=-55 dBm Noise level=-92 dBmIs the SSID really hidden? Did you go through the process to connect to a hidden wireless network in Network Manager?

Are there any clues here?```
dmesg | grep -e wlan -e mt76
uname -r
```

---

### Post by woj_s on 2014-09-11
Hmmm strange ..very strange !
I remove check on Hide wireless network on router ...  and ... hurra ! it works !
Next hide network ..and still works !
but why ?

nevermind ... 

Its important, wifi card works !

What about reboots ?
Its OK ? ... will work ?

---

### Post by chili555 on 2014-09-11
It should, but you could just reboot and tell us!!

---

### Post by woj_s on 2014-09-11
Great !
Still works !

**Chili555**, thanks a lot for your help !!!

---

### Post by chili555 on 2014-09-11
> **woj_s said:**
> Great !
Still works !

**Chili555**, thanks a lot for your help !!!Happy to help any time. Just post here or a new thread and I'll be there.

---

### Post by toshih on 2014-11-03
Hi! Could You please  help me. It seems I have similar Ralink's USB stick (ipTime N150UA), drivers DPO_MT7601U_LinuxSTA_3.0.0.4_20130913 and Ubuntu 14.04.1...


kumho@kumho-desktop:~$ lsusb
Bus 002 Device 004: ID 148f:7601 Ralink Technology, Corp. 
Bus 002 Device 003: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1d57:f833 Xenta 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kumho@kumho-desktop:~$ uname -r
3.13.0-32-lowlatency


Trying use any way described in this tread I get errors as result.
Googling brings nothing...
It my first attempt to get date with Ubuntu but the point looks like insurmountable obstacle.

---

### Post by toshih on 2014-11-03
also tryed this way


```
sudo apt-get install --reinstall linux-headers-generic build-essential  
tar xjf DPO_MT7601U_LinuxSTA_3.0.0.4_20130913.tar.bz2  
cd DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/  
patch -p0 < ~/(ADD THE PATH)/rt2870-mt7601Usta-kuid_t-kgid_t.patch  
make  
su -c 'mkdir -p /etc/Wireless/RT2870STA/'  
su -c 'cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat'  


Connect the USB


su -c '/sbin/insmod os/linux/mt7601Usta.ko'


If works:


su -c 'make install'
```


WI-FI shows me "linked", but in the process of connecting to an Internet system stops with kernel panic

---

### Post by chili555 on 2014-11-04
This is one of the trickiest devices to get going that I know of. Did you try this? [http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation)

---

### Post by toshih on 2014-11-04
Yes I did ([http://askubuntu.com/questions/45706...r-installation](http://askubuntu.com/questions/45706...r-installation))... It brings "kernel panic". Now I just rolled back to 12.04.01 with 3.2.0-23, and all works perfect. But by the way, until which kernel version it possible to use? Thank You!

---

### Post by chili555 on 2014-11-04
> **toshih said:**
> Yes I did ([http://askubuntu.com/questions/45706...r-installation](http://askubuntu.com/questions/45706...r-installation))... It brings "kernel panic". Now I just rolled back to 12.04.01 with 3.2.0-23, and all works perfect. But by the way, until which kernel version it possible to use? Thank You!I haven't any idea. I'd assume that any 3.2.0-xx kernel would be fine. If it's working well now, I'd be happy and move on.

---

### Post by ian-mellor-me on 2015-01-31
> **chili555 said:**
> Please show us the result of:```
cd ~/Scrivania/DPA_MT7601U_LinuxSTA_3.0.0.4_20130916
make clean
make
sudo make install
```Thanks.

Hi All,

I'm also a Linux newbie and I have the same dongle. I have checked I have the relevant packages as per this thread and I have completed the make commands as above, however I recieve lots of errors as per the code below, any help would be appreciated...


```
leaders@Office:~/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ make
make -C tools
make[1]: Entering directory `/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools/bin2h
cp -f os/linux/Makefile.6 /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/Makefile
make -C /lib/modules/3.13.0-45-generic/build SUBDIRS=/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-45-generic'
  CC [M]  /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsUsDelay’:
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:179:8: warning: unused variable ‘i’ [-Wunused-variable]
  ULONG i;
        ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:497:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);
   ^
In file included from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:31,
                 from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44,
                 from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32:
/usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:499:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pData, DataSize);
   ^
In file included from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:31,
                 from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44,
                 from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32:
/usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:650:20: warning: assignment makes integer from pointer without a cast [enabled by default]
   pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;
                    ^
In file included from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44:0,
                 from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32:
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:886:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:669:2: note: in expansion of macro ‘SET_OS_PKT_DATATAIL’
  SET_OS_PKT_DATATAIL(pRxPkt, pData, DataSize);
  ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:695:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1121:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1122:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();
                    ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpDrvAllRFPrint’:
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: warning: passing argument 2 of ‘file_w->f_op->write’ from incompatible pointer type [enabled by default]
    file_w->f_op->write(file_w, pBuf, BufLen, &file_w->f_pos);
    ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:22: warning: unused variable ‘macValue’ [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
                      ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:9: warning: unused variable ‘macAddr’ [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
         ^
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRelease’:
/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2173:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
  struct net_device *net_dev = (struct net_device *)pNetDev;
                     ^
make[2]: *** [/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/leaders/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-45-generic'
make: *** [LINUX] Error 2
```

---

### Post by chili555 on 2015-01-31
> **ian-mellor-me said:**
> Hi All,

I'm also a Linux newbie and I have the same dongle. I have checked I have the relevant packages as per this thread and I have completed the make commands as above, however I recieve lots of errors as per the code below, any help would be appreciated...That old antique will never compile on a modern 3.13.0-xx kernel. I suggest you try this instead: [http://askubuntu.com/questions/577941/installing-the-driver-for-tp-link-tl-wn727n-on-ubuntu-14-04/578017#578017](http://askubuntu.com/questions/577941/installing-the-driver-for-tp-link-tl-wn727n-on-ubuntu-14-04/578017#578017)

---

### Post by ian-mellor-me on 2015-01-31
> **chili555 said:**
> That old antique will never compile on a modern 3.13.0-xx kernel. I suggest you try this instead: [http://askubuntu.com/questions/577941/installing-the-driver-for-tp-link-tl-wn727n-on-ubuntu-14-04/578017#578017](http://askubuntu.com/questions/577941/installing-the-driver-for-tp-link-tl-wn727n-on-ubuntu-14-04/578017#578017)

Thanks that worked.

Ian

---

