---
title: "Ubuntu continuously dropping wireless connection - please help!"
date: 2016-10-04
forum: Networking &amp; Wireless
---

### Post by ikse on 2016-10-04
I actually found this forum by doing a search to try and fix my problem.  What I found was a very old thread in which someone had my very same  problem, and they were helped, so the thread was marked [SOLVED],  however others have posted there for help and haven't been answered, and  it seems obvious that its because they are posting in a solved thread.  That is the reason I've created a new thread.

The thread I'm referencing above is here: [https://ubuntuforums.org/showthread.php?t=1289484](https://ubuntuforums.org/showthread.php?t=1289484)

Its clear in reading the thread that the person who needed help had a  different cause for their problem, as I can see by looking at my own  feedback that the text highlighted in bold in the topic is correct for  me. That means something ELSE is wrong. Can someone look at this and  tell me what is causing my connection to drop? I have to manually  disable and re-enable the connection to get back online, and its a  constant problem...

I'm not sure if this is helpful, but it may be worth mentioning that I use windows on the same machine and do not have this issue there...

Entering: lspci

```
ikse@ikse-HP-Pavilion-17-Notebook-PC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8610G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
```

Entering: sudo lshw -C network

```
ikse@ikse-HP-Pavilion-17-Notebook-PC:~$ sudo lshw -C network
[sudo] password for ikse: 
  *-network               
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 74:29:af:62:f7:8e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee  driverversion=3.19.0-68-generic firmware=N/A ip=192.168.1.9 latency=0  link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:38 ioport:e000(size=256) memory:fea00000-fea03fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 07
       serial: 38:63:bb:ab:36:3b
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12  latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:35 ioport:d000(size=256) memory:fe914000-fe914fff memory:fe910000-fe913fff memory:fe900000-fe90ffff

```

I greatly appreciate any helpful advice on this.

---

### Post by deadflowr on 2016-10-04
*Thread moved to **Networking & Wireless**.*

Have a quick read of the Networking sticky here:[https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")

---

### Post by jeremy31 on 2016-10-04
To start try ```
echo "options rtl8188ee fwlps=N" | sudo tee /etc/modprobe.d/rtl8188ee.conf
```
Reboot

---

