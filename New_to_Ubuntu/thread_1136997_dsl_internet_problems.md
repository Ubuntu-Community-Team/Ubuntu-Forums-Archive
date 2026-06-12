---
title: "dsl internet problems"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by SnaveDogg on 2009-04-25
OK, here I am still trying to get it to work.

Installed new ethernet card.

rebooted

in terminal I typed
sudo ifconfig eth1 
 
output

eth1    Link encap:Ethernet HWaddr 00:80:ad:7f:d5:6a
          BROADCAST MULTICAST MTU:1500 Metric:1
          RX packet:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets: 0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          Base address:0x3000

then I typed in sudo ifconfig eth1 up

and got

SIOCSIFFLAGS: Device or resource is busy

now what? it seems that it is recognizing the ethernet card? Am I reading that right?

I'm using a Speedstream modem, and a DYNEX wireless router. Taking the cat5 cable output from the wireless router back to the IN on the ethernet card.

how/where do I configure it?
do I use static IP or DCHP? where will I find settings?
Can I get the IP from my Windows laptop that is working (the one I am now typing on)?
Do both computers have to have the same IP address subnet mask DNS?

I have no clue what I'm doing, I just want this to work. Please help. I'm now on day 4 of this saga.

---

### Post by SnaveDogg on 2009-04-25
I did a lspci -v command in terminal ( as I saw from another post) and got this

00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 02)
    Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Intel Corporation 82810 (CGC) Chipset Graphics Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 3
    Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Memory at f4000000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AB PCI Bridge (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f4100000-f41fffff

00:1f.0 ISA bridge: Intel Corporation 82801AB ISA Bridge (LPC) (rev 02)
    Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801AB IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Intel Corporation 82801AB IDE Controller
    Flags: bus master, medium devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at 1800 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AB USB Controller (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation 82801AB USB Controller
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 1820 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AB SMBus Controller (rev 02)
    Subsystem: Intel Corporation 82801AB SMBus Controller
    Flags: medium devsel, IRQ 9
    I/O ports at 1810 [size=16]

00:1f.5 Multimedia audio controller: Intel Corporation 82801AB AC'97 Audio Controller (rev 02)
    Subsystem: Unknown device 4352:5933
    Flags: bus master, medium devsel, latency 0, IRQ 9
    I/O ports at 1200 [size=256]
    I/O ports at 1300 [size=64]

01:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
    Subsystem: Unknown device 4554:434e
    Flags: bus master, medium devsel, latency 165
    I/O ports at 3000 [size=256]
    Memory at f4100000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at f4140000 [disabled] [size=256K]
    Capabilities: <access denied>

01:0d.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
    Flags: 66MHz, medium devsel
    Memory at f4101000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

01:0d.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
    Flags: 66MHz, medium devsel
    Memory at f4102000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

01:0d.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
    Flags: 66MHz, medium devsel
    Memory at f4103000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

01:0d.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Unknown device 2020:8888
    Flags: 66MHz, medium devsel
    Memory at f4100400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

01:0e.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
    Subsystem: Mac System Co Ltd HP
    Flags: bus master, medium devsel, latency 64
    Memory at f4110000 (32-bit, non-prefetchable) [disabled] [size=64K]
    I/O ports at 3400 [disabled] [size=8]
    Capabilities: <access denied>

LOOKS LIKE "access denied" on the USB card, the ethernet card and the Conexant modem


How do I fix this??

---

