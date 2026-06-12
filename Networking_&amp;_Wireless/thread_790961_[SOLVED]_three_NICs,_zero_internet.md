---
title: "[SOLVED] three NICs, zero internet"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by marksilverman on 2008-05-11
I have a HP Evo N800c laptop where I just installed Hardy Heron. I have three network cards and I can't get any of them to work! System -> Admin -> Network shows nothing and the only device under Network Tools is the "Loopback interface".

first card: Intel PRO/100 P Mobile Combo Adapter (this card might be broken)
second card: NETGEAR WG511 v2 Wireless PCMCIA
third card: Compaq Wireless LAN Multiport W200

I found directions about getting the W200 to work on the wifi forum, but it requires a working connection (ironic).

output from ifconfig:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70184 (68.5 KB)  TX bytes:70184 (68.5 KB)

output from lspci (WG511v2 is at the end):
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
	Subsystem: Compaq Computer Corporation Unknown device 004a
	Flags: bus master, fast devsel, latency 0
	Memory at a0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: [e4] Vendor Specific Information
	Capabilities: [a0] AGP version 2.0

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 80300000-803fffff
	Prefetchable memory behind bridge: 88000000-900fffff

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 80000000-802fffff

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Compaq Computer Corporation Unknown device 004a
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 4440 [size=16]
	Memory at 40000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
	Subsystem: Compaq Computer Corporation Unknown device 004a
	Flags: bus master, medium devsel, latency 0, IRQ 5
	I/O ports at 4000 [size=256]
	I/O ports at 4400 [size=64]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA controller])
	Subsystem: Compaq Computer Corporation Unknown device 004a
	Flags: bus master, stepping, 66MHz, medium devsel, latency 66, IRQ 11
	Memory at 88000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at 80300000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at 90000000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
	Capabilities: [50] Power Management version 2

02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
	Subsystem: AMBIT Microsystem Corp. Evo N600c
	Flags: bus master, medium devsel, latency 66, IRQ 5
	Memory at 80200000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 2400 [size=8]
	I/O ports at 2000 [size=256]
	Capabilities: [f8] Power Management version 2

02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
	Subsystem: Compaq Computer Corporation Unknown device 004a
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 80080000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 44000000-47fff000 (prefetchable)
	Memory window 1: 48000000-4bfff000
	I/O window 0: 00002800-000028ff
	I/O window 1: 00002c00-00002cff
	16-bit legacy interface ports at 0001

02:0e.0 USB Controller: NEC Corporation USB (rev 41) (prog-if 10 [OHCI])
	Subsystem: Compaq Computer Corporation Unknown device 004a
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at 80100000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 2

02:0e.1 USB Controller: NEC Corporation USB (rev 41) (prog-if 10 [OHCI])
	Subsystem: Compaq Computer Corporation Unknown device 004a
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at 80180000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 2

02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Compaq Computer Corporation Unknown device 004a
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at 80280000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Power Management version 2

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
	Subsystem: Netgear WG511v2 54 Mbps Wireless PC Card
	Flags: 66MHz, medium devsel, IRQ 11
	Memory at 48000000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Memory at 48010000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: [40] Power Management version 2

please help!

thanks,
Mark

---

### Post by superprash2003 on 2008-05-11
have you tried restriced drivers manager under system->administration .. ensure that any LAN or WLAN cards if listed is enabled

---

### Post by marksilverman on 2008-05-11
I've got nothing called "restriced drivers manager" in my system administration menu. is it somewhere else?

---

### Post by marksilverman on 2008-05-11
oh hang on, apparantly it's now called "hardware drivers". Nothing comes up ("No proprietary drivers are in use on this system"). other ideas?

---

### Post by marksilverman on 2008-05-11
additional info:

lshw -C network:
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 3
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=0

lsusb:
Bus 003 Device 004: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by dmizer on 2008-05-11
okay, you'll need ndiswrapper.  here's how to install ndiswrapper when you don't have internet connection:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#head-6c3f75213ff90d97beac83ac70cd1a6574a16d27](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#head-6c3f75213ff90d97beac83ac70cd1a6574a16d27)

once you have ndiswrapper installed, try this howto:
[http://ubuntuforums.org/showthread.php?t=305983](http://ubuntuforums.org/showthread.php?t=305983)

---

### Post by marksilverman on 2008-05-12
Thanks, it's working! It was hard to find the driver (the NETGEAR web site only provides an EXE file, not INF), but I worked it out.

---

### Post by dmizer on 2008-05-12
congrats!  glad to hear it.

now, mark this thread as resolved (with the thread tools dropdown menu) so others know that there is a solution here. :)

---

