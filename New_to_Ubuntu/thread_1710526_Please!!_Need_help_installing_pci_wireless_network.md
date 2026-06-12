---
title: "Please!! Need help installing pci wireless network card!"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by smahoney77 on 2011-03-20
I am running Ubuntu on a Compaq Presario that used to have XP pro on it. It has a AMD 64 Athlon processor and i just put in a NETGEAR MA311 Network Adapter. I have looked all over the net but for some reason no one has had this problem(installing the card that is). If you can tell me exactly what I need to do to get drivers to it with no install disk and no internet (on the Compac, i have internet on my mac) or to do some stuff in terminal to activate the card to access wireless networks. I do not know much about command stuff so if you could give my step by step instructions that would be greatly appreciated.

Also if you could possibly tell me how to get Wine on the system that would be good too.

I would be very thankful to whoever can help me.

---

### Post by 5149.5 on 2011-03-20
Open terminal, enter lspci, and paste the results in a post.

---

### Post by smahoney77 on 2011-03-20
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)
03:08.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
03:09.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
03:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
```so apparently all i had to do was restart the computer because it works fine and im using the internet on it right as i type this (i love how its always the most basic answer with me.

If you notice anything wrong with this code pleas do still tell me

---

### Post by smahoney77 on 2011-03-20
If you also have suggestions on what brand HD and RAM will work well with Ubuntu that that would be awsome.

---

### Post by grahammechanical on 2011-03-20
You ask:

> Also if you could possibly tell me how to get Wine on the system that would be good too.

Answer: Load up the Ubuntu Software Centre and search for wine. First click install.

As for this;

> If you also have suggestions on what brand HD and RAM will work well with Ubuntu that that would be awsome.

You must get RAM that is compatible with your motherboard. If it works with your motherboard it will work with Ubuntu, I am sure. It is the same with hard discs. If I am wrong someone will say so.

Regards.

---

