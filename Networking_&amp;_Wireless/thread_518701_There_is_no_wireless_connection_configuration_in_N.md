---
title: "There is no wireless connection configuration in Network Settings"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by kurt_issac on 2007-08-06
I installed ubuntu in my friend's notebook, but only Wired Connection and Modem connection configuration available.

The wireless card should be no problem, because in windows, wireless is okay.

My notebook have no wireless problem, but why there is no wireless connection in my friend's notebook? His note book is still brand new.

Can anyone help? Thanx!

---

### Post by Steve1961 on 2007-08-06
It all depends on the type of wireless chipset in the notebook.  You can find this out by typing:

lspci -v

If there isn't a native driver available you may need to use ndiswrapper, but post the out put of this command first.

---

### Post by kurt_issac on 2007-08-15
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cff00000
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc Unknown device 5a39 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 225
        I/O ports at 8440 [size=8]
        I/O ports at 8434 [size=4]
        I/O ports at 8438 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8400 [size=16]
        Memory at c0004000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 32000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 50
        Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 50
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 50
        Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: 66MHz, medium devsel
        I/O ports at 8410 [size=16]
        Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 82 [Master PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 233
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 8420 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, slow devsel, latency 64, IRQ 233
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0c, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: c0200000-c02fffff
        Prefetchable memory behind bridge: 30000000-31ffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>

08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at c0210000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 34000000-35fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c0211000 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

08:01.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 225
        Memory at c0211400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c0211800 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

08:01.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: medium devsel, IRQ 255
        Memory at c0211100 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <access denied>

08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 58
        I/O ports at a000 [size=256]
        Memory at c0211c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0418
        Flags: bus master, medium devsel, latency 80, IRQ 11
        Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
```

These are the ouput.

---

### Post by Steve1961 on 2007-08-16
OK, the wireless chipset is the last entry.  I suggest you search for a how to on this forum for the atheros ar5005g.  See for instance:

[http://ubuntuforums.org/showthread.php?t=522805&highlight=AR5005G](http://ubuntuforums.org/showthread.php?t=522805&highlight=AR5005G)

---

### Post by skdlnx on 2007-08-16
Newbie here to Feisty Fawn also. I have a hp media center m7334n pc, with a wireless pci card that works fine in windows. It's running the i386 desktop ubuntu install on a AMD Athlon 64 X2 3800 dual core PC. Had issues with the AMD64 desktop install cd previously. 

 Anyway, I also only get a "wired connection" in NetworkManager Applet, so I may have the same issue.  Under windows vista, it says that the WLAN card is Atheros based. Unfortunately I couldn't figure out how to find out which driver that uses specifically, because it always lists itself as HP Atheros WLAN in Device Manager. I'm hoping that I can use Madwifi or Ndiswrapper to help me configure and use this wireless card when running Ubuntu, but need help on where to start. I've already downloaded madwifi and ndiswrapper separately from Synaptic Manager.  

Here is the output of my desktop when running the " lspci -v " command via Terminal. Any advice would be helpful. Thanks!

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64
        I/O ports at 4100 [disabled] [size=32]
        Memory at <ignored> (64-bit, non-prefetchable)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdc00000-fdcfffff
        Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
        Capabilities: <access denied>

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at fe00 [size=8]
        I/O ports at fd00 [size=4]
        I/O ports at fc00 [size=8]
        I/O ports at fb00 [size=4]
        I/O ports at fa00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 80000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: 66MHz, medium devsel
        I/O ports at 0500 [size=16]
        Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f800 [size=16]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: f8000000-fbffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series] (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 3
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at df00 [size=256]
        Memory at fdcf0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 3000
        Flags: fast devsel, IRQ 5
        Memory at c0000000 (32-bit, prefetchable) [disabled] [size=256M]
        I/O ports at ef00 [disabled] [size=256]
        Memory at fddf0000 (32-bit, non-prefetchable) [disabled] [size=64K]
        [virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
        Subsystem: ATI Technologies Inc Unknown device 3001
        Flags: fast devsel
        Memory at fdde0000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)
        Subsystem: Lite-On Communications Inc Unknown device 5001
        Flags: medium devsel, IRQ 18
        Memory at fdee0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

03:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at cf00 [size=32]
        Capabilities: <access denied>

03:01.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 64
        I/O ports at ce00 [size=8]
        Capabilities: <access denied>

03:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
        Memory at fdef8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

03:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 150
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at cd00 [size=256]
        Memory at fdefe000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at fde00000 [disabled] [size=64K]
        Capabilities: <access denied>

03:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at fdefd000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at cc00 [size=128]
        Capabilities: <access denied>

---

### Post by Steve1961 on 2007-08-16
Try this thread

[http://ubuntuforums.org/showthread.php?t=503525&highlight=AR5006X](http://ubuntuforums.org/showthread.php?t=503525&highlight=AR5006X)

Your wireless chipset is an Atheros AR5006X

---

### Post by kurt_issac on 2007-08-18
Thanx, it works!

---

