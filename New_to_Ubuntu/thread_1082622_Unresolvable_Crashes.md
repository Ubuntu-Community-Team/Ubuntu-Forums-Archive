---
title: "Unresolvable Crashes"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by tstirrat on 2009-02-28
I recently reformatted a Lenovo T43 (all stock parts except for the hard drive - a new 120gb seagate) and installed Ubuntu 8.10.

The computer crashes pretty much randomly. Being connected to the internet doesn't make a difference, which makes me think it doesn't have anything to do with the wireless card.

When it does crash, I can still move the mouse around the screen, but the image on the screen is frozen, and the computer does not accept any input. Ctrl+alt+backspace doesn't work, and nor do the magic sysreq keys. I end up having to do a hard reset (holding down the power button).

One problem I am aware of is that when I boot the computer, it comes up with an error message saying something along the lines of "This hard drive may not work with this computer." Could that be causing the problems?

Also, how can I find more information (system logs and debugging info and the like)?

---

### Post by hyperyoda on 2009-02-28
> **tstirrat said:**
> I recently reformatted a Lenovo T43 (all stock parts except for the hard drive - a new 120gb seagate) and installed Ubuntu 8.10.

The computer crashes pretty much randomly. Being connected to the internet doesn't make a difference, which makes me think it doesn't have anything to do with the wireless card.

When it does crash, I can still move the mouse around the screen, but the image on the screen is frozen, and the computer does not accept any input. Ctrl+alt+backspace doesn't work, and nor do the magic sysreq keys. I end up having to do a hard reset (holding down the power button).

One problem I am aware of is that when I boot the computer, it comes up with an error message saying something along the lines of "This hard drive may not work with this computer." Could that be causing the problems?

Also, how can I find more information (system logs and debugging info and the like)?


Hi,

Is the actual kernel crashing or just X? Look in your logs:
/var/log/messages
/var/log/daemon.log
/var/log/syslog
/var/log/kern.log
/var/log/debug
/var/log/Xorg.log

Please pastebin these for us to examine.

Also post the output of:
$ dmesg

Zach

---

### Post by 3rdalbum on 2009-02-28
After a crash, wait about 5 minutes for the kernel to sync its buffered data to disk. Then reboot, and take a look in the Gnome-System-Log program under "messages" or "kern.log". If there are any error messages from the time of the crash, then you've got something to work with.

---

### Post by tstirrat on 2009-02-28
Dmesg output:

