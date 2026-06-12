---
title: "Device Not Ready (Firmware missing)"
date: 2016-06-18
forum: Networking &amp; Wireless
---

### Post by Eranga_Gamagedara on 2016-06-18
[B]Im using Ubuntu 16.04 LTS in network menu shown Device Not Ready (Firmware missing). please help me to get work my pc's wireless adaptor.

when i run "lspci -v" it shows
[/B]
```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
    Subsystem: Hewlett-Packard Company Haswell-ULT DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: hsw_uncore

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Haswell-ULT Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at b2000000 (64-bit, non-prefetchable) [size=4M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
    Subsystem: Hewlett-Packard Company Haswell-ULT HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at b2710000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04) (prog-if 30 [XHCI])
    Subsystem: Hewlett-Packard Company 8 Series USB xHCI HC
    Flags: bus master, medium devsel, latency 0, IRQ 42
    Memory at b2700000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
    Subsystem: Hewlett-Packard Company 8 Series HECI
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at b2718000 (64-bit, non-prefetchable) [size=32]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
    Subsystem: Hewlett-Packard Company 8 Series HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at b2714000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 9fb00000-9fcfffff
    Prefetchable memory behind bridge: 000000009fd00000-000000009fefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 2 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: b1000000-b1ffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000b0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: b2600000-b26fffff
    Prefetchable memory behind bridge: 00000000b2400000-00000000b24fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 6 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: b2500000-b25fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company 8 Series USB EHCI
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at b271c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
    Subsystem: Hewlett-Packard Company 8 Series LPC Controller
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company 8 Series SATA Controller 1 [AHCI mode]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 45
    I/O ports at 5088 [size=8]
    I/O ports at 5094 [size=4]
    I/O ports at 5080 [size=8]
    I/O ports at 5090 [size=4]
    I/O ports at 5060 [size=32]
    Memory at b271b000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
    Subsystem: Hewlett-Packard Company 8 Series SMBus Controller
    Flags: medium devsel, IRQ 11
    Memory at b2719000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5040 [size=32]
    Kernel modules: i2c_i801

02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company RTS5229 PCI Express Card Reader
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at b1000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
    Flags: bus master, fast devsel, latency 0, IRQ 44
    I/O ports at 3000 [size=256]
    Memory at b2600000 (64-bit, non-prefetchable) [size=4K]
    Memory at b2400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

09:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
    DeviceName:  
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b2510000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci, rt3290sta

09:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at b2500000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>


```

---

