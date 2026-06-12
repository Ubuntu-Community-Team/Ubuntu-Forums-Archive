---
title: "frusterating plz help"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by justin111 on 2008-04-27
hi i have been trying and try for the past few weeks to get a distro with nice size repositories to work with my card dwl-g122 b1 last night after 5 reinstall of mint 4.0 and a few hours of work i gave up for the night and downloaded hardy heron i booted up the live CD and bam it worked then after install i restarted and booted up normally and it doesn't work what did i do to deserve this:confused:

---

### Post by Das Oracle on 2008-04-27
what is your output of running 'lspci' ?

---

### Post by justin111 on 2008-04-27
> **Das Oracle said:**
> what is your output of running 'lspci' ?


00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

---

### Post by justin111 on 2008-04-27
is that what you wanted

---

### Post by Monicker on 2008-04-27
> **justin111 said:**
> is that what you wanted

That is a d-link usb device correct?  It won't show up in lspci.  Try lsusb.


I don't know how well its supported in HH, but a forum search should turn up more info.


This might help:

[https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29")

---

### Post by justin111 on 2008-04-27
Bus 002 Device 006: ID 08ec:0008 M-Systems Flash Disk Pioneers 
Bus 002 Device 003: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000

---

