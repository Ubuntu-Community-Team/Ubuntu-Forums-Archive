---
title: "Can't run any 3d games"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Durolipons on 2009-12-02
No games seem to work. At least none of the good ones. i tried Tremulus, Enemy lines, War zone 2100 to mention a few. they all show up on the applications menu but when I click on them nothing happens at all. 
I'm not a complete newbie but I'm sure there is a simple explanation. 
I really do need some help.

---

### Post by Marvin666 on 2009-12-02
Try posting this in absolute beginner talk.
This area is just for fun posts, not tech support.

---

### Post by Elfy on 2009-12-02
moved to ABT

---

### Post by NoaHall on 2009-12-02
Try looking in System -> Admin -> Hardware Drivers and install the driver.

Don't make two threads on the same topic, btw.

---

### Post by Durolipons on 2009-12-02
> **NoaHall said:**
> Try looking in System -> Admin -> Hardware Drivers and install the driver.

Don't make two threads on the same topic, btw.

Sorry, I am new to ubuntu forums, I hope I'm not making to much of a hash of things. I'm going top try the live irc chat as soon as i can. Hardware drivers always reports that there are no proprietary drivers for my system.

---

### Post by NoaHall on 2009-12-02
Hm. In that case, what graphics card are you using?

---

### Post by halitech on 2009-12-02
do you know what video card you have in the system?
```
lspci -v
```
will tell you what you have.

---

### Post by Durolipons on 2009-12-02
> **halitech said:**
> do you know what video card you have in the system?
```
lspci -v
```will tell you what you have.

05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at ff300000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 44000000-47fff000
    I/O window 0: 0000d000-0000d0ff
    I/O window 1: 0000d400-0000d4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at d800 [size=256]
    Memory at ff3ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: epl, 8139too, 8139cp

However this should report an intel chipset.

---

### Post by halitech on 2009-12-02
thats only the end of the output and is missing alot of detail. Lets do just
```
lspci
```and post the output

---

### Post by NoaHall on 2009-12-02
> **Durolipons said:**
> 05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at ff300000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 44000000-47fff000
    I/O window 0: 0000d000-0000d0ff
    I/O window 1: 0000d400-0000d4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at d800 [size=256]
    Memory at ff3ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: epl, 8139too, 8139cp

However this should report an intel chipset.

So it's a intel card you have? Hm, I'm afraid they don't have very good drivers.

---

### Post by Durolipons on 2009-12-02
> **halitech said:**
> thats only the end of the output and is missing alot of detail. Lets do just
```
lspci
```and post the output

Sorry yes this is the whole text:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ec00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at ff640000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0
    Memory at ff580000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at ff63c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: ff200000-ff2fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at e880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at e480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at e400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ff63bc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: ff300000-ff3fffff
    Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7128
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at ff2f0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at ff300000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 44000000-47fff000
    I/O window 0: 0000d000-0000d0ff
    I/O window 1: 0000d400-0000d4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at d800 [size=256]
    Memory at ff3ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: epl, 8139too, 8139cp

---

### Post by Durolipons on 2009-12-02
> **NoaHall said:**
> So it's a intel card you have? Hm, I'm afraid they don't have very good drivers. Should run these games though even if I have to stop other processes. Posted this a minute ago but it did'nt send.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ec00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at ff640000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0
    Memory at ff580000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at ff63c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: ff200000-ff2fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at e880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at e480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at e400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ff63bc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: ff300000-ff3fffff
    Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7128
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at ff2f0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at ff300000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 44000000-47fff000
    I/O window 0: 0000d000-0000d0ff
    I/O window 1: 0000d400-0000d4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at d800 [size=256]
    Memory at ff3ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: epl, 8139too, 8139cp

---

### Post by Cam42 on 2009-12-02
it did send... :\

---

### Post by Durolipons on 2009-12-02
> **Cam42 said:**
> it did send... :\
The battle of westnoth works.

---

### Post by Durolipons on 2009-12-02
> **Cam42 said:**
> it did send... :\
The battle of westnoth works.

---

### Post by Some Penguin on 2009-12-02
I haven't checked yet, but I would be somewhat surprised if Wesnoth required, say, GLX, considering that it's purely 2D sprite-based.

You might want to see what 'glxinfo' gives you.  In particular, if 'glxinfo | grep rendering' says 'software rasterizer' or 'no', then hardware acceleration (if any) is not being used. 

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

might also be of interest.

---

### Post by Ylon on 2009-12-02
As "good ones" seems you may refer on games with intensive OpenGL use. Try to run these games in terminal and see which errors did match (repeat on different games)?

---

### Post by Weepleman on 2009-12-02
I just had a problem like this.  Do you by chance have any Nvidia drivers on your system, I did for some reason.  What worked for me was running ```
sudo apt-get autoremove
```

---

