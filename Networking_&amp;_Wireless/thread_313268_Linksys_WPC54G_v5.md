---
title: "Linksys WPC54G v5"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by lwr on 2006-12-05
I've got a Linksys WPC54G v5 card I want to use with my Dell Inspiron 2500. I'm guessing I'm going to have to use Windows wireless drivers and ndiswrapper, but if I don't, please let me know. Has anyone had any experience of getting this card working? Any suggestions on what drivers I need to use would be highly appreciated. Thanks

Luke

---

### Post by FrodoB on 2006-12-05
Publish the outputs of:

lspci -v

iwconfig

---

### Post by lwr on 2006-12-06
lspci -v gives:
```

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
        Subsystem: Dell Unknown device 00c9
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 11) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 00c9
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 10
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Memory at f4000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=09, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f4100000-f41fffff
        Prefetchable memory behind bridge: 20000000-23ffffff

00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03) (prog-if 80 [Master])
        Subsystem: Intel Corporation Unknown device 4541
        Flags: bus master, medium devsel, latency 0
        I/O ports at 1800 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 4541
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1820 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 03)
        Subsystem: Intel Corporation Unknown device 4541
        Flags: medium devsel, IRQ 5
        I/O ports at 1810 [size=16]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 4541
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 03)
        Subsystem: Dell Unknown device 00c9
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1c00 [size=256]
        I/O ports at 1840 [size=64]

01:03.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
        Subsystem: Dell Unknown device 00c9
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 5
        Memory at f4101000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 24000000-25fff000
        I/O window 0: 00002800-000028ff
        I/O window 1: 00002c00-00002cff
        16-bit legacy interface ports at 0001

01:03.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
        Subsystem: Dell Unknown device 00c9
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 5
        Memory at f4102000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 22000000-23fff000 (prefetchable)
        Memory window 1: 26000000-27fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00003000-000030ff
        16-bit legacy interface ports at 0001

01:0b.0 Communication controller: Agere Systems WinModem 56k (rev 01)
        Subsystem: Actiontec Electronics Inc Unknown device 2000
        Flags: medium devsel, IRQ 5
        Memory at f4100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 2400 [size=8]
        I/O ports at 2000 [size=256]
        Capabilities: <access denied>

06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Linksys Unknown device 0040
        Flags: 66MHz, medium devsel, IRQ 5
        Memory at 26000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Memory at 26010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

```

iwconfig gives:
```
lo        no wireless extensions.

sit0      no wireless extensions.
```

Thanks

---

### Post by FrodoB on 2006-12-06
Here is your device:

06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Linksys Unknown device 0040
        Flags: 66MHz, medium devsel, IRQ 5
        Memory at 26000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Memory at 26010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

This instruction for the TRENDnet TEW-421PC rev B1 is what you need as it uses the same chipset. Infact I would try the exact TRENDnet driver as it will likely work as well:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29")

---

