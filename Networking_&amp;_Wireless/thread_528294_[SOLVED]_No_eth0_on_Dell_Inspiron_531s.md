---
title: "[SOLVED] No eth0 on Dell Inspiron 531s"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by teleclimber on 2007-08-17
Hi all,

I got a Dell Inspiron 531s desktop with Vista Preinstalled. It's an AMD machine with a Nvidia nforce 430 chipset according to forum posts on Dell's site.

I am trying to get Ubuntu 6.06 working decently. So far it's installed but I can't get it to find the network card. I tried several things:

First, forcedeth wasn't loading at boot. Even after I fixed that eth0 wasn't showing up with ifconfig -a.

Then I installed nvidia's Linux nForce Driver - IA32 Version: 1.0-0310 without problems. But after reboot and checking that the driver is being used and forcedeth is not, there still isn't an eth0 in ifconfig -a.

NVIDIA says to try changing the BIOS settings to OS='other', but I can't find any such setting in my phoenix BIOS. see:

[http.download.nvidia.com/XFree86/nforce/1.0-0310/ReleaseNotes.html#Troubleshooting]("http.download.nvidia.com/XFree86/nforce/1.0-0310/ReleaseNotes.html#Troubleshooting")

So now I'm stuck. :confused: Any help would be very much appreciated! Thanks!!

uname -r : 2.6.15-26-386


$ sudo lspci -v
0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 03ea (rev a1)
        Subsystem: Dell: Unknown device 020e
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #08 [0220]
        Capabilities: [dc] #08 [a801]

0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 03e0 (rev a2)
        Subsystem: Dell: Unknown device 020e
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation: Unknown device 03eb (rev a2)
        Subsystem: Dell: Unknown device 020e
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at fc00 [size=64]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: [44] Power Management version 2

0000:00:01.2 RAM memory: nVidia Corporation: Unknown device 03f5 (rev a2)
        Subsystem: Dell: Unknown device 020e
        Flags: 66MHz, fast devsel

0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 03f1 (rev a3) (prog-if 10 [OHCI])
        Subsystem: Dell: Unknown device 020e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 03f2 (rev a3) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 020e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] #0a [2098]
        Capabilities: [80] Power Management version 2

0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 03f3 (rev a1) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: fd900000-fd9fffff
        Capabilities: [b8] #0d [0000]
        Capabilities: [8c] #08 [a800]

0000:00:05.0 0403: nVidia Corporation: Unknown device 03f0 (rev a2)
        Subsystem: Dell: Unknown device 020e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] #08 [a802]

0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 03ec (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell: Unknown device 020e
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: [44] Power Management version 2

0000:00:07.0 Bridge: nVidia Corporation: Unknown device 03ef (rev a2)
        Subsystem: Dell: Unknown device 020e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ec00 [size=8]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/3 Enable-
        Capabilities: [6c] #08 [a802]

0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 03f6 (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Dell: Unknown device 020e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d800 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] #08 [a802]

0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 03e8 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000fdc00000-00000000fdc00000
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] #08 [a800]
        Capabilities: [80] #10 [0141]

0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fdb00000-fdbfffff
        Prefetchable memory behind bridge: 00000000fda00000-00000000fda00000
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] #08 [a800]
        Capabilities: [80] #10 [0141]

0000:00:0d.0 VGA compatible controller: nVidia Corporation: Unknown device 03d0 (rev a2) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 020e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] #08 [2101]

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

---

### Post by noob12 on 2007-08-17
I'm assuming you mean the device isn't showing up with any eth* interface at all.

Does **sudo lshw -C network** indicate that the expected driver has claimed the device?

Also check **dmesg** for PCI routing issues.  You can post that if you want.

I'm not sure what the name of the new driver you're using is, but try looking at **modinfo *drivername*** for any debug flags you can enable on the driver.  Then try reloading it with any debug options it has and see if you see anything more interesting on the tail of dmesg.

---

### Post by teleclimber on 2007-08-17
Hi noob12 thanks for the help so far.

You are correct I am not seeing any eth* at all. Network  works fine in Vista.

'sudo lshw -C network' shows no output. There is output if I just dp 'sudo lshw', just no network-related hardware.

There are suspicious entries in dmesg, but there are no debug options in the driver.

Well it's no longer a problem because I took $22 to Best Buy and bought a no-name NIC and 'poof' there is my eth0.

Next up is the graphics. We'll see how that works.

---

### Post by noob12 on 2007-08-18
Ah.  The money solution.  Mark the thread solved !  :-)

---

### Post by teleclimber on 2007-08-18
money well spent!

):P

---

