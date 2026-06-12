---
title: "Help w/ wireless, ndiswrapper, Feisty"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by johnacook on 2007-05-06
I hate to start a new thread, but most others stop short, assuming evrything went well. So far:
 
Dowloaded, installed ndiswrapper-1.43 from SF. - didn't work
Finally thru combination of ndiswrapper-utils, -common, and everything I could find, and ndisgtk, I am able to install drivers.
WG311v3 - dmesg indicated that driver was 32-bit and wouldn't work. - removed.
Mrv8000c - installed, but configuration doesn't look right.
 
Please take a look and let me know what's next: 
 
john@main:~$ sudo ndiswrapper -l
mrv8000c : driver installed
device (11AB:1FAA) present
 
john@main:~$ ifconfig
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:400 (400.0 b) TX bytes:400 (400.0 b)
 
john@main:~$ sudo ifconfig
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:400 (400.0 b) TX bytes:400 (400.0 b)
 
john@main:~$ sudo lshw -C network
*-network UNCLAIMED 
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 9
bus info: pci@02:09.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: latency=32
resources: iomemory:f7ff0000-f7ffffff iomemory:f7fe0000-f7feffff irq:10
 
john@main:~$ sudo iwconfig
lo no wireless extensions.
 
john@main:~$ sudo iwconfig wlan0
wlan0 No such device
 
[EMAIL="john@main:~$"]john@main:~$[/EMAIL]

---

