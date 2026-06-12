---
title: "USB 2.0 on Thinkpad t42"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by wogga on 2009-11-09
I just upgraded to 9.10. Still no apparent support for usb 2.0. I'm running a Tb external drive with usb 2.0 capability, and dreading transferring at 2mbps or less. This machine apparently supports usb 2.0, but i'm a total noob and don't know how to enable the support. Can anyone help? I had xp running on this machine shortly, and it too had issues with the usb 2.0, telling me that i had the capability, but that i needed a special hotfix to enable it.

 Here is the output of dmesg:

```
[    0.044467] Booting paravirtualized kernel on bare hardware
[    0.044699] regulator: core version 0.5
[    0.044721] Time: 22:07:21  Date: 11/09/09
[    0.044776] NET: Registered protocol family 16
[    0.044922] EISA bus registered
[    0.044939] ACPI: bus type pci registered
[    0.045184] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
[    0.045186] PCI: Using configuration type 1 for base access
[    0.046322] bio: create slab <bio-0> at 0
[    0.048560] ACPI: EC: EC description table is found, configuring boot EC
[    0.056620] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.069332] ACPI: Interpreter enabled
[    0.069338] ACPI: (supports S0 S3 S4 S5)
[    0.069365] ACPI: Using PIC for interrupt routing
[    0.084493] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.084496] ACPI: EC: driver started in interrupt mode
[    0.084540] ACPI: Power Resource [PUBS] (on)
[    0.089024] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.089049] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.089094] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.089210] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
[    0.089263] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.089316] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.089377] pci 0000:00:1d.7: reg 10 32bit mmio: [0xc0000000-0xc00003ff]
[    0.089434] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.089439] pci 0000:00:1d.7: PME# disabled
[    0.089528] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.089533] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.089558] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.089565] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.089573] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.089580] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.089587] pci 0000:00:1f.1: reg 20 io port: [0x1860-0x186f]
[    0.089595] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.089646] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.089690] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.089697] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.089705] pci 0000:00:1f.5: reg 18 32bit mmio: [0xc0000c00-0xc0000dff]
[    0.089712] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xc0000800-0xc00008ff]
[    0.089741] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.089746] pci 0000:00:1f.5: PME# disabled
[    0.089776] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.089783] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.089820] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.089825] pci 0000:00:1f.6: PME# disabled
[    0.089861] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.089867] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.089873] pci 0000:01:00.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.089889] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.089908] pci 0000:01:00.0: supports D1 D2
[    0.089943] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.089947] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.089952] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.089987] pci 0000:02:00.0: reg 10 32bit mmio: [0xb0000000-0xb0000fff]
[    0.090007] pci 0000:02:00.0: supports D1 D2
[    0.090009] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090014] pci 0000:02:00.0: PME# disabled
[    0.090049] pci 0000:02:00.1: reg 10 32bit mmio: [0xb1000000-0xb1000fff]
[    0.090068] pci 0000:02:00.1: supports D1 D2
[    0.090071] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090076] pci 0000:02:00.1: PME# disabled
[    0.090116] pci 0000:02:01.0: reg 10 32bit mmio: [0xc0220000-0xc023ffff]
[    0.090123] pci 0000:02:01.0: reg 14 32bit mmio: [0xc0200000-0xc020ffff]
[    0.090131] pci 0000:02:01.0: reg 18 io port: [0x8000-0x803f]
[    0.090151] pci 0000:02:01.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.090170] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
[    0.090175] pci 0000:02:01.0: PME# disabled
[    0.090208] pci 0000:02:02.0: reg 10 32bit mmio: [0xc0214000-0xc0214fff]
[    0.090252] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
[    0.090257] pci 0000:02:02.0: PME# disabled
[    0.090296] pci 0000:00:1e.0: transparent bridge
[    0.090301] pci 0000:00:1e.0: bridge io port: [0x4000-0x8fff]
[    0.090306] pci 0000:00:1e.0: bridge 32bit mmio: [0xc0200000-0xcfffffff]
[    0.090311] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.090351] pci_bus 0000:00: on NUMA node 0
[    0.090356] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.090410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.090439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.094351] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.094544] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.094734] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.094925] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.095095] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.095266] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.095442] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.095633] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.095868] SCSI subsystem initialized
[    0.095919] libata version 3.00 loaded.
[    0.096017] usbcore: registered new interface driver usbfs
[    0.096045] usbcore: registered new interface driver hub
[    0.096074] usbcore: registered new device driver usb
[    0.096218] ACPI: WMI: Mapper loaded
[    0.096220] PCI: Using ACPI for IRQ routing
[    0.096517] Bluetooth: Core ver 2.15
[    0.096547] NET: Registered protocol family 31
[    0.096550] Bluetooth: HCI device and connection manager initialized
[    0.096553] Bluetooth: HCI socket layer initialized
[    0.096556] NetLabel: Initializing
[    0.096558] NetLabel:  domain hash size = 128
[    0.096559] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.096576] NetLabel:  unlabeled traffic allowed by default
[    0.098651] pnp: PnP ACPI init
[    0.098670] ACPI: bus type pnp registered
[    0.102604] pnp: PnP ACPI: found 13 devices
[    0.102608] ACPI: ACPI bus type pnp unregistered
[    0.102612] PnPBIOS: Disabled by ACPI PNP
[    0.102626] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.102631] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.102634] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.102638] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.102642] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.102645] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.102649] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.102653] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.102657] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.102660] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.102664] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.102668] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.102671] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[    0.102675] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.102684] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.102688] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.102691] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.102695] system 00:02: ioport range 0x1600-0x162f has been reserved
[    0.102699] system 00:02: ioport range 0x1632-0x167f has been reserved
[    0.102702] system 00:02: ioport range 0x1630-0x1631 has been reserved
[    0.137381] AppArmor: AppArmor Filesystem Enabled
[    0.137414] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.137417] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.137422] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.137427] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.137436] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.137439] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
[    0.137444] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
[    0.137449] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
[    0.137455] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.137460] pci 0000:02:00.1: CardBus bridge, secondary bus 0000:07
[    0.137463] pci 0000:02:00.1:   IO window: 0x004800-0x0048ff
[    0.137468] pci 0000:02:00.1:   IO window: 0x004c00-0x004cff
[    0.137473] pci 0000:02:00.1:   PREFETCH window: 0xec000000-0xefffffff
[    0.137478] pci 0000:02:00.1:   MEM window: 0xc8000000-0xcbffffff
[    0.137484] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.137488] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
[    0.137494] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
[    0.137499] pci 0000:00:1e.0:   PREFETCH window: 0xe8000000-0xefffffff
[    0.137516] pci 0000:00:1e.0: setting latency timer to 64
[    0.137855] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.137858] PCI: setting IRQ 11 as level-triggered
[    0.137864] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.138186] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.138190] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.138198] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.138202] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.138205] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.138208] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.138212] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.138215] pci_bus 0000:02: resource 0 io:  [0x4000-0x8fff]
[    0.138218] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xcfffffff]
[    0.138222] pci_bus 0000:02: resource 2 pref mem [0xe8000000-0xefffffff]
[    0.138225] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.138228] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.138232] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.138235] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.138238] pci_bus 0000:03: resource 2 pref mem [0xe8000000-0xebffffff]
[    0.138242] pci_bus 0000:03: resource 3 mem: [0xc4000000-0xc7ffffff]
[    0.138245] pci_bus 0000:07: resource 0 io:  [0x4800-0x48ff]
[    0.138248] pci_bus 0000:07: resource 1 io:  [0x4c00-0x4cff]
[    0.138251] pci_bus 0000:07: resource 2 pref mem [0xec000000-0xefffffff]
[    0.138255] pci_bus 0000:07: resource 3 mem: [0xc8000000-0xcbffffff]
[    0.138294] NET: Registered protocol family 2
[    0.138401] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.138784] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.140240] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.141143] TCP: Hash tables configured (established 131072 bind 65536)
[    0.141148] TCP reno registered
[    0.141301] NET: Registered protocol family 1
[    0.141410] Trying to unpack rootfs image as initramfs...
[    0.393035] Freeing initrd memory: 7464k freed
[    0.403736] Simple Boot Flag at 0x35 set to 0x1
[    0.403846] cpufreq-nforce2: No nForce2 chipset.
[    0.403894] Scanning for low memory corruption every 60 seconds
[    0.404156] audit: initializing netlink socket (disabled)
[    0.404190] type=2000 audit(1257804440.404:1): initialized
[    0.414574] highmem bounce pool size: 64 pages
[    0.414581] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.416281] VFS: Disk quotas dquot_6.5.2
[    0.416350] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.416980] fuse init (API version 7.12)
[    0.417077] msgmni has been set to 1732
[    0.417309] alg: No test for stdrng (krng)
[    0.417322] io scheduler noop registered
[    0.417325] io scheduler anticipatory registered
[    0.417327] io scheduler deadline registered
[    0.417379] io scheduler cfq registered (default)
[    0.417465] pci 0000:01:00.0: Boot video device
[    0.417580] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.417607] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.418071] ACPI: AC Adapter [AC] (on-line)
[    0.418155] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.418160] ACPI: Power Button [PWRF]
[    0.418215] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.418674] ACPI: Lid Switch [LID]
[    0.418727] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.418732] ACPI: Sleep Button [SLPB]
[    0.421002] Marking TSC unstable due to TSC halts in idle
[    0.421024] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.421051] processor LNXCPU:00: registered as cooling_device0
[    0.421056] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.424020] Switched to high resolution mode on CPU 0
[    0.426579] thermal LNXTHERM:01: registered as thermal_zone0
[    0.426588] ACPI: Thermal Zone [THM0] (46 C)
[    0.426638] isapnp: Scanning for PnP cards...
[    0.779859] isapnp: No Plug & Play device found
[    0.781124] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.782026] serial 00:0a: activated
[    0.782115] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.782224] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.782232] serial 0000:00:1f.6: PCI INT B disabled
[    0.783276] brd: module loaded
[    0.783799] loop: module loaded
[    0.783881] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.784041] ata_piix 0000:00:1f.1: version 2.13
[    0.784050] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.784422] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.784427] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.784474] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.784549] scsi0 : ata_piix
[    0.784690] scsi1 : ata_piix
[    0.785639] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    0.785643] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    0.786602] Fixed MDIO Bus: probed
[    0.786642] PPP generic driver version 2.4.2
[    0.786740] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.817915] ACPI: Battery Slot [BAT0] (battery present)
[    0.822164] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.822488] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.822492] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.822507] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.822512] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.822574] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.826482] ehci_hcd 0000:00:1d.7: debug port 1
[    0.826489] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.826498] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    0.840036] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.840120] usb usb1: configuration #1 chosen from 1 choice
[    0.840154] hub 1-0:1.0: USB hub found
[    0.840164] hub 1-0:1.0: 6 ports detected
[    0.840234] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.840257] uhci_hcd: USB Universal Host Controller Interface driver
[    0.840730] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.840737] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.840744] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.840748] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.840780] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.840802] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    0.840891] usb usb2: configuration #1 chosen from 1 choice
[    0.840921] hub 2-0:1.0: USB hub found
[    0.840936] hub 2-0:1.0: 2 ports detected
[    0.841438] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.841762] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.841767] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.841774] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.841777] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.841815] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.841837] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    0.841920] usb usb3: configuration #1 chosen from 1 choice
[    0.841950] hub 3-0:1.0: USB hub found
[    0.841958] hub 3-0:1.0: 2 ports detected
[    0.842007] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.842014] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.842018] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.842049] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.842070] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    0.842163] usb usb4: configuration #1 chosen from 1 choice
[    0.842195] hub 4-0:1.0: USB hub found
[    0.842202] hub 4-0:1.0: 2 ports detected
[    0.842306] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.848919] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.848926] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.848987] mice: PS/2 mouse device common for all mice
[    0.849097] rtc_cmos 00:06: RTC can wake from S4
[    0.849135] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.849152] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.849265] device-mapper: uevent: version 1.0.3
[    0.849356] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.849440] device-mapper: multipath: version 1.1.0 loaded
[    0.849444] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.849572] EISA: Probing bus 0 at eisa.0
[    0.849578] Cannot allocate resource for EISA slot 1
[    0.849581] Cannot allocate resource for EISA slot 2
[    0.849583] Cannot allocate resource for EISA slot 3
[    0.849586] Cannot allocate resource for EISA slot 4
[    0.849588] Cannot allocate resource for EISA slot 5
[    0.849591] Cannot allocate resource for EISA slot 6
[    0.849593] Cannot allocate resource for EISA slot 7
[    0.849596] Cannot allocate resource for EISA slot 8
[    0.849598] EISA: Detected 0 cards.
[    0.849687] cpuidle: using governor ladder
[    0.849756] cpuidle: using governor menu
[    0.850305] TCP cubic registered
[    0.850485] NET: Registered protocol family 10
[    0.850954] lo: Disabled Privacy Extensions
[    0.851287] NET: Registered protocol family 17
[    0.851306] Bluetooth: L2CAP ver 2.13
[    0.851308] Bluetooth: L2CAP socket layer initialized
[    0.851312] Bluetooth: SCO (Voice Link) ver 0.6
[    0.851313] Bluetooth: SCO socket layer initialized
[    0.851351] Bluetooth: RFCOMM TTY layer initialized
[    0.851354] Bluetooth: RFCOMM socket layer initialized
[    0.851356] Bluetooth: RFCOMM ver 1.11
[    0.851485] P-state transition latency capped at 20 uS
[    0.851777] Using IPI No-Shortcut mode
[    0.851843] PM: Resume from disk failed.
[    0.851857] registered taskstats version 1
[    0.851975]   Magic number: 1:107:148
[    0.851989] bdi 1:0: hash matches
[    0.852078] rtc_cmos 00:06: setting system clock to 2009-11-09 22:07:21 UTC (1257804441)
[    0.852082] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.852085] EDD information not available.
[    0.854159] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.948710] ata2.00: ATAPI: UJDA765 DVD/CDRW, 1.02, max UDMA/33
[    0.949202] ata1.00: ATA-6: HTS541040G9AT00, MB2IA5BJ, max UDMA/100
[    0.949205] ata1.00: 78140160 sectors, multi 16: LBA 
[    0.964522] ata2.00: configured for UDMA/33
[    0.964930] ata1.00: configured for UDMA/100
[    0.965073] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2I PQ: 0 ANSI: 5
[    0.965206] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.965255] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.965310] sd 0:0:0:0: [sda] Write Protect is off
[    0.965314] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.965341] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.965481]  sda:
[    0.967054] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA765 DVD/CDRW 1.02 PQ: 0 ANSI: 5
[    0.970086] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.970090] Uniform CD-ROM driver Revision: 3.20
[    0.970175] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.970217] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.981877]  sda1 sda2 < sda5 >
[    1.004733] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.004751] Freeing unused kernel memory: 540k freed
[    1.005161] Write protecting the kernel text: 4568k
[    1.005203] Write protecting the kernel read-only data: 1836k
[    1.202084] Linux agpgart interface v0.103
[    1.206190] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    1.222221] Floppy drive(s): fd0 is 1.44M
[    1.226903] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/device:04/input/input5
[    1.226949] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.231458] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    1.231462] Copyright (c) 1999-2006 Intel Corporation.
[    1.231504] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.264929] FDC 0 is a National Semiconductor PC87306
[    1.506993] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:d6:aa:bf
[    1.554209] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.576861] [drm] Initialized drm 1.1.0 20060810
[    1.600711] [drm] radeon default to kernel modesetting DISABLED.
[    1.600867] pci 0000:01:00.0: power state changed by ACPI to D0
[    1.600881] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.602366] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    1.621477] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    2.623318] PM: Starting manual resume from disk
[    2.623323] PM: Resume from partition 8:5
[    2.623326] PM: Checking hibernation image.
[    2.623481] PM: Resume from disk failed.
[    2.636022] Clocksource tsc unstable (delta = -122281630 ns)
[    2.668048] kjournald starting.  Commit interval 5 seconds
[    2.668058] EXT3-fs: mounted filesystem with writeback data mode.
[    3.853345] type=1505 audit(1257804444.499:2): operation="profile_load" pid=361 name=/usr/share/gdm/guest-session/Xsession
[    4.064141] type=1505 audit(1257804444.711:3): operation="profile_load" pid=362 name=/sbin/dhclient3
[    4.064204] type=1505 audit(1257804444.711:4): operation="profile_load" pid=362 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.064253] type=1505 audit(1257804444.711:5): operation="profile_load" pid=362 name=/usr/lib/connman/scripts/dhclient-script
[   16.477568] type=1505 audit(1257804457.123:6): operation="profile_load" pid=363 name=/usr/bin/evince
[   16.478753] type=1505 audit(1257804457.123:7): operation="profile_load" pid=363 name=/usr/bin/evince-previewer
[   16.479711] type=1505 audit(1257804457.123:8): operation="profile_load" pid=363 name=/usr/bin/evince-thumbnailer
[   16.818817] type=1505 audit(1257804457.463:9): operation="profile_load" pid=365 name=/usr/lib/cups/backend/cups-pdf
[   16.819013] type=1505 audit(1257804457.463:10): operation="profile_load" pid=365 name=/usr/sbin/cupsd
[   16.916368] type=1505 audit(1257804457.563:11): operation="profile_load" pid=366 name=/usr/sbin/tcpdump
[   17.965616] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k 
[   18.524435] EXT3 FS on sda1, internal journal
[   18.840892] udev: starting version 147
[   20.113574] parport_pc 00:0b: reported by Plug and Play ACPI
[   20.113616] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   20.592984] irda_init()
[   20.592998] NET: Registered protocol family 23
[   21.359797] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.414947] nsc-ircc 00:0c: activated
[   21.414953] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   21.415119] nsc-ircc, chip->init
[   21.415128] nsc-ircc, Found chip at base=0x02e
[   21.415151] nsc-ircc, driver loaded (Dag Brattli)
[   21.415879] IrDA: Registered device irda0
[   21.415881] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   21.828848] lp0: using parport0 (interrupt-driven).
[   21.832413] ppdev: user-space parallel port driver
[   21.834943] Non-volatile memory driver v1.3
[   21.838340] intel_rng: FWH not detected
[   21.999527] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   21.999533] serio: Synaptics pass-through port at isa0060/serio1/input0
[   22.040629] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   22.509517] lib80211: common routines for IEEE802.11 drivers
[   22.509522] lib80211_crypt: registered algorithm 'NULL'
[   22.833589] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.051265] thinkpad_acpi: ThinkPad ACPI Extras v0.23
[   23.051269] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   23.051271] thinkpad_acpi: ThinkPad BIOS 1RETDKWW (3.16 ), EC 1RHT71WW-3.04
[   23.051274] thinkpad_acpi: IBM ThinkPad T42, model 2373YCP
[   23.057269] Registered led device: tpacpi::thinklight
[   23.057303] Registered led device: tpacpi::power
[   23.057321] Registered led device: tpacpi::standby
[   23.060373] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
[   23.670404] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   23.670410] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   24.318510] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0552]
[   24.318529] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
[   24.318532] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
[   24.318537] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21b22, devctl 0x64
[   24.552452] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0430, PCI irq 11
[   24.552457] yenta_cardbus 0000:02:00.0: Socket status: 30000086
[   24.552467] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   24.552472] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: clean.
[   24.553749] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   24.553754] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   24.553986] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0552]
[   24.554002] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
[   24.554005] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
[   24.554011] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21b22, devctl 0x64
[   24.576724] psmouse serio2: ID: 10 00 64
[   24.784476] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0430, PCI irq 11
[   24.784481] yenta_cardbus 0000:02:00.1: Socket status: 30000086
[   24.784491] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   24.784496] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: clean.
[   24.785782] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   24.785786] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   24.796732] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   24.796736] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   24.796828] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   24.796895] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   24.796941] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[   25.429244] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   25.430258] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.430700] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   25.431067] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   25.431589] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   25.493251] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   25.494242] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.494674] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   25.495041] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   25.495558] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   25.621226] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   25.789590] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   25.789646] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   26.712134] intel8x0_measure_ac97_clock: measured 55528 usecs (2675 samples)
[   26.712139] intel8x0: clocking to 48000
[   26.816879] type=1505 audit(1257804467.463:12): operation="profile_replace" pid=793 name=/usr/share/gdm/guest-session/Xsession
[   27.358623] type=1505 audit(1257804468.003:13): operation="profile_replace" pid=801 name=/sbin/dhclient3
[   27.358765] type=1505 audit(1257804468.003:14): operation="profile_replace" pid=801 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   27.358849] type=1505 audit(1257804468.003:15): operation="profile_replace" pid=801 name=/usr/lib/connman/scripts/dhclient-script
[   28.758781] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   29.102001] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
[   33.062619] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.978327] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   37.978348] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   37.978385] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   38.292126] [drm] Setting GART location based on new memory map
[   38.292138] [drm] Loading R100 Microcode
[   38.292194] [drm] writeback test succeeded in 2 usecs
[   41.155574] type=1505 audit(1257804481.799:16): operation="profile_replace" pid=804 name=/usr/bin/evince
[   41.158460] type=1505 audit(1257804481.803:17): operation="profile_replace" pid=804 name=/usr/bin/evince-previewer
[   41.160150] type=1505 audit(1257804481.807:18): operation="profile_replace" pid=804 name=/usr/bin/evince-thumbnailer
[   41.504041] type=1505 audit(1257804482.147:19): operation="profile_replace" pid=978 name=/usr/lib/cups/backend/cups-pdf
[   41.504562] type=1505 audit(1257804482.151:20): operation="profile_replace" pid=978 name=/usr/sbin/cupsd
[   41.604552] type=1505 audit(1257804482.251:21): operation="profile_replace" pid=981 name=/usr/sbin/tcpdump
[   43.836025] eth1: no IPv6 routers present
[   87.276680] lib80211_crypt: registered algorithm 'CCMP'
[   87.468106] padlock: VIA PadLock not detected.
[   92.262087] lib80211_crypt: registered algorithm 'TKIP'
[  145.428079] usb 1-3: new high speed USB device using ehci_hcd and address 2
[  145.660049] usb 1-3: device descriptor read/64, error -71
[  145.984092] usb 1-3: device descriptor read/64, error -71
[  146.200072] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  146.332054] usb 1-3: device descriptor read/64, error -71
[  146.561959] usb 1-3: device descriptor read/64, error -71
[  146.776071] usb 1-3: new high speed USB device using ehci_hcd and address 4
[  147.192051] usb 1-3: device not accepting address 4, error -71
[  147.308068] usb 1-3: new high speed USB device using ehci_hcd and address 5
[  147.824055] usb 1-3: device not accepting address 5, error -71
[  147.824090] hub 1-0:1.0: unable to enumerate USB device on port 3
[  148.092073] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  148.237403] usb 3-1: not running at top speed; connect to a high speed hub
[  148.271649] usb 3-1: configuration #1 chosen from 1 choice
[  148.373664] Initializing USB Mass Storage driver...
[  148.376089] scsi2 : SCSI emulation for USB Mass Storage devices
[  148.376363] usbcore: registered new interface driver usb-storage
[  148.376373] USB Mass Storage support registered.
[  148.382226] usb-storage: device found at 2
[  148.382229] usb-storage: waiting for device to settle before scanning
[  153.381221] usb-storage: device scan complete
[  153.384394] scsi 2:0:0:0: Direct-Access     ST310005 20AS                  PQ: 0 ANSI: 2 CCS
[  153.385494] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  153.406971] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[  153.411191] sd 2:0:0:0: [sdb] Write Protect is off
[  153.411203] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[  153.411211] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  153.421178] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  153.421190]  sdb: sdb1
[  153.567287] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  153.567301] sd 2:0:0:0: [sdb] Attached SCSI disk
c@HAL-9000:~$
```

