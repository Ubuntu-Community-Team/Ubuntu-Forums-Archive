---
title: "trying to get  a netgear n300 to work please help"
date: 2016-09-20
forum: Networking &amp; Wireless
---

### Post by xiph3r79 on 2016-09-20
by all means im no linux guru, im trying to get my netgear n300 to work as keeping the pc plugged in is something i cant keep doing. currently running ubuntu 16.04

lspci -nn
```
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex [1022:1705]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6530D] [1002:964a]
00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port [1022:1707]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port [1022:1709]
00:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port [1022:170a]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7801] (rev 40)
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 13)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7809] (rev 11)
00:14.7 SD Host controller [0805]: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller [1022:7806]
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7 [1022:1719]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)


```


lsusb
```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

dmesg | grep ndis
```
[  738.306059] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[  738.309733] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  738.614553] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  739.137227] usbcore: registered new interface driver ndiswrapper
[  739.157186] ndiswrapper 1-1:1.0 enxa42b8c5cceb0: renamed from wlan0
[  739.175955] ndiswrapper: interface renamed to 'enxa42b8c5cceb0'


```

ndiswrapper -l


```
bcmn43xx64 : driver installed
    device (0846:9020) present
bcmwlhigh5 : invalid driver!



```
ndiswrapper -v
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/4.4.0-38-generic/updates/dkms/ndiswrapper.ko
version:        1.59
vermagic:       4.4.0-38-generic SMP mod_unload modversions 


```

---

### Post by mörgæs on 2016-09-21
Hi, welcome to the fora.

Does this help? 
[https://ubuntuforums.org/showthread.php?t=2221251](https://ubuntuforums.org/showthread.php?t=2221251)

---

### Post by xiph3r79 on 2016-09-22
yes thankyou :)

---

