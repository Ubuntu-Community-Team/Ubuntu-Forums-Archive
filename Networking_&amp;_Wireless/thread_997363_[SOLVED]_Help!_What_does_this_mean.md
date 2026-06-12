---
title: "[SOLVED] Help! What does this mean?"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by E-Cecilia on 2008-11-29
When I type in terminal **lspci -v | less**, I get

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: b0100000-b01fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: b0200000-b02fffff
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at 8440 [size=8]
        I/O ports at 8434 [size=4]
        I/O ports at 8438 [size=8]
        I/O ports at 8430 [size=4]
log file:


*What does it basically say? I'm a newbie when it comes to this... :(*

---

### Post by E-Cecilia on 2008-11-29
I don't know if it helps but my computer specs say that I have a Broadcom 802.11b/g WLAN (I saw it in the box the computer came in)... I don't know why Ubuntu doesn't recogznize it.

---