*bump*
Could really use some help. Will happily post any requested screenshots or other info for anyone who can lend a hand.

---

### Post by twisted_steel on 2009-11-09
Hmm, USB 2.0 is working on my T42, though there are different models out there.  I don't have an external drive to test, just my mp3 player.  Have you tried booting with the drive plugged in to see if you get a different result?

---

### Post by wogga on 2009-11-09
Yup. Result is the same.

---

### Post by tgalati4 on 2009-11-09
It should work out of the box.

T42's and others have had problems with static-electricity damage to the USB controller.  It's not repairable (other than replacing the motherboard).  It's possible that your controller is damaged, but still able to run at USB 1.0 speeds.

---

### Post by twisted_steel on 2009-11-09
Shot in the dark here ...

Try the following in a terminal
```
sudo modprobe -r ehci_hcd
sudo modprobe ehci_hcd
```This will remove the USB 2.0 module and reload it.  It has fixed other problems for people in the past.  See if you get any improvements with the speed and in dmesg.

---

### Post by wogga on 2009-11-10
c@HAL-9000:~$ sudo modprobe -r ehci_hcd
[sudo] password for c: 
FATAL: Module ehci_hcd not found.

:-(

---

### Post by twisted_steel on 2009-11-10
Apparently ehci_hcd is no longer build as a module in Karmic.  Check out comment #3 on [this page]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354832") for a potential workaround.

---

