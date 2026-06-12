---
title: "Thinkpad T460s + 19.04 = No Bluetooth?"
date: 2019-06-05
forum: Networking &amp; Wireless
---

### Post by Gordon_Copestake on 2019-06-05
I have a Thinkpad T460s with Ubuntu 19.04 fresh install.
Everything works fine apart from bluetooth.
I believe this laptop has an Intel 8087:0a2b Bluetooth adapter

Any hints as to what I need to do to enable bluetooth?

lspci:
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Skylake GT2 [HD Graphics 520] (rev 07)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:16.3 Serial controller: Intel Corporation Device 9d3d (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #3 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection I219-LM (rev 21)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
04:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)

lsusb:
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04ca:7058 Lite-On Technology Corp. 
Bus 001 Device 008: ID 1199:9079 Sierra Wireless, Inc. 
Bus 001 Device 007: ID 1fd2:5003  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2019-06-05
Is there anything in BIOS settings about bluetooth?  It should show in lsusb results

---

### Post by him610 on 2019-06-05
> I believe this laptop has an Intel 8087:0a2b Bluetooth adapter
What makes you think this? From what I have discovered, the Intel 8087:0a2b is paired with Intel 8265/8275 adapters, not the 8260 device; although, I could be wrong.

How about displaying the results of *rfkill list*

---

