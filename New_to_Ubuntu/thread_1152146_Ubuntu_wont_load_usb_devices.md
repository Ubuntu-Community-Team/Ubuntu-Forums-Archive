---
title: "Ubuntu wont load usb devices"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by mr.big_gun on 2009-05-07
i have tried flash drives, ipods, and camera and each time i plug in anything to usb it shows up as "Usb Device"! thats it! no IPOD, no 8 gb memory... nothing. i cant get anything to work in usb. 

however i am running dual boot with xp and my usb ports work fine there and they also work fine when i use them in my ubuntu Virtual box running xp.  what is going on? it just started doin this

please help me

---

### Post by alwayshere on 2009-05-07
sounds very weird easy thing to try first would be a reinstall of ubuntu

---

### Post by mr.big_gun on 2009-05-07
you see thats exactly what i dont want to do because i just did that and everything it already put back on

---

### Post by y_garti on 2009-05-07
how about try it on the live cd?

---

### Post by Dex73 on 2009-05-07
If you didn't remove them using the safely remove option when in Windows Ubuntu will read them as connected to another system and not connect. You can go back and remove them properly or enter the correct sudo command to fix it. If this is your real problem.

---

### Post by kay-man on 2009-05-07
Can you plug something into a USB port and then run

dmesg

on a terminal and post the output?

Also

sudo lsusb

and 

sudo lshw

might be useful.

---

### Post by mr.big_gun on 2009-05-07
Okay here it is, im not really sure which part to post so ill just do the who thing lol

dmesg, i got:

