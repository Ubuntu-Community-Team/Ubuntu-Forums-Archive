---
title: "Wireless on a hp pavilion ze4500"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by surferkid993 on 2007-11-14
I'm having trouble getting my wireless internet to work on my HP pavilion ze4500
I don't understand all of this, but this is the output of "lspci -v | less":

```
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        Memory at d0400000 (32-bit, prefetchable) [size=4K]
        I/O ports at 8090 [disabled] [size=4]
        Capabilities: <access denied>

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff

00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin USB
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller
```

---

