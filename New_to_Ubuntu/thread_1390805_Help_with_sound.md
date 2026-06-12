---
title: "Help with sound"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Drenriza on 2010-01-26
I cannot get my

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03). To work. Hope someone can help me.

Ido not run pulseaudio, on my laptop only alsamixer.

cristian@cristian-linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
cristian@cristian-linux:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 7110 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, fast devsel, latency 0
	Memory at d8400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, fast devsel, latency 0, IRQ 217
	Memory at d8800000 (32-bit, non-prefetchable) [size=128K]
	Memory at d8824000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 70e0 [size=32]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 70c0 [size=32]
	Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 70a0 [size=32]
	Capabilities: <access denied>

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 7080 [size=32]
	Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at d8825c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d8820000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: d8700000-d87fffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: d8600000-d86fffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=43, sec-latency=0
	I/O behind bridge: 00005000-00006fff
	Memory behind bridge: d4000000-d7ffffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=44, subordinate=84, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: d0000000-d3ffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 7060 [size=32]
	Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 7040 [size=32]
	Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 7020 [size=32]
	Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at d8825800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=85, subordinate=89, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d8500000-d85fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 219
	I/O ports at 7108 [size=8]
	I/O ports at 711c [size=4]
	I/O ports at 7100 [size=8]
	I/O ports at 7118 [size=4]
	I/O ports at 7000 [size=32]
	Memory at d8825000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation Unknown device 4236
	Subsystem: Intel Corporation Unknown device 1011
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at d8600000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

85:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at d8501000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

85:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
	Subsystem: Hewlett-Packard Company Unknown device 30db
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at d8501900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

85:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev bb)
	!!! Invalid class 0880 for header type 02
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at d8501800 (32-bit, non-prefetchable) [size=256]
	Bus: primary=85, secondary=86, subordinate=89, sec-latency=176
	Memory window 0: dc000000-dffff000 (prefetchable)
	Memory window 1: f0000000-f3fff000
	I/O window 0: 00002000-000020ff
	I/O window 1: 00002400-000024ff
	<access denied to the rest>

85:09.3 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ff) (prog-if ff)
	!!! Unknown header type 7f

---

