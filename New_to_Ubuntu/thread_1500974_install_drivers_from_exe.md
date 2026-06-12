---
title: "install drivers from exe"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by redesigner on 2010-06-03
Is it possible to install windows .exe drivers on Karmic? I'm trying to fix my wireless card.

---

### Post by bodhi.zazen on 2010-06-03
yes, you use ndiswrapper

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

ndiswrapper uses the INF files, not the exe

What wireless card is it ?

---

### Post by redesigner on 2010-06-03
Im not sure, but I ran ```
lspci -v |  less
``` from [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
And it gave me all this ```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Dell Device 02aa
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02aa
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f6c00000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at efe8 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02aa
    Flags: bus master, fast devsel, latency 0
    Memory at f6b00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Dell Device 02aa
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6f60 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Dell Device 02aa
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6f80 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Dell Device 02aa
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 6fa0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Dell Device 02aa
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Dell Device 02aa
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    Memory behind bridge: f6900000-f69fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f6800000-f68fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f6600000-f67fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Dell Device 02aa
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6f00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Dell Device 02aa
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6f20 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Dell Device 02aa
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 6f40 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Dell Device 02aa
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Dell Device 02aa
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Dell Device 02aa
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
    I/O ports at 6e70 [size=8]
    I/O ports at 6e78 [size=4]
    I/O ports at 6e80 [size=8]
    I/O ports at 6e88 [size=4]
    I/O ports at 6ea0 [size=32]
    Memory at fed1c800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 02aa
    Flags: medium devsel, IRQ 4
    Memory at f6afbf00 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1100 [size=32]
    Kernel modules: i2c-i801

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
    Subsystem: Dell Device 02aa
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f68fc000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at de00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Dell Device 000c
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb


```

---

### Post by themusicalduck on 2010-06-03
Have you checked System > Administration > Hardware Drivers first? To see if you can install a driver from there.

---

### Post by redesigner on 2010-06-03
I did and it gave me this:
[IMG]http://i48.tinypic.com/2376l0.jpg[/IMG]

---

### Post by oldsoundguy on 2010-06-03
broadcom stuff .. not the best:

[http://www.google.com/search?hl=en&client=firefox-a&hs=ePK&rls=org.mozilla%3Aen-US%3Aofficial&q=install+broadcom+wireless+in+9.10&btnG=Search&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=en&client=firefox-a&hs=ePK&rls=org.mozilla%3Aen-US%3Aofficial&q=install+broadcom+wireless+in+9.10&btnG=Search&aq=f&aqi=&aql=&oq=&gs_rfai=)

---

### Post by bodhi.zazen on 2010-06-03
> **redesigner said:**
> Im not sure, but I ran ```
lspci -v |  less
``` from [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Try

Broadcom Corporation BCM4312

Try

```
sudo apt-get install  bcmwl-kernel-source
```And reboot.

If that does not work, see

[https://wiki.ubuntu.com/Testing/Laptop/Lucid/Reports/AcerAspireOneD150#Wireless%20%28Lucid%20Lynx%29](https://wiki.ubuntu.com/Testing/Laptop/Lucid/Reports/AcerAspireOneD150#Wireless%20%28Lucid%20Lynx%29)

---

### Post by themusicalduck on 2010-06-03
It looks like the drivers are installed already then. If you explain why the wireless isn't working properly then we can probably help to fix it for you.

I wouldn't try using ndiswrapper yet.

---

### Post by redesigner on 2010-06-03
Thanks for your help!
For wireless issues, that weren't resolved by the drivers I have a new thread. [http://ubuntuforums.org/showthread.php?p=9406901#post9406901](http://ubuntuforums.org/showthread.php?p=9406901#post9406901)

---

