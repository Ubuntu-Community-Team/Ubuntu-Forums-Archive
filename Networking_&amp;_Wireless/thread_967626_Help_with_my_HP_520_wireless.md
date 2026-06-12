---
title: "Help with my HP 520 wireless"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by Crimson Fatalis on 2008-11-02
Hi! I'm new to the board and also new to ubuntu 8.04 hardy.

I'm having problem, where my wireless can't connect and the led light won't even start. can anyone tell me where to start and do it step by step thanks.

---

### Post by nothingspecial on 2008-11-02
Open a terminal and type ```
lspci -v
``` then post the results.

---

### Post by Crimson Fatalis on 2008-11-02
here's the result:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30d5
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30d5
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0400000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 3000 [size=8]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0480000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30d5
	Flags: bus master, fast devsel, latency 0
	Memory at f0500000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30d5
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0580000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
	Memory behind bridge: f0000000-f00fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30d5
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 3020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30d5
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f0584000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0100000-f03fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30d5
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
	Subsystem: Hewlett-Packard Company Unknown device 30d5
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 3040 [size=16]
	Capabilities: <access denied>

02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30d5
	Flags: bus master, medium devsel, latency 168, IRQ 18
	Memory at f0100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 80000000-83fff000 (prefetchable)
	Memory window 1: 84000000-87fff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001

02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30d5
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at f0101000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 2000 [size=64]
	Capabilities: <access denied>

10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 135b
	Flags: bus master, fast devsel, latency 0, IRQ 221
	Memory at f0000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

can anyone help? at least tell me what i'm supposed to do?

---

### Post by Crimson Fatalis on 2008-11-02
Sorry for the double post, but could anyone help me? i really need to fix this soon, because i need to use connection to finish my work.Thx

---

