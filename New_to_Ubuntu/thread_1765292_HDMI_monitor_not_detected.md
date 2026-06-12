---
title: "HDMI monitor not detected"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by dinostabOMG on 2011-05-22
Brand new install of Natty on a brand new Dell XPS 15 (model P11F) laptop. Using Ubuntu Classic session and the on-board intel graphics card.

The system won't detect my external monitor. When I open Preferences -> Monitors, only the laptop monitor is shown. Dual booting with Windows 7, in Windows it works fine, I just have to plug it into the HDMI slot.

I don't know if it helps but here is lspci -v:

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0000000-f10fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 55
	Memory at f1400000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f1c05000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Dell Device 050e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f1c0a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 53
	Memory at f1c00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f1b00000-f1bfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: f1a00000-f1afffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: f1900000-f19fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Prefetchable memory behind bridge: 00000000f1800000-00000000f18fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Dell Device 050e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f1c09000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
	Subsystem: Dell Device 050e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 050e
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
	I/O ports at 4088 [size=8]
	I/O ports at 4094 [size=4]
	I/O ports at 4080 [size=8]
	I/O ports at 4090 [size=4]
	I/O ports at 4060 [size=32]
	Memory at f1c08000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: Dell Device 050e
	Flags: medium devsel, IRQ 10
	Memory at f1c04000 (64-bit, non-prefetchable) [size=256]
	I/O ports at efa0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 3000 [size=128]
	Expansion ROM at f1000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN
	Flags: bus master, fast devsel, latency 0, IRQ 54
	Memory at f1b00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f1a00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at 2000 [size=256]
	Memory at f1804000 (64-bit, prefetchable) [size=4K]
	Memory at f1800000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


```

[It's been established]("http://ubuntuforums.org/showthread.php?t=1617541") that the nvidia card won't work in Ubuntu, so I'm using the Intel one instead.

---

### Post by warsev on 2011-06-07
> **dinostabOMG said:**
> 
...
The system won't detect my external monitor. When I open Preferences -> Monitors, only the laptop monitor is shown.  ...

I have this exact same problem. Laptop is a HP G72-B66US with Intel Core3 and Intel graphics. Kernel is 2.6.38-10.44 generic.

I'm hoping someone has found a solution before I start messing things up further.

---

### Post by wildmanne39 on 2011-06-07
> **dinostabOMG said:**
> Brand new install of Natty on a brand new Dell XPS 15 (model P11F) laptop. Using Ubuntu Classic session and the on-board intel graphics card.

The system won't detect my external monitor. When I open Preferences -> Monitors, only the laptop monitor is shown. Dual booting with Windows 7, in Windows it works fine, I just have to plug it into the HDMI slot.

I don't know if it helps but here is lspci -v:

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0000000-f10fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 55
	Memory at f1400000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f1c05000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Dell Device 050e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f1c0a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 53
	Memory at f1c00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f1b00000-f1bfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: f1a00000-f1afffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: f1900000-f19fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Prefetchable memory behind bridge: 00000000f1800000-00000000f18fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Dell Device 050e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f1c09000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
	Subsystem: Dell Device 050e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 050e
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
	I/O ports at 4088 [size=8]
	I/O ports at 4094 [size=4]
	I/O ports at 4080 [size=8]
	I/O ports at 4090 [size=4]
	I/O ports at 4060 [size=32]
	Memory at f1c08000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: Dell Device 050e
	Flags: medium devsel, IRQ 10
	Memory at f1c04000 (64-bit, non-prefetchable) [size=256]
	I/O ports at efa0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 3000 [size=128]
	Expansion ROM at f1000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN
	Flags: bus master, fast devsel, latency 0, IRQ 54
	Memory at f1b00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f1a00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Dell Device 050e
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at 2000 [size=256]
	Memory at f1804000 (64-bit, prefetchable) [size=4K]
	Memory at f1800000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


```

[It's been established]("http://ubuntuforums.org/showthread.php?t=1617541") that the nvidia card won't work in Ubuntu, so I'm using the Intel one instead.
Hi, look at these two guides and see if you can make it work.
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected) The second link talks about setting up a dual monitor.

---

