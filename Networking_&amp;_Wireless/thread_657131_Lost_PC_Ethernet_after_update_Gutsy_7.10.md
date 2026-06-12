---
title: "Lost PC Ethernet after update Gutsy 7.10"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by adamitj on 2008-01-03
I have downloaded Ubuntu x86 7.10 from [www.ubuntu.com](www.ubuntu.com) and installed on an AMD 64 processor PC. 

The reasons are for my Eclipse/Java development environment, wich causes several bugs on AMD 64 platform (in this case I was not able to use AMD64 version).

I could install Ubuntu 7.10 perfectly, and it works very well. Since I installed all available updates of Ubuntu (including Kernel), I lost my ethernet connection. The linux just doesn't configure the eth0, but can detect the right PCI card.

My configuration is:
-CPU AMD 64 4200+ X2;
-2 GB RAM;
-250 GB SATA II HD;
-MB ASUS M2NPV-MX (with onboard nVidia Lan wrecked and disabled on firewall);
-VIA VT6105 [Rhine-III] PCI Ethernet controller;

The results of $ lspci is:

```
tiago@minerva:~$ lspci
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
04:09.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev ff)
```

The network icon (the one in left side of clock) cannot detect the network card too.

How can I solve this problem?

---

### Post by Predator[23rd] on 2008-01-03
Hi!

> **adamitj said:**
> How can I solve this problem?

edit your */etc/network/interfaces* file and add the lines:

[I]auto eth0
iface eth0 inet dhcp[/I]

and restart you network with **sudo /etc/init.d/networking restart**

that should solve the problem...

---

