---
title: "Ubuntu does not recognise LAN chip or mainboard"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by FloSynergy on 2007-06-19
Hi all,

I am desperately seeking help to get my new computer working right:
AM64x2
Biostar NF61S Micro AM2 SE
2Gb RAM
80Gb IDE HDD

I have checked out numerous posts and also the [URL="https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check"]WifiDocs/WirelessTroubleshootingGuide 
[/URL] to try and get my system to connect to the net.

It seems that there is an issue with Ubuntu recognizing the actual mainboard card and all chips on it - the LAN chip is a realtek 8201cl phy.

sudo pccardctl ident yields nothing.
 ifconfig -a yields the following:

florian@florian-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:24947 (24.3 KiB)  TX bytes:24947 (24.3 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lspci -v yields the following:
florian@florian-desktop:~$ lspci -v
0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 03ea (rev a1)
        Subsystem: nVidia Corporation: Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 03e0 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 3407
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation: Unknown device 03eb (rev a2)
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 3407
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at fc00 [size=64]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <available only to root>

0000:00:01.2 RAM memory: nVidia Corporation: Unknown device 03f5 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 3407
        Flags: 66MHz, fast devsel

0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 03f1 (rev a2) (p rog-if 10 [OHCI])
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 3407
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 03f2 (rev a2) (p rog-if 20 [EHCI])
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 3407
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 03f3 (rev a1) (prog- if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fdf00000-fdffffff
        Prefetchable memory behind bridge: fd800000-fd8fffff
        Capabilities: <available only to root>

0000:00:05.0 0403: nVidia Corporation: Unknown device 03f0 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 820d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 03ec (rev a2) (pr og-if 8a [Master SecP PriP])
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 3407
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:07.0 Bridge: nVidia Corporation: Unknown device 03ef (rev a2)
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 2505
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ec00 [size=8]
        Capabilities: <available only to root>

0000:00:08.0 RAID bus controller: nVidia Corporation: Unknown device 03f6 (rev a 2) (prog-if 85)
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 5405
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d800 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 03e8 (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: 00000000fdd00000-00000000fdd00000
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fdc00000-fdcfffff
        Prefetchable memory behind bridge: 00000000fdb00000-00000000fdb00000
        Capabilities: <available only to root>

0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fda00000-fdafffff
        Prefetchable memory behind bridge: 00000000fd900000-00000000fd900000
        Capabilities: <available only to root>

0000:00:0d.0 VGA compatible controller: nVidia Corporation: Unknown device 03d1 (rev a2) (prog-if 00 [VGA])
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 1404
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
        Flags: fast devsel
        Capabilities: <available only to root>

I'm really not sure how to resolve all this - if anyone has an idea that can help me, i'd be very glad to hear it.

thanks and be well,

flo

---

### Post by FloSynergy on 2007-06-20
Sorted!!!

It seems that it was just a matter of upgrading to feisty faun 7.04.
the installation went smoothly - not a hitch at all.
It picked up the eth0 right away, ditto for sound.

I am very impressed.

Viva Ubuntu Viva!

:D

---

