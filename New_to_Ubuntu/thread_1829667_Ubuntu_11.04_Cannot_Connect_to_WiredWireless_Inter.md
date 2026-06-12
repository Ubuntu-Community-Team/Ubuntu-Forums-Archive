---
title: "Ubuntu 11.04 Cannot Connect to Wired/Wireless Internet"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by ingarion on 2011-08-20
Hello,
I have an HP Mini 210 running Ubuntu 11.04. About 6 hours ago, I was able to connect to the internet via both wired and wireless. The update manager popped up with some recommended updates, and after restarting my computer, both connections were lost. However, my desktop's internet connection works. I have found a couple posts with the same issue, but both their hardware and terminal outputs were different. I'm not sure what info from my computer you need, but a similar thread posted these four:

lspci -v:
```
 00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, fast devsel, latency 0  
     Capabilities: <access denied>  
     Kernel driver in use: agpgart-intel  
 

 00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, fast devsel, latency 0, IRQ 44  
     Memory at 54180000 (32-bit, non-prefetchable) [size=512K]  
     I/O ports at 30c0 [size=8]  
     Memory at 40000000 (32-bit, prefetchable) [size=256M]  
     Memory at 54000000 (32-bit, non-prefetchable) [size=1M]  
     Expansion ROM at <unassigned> [disabled]  
     Capabilities: <access denied>  
     Kernel driver in use: i915  
     Kernel modules: i915  
 

 00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, fast devsel, latency 0  
     Memory at 54100000 (32-bit, non-prefetchable) [size=512K]  
     Capabilities: <access denied>  
 

 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, fast devsel, latency 0, IRQ 45  
     Memory at 54200000 (64-bit, non-prefetchable) [size=16K]  
     Capabilities: <access denied>  
     Kernel driver in use: HDA Intel  
     Kernel modules: snd-hda-intel  
 

 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])  
     Flags: bus master, fast devsel, latency 0  
     Bus: primary=00, secondary=01, subordinate=01, sec-latency=0  
     I/O behind bridge: 00002000-00002fff  
     Memory behind bridge: 53000000-53ffffff  
     Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff  
     Capabilities: <access denied>  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp  
 

 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])  
     Flags: bus master, fast devsel, latency 0  
     Bus: primary=00, secondary=02, subordinate=02, sec-latency=0  
     I/O behind bridge: 00001000-00001fff  
     Memory behind bridge: 52000000-52ffffff  
     Prefetchable memory behind bridge: 0000000051000000-0000000051ffffff  
     Capabilities: <access denied>  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp  
 

 00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, medium devsel, latency 0, IRQ 16  
     I/O ports at 3080 [size=32]  
     Kernel driver in use: uhci_hcd  
 

 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, medium devsel, latency 0, IRQ 17  
     I/O ports at 3060 [size=32]  
     Kernel driver in use: uhci_hcd  
 

 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, medium devsel, latency 0, IRQ 18  
     I/O ports at 3040 [size=32]  
     Kernel driver in use: uhci_hcd  
 

 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, medium devsel, latency 0, IRQ 19  
     I/O ports at 3020 [size=32]  
     Kernel driver in use: uhci_hcd  
 

 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, medium devsel, latency 0, IRQ 16  
     Memory at 54205000 (32-bit, non-prefetchable) [size=1K]  
     Capabilities: <access denied>  
     Kernel driver in use: ehci_hcd  
 

 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])  
     Flags: bus master, fast devsel, latency 0  
     Bus: primary=00, secondary=03, subordinate=03, sec-latency=32  
     Capabilities: <access denied>  
 

 00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, medium devsel, latency 0  
     Capabilities: <access denied>  
     Kernel modules: iTCO_wdt  
 

 00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43  
     I/O ports at 30b8 [size=8]  
     I/O ports at 30cc [size=4]  
     I/O ports at 30b0 [size=8]  
     I/O ports at 30c8 [size=4]  
     I/O ports at 30a0 [size=16]  
     Memory at 54204000 (32-bit, non-prefetchable) [size=1K]  
     Capabilities: <access denied>  
     Kernel driver in use: ahci  
     Kernel modules: ahci  
 

 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: medium devsel, IRQ 10  
     I/O ports at 3000 [size=32]  
     Kernel modules: i2c-i801  
 

 01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)  
     Subsystem: Hewlett-Packard Company Device 3594  
     Flags: bus master, fast devsel, latency 0, IRQ 42  
     I/O ports at 2000 [size=256]  
     Memory at 50004000 (64-bit, prefetchable) [size=4K]  
     Memory at 50000000 (64-bit, prefetchable) [size=16K]  
     Capabilities: <access denied>  
     Kernel driver in use: r8169  
     Kernel modules: r8169  
 

 02:00.0 Network controller: Ralink corp. Device 5390  
     Subsystem: Hewlett-Packard Company Device 1636  
     Flags: bus master, fast devsel, latency 0, IRQ 10  
     Memory at 52000000 (32-bit, non-prefetchable) [size=64K]  
     Capabilities: <access denied>  
 
```ifconfig -a:
```
 eth0      Link encap:Ethernet  HWaddr 2c:27:d7:e5:1c:40   
           inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::2e27:d7ff:fee5:1c40/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:21077 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:89 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:1840034 (1.8 MB)  TX bytes:12007 (12.0 KB)  
           Interrupt:42 Base address:0xa000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)  
 
```iwconfig:
```
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.
 
```uname -r:
```
 2.6.38-11-generic  
 
```

---

### Post by cj13579 on 2011-08-20
it looks as though your ethernet adapter (eth0) has picked up an address: 192.168.1.107. Can you ping anything, even if it is just something else on your LAN and not the internet?

---

### Post by ingarion on 2011-08-21
I hope that I'm doing this correctly... Here are the terminal outputs.

When I ping my desktop computer, which is using the same network, with ethernet:
ping 199.111.241.17
```
PING 199.111.241.17 (199.111.241.17) 56(84) bytes of data.
```However, the opening line (name@computer:~$) never showed up on the next line. 

When I ping my desktop computer with wireless:
ping 199.111.241.17
```
connect: Network is unreachable
```Another thing is that when I click on the network icon, it doesn't give me any option to turn on wireless. Normally "Enable Wireless" would be next to "Enable Networking" and that I would have to check it, and I should be able to view all wireless connections. But neither of these items on the menu are there at all.

---

### Post by ingarion on 2011-08-21
Ah it's fixed! I figured that since I updated some stuff, I had to update my driver. So I found [this]("http://ubuntuforums.org/showthread.php?t=1740963"). The only that was different is that the patches that I had to download from post #24 were named differently, so I just patched the files that ended in .patch with the correct names. =D

---

