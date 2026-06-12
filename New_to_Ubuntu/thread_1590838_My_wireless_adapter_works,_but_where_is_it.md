---
title: "My wireless adapter works, but where is it?"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Cycledoc on 2010-10-08
I'm curious about the* lspci* command.  I'm using  a medialink  wireless adapter MWN-USB150N on my Inspiron 2650--it works beautifully for me.

Below is my lspci -v results.  Shouldn't the results  show the medialink?  What am I missing?  

Thanks!

[I]00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)
    Subsystem: Dell Device 00f3
    Flags: bus master, fast devsel, latency 0
    Memory at ec000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
    Flags: bus master, 66MHz, fast devsel, latency 96
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    Memory behind bridge: e0000000-e7ffffff
    Prefetchable memory behind bridge: f0000000-f7ffffff
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
    Subsystem: Dell Device 00f3
    Flags: bus master, medium devsel, latency 0, IRQ 10
    I/O ports at 1800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
    Subsystem: Dell Device 00f3
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=168
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: e8000000-e80fffff
    Prefetchable memory behind bridge: 20000000-25ffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 00f3
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1840 [size=16]
    Memory at 26000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
    Subsystem: Dell Device 00f3
    Flags: medium devsel, IRQ 10
    I/O ports at 1860 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
    Subsystem: Dell Device 00f3
    Flags: bus master, medium devsel, latency 0, IRQ 10
    I/O ports at 1c00 [size=256]
    I/O ports at 1880 [size=64]
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
    Subsystem: Conexant Systems, Inc. Device 5421
    Flags: medium devsel, IRQ 10
    I/O ports at 2400 [size=256]
    I/O ports at 2000 [size=128]
    Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
    Subsystem: Dell Device 00f3
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
    Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    [virtual] Expansion ROM at e1000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, rivafb, nouveau

02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
    Subsystem: Dell Device 00f3
    Flags: bus master, medium devsel, latency 80, IRQ 10
    I/O ports at 3000 [size=128]
    Memory at e8000000 (32-bit, non-prefetchable) [size=128]
    [virtual] Expansion ROM at 24000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: 3c59x
    Kernel modules: 3c59x

02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
    Subsystem: Dell Device 00f3
    Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
    Memory at e8001000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: 28000000-2bfff000
    I/O window 0: 00003400-000034ff
    I/O window 1: 00003800-000038ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

03:00.0 USB Controller: NEC Corporation USB (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: ohci_hcd

03:00.1 USB Controller: NEC Corporation USB (rev 41) (prog-if 10)
    Subsystem: Device 17c6:0036
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at 28001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

03:00.2 USB Controller: NEC Corporation USB 2.0 (rev ff) (prog-if ff)
    Subsystem: Device 17c6:00e1
    Flags: bus master, medium devsel, latency 68, IRQ 10
    Memory at 28002000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd[/I]

---

### Post by plucky on 2010-10-08
**MWN-USB150N**

What does ```
lsusb
``` show?

---

### Post by coffeecat on 2010-10-08
> **Cycledoc said:**
> I'm curious about the* lspci* command.

....

Shouldn't the results  show the medialink?  What am I missing?  

From man lspci:

> lspci - list all PCI devices

Your device is a USB one. Anyway, plucky has put you right.

---

### Post by Cycledoc on 2010-10-08
Simple, Many thanks

lsusb shows this:

[I]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:c00f Logitech, Inc. MouseMan Traveler/Mobile
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/I]

---

### Post by coffeecat on 2010-10-08
> **Cycledoc said:**
> *Bus 003 Device 002: ID 148f:3070 Ralink Technology, Corp.*

If the output of lsusb is a bit taciturn, googling the ID number  (148f:3070) usually helps to identify the  exact chipset. In this case it seems straightforward. 148f = Ralink and 3070 = RT3070 I believe. Not all manufacturers are as logical with their ID numbers, but you could google it if you want to double-check.

---

