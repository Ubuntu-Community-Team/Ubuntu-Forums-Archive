---
title: "Ubuntu 14.04 Troubleshooting - can't find wireless router"
date: 2014-11-03
forum: Networking &amp; Wireless
---

### Post by Matt_Hamann on 2014-11-03
I tried to edit sudo nano /etc/network/interfaces to change my wireless router password and may have screwed up my wireless connection. I tried to delete all the edits I made but it may be too late. As it stands, I cannot connect to any wifi. I use a external wireless driver I hook into a USB. Here is all the relevant information:

```
sudo nano /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



sudo lspci -v

    00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0a <?>
	Kernel driver in use: agpgart-intel


00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at fc000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915


00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, fast devsel, latency 0
	Memory at fc400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3


00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd


00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd


00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd


00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fc704800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci-pci


00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fc700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c524
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport


00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c524
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport


00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c524
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport


00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1880 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd


00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 18a0 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd


00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18c0 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd


00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fc704c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci-pci


00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Capabilities: [50] Subsystem: Samsung Electronics Co Ltd Device c524


00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: lpc_ich


00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
	I/O ports at 1818 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 1810 [size=8]
	I/O ports at 1808 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fc704000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/16 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci


00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Samsung Electronics Co Ltd Device c524
	Flags: medium devsel, IRQ 5
	Memory at 80000000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]


06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
	Subsystem: Samsung Electronics Co Ltd Device c518
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fa000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 4000 [size=256]
	[virtual] Expansion ROM at f4000000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Vital Product Data
	Capabilities: [5c] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: sky2






ifconfig

docker0   Link encap:Ethernet  HWaddr 56:84:7a:fe:97:99  
          inet addr:172.17.42.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth0      Link encap:Ethernet  HWaddr 00:13:77:97:c5:91  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:77ff:fe97:c591/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8619590 (8.6 MB)  TX bytes:2175028 (2.1 MB)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:287856 (287.8 KB)  TX bytes:287856 (287.8 KB)


wlan0     Link encap:Ethernet  HWaddr 64:e5:99:f6:0d:2b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)







iwconfig


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
docker0   no wireless extensions.


lo        no wireless extensions.


eth0      no wireless extensions.
```

---

### Post by Bucky Ball on 2014-11-03
Welcome.

Can you see the available networks but can't connect?
What does your router password have to do with the file '/etc/network/interfaces'?
What wireless dongle are you using?
What release/flavour of Ubuntu?
Is the router name as it was?

Please use code tags when posting ```
. Neater, space saving and easier to read. See the last link in my signature. ;)

Please post the output of:

[code]sudo lshw -C network
```

I have this in /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

Click your network icon and 'edit'>wireless connection>check. Is everything setup in there to match the router? Static or Auto IP? Did you change the router name? In that case you need to change the name in Network Manager, too.

* A tip. Prior to editing important files, make a copy. E.g., using the /etc/network/interfaces file:

```
sudo cp dir /etc/network/interfaces /etc/network/interfaces.bak
```

Copy it back:

```
sudo cp dir /etc/network/interfaces.bak /etc/network/interfaces
```

---

### Post by Matt_Hamann on 2014-11-03
Sorry to trouble you, but I finally found my wireless router. Now for the original issue of how customize it to create a username and password for the WiFi.

In case you are still interested, here's what I wrote before I restarted my computer:




Can you see the available networks but can't connect?
  Yes
What does your router password have to do with the file '/etc/network/interfaces'?
  Long story short, I tried to reset my wireless router and reset the password and took the wrong steps or entered the wrong information. Stupid noob mistake.
What wireless dongle are you using?
  It's one that came with my Samsung Sens P410 laptop. It's a Korean model (I currently live in South Korea).
What release/flavour of Ubuntu?
  Lubuntu 14.04
Is the router name as it was?
  If I understand your question correctly, yes the router name is the same as it was before I attempted the edits.


To get to your troubleshooting tips:
               
```
 sudo lshw -C network 
 *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:97:c5:91
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.2.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fa000000-fa003fff ioport:4000(size=256) memory:f4000000-f401ffff
  *-network
       description: Wireless interface
       physical id: 4
       bus info: usb@2:1
       logical name: wlan0
       serial: 64:e5:99:f6:0d:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.13.0-37-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by Bucky Ball on 2014-11-03
Okay. Well, I'm guessing you must have the details wrong in Network Manager. To get to the router just put its IP address in the address bar of a browser and login. Check the name of the router. Back to Network Manager and check it matches, and so on. 

From your output everything seems to be up and running as your USB dongle is recognised as wlan0 and there is a driver loaded. Did this card work 'out of the box' in 14.04? You plugged it in and it worked? Seems to be working now. 

If you know the IP address of your router, try pinging it with:

```
ping ***.***.***.***
```

Where  ***.***.***.*** is your router IP.

You haven't changed the password? Best to plug a cable into the router and set it up properly before going much further. Not a good idea to try and do this via wireless.

---

