---
title: "HP Printer not recognized by 10.4"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by letinsh on 2010-05-13
Fairly new to Ubuntu/Linux.  Installed 9.10 a few months ago and fumbled my way around until I figured out the basics.  Thought I was doing good, so I decided to upgrade to Lynx.  

Did the upgrade and found some problems, most of which have been fixed by subsequent updates, or google-fu.  The biggest problem I'm having now is my printer.  I have an HP LaserJet 1100.  In 9.10, I plugged the sucker up, it auto-detected and that was that-no problem.  

As soon as I upgraded, it refuses to even see the printer when I plug it into the USB.  I go to System -> Admin -> Printing and get a window which has in the bottom corner "Not connected," and has the options for adding a new printer grayed out.

Any help would be appreciated!

---

### Post by -humanaut- on 2010-05-13
It could be a problem with upgrading versus a clean install. plug in the printer and type this into a terminal  ```
lspci
``` post back then ```
lsusb
``` and post back. Is it just USB or does it have the parallel port also?

---

### Post by letinsh on 2010-05-13
lspci produces:
> 00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
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
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
08:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
lsusb produces:
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 003 Device 003: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


This just has usb.
Thanks for your help!

---

### Post by letinsh on 2010-05-13
well, just installed the latest updates, restarted, and now the computer decides to recognize and install the printer / drivers.
Test printed a document and it looks fine....so I guess problem solved.  
Thanks for your help, though!

---

