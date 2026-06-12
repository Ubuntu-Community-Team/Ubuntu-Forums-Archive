---
title: "Unable to Connect to Internet"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by azntnkn on 2009-10-05
I recently installed Ubuntu 9.04 without any problems. However, I have not been able to connect to the internet wired or wireless. I've looked around the forums and have tried various things, but nothing has worked thus far.

I'm running a Gateway and dual-booting Windows and Ubuntu. I'm not sure exactly what information is needed so I'll include what I've seen around the forums:



> 
-----sudo lshw -C network-----
------------------------------

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:50:77:cf
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d2:9e:cb:0c:43:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

----lspci-----
--------------

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

-----ifconfig-----
------------------

eth0      Link encap:Ethernet  HWaddr 00:03:25:50:77:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

-----iwconfig------
-------------------

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



-----netstat -r -----
---------------------

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

-----iwlist scanning -----
--------------------------

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.



Thanks in advance for any help, and if there is anything else needed, let me know.

---

### Post by zvacet on 2009-10-06
Did you tried in network manager select> wired and there put your setings.You can also try to do the same in dsl.

---

### Post by Bucky Ball on 2009-10-06
System->Administration->Hardware Drivers and make sure there is nothing disabled for the wireless card ...

---

### Post by azntnkn on 2009-10-08
Thanks for the suggestions; nothing has worked so far though. I've tried going through the network manager before, but it didn't work. I tried again, same result. 

I forgot to mention that I'm running a laptop. Going through hardware drivers showed no results.

---

