---
title: "ubuntu 12.04 LTS, wired network not being detected after first updating"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by sambit.rc on 2013-10-27
I got a new netbook with 12.04 LTS pre-installed. Updates were applied using the ethernet connection. But after the laptop restarted following the update, the ethernet connection is not being detected.
I would be grateful if someone can help me fix this problem.

Running a System Test for networking only, the following results were obtained:

   [FONT=Liberation Serif]networking/detect PASSED[/FONT]
 
 [FONT=Liberation Serif]Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01) [/FONT] 
 [FONT=Liberation Serif]Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10) [/FONT] 
 
 [FONT=Liberation Serif]networking/internet FAILED[/FONT]
 
 [FONT=Liberation Serif]ERROR:root:Could not find def gateway info in /proc [/FONT] 
 [FONT=Liberation Serif]ERROR:root:Could not find default gateway by running route [/FONT] 

**$ /sbin/ifconfig** gives the following output:
   

> lo        Link encap:Local Loopback   

           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:2624 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:2624 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:195424 (195.4 KB)  TX bytes:195424 (195.4 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 6c:71:d9:8e:e7:ab   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**$ ip link **gives the following output:

 > 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN  

     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00  
 2: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000  
     link/ether 6c:71:d9:8e:e7:ab brd ff:ff:ff:ff:ff:ff

**$ lspci -v** gives the following output:

   > 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)  

     Subsystem: ASUSTeK Computer Inc. Device 14c7  
     Flags: bus master, fast devsel, latency 0  
     Capabilities: <access denied>  
     Kernel driver in use: agpgart-intel  
 

 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])  
     Subsystem: ASUSTeK Computer Inc. Device 14c7  
     Flags: bus master, fast devsel, latency 0, IRQ 42  
     Memory at f7800000 (64-bit, non-prefetchable) [size=4M]  
     Memory at e0000000 (64-bit, prefetchable) [size=256M]  
     I/O ports at f000 [size=64]  
     Expansion ROM at <unassigned> [disabled]  
     Capabilities: <access denied>  
     Kernel driver in use: i915  
     Kernel modules: i915  
 

 00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])  
     Subsystem: ASUSTeK Computer Inc. Device 14c7  
     Flags: bus master, medium devsel, latency 0, IRQ 41  
     Memory at f7e00000 (64-bit, non-prefetchable) [size=64K]  
     Capabilities: <access denied>  
     Kernel driver in use: xhci_hcd  
 

 00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)  
     Subsystem: ASUSTeK Computer Inc. Device 14c7  
     Flags: bus master, fast devsel, latency 0, IRQ 43  
     Memory at f7e1a000 (64-bit, non-prefetchable) [size=16]  
     Capabilities: <access denied>  
     Kernel driver in use: mei  
     Kernel modules: mei  
 

 00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])  
     Subsystem: ASUSTeK Computer Inc. Device 14c7  
     Flags: bus master, medium devsel, latency 0, IRQ 16  
     Memory at f7e18000 (32-bit, non-prefetchable) [size=1K]  
     Capabilities: <access denied>  
     Kernel driver in use: ehci_hcd  
 

 00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)  
     Subsystem: ASUSTeK Computer Inc. Device 1c33  
     Flags: bus master, fast devsel, latency 0, IRQ 44  
     Memory at f7e10000 (64-bit, non-prefetchable) [size=16K]  
     Capabilities: <access denied>  
     Kernel driver in use: snd_hda_intel  
     Kernel modules: snd-hda-intel  
 

 00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])  
     Flags: bus master, fast devsel, latency 0  
     Bus: primary=00, secondary=01, subordinate=01, sec-latency=0  
     Capabilities: <access denied>  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp  
 

 00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])  
     Flags: bus master, fast devsel, latency 0  
     Bus: primary=00, secondary=02, subordinate=02, sec-latency=0  
     Memory behind bridge: f7d00000-f7dfffff  
     Capabilities: <access denied>  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp  
 

 00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4) (prog-if 00 [Normal decode])  
     Flags: bus master, fast devsel, latency 0  
     Bus: primary=00, secondary=03, subordinate=03, sec-latency=0  
     I/O behind bridge: 0000e000-0000efff  
     Memory behind bridge: f7c00000-f7cfffff  
     Capabilities: <access denied>  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp  
 

 00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])  
     Subsystem: ASUSTeK Computer Inc. Device 14c7  
     Flags: bus master, medium devsel, latency 0, IRQ 23  
     Memory at f7e17000 (32-bit, non-prefetchable) [size=1K]  
     Capabilities: <access denied>  
     Kernel driver in use: ehci_hcd  
 

 00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)  
     Subsystem: ASUSTeK Computer Inc. Device 14c7  
     Flags: bus master, medium devsel, latency 0  
     Capabilities: <access denied>  
     Kernel modules: iTCO_wdt  
 

 00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])  
     Subsystem: ASUSTeK Computer Inc. Device 14c7  
     Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40  
     I/O ports at f0b0 [size=8]  
     I/O ports at f0a0 [size=4]  
     I/O ports at f090 [size=8]  
     I/O ports at f080 [size=4]  
     I/O ports at f060 [size=32]  
     Memory at f7e16000 (32-bit, non-prefetchable) [size=2K]  
     Capabilities: <access denied>  
     Kernel driver in use: ahci  
 

 00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)  
     Subsystem: ASUSTeK Computer Inc. Device 14c7  
     Flags: medium devsel, IRQ 10  
     Memory at f7e15000 (64-bit, non-prefetchable) [size=256]  
     I/O ports at f040 [size=32]  
     Kernel modules: i2c-i801  
 

 02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)  
     Subsystem: AzureWave Device 1186  
     Flags: bus master, fast devsel, latency 0, IRQ 17  
     Memory at f7d00000 (64-bit, non-prefetchable) [size=512K]  
     Expansion ROM at f7d80000 [disabled] [size=64K]  
     Capabilities: <access denied>  
     Kernel driver in use: ath9k  
     Kernel modules: ath9k  
 

 03:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)  
     Subsystem: ASUSTeK Computer Inc. Device 14c7  
     Flags: bus master, fast devsel, latency 0, IRQ 10  
     Memory at f7c00000 (64-bit, non-prefetchable) [size=256K]  
     I/O ports at e000 [size=128]  
     Capabilities: <access denied>

---

