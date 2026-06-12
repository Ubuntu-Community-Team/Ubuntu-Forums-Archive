---
title: "Conexant modem with linuxant HSF drivers causing soft lock?"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by yarri on 2006-12-29
Hi!

	I am trying to setup Ubuntu Dapper on my parents box. They have a Conexant modem so I have bought linuxant drivers. They seem to work just fine for the moment, but after some time PC just hangs. I am unable to do anything with it. It does not respond to the keyboard nor mouse (so I cannot use ctrl+alt+f1 to access the console. In this situation computer is unusable. Nevertheless I have noticed a message saying: BUG: soft lockup on CPU#0 detected. - it was printed in the console a a moment be for hangup. I have a dapper ubuntu with kernel 2.6.15-23-686 
Do you have any idea what could be the reason and how could I resolve it? What more information should I provide?

                                                       Thank you very much for help
                                                                              Yarri

 
This is lspci output:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x]  (rev 44)
        Flags: bus master, medium devsel, latency 0
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 1.0

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro13 3x AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: dc000000-ddffffff
        Prefetchable memory behind bridge: d0000000-d7ffffff
        Capabilities: [80] Power Management version 2

0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev  23)
        Subsystem: VIA Technologies, Inc. VT82C596/A/B PCI to ISA Bridge
        Flags: bus master, stepping, medium devsel, latency 0

0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 32
        I/O ports at d000 [size=16]
        Capabilities: [c0] Power Management version 2

0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 11) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at d400 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
        Flags: medium devsel

0000:00:10.0 Communication controller: Conexant HSF 56k Data/Fax/Voice Modem (Wo rldW SmartDAA) (rev 01)
        Subsystem: Conexant HSF 56k Data/Fax/Voice Modem (WorldW SmartDAA)
        Flags: medium devsel, IRQ 5
        Memory at de020000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at d800 [size=8]
        Capabilities: [40] Power Management version 2

0000:00:11.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)
        Subsystem: Aureal Semiconductor AU8820 Vortex Digital Audio Processor
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at de000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at dc00 [size=8]
        I/O ports at e000 [size=8]
        Capabilities: [dc] Power Management version 1

0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 11
        Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at dd000000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 2.0

---

