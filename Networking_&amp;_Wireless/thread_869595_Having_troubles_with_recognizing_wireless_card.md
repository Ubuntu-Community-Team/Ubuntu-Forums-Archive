---
title: "Having troubles with recognizing wireless card"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by xandr55 on 2008-07-25
Here is the output from lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
sherry@sherry-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: e8000000-efffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 24c0
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 24c0
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at bf40 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 24c0
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Unknown device 24c0
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
	I/O behind bridge: 0000d000-0000efff
	Memory behind bridge: f6000000-fbffffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Unknown device 24c0
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Unknown device 0149
	Flags: bus master, medium devsel, latency 0, IRQ 7
	I/O ports at b800 [size=256]
	I/O ports at bc40 [size=64]
	Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
	Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
	Subsystem: Broadcom Corporation Unknown device 4d64
	Flags: medium devsel, IRQ 7
	I/O ports at b400 [size=256]
	I/O ports at b080 [size=128]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 0149
	Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at c000 [size=256]
	Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: <access denied>

02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
	Subsystem: Unknown device 4401:1028
	Flags: bus master, fast devsel, latency 32, IRQ 7
	Memory at faffe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
	Subsystem: Dell Truemobile 1400
	Flags: bus master, fast devsel, latency 32, IRQ 11
	Memory at faffc000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
	Subsystem: Dell Inspiron 5100
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at f6000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 24000000-27fff000 (prefetchable)
	Memory window 1: 28000000-2bfff000
	I/O window 0: 0000d000-0000d0ff
	I/O window 1: 0000d400-0000d4ff
	16-bit legacy interface ports at 0001

02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 0149
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at faffb800 (32-bit, non-prefetchable) [size=2K]
	Memory at faff4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

I don't think that they are supposed to say access denied, I also think that I need to do something along the lines of installing the driver from Cafuego's Custom Packages, but would need to do so from another computer, as the one with linux does not have internet right now...

Also there was no output from the following command

sudo pccardctl ident

which I think is not a good sign
Any help or ideas to go on would be appreciated, if more information is needed let me know...
Thank you a bunch a head of time

---

