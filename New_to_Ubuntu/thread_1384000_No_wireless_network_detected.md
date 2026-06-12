---
title: "No wireless network detected"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by vishdes on 2010-01-17
Hi,

I was searching through the forum and it seems my problem is a little bit different. Ubuntu does no find any wireless networks. When I connect to the LAN cable, the internet works fine.

But somehow I cannot see any wireless networks to connect to. I have posted below the lspci from the terminal

vishal@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
30:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
vishal@ubuntu:~$ ^C
vishal@ubuntu:~$ 

Also I don't see any specific hardware drivers to enable in the hardware drivers applications.


Please Help :(

---

### Post by slughappy1 on 2010-01-17
I'm not spectacular at dealing with Wireless problems, but how about trying the drivers Broadcom has? Since it looks like you have their BCM4312 wireless card [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Or maybe I'm just plain wrong :-)

---

### Post by bkratz on 2010-01-17
You might find your answers in this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by vishdes on 2010-01-18
Thank you everyone for the prompt response.
 
 Yes both of you were correct. No drivers installed.
 
 @ bkratz - thanks for the link to the thread. It was a smooth ride after that.
 
 I just had to update via the update manager and activate the driver.

---

### Post by bkratz on 2010-01-18
> **vishdes said:**
> Thank you everyone for the prompt response.
 
 Yes both of you were correct. No drivers installed.
 
 @ bkratz - thanks for the link to the thread. It was a smooth ride after that.
 
 I just had to update via the update manager and activate the driver.

Glad it worked out for you!

---

