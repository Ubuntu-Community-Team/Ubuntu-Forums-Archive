---
title: "Edimax ew-7822ulc driver not compiling"
date: 2018-05-17
forum: Networking &amp; Wireless
---

### Post by diane258 on 2018-05-17
Hello everyone,

I am trying to install the Linux driver from the edimax website for the wifi net worker. however when i go to compile this happens. any ideas?

```
darkstar@darkstar-MS-7A39:~/Downloads/edi$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-41-generic/build M=/home/darkstar/Downloads/edi  modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-41-generic'
  CC [M]  /home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.o
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_cfg80211_indicate_connect’:
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:766:6: error: passing argument 2 of ‘cfg80211_roamed’ from incompatible pointer type [-Werror=incompatible-pointer-types]
    , notify_channel
      ^
In file included from /home/darkstar/Downloads/edi/include/osdep_service_linux.h:88:0,
                 from /home/darkstar/Downloads/edi/include/osdep_service.h:47,
                 from /home/darkstar/Downloads/edi/include/drv_types.h:27,
                 from /home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:17:
./include/net/cfg80211.h:5477:6: note: expected ‘struct cfg80211_roam_info *’ but argument is of type ‘struct ieee80211_channel *’
 void cfg80211_roamed(struct net_device *dev, struct cfg80211_roam_info *info,
      ^
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:768:6: warning: passing argument 3 of ‘cfg80211_roamed’ makes integer from pointer without a cast [-Wint-conversion]
    , cur_network->network.MacAddress
      ^
In file included from /home/darkstar/Downloads/edi/include/osdep_service_linux.h:88:0,
                 from /home/darkstar/Downloads/edi/include/osdep_service.h:47,
                 from /home/darkstar/Downloads/edi/include/drv_types.h:27,
                 from /home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:17:
./include/net/cfg80211.h:5477:6: note: expected ‘gfp_t {aka unsigned int}’ but argument is of type ‘unsigned char *’
 void cfg80211_roamed(struct net_device *dev, struct cfg80211_roam_info *info,
      ^
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:764:3: error: too many arguments to function ‘cfg80211_roamed’
   cfg80211_roamed(padapter->pnetdev
   ^
In file included from /home/darkstar/Downloads/edi/include/osdep_service_linux.h:88:0,
                 from /home/darkstar/Downloads/edi/include/osdep_service.h:47,
                 from /home/darkstar/Downloads/edi/include/drv_types.h:27,
                 from /home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:17:
./include/net/cfg80211.h:5477:6: note: declared here
 void cfg80211_roamed(struct net_device *dev, struct cfg80211_roam_info *info,
      ^
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_cfg80211_add_monitor_if’:
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:3850:10: error: ‘struct net_device’ has no member named ‘destructor’
  mon_ndev->destructor = rtw_ndev_destructor;
          ^
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_cfg80211_preinit_wiphy’:
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:6812:18: error: ‘WIPHY_FLAG_SUPPORTS_SCHED_SCAN’ undeclared (first use in this function)
  wiphy->flags |= WIPHY_FLAG_SUPPORTS_SCHED_SCAN;
                  ^
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:6812:18: note: each undeclared identifier is reported only once for each function it appears in
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c: At top level:
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:6849:25: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .change_virtual_intf = cfg80211_rtw_change_iface,
                         ^
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:6849:25: note: (near initialization for ‘rtw_cfg80211_ops.change_virtual_intf’)
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:6872:22: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .add_virtual_intf = cfg80211_rtw_add_virtual_intf,
                      ^
/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.c:6872:22: note: (near initialization for ‘rtw_cfg80211_ops.add_virtual_intf’)
cc1: some warnings being treated as errors
scripts/Makefile.build:316: recipe for target '/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.o' failed
make[2]: *** [/home/darkstar/Downloads/edi/os_dep/linux/ioctl_cfg80211.o] Error 1
Makefile:1550: recipe for target '_module_/home/darkstar/Downloads/edi' failed
make[1]: *** [_module_/home/darkstar/Downloads/edi] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-41-generic'
Makefile:1801: recipe for target 'modules' failed
make: *** [modules] Error 2
darkstar@darkstar-MS-7A39:~/Downloads/edi$
```

---

### Post by wildmanne39 on 2018-05-17
Please click on the codetags link in my signature to see how to use code tags when posting code.

