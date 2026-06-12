---
title: "Sound Problems"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by John A on 2010-08-19
I'm posting this again as I got no help last time. I have the usual problem of "My sound is not working". I'd love for any help. I have a few images and my output from ```
lspci
``` ```
lspci -v
``` and ```
aplay -l
```. Please help me as soon as possible. Thanks, John.

P.S - I can't really do anything with the speaker as it is hidden in the case.
-------------------------------------------------------------------------------------------------------
john@john-desktop:/usr/src$ lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
-------------------------------------------------------------------------------------------------------
john@john-desktop:/usr/src$ lspci -v
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dfd00000-dfefffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff00 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at dfffbc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: dfc00000-dfcfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: dfb00000-dfbfffff
    Prefetchable memory behind bridge: 00000000d0200000-00000000d03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 01da
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fec0 [size=16]
    I/O ports at ecc0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    Subsystem: Dell Device 01da
    Flags: medium devsel, IRQ 9
    Memory at dfffbb00 (32-bit, non-prefetchable) [size=256]
    I/O ports at ece0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell Device 01da
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe40 [size=8]
    I/O ports at fe50 [size=4]
    I/O ports at fe60 [size=8]
    I/O ports at fe70 [size=4]
    I/O ports at fed0 [size=16]
    I/O ports at ecd0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
    Subsystem: Dell Device 0402
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dfde0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at dc00 [size=256]
    Expansion ROM at dfe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)
    Subsystem: Dell Device 0403
    Flags: bus master, fast devsel, latency 0
    Memory at dfdf0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at dfbf0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3
-------------------------------------------------------------------------------------------------------
john@john-desktop:/usr/src$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by candtalan on 2010-08-19
Sorry to hear you are having problems.

It might sound obvious but ensure that all that is available is turned up to high values (be aware if it starts loud! )

also check that nothing is 'muted'
on one of your screen shots it seems that an input is muted

hth

---

### Post by John A on 2010-08-19
> **candtalan said:**
> Sorry to hear you are having problems.

It might sound obvious but ensure that all that is available is turned up to high values (be aware if it starts loud! )

also check that nothing is 'muted'
on one of your screen shots it seems that an input is muted

hth

I unmuted the the input and threw it up to 100% unamplified.

---

### Post by candtalan on 2010-08-19
> **John A said:**
> I unmuted the the input and threw it up to 100% unamplified.

you have sound ok now, or what?

---

### Post by John A on 2010-08-19
> **candtalan said:**
> you have sound ok now, or what?

No, I still have no sound.

---

