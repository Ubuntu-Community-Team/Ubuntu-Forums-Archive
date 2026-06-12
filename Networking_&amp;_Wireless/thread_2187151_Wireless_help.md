---
title: "Wireless help"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by bronsoncornilles on 2013-11-11
I have been trying to get my wirless to work on my new 12.04 install of ubuntu for about 7 hours now. I have not found a thread that could specifically remedy my situation. I know i have a broadcom wireless chip, but i can not for the life of me figure out what to download/ do to get it to work. Could someone please at least point me in the right direction. All help is greatly appreciated.

My lspci is:

00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce Go 6150] (rev a2)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: NVIDIA Corporation MCP51 PMU (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by tuhinr.007 on 2013-11-11
I'm not an expert or anything, but what I did was install the updates (ubuntu) and then downloaded the driver from "additional driver" section. This process helped me to install the driver, but the adapter ain't recognising any wireless network.

---

### Post by chili555 on 2013-11-11
The Broadcom 4311 requires firmware and *not* the 'Addtional Drivers' tool. Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and enjoy your wireless.

@tuhinr.007-- If yours is not the 4311, please start your own new thread and tell us about it:```
lspci -nn -d 14e4:
```

---

