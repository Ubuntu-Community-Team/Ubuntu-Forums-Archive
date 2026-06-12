---
title: "WNDA3100v3 on Ubuntu 18.04 errors upon make"
date: 2018-08-04
forum: Networking &amp; Wireless
---

### Post by fravec on 2018-08-04
Hello community!

So, my problem is simply that I would like to get my WNDA3100v3 running on my 18.04 machine. After some intense research I found out that most of the threads on the internet ultimately point to this [git repository]("https://github.com/jurobystricky/Netgear-A6210") when it is about this device. Of course I followed the installation instructions, but at some point I ended up in a mess.

When executing the **make** command in the respective directory, I receive this:
```
$ make
export DBGFLAGS

*** Building driver with debug messages ***

cp -f os/linux/Makefile.6 /home/jfd/Desktop/Netgear-A6210/os/linux/Makefile
make -C /lib/modules/4.15.0-29-generic/build DBGFLAGS=-DDBG SUBDIRS=/home/jfd/Desktop/Netgear-A6210/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-29-generic'
  CC [M]  /home/jfd/Desktop/Netgear-A6210/os/linux/../../sta/assoc.o
In file included from ./include/linux/list.h:5:0,
                 from ./include/linux/module.h:9,
                 from /home/jfd/Desktop/Netgear-A6210/include/os/rt_linux.h:14,
                 from /home/jfd/Desktop/Netgear-A6210/include/rtmp_os.h:30,
                 from /home/jfd/Desktop/Netgear-A6210/include/rtmp_comm.h:64,
                 from /home/jfd/Desktop/Netgear-A6210/include/rt_config.h:34,
                 from /home/jfd/Desktop/Netgear-A6210/os/linux/../../sta/assoc.c:28:
./include/linux/types.h:17:9: error: unknown type name ‘__kernel_ino_t’
 typedef __kernel_ino_t  ino_t;
         ^~~~~~~~~~~~~~
./include/linux/types.h:18:9: error: unknown type name ‘__kernel_mode_t’
 typedef __kernel_mode_t  mode_t;
         ^~~~~~~~~~~~~~~
./include/linux/types.h:21:9: error: unknown type name ‘__kernel_off_t’
 typedef __kernel_off_t  off_t;
         ^~~~~~~~~~~~~~
./include/linux/types.h:22:9: error: unknown type name ‘__kernel_pid_t’
 typedef __kernel_pid_t  pid_t;
         ^~~~~~~~~~~~~~
./include/linux/types.h:23:9: error: unknown type name ‘__kernel_daddr_t’
 typedef __kernel_daddr_t daddr_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:25:9: error: unknown type name ‘__kernel_suseconds_t’
 typedef __kernel_suseconds_t suseconds_t;
         ^~~~~~~~~~~~~~~~~~~~
./include/linux/types.h:26:9: error: unknown type name ‘__kernel_timer_t’
 typedef __kernel_timer_t timer_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:27:9: error: unknown type name ‘__kernel_clockid_t’
 typedef __kernel_clockid_t clockid_t;
         ^~~~~~~~~~~~~~~~~~
./include/linux/types.h:32:9: error: unknown type name ‘__kernel_uid32_t’
 typedef __kernel_uid32_t uid_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:33:9: error: unknown type name ‘__kernel_gid32_t’
 typedef __kernel_gid32_t gid_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:34:9: error: unknown type name ‘__kernel_uid16_t’
 typedef __kernel_uid16_t        uid16_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:35:9: error: unknown type name ‘__kernel_gid16_t’
 typedef __kernel_gid16_t        gid16_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:41:9: error: unknown type name ‘__kernel_old_uid_t’
 typedef __kernel_old_uid_t old_uid_t;
         ^~~~~~~~~~~~~~~~~~
./include/linux/types.h:42:9: error: unknown type name ‘__kernel_old_gid_t’
 typedef __kernel_old_gid_t old_gid_t;
         ^~~~~~~~~~~~~~~~~~
./include/linux/types.h:46:9: error: unknown type name ‘__kernel_loff_t’
 typedef __kernel_loff_t  loff_t;
         ^~~~~~~~~~~~~~~
./include/linux/types.h:55:9: error: unknown type name ‘__kernel_size_t’
 typedef __kernel_size_t  size_t;
         ^~~~~~~~~~~~~~~
./include/linux/types.h:60:9: error: unknown type name ‘__kernel_ssize_t’
 typedef __kernel_ssize_t ssize_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:65:9: error: unknown type name ‘__kernel_ptrdiff_t’
 typedef __kernel_ptrdiff_t ptrdiff_t;
         ^~~~~~~~~~~~~~~~~~
./include/linux/types.h:70:9: error: unknown type name ‘__kernel_time_t’
 typedef __kernel_time_t  time_t;
         ^~~~~~~~~~~~~~~
./include/linux/types.h:75:9: error: unknown type name ‘__kernel_clock_t’
 typedef __kernel_clock_t clock_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:80:9: error: unknown type name ‘__kernel_caddr_t’
 typedef __kernel_caddr_t caddr_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:199:2: error: unknown type name ‘__kernel_daddr_t’
  __kernel_daddr_t f_tfree;
  ^~~~~~~~~~~~~~~~
./include/linux/types.h:200:2: error: unknown type name ‘__kernel_ino_t’
  __kernel_ino_t  f_tinode;
  ^~~~~~~~~~~~~~
In file included from ./include/linux/list.h:9:0,
                 from ./include/linux/module.h:9,
                 from /home/jfd/Desktop/Netgear-A6210/include/os/rt_linux.h:14,
                 from /home/jfd/Desktop/Netgear-A6210/include/rtmp_os.h:30,
                 from /home/jfd/Desktop/Netgear-A6210/include/rtmp_comm.h:64,
                 from /home/jfd/Desktop/Netgear-A6210/include/rt_config.h:34,
                 from /home/jfd/Desktop/Netgear-A6210/os/linux/../../sta/assoc.c:28:
./include/linux/kernel.h:6:10: fatal error: stdarg.h: No such file or directory
 #include <stdarg.h>
          ^~~~~~~~~~
compilation terminated.
scripts/Makefile.build:332: recipe for target '/home/jfd/Desktop/Netgear-A6210/os/linux/../../sta/assoc.o' failed
make[2]: *** [/home/jfd/Desktop/Netgear-A6210/os/linux/../../sta/assoc.o] Error 1
Makefile:1558: recipe for target '_module_/home/jfd/Desktop/Netgear-A6210/os/linux' failed
make[1]: *** [_module_/home/jfd/Desktop/Netgear-A6210/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-29-generic'
Makefile:59: recipe for target 'debug' failed
make: *** [debug] Error 2

```
I assume that I am missing something regarding C or C++, so I append my C++ packages:
```
$ apt list --installed | grep -i gcc

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

gcc/bionic,now 4:7.3.0-3ubuntu2 amd64 [installed]
gcc-7/bionic,now 7.3.0-16ubuntu3 amd64 [installed,automatic]
gcc-7-base/bionic,now 7.3.0-16ubuntu3 amd64 [installed]
gcc-8-base/bionic,now 8-20180414-1ubuntu2 amd64 [installed]
libcaca0/bionic,now 0.99.beta19-2build2~gcc5.3 amd64 [installed]
libgcc-7-dev/bionic,now 7.3.0-16ubuntu3 amd64 [installed,automatic]
libgcc1/bionic,now 1:8-20180414-1ubuntu2 amd64 [installed]

```
```
$ apt list --installed | grep -i cpp

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

cpp/bionic,now 4:7.3.0-3ubuntu2 amd64 [installed]
cpp-7/bionic,now 7.3.0-16ubuntu3 amd64 [installed]

```
```
$ apt list --installed | grep -i c++

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libstdc++-7-dev/bionic,now 7.3.0-16ubuntu3 amd64 [installed,automatic]
libstdc++6/bionic,now 8-20180414-1ubuntu2 amd64 [installed]


```

