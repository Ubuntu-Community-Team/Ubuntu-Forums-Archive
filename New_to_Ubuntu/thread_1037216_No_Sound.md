---
title: "No Sound?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by RadiationHazard on 2009-01-11
I have just installed Ubuntu 8.10 64 bit version on my friends laptop because we are going to use Linux Multimedia Studio to help make a CD and we need Linux installed on both of our computers because we both need to be able to email the sound file back and forth and edit it and add to it. So obviously we're going to need the speakers to work to make music. Can some of you guys on here with more experience with Ubuntu than me help me get is speakers up and working. Thank you so much to anybody who has the time to help us out!

PS. [Here]("http://reviews.cnet.com/laptops/hp-dv4-1125nr/4505-3121_7-33309968.html") is a site that supplies a little more info about is PC.

[http://reviews.cnet.com/laptops/hp-dv4-1125nr/4505-3121_7-33309968.html](http://reviews.cnet.com/laptops/hp-dv4-1125nr/4505-3121_7-33309968.html)

---

### Post by gettinoriginal on 2009-01-11
Try these, they sure helped me:  :p

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by RadiationHazard on 2009-01-16
> **gettinoriginal said:**
> Try these, they sure helped me:  :p

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


thanks :)

I still haven't gotten it working but I think I know what the problem is. A lot of the drivers are saying "Capabilities: <access denied>". The audio is one of them. How to I change that? Here is the list of what pops up when I put in "lspci -v | less"

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 7110 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0
        Memory at d6400000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 70e0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 70c0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at dc504c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at dc500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: db500000-dc4fffff
        Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: da500000-db4fffff
        Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: d9500000-da4fffff
        Prefetchable memory behind bridge: 00000000d2400000-00000000d33fffff
        Capabilities: <access denied>
 Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8500000-d94fffff
        Prefetchable memory behind bridge: 00000000d3400000-00000000d43fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d7500000-d84fffff
        Prefetchable memory behind bridge: 00000000d4400000-00000000d53fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=08, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: d6500000-d74fffff
        Prefetchable memory behind bridge: 00000000d5400000-00000000d63fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 70a0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 7080 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 7060 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 7040 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at dc504800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2296
        I/O ports at 7108 [size=8]
        I/O ports at 711c [size=4]
        I/O ports at 7100 [size=8]
        I/O ports at 7118 [size=4]
        I/O ports at 7020 [size=32]
        Memory at dc504000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: medium devsel, IRQ 11
        Memory at dc505000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 7000 [size=32]
        Kernel modules: i2c-i801

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
        Subsystem: Hewlett-Packard Company Device 137c
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d9500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: wl

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0, IRQ 2297
        I/O ports at 3000 [size=256]
        Memory at d3410000 (64-bit, prefetchable) [size=4K]
        Memory at d3400000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at d3420000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

05:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d7500300 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

05:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: fast devsel, IRQ 16
        Memory at d7500200 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel modules: sdhci-pci

05:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d7500100 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

05:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d7500000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

(END)

```

---

