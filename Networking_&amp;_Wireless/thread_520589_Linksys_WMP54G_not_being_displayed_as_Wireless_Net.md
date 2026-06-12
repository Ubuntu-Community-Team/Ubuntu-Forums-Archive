---
title: "Linksys WMP54G not being displayed as Wireless Networking Device"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by PinkBullets9 on 2007-08-08
I recently bought the Wireless card because I wanted to bring the desktop up to my room. I get it connected and I know that Ubuntu can see it because when I put lspci into a terminal I get this result: 00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**_01:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI_**
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6200] (rev a2)
I assume that is the wireless card. But when I look into the network it gives me only two options Wired connection and Modem. It came up with wireless once but it didn't seem to work. See the attachment. I tried installing the drivers through Ndiswrapper and by compiling it from Serial Monkey neither worked. Any help is appreciated. Thanks in advance

---

### Post by noob12 on 2007-08-09
This will tell us a bit more, including what driver is currently associated and what kernel you are running.
```

sudo lshw -C network

uname -r

cat /etc/blacklist

cat /etc/modules

```

---

### Post by PinkBullets9 on 2007-08-09
I actually fixed this problem but thanks for your help. The driver got uninstalled somehow all I had to do was reinstall and start it up.

---

