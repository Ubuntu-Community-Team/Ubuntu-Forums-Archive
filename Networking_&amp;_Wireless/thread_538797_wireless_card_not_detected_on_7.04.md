---
title: "wireless card not detected on 7.04?"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by sharmar on 2007-08-30
Could you let me know why the wireless card is not detected on ubuntu 7.04 but is detected on vista.

---

### Post by bmartin on 2007-08-30
Yes. I imagine your card is detected, but the drivers for your card are probably not present.

What kind of card is it? Do you know what chipset it uses?

If it's a USB card, what is the output of the **lsusb** command? Otherwise, look at the output of **lspci** and paste any lines that might indicate what your wireless is.

---

### Post by luisromangz on 2007-08-30
Because your wireless card's manufacturer doesn't provide open specification so drivers can't be build with relative ease.

---

### Post by sharmar on 2007-08-30
Thanks for your reply.

The wireless works on windows but not on ubuntu 7.04. The wired internet does work though on ubuntu. So it does connect to the router but is not picking the wireless connection. Please help me with this.

ON ifconfig I get this.

eth0 Link encap:Ethernet HWaddr 00:163:A7:1F:48
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:19 Base address:0x6000

eth0:avah Link encap:Ethernet HWaddr 00:163:A7:1F:48
inet addr:169.254.5.150 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:19 Base address:0x6000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:14 errors:0 dropped:0 overruns:0 frame:0
TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1204 (1.1 KiB) TX bytes:1204 (1.1 KiB)

---

### Post by bmartin on 2007-08-30
@sharmar: Open up a terminal (Applications > Accessories > Terminal), enter **lspci** and hit enter, and post the output here. Then post the output of **lsusb**. One of those should tell us what your wireless card is and we should be able to get it working.

---

### Post by sharmar on 2007-08-30
Thanks a lot for helping me out with this. i have put the outputs below. 

Output of lspci:

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
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
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
01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


Output of lsusb:

Bus 002 Device 002: ID 0c45:62c0 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by bmartin on 2007-08-31
You have a Broadcom chipset. You'll probably want [this thread]("http://ubuntuforums.org/showthread.php?t=405990"). It has a graphical installer.

---

