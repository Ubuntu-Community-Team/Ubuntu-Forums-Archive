---
title: "Realtek RTL8188CE: Wireless not working"
date: 2015-02-07
forum: Networking &amp; Wireless
---

### Post by jrigby on 2015-02-07
I am very new to linux and very new to the CLI.  I am running Ubuntu 14.04 LTS. When I was running from disk my wireless worked fine. Now that I have installed the wireless connection works intermittently, and when it does work the speeds are not good. I am currently tethered to my cellphone, and have a pretty good connection. I have run the following commands:
 

 lspci > ~/hwinfo.txt lsusb >> ~/hwinfo.txt lshw -C network >>
~/hwinfo.txt 


And here is the
result: 
```

00:00.0 Host
bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root
Complex
00:01.0 VGA
compatible controller: Advanced Micro Devices, Inc. [AMD/ATI]
BeaverCreek [Radeon HD 6520G]
00:01.1 Audio
device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio
[Radeon HD 6500D and 6400G-6600G series]
00:02.0 PCI bridge:
Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:11.0 SATA
controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller
[AHCI mode] (rev 40)
00:12.0 USB
controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI
Controller (rev 11)
00:12.2 USB
controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI
Controller (rev 11)
00:13.0 USB
controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI
Controller (rev 11)
00:13.2 USB
controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI
Controller (rev 11)
00:14.0 SMBus:
Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 13)
00:14.1 IDE
interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller
00:14.2 Audio
device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev
01)
00:14.3 ISA bridge:
Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge:
Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge:
Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE
port 0)
00:15.1 PCI bridge:
Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE
port 1)
00:15.2 PCI bridge:
Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE
port 2)
00:16.0 USB
controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI
Controller (rev 11)
00:16.2 USB
controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI
Controller (rev 11)
00:18.0 Host
bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor
Function 0 (rev 43)
00:18.1 Host
bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor
Function 1
00:18.2 Host
bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor
Function 2
00:18.3 Host
bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor
Function 3
00:18.4 Host
bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor
Function 4
00:18.5 Host
bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor
Function 6
00:18.6 Host
bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor
Function 5
00:18.7 Host
bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor
Function 7
04:00.0 Network
controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n
WiFi Adapter (rev 01)
05:00.0 Ethernet
controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI
Express Fast Ethernet controller (rev 05)
Bus 003 Device 001:
ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001:
ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003:
ID 04f2:b289 Chicony Electronics Co., Ltd 
Bus 002 Device 001:
ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001:
ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005:
ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 001 Device 001:
ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001:
ID 1d6b:0001 Linux Foundation 1.1 root hub
  *-network
       description:
Wireless interface
       product:
RTL8188CE 802.11b/g/n WiFi Adapter
       vendor:
Realtek Semiconductor Co., Ltd.
       physical id:
0
       bus info:
pci@0000:04:00.0
       logical
name: wlan0
       version: 01
       serial:
d0:df:9a:f8:39:e4
       width: 64
bits
       clock:
33MHz
      
capabilities: bus_master cap_list ethernet physical wireless
      
configuration: broadcast=yes driver=rtl8192ce
driverversion=3.13.0-45-generic firmware=N/A latency=0 link=no
multicast=yes wireless=IEEE 802.11bgn
       resources:
irq:16 ioport:e000(size=256) memory:fea00000-fea03fff
  *-network
       description:
Ethernet interface
       product:
RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor:
Realtek Semiconductor Co., Ltd.
       physical id:
0
       bus info:
pci@0000:05:00.0
       logical
name: eth0
       version: 05
       serial:
38:60:77:66:9a:33
       size:
10Mbit/s
       capacity:
100Mbit/s
       width: 64
bits
       clock:
33MHz
      
capabilities: bus_master cap_list ethernet physical tp mii 10bt
10bt-fd 100bt 100bt-fd autonegotiation
      
configuration: autonegotiation=on broadcast=yes driver=r8169
driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw
latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources:
irq:45 ioport:d000(size=256) memory:d0004000-d0004fff
memory:d0000000-d0003fff
  *-network
       description:
Ethernet interface
       physical id:
1
       logical
name: usb0
       serial:
02:04:54:55:62:34
      
capabilities: ethernet physical
      
configuration: broadcast=yes driver=rndis_host
driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.218
link=yes multicast=yes
  *-network
       description:
Wireless interface
       product:
RTL8188CE 802.11b/g/n WiFi Adapter
       vendor:
Realtek Semiconductor Co., Ltd.
       physical id:
0
       bus info:
pci@0000:04:00.0
       logical
name: wlan0
       version: 01
       serial:
d0:df:9a:f8:39:e4
       width: 64
bits
       clock:
33MHz
      
capabilities: pm msi pciexpress bus_master cap_list ethernet physical
wireless
      
configuration: broadcast=yes driver=rtl8192ce
driverversion=3.13.0-45-generic firmware=N/A latency=0 link=no
multicast=yes wireless=IEEE 802.11bgn
       resources:
irq:16 ioport:e000(size=256) memory:fea00000-fea03fff
  *-network
       description:
Ethernet interface
       product:
RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor:
Realtek Semiconductor Co., Ltd.
       physical id:
0
       bus info:
pci@0000:05:00.0
       logical
name: eth0
       version: 05
       serial:
38:60:77:66:9a:33
       size:
10Mbit/s
       capacity:
100Mbit/s
       width: 64
bits
       clock:
33MHz
      
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet
physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
      
configuration: autonegotiation=on broadcast=yes driver=r8169
driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw
latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources:
irq:45 ioport:d000(size=256) memory:d0004000-d0004fff
memory:d0000000-d0003fff
  *-network
       description:
Ethernet interface
       physical id:
1
       logical
name: usb0
       serial:
02:04:54:55:62:34
      
capabilities: ethernet physical
      
configuration: broadcast=yes driver=rndis_host
driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.218
link=yes multicast=yes
```

---

