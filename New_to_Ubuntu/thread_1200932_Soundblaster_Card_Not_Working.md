---
title: "Soundblaster Card Not Working"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Zopiac on 2009-06-30
I have a Soundblaster Prodigy 2 sound card, model SB0400, that I cannot figure out how to get working. I am running Ubuntu Studio 9.04. I have disabled the onboard audio in my BIOS.

Here is a copy of my lspci -v:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 82f1
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: ASUSTeK Computer Inc. Device 9602
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbd00000-fbefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 00000000faf00000-00000000faffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at c000 [size=8]
	I/O ports at b000 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 8000 [size=16]
	Memory at fbcff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fbcfe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fbcfd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fbcff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbcfc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbcfb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fbcfa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbcf9000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
	Subsystem: ASUSTeK Computer Inc. Device 82f1
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at d000 [size=256]
	Memory at fbef0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fbd00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 82c6
	Flags: bus master, fast devsel, latency 0, IRQ 2301
	I/O ports at e800 [size=256]
	Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
	Memory at faff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

Motherboard is Asus M3A78-EM in case it isn't listen in the lspci

Thanks in advance for help :)

---

### Post by Zopiac on 2009-06-30
I just made sure the card was securely in (it was a bit loose before) and did sudo lspci -v (just incase sudo might get something more?)

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 82f1
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: ASUSTeK Computer Inc. Device 9602
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbd00000-fbefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 82f1
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 00000000faf00000-00000000faffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 82f1
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at c000 [size=8]
	I/O ports at b000 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 8000 [size=16]
	Memory at fbcff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] SATA HBA <?>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fbcfe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fbcfd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fbcff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbcfc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbcfb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fbcfa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/1 Enable-
	Kernel driver in use: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbcf9000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
	Subsystem: ASUSTeK Computer Inc. Device 82f1
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at d000 [size=256]
	Memory at fbef0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fbd00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 82c6
	Flags: bus master, fast devsel, latency 0, IRQ 2301
	I/O ports at e800 [size=256]
	Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
	Memory at faff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 81-68-10-ec-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169

```

---

