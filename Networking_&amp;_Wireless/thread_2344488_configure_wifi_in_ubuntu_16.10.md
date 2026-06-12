---
title: "configure wifi in ubuntu 16.10"
date: 2016-11-25
forum: Networking &amp; Wireless
---

### Post by thosecars822 on 2016-11-25
Hello
I just installed lubuntu 16.10 in this laptop.
For some reason there is no wifi adaper icon on the right section of the task bar. I do not know how to configure the wifi adapter. Does any one know how to do this?

```
~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 1
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 2
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 3
00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS482M [Mobility Radeon Xpress 200]
02:01.0 Ethernet controller: Broadcom Limited NetXtreme BCM5788 Gigabit Ethernet (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
30:00.0 Network controller: Broadcom Limited BCM4311 802.11a/b/g (rev 01)
```




Thanks

---

### Post by wildmanne39 on 2016-11-25
Please do:
```
sudo apt-get install --reinstall network-manager-gnome 
```
Does the icon show now? You also need to install the firmware for the b43 driver if you have not done so by doing:
```
sudo apt-get install firmware-b43-installer
```
Reboot

---

### Post by thosecars822 on 2016-11-26
Thank you! That worked!

---

### Post by wildmanne39 on 2016-11-26
Glad it worked, please use thread tools at the top of the page to mark the thread solved.
Thanks and Enjoy!:)

---

