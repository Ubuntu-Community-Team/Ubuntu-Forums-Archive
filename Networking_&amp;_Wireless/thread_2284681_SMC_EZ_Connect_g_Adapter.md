---
title: "SMC EZ Connect g Adapter"
date: 2015-07-01
forum: Networking &amp; Wireless
---

### Post by John_Dalay on 2015-07-01
I am trying to get my SMC EZ Connect g USB 2.0 wireless adapter to work but it never creates the wlan0 interface.  After lots of research, although I am a Linux novice (more or less), the instructions I found never ended up working.  Nor did I want to use ndiswrapper since what I found indicated the 32-bit XP/2000 driver would not work on 64-bit Ubuntu.  That the OS is 64-bit is something I am considering to be part of the problem here too.  But I digress.  Here is a brief summary of my findings: 

   1) The device is recognized by 'lsusb'
   2) 'dmesg' seems to indicate a driver loading error (that I can tell) 

The steps in between that I tried include installing the 'linux-firmware-nonfree' package, 'modprobe -r p54usb', 'modprobe p54usb', directly downloading and installing the prism54 driver from its main site. 

Furthermore, sites like [http://lxr.free-electrons.com/source/drivers/net/wireless/p54/p54usb.c](http://lxr.free-electrons.com/source/drivers/net/wireless/p54/p54usb.c) may indicate it is a memory problem.  One of the  'dmesg' error messages is "(p54usb) unable to jump to boot ROM (-19)".[br][/br][br][/br]  [thread]1663589[/thread] came the closest to my problem but not quite.  It had a different kernel error.  Moreover, that thread worked with 32-bit Ubuntu, if I read it right.  But before I get ahead of myself again, I am not sure how much further I can go on my own.  Any help would be appreciated.  Here are the wireless related details. 

Machine Brand and Model (PC): ```
 Dell OptiPlex 745 (rebuilt desktop and likely not the original PCI components) 
```  Wireless Brand, Model and Wireless Chipset: (lsusb) ```
 Bus 001 Device 009: ID 0707:ee13 Standard Microsystems Corp. SMC2862W-G v2 EZ Connect 802.11g Adapter [Intersil ISL3887]
Part #: 99-012084-374 
```  check interface: (iwconfig) ```
 lo        no wireless extensions.
eth0      no wireless extensions. 
```  Check for modules: (lsmod | grep -i p54) ```
 p54usb                 17612  0
p54common              37860  1 p54usb
crc_ccitt              12707  1 p54common
mac80211              506921  4 p54usb,p54common,rt2x00usb,rt2x00lib
cfg80211              205774  3 p54common,rt2x00lib,mac80211 
```  Kernel boot messages: ```
 [  602.200319]  [<ffffffffa038b01e>] p54u_init+0x1e/0x1000 [p54usb] 
[  722.200319]  [<ffffffffa038b01e>] p54u_init+0x1e/0x1000 [p54usb] 
[  842.200317]  [<ffffffffa038b01e>] p54u_init+0x1e/0x1000 [p54usb] 
[  962.200320]  [<ffffffffa038b01e>] p54u_init+0x1e/0x1000 [p54usb] 
[ 5537.708044] usb 1-3: (p54usb) unable to reset device (-19)! 
[ 5537.762867] ieee80211 phy2: p54 detected a LM87 firmware 
[ 5537.762872] p54: rx_mtu reduced from 3240 to 2384 
[ 5537.762887] usb 1-3: (p54usb) unable to jump to boot ROM (-19)! 
[ 5537.762941] usbcore: registered new interface driver p54usb 
[ 7326.516405] usb 1-3: (p54usb) unable to reset device (-19)! 
[ 7326.518210] ieee80211 phy4: p54 detected a LM87 firmware 
[ 7326.518214] p54: rx_mtu reduced from 3240 to 2384 
[ 7326.518225] usb 1-3: (p54usb) unable to jump to boot ROM (-19)! 
```  Network configuration: (no wireless configured)
Scan for networks: (no wireless interface to scan) 

Ubuntu Version: ```
 Ubuntu 12.04.5 LTS 
```  Kernel/architecture (64 bit): ```
 3.2.0-86-generic x86_64 
```

---