```
[    1.009394] pci 0000:01:00.0: supports D2
[    1.009453] PCI: bridge 0000:00:01.0 io port: [3000, 3fff]
[    1.009460] PCI: bridge 0000:00:01.0 32bit mmio: [b0100000, b01fffff]
[    1.009468] PCI: bridge 0000:00:01.0 32bit mmio pref: [c0000000, c7ffffff]
[    1.009560] PCI: 0000:02:00.0 reg 10 64bit mmio: [b0200000, b020ffff]
[    1.009639] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    1.009649] pci 0000:02:00.0: PME# disabled
[    1.009712] PCI: bridge 0000:00:1c.0 32bit mmio: [b0200000, b02fffff]
[    1.009789] PCI: bridge 0000:00:1c.2 io port: [4000, 4fff]
[    1.009797] PCI: bridge 0000:00:1c.2 32bit mmio: [b2000000, b3ffffff]
[    1.009810] PCI: bridge 0000:00:1c.2 64bit mmio pref: [c8000000, c80fffff]
[    1.009871] PCI: 0000:0b:00.0 reg 10 32bit mmio: [b4000000, b4000fff]
[    1.009899] pci 0000:0b:00.0: supports D1
[    1.009903] pci 0000:0b:00.0: supports D2
[    1.009908] pci 0000:0b:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.009918] pci 0000:0b:00.0: PME# disabled
[    1.009987] PCI: 0000:0b:02.0 reg 10 32bit mmio: [b4001000, b4001fff]
[    1.010068] pci 0000:0b:02.0: PME# supported from D0 D3hot D3cold
[    1.010078] pci 0000:0b:02.0: PME# disabled
[    1.010145] pci 0000:00:1e.0: transparent bridge
[    1.010153] PCI: bridge 0000:00:1e.0 io port: [5000, 8fff]
[    1.010162] PCI: bridge 0000:00:1e.0 32bit mmio: [b4000000, bfffffff]
[    1.010174] PCI: bridge 0000:00:1e.0 64bit mmio pref: [d0000000, d7ffffff]
[    1.010232] bus 00 -> node 0
[    1.010250] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.010855] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    1.011222] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    1.011628] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    1.012045] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    1.022495] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    1.023096] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    1.023691] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    1.024295] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    1.024890] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    1.025484] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    1.026078] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    1.026672] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    1.027063] ACPI: Power Resource [PUBS] (on)
[    1.027063] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.027063] pnp: PnP ACPI init
[    1.027063] ACPI: bus type pnp registered
[    1.038493] pnp: PnP ACPI: found 14 devices
[    1.038499] ACPI: ACPI bus type pnp unregistered
[    1.038506] PnPBIOS: Disabled by ACPI PNP
[    1.039248] PCI: Using ACPI for IRQ routing
[    1.039477] NET: Registered protocol family 8
[    1.039477] NET: Registered protocol family 20
[    1.039477] NetLabel: Initializing
[    1.039477] NetLabel:  domain hash size = 128
[    1.039477] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.039477] NetLabel:  unlabeled traffic allowed by default
[    1.039477] hpet clockevent registered
[    1.039477] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.039477] hpet0: 3 64-bit timers, 14318180 Hz
[    1.040670] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.040677]    actual entries 65620
[    1.040831] AppArmor: AppArmor Filesystem Enabled
[    1.040866] ACPI: RTC can wake from S4
[    1.040881] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    1.040881] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    1.040881] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    1.040881] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    1.040881] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    1.040881] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    1.040881] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    1.040881] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    1.040881] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    1.040881] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    1.040881] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    1.040881] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    1.040881] system 00:00: iomem range 0x100000-0x5fffffff could not be reserved
[    1.040881] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    1.040881] system 00:02: ioport range 0x1000-0x107f has been reserved
[    1.040881] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    1.040881] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    1.040881] system 00:02: ioport range 0x1600-0x1641 has been reserved
[    1.040881] system 00:02: ioport range 0x1644-0x167f has been reserved
[    1.040881] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    1.040881] system 00:02: iomem range 0xf0008000-0xf000bfff could not be reserved
[    1.040881] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[    1.040881] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[    1.040881] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[    1.077785] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.077793] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    1.077802] pci 0000:00:01.0:   MEM window: 0xb0100000-0xb01fffff
[    1.077810] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000c7ffffff
[    1.077820] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.077825] pci 0000:00:1c.0:   IO window: disabled
[    1.077835] pci 0000:00:1c.0:   MEM window: 0xb0200000-0xb02fffff
[    1.077843] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.077855] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    1.077863] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    1.077873] pci 0000:00:1c.2:   MEM window: 0xb2000000-0xb3ffffff
[    1.077882] pci 0000:00:1c.2:   PREFETCH window: 0x000000c8000000-0x000000c80fffff
[    1.077899] pci 0000:0b:00.0: CardBus bridge, secondary bus 0000:0c
[    1.077905] pci 0000:0b:00.0:   IO window: 0x005000-0x0050ff
[    1.077914] pci 0000:0b:00.0:   IO window: 0x005400-0x0054ff
[    1.077924] pci 0000:0b:00.0:   PREFETCH window: 0xd0000000-0xd3ffffff
[    1.077934] pci 0000:0b:00.0:   MEM window: 0xb8000000-0xbbffffff
[    1.077944] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0b
[    1.077951] pci 0000:00:1e.0:   IO window: 0x5000-0x8fff
[    1.077962] pci 0000:00:1e.0:   MEM window: 0xb4000000-0xbfffffff
[    1.077971] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000d7ffffff
[    1.077996] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.078004] pci 0000:00:01.0: setting latency timer to 64
[    1.078019] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.078028] pci 0000:00:1c.0: setting latency timer to 64
[    1.078043] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.078053] pci 0000:00:1c.2: setting latency timer to 64
[    1.078066] pci 0000:00:1e.0: setting latency timer to 64
[    1.078082] pci 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.078093] bus: 00 index 0 io port: [0, ffff]
[    1.078099] bus: 00 index 1 mmio: [0, ffffffff]
[    1.078105] bus: 01 index 0 io port: [3000, 3fff]
[    1.078110] bus: 01 index 1 mmio: [b0100000, b01fffff]
[    1.078115] bus: 01 index 2 mmio: [c0000000, c7ffffff]
[    1.078121] bus: 01 index 3 mmio: [0, 0]
[    1.078125] bus: 02 index 0 mmio: [0, 0]
[    1.078130] bus: 02 index 1 mmio: [b0200000, b02fffff]
[    1.078135] bus: 02 index 2 mmio: [0, 0]
[    1.078140] bus: 02 index 3 mmio: [0, 0]
[    1.078145] bus: 03 index 0 io port: [4000, 4fff]
[    1.078150] bus: 03 index 1 mmio: [b2000000, b3ffffff]
[    1.078156] bus: 03 index 2 mmio: [c8000000, c80fffff]
[    1.078161] bus: 03 index 3 mmio: [0, 0]
[    1.078166] bus: 0b index 0 io port: [5000, 8fff]
[    1.078171] bus: 0b index 1 mmio: [b4000000, bfffffff]
[    1.078176] bus: 0b index 2 mmio: [d0000000, d7ffffff]
[    1.078182] bus: 0b index 3 io port: [0, ffff]
[    1.078187] bus: 0b index 4 mmio: [0, ffffffff]
[    1.078192] bus: 0c index 0 io port: [5000, 50ff]
[    1.078197] bus: 0c index 1 io port: [5400, 54ff]
[    1.078202] bus: 0c index 2 mmio: [d0000000, d3ffffff]
[    1.078208] bus: 0c index 3 mmio: [b8000000, bbffffff]
[    1.078224] NET: Registered protocol family 2
[    1.078480] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.078984] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.079927] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.080463] TCP: Hash tables configured (established 131072 bind 65536)
[    1.080470] TCP reno registered
[    1.080651] NET: Registered protocol family 1
[    1.080894] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.909380]  it is
[    2.794158] Freeing initrd memory: 8021k freed
[    2.794617] Simple Boot Flag at 0x35 set to 0x1
[    2.795973] audit: initializing netlink socket (disabled)
[    2.796040] type=2000 audit(1235844466.796:1): initialized
[    2.811302] highmem bounce pool size: 64 pages
[    2.811316] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.818951] VFS: Disk quotas dquot_6.5.1
[    2.819147] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.819408] msgmni has been set to 1752
[    2.819702] io scheduler noop registered
[    2.819709] io scheduler anticipatory registered
[    2.819715] io scheduler deadline registered
[    2.819743] io scheduler cfq registered (default)
[    2.819881] pci 0000:01:00.0: Boot video device
[    2.820133] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    2.820183] pcieport-driver 0000:00:01.0: found MSI capability
[    2.820228] pci_express 0000:00:01.0:pcie00: allocate port service
[    2.820374] pci_express 0000:00:01.0:pcie03: allocate port service
[    2.820577] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.820634] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.820693] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.820812] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.820899] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.821146] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    2.821203] pcieport-driver 0000:00:1c.2: found MSI capability
[    2.821260] pci_express 0000:00:1c.2:pcie00: allocate port service
[    2.821385] pci_express 0000:00:1c.2:pcie02: allocate port service
[    2.822020] pci_express 0000:00:1c.2:pcie03: allocate port service
[    2.822647] isapnp: Scanning for PnP cards...
[    3.177652] isapnp: No Plug & Play device found
[    3.257541] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.259944] serial 00:0a: activated
[    3.260521] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    3.260939] serial 0000:00:1e.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    3.260953] serial 0000:00:1e.3: PCI INT B disabled
[    3.264217] brd: module loaded
[    3.264365] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.264627] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    3.272272] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.272282] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.272852] mice: PS/2 mouse device common for all mice
[    3.273130] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.273167] rtc0: alarms up to one month, y3k, hpet irqs
[    3.273413] EISA: Probing bus 0 at eisa.0
[    3.273426] Cannot allocate resource for EISA slot 1
[    3.273432] Cannot allocate resource for EISA slot 2
[    3.273438] Cannot allocate resource for EISA slot 3
[    3.273443] Cannot allocate resource for EISA slot 4
[    3.273449] Cannot allocate resource for EISA slot 5
[    3.273455] Cannot allocate resource for EISA slot 6
[    3.273460] Cannot allocate resource for EISA slot 7
[    3.273466] Cannot allocate resource for EISA slot 8
[    3.273471] EISA: Detected 0 cards.
[    3.273477] cpuidle: using governor ladder
[    3.273483] cpuidle: using governor menu
[    3.274621] TCP cubic registered
[    3.274672] Using IPI No-Shortcut mode
[    3.275067] registered taskstats version 1
[    3.275298]   Magic number: 13:54:141
[    3.275309] block ram6: hash matches
[    3.275415] acpi device:12: hash matches
[    3.275464] rtc_cmos 00:06: setting system clock to 2009-02-28 18:07:48 UTC (1235844468)
[    3.275472] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.275477] EDD information not available.
[    3.275909] Freeing unused kernel memory: 424k freed
[    3.276040] Write protecting the kernel text: 2580k
[    3.276106] Write protecting the kernel read-only data: 940k
[    3.279671] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.664078] fuse init (API version 7.9)
[    4.020017] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    4.028025] processor ACPI0007:00: registered as cooling_device0
[    4.028036] ACPI: Processor [CPU] (supports 8 throttling states)
[    4.072045] thermal LNXTHERM:01: registered as thermal_zone0
[    4.074994] ACPI: Thermal Zone [THM0] (47 C)
[    5.420243] tg3.c:v3.94 (August 14, 2008)
[    5.420267] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.420285] tg3 0000:02:00.0: setting latency timer to 64
[    5.552583] eth0: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:15:58:7f:de:5a
[    5.552595] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    5.552602] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    5.704758] usbcore: registered new interface driver usbfs
[    5.704806] usbcore: registered new interface driver hub
[    5.732066] usbcore: registered new device driver usb
[    5.760686] USB Universal Host Controller Interface driver v3.0
[    5.768103] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    5.768119] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.768135] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.768143] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.768241] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    5.768296] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[    5.768593] usb usb1: configuration #1 chosen from 1 choice
[    5.768656] hub 1-0:1.0: USB hub found
[    5.768671] hub 1-0:1.0: 2 ports detected
[    5.820151] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    5.873029] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    5.873051] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.873067] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.873074] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.873132] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    5.873182] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
[    5.873386] usb usb2: configuration #1 chosen from 1 choice
[    5.873453] hub 2-0:1.0: USB hub found
[    5.873467] hub 2-0:1.0: 2 ports detected
[    5.904842] ACPI: ACPI Dock Station Driver
[    5.976421] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.976439] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.976447] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.976501] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    5.976551] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    5.976751] usb usb3: configuration #1 chosen from 1 choice
[    5.976813] hub 3-0:1.0: USB hub found
[    5.976828] hub 3-0:1.0: 2 ports detected
[    6.089974] SCSI subsystem initialized
[    6.152704] libata version 3.00 loaded.
[    6.184454] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    6.184472] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    6.184480] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    6.184533] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    6.184584] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001860
[    6.184788] usb usb4: configuration #1 chosen from 1 choice
[    6.184852] hub 4-0:1.0: USB hub found
[    6.184868] hub 4-0:1.0: 2 ports detected
[    6.289142] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    6.289159] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    6.289181] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    6.289189] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.289252] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    6.293194] ehci_hcd 0000:00:1d.7: debug port 1
[    6.293205] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    6.293219] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xb0000000
[    6.297131] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    6.308074] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.308302] usb usb5: configuration #1 chosen from 1 choice
[    6.308366] hub 5-0:1.0: USB hub found
[    6.308382] hub 5-0:1.0: 8 ports detected
[    6.364063] hub 3-0:1.0: unable to enumerate USB device on port 2
[    6.532060] ata_piix 0000:00:1f.2: version 2.12
[    6.532084] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    6.688042] ata_piix 0000:00:1f.2: setting latency timer to 64
[    6.689482] scsi0 : ata_piix
[    6.689670] scsi1 : ata_piix
[    6.692462] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18c0 irq 14
[    6.692470] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15
[    6.856438] ata1.00: ATA-6: ST9120822A,  3.ALE, max UDMA/100
[    6.856446] ata1.00: 234441648 sectors, multi 16: LBA48 
[    6.856453] ata1.00: applying bridge limits
[    6.872389] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    6.872499] ata1.00: configured for UDMA/100
[    7.036507] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4247N, 1.01, max UDMA/33
[    7.046911] usb 3-2: configuration #1 chosen from 1 choice
[    7.052461] ata2.00: configured for UDMA/33
[    7.052670] scsi 0:0:0:0: Direct-Access     ATA      ST9120822A       n/a  PQ: 0 ANSI: 5
[    7.057000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4247N 1.01 PQ: 0 ANSI: 5
[    7.234087] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.234171] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    7.289359] Driver 'sd' needs updating - please use bus_type methods
[    7.289538] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    7.289576] sd 0:0:0:0: [sda] Write Protect is off
[    7.289582] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.289642] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.289768] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    7.289803] sd 0:0:0:0: [sda] Write Protect is off
[    7.289809] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.289869] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.289878]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    7.335604]  sda5 >
[    7.335879] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.350279] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    7.350288] Uniform CD-ROM driver Revision: 3.20
[    7.350461] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.425630] Marking TSC unstable due to TSC halts in idle
[    7.615465] PM: Starting manual resume from disk
[    7.615473] PM: Resume from partition 8:5
[    7.615477] PM: Checking hibernation image.
[    7.615681] PM: Resume from disk failed.
[    7.675402] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.675411] EXT3-fs: write access will be enabled during recovery.
[    8.448674] kjournald starting.  Commit interval 5 seconds
[    8.448699] EXT3-fs: sda1: orphan cleanup on readonly fs
[    8.448711] ext3_orphan_cleanup: deleting unreferenced inode 2908450
[    8.448775] EXT3-fs: sda1: 1 orphan inode deleted
[    8.448781] EXT3-fs: recovery complete.
[    8.459317] EXT3-fs: mounted filesystem with ordered data mode.
[   15.827819] udevd version 124 started
[   17.533815] Linux agpgart interface v0.103
[   17.721462] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.797417] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.192213] iTCO_vendor_support: vendor-support=0
[   18.260211] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   18.261467] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   18.261673] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.404126] intel_rng: FWH not detected
[   19.540909] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   19.556020] ACPI: Power Button (FF) [PWRF]
[   19.556193] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   19.564175] ACPI: Lid Switch [LID]
[   19.564326] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   19.576028] ACPI: Sleep Button (CM) [SLPB]
[   21.524226] irda_init()
[   21.524251] NET: Registered protocol family 23
[   21.770298] nsc-ircc 00:0c: activated
[   21.770309] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   21.770383] nsc-ircc, chip->init
[   21.770398] nsc-ircc, Found chip at base=0x02e
[   21.770438] nsc-ircc, driver loaded (Dag Brattli)
[   21.771142] IrDA: Registered device irda0
[   21.771148] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   21.889220] parport_pc 00:0b: reported by Plug and Play ACPI
[   21.889280] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   22.306541] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/device:04/input/input5
[   22.316029] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   22.336996] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: found ejectable bay
[   22.337011] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: Adding notify handler
[   22.337067] ACPI: Error installing bay notify handler
[   23.158317] Yenta: CardBus bridge found at 0000:0b:00.0 [1014:056c]
[   23.215974] lib80211: common routines for IEEE802.11 drivers
[   23.215983] lib80211_crypt: registered algorithm 'NULL'
[   23.238301] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   23.238309] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   23.278412] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   23.278420] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.284742] Yenta: ISA IRQ mask 0x0c30, PCI irq 16
[   23.284749] Socket status: 30000006
[   23.284756] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x8fff
[   23.284763] cs: IO port probe 0x5000-0x8fff: clean.
[   23.286966] pcmcia: parent PCI bridge Memory window: 0xb4000000 - 0xbfffffff
[   23.286973] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd7ffffff
[   23.288577] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   23.301974] ipw2200 0000:0b:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   23.302053] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.302144] firmware: requesting ipw2200-bss.fw
[   23.758393] Non-volatile memory driver v1.2
[   23.897853] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   23.897860] thinkpad_acpi: http://ibm-acpi.sf.net/
[   23.897865] thinkpad_acpi: ThinkPad BIOS 1YET65WW (1.29 ), EC 1YHT29WW-1.06
[   23.897872] thinkpad_acpi: IBM ThinkPad T43, model 2686M4U
[   23.928027] Registered led device: tpacpi::thinklight
[   23.928576] thinkpad_acpi: another device driver is already handling bay events
[   23.928583] thinkpad_acpi: disabling subdriver bay
[   23.928678] Registered led device: tpacpi::power
[   23.928745] Registered led device: tpacpi:orange:batt
[   23.928810] Registered led device: tpacpi:green:batt
[   23.928910] Registered led device: tpacpi::dock_active
[   23.928979] Registered led device: tpacpi::bay_active
[   23.929047] Registered led device: tpacpi::dock_batt
[   23.929113] Registered led device: tpacpi::unknown_led
[   23.929180] Registered led device: tpacpi::standby
[   23.953507] thinkpad_acpi: fan_init: initial fan status is unknown, assuming it is in auto mode
[   23.953752] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
[   24.792281] ACPI: AC Adapter [AC] (off-line)
[   25.004776] ACPI: Battery Slot [BAT0] (battery present)
[   26.458021] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   26.458032] serio: Synaptics pass-through port at isa0060/serio1/input0
[   26.495674] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   28.813624] cs: IO port probe 0x100-0x3af: clean.
[   28.815439] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   28.816280] cs: IO port probe 0x820-0x8ff: clean.
[   28.816950] cs: IO port probe 0xc00-0xcf7: clean.
[   28.817913] cs: IO port probe 0xa00-0xaff: clean.
[   29.008234] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   29.008300] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   29.008340] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   29.932034] intel8x0_measure_ac97_clock: measured 55358 usecs
[   29.932042] intel8x0: clocking to 48000
[   30.801092] lp0: using parport0 (interrupt-driven).
[   31.038812] Adding 4546352k swap on /dev/sda5.  Priority:-1 extents:1 across:4546352k
[   31.093874] EXT3 FS on sda1, internal journal
[   31.670848] type=1505 audit(1235844497.055:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4004
[   31.774137] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   31.980033] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   32.295501] type=1505 audit(1235844497.679:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4009
[   32.295912] type=1505 audit(1235844497.679:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4009
[   32.530147] ip_tables: (C) 2000-2006 Netfilter Core Team
[   33.359180] ACPI: WMI: Mapper loaded
[   33.414174] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: found ejectable bay
[   33.414189] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: Adding notify handler
[   33.414243] ACPI: Error installing bay notify handler
[   34.536016] Clocksource tsc unstable (delta = 666677988 ns)
[   34.648916] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   34.720784] IBM machine detected. Enabling interrupts during APM calls.
[   34.720791] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   34.720793] apm: overridden by ACPI.
[   34.827350] ppdev: user-space parallel port driver
[   36.975013] Bluetooth: Core ver 2.13
[   36.977452] NET: Registered protocol family 31
[   36.977461] Bluetooth: HCI device and connection manager initialized
[   36.977468] Bluetooth: HCI socket layer initialized
[   37.035436] Bluetooth: L2CAP ver 2.11
[   37.035446] Bluetooth: L2CAP socket layer initialized
[   37.071470] Bluetooth: SCO (Voice Link) ver 0.6
[   37.071475] Bluetooth: SCO socket layer initialized
[   37.099158] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.099164] Bluetooth: BNEP filters: protocol multicast
[   37.149985] Bridge firewalling registered
[   37.164908] Bluetooth: RFCOMM socket layer initialized
[   37.165354] Bluetooth: RFCOMM TTY layer initialized
[   37.165357] Bluetooth: RFCOMM ver 1.10
[   39.034613] pci 0000:01:00.0: power state changed by ACPI to D0
[   39.034637] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   39.315213] [drm] Initialized drm 1.1.0 20060810
[   39.334129] pci 0000:01:00.0: setting latency timer to 64
[   39.334788] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   39.749028] [drm] Setting GART location based on new memory map
[   39.751386] [drm] Loading R300 Microcode
[   39.751432] [drm] Num pipes: 1
[   39.751444] [drm] writeback test succeeded in 1 usecs
[   41.505233] NET: Registered protocol family 17
[   88.960142] NET: Registered protocol family 10
[   88.963309] lo: Disabled Privacy Extensions
[   88.965488] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   99.884017] eth1: no IPv6 routers present
[  148.740526] ppdev0: registered pardevice
[  148.788342] ppdev0: unregistered pardevice
[  150.463368] ppdev0: registered pardevice
[  150.512286] ppdev0: unregistered pardevice
[  151.850177] ppdev0: registered pardevice
[  151.892644] ppdev0: unregistered pardevice

```

