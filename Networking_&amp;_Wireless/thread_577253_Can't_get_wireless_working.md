---
title: "Can't get wireless working"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by bg1256 on 2007-10-16
I just purchased a new computer today (Gateway MT 3423), and it's a nice little machine for me.

However, I cannot seem to get wireless working.

When I run:
```
lspci -v | less
```

I get (tried to highlight what I thought was important):
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fa100000-fa8fffff
        Prefetchable memory behind bridge: 00000000bdf00000-00000000bfefffff
        Capabilities: <access denied>
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2) (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at b0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 3080 [size=16]
        Capabilities: <access denied>
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=64
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: b3400000-b34fffff
        Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

[B]00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Gateway 2000 Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3090 [size=8]
        Capabilities: <access denied>[/B]

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

[B]06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. Unknown device 8225
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 6000 [size=256]
        Memory at b3400000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>[/B]
```
:

When I was researching the machine online, I thought it had a broadcom chipset, which is not ideal, but it is something I had worked with before and was prepared to deal with.

However, it does not seem this is actually the case, and now I don't have a clue where to go.

Anyone know?

Thanks a million!








I do have nvidial-glx installed so I can have compiz working.  I don't think this is the problem, as the wireless didn't work when using the Live CD either. But, it is one thing I thought of.

---

### Post by spd106 on 2007-10-16
You're going to need ndiswrapper to get the card working on Ubuntu 7.04, see [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I'm not 100% about this, but there may be a [driver]("http://rtl-wifi.sourceforge.net/wiki/Main_Page") included in Ubuntu 7.10.

---

### Post by bg1256 on 2007-10-16
Thanks spd106.  I figured I would need ndiswrapper.

However, I am not sure which windows driver to use, even after I get ndiswrapper installed.

---

### Post by bg1256 on 2007-10-16
Well, I have determined that I definitely have a Realtek wirless chip, and I have no idea what driver to use for it.

Here's a picture of my chip, letting me know for sure it is realtek:
[http://support.gateway.com/s/Mobile/Q106/Bishop/6008015R/6008015Rmv.shtml](http://support.gateway.com/s/Mobile/Q106/Bishop/6008015R/6008015Rmv.shtml)

It's an RTL8185L

---

### Post by bg1256 on 2007-10-16
I've now located the windows drivers for this particular wireless card:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)

Does anyone know how I could get this working via ndiswrapper?

---

### Post by bliffle on 2007-10-16
I was just reading in another thread (don't remember where it was exactly, but maybe it was the Absolute Beginners forum) that realtek has something for that and the guy said it worked perfectly for him.

---

### Post by Hero of Time on 2007-10-16
Obvious question, but have you tried the Linux driver on that page? It is for the 2.6.x kernel, so it should work just fine for Feisty and Gutsy.

---

