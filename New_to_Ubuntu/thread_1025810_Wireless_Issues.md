---
title: "Wireless Issues"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Zorinea on 2008-12-30
I have a HP laptop which comes with Vista. The wireless range reaches to the desk very easily. 

When I put Ubuntu on and follow these instructions:

> In the System - Administration menu you choose Software Sources and enable the Hardy Proposed updates (hardy-proposed).

Updating your system will then update your kernel too. Once the update is complete, reboot your system and run this command in the terminal:

sudo aptitude install b43-fwcutter

When it asks to download firmware, allow it to do so.

After it's finished, reboot again and it should work

Daniel

The wireless range is not as far. It's the only reason why I'm still on Windows. Any help please?

---

### Post by Copitox on 2009-01-24
Tell me what your wireless card is... i'm guessing is the same as mine's. 

Open a terminal (Aplications> Accesories> Terminal) and run

lspci 

then paste what it says here!

If i'm right, i can tell you how to set it up!


EDIT: sorry, i meant wireless card!

---

### Post by ellis rowell on 2009-02-14
I have the same problem with an Acer Aspire 5101.

Wireless Lan details = 06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Is this enough info?

---

### Post by Zorinea on 2009-03-11
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

