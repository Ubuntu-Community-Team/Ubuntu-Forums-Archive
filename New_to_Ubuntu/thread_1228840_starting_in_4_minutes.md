---
title: "starting in 4 minutes??"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by duruttye on 2009-08-01
Hey there!

I don't know what happened, but my ubuntu machine is starting up in about 4 minutes, it seems that it is loading okay, but it goes really slow. After it gets going, everything is back to normal.

I'm using ubuntu 9.04 with latest updates on a dell vostro laptop (3 GB memory, 2,2 Mhz intel dual core).

here is the dmesg output

[HTML]
[    0.571222] pci 0000:03:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.571235] pci 0000:03:01.0: supports D1 D2
[    0.571237] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.571242] pci 0000:03:01.0: PME# disabled
[    0.571290] pci 0000:03:01.1: reg 10 32bit mmio: [0xf69ff800-0xf69fffff]
[    0.571346] pci 0000:03:01.1: supports D1 D2
[    0.571348] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.571353] pci 0000:03:01.1: PME# disabled
[    0.571402] pci 0000:03:01.2: reg 10 32bit mmio: [0xf69ff600-0xf69ff6ff]
[    0.571458] pci 0000:03:01.2: supports D1 D2
[    0.571459] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.571465] pci 0000:03:01.2: PME# disabled
[    0.571513] pci 0000:03:01.3: reg 10 32bit mmio: [0xf69ff700-0xf69ff7ff]
[    0.571569] pci 0000:03:01.3: supports D1 D2
[    0.571571] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.571576] pci 0000:03:01.3: PME# disabled
[    0.571657] pci 0000:00:1e.0: transparent bridge
[    0.571665] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6900000-0xf69fffff]
[    0.571723] bus 00 -> node 0
[    0.571730] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.572195] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.572374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.572505] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.572639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.583198] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    0.583333] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.583470] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *3
[    0.583589] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11) *0, disabled.
[    0.583723] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.583859] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.583993] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.584122] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.584274] ACPI: WMI: Mapper loaded
[    0.584329] SCSI subsystem initialized
[    0.584329] libata version 3.00 loaded.
[    0.584329] usbcore: registered new interface driver usbfs
[    0.584329] usbcore: registered new interface driver hub
[    0.584329] usbcore: registered new device driver usb
[    0.584329] PCI: Using ACPI for IRQ routing
[    0.592010] Bluetooth: Core ver 2.13
[    0.592024] NET: Registered protocol family 31
[    0.592024] Bluetooth: HCI device and connection manager initialized
[    0.592024] Bluetooth: HCI socket layer initialized
[    0.592024] NET: Registered protocol family 8
[    0.592024] NET: Registered protocol family 20
[    0.592034] NetLabel: Initializing
[    0.592036] NetLabel:  domain hash size = 128
[    0.592037] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.592050] NetLabel:  unlabeled traffic allowed by default
[    0.592067] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.592072] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.596070] AppArmor: AppArmor Filesystem Enabled
[    0.600013] Switched to high resolution mode on CPU 0
[    0.600420] Switched to high resolution mode on CPU 1
[    0.604010] pnp: PnP ACPI init
[    0.604021] ACPI: bus type pnp registered
[    0.625362] pnp 00:09: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.625365] pnp 00:09: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.625459] pnp 00:0a: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.625462] pnp 00:0a: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.625465] pnp 00:0a: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.625468] pnp 00:0a: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649418] pnp: PnP ACPI: found 12 devices
[    0.649420] ACPI: ACPI bus type pnp unregistered
[    0.649424] PnPBIOS: Disabled by ACPI PNP
[    0.649436] system 00:05: ioport range 0xc80-0xcff could not be reserved
[    0.649443] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.649449] system 00:09: ioport range 0x900-0x97f has been reserved
[    0.649452] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.649458] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[    0.649461] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[    0.649463] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[    0.649466] system 00:0a: ioport range 0x809-0x809 has been reserved
[    0.649472] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[    0.649474] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[    0.649477] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.649480] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.649482] system 00:0b: iomem range 0x100000-0xbf6c13ff could not be reserved
[    0.649485] system 00:0b: iomem range 0xbf6c1400-0xbf6fffff has been reserved
[    0.649488] system 00:0b: iomem range 0xbf700000-0xbf7fffff has been reserved
[    0.649490] system 00:0b: iomem range 0xffe00000-0xffffffff has been reserved
[    0.649493] system 00:0b: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.649496] system 00:0b: iomem range 0xfec00000-0xfec0ffff has been reserved
[    0.649498] system 00:0b: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.649501] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.649503] system 00:0b: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.649506] system 00:0b: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.649508] system 00:0b: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.649511] system 00:0b: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.649513] system 00:0b: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.649516] system 00:0b: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.684246] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.684249] pci 0000:00:1c.0:   IO window: disabled
[    0.684256] pci 0000:00:1c.0:   MEM window: disabled
[    0.684261] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.684269] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.684271] pci 0000:00:1c.1:   IO window: disabled
[    0.684278] pci 0000:00:1c.1:   MEM window: 0xf6c00000-0xf6cfffff
[    0.684283] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.684293] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.684296] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
[    0.684303] pci 0000:00:1c.5:   MEM window: 0xf6a00000-0xf6bfffff
[    0.684309] pci 0000:00:1c.5:   PREFETCH window: 0x000000f0000000-0x000000f00fffff
[    0.684323] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
[    0.684325] pci 0000:03:01.0:   IO window: 0x002000-0x0020ff
[    0.684330] pci 0000:03:01.0:   IO window: 0x002400-0x0024ff
[    0.684336] pci 0000:03:01.0:   PREFETCH window: 0xc4000000-0xc7ffffff
[    0.684341] pci 0000:03:01.0:   MEM window: 0xc8000000-0xcbffffff
[    0.684347] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.684351] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.684357] pci 0000:00:1e.0:   MEM window: 0xf6900000-0xf69fffff
[    0.684363] pci 0000:00:1e.0:   PREFETCH window: 0x000000c4000000-0x000000c7ffffff
[    0.684383] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.684390] pci 0000:00:1c.0: setting latency timer to 64
[    0.684401] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.684407] pci 0000:00:1c.1: setting latency timer to 64
[    0.684417] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.684422] pci 0000:00:1c.5: setting latency timer to 64
[    0.684431] pci 0000:00:1e.0: setting latency timer to 64
[    0.684441] pci 0000:03:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.684447] bus: 00 index 0 io port: [0x00-0xffff]
[    0.684449] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.684451] bus: 0b index 0 mmio: [0x0-0x0]
[    0.684453] bus: 0b index 1 mmio: [0x0-0x0]
[    0.684455] bus: 0b index 2 mmio: [0x0-0x0]
[    0.684456] bus: 0b index 3 mmio: [0x0-0x0]
[    0.684458] bus: 0c index 0 mmio: [0x0-0x0]
[    0.684460] bus: 0c index 1 mmio: [0xf6c00000-0xf6cfffff]
[    0.684462] bus: 0c index 2 mmio: [0x0-0x0]
[    0.684464] bus: 0c index 3 mmio: [0x0-0x0]
[    0.684466] bus: 09 index 0 io port: [0xd000-0xdfff]
[    0.684468] bus: 09 index 1 mmio: [0xf6a00000-0xf6bfffff]
[    0.684470] bus: 09 index 2 mmio: [0xf0000000-0xf00fffff]
[    0.684471] bus: 09 index 3 mmio: [0x0-0x0]
[    0.684473] bus: 03 index 0 io port: [0x2000-0x2fff]
[    0.684475] bus: 03 index 1 mmio: [0xf6900000-0xf69fffff]
[    0.684478] bus: 03 index 2 mmio: [0xc4000000-0xc7ffffff]
[    0.684479] bus: 03 index 3 io port: [0x00-0xffff]
[    0.684481] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.684483] bus: 04 index 0 io port: [0x2000-0x20ff]
[    0.684485] bus: 04 index 1 io port: [0x2400-0x24ff]
[    0.684487] bus: 04 index 2 mmio: [0xc4000000-0xc7ffffff]
[    0.684489] bus: 04 index 3 mmio: [0xc8000000-0xcbffffff]
[    0.684499] NET: Registered protocol family 2
[    0.696053] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.696309] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.696782] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.697129] TCP: Hash tables configured (established 131072 bind 65536)
[    0.697132] TCP reno registered
[    0.704100] NET: Registered protocol family 1
[    0.704230] checking if image is initramfs... it is
[    1.310367] Freeing initrd memory: 7385k freed
[    1.310584] cpufreq: No nForce2 chipset.
[    1.310730] audit: initializing netlink socket (disabled)
[    1.310757] type=2000 audit(1249137473.308:1): initialized
[    1.317854] highmem bounce pool size: 64 pages
[    1.317859] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.319136] VFS: Disk quotas dquot_6.5.1
[    1.319196] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.319783] fuse init (API version 7.10)
[    1.319862] msgmni has been set to 1672
[    1.320039] alg: No test for stdrng (krng)
[    1.320053] io scheduler noop registered
[    1.320054] io scheduler anticipatory registered
[    1.320056] io scheduler deadline registered
[    1.320070] io scheduler cfq registered (default)
[    1.320082] pci 0000:00:02.0: Boot video device
[    1.321810] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.321868] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.321910] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.321927] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.321943] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.321954] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.322036] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.322091] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.322128] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    1.322146] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.322158] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.322169] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.322249] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.322304] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.322342] pcieport-driver 0000:00:1c.5: irq 2301 for MSI/MSI-X
[    1.322359] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.322371] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.322382] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.322469] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.322550] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.322690] ACPI: AC Adapter [AC] (on-line)
[    1.353398] ACPI: Battery Slot [BAT0] (battery present)
[    1.353474] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.356139] ACPI: Lid Switch [LID]
[    1.356182] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.356189] ACPI: Power Button (CM) [PBTN]
[    1.356227] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.356230] ACPI: Sleep Button (CM) [SBTN]
[    1.356790] ACPI: SSDT BF6C20F2, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.357160] ACPI: SSDT BF6C1A88, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.357535] Monitor-Mwait will be used to enter C-1 state
[    1.357538] Monitor-Mwait will be used to enter C-2 state
[    1.357540] Monitor-Mwait will be used to enter C-3 state
[    1.357556] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.357584] processor ACPI_CPU:00: registered as cooling_device0
[    1.357588] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.357927] ACPI: SSDT BF6C2378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.358244] ACPI: SSDT BF6C206D, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.358658] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.358678] processor ACPI_CPU:01: registered as cooling_device1
[    1.358681] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.369016] thermal LNXTHERM:01: registered as thermal_zone0
[    1.377381] ACPI: Thermal Zone [THM] (57 C)
[    1.377441] isapnp: Scanning for PnP cards...
[    1.731586] isapnp: No Plug & Play device found
[    1.741193] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.742216] brd: module loaded
[    1.742514] loop: module loaded
[    1.742581] Fixed MDIO Bus: probed
[    1.742587] PPP generic driver version 2.4.2
[    1.742641] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.742673] Driver 'sd' needs updating - please use bus_type methods
[    1.742684] Driver 'sr' needs updating - please use bus_type methods
[    1.742757] ata_piix 0000:00:1f.2: version 2.12
[    1.742771] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.742776] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.896047] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.896123] scsi0 : ata_piix
[    1.896218] scsi1 : ata_piix
[    1.897100] ata1: SATA max UDMA/133 cmd 0x6e70 ctl 0x6e78 bmdma 0x6ea0 irq 17
[    1.897108] ata2: SATA max UDMA/133 cmd 0x6e80 ctl 0x6e88 bmdma 0x6ea8 irq 17
[    2.692103] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.692122] ata1.01: SATA link down (SStatus 0 SControl 300)
[    2.747426] ata1.00: ATA-8: WDC WD1200BEVT-75ZCT2, 11.01A11, max UDMA/133
[    2.747428] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    2.761445] ata1.00: configured for UDMA/133
[    3.206003] irq 17: nobody cared (try booting with the "irqpoll" option)
[    3.206053] Pid: 0, comm: swapper Not tainted 2.6.28-14-generic #47-Ubuntu
[    3.206055] Call Trace:
[    3.206063]  [<c04fde46>] ? printk+0x18/0x1a
[    3.206068]  [<c017fe77>] __report_bad_irq+0x27/0x90
[    3.206071]  [<c018003e>] note_interrupt+0x15e/0x1a0
[    3.206075]  [<c017ec09>] ? handle_IRQ_event+0x39/0x70
[    3.206078]  [<c0180603>] handle_fasteoi_irq+0xa3/0xd0
[    3.206083]  [<c015b8b7>] ? tick_check_idle+0x17/0x30
[    3.206087]  [<c010684e>] do_IRQ+0x7e/0xa0
[    3.206090]  [<c01051f3>] common_interrupt+0x23/0x30
[    3.206093]  [<c010b012>] ? mwait_idle+0x42/0x50
[    3.206096]  [<c010285d>] cpu_idle+0x6d/0xd0
[    3.206100]  [<c04ee48e>] rest_init+0x4e/0x60
[    3.206105]  [<c07318fd>] start_kernel+0x310/0x37c
[    3.206108]  [<c07313a4>] ? unknown_bootoption+0x0/0x1f8
[    3.206111]  [<c0731099>] __init_begin+0x99/0xa1
[    3.206113] handlers:
[    3.206150] [<c0391380>] (ata_sff_interrupt+0x0/0x230)
[    3.206263] Disabling IRQ #17
[    3.556091] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.556109] ata2.01: SATA link down (SStatus 0 SControl 0)
[    8.560134] ata2.00: qc timeout (cmd 0xa1)
[    8.560140] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[    9.356089] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.356107] ata2.01: SATA link down (SStatus 0 SControl 0)
[   19.356020] ata2.00: qc timeout (cmd 0xa1)
[   19.356026] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   19.356031] ata2.00: limiting SATA link speed to 1.5 Gbps
[   20.152089] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   20.152107] ata2.01: SATA link down (SStatus 0 SControl 0)
[   50.152021] ata2.00: qc timeout (cmd 0xa1)
[   50.152027] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   50.948088] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   50.948107] ata2.01: SATA link down (SStatus 0 SControl 0)
[   50.948239] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVT-7 11.0 PQ: 0 ANSI: 5
[   50.948337] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[   50.948353] sd 0:0:0:0: [sda] Write Protect is off
[   50.948355] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   50.948380] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.948446] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[   50.948459] sd 0:0:0:0: [sda] Write Protect is off
[   50.948461] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   50.948485] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.948488]  sda: sda1 sda2 sda3
[   51.304184] sd 0:0:0:0: [sda] Attached SCSI disk
[   51.304231] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   51.304918] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   51.304946] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   51.304970] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[   51.304974] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   51.305038] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   51.308963] ehci_hcd 0000:00:1a.7: debug port 1
[   51.308971] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[   51.308987] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[   51.324010] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[   51.324084] usb usb1: configuration #1 chosen from 1 choice
[   51.324110] hub 1-0:1.0: USB hub found
[   51.324117] hub 1-0:1.0: 4 ports detected
[   51.324227] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   51.324239] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   51.324243] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   51.324286] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   51.328193] ehci_hcd 0000:00:1d.7: debug port 1
[   51.328201] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   51.328214] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[   51.344010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[   51.344061] usb usb2: configuration #1 chosen from 1 choice
[   51.344087] hub 2-0:1.0: USB hub found
[   51.344093] hub 2-0:1.0: 6 ports detected
[   51.344187] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   51.344204] uhci_hcd: USB Universal Host Controller Interface driver
[   51.344236] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   51.344245] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[   51.344248] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   51.344292] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   51.344322] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
[   51.344395] usb usb3: configuration #1 chosen from 1 choice
[   51.344418] hub 3-0:1.0: USB hub found
[   51.344425] hub 3-0:1.0: 2 ports detected
[   51.344510] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   51.344517] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[   51.344520] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   51.344559] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   51.344595] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
[   51.344666] usb usb4: configuration #1 chosen from 1 choice
[   51.344691] hub 4-0:1.0: USB hub found
[   51.344697] hub 4-0:1.0: 2 ports detected
[   51.344779] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   51.344786] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   51.344789] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   51.344830] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   51.344858] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
[   51.344930] usb usb5: configuration #1 chosen from 1 choice
[   51.344953] hub 5-0:1.0: USB hub found
[   51.344959] hub 5-0:1.0: 2 ports detected
[   51.345038] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   51.345045] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   51.345049] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   51.345090] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   51.345118] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
[   51.345190] usb usb6: configuration #1 chosen from 1 choice
[   51.345213] hub 6-0:1.0: USB hub found
[   51.345219] hub 6-0:1.0: 2 ports detected
[   51.345310] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   51.345316] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   51.345320] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   51.345360] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   51.345388] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[   51.345460] usb usb7: configuration #1 chosen from 1 choice
[   51.345486] hub 7-0:1.0: USB hub found
[   51.345492] hub 7-0:1.0: 2 ports detected
[   51.345633] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   51.352383] serio: i8042 KBD port at 0x60,0x64 irq 1
[   51.352389] serio: i8042 AUX port at 0x60,0x64 irq 12
[   51.356036] mice: PS/2 mouse device common for all mice
[   51.372069] rtc_cmos 00:03: RTC can wake from S4
[   51.372102] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[   51.372137] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[   51.372200] device-mapper: uevent: version 1.0.3
[   51.372292] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   51.372364] device-mapper: multipath: version 1.0.5 loaded
[   51.372366] device-mapper: multipath round-robin: version 1.0.0 loaded
[   51.372441] EISA: Probing bus 0 at eisa.0
[   51.372449] Cannot allocate resource for EISA slot 1
[   51.372451] Cannot allocate resource for EISA slot 2
[   51.372479] EISA: Detected 0 cards.
[   51.372588] cpuidle: using governor ladder
[   51.372709] cpuidle: using governor menu
[   51.373206] TCP cubic registered
[   51.373280] Marking TSC unstable due to TSC halts in idle
[   51.373307] NET: Registered protocol family 10
[   51.373718] lo: Disabled Privacy Extensions
[   51.374039] NET: Registered protocol family 17
[   51.374056] Bluetooth: L2CAP ver 2.11
[   51.374058] Bluetooth: L2CAP socket layer initialized
[   51.374061] Bluetooth: SCO (Voice Link) ver 0.6
[   51.374062] Bluetooth: SCO socket layer initialized
[   51.374123] Bluetooth: RFCOMM socket layer initialized
[   51.374131] Bluetooth: RFCOMM TTY layer initialized
[   51.374133] Bluetooth: RFCOMM ver 1.10
[   51.374797] Using IPI No-Shortcut mode
[   51.374875] registered taskstats version 1
[   51.375002]   Magic number: 5:152:636
[   51.375031] power_supply AC: hash matches
[   51.375034] pci_express 0000:00:1c.1:pcie02: hash matches
[   51.375106] rtc_cmos 00:03: setting system clock to 2009-08-01 14:38:44 UTC (1249137524)
[   51.375109] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   51.375111] EDD information not available.
[   51.375303] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[   51.375415] Freeing unused kernel memory: 532k freed
[   51.375568] Write protecting the kernel text: 4116k
[   51.375626] Write protecting the kernel read-only data: 1524k
[   51.636912] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   51.636954] r8169 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   51.637080] r8169 0000:09:00.0: setting latency timer to 64
[   51.637457] r8169 0000:09:00.0: irq 2300 for MSI/MSI-X
[   51.638233] eth0: RTL8102e at 0xf7c58000, 00:21:70:8e:ad:42, XID 24a00000 IRQ 2300
[   51.748837] ohci1394 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   51.801626] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f69ff800-f69fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   52.008082] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   52.197362] usb 3-1: configuration #1 chosen from 1 choice
[   52.500064] Clocksource tsc unstable (delta = -450544953 ns)
[   53.072544] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc000353c99e1]
[   57.604269] kjournald starting.  Commit interval 5 seconds
[   57.604281] EXT3-fs: mounted filesystem with ordered data mode.
[  181.212754] udev: starting version 141
[  193.609965] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:029a]
[  193.737406] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 16
[  193.737411] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[  193.737415] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[  193.737423] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[  193.737426] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[  193.737627] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xf6900000 - 0xf69fffff
[  193.737629] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xc4000000 - 0xc7ffffff
[  194.109293] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[  195.412251] Linux agpgart interface v0.103
[  196.708691] iTCO_vendor_support: vendor-support=0
[  196.809243] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[  196.809417] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[  196.809519] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  198.909637] Bluetooth: Generic Bluetooth USB driver ver 0.3
[  198.909771] usbcore: registered new interface driver btusb
[  199.800181] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[  199.809364] sdhci: Secure Digital Host Controller Interface driver
[  199.809367] sdhci: Copyright(c) Pierre Ossman
[  199.909343] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 21)
[  199.909365] sdhci-pci 0000:03:01.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[  199.912542] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
[  199.928859] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/input/input5
[  199.957178] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[  199.957269] ACPI Warning (nspredef-0357): \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) [20080926]
[  199.957384] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/input/input6
[  199.961158] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[  199.969697] ricoh-mmc: Ricoh MMC Controller disabling driver
[  199.969701] ricoh-mmc: Copyright(c) Philip Langdale
[  199.969735] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.3 [1180:0843] (rev 11)
[  199.969755] ricoh-mmc: Controller is now disabled.
[  200.047307] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[  200.047658] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[  200.050683] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[  200.085109] cfg80211: Using static regulatory domain info
[  200.085112] cfg80211: Regulatory domain: US
[  200.085114] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  200.085116] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[  200.085119] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  200.085121] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  200.085123] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  200.085125] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  200.085128] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[  200.085170] cfg80211: Calling CRDA for country: US
[  200.091687] ip_tables: (C) 2000-2006 Netfilter Core Team
[  200.155788] cfg80211: Regulatory domain changed to country: US
[  200.155793] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  200.155795] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  200.155798] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  200.155800] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  200.155802] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  200.155805] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  200.210064] ath5k 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  200.210079] ath5k 0000:0c:00.0: setting latency timer to 64
[  200.210155] ath5k 0000:0c:00.0: registered as 'phy0'
[  200.280617] phy0: Selected rate control algorithm 'minstrel'
[  200.411436] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[  200.431352] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[  200.439869] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[  200.490443] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[  200.492688] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[  200.493628] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[  200.494367] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[  200.495364] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[  200.513709] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[  200.513930] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[  200.513933] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[  200.513935] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[  200.767459] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  200.767587] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  201.010233] lp: driver loaded but no devices found
[  201.012247] ath_hal: module license 'Proprietary' taints kernel.
[  201.013535] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  201.024726] wlan: 0.9.4
[  201.030500] ath_pci: 0.9.4
[  201.521145] EXT3 FS on sda1, internal journal
[  202.876223] kjournald starting.  Commit interval 5 seconds
[  202.876566] EXT3 FS on sda3, internal journal
[  202.876571] EXT3-fs: mounted filesystem with ordered data mode.
[  202.908781] kjournald starting.  Commit interval 5 seconds
[  202.909106] EXT3 FS on sda2, internal journal
[  202.909110] EXT3-fs: mounted filesystem with ordered data mode.
[  203.167862] type=1505 audit(1249137676.288:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2147
[  203.214246] type=1505 audit(1249137676.336:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2151
[  203.214380] type=1505 audit(1249137676.336:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2151
[  203.214423] type=1505 audit(1249137676.336:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2151
[  203.214463] type=1505 audit(1249137676.336:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2151
[  203.343307] type=1505 audit(1249137676.464:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2156
[  203.343519] type=1505 audit(1249137676.464:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2156
[  203.371532] type=1505 audit(1249137676.492:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2160
[  206.172948] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  206.172951] Bluetooth: BNEP filters: protocol multicast
[  206.213394] Bridge firewalling registered
[  206.956987] ppdev: user-space parallel port driver
[  207.623245] [drm] Initialized drm 1.1.0 20060810
[  207.634493] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  207.634499] pci 0000:00:02.0: setting latency timer to 64
[  207.634622] pci 0000:00:02.0: irq 2299 for MSI/MSI-X
[  207.634713] [drm] Initialized i915 1.6.0 20080730 on minor 0
[  208.965381] [drm:i915_setparam] *ERROR* unknown parameter 4
[  209.810211] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  210.876226] r8169: eth0: link down
[  210.876441] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  210.905338] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  238.641197] wlan0: authenticate with AP f62066b8
[  238.642749] wlan0: authenticated
[  238.642752] wlan0: associate with AP f62066b8
[  238.644964] wlan0: RX AssocResp from f5ed204a (capab=0x411 status=0 aid=1)
[  238.644966] wlan0: associated
[  238.645773] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  249.432101] wlan0: no IPv6 routers present
[/HTML]

Until now it started up in less than a minute. 
Any ideas what is wrong?
thank you

---

### Post by llamabr on 2009-08-01
Did you change anything, or recently do an update?

4 minutes is not impossibly long, particularly if it eventually loads fine.

---

### Post by freak42 on 2009-08-01
there are three positions where it waits quite a while..

here:
[    9.356089] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.356107] ata2.01: SATA link down (SStatus 0 SControl 0)
[   19.356020] ata2.00: qc timeout (cmd 0xa1)

and here
[   20.152089] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   20.152107] ata2.01: SATA link down (SStatus 0 SControl 0)
[   50.152021] ata2.00: qc timeout (cmd 0xa1)


and the longest here:
[   57.604281] EXT3-fs: mounted filesystem with ordered data mode.
[  181.212754] udev: starting version 141

for udev waiting long you might wanna look at this thread, if anything in there helps you, or search around the forum.
[https://bugzilla.redhat.com/show_bug.cgi?id=433933](https://bugzilla.redhat.com/show_bug.cgi?id=433933)

I don't know what happens to your sata link(s)?

hth
freak42

---

### Post by duruttye on 2009-08-02
Well, after a few slow starts everything went back to normal after the latest update/upgrade.

I have no idea what was the problem.
Anyway, thank you for your replies!

---

