---
title: "Why so difficult ?"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by Pizarro on 2007-06-15
I have now tried and failed twice to  get ubuntu/xunbuntu to work wireless on two separate laptops. I have tried both laptops on l their different internal  broadcom cards and both with an usb dongle style and ndiswrapper. I could on occasion  see available networks but connect !!! This is with all encryption turned off.
  The same laptops went straight on to the network when used with PCLinusOS and puppy, load ndiswrapper load windows inf and" hey presto" This is with wpa turned on!
 So why is this so hard with ubuntu the distro I use as dual boot at home and love? Admittedly not wireless,why give myself more pain?:roll:

---

### Post by Jose Catre-Vandis on 2007-06-15
We'll need more information about the specific wireless adapters and dongles to advise.

In a terminal, with the adapter inserted (if necessary), run
```
 lspci -v
```
&
```
lsusb
```

and post the output

Which ubuntu are you using? Breezy/Dapper/Edgy/Fiesty?

Also worth checking your dmesg after insertion/boot up, to see what is happening/not happening

---

### Post by Pizarro on 2007-06-21
Feisty
fiona@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at e000 [size=8]
        Memory at a0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0080000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, fast devsel, latency 0
        Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=03, sec-latency=0
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: c8000000-cfffffff
        Prefetchable memory behind bridge: 0000000098000000-000000009fffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        I/O behind bridge: 0000a000-0000bfff
        Memory behind bridge: c4000000-c7ffffff
        Prefetchable memory behind bridge: 0000000094000000-0000000097ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1200 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1220 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1240 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1260 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at 10000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: bc000000-c3ffffff
        Prefetchable memory behind bridge: 000000008c000000-0000000093ffffff
        Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e100 [size=256]
        I/O ports at e200 [size=64]
        Memory at d00c0000 (32-bit, non-prefetchable) [size=512]
        Memory at d00c0200 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: medium devsel, IRQ 18
        I/O ports at e300 [size=256]
        I/O ports at e400 [size=128]
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1100 [size=16]

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: medium devsel, IRQ 11
        I/O ports at 1400 [size=32]

05:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, fast devsel, latency 128, IRQ 22
        Memory at bc002000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: AMBIT Microsystem Corp. Aspire 3022WLMi, 5024WLMi
        Flags: bus master, fast devsel, latency 128, IRQ 23
        Memory at bc000000 (32-bit, non-prefetchable) [size=8K]

05:04.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0081
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at bc004000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 8c000000-8ffff000 (prefetchable)
        Memory window 1: c0000000-c3fff000
        I/O window 0: 00008000-000080ff
        I/O window 1: 00008400-000084ff
        16-bit legacy interface ports at 0001

I am trying to connect with the network settings . It can see my router. I have changed to WEP hex using DHCP.

---

