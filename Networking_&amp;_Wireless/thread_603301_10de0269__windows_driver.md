---
title: "10de:02:69  windows driver"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Tlingit on 2007-11-05
Hello,
If anyone could help me find the windows driver for this card i would appreciate it thank you
 here is the id or the name of the card actully it is a little screw on antenna on the back of my PC

00:14.0 bridge: nVidia corporation MCP51 Ethernet controller (rev a3)
 id = 10de:0269 (rev a3

---

### Post by Tlingit on 2007-11-05
lspci

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01dd (rev a1)

02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)


```
sudo lshw -C network
```
 *-network               

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:c0:a8:df:b5:af

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g



```

---

