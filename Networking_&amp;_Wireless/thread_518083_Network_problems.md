---
title: "Network problems"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by jessecuster on 2007-08-05
I have just installed Ubuntu 7.04, it definitely recognized my wireless card, and now I can see other networks around me, including my own, but the squares next to each network are blank. If I try to connect to my own network, which I have disabled security for the meantime, it tries and tries and then will not connect.   What am I doing wrong?

---

### Post by kevdog on 2007-08-05
Can you post the following

lspci -nn (if pci network card)
lsusb -v (if usb wireless dongle)
lshw -C network
ifconfig

---

### Post by wjp.reg on 2007-08-05
> **jessecuster said:**
> I have just installed Ubuntu 7.04, it definitely recognized my wireless card, and now I can see other networks around me, including my own, but the squares next to each network are blank. If I try to connect to my own network, which I have disabled security for the meantime, it tries and tries and then will not connect.   What am I doing wrong?

> the squares next to each network are blank?  Not sure what you are referring to.

What kind of network?

Forget it.

---

### Post by jessecuster on 2007-08-05
Nevermind.

---

### Post by jessecuster on 2007-08-05
Scratch that I got the burner to work, here are the files.


lspci-nn:

00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
00:02.1 Display controller [0380]: Intel Corporation 82915G Integrated Graphics Controller [8086:2782] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
03:01.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 03)

lshw -C network:

*-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@03:01.0
       logical name: ra0
       version: 01
       serial: 00:12:17:8d:e4:b6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:dfbfe000-dfbfffff irq:22
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@03:08.0
       logical name: eth0
       version: 03
       serial: 00:13:20:6e:e3:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:dfbfd000-dfbfdfff ioport:dcc0-dcff irq:17


ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:13:20:6E:E3:6E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:12:17:8D:E4:B6  
          inet6 addr: fe80::212:17ff:fe8d:e4b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:291840 (285.0 KiB)
          Interrupt:22 Base address:0x8000

---

### Post by jessecuster on 2007-08-07
just wanted to see if anyone could help with this.

---

