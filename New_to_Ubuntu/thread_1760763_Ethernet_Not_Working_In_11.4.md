---
title: "Ethernet Not Working In 11.4"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by tdrusk on 2011-05-17
EDIT: I think I may have found the solution here([http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)). Verification before I try it?

Hey guys, the title describes my problem. It has worked in the past. If I log off wireless and plug in the Ethernet cable it should work off of it, but it doesn't. Maybe I am doing something wrong with network manager or the driver isn't functioning properly.  The Atheros is not working.

```
$lspci -v

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Toshiba America Info Systems Device 9602 (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: d4100000-d42fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: Toshiba America Info Systems Device fd50
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00007000-0000afff
    Memory behind bridge: d3100000-d40fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Toshiba America Info Systems Device fd50
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: d3000000-d30fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Toshiba America Info Systems Device fd50
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at c038 [size=8]
    I/O ports at c04c [size=4]
    I/O ports at c030 [size=8]
    I/O ports at c048 [size=4]
    I/O ports at c010 [size=16]
    Memory at d4307000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d4306000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d4307600 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d4305000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d4307500 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d4300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=64

00:15.0 PCI bridge: ATI Technologies Inc Device 43a0 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0f, sec-latency=0
    I/O behind bridge: 00002000-00005fff
    Memory behind bridge: d2000000-d2ffffff
    Prefetchable memory behind bridge: 00000000d1000000-00000000d1ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: ATI Technologies Inc Device 0000
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d4304000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d4307400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at b000 [size=256]
    Memory at d4200000 (32-bit, non-prefetchable) [size=64K]
    Memory at d4100000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d3100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 58-94-6b-ff-ff-52-ce-6c
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

08:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at d3000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 6000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-3f-b4-bc-60-eb-69-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c

```

---

### Post by linuxman94 on 2011-05-17
That solution should work (it has worked for other people).  Good luck!

---

