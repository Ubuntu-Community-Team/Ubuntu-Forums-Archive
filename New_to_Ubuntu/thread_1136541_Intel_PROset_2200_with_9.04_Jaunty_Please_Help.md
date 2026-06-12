---
title: "Intel PROset 2200 with 9.04 Jaunty Please Help"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by AlbertT on 2009-04-25
I found another post with the same title, but to be honest it didn't answer my question because it turned out the person had something else.

PLEASE HELP!! 
Is it working? It feels like I need to turn it on somehow... I have no idea:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.







lspci -v
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 1821
    Flags: bus master, fast devsel, latency 0
    Memory at <unassigned> (32-bit, prefetchable)
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 182a
    Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 182b
    Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 1712
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Memory at feb00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc00 [size=8]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 1712
    Flags: bus master, fast devsel, latency 0
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1828
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1828
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1828
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 1829
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at febff800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=09, sec-latency=64
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe700000-fe8fffff
    Prefetchable memory behind bridge: de500000-de6fffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 1828
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Memory at 20000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1828
    Flags: medium devsel
    I/O ports at e800 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1803
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at e000 [size=256]
    I/O ports at e100 [size=64]
    Memory at 20000400 (32-bit, non-prefetchable) [size=512]
    Memory at 20000600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1826
    Flags: medium devsel, IRQ 17
    I/O ports at e200 [size=256]
    I/O ports at e300 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

01:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
    Subsystem: ASUSTeK Computer Inc. Device 1824
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at fe700000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
    Memory window 0: 24000000-27fff000 (prefetchable)
    Memory window 1: 28000000-2bfff000
    I/O window 0: 0000c000-0000c0ff
    I/O window 1: 0000c400-0000c4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

01:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
    Subsystem: ASUSTeK Computer Inc. Device 1824
    Flags: bus master, medium devsel, latency 168, IRQ 18
    Memory at fe701000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=01, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: 2c000000-2ffff000 (prefetchable)
    Memory window 1: 30000000-33fff000
    I/O window 0: 0000cc00-0000ccff
    I/O window 1: 00001000-000010ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

01:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 1827
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at fe8ff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device 1045
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at c800 [size=256]
    Memory at fe8ff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation Device 2701
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fe8fe000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200

---

### Post by Peter09 on 2009-04-25
Some laptops have a switch which will turn the wireless card on/off. Just check that (if you have one) its on.

---

### Post by AlbertT on 2009-04-25
Wow, this forum is fast. Thanks! Awesome.

There is no switch, but now it works! I have no idea why.

I have been trying for the past two days, downloading drivers, realizing ubuntu already comes with it, but it never worked and I couldn't turn on the wireless using the network icon.

I did a bunch of random commands I saw on some posts, not really knowing what I'm doing.

like:

sudo aptitude install wireless-tool

sudo aptitude install build essential

sudo aptitude install checkinstall

sudo aptitude install ieee80200-source
          
            -which didn't work.

and the wireless still wasn't working, but after reboot, it does! why? I guess I'm just asking for my own education.

haha, darn I felt I didn't learn anything. I thought I would be able to begin to understand linux.:lolflag:

[FONT=monospace][/FONT]
THANKS FOR THE REPLY.

---

### Post by AlbertT on 2009-04-25
Wow, this forum is fast. Thanks! Awesome.

There is no switch, but now it works! I have no idea why.

I have been trying for the past two days, downloading drivers, realizing ubuntu already comes with it, but it never worked and I couldn't turn on the wireless using the network icon.

I did a bunch of random commands I saw on some posts, not really knowing what I'm doing.

like:

sudo aptitude install wireless-tool

sudo aptitude install build essential

sudo aptitude install checkinstall

sudo aptitude install ieee80200-source
          
            -which didn't work.

and the wireless still wasn't working, but after reboot, it does! why? I guess I'm just asking for my own education.

haha, darn I felt I didn't learn anything. I thought I would be able to begin to understand linux.:lolflag:


THANKS FOR THE REPLY.

---

### Post by Cebonet on 2009-09-17
I have the same problem, I have a switch that used to work with previous versions of ubuntu, now I am stuck. Anyone that knows the solution?

---

