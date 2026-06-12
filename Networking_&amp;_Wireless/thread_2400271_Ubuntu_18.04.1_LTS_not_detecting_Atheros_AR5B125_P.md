---
title: "Ubuntu 18.04.1 LTS not detecting Atheros AR5B125 PCI-e card"
date: 2018-09-04
forum: Networking &amp; Wireless
---

### Post by grbaset on 2018-09-04
Hello, I've just installed Ubuntu 18.04.1 and for some reason, it doesn't detect my ASUS K53E's wireless network card (Atheros AR5B125, AzureWave AW-NE186H). Now, I know the card is supported because I installed Ubuntu 16.04 in the same laptop and upgraded to 18.04 and no problems whatsoever with the card. The problem is that Ubuntu doesn't detect it at all. See lspci -v output:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. 2nd Generation Core Processor Family DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>


00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. 2nd Generation Core Processor Family Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at ddc00000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915


00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family MEI Controller
    Flags: bus master, fast devsel, latency 0, IRQ 37
    Memory at dfe0b000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me


00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family USB Enhanced Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at dfe08000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 38
    Memory at dfe00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: df400000-dfdfffff
    Prefetchable memory behind bridge: 00000000d1600000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: dea00000-df3fffff
    Prefetchable memory behind bridge: 00000000d0b00000-00000000d14fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: de000000-de9fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d09fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family USB Enhanced Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at dfe07000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. HM65 Express Chipset Family LPC Controller
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich


00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 35
    I/O ports at e0b0 [size=8]
    I/O ports at e0a0 [size=4]
    I/O ports at e090 [size=8]
    I/O ports at e080 [size=4]
    I/O ports at e060 [size=32]
    Memory at dfe06000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci


00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family SMBus Controller
    Flags: medium devsel, IRQ 5
    Memory at dfe05000 (64-bit, non-prefetchable) [size=256]
    I/O ports at e040 [size=32]
    Kernel modules: i2c_i801


02:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. ASM1042 SuperSpeed USB Host Controller
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at dea00000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


03:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
    Subsystem: ASUSTeK Computer Inc. AR8151 v2.0 Gigabit Ethernet
    Flags: bus master, fast devsel, latency 0, IRQ 39
    Memory at de000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at b000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

```
As you can see, the card doesn't appear to be detected at all. I've tried reseating it to no avail. I've tried all the solutions I've found on the Internet and nothing. rfkill list returns nothing.

Here's the pastebin: [http://paste.ubuntu.com/p/3yKr3hvRzH/](http://paste.ubuntu.com/p/3yKr3hvRzH/).

EDIT: I've booted Windows 10 (it's a dual boot) and it doesn't detect it either (checked on Device Manager). So it seems that unfortunately it might be a hardware problem...

---

### Post by grbaset on 2018-09-05
I've solved the problem. I had two suspects: the PCI-e bus and the BIOS settings. Guess which one was wrong. For some reason unknown to me now, I locked the network card in the "Security" tab. Doh! Oops! Now it works in both OS.

---

