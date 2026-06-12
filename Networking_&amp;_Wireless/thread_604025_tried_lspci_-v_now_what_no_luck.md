---
title: "tried lspci -v now what no luck"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Tlingit on 2007-11-05
I cant pick out my card will some one point it out for me???  I could when i set my laptop up but on my pc i cant seem to find the right one will some one please point it out for me??
```
 lspci -v

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0

        Capabilities: <access denied>



00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0



00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0

        Capabilities: <access denied>



00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])

        Flags: bus master, fast devsel, latency 0

        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

        I/O behind bridge: 0000a000-0000afff

        Memory behind bridge: fa000000-fcffffff

        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff

        Capabilities: <access denied>



00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0

        Capabilities: <access denied>



00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0



00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel, IRQ 11

        I/O ports at 4c00 [size=64]

        I/O ports at 4c40 [size=64]

        Capabilities: <access denied>



00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20

        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16

        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]

        Capabilities: <access denied>



00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17

        I/O ports at 09f0 [size=8]

        I/O ports at 0bf0 [size=4]

        I/O ports at 0970 [size=8]

        I/O ports at 0b70 [size=4]

        I/O ports at e400 [size=16]

        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])

        Subsystem: Hewlett-Packard Company Unknown device 2a38

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18

        I/O ports at 09e0 [size=8]

        I/O ports at 0be0 [size=4]

        I/O ports at 0960 [size=8]

        I/O ports at 0b60 [size=4]

        I/O ports at d000 [size=16]

        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])

        Flags: bus master, 66MHz, fast devsel, latency 0

        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128

        I/O behind bridge: 0000b000-0000bfff

        Memory behind bridge: fde00000-fdefffff

        Prefetchable memory behind bridge: fdd00000-fddfffff

        Capabilities: <access denied>



00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17

        Memory at fe024000 (32-bit, non-prefetchable) [size=16K]

        Capabilities: <access denied>



00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16

        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]

        I/O ports at cc00 [size=8]

        Capabilities: <access denied>



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



01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01dd (rev a1) (prog-if 00 [VGA])

        Subsystem: ASUSTeK Computer Inc. Unknown device 034b

        Flags: bus master, fast devsel, latency 0, IRQ 5

        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]

        Memory at e0000000 (64-bit, prefetchable) [size=256M]

        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]

        Expansion ROM at fcfe0000 [disabled] [size=128K]

        Capabilities: <access denied>



02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, medium devsel, latency 32, IRQ 19

        Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



tlingit@Eeshon:~$ 



 
```

---

