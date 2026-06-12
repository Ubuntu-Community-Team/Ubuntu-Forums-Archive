---
title: "Wired Lan will not show up"
date: 2018-10-07
forum: Networking &amp; Wireless
---

### Post by chesc on 2018-10-07
Hello everyone

I haven't used Ubuntu for a while but I decided to install it on my old windows PC. (I'm trying to escape the Apple ecosystem)

The Wired Lan will not show up. It did work before I installed Lubuntu 18.04. When I plug the cable into my Mac I have no problems.

Any Ideas?

Thank you 

Richard

---

### Post by The Cog on 2018-10-07
For a start, can you post the output of these two commands:
```
lspci -v
ip link
```

---

### Post by chesc on 2018-10-07
```

lspci -v

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>


00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at c800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd


00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at c880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd


00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at cc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd


00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f9fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 25
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 80000000-803fffff
	Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 80400000-807fffff
	Prefetchable memory behind bridge: 00000000f8e00000-00000000f8efffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at c080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd


00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at c400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd


00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at c480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd


00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f9fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Capabilities: <access denied>


00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. 82801IB (ICH9) LPC Interface Controller
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich


00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA Controller [IDE mode] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. 82801IB (ICH9) 2 port SATA Controller [IDE mode]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at b000 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at a880 [size=8]
	I/O ports at a800 [size=4]
	I/O ports at a480 [size=16]
	I/O ports at a400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: pata_acpi


00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: medium devsel, IRQ 5
	Memory at f9fff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c_i801


00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at c000 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at b880 [size=8]
	I/O ports at b800 [size=4]
	I/O ports at b480 [size=16]
	I/O ports at b400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: pata_acpi


01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 8800 GT] (rev a2) (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 0, IRQ 24
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau


04:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Motherboard
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ec00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire_ohci

ip link

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

```

---

### Post by chesc on 2018-10-07
Thank you

---

### Post by The Cog on 2018-10-07
I don't understand that - lspci doesn't even list the existence of an ethernet card, let alone the driver in use.
Maybe someone else has an idea, but in the meantime, do you know what type of ethernet adapter you actually have?

---

### Post by chesc on 2018-10-07
It's the one built into my asus p5k pro motherboard

The Asus website says: [COLOR=#333333][FONT=&quot]PCIe Gigabit LAN controller featuring AI NET2[/FONT][/COLOR]

---

### Post by chesc on 2018-10-07
Thank you anyway!

P.S The ethernet is enabled in the bios..

---

### Post by The Cog on 2018-10-08
Bump. Somebody must have an idea.

---