By the way, the device is found by the OS, as you can see from this excerpt:
```
$ lsusb
...
Bus 001 Device 007: ID 0846:9014 NetGear, Inc. 
...

```

Might also be interesting to see:
```
$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 11
       serial: f8:0f:41:c8:0e:73
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.137.61 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:18 ioport:e000(size=256) memory:d0604000-d0604fff memory:d0600000-d0603fff

```

I hope I provided enough information for somebody to figure out and help me. Thank you in advance!

---

### Post by chili555 on 2018-08-04
Please try this instead:```
git clone -b port-to-4.15 https://github.com/kaduke/Netgear-A6210.git
```

---

### Post by fravec on 2018-08-05
Thank you for your quick answer! Unfortunately it changed nothing on my situation. It remains not listed in the wlan adapter list and the commands I gave in the initial post show the same results as before. Perhaps I broke or misconfigured/overconfigured something when trying all the other tutorials recently. Do you have any idea how I can diagnose, if so?

Many thanks in advance!

PS: for sake of completeness, I append the result of a _second_ **make** run:
```
$ make
export DBGFLAGS

*** Building driver with debug messages ***

cp -f os/linux/Makefile.6 /home/jfd/Desktop/Netgear-A6210/os/linux/Makefile
make -C /lib/modules/4.15.0-29-generic/build DBGFLAGS=-DDBG SUBDIRS=/home/jfd/Desktop/Netgear-A6210/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-29-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-29-generic'

$ sudo make install
make -C /home/jfd/Desktop/Netgear-A6210/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/jfd/Desktop/Netgear-A6210/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir -pv /etc/Wireless/RT2870STA
mkdir: created directory '/etc/Wireless/RT2870STA'
cp /home/jfd/Desktop/Netgear-A6210/conf/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/
install -m 644 -c mt7662u_sta.ko /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.15.0-29-generic
make[1]: Leaving directory '/home/jfd/Desktop/Netgear-A6210/os/linux'

```

