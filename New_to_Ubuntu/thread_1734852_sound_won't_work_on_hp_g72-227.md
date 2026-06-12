---
title: "sound won't work on hp g72-227"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by jzprice on 2011-04-20
i'm brand new with linux and know little about the deeper parts of computers. i have linux installed and set up, however, there is no sound whatsoever. i have checked alsamixer and everything is unmuted. i then typed this in and found the following:

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC270
Codec: Intel Cantiga HDMI

my friend, whom is experienced in linux, looked it over and couldn't figure it out, but he admitted that he knew little about drivers. the furthest we got was the beep when it reboots. no sound otherwise. any help would be greatly appreciated.

---

### Post by ttshivers on 2011-04-20
Can you give us information about your hardware.

---

### Post by jzprice on 2011-04-20
hopefully this helps:


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4110 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0
	Memory at d2400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 40e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 40c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at d4505c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at d4500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d3500000-d44fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2500000-d34fffff
	Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 40a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 4080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 4060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 4040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at d4505800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at 4108 [size=8]
	I/O ports at 411c [size=4]
	I/O ports at 4100 [size=8]
	I/O ports at 4118 [size=4]
	I/O ports at 4020 [size=32]
	Memory at d4505000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: medium devsel, IRQ 11
	Memory at d4506000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 4000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: fast devsel, IRQ 11
	Memory at d4504000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
	Subsystem: Hewlett-Packard Company Device 1467
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 3000 [size=256]
	Memory at d3500000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl819xSE
	Kernel modules: r8192se_pci

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0, IRQ 26
	I/O ports at 2000 [size=256]
	Memory at d1410000 (64-bit, prefetchable) [size=4K]
	Memory at d1400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1420000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

---

### Post by ttshivers on 2011-04-20
It looks like you have this as your sound card: Intel Corporation 82801I (ICH9 Family) HD Audio Controller.  This might help you [http://ubuntuforums.org/showthread.php?t=1036508]("http://ubuntuforums.org/showthread.php?t=1036508").  And I'm still looking for a solution.

---

### Post by jzprice on 2011-04-20
alright, so i tried out that link, sounded like it would have worked. but no cigar. at this point, that beep sounds so beautiful everytime i reboot. :) anyways. that one seems the closest yet. i'll keep playing around with it.

---

### Post by jzprice on 2011-04-21
still nothing. anyone?

---

