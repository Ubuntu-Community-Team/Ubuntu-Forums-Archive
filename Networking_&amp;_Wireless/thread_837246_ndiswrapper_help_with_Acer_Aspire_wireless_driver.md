---
title: "ndiswrapper help with Acer Aspire wireless driver"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by DaddyUnit on 2008-06-22
I have a new (reconditioned) Acer Aspire 4520 laptop, out of the box two days ago and installed Hardy for AMD64 (see details below).

I FINALLY got ndiswrapper to install after reading wieman01's sticky post at [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419) and ran it on a windows driver for the wireless card as described in this post [http://fedora4520.blogspot.com/2008/02/wireless-atheros-ar5bxb63-or-ar5006eg.html](http://fedora4520.blogspot.com/2008/02/wireless-atheros-ar5bxb63-or-ar5006eg.html).

When I run ndiswrapper -l I get:
```
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

```

I don't know for sure that this is the right thing.

I don't know what to do next. I rebooted then went to System > Administration > Network and didn't see anything new. Is this because I still don't have the right driver, or because I haven't done something with the ndiswrapper that I should have done?

wieman01's post says "Then reboot the computer and see if you can connect using your favorite networking applet (e.g. Network Manager, WICD, Wifi Radar, etc.)." Do I need one of these? If so, how would I get it.

The people on this forum have been great and your continued support and assistance is very much appreciated.

Here are more details on my machine:

Acer Aspire 4520
AMD Athlon X2 Dual Core Processor 1K-53(1.7GHz, 2x 256KB L2 Cache)
There's a sticker on the case that says I've got nvidia GeForce 7000M

lspci```

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```


iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```
iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

---

