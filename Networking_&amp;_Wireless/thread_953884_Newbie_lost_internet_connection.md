---
title: "Newbie lost internet connection"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by richie3418 on 2008-10-20
I took a little break from Ubuntu after having a lot of trouble before. I set up Mandriva 2008 on another hard drive and was very successful. Anyway I reloaded this Ubuntu 8.04 on another hd  everything was going well until I installed my wireless driver which didn't work. I tried to connect with my hard wire and it will not connect. I went to the network settings  and it will not let me put a check in the box for wired connection. Can anyone tell me how to get back my wired connection then maybe I can start over with the other?

---

### Post by ztrange on 2008-10-20
If your ethernet NIC is suppported by Ubuntu, simply plug the ethernet in and it should work Also, search for model specific info, you can see the model of your wilerd NIC with lspci. And you can see the status of your ethernet connection with ifconfig. If with ifconfig you see no adapter, then your adapter is not detected.

As for the wireless, you should tell us which wireless NIC do you have...

---

### Post by richie3418 on 2008-10-20
The ethernet was working before I installed the wireless driver. The wireless card is a Linksys wireless B 2.4 GHz 802.11b model
WPC11 ver.4, driver: LSRTNDS.INF
I just took the card out to make sure of the above information and now the ethernet is working. When I re-installed Ubuntu I had the card in and the etho was working. When I installes the wireless driver the etho quit working. The driver I mentioned above is the same one I used with Mandriva and it worked.
I got the below when I typed lspci -v | less in the terminal.

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/
O Controller (rev 02)
        Subsystem: Dell Unknown device 017f
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor
 to I/O Controller (rev 02)
        Subsystem: Dell Unknown device 017f
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor
 to I/O Controller (rev 02)
        Subsystem: Dell Unknown device 017f
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Grap
hics Device (rev 02) (prog-if 00 [VGA controller])
        Subsystem: Dell Unknown device 017f
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at f6f80000 (32-bit, non-prefetchable) [size=512K]
:
 I/O ports at c000 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Dell Unknown device 017f
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at f6f00000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 017f
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 017f
        Flags: bus master, medium devsel, latency 0, IRQ 11
:
 I/O ports at bf40 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 017f
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 017f
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at f6effc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: f8000000-fdffffff
0:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 017f
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at bfa0 [size=16]
        Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Unknown device 017f
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at c800 [size=256]
        I/O ports at cc40 [size=64]
        Memory at f6eff800 (32-bit, non-prefetchable) [size=512]
        Memory at f6eff400 (32-bit, non-prefetchable) [size=256]
  Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: Broadcom Corporation Unknown device 4d64
        Flags: medium devsel, IRQ 7
        I/O ports at c400 [size=256]
        I/O ports at c080 [size=128]
        Capabilities: <access denied>

02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Dell Unknown device 017f
        Flags: bus master, fast devsel, latency 32, IRQ 7
        Memory at fcffe000 (32-bit, non-prefetchable) [size=8K]
        Expansion ROM at fc000000 [disabled] [size=16K]
        Capabilities: <access denied>

02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: Dell Unknown device 017f
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at fc004000 (32-bit, non-prefetchable) [size=4K]
:
 Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: f8000000-fbfff000 (prefetchable)
        Memory window 1: 34000000-37fff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        16-bit legacy interface ports at 0001

---

