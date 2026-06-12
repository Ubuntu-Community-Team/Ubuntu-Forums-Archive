---
title: "wireless doesent work using kernal 2.6.31-11"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by cosmoshell on 2011-08-12
im using a ralink rt5390.

---

### Post by elgordodude on 2011-08-12
This requires way more information. Can you see the card using lspci or lsusb (depending on the interface) have you tried installing drivers with ndiswrapper, lastly can you see wireless networks in network manager, but just can't connect to your home network? More information will give better answers.

---

### Post by cosmoshell on 2011-08-12
> **elgordodude said:**
> This requires way more information. Can you see the card using lspci or lsusb (depending on the interface) have you tried installing drivers with ndiswrapper, lastly can you see wireless networks in network manager, but just can't connect to your home network? More information will give better answers.

 lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9641
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Device 1707
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1709
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Device 170a
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 170b
00:10.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 VGA compatible controller: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Network controller: Ralink corp. Device 5390
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)



no wireless detected in network stuff. cant connect to any network.

---

### Post by elgordodude on 2011-08-12
> 03:00.0 Network controller: Ralink corp. Device 5390
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

Well at least we know it's there, even though it's not recognized and the drivers are probably not installed. On 10.10 I'm on kernel 35-30, is updating possible? While I had some troubles with wireless a year and a half or so ago, I find a lot of cards work out of the box now.

In no small part because ndiswrapper has become a default installation, so if updating is out of the question try...  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Make sure you download the current drivers, with the ndiswrapper files. It looks like your card will work with linux, so good luck

---

### Post by cosmoshell on 2011-08-12
> **elgordodude said:**
> Well at least we know it's there, even though it's not recognized and the drivers are probably not installed. On 10.10 I'm on kernel 35-30, is updating possible? While I had some troubles with wireless a year and a half or so ago, I find a lot of cards work out of the box now.

In no small part because ndiswrapper has become a default installation, so if updating is out of the question try...  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Make sure you download the current drivers, with the ndiswrapper files. It looks like your card will work with linux, so good luck

have current drivers, not sure if i used ndiswrapper or not, os is fully updated, wifi just doesent work under other kernals.

---

### Post by cosmoshell on 2011-08-13
bump

---

### Post by cosmoshell on 2011-08-19
bump

---

### Post by sumn2do on 2011-08-19
I just encountered this problem today too.  It was with kernel 2.6.38-11.  I was able to get my wireless working again by installing the drivers as described in this forum post. [http://ubuntuforums.org/showthread.php?t=1824605&highlight=rt5390](http://ubuntuforums.org/showthread.php?t=1824605&highlight=rt5390)

Good luck to you.

---

### Post by coffeecat on 2011-08-19
@cosmoshell, if you are using kernel 2.6.31, then you are probably running Ubuntu Karmic/9.10 which has passed end-of-life and is no longer supported - no more updates. Before trying to trouble-shoot your wireless difficulties, you would be advised to think about upgrading to a supported version of Ubuntu.

---