[    0.455920] pci 0000:03:07.0: PME# supported from D3hot D3cold
[    0.455924] pci 0000:03:07.0: PME# disabled
[    0.455947] pci 0000:00:10.0: transparent bridge
[    0.455950] PCI: bridge 0000:00:10.0 io port: [e000, efff]
[    0.455953] PCI: bridge 0000:00:10.0 32bit mmio: [feb00000, febfffff]
[    0.455968] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.456365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.456489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[    0.456636] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.469846] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *5
[    0.470116] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *5
[    0.470383] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.470649] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.470916] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.471183] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.471450] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *10
[    0.471723] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.471991] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.472265] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *5
[    0.472532] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.472799] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *5
[    0.473066] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.473334] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.473607] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
[    0.473874] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *5
[    0.474145] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[    0.474417] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[    0.474733] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.474907] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - A4, should be A0 [20080609]
[    0.474914] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.474946] pnp: PnP ACPI init
[    0.474953] ACPI: bus type pnp registered
[    0.481068] pnp: PnP ACPI: found 14 devices
[    0.481070] ACPI: ACPI bus type pnp unregistered
[    0.481431] PCI: Using ACPI for IRQ routing
[    0.492064] NET: Registered protocol family 8
[    0.492066] NET: Registered protocol family 20
[    0.492099] NetLabel: Initializing
[    0.492100] NetLabel:  domain hash size = 128
[    0.492102] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.492116] NetLabel:  unlabeled traffic allowed by default
[    0.493291] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.493293]    actual entries 65586
[    0.493546] AppArmor: AppArmor Filesystem Enabled
[    0.493574] ACPI: RTC can wake from S4
[    0.504060] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.504067] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.504070] system 00:07: ioport range 0x800-0x80f has been reserved
[    0.504073] system 00:07: ioport range 0x4000-0x407f has been reserved
[    0.504075] system 00:07: ioport range 0x4080-0x40ff has been reserved
[    0.504078] system 00:07: ioport range 0x4400-0x447f has been reserved
[    0.504080] system 00:07: ioport range 0x4480-0x44ff has been reserved
[    0.504083] system 00:07: ioport range 0x4800-0x487f has been reserved
[    0.504085] system 00:07: ioport range 0x4880-0x48ff has been reserved
[    0.504088] system 00:07: ioport range 0x2000-0x207f has been reserved
[    0.504091] system 00:07: ioport range 0x2080-0x20ff has been reserved
[    0.504093] system 00:07: iomem range 0xfea80000-0xfeabffff has been reserved
[    0.504096] system 00:07: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.504103] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.504106] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.504108] system 00:08: iomem range 0xff380000-0xff3fffff has been reserved
[    0.504116] system 00:0b: ioport range 0xa00-0xa0f has been reserved
[    0.504119] system 00:0b: ioport range 0xa10-0xa1f has been reserved
[    0.504124] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.504130] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.504132] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.504135] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.504138] system 00:0d: iomem range 0x100000-0x3fffffff could not be reserved
[    0.504141] system 00:0d: iomem range 0xff780000-0xffffffff could not be reserved
[    0.509138] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.509140] pci 0000:00:03.0:   IO window: disabled
[    0.509143] pci 0000:00:03.0:   MEM window: disabled
[    0.509145] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.509148] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.509150] pci 0000:00:04.0:   IO window: disabled
[    0.509152] pci 0000:00:04.0:   MEM window: disabled
[    0.509154] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.509157] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.509160] pci 0000:00:10.0:   IO window: 0xe000-0xefff
[    0.509163] pci 0000:00:10.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.509166] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.509177] pci 0000:00:03.0: setting latency timer to 64
[    0.509181] pci 0000:00:04.0: setting latency timer to 64
[    0.509185] pci 0000:00:10.0: setting latency timer to 64
[    0.509188] bus: 00 index 0 io port: [0, ffff]
[    0.509189] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.509191] bus: 01 index 0 mmio: [0, 0]
[    0.509193] bus: 01 index 1 mmio: [0, 0]
[    0.509194] bus: 01 index 2 mmio: [0, 0]
[    0.509196] bus: 01 index 3 mmio: [0, 0]
[    0.509197] bus: 02 index 0 mmio: [0, 0]
[    0.509199] bus: 02 index 1 mmio: [0, 0]
[    0.509200] bus: 02 index 2 mmio: [0, 0]
[    0.509202] bus: 02 index 3 mmio: [0, 0]
[    0.509204] bus: 03 index 0 io port: [e000, efff]
[    0.509205] bus: 03 index 1 mmio: [feb00000, febfffff]
[    0.509207] bus: 03 index 2 mmio: [0, 0]
[    0.509208] bus: 03 index 3 io port: [0, ffff]
[    0.509210] bus: 03 index 4 mmio: [0, ffffffffffffffff]
[    0.509223] NET: Registered protocol family 2
[    0.512050] Switched to high resolution mode on CPU 0
[    0.548091] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.548732] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.551509] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.552840] TCP: Hash tables configured (established 131072 bind 65536)
[    0.552843] TCP reno registered
[    0.564168] NET: Registered protocol family 1
[    0.564299] checking if image is initramfs... it is
[    1.299141] Freeing initrd memory: 10017k freed
[    1.311689] audit: initializing netlink socket (disabled)
[    1.311710] type=2000 audit(1241730856.308:1): initialized
[    1.317053] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.319681] VFS: Disk quotas dquot_6.5.1
[    1.319774] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.319879] msgmni has been set to 1748
[    1.320026] io scheduler noop registered
[    1.320028] io scheduler anticipatory registered
[    1.320030] io scheduler deadline registered
[    1.320148] io scheduler cfq registered (default)
[    1.320165] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.320203] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.320214] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.320223] pci 0000:00:05.0: Boot video device
[    1.320245] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.748052] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.748062] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.748073] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.748197] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.748221] pcieport-driver 0000:00:03.0: found MSI capability
[    1.748245] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.748287] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.748351] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.748372] pcieport-driver 0000:00:04.0: found MSI capability
[    1.748389] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.748427] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.782140] Linux agpgart interface v0.103
[    1.782146] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.784352] brd: module loaded
[    1.784431] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.784544] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.786949] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.786954] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.796111] mice: PS/2 mouse device common for all mice
[    1.796225] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.796254] rtc0: alarms up to one year, y3k
[    1.796290] cpuidle: using governor ladder
[    1.796292] cpuidle: using governor menu
[    1.796697] TCP cubic registered
[    1.796911] registered taskstats version 1
[    1.797081]   Magic number: 9:913:246
[    1.797123] tty ttyw2: hash matches
[    1.797287] rtc_cmos 00:02: setting system clock to 2009-05-07 21:14:17 UTC (1241730857)
[    1.797290] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.797291] EDD information not available.
[    1.797327] Freeing unused kernel memory: 540k freed
[    1.797897] Write protecting the kernel read-only data: 4348k
[    1.825179] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.860517] compcache: Compressed swap size set to: 223980 KB
[    1.861538] TLSF: pool: ffffc200001e7000, init_size=16384, max_size=0, grow_size=16384
[    2.024042] fuse init (API version 7.9)
[    2.198409] processor ACPI0007:00: registered as cooling_device0
[    2.812123] usbcore: registered new interface driver usbfs
[    2.812154] usbcore: registered new interface driver hub
[    2.820254] No dock devices found.
[    2.842427] usbcore: registered new device driver usb
[    2.854235] SCSI subsystem initialized
[    2.854764] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[    2.854777] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUB2] -> GSI 23 (level, low) -> IRQ 23
[    2.854791] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.854794] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.854849] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    2.854885] ehci_hcd 0000:00:0b.1: debug port 1
[    2.854889] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    2.854911] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xfeadfc00
[    2.856612] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.870342] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.870551] usb usb1: configuration #1 chosen from 1 choice
[    2.870601] hub 1-0:1.0: USB hub found
[    2.870612] hub 1-0:1.0: 8 ports detected
[    2.897436] libata version 3.00 loaded.
[    3.010186] Adding 223976k swap on /dev/ramzswap0.  Priority:100 extents:1 across:223976k
[    3.076951] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22
[    3.076966] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUB0] -> GSI 22 (level, low) -> IRQ 22
[    3.076985] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    3.076988] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    3.077015] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    3.077050] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xfeade000
[    3.134291] usb usb2: configuration #1 chosen from 1 choice
[    3.134320] hub 2-0:1.0: USB hub found
[    3.134333] hub 2-0:1.0: 8 ports detected
[    3.340485] pata_amd 0000:00:0d.0: version 0.3.10
[    3.340544] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.341235] scsi0 : pata_amd
[    3.341338] scsi1 : pata_amd
[    3.344111] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.344114] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.532959] ata1.01: ATA-7: WDC WD2000BB-22RDA0, 20.00K20, max UDMA/100
[    3.532963] ata1.01: 390721968 sectors, multi 16: LBA48 
[    3.532980] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6c5c0) ACPI=0x3f01f (900:20:0x14)
[    3.548580] ata1.01: configured for UDMA/100
[    3.588041] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    3.720317] ata2.00: ATAPI: HL-DT-ST DVD-RW GSA-H11N, JG03, max UDMA/66
[    3.720335] ata2.01: ATAPI:         16X52X32X52COMBO, 110G, max UDMA/33
[    3.720351] ata2: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc6c5c0) ACPI=0x1f01f (30:60:0x15)
[    3.720356] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc6c5c0) ACPI=0x701f (30:60:0x15)
[    3.736252] ata2.00: configured for UDMA/66
[    3.752251] ata2.01: configured for UDMA/33
[    3.752299] isa bounce pool size: 16 pages
[    3.752386] scsi 0:0:1:0: Direct-Access     ATA      WDC WD2000BB-22R 20.0 PQ: 0 ANSI: 5
[    3.756280] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GSA-H11N  JG03 PQ: 0 ANSI: 5
[    3.758101] scsi 1:0:1:0: CD-ROM                     16X52X32X52COMBO 110G PQ: 0 ANSI: 5
[    3.758185] sata_nv 0000:00:0e.0: version 3.5
[    3.758608] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21
[    3.758621] sata_nv 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 21 (level, low) -> IRQ 21
[    3.758624] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.758676] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.760157] scsi2 : sata_nv
[    3.761057] scsi3 : sata_nv
[    3.761220] ata3: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 21
[    3.761223] ata4: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 21
[    3.791262] usb 2-2: configuration #1 chosen from 1 choice
[    3.794503] hub 2-2:1.0: USB hub found
[    3.797094] hub 2-2:1.0: 4 ports detected
[    4.228026] usb 2-3: new full speed USB device using ohci_hcd and address 3
[    4.384071] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.384481] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    4.384493] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    4.384498] forcedeth 0000:00:14.0: setting latency timer to 64
[    4.384533] nv_probe: set workaround bit for reversed mac addr
[    4.431713] usb 2-3: configuration #1 chosen from 1 choice
[    4.736025] usb 2-7: new full speed USB device using ohci_hcd and address 4
[    4.905158] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:17:60:12:39
[    4.905162] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    4.906056] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
[    4.906068] b43-pci-bridge 0000:03:06.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[    4.952281] usb 2-7: configuration #1 chosen from 1 choice
[    4.964109] ssb: Sonics Silicon Backplane found on PCI device 0000:03:06.0
[    4.973273] usbcore: registered new interface driver libusual
[    4.982025] Initializing USB Mass Storage driver...
[    4.988184] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.988297] usbcore: registered new interface driver usb-storage
[    4.988301] USB Mass Storage support registered.
[    4.988305] usb-storage: device found at 4
[    4.988307] usb-storage: waiting for device to settle before scanning
[    4.991720] scsi 0:0:1:0: Attached scsi generic sg0 type 0
[    4.991759] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.991800] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    5.032138] Driver 'sd' needs updating - please use bus_type methods
[    5.032286] sd 0:0:1:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    5.032303] sd 0:0:1:0: [sda] Write Protect is off
[    5.032305] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    5.032327] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.032401] sd 0:0:1:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    5.032413] sd 0:0:1:0: [sda] Write Protect is off
[    5.032415] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    5.032435] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.032438]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.039184]  sda1 sda2 sda3 < sda5 >
[    5.063247] sd 0:0:1:0: [sda] Attached SCSI disk
[    5.068606] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[    5.068611] Uniform CD-ROM driver Revision: 3.20
[    5.068719] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.073760] sr1: scsi3-mmc drive: 4x/52x writer cd/rw xa/form2 cdda tray
[    5.073886] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    5.374536] PM: Starting manual resume from disk
[    5.374540] PM: Resume from partition 8:5
[    5.374541] PM: Checking hibernation image.
[    5.374708] PM: Resume from disk failed.
[    5.408182] kjournald starting.  Commit interval 5 seconds
[    5.408203] EXT3-fs: mounted filesystem with ordered data mode.
[    9.989156] usb-storage: device scan complete
[    9.996117] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   10.003109] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   10.010108] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   10.017106] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   10.028199] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   10.028381] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   10.039162] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   10.039208] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   10.050163] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   10.050210] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   10.061163] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   10.061211] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   11.297280] udevd version 124 started
[   11.902399] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.952251] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.004239] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.020039] ACPI: Power Button (FF) [PWRF]
[   12.020226] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.036022] ACPI: Power Button (CM) [PWRB]
[   12.748235] parport_pc 00:05: reported by Plug and Play ACPI
[   12.748289] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   13.053525]  : Error requesting region 5000 .. 503F for SMB1
[   13.053574] nForce2_smbus 0000:00:0a.1: Error probing SMB1.
[   13.053704] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x6000
[   13.384077] nvidia: module license 'NVIDIA' taints kernel.
[   13.851544] ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 18
[   13.851560] nvidia 0000:00:05.0: PCI INT A -> Link[LNEC] -> GSI 18 (level, low) -> IRQ 18
[   13.851566] nvidia 0000:00:05.0: setting latency timer to 64
[   13.851834] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.11  Wed Nov 26 10:53:43 PST 2008
[   13.908240] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   14.299070] b43-phy0: Broadcom 4318 WLAN found
[   14.349173] Linux video capture interface: v2.00
[   14.373501] phy0: Selected rate control algorithm 'pid'
[   14.484416] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   14.507649] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   14.507655] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   14.507677] HDA Intel 0000:00:10.1: setting latency timer to 64
[   14.546497] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   14.564433] gspca: main v2.2.0 registered
[   14.579444] gspca: probing 0733:0430
[   14.594798] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   15.041365] gspca: probe ok
[   15.041399] usbcore: registered new interface driver spca505
[   15.041415] spca505: registered
[   19.136719] lp0: using parport0 (interrupt-driven).
[   19.304231] Adding 2618552k swap on /dev/sda5.  Priority:-1 extents:1 across:2618552k
[   19.669457] EXT3 FS on sda1, internal journal
[   20.275843] type=1505 audit(1241730876.244:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4145
[   20.322238] type=1505 audit(1241730876.292:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4150
[   20.486345] type=1505 audit(1241730876.456:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4154
[   20.486611] type=1505 audit(1241730876.456:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4154
[   20.598244] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.236513] ACPI: WMI: Mapper loaded
[   21.480688] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (1 cpu cores) (version 2.20.00)
[   21.484545] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   22.503412] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.561609] ppdev: user-space parallel port driver
[   28.214633] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   28.214639] vboxdrv: Successfully done.
[   28.214641] vboxdrv: Found 1 processor cores.
[   28.216910] VBoxDrv: dbg - g_abExecMemory=ffffffffa0c41440
[   28.217498] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   28.217501] vboxdrv: Successfully loaded version 2.2.0 (interface 0x000a0009).
[   28.444963] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0de1040
[   36.713327] Bluetooth: Core ver 2.13
[   36.715489] NET: Registered protocol family 31
[   36.715494] Bluetooth: HCI device and connection manager initialized
[   36.715498] Bluetooth: HCI socket layer initialized
[   36.730877] Bluetooth: L2CAP ver 2.11
[   36.730882] Bluetooth: L2CAP socket layer initialized
[   36.741443] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.741449] Bluetooth: BNEP filters: protocol multicast
[   36.793639] Bridge firewalling registered
[   36.803436] Bluetooth: SCO (Voice Link) ver 0.6
[   36.803441] Bluetooth: SCO socket layer initialized
[   36.831560] Bluetooth: RFCOMM socket layer initialized
[   36.831846] Bluetooth: RFCOMM TTY layer initialized
[   36.831850] Bluetooth: RFCOMM ver 1.10
[   40.920883] eth0: no link during initialization.
[   40.942699] input: b43-phy0 as /devices/virtual/input/input6
[   41.032055] firmware: requesting b43/ucode5.fw
[   41.209157] firmware: requesting b43/pcm5.fw
[   41.272896] firmware: requesting b43/b0g0initvals5.fw
[   41.403136] firmware: requesting b43/b0g0bsinitvals5.fw
[   41.596044] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   41.719472] Registered led device: b43-phy0::tx
[   41.720279] Registered led device: b43-phy0::rx
[   41.720724] Registered led device: b43-phy0::radio
[   42.099949] NET: Registered protocol family 17
[  125.055828] UDF-fs: Partition marked readonly; forcing readonly mount
[  125.095520] UDF-fs INFO UDF: Mounting volume 'Data disc (05 May 09)', timestamp 2009/05/05 16:29 (1f10)
[  131.457108] wlan0: authenticate with AP 00:18:01:fb:d2:30
[  131.458490] wlan0: authenticated
[  131.458493] wlan0: associate with AP 00:18:01:fb:d2:30
[  131.461174] wlan0: RX AssocResp from 00:18:01:fb:d2:30 (capab=0x431 status=0 aid=2)
[  131.461180] wlan0: associated
[  135.775671] NET: Registered protocol family 10
[  135.778433] lo: Disabled Privacy Extensions
[  135.780077] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  146.540017] wlan0: no IPv6 routers present
[  196.719163] ppdev0: registered pardevice
[  196.768036] ppdev0: unregistered pardevice
[  197.520221] ppdev0: registered pardevice
[  197.568162] ppdev0: unregistered pardevice
[  197.606247] ppdev0: registered pardevice
[  197.652222] ppdev0: unregistered pardevice
[  254.656045] usb 1-8: new high speed USB device using ehci_hcd and address 5
[  254.818569] usb 1-8: configuration #1 chosen from 1 choice
[  254.844036] scsi5 : SCSI emulation for USB Mass Storage devices
[  254.844782] usb-storage: device found at 5
[  254.844785] usb-storage: waiting for device to settle before scanning
[  259.844312] usb-storage: device scan complete
[  259.846028] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[  260.099267] sd 5:0:0:0: [sdf] 15798272 512-byte hardware sectors (8089 MB)
[  260.100760] sd 5:0:0:0: [sdf] Write Protect is off
[  260.100764] sd 5:0:0:0: [sdf] Mode Sense: 23 00 00 00
[  260.100766] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[  260.105755] sd 5:0:0:0: [sdf] 15798272 512-byte hardware sectors (8089 MB)
[  260.106747] sd 5:0:0:0: [sdf] Write Protect is off
[  260.106750] sd 5:0:0:0: [sdf] Mode Sense: 23 00 00 00
[  260.106752] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[  260.107194]  sdf: sdf1
[  260.107981] sd 5:0:0:0: [sdf] Attached SCSI removable disk
[  260.108350] sd 5:0:0:0: Attached scsi generic sg7 type 0
[  267.960990] usb 1-8: USB disconnect, address 5
[  282.993939] usb 2-2.4: new full speed USB device using ohci_hcd and address 5
[  283.096880] usb 2-2.4: not running at top speed; connect to a high speed hub
[  283.126058] usb 2-2.4: configuration #1 chosen from 1 choice
[  283.160046] scsi6 : SCSI emulation for USB Mass Storage devices
[  283.169853] usb-storage: device found at 5
[  283.169858] usb-storage: waiting for device to settle before scanning
[  287.111875] usb 2-2.1: new full speed USB device using ohci_hcd and address 6
[  287.208828] usb 2-2.1: not running at top speed; connect to a high speed hub
[  287.232068] usb 2-2.1: configuration #1 chosen from 1 choice
[  287.272027] scsi7 : SCSI emulation for USB Mass Storage devices
[  287.277339] usb-storage: device found at 6
[  287.277347] usb-storage: waiting for device to settle before scanning
[  288.169408] usb-storage: device scan complete
[  288.176363] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[  288.438227] sd 6:0:0:0: [sdf] 15798272 512-byte hardware sectors (8089 MB)
[  288.445217] sd 6:0:0:0: [sdf] Write Protect is off
[  288.445221] sd 6:0:0:0: [sdf] Mode Sense: 23 00 00 00
[  288.445223] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[  288.471212] sd 6:0:0:0: [sdf] 15798272 512-byte hardware sectors (8089 MB)
[  288.478201] sd 6:0:0:0: [sdf] Write Protect is off
[  288.478204] sd 6:0:0:0: [sdf] Mode Sense: 23 00 00 00
[  288.478207] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[  288.479522]  sdf: sdf1
[  288.489461] sd 6:0:0:0: [sdf] Attached SCSI removable disk
[  288.489830] sd 6:0:0:0: Attached scsi generic sg7 type 0
[  292.277346] usb-storage: device scan complete
[  292.284311] scsi 7:0:0:0: Direct-Access     USB 2.0  SD MMC Reader         PQ: 0 ANSI: 0 CCS
[  292.330335] sd 7:0:0:0: [sdg] 7744512 512-byte hardware sectors (3965 MB)
[  292.342135] sd 7:0:0:0: [sdg] Write Protect is off
[  292.342142] sd 7:0:0:0: [sdg] Mode Sense: 03 00 00 00
[  292.342144] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[  292.369255] sd 7:0:0:0: [sdg] 7744512 512-byte hardware sectors (3965 MB)
[  292.377080] sd 7:0:0:0: [sdg] Write Protect is off
[  292.377087] sd 7:0:0:0: [sdg] Mode Sense: 03 00 00 00
[  292.377089] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[  292.378516]  sdg: sdg1
[  292.388683] sd 7:0:0:0: [sdg] Attached SCSI removable disk
[  292.389330] sd 7:0:0:0: Attached scsi generic sg8 type 0
[  302.749064] usb 2-2.3: new full speed USB device using ohci_hcd and address 7
[  302.849013] usb 2-2.3: not running at top speed; connect to a high speed hub
[  302.884731] usb 2-2.3: configuration #1 chosen from 2 choices
[  302.905495] scsi8 : SCSI emulation for USB Mass Storage devices
[  302.906970] usb-storage: device found at 7
[  302.906973] usb-storage: waiting for device to settle before scanning
[  307.905536] usb-storage: device scan complete
[  307.912505] scsi 8:0:0:0: Direct-Access     Apple    iPod             2.70 PQ: 0 ANSI: 2
[  307.953557] sd 8:0:0:0: [sdh] 991232 2048-byte hardware sectors (2030 MB)
[  307.960535] sd 8:0:0:0: [sdh] Write Protect is off
[  307.960543] sd 8:0:0:0: [sdh] Mode Sense: 64 00 00 08
[  307.960546] sd 8:0:0:0: [sdh] Assuming drive cache: write through
[  307.982470] sd 8:0:0:0: [sdh] 991232 2048-byte hardware sectors (2030 MB)
[  307.989483] sd 8:0:0:0: [sdh] Write Protect is off
[  307.989491] sd 8:0:0:0: [sdh] Mode Sense: 64 00 00 08
[  307.989493] sd 8:0:0:0: [sdh] Assuming drive cache: write through
[  307.990061]  sdh:
[  308.003547] sd 8:0:0:0: [sdh] Attached SCSI removable disk
[  308.003958] sd 8:0:0:0: Attached scsi generic sg9 type 0

