Thanks

---

### Post by praseodym on 2018-05-18
What driver for which device?

Please show
```

lspci -nnk
lsusb
```

---

### Post by diane258 on 2018-05-18
[https://www.edimax.com/edimax/download/download/data/edimax/global/download/for_home/wireless_adapters/wireless_adapters_ac1200_dual-band/ew-7822ulc](https://www.edimax.com/edimax/download/download/data/edimax/global/download/for_home/wireless_adapters/wireless_adapters_ac1200_dual-band/ew-7822ulc)

It is a USB wireless wifi device

---

### Post by diane258 on 2018-05-18
This is the data
```

spci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1450]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1450]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Device [1022:1451]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1451]
00:01.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1452]
00:01.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:1453]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1452]
    DeviceName:  Onboard IGD
00:03.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1452]
00:03.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:1453]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:04.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1452]
00:07.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1452]
00:07.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:1454]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:08.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1452]
00:08.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:1454]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:790b] (rev 59)
    Subsystem: Micro-Star International Co., Ltd. [MSI] FCH SMBus Controller [1462:7a39]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:790e] (rev 51)
    Subsystem: Micro-Star International Co., Ltd. [MSI] FCH LPC Bridge [1462:7a39]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1460]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1461]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1462]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1463]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1464]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1465]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1466]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1467]
03:00.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] Device [1022:43bb] (rev 02)
    Subsystem: ASMedia Technology Inc. Device [1b21:1142]
    Kernel driver in use: xhci_hcd
03:00.1 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] Device [1022:43b7] (rev 02)
    Subsystem: ASMedia Technology Inc. Device [1b21:1062]
    Kernel driver in use: ahci
    Kernel modules: ahci
03:00.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:43b2] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
04:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:43b4] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
04:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:43b4] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
04:06.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:43b4] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
04:07.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:43b4] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
1e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7a39]
    Kernel driver in use: r8169
    Kernel modules: r8169
22:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:67df] (rev ef)
    Subsystem: XFX Pine Group Inc. Device [1682:c570]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu
22:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:aaf0]
    Subsystem: XFX Pine Group Inc. Device [1682:aaf0]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
23:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device [1022:145a]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:145a]
23:00.2 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Device [1022:1456]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1456]
    Kernel driver in use: ccp
    Kernel modules: ccp
23:00.3 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] Device [1022:145c]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7a39]
    Kernel driver in use: xhci_hcd
24:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device [1022:1455]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1455]
24:00.2 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901] (rev 51)
    Subsystem: Micro-Star International Co., Ltd. [MSI] FCH SATA Controller [AHCI mode] [1462:7a39]
    Kernel driver in use: ahci
    Kernel modules: ahci
24:00.3 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Device [1022:1457]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:fa39]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
darkstar@darkstar-MS-7A39:~/Downloads/edi$ 

```

---

### Post by diane258 on 2018-05-18
lsusb
```

lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 7392:b822 Edimax Technology Co., Ltd 
Bus 001 Device 004: ID 154b:007a PNY Classic Attache Flash Drive
Bus 001 Device 003: ID 1532:010d Razer USA, Ltd 
Bus 001 Device 002: ID 0461:4d42 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
darkstar@darkstar-MS-7A39:~/Downloads/edi$ 


```

---

### Post by diane258 on 2018-05-18
this is the second part
```

lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 7392:b822 Edimax Technology Co., Ltd 
Bus 001 Device 004: ID 154b:007a PNY Classic Attache Flash Drive
Bus 001 Device 003: ID 1532:010d Razer USA, Ltd 
Bus 001 Device 002: ID 0461:4d42 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
darkstar@darkstar-MS-7A39:~/Downloads/edi$ 

```

---

### Post by chili555 on 2018-05-18
With a temporary working internet connection, do:

```
sudo apt update 
sudo apt install git
git clone https://github.com/MeissnerEffect/rtl8822bu.git
cd rtl8822bu
make
sudo make install
sudo modprobe 88x2bu
```

If, after the 'make' step, you have errors, please post them here. Warnings are probably alright.

You will have compiled the driver for your current running kernel only. When Update Manager installs a later one, also known as linux-image, after the requested reboot, re-compile:

```
cd rtl8822bu
make clean
make
sudo make install
sudo modprobe 88x2bu
```

---

### Post by wildmanne39 on 2018-05-18
Hello diane258, in future posts please add all the code that you run in one post instead of creating multiple posts.

Thanks

---

### Post by diane258 on 2018-05-18
Oh wow it worked!

So what did i do wrong?

i downloaded the driver and put it in the own dir. i did the make command and got the errors seen above.

---

### Post by chili555 on 2018-05-18
> So what did i do wrong?

i downloaded the driver and put it in the own dir. i did the make command and got the errors seen above.I don't think you did anything wrong. Edimax, however, provides a driver that will compile on most kernels. If the kernel is pretty new as your 4.13.0-xx is, it doesn't compile.

Old Doc Chili, on the other hand, scours the internet to find a driver that compiles without error by downloading it and compiling it *before* he proposes a solution. Hey, it's what we do!!

Compiling drivers is a black art and I love a mystery!

Glad it's working. Please use thread tools at the top to mark Solved.

---

### Post by praseodym on 2018-05-20
[https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836](https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836)

Try this one

---

### Post by chili555 on 2018-05-20
I believe it's already solved. I wouldn't advise trying something different if it's working well now.

---

### Post by Mip5 on 2018-11-06
Hi,

I just tried compiling the driver using the instructions in this thread and got the following errors:

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-38-generic/build M=/home/MyName/rtl8822bu  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-38-generic'
  CC [M]  /home/MyName/rtl8822bu/core/rtw_cmd.o
In file included from ./include/linux/list.h:9:0,
                 from ./include/linux/module.h:9,
                 from /home/MyName/rtl8822bu/include/basic_types.h:76,
                 from /home/MyName/rtl8822bu/include/drv_types.h:26,
                 from /home/MyName/rtl8822bu/core/rtw_cmd.c:17:
./include/linux/kernel.h:6:10: fatal error: stdarg.h: No such file or directory
 #include <stdarg.h>
          ^~~~~~~~~~
compilation terminated.
scripts/Makefile.build:332: recipe for target '/home/MyName/rtl8822bu/core/rtw_cmd.o' failed
make[2]: *** [/home/MyName/rtl8822bu/core/rtw_cmd.o] Error 1
Makefile:1551: recipe for target '_module_/home/MyName/rtl8822bu' failed
make[1]: *** [_module_/home/MyName/rtl8822bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-38-generic'
Makefile:1999: recipe for target 'modules' failed
make: *** [modules] Error 2

----------

Thanks in advance,

Marc

---

### Post by chili555 on 2018-11-06
> **Mip5 said:**
> Hi,

I just tried compiling the driver using the instructions in this thread and got the following errors:

<snip>
./include/linux/kernel.h:6:10: fatal error: stdarg.h: No such file or directory
 #include <stdarg.h>
          ^~~~~~~~~~
compilation terminated.
scripts/Makefile.build:332: recipe for target '/home/MyName/rtl8822bu/core/rtw_cmd.o' failed
<snip>
Makefile:1999: recipe for target 'modules' failed
make: *** [modules] Error 2

----------

Thanks in advance,

MarcPlease try:```
cd rtl8822bu
rm .cache.mk
make clean
git pull
make
```Any improvement?

---

### Post by Mip5 on 2018-11-06
Excellent! Thank you. 

Now the only problem I have is that I can only get a reliable connection when I'm close to the access point. In general, have you had good luck with this device?

---

### Post by chili555 on 2018-11-07
> **Mip5 said:**
> Excellent! Thank you. 

Now the only problem I have is that I can only get a reliable connection when I'm close to the access point. In general, have you had good luck with this device?I have had no luck at all with this device; I don't own one. Like most of the wireless gurus here, I just have a tiny bit of skill at finding and compiling the correct driver for your device.

As for the range, let's try a driver parameter. From the terminal:

```
sudo -i
echo "options 88x2bu rtw_ant_num=1"  >  /etc/modprobe.d/88x2bu.conf
exit
```

Reboot and test. If the parameter is ineffective, run the sequence again but with rtw_ant_num=2 and reboot and test.

---

### Post by Mip5 on 2018-11-07
Well done indeed! It's definitely better. Both settings (1 and 2) seem to have improved the connection, but I can more reliably establish the connection using 2.

Thanks so much!

Marc

---

