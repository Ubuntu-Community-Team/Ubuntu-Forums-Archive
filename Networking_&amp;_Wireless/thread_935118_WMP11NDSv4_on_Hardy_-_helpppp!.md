---
title: "WMP11NDSv4 on Hardy - helpppp!"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by kelstar on 2008-10-01
So this wireless card: not working.

It works fine on Windows but Ubuntu doesn't see it at all.

I got the drivers from the website: they won't install. 

I got ndiswrapper from the Ubuntu site (because it wasn't there before) and installed all components. Still nothing.

Tried to install drivers again: nothing.

I've searched the threads and tried everything that they came up with. I'm losing it when it comes to the driver install. I have a few driver files, but I know the ones I need are LSIPNDS and WMP11NDS (the .inf/.sys files)

Any ideas? Or a link you could point me to?

---

### Post by seancarlgrech on 2008-10-01
check if your card is supported first
 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by seancarlgrech on 2008-10-01
open the terminal an type in: 
```
lspci -v | less
```
 
and post the results here...

---

### Post by kelstar on 2008-10-01
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: ATI Technologies Inc RS480 Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 64

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Elitegroup Computer Systems Unknown device 1b34
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at ff00 [size=8]
        I/O ports at fe00 [size=4]
        I/O ports at fd00 [size=8]
        I/O ports at fc00 [size=4]
        I/O ports at fb00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 80000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Elitegroup Computer Systems Unknown device 1b34
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at fa00 [size=8]
        I/O ports at f900 [size=4]
        I/O ports at f800 [size=8]
        I/O ports at f700 [size=4]
        I/O ports at f600 [size=16]
        Memory at fe02e000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 80080000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1b34
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1b34
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1b34
:

---

### Post by seancarlgrech on 2008-10-01
can you tell what make, model etc... is your network card?

---