and for sudo lsusb:

Bus 002 Device 007: ID 05ac:1301 Apple, Inc. iPod Shuffle 2.Gen
Bus 002 Device 006: ID 14cd:8123 Super Top 
Bus 002 Device 005: ID 0951:1607 Kingston Technology Data Traveler 2.0
Bus 002 Device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 003: ID 0733:0430 ViewQuest Technologies, Inc. Intel Pro Share WebCam
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub







and for sudo lshw:

     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: C51G [GeForce 6100]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.27-11-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub slots=8 speed=12.0MB/s
           *-usb:0
                description: USB hub
                product: TUSB2046 Hub
                vendor: Texas Instruments, Inc.
                physical id: 2
                bus info: usb@2:2
                version: 1.25
                capabilities: usb-1.10
                configuration: driver=hub slots=4 speed=12.0MB/s
              *-usb:0
                   description: Mass storage device
                   product: USB 2.0  SD MMC READER
                   vendor: SDMMC MA8123
                   physical id: 1
                   bus info: usb@2:2.1
                   logical name: scsi7
                   version: 2.01
                   serial: 812320080329
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@7:0.0.0
                      logical name: /dev/sdg
                      size: 3781MiB (3965MB)
                      capabilities: partitioned partitioned:dos
                    *-volume
                         description: Windows FAT volume
                         physical id: 1
                         bus info: scsi@7:0.0.0,1
                         logical name: /dev/sdg1
                         version: FAT32
                         serial: 3436-3437
                         size: 3770MiB
                         capacity: 3777MiB
                         capabilities: primary fat initialized
                         configuration: FATs=2 filesystem=fat
              *-usb:1
                   description: Mass storage device
                   product: iPod
                   vendor: Apple
                   physical id: 3
                   bus info: usb@2:2.3
                   logical name: scsi8
                   version: 1.00
                   serial: 000A27001C25AD00
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: iPod
                      vendor: Apple
                      physical id: 0.0.0
                      bus info: scsi@8:0.0.0
                      logical name: /dev/sdh
                      version: 2.70
                      serial: 4H835DRV1ZH
                      size: 1936MiB (2030MB)
                      capabilities: removable
                      configuration: ansiversion=2
                    *-medium
                         description: Windows FAT volume
                         vendor: MSDOS5.0
                         physical id: 0
                         logical name: /dev/sdh
                         version: FAT32
                         serial: e4ff-11dc
                         size: 1935MiB
                         capacity: 1936MiB
                         capabilities: fat initialized
                         configuration: FATs=2 filesystem=fat signature=6f20736b
              *-usb:2
                   description: Mass storage device
                   product: DataTraveler 2.0
                   vendor: Kingston
                   physical id: 4
                   bus info: usb@2:2.4
                   logical name: scsi6
                   version: 1.10
                   serial: 000AEBFFB51C5B8C100A00FF
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sdf
                      size: 7714MiB (8088MB)
                      capabilities: partitioned partitioned:dos
                    *-volume
                         description: Windows FAT volume
                         vendor: MSWIN4.1
                         physical id: 1
                         bus info: scsi@6:0.0.0,1
                         logical name: /dev/sdf1
                         version: FAT32
                         serial: 96b0-a63e
                         size: 7705MiB
                         capacity: 7710MiB
                         capabilities: primary bootable fat initialized
                         configuration: FATs=2 filesystem=fat label=KINGSTON
           *-usb:1
                description: Generic USB device
                product: Intel Pro Share WebCam
                vendor: ViewQuest Technologies, Inc.
                physical id: 3
                bus info: usb@2:3
                version: 0.90
                capabilities: usb-1.00
                configuration: driver=spca505 maxpower=500mA speed=12.0MB/s
           *-usb:2
                description: Mass storage device
                product: USB Reader
                physical id: 7
                bus info: usb@2:7
                logical name: scsi4
                version: 1.00
                serial: 2004888
                capabilities: usb-1.10 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
              *-disk:0
                   description: SCSI Disk
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/sdb
              *-disk:1
                   description: SCSI Disk
                   physical id: 0.0.1
                   bus info: scsi@4:0.0.1
                   logical name: /dev/sdc
              *-disk:2
                   description: SCSI Disk
                   physical id: 0.0.2
                   bus info: scsi@4:0.0.2
                   logical name: /dev/sdd
              *-disk:3
                   description: SCSI Disk
                   physical id: 0.0.3
                   bus info: scsi@4:0.0.3
                   logical name: /dev/sde
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.27-11-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub slots=8 speed=480.0MB/s
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi0
          logical name: scsi1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-disk
             description: ATA Disk
             product: WDC WD2000BB-22R
             vendor: Western Digital
             physical id: 0
             bus info: scsi@0:0.1.0
             logical name: /dev/sda
             version: 20.0
             serial: WD-WMANL1451554
             size: 186GiB (200GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=4b36bdea
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: 31f60343-31cf-432a-a238-fd304e88adae
                size: 144GiB
                capacity: 144GiB
                capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2009-05-05 21:39:42 filesystem=ext3 modified=2009-05-07 15:37:57 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-05-07 14:10:34 state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.1.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: d0153ec4-f7ea-7b4c-a01d-c912a60a9afe
                size: 39GiB
                capacity: 39GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2009-05-05 22:54:02 filesystem=ntfs state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.1.0,3
                logical name: /dev/sda3
                size: 2557MiB
                capacity: 2557MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2557MiB
                   capabilities: nofs
        *-cdrom:0
             description: DVD writer
             product: DVD-RW GSA-H11N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /media/cdrom0
             version: JG03
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/cdrom0
                configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-cdrom:1
             description: DVD reader
             product: 16X52X32X52COMBO
             physical id: 1
             bus info: scsi@1:0.1.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: 110G
             serial: )        16X52X32X52COMBO110G040617AOpen0701611
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
        *-network
             description: Network controller
             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 6
             bus info: pci@0000:03:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=b43-pci-bridge latency=64 module=ssb
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: 7
             bus info: pci@0000:03:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=64
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a1
          serial: 00:16:17:60:12:39
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:29:8a:15
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.4 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:2 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 26:ea:28:1a:8d:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes






and here is a snapshot of how it says Usb Drive and wont let me open anything:


[IMG]http://tinypic.com/r/25gxfsi/5[/IMG]

---

### Post by mr.big_gun on 2009-05-07
[IMG]http://i40.tinypic.com/25gxfsi.png[/IMG]

---

### Post by kay-man on 2009-05-07
Well, the good news is that your devices seem to be connected properly. I can see a webcam, an ipod and an 8GB kingston traveler, and no obvious issues.

Your USB stick should be /dev/sdf1.

Try to mount it by hand, i.e. create a new directory and use that as the  mount point for the device:

mount -t vfat /dev/sdf1 <your new directory>

or maybe sudo that if it doesn't work like this. Then see if you can access the data on the stick through your new directory, and let us know the result.

---

### Post by mariliasaca on 2009-05-08
I have 2 problems with usb devices in Ubuntu 9.04, on a Dell notebook. I used 8.10 for a long time, perfectly working. When upgrading to 9.04 last week the problems began:

1) the usb mouse (a very much generic one) works well if it is plugged at the boot. If removed and replugged... nothing. If the gnome is re-inicialized (ctrl-alt-back) it comes back.
2) pendrives: the same. Except that only a reboot brings it back. The label of the disks stay in the "Places", the last mounted directories are displayed in the browser, if I "unmount" it I recive a msg saying that it is not mounted, no icone on the desktop. And I really don't know if I can take it out, as I don't know if the pen is erally unmounted. 