---

### Post by praseodym on 2018-08-05
Please show

```
modinfo mt7662u_sta
```

---

### Post by fravec on 2018-08-05
```
$ modinfo mt7662u_sta
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/mt7662u_sta.ko
version:        3.0.0.1
license:        GPL
description:    Ralink Wireless Lan Linux Driver
author:         Ralink
srcversion:     67F91ED0585DA74BA635EB9
alias:          usb:v0E8Dp7662d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp7632d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp7612d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v045Ep02E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17EBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p180Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9014d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
name:           mt7662u_sta
vermagic:       4.15.0-29-generic SMP mod_unload 
parm:           mac:rt_wifi: wireless mac addr (charp)
parm:           mode:rt_wifi: wireless operation mode (charp)

```

---

### Post by praseodym on 2018-08-05
Ok, lets see
```

sudo modprobe -v mt7662u_sta
dmesg | egrep 'rt2|mt7|firm|key'
```

---

### Post by fravec on 2018-08-05
```
$ sudo modprobe -v mt7662u_sta
insmod /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/mt7662u_sta.ko 
modprobe: ERROR: could not insert 'mt7662u_sta': Required key not available

```

```
$ dmesg | egrep 'rt2|mt7|firm|key'
[    2.117784] Initialise system trusted keyrings
[    2.124552] Asymmetric key parser 'x509' registered
[    2.193176] Loaded X.509 cert 'Build time autogenerated kernel key: 1cc37f41791529df57507d3747a6804ab53f482b'
[    2.193425] Loaded UEFI:db cert 'Acer Database: 84f00f5841571abd2cc11a8c26d5c9c8d2b6b0b5' linked to secondary sys keyring
[     2.193468] Loaded UEFI:db cert 'Microsoft Corporation UEFI CA 2011:  13adbf4309bd82709c8cd54f316ed522988a1bd4' linked to secondary sys  keyring
[    2.193508] Loaded UEFI:db cert 'Microsoft Windows  Production PCA 2011: a92902398e16c49778cd90f99e4f9ae17c55af53' linked to  secondary sys keyring
[    2.199477] Loaded UEFI:MokListRT cert  'Canonical Ltd. Master Certificate Authority:  ad91990bc22ab1f517048c23b6655a268e345a63' linked to secondary sys  keyring
[    2.211662] Key type big_key registered
```

---

### Post by chili555 on 2018-08-05
Please disable secure boot.

---

### Post by fravec on 2018-08-05
That worked for me. I am posting via the wlan dongle! Thank you gentlemen!

---