---

### Post by tstirrat on 2009-02-28
When you say pastebin, do you mean copy-pasting the entire contents?

---

### Post by tstirrat on 2009-02-28
Bump...

Feb 21 17:12:36 Rally200 kernel: [ 1207.322414] Uhhuh. NMI received for unknown reason b1 on CPU 0.
Feb 21 17:12:36 Rally200 kernel: [ 1207.322437] You have some hardware problem, likely on the PCI bus.
Feb 21 17:12:36 Rally200 kernel: [ 1207.322443] Dazed and confused, but trying to continue

This seemed interesting...

(I like the programmer's sense of humor :D)

---

### Post by tstirrat on 2009-02-28
Another weird thing: after a crash, when I reboot the computer, the computer finishes going through the startup procedures, but before the GUI itself shows up, there's a flash of the last screen before the computer froze and shut off. The bottom half of it is exactly as it was, and the top half is pixelated.

---

### Post by tstirrat on 2009-02-28
Bump

---

### Post by tstirrat on 2009-03-02
:-\"

---

### Post by sandyd on 2009-03-02
theirs bugs like yours lying around.....
[https://answers.launchpad.net/ubuntu/+question/5537](https://answers.launchpad.net/ubuntu/+question/5537)

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643/comments/9)

do you have an option in the bios for cool n' quiet?

---

### Post by tstirrat on 2009-03-02
Not that I'm aware of.

The first link looks promising - Thanks :D

---

### Post by orethrius on 2009-03-02
> **tstirrat said:**
> When you say pastebin, do you mean copy-pasting the entire contents?

Essentially, yes, to a site like [www.pastebin.com](www.pastebin.com) (typically used for collaborative coding / debugging).

---

### Post by tstirrat on 2009-03-03
Will the error itself only show up in the logs if the computer has crashed recently? I haven't had it crash in about 3 days now.

And thank you for the info on pastebin :D

---