I am seriously thinking in going back to 8.10, as I am not competent enough to do much by terminal.

---

### Post by kay-man on 2009-05-08
ok, to start off with that last remark, everybody can use the terminal, or in any case learn to do so. All it takes is at least one finger, but I get better results personally using 2 :).

I don't know too much of the handling of usb devices in gnome, as I use kubuntu myself. I do however get very good results using autofs, which will automatically mount and unmount devices, meaning you don't need to worry about that yourself.

I set this up using [this tutorial]("http://www.greenfly.org/tips/autofs.html") at least a year ago, and my usb drives work without any issues. I've upgraded at least twice since then, and I've never even had to look at this stuff again. That's how good it works.

---

### Post by mariliasaca on 2009-05-09
Yes, I can learn!!! Actually I type commands in whatever I do, but I feel really unsure on mixing with those incantations. I don't know the basics, and honestly, I don't have enough time to learn all I should. 

The good news is that I discovered the pen drive problem. I was between the chair and the keyboard: as it didn't appear on the workspace I though it was not accessible. But reading through the greenfly page I could understand what was my problem. I just have to try to access it, and it is there!  

However, the mouse don't come back when replugged. And I need to do that eventually, as I only have 2 usb. Help???

---

### Post by mr.big_gun on 2009-05-10
hey thanks ppl i just reformatted and said ta hell with it
thanks for the help tho

---

### Post by hanzj on 2009-08-08
mr. big gun,
so you reformatted. but what did you do next? Did you just re-install ubuntu 9.04? did that help?

before your reformatting, did you get to ubuntu 9.04 via the upgrade path?

---

### Post by mr.big_gun on 2009-09-16
when i reformatted i did it with 8.10   i haven't tried 9.04 yet  im fine with my comp like it is now
i have messed with linux for a while and i think that it was just one of those installs that you get every now and then and it misses a tiny piece of data but who knows
i used the same copy every time i reformatted

---

