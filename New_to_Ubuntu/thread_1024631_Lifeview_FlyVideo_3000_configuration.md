---
title: "Lifeview FlyVideo 3000 configuration"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by TheDarkMaster on 2008-12-29
Hi all,
I just newly got a FlyVideo 3000 TV/FM-tuner card from a friend. I forgot to ask the box so I got no more info about it the my computer itself can specify. But now comes the problem: the card apears to be working correctly because Gnomeradio works so at least the FM-tuner does it's work. But now I got an very old Sega console and I want to play the games(as they are still fun) but my TV can't get it. So I tried to connect the antenna(yeah it's really old) to my TV-tuner. And it could be because I'm new but I can't get anything working(except for the radio). MythTV won't work because it can't initialize LiveTV. And I don't get tvtime and mplayer(so I can't switch channels). Also I don't have a remote with it and tvtime thinks I have it because there's no interface, at least I couldn't find it.
This are the outputs of dmesg, lspci and MythTV when it crashes:

dmesg:
```
[    0.418223] pci 0000:02:05.0: supports D2
[    0.418225] pci 0000:02:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.418230] pci 0000:02:05.0: PME# disabled
[    0.418265] PCI: 0000:02:07.0 reg 10 32bit mmio: [e4006000, e40067ff]
[    0.418274] PCI: 0000:02:07.0 reg 14 32bit mmio: [e4000000, e4003fff]
[    0.418320] pci 0000:02:07.0: supports D1
[    0.418322] pci 0000:02:07.0: supports D2
[    0.418324] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot
[    0.418329] pci 0000:02:07.0: PME# disabled
[    0.418365] pci 0000:00:1e.0: transparent bridge
[    0.418370] PCI: bridge 0000:00:1e.0 io port: [a000, afff]
[    0.418375] PCI: bridge 0000:00:1e.0 32bit mmio: [e4000000, e40fffff]
[    0.418391] bus 00 -> node 0
[    0.418400] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.418703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.428095] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.428250] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.428403] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.428556] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.428708] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.428861] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.429013] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.429167] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.429408] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.429460] pnp: PnP ACPI init
[    0.429471] ACPI: bus type pnp registered
[    0.434661] pnp: PnP ACPI: found 16 devices
[    0.434665] ACPI: ACPI bus type pnp unregistered
[    0.434670] PnPBIOS: Disabled by ACPI PNP
[    0.435187] PCI: Using ACPI for IRQ routing
[    0.435340] NET: Registered protocol family 8
[    0.435340] NET: Registered protocol family 20
[    0.435340] NetLabel: Initializing
[    0.435340] NetLabel:  domain hash size = 128
[    0.435340] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.435340] NetLabel:  unlabeled traffic allowed by default
[    0.435340] hpet clockevent registered
[    0.435340] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.435340] hpet0: 3 64-bit timers, 14318180 Hz
[    0.436588] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.436591]    actual entries 65620
[    0.436746] AppArmor: AppArmor Filesystem Enabled
[    0.436770] ACPI: RTC can wake from S4
[    0.436782] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.436782] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.436782] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.436782] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.436782] system 00:0c: ioport range 0x400-0x4bf could not be reserved
[    0.436782] system 00:0d: iomem range 0xd0000000-0xdfffffff could not be reserved
[    0.436782] system 00:0e: iomem range 0xd5000-0xd7fff has been reserved
[    0.436782] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[    0.436782] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[    0.436782] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[    0.436782] system 00:0e: iomem range 0x9fff0000-0x9fffffff could not be reserved
[    0.436782] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.436782] system 00:0e: iomem range 0x100000-0x9ffeffff could not be reserved
[    0.436782] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.436782] system 00:0e: iomem range 0xfed13000-0xfed1dfff could not be reserved
[    0.436782] system 00:0e: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.436782] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.436782] system 00:0e: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.436782] system 00:0e: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.436782] system 00:0e: iomem range 0xe0000-0xeffff has been reserved
[    0.472778] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.472783] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.472788] pci 0000:00:01.0:   MEM window: 0xe2000000-0xe3ffffff
[    0.472793] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000e1ffffff
[    0.472800] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.472804] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.472809] pci 0000:00:1e.0:   MEM window: 0xe4000000-0xe40fffff
[    0.472814] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.472832] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.472838] pci 0000:00:01.0: setting latency timer to 64
[    0.472848] pci 0000:00:1e.0: setting latency timer to 64
[    0.472854] bus: 00 index 0 io port: [0, ffff]
[    0.472857] bus: 00 index 1 mmio: [0, ffffffff]
[    0.472859] bus: 01 index 0 io port: [9000, 9fff]
[    0.472862] bus: 01 index 1 mmio: [e2000000, e3ffffff]
[    0.472864] bus: 01 index 2 mmio: [e0000000, e1ffffff]
[    0.472866] bus: 01 index 3 mmio: [0, 0]
[    0.472869] bus: 02 index 0 io port: [a000, afff]
[    0.472871] bus: 02 index 1 mmio: [e4000000, e40fffff]
[    0.472873] bus: 02 index 2 mmio: [0, 0]
[    0.472875] bus: 02 index 3 io port: [0, ffff]
[    0.472878] bus: 02 index 4 mmio: [0, ffffffff]
[    0.472890] NET: Registered protocol family 2
[    0.473072] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.473447] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.474054] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.474479] TCP: Hash tables configured (established 131072 bind 65536)
[    0.474483] TCP reno registered
[    0.474689] NET: Registered protocol family 1
[    0.474853] checking if image is initramfs... it is
[    0.936084] Switched to high resolution mode on CPU 0
[    1.165930] Freeing initrd memory: 8012k freed
[    1.166149] Simple Boot Flag value 0xe read from CMOS RAM was invalid
[    1.166153] Simple Boot Flag at 0x36 set to 0x1
[    1.166824] audit: initializing netlink socket (disabled)
[    1.166846] type=2000 audit(1230561163.164:1): initialized
[    1.172306] highmem bounce pool size: 64 pages
[    1.172315] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.175286] VFS: Disk quotas dquot_6.5.1
[    1.175405] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.175538] msgmni has been set to 1734
[    1.175701] io scheduler noop registered
[    1.175704] io scheduler anticipatory registered
[    1.175706] io scheduler deadline registered
[    1.175723] io scheduler cfq registered (default)
[    1.175821] pci 0000:01:00.0: Boot video device
[    1.175950] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.176017] pcieport-driver 0000:00:01.0: found MSI capability
[    1.176056] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.176120] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.176556] isapnp: Scanning for PnP cards...
[    1.528275] isapnp: No Plug & Play device found
[    1.579079] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.579237] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.579418] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.580239] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.580605] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.580880] serial 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.581343] 0000:02:01.0: ttyS2 at I/O 0xa008 (irq = 19) is a 16450
[    1.581633] 0000:02:01.0: ttyS3 at I/O 0xa010 (irq = 19) is a 8250
[    1.581733] Couldn't register serial port 0000:02:01.0: -28
[    1.583945] brd: module loaded
[    1.584389] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.584564] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.587501] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.587510] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.587939] mice: PS/2 mouse device common for all mice
[    1.588139] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.588165] rtc0: alarms up to one month, hpet irqs
[    1.588335] EISA: Probing bus 0 at eisa.0
[    1.588366] EISA: Detected 0 cards.
[    1.588370] cpuidle: using governor ladder
[    1.588372] cpuidle: using governor menu
[    1.589037] TCP cubic registered
[    1.589073] Using IPI No-Shortcut mode
[    1.589325] registered taskstats version 1
[    1.589443]   Magic number: 4:180:537
[    1.589448] bdi 1:15: hash matches
[    1.589579] rtc_cmos 00:03: setting system clock to 2008-12-29 14:32:44 UTC (1230561164)
[    1.589583] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.589585] EDD information not available.
[    1.589940] Freeing unused kernel memory: 424k freed
[    1.590001] Write protecting the kernel text: 2576k
[    1.590037] Write protecting the kernel read-only data: 936k
[    1.611771] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.846909] fuse init (API version 7.9)
[    2.105814] processor ACPI0007:00: registered as cooling_device0
[    2.105821] ACPI: Processor [CPU0] (supports 2 throttling states)
[    2.798429] usbcore: registered new interface driver usbfs
[    2.798463] usbcore: registered new interface driver hub
[    2.798522] usbcore: registered new device driver usb
[    2.807480] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.807496] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.807501] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.807558] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.811472] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.811488] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe4104000
[    2.829817] USB Universal Host Controller Interface driver v3.0
[    2.856041] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.856260] usb usb1: configuration #1 chosen from 1 choice
[    2.856300] hub 1-0:1.0: USB hub found
[    2.856313] hub 1-0:1.0: 8 ports detected
[    2.856535] No dock devices found.
[    2.901422] SCSI subsystem initialized
[    2.905016] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.959184] libata version 3.00 loaded.
[    3.064446] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.064459] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.064463] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.064495] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.064525] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000bc00
[    3.064643] usb usb2: configuration #1 chosen from 1 choice
[    3.064679] hub 2-0:1.0: USB hub found
[    3.064690] hub 2-0:1.0: 2 ports detected
[    3.272742] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.272755] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.272759] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.272795] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.272831] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b000
[    3.272971] usb usb3: configuration #1 chosen from 1 choice
[    3.273007] hub 3-0:1.0: USB hub found
[    3.273018] hub 3-0:1.0: 2 ports detected
[    3.288036] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    3.376344] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.376357] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.376362] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.376398] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.376435] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[    3.376558] usb usb4: configuration #1 chosen from 1 choice
[    3.376596] hub 4-0:1.0: USB hub found
[    3.376606] hub 4-0:1.0: 2 ports detected
[    3.421484] usb 1-6: configuration #1 chosen from 1 choice
[    3.421720] hub 1-6:1.0: USB hub found
[    3.422057] hub 1-6:1.0: 4 ports detected
[    3.584338] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.584350] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.584355] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.584388] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.584425] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
[    3.584545] usb usb5: configuration #1 chosen from 1 choice
[    3.584583] hub 5-0:1.0: USB hub found
[    3.584597] hub 5-0:1.0: 2 ports detected
[    3.636036] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    3.769133] usb 1-8: configuration #1 chosen from 1 choice
[    3.792400] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.792442] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    3.792460] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    3.792499] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.792504] 8139cp 0000:02:05.0: Try the "8139too" driver instead.
[    3.797542] ohci1394 0000:02:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.847305] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e4006000-e40067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.849832] 8139too Fast Ethernet driver 0.9.28
[    3.859142] 8139too 0000:02:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.860094] eth0: RealTek RTL8139 at 0xa400, 00:0f:ea:c4:df:56, IRQ 21
[    3.860097] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.860288] ata_piix 0000:00:1f.2: version 2.12
[    3.860300] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.860305] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.860353] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.861025] scsi0 : ata_piix
[    3.861151] scsi1 : ata_piix
[    3.862327] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    3.862331] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    3.900033] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    4.024351] ata1.00: ATA-6: ST380013AS, 3.00, max UDMA/133
[    4.024357] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.040373] ata1.00: configured for UDMA/133
[    4.124777] usb 2-1: configuration #1 chosen from 1 choice
[    4.128432] usbcore: registered new interface driver libusual
[    4.136880] Initializing USB Mass Storage driver...
[    4.144639] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.149157] usb-storage: device found at 4
[    4.149161] usb-storage: waiting for device to settle before scanning
[    4.151329] scsi3 : SCSI emulation for USB Mass Storage devices
[    4.151975] usbcore: registered new interface driver usb-storage
[    4.151981] USB Mass Storage support registered.
[    4.152141] usb-storage: device found at 2
[    4.152144] usb-storage: waiting for device to settle before scanning
[    4.236392] ata2.00: ATAPI: _NEC DVD_RW ND-3530A, 2.01, max UDMA/33
[    4.236419] ata2.01: ATAPI: TSSTcorpCD/DVDW SH-S162L, TS06, max UDMA/33
[    4.252324] ata2.00: configured for UDMA/33
[    4.292298] ata2.01: configured for UDMA/33
[    4.292438] scsi 0:0:0:0: Direct-Access     ATA      ST380013AS       3.00 PQ: 0 ANSI: 5
[    4.292672] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.294348] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-3530A  2.01 PQ: 0 ANSI: 5
[    4.294497] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.295611] scsi 1:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S162L TS06 PQ: 0 ANSI: 5
[    4.295754] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    4.341934] Driver 'sd' needs updating - please use bus_type methods
[    4.344578] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.344608] sd 0:0:0:0: [sda] Write Protect is off
[    4.344612] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.344659] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.344757] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.344783] sd 0:0:0:0: [sda] Write Protect is off
[    4.344787] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.344833] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.344838]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.360215]  sda1
[    4.360350] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.364842] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.364849] Uniform CD-ROM driver Revision: 3.20
[    4.364965] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.376305] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.376438] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    5.124945] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea0000c35e8a]
[    9.148124] usb-storage: device scan complete
[    9.153765] usb-storage: device scan complete
[    9.163382] scsi 2:0:0:0: Direct-Access     ST350083 0AS                   PQ: 0 ANSI: 2 CCS
[    9.172624] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    9.173356] sd 2:0:0:0: [sdb] Write Protect is off
[    9.173361] sd 2:0:0:0: [sdb] Mode Sense: 3c 00 00 00
[    9.173364] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.174107] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    9.174852] sd 2:0:0:0: [sdb] Write Protect is off
[    9.174856] sd 2:0:0:0: [sdb] Mode Sense: 3c 00 00 00
[    9.174858] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.174865]  sdb:<5>scsi 3:0:0:0: Direct-Access     GENERIC  USB Storage-SMC  500A PQ: 0 ANSI: 0 CCS
[    9.191765]  sdb1 sdb3 < sdb5<5>scsi 3:0:0:1: Direct-Access     GENERIC  USB Storage-CFC  500A PQ: 0 ANSI: 0 CCS
[    9.220858]  sdb6 >
[    9.221104] sd 2:0:0:0: [sdb] Attached SCSI disk
[    9.221268] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    9.237785] scsi 3:0:0:2: Direct-Access     GENERIC  USB Storage-SDC  500A PQ: 0 ANSI: 0 CCS
[    9.265779] scsi 3:0:0:3: Direct-Access     GENERIC  USB Storage-MSC  500A PQ: 0 ANSI: 0 CCS
[    9.278913] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[    9.279087] sd 3:0:0:0: Attached scsi generic sg4 type 0
[    9.283883] sd 3:0:0:1: [sdd] Attached SCSI removable disk
[    9.284136] sd 3:0:0:1: Attached scsi generic sg5 type 0
[    9.288879] sd 3:0:0:2: [sde] Attached SCSI removable disk
[    9.289029] sd 3:0:0:2: Attached scsi generic sg6 type 0
[    9.293899] sd 3:0:0:3: [sdf] Attached SCSI removable disk
[    9.294076] sd 3:0:0:3: Attached scsi generic sg7 type 0
[    9.553980] PM: Starting manual resume from disk
[    9.553985] PM: Resume from partition 8:22
[    9.553987] PM: Checking hibernation image.
[    9.554372] PM: Resume from disk failed.
[    9.631289] kjournald starting.  Commit interval 5 seconds
[    9.631304] EXT3-fs: mounted filesystem with ordered data mode.
[   15.466277] udevd version 124 started
[   16.163215] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.263261] Linux agpgart interface v0.103
[   16.349061] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.596440] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   16.612053] ACPI: Power Button (FF) [PWRF]
[   16.612202] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   16.628040] ACPI: Power Button (CM) [PWRB]
[   16.994936] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   17.374305] Linux video capture interface: v2.00
[   17.405428] [fglrx] Maximum main memory to use for locked dma buffers: 2394 MBytes.
[   17.405581] [fglrx]   vendor: 1002 device: 5b60 count: 1
[   17.406004] [fglrx] ioport: bar 1, base 0x9000, size: 0x100
[   17.406024] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.406031] pci 0000:01:00.0: setting latency timer to 64
[   17.406707] [fglrx] PAT is enabled successfully!
[   17.406746] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   17.682087] saa7130/34: v4l2 driver version 0.2.14 loaded
[   17.682746] saa7134 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   17.682755] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 20, latency: 32, mmio: 0xe4007000
[   17.682764] saa7134[0]: subsystem: 4e42:0138, board: LifeView FlyVIDEO3000 [card=2,insmod option]
[   17.682775] saa7134[0]: board init: gpio is 39000
[   17.682778] saa7134[0]: there are different flyvideo cards with different tuners
[   17.682780] saa7134[0]: out there, you might have to use the tuner=<nr> insmod
[   17.682781] saa7134[0]: option to override the default value.
[   17.682937] input: saa7134 IR (LifeView FlyVIDEO30 as /devices/pci0000:00/0000:00:1e.0/0000:02:00.0/input/input4
[   17.704034] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.704058] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.737641] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   17.738094] hda_codec: Cannot set up configuration from BIOS.  Using 3-stack mode...
[   17.992595] parport_pc 00:09: reported by Plug and Play ACPI
[   17.992674] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   18.041278] saa7134[0]: i2c eeprom 00: 42 4e 38 01 10 28 ff ff ff ff ff ff ff ff ff ff
[   18.041292] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041303] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041313] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041324] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041335] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041345] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041356] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041366] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041377] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041388] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041398] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041409] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041420] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041430] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041441] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.114470] tuner' 0-0061: chip found @ 0xc2 (saa7134[0])
[   18.320043] tuner-simple 0-0061: creating new instance
[   18.320049] tuner-simple 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   18.367405] saa7134[0]: registered device video0 [v4l2]
[   18.367474] saa7134[0]: registered device vbi0
[   18.367546] saa7134[0]: registered device radio0
[   18.389400] saa7134 ALSA driver for DMA sound loaded
[   18.389436] saa7134[0]/alsa: saa7134[0] at 0xe4007000 irq 20 registered as card -2
[   18.572502] iTCO_vendor_support: vendor-support=0
[   18.575835] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   18.576031] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0460)
[   18.576203] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.663892] intel_rng: FWH not detected
[   19.676669] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   19.932936] logips2pp: Detected unknown logitech mouse model 105
[   20.412930] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   24.363394] lp0: using parport0 (interrupt-driven).
[   24.584999] Adding 7590672k swap on /dev/sdb6.  Priority:-1 extents:1 across:7590672k
[  302.287837] EXT3 FS on sdb5, internal journal
[  303.304136] type=1505 audit(1230557866.077:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=6037
[  303.375086] type=1505 audit(1230557866.145:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=6042
[  303.570164] type=1505 audit(1230557866.341:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=6046
[  303.570393] type=1505 audit(1230557866.341:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=6046
[  303.625549] type=1505 audit(1230557866.397:6): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=6050
[  303.744212] ip_tables: (C) 2000-2006 Netfilter Core Team
[  304.273178] ACPI: WMI: Mapper loaded
[  305.404493] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  307.479782] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  307.479790] apm: overridden by ACPI.
[  308.425291] ppdev: user-space parallel port driver
[  312.061741] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  312.061752] vboxdrv: Successfully done.
[  312.061754] vboxdrv: Found 1 processor cores.
[  312.062843] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  312.062850] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[  312.278438] NET: Registered protocol family 10
[  312.280088] lo: Disabled Privacy Extensions
[  320.097828] Bluetooth: Core ver 2.13
[  320.100728] NET: Registered protocol family 31
[  320.100737] Bluetooth: HCI device and connection manager initialized
[  320.100741] Bluetooth: HCI socket layer initialized
[  320.153843] Bluetooth: L2CAP ver 2.11
[  320.153851] Bluetooth: L2CAP socket layer initialized
[  320.171181] Bluetooth: SCO (Voice Link) ver 0.6
[  320.171189] Bluetooth: SCO socket layer initialized
[  320.191342] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  320.191350] Bluetooth: BNEP filters: protocol multicast
[  320.230381] Bridge firewalling registered
[  320.231504] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  320.253904] Bluetooth: RFCOMM socket layer initialized
[  320.254214] Bluetooth: RFCOMM TTY layer initialized
[  320.254221] Bluetooth: RFCOMM ver 1.10
[  324.412515] eth0: link down
[  324.412970] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  326.637862] [fglrx] Reserved FB block: Shared offset:0, size:40000 
[  326.637879] [fglrx] Reserved FB block: Unshared offset:1fbb000, size:44000 
[  326.637882] [fglrx] Reserved FB block: Unshared offset:1fff000, size:1000 
[  417.449781] UDF-fs: Partition marked readonly; forcing readonly mount
[  417.480600] UDF-fs INFO UDF: Mounting volume 'Sims2_EP5_1', timestamp 2007/01/26 09:41 (103c)
[  495.064101] ppdev0: registered pardevice
[  495.112050] ppdev0: unregistered pardevice
[  495.341764] ppdev0: registered pardevice
[  495.388301] ppdev0: unregistered pardevice
[  496.222668] ppdev0: registered pardevice
[  496.272183] ppdev0: unregistered pardevice
[  510.166990] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  510.167490] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  510.240507] NET: Registered protocol family 17
[  515.694836] eth0: link down
[  520.280015] eth0: no IPv6 routers present
[  522.382778] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  531.665764] eth0: link down
[  533.969429] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  563.153576] firefox[8805]: segfault at b798821e ip b7cc8571 sp bf86c0d4 error 4 in libc-2.8.90.so[b7c9a000+158000]

```

lspci:
```
[CODE]rved
[    0.436782] system 00:0e: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.436782] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.436782] system 00:0e: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.436782] system 00:0e: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.436782] system 00:0e: iomem range 0xe0000-0xeffff has been reserved
[    0.472778] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.472783] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.472788] pci 0000:00:01.0:   MEM window: 0xe2000000-0xe3ffffff
[    0.472793] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000e1ffffff
[    0.472800] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.472804] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.472809] pci 0000:00:1e.0:   MEM window: 0xe4000000-0xe40fffff
[    0.472814] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.472832] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.472838] pci 0000:00:01.0: setting latency timer to 64
[    0.472848] pci 0000:00:1e.0: setting latency timer to 64
[    0.472854] bus: 00 index 0 io port: [0, ffff]
[    0.472857] bus: 00 index 1 mmio: [0, ffffffff]
[    0.472859] bus: 01 index 0 io port: [9000, 9fff]
[    0.472862] bus: 01 index 1 mmio: [e2000000, e3ffffff]
[    0.472864] bus: 01 index 2 mmio: [e0000000, e1ffffff]
[    0.472866] bus: 01 index 3 mmio: [0, 0]
[    0.472869] bus: 02 index 0 io port: [a000, afff]
[    0.472871] bus: 02 index 1 mmio: [e4000000, e40fffff]
[    0.472873] bus: 02 index 2 mmio: [0, 0]
[    0.472875] bus: 02 index 3 io port: [0, ffff]
[    0.472878] bus: 02 index 4 mmio: [0, ffffffff]
[    0.472890] NET: Registered protocol family 2
[    0.473072] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.473447] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.474054] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.474479] TCP: Hash tables configured (established 131072 bind 65536)
[    0.474483] TCP reno registered
[    0.474689] NET: Registered protocol family 1
[    0.474853] checking if image is initramfs... it is
[    0.936084] Switched to high resolution mode on CPU 0
[    1.165930] Freeing initrd memory: 8012k freed
[    1.166149] Simple Boot Flag value 0xe read from CMOS RAM was invalid
[    1.166153] Simple Boot Flag at 0x36 set to 0x1
[    1.166824] audit: initializing netlink socket (disabled)
[    1.166846] type=2000 audit(1230561163.164:1): initialized
[    1.172306] highmem bounce pool size: 64 pages
[    1.172315] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.175286] VFS: Disk quotas dquot_6.5.1
[    1.175405] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.175538] msgmni has been set to 1734
[    1.175701] io scheduler noop registered
[    1.175704] io scheduler anticipatory registered
[    1.175706] io scheduler deadline registered
[    1.175723] io scheduler cfq registered (default)
[    1.175821] pci 0000:01:00.0: Boot video device
[    1.175950] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.176017] pcieport-driver 0000:00:01.0: found MSI capability
[    1.176056] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.176120] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.176556] isapnp: Scanning for PnP cards...
[    1.528275] isapnp: No Plug & Play device found
[    1.579079] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.579237] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.579418] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.580239] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.580605] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.580880] serial 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.581343] 0000:02:01.0: ttyS2 at I/O 0xa008 (irq = 19) is a 16450
[    1.581633] 0000:02:01.0: ttyS3 at I/O 0xa010 (irq = 19) is a 8250
[    1.581733] Couldn't register serial port 0000:02:01.0: -28
[    1.583945] brd: module loaded
[    1.584389] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.584564] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.587501] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.587510] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.587939] mice: PS/2 mouse device common for all mice
[    1.588139] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.588165] rtc0: alarms up to one month, hpet irqs
[    1.588335] EISA: Probing bus 0 at eisa.0
[    1.588366] EISA: Detected 0 cards.
[    1.588370] cpuidle: using governor ladder
[    1.588372] cpuidle: using governor menu
[    1.589037] TCP cubic registered
[    1.589073] Using IPI No-Shortcut mode
[    1.589325] registered taskstats version 1
[    1.589443]   Magic number: 4:180:537
[    1.589448] bdi 1:15: hash matches
[    1.589579] rtc_cmos 00:03: setting system clock to 2008-12-29 14:32:44 UTC (1230561164)
[    1.589583] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.589585] EDD information not available.
[    1.589940] Freeing unused kernel memory: 424k freed
[    1.590001] Write protecting the kernel text: 2576k
[    1.590037] Write protecting the kernel read-only data: 936k
[    1.611771] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.846909] fuse init (API version 7.9)
[    2.105814] processor ACPI0007:00: registered as cooling_device0
[    2.105821] ACPI: Processor [CPU0] (supports 2 throttling states)
[    2.798429] usbcore: registered new interface driver usbfs
[    2.798463] usbcore: registered new interface driver hub
[    2.798522] usbcore: registered new device driver usb
[    2.807480] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.807496] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.807501] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.807558] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.811472] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.811488] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe4104000
[    2.829817] USB Universal Host Controller Interface driver v3.0
[    2.856041] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.856260] usb usb1: configuration #1 chosen from 1 choice
[    2.856300] hub 1-0:1.0: USB hub found
[    2.856313] hub 1-0:1.0: 8 ports detected
[    2.856535] No dock devices found.
[    2.901422] SCSI subsystem initialized
[    2.905016] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.959184] libata version 3.00 loaded.
[    3.064446] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.064459] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.064463] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.064495] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.064525] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000bc00
[    3.064643] usb usb2: configuration #1 chosen from 1 choice
[    3.064679] hub 2-0:1.0: USB hub found
[    3.064690] hub 2-0:1.0: 2 ports detected
[    3.272742] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.272755] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.272759] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.272795] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.272831] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b000
[    3.272971] usb usb3: configuration #1 chosen from 1 choice
[    3.273007] hub 3-0:1.0: USB hub found
[    3.273018] hub 3-0:1.0: 2 ports detected
[    3.288036] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    3.376344] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.376357] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.376362] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.376398] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.376435] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[    3.376558] usb usb4: configuration #1 chosen from 1 choice
[    3.376596] hub 4-0:1.0: USB hub found
[    3.376606] hub 4-0:1.0: 2 ports detected
[    3.421484] usb 1-6: configuration #1 chosen from 1 choice
[    3.421720] hub 1-6:1.0: USB hub found
[    3.422057] hub 1-6:1.0: 4 ports detected
[    3.584338] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.584350] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.584355] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.584388] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.584425] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
[    3.584545] usb usb5: configuration #1 chosen from 1 choice
[    3.584583] hub 5-0:1.0: USB hub found
[    3.584597] hub 5-0:1.0: 2 ports detected
[    3.636036] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    3.769133] usb 1-8: configuration #1 chosen from 1 choice
[    3.792400] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.792442] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    3.792460] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    3.792499] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.792504] 8139cp 0000:02:05.0: Try the "8139too" driver instead.
[    3.797542] ohci1394 0000:02:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.847305] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e4006000-e40067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.849832] 8139too Fast Ethernet driver 0.9.28
[    3.859142] 8139too 0000:02:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.860094] eth0: RealTek RTL8139 at 0xa400, 00:0f:ea:c4:df:56, IRQ 21
[    3.860097] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.860288] ata_piix 0000:00:1f.2: version 2.12
[    3.860300] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.860305] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.860353] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.861025] scsi0 : ata_piix
[    3.861151] scsi1 : ata_piix
[    3.862327] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    3.862331] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    3.900033] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    4.024351] ata1.00: ATA-6: ST380013AS, 3.00, max UDMA/133
[    4.024357] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.040373] ata1.00: configured for UDMA/133
[    4.124777] usb 2-1: configuration #1 chosen from 1 choice
[    4.128432] usbcore: registered new interface driver libusual
[    4.136880] Initializing USB Mass Storage driver...
[    4.144639] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.149157] usb-storage: device found at 4
[    4.149161] usb-storage: waiting for device to settle before scanning
[    4.151329] scsi3 : SCSI emulation for USB Mass Storage devices
[    4.151975] usbcore: registered new interface driver usb-storage
[    4.151981] USB Mass Storage support registered.
[    4.152141] usb-storage: device found at 2
[    4.152144] usb-storage: waiting for device to settle before scanning
[    4.236392] ata2.00: ATAPI: _NEC DVD_RW ND-3530A, 2.01, max UDMA/33
[    4.236419] ata2.01: ATAPI: TSSTcorpCD/DVDW SH-S162L, TS06, max UDMA/33
[    4.252324] ata2.00: configured for UDMA/33
[    4.292298] ata2.01: configured for UDMA/33
[    4.292438] scsi 0:0:0:0: Direct-Access     ATA      ST380013AS       3.00 PQ: 0 ANSI: 5
[    4.292672] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.294348] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-3530A  2.01 PQ: 0 ANSI: 5
[    4.294497] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.295611] scsi 1:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S162L TS06 PQ: 0 ANSI: 5
[    4.295754] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    4.341934] Driver 'sd' needs updating - please use bus_type methods
[    4.344578] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.344608] sd 0:0:0:0: [sda] Write Protect is off
[    4.344612] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.344659] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.344757] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.344783] sd 0:0:0:0: [sda] Write Protect is off
[    4.344787] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.344833] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.344838]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.360215]  sda1
[    4.360350] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.364842] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.364849] Uniform CD-ROM driver Revision: 3.20
[    4.364965] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.376305] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.376438] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    5.124945] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea0000c35e8a]
[    9.148124] usb-storage: device scan complete
[    9.153765] usb-storage: device scan complete
[    9.163382] scsi 2:0:0:0: Direct-Access     ST350083 0AS                   PQ: 0 ANSI: 2 CCS
[    9.172624] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    9.173356] sd 2:0:0:0: [sdb] Write Protect is off
[    9.173361] sd 2:0:0:0: [sdb] Mode Sense: 3c 00 00 00
[    9.173364] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.174107] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    9.174852] sd 2:0:0:0: [sdb] Write Protect is off
[    9.174856] sd 2:0:0:0: [sdb] Mode Sense: 3c 00 00 00
[    9.174858] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.174865]  sdb:<5>scsi 3:0:0:0: Direct-Access     GENERIC  USB Storage-SMC  500A PQ: 0 ANSI: 0 CCS
[    9.191765]  sdb1 sdb3 < sdb5<5>scsi 3:0:0:1: Direct-Access     GENERIC  USB Storage-CFC  500A PQ: 0 ANSI: 0 CCS
[    9.220858]  sdb6 >
[    9.221104] sd 2:0:0:0: [sdb] Attached SCSI disk
[    9.221268] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    9.237785] scsi 3:0:0:2: Direct-Access     GENERIC  USB Storage-SDC  500A PQ: 0 ANSI: 0 CCS
[    9.265779] scsi 3:0:0:3: Direct-Access     GENERIC  USB Storage-MSC  500A PQ: 0 ANSI: 0 CCS
[    9.278913] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[    9.279087] sd 3:0:0:0: Attached scsi generic sg4 type 0
[    9.283883] sd 3:0:0:1: [sdd] Attached SCSI removable disk
[    9.284136] sd 3:0:0:1: Attached scsi generic sg5 type 0
[    9.288879] sd 3:0:0:2: [sde] Attached SCSI removable disk
[    9.289029] sd 3:0:0:2: Attached scsi generic sg6 type 0
[    9.293899] sd 3:0:0:3: [sdf] Attached SCSI removable disk
[    9.294076] sd 3:0:0:3: Attached scsi generic sg7 type 0
[    9.553980] PM: Starting manual resume from disk
[    9.553985] PM: Resume from partition 8:22
[    9.553987] PM: Checking hibernation image.
[    9.554372] PM: Resume from disk failed.
[    9.631289] kjournald starting.  Commit interval 5 seconds
[    9.631304] EXT3-fs: mounted filesystem with ordered data mode.
[   15.466277] udevd version 124 started
[   16.163215] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.263261] Linux agpgart interface v0.103
[   16.349061] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.596440] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   16.612053] ACPI: Power Button (FF) [PWRF]
[   16.612202] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   16.628040] ACPI: Power Button (CM) [PWRB]
[   16.994936] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   17.374305] Linux video capture interface: v2.00
[   17.405428] [fglrx] Maximum main memory to use for locked dma buffers: 2394 MBytes.
[   17.405581] [fglrx]   vendor: 1002 device: 5b60 count: 1
[   17.406004] [fglrx] ioport: bar 1, base 0x9000, size: 0x100
[   17.406024] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.406031] pci 0000:01:00.0: setting latency timer to 64
[   17.406707] [fglrx] PAT is enabled successfully!
[   17.406746] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   17.682087] saa7130/34: v4l2 driver version 0.2.14 loaded
[   17.682746] saa7134 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   17.682755] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 20, latency: 32, mmio: 0xe4007000
[   17.682764] saa7134[0]: subsystem: 4e42:0138, board: LifeView FlyVIDEO3000 [card=2,insmod option]
[   17.682775] saa7134[0]: board init: gpio is 39000
[   17.682778] saa7134[0]: there are different flyvideo cards with different tuners
[   17.682780] saa7134[0]: out there, you might have to use the tuner=<nr> insmod
[   17.682781] saa7134[0]: option to override the default value.
[   17.682937] input: saa7134 IR (LifeView FlyVIDEO30 as /devices/pci0000:00/0000:00:1e.0/0000:02:00.0/input/input4
[   17.704034] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.704058] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.737641] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   17.738094] hda_codec: Cannot set up configuration from BIOS.  Using 3-stack mode...
[   17.992595] parport_pc 00:09: reported by Plug and Play ACPI
[   17.992674] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   18.041278] saa7134[0]: i2c eeprom 00: 42 4e 38 01 10 28 ff ff ff ff ff ff ff ff ff ff
[   18.041292] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041303] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041313] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041324] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041335] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041345] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041356] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041366] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041377] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041388] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041398] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041409] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041420] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041430] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.041441] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.114470] tuner' 0-0061: chip found @ 0xc2 (saa7134[0])
[   18.320043] tuner-simple 0-0061: creating new instance
[   18.320049] tuner-simple 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   18.367405] saa7134[0]: registered device video0 [v4l2]
[   18.367474] saa7134[0]: registered device vbi0
[   18.367546] saa7134[0]: registered device radio0
[   18.389400] saa7134 ALSA driver for DMA sound loaded
[   18.389436] saa7134[0]/alsa: saa7134[0] at 0xe4007000 irq 20 registered as card -2
[   18.572502] iTCO_vendor_support: vendor-support=0
[   18.575835] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   18.576031] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0460)
[   18.576203] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.663892] intel_rng: FWH not detected
[   19.676669] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   19.932936] logips2pp: Detected unknown logitech mouse model 105
[   20.412930] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   24.363394] lp0: using parport0 (interrupt-driven).
[   24.584999] Adding 7590672k swap on /dev/sdb6.  Priority:-1 extents:1 across:7590672k
[  302.287837] EXT3 FS on sdb5, internal journal
[  303.304136] type=1505 audit(1230557866.077:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=6037
[  303.375086] type=1505 audit(1230557866.145:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=6042
[  303.570164] type=1505 audit(1230557866.341:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=6046
[  303.570393] type=1505 audit(1230557866.341:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=6046
[  303.625549] type=1505 audit(1230557866.397:6): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=6050
[  303.744212] ip_tables: (C) 2000-2006 Netfilter Core Team
[  304.273178] ACPI: WMI: Mapper loaded
[  305.404493] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  307.479782] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  307.479790] apm: overridden by ACPI.
[  308.425291] ppdev: user-space parallel port driver
[  312.061741] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  312.061752] vboxdrv: Successfully done.
[  312.061754] vboxdrv: Found 1 processor cores.
[  312.062843] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  312.062850] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[  312.278438] NET: Registered protocol family 10
[  312.280088] lo: Disabled Privacy Extensions
[  320.097828] Bluetooth: Core ver 2.13
[  320.100728] NET: Registered protocol family 31
[  320.100737] Bluetooth: HCI device and connection manager initialized
[  320.100741] Bluetooth: HCI socket layer initialized
[  320.153843] Bluetooth: L2CAP ver 2.11
[  320.153851] Bluetooth: L2CAP socket layer initialized
[  320.171181] Bluetooth: SCO (Voice Link) ver 0.6
[  320.171189] Bluetooth: SCO socket layer initialized
[  320.191342] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  320.191350] Bluetooth: BNEP filters: protocol multicast
[  320.230381] Bridge firewalling registered
[  320.231504] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  320.253904] Bluetooth: RFCOMM socket layer initialized
[  320.254214] Bluetooth: RFCOMM TTY layer initialized
[  320.254221] Bluetooth: RFCOMM ver 1.10
[  324.412515] eth0: link down
[  324.412970] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  326.637862] [fglrx] Reserved FB block: Shared offset:0, size:40000 
[  326.637879] [fglrx] Reserved FB block: Unshared offset:1fbb000, size:44000 
[  326.637882] [fglrx] Reserved FB block: Unshared offset:1fff000, size:1000 
[  417.449781] UDF-fs: Partition marked readonly; forcing readonly mount
[  417.480600] UDF-fs INFO UDF: Mounting volume 'Sims2_EP5_1', timestamp 2007/01/26 09:41 (103c)
[  495.064101] ppdev0: registered pardevice
[  495.112050] ppdev0: unregistered pardevice
[  495.341764] ppdev0: registered pardevice
[  495.388301] ppdev0: unregistered pardevice
[  496.222668] ppdev0: registered pardevice
[  496.272183] ppdev0: unregistered pardevice
[  510.166990] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  510.167490] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  510.240507] NET: Registered protocol family 17
[  515.694836] eth0: link down
[  520.280015] eth0: no IPv6 routers present
[  522.382778] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  531.665764] eth0: link down
[  533.969429] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  563.153576] firefox[8805]: segfault at b798821e ip b7cc8571 sp bf86c0d4 error 4 in libc-2.8.90.so[b7c9a000+158000]
thijs@Thijs-Desktop:~$ 
thijs@Thijs-Desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
02:01.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
thijs@Thijs-Desktop:~$ clear screen

thijs@Thijs-Desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
02:01.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```

MythTV
```

thijs@Thijs-Desktop:~$ mythfrontend
2008-12-29 14:54:34.333 Using runtime prefix = /usr
2008-12-29 14:54:34.846 XScreenSaver support enabled
2008-12-29 14:54:34.846 DPMS is active.
2008-12-29 14:54:34.868 Using localhost value of localhost
2008-12-29 14:54:34.908 New DB connection, total: 1
2008-12-29 14:54:34.914 Connected to database 'mythtv' at host: 127.0.0.1
2008-12-29 14:54:34.928 Closing DB connection named 'DBManager0'
2008-12-29 14:54:34.938 Primary screen 0.
2008-12-29 14:54:34.939 Connected to database 'mythtv' at host: 127.0.0.1
2008-12-29 14:54:34.940 Using screen 0, 1280x1024 at 0,0
2008-12-29 14:54:34.975 New DB connection, total: 2
2008-12-29 14:54:34.996 Connected to database 'mythtv' at host: 127.0.0.1
2008-12-29 14:54:34.998 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-12-29 14:54:34.998 Enabled verbose msgs:  important general
2008-12-29 14:54:36.279 No theme dir: /home/thijs/.mythtv/themes/neon-wide
2008-12-29 14:54:36.819 Primary screen 0.
2008-12-29 14:54:36.819 Using screen 0, 1280x1024 at 0,0
2008-12-29 14:54:36.820 No theme dir: /home/thijs/.mythtv/themes/neon-wide
2008-12-29 14:54:36.821 Switching to wide mode (neon-wide)
2008-12-29 14:54:37.099 Using the Qt painter
mythtv: could not connect to socket
mythtv: Bestand of map bestaat niet
2008-12-29 14:54:37.100 lirc_init failed for mythtv, see preceding messages
2008-12-29 14:54:37.100 JoystickMenuClient Error: Joystick disabled - Failed to read /home/thijs/.mythtv/joystickmenurc
2008-12-29 14:54:39.569 Specified base font 'medium' does not exist for font clock
2008-12-29 14:54:39.570 Specified base font 'medium' does not exist for font small
2008-12-29 14:54:39.570 Specified base font 'medium' does not exist for font medium
2008-12-29 14:54:39.570 Specified base font 'medium' does not exist for font large
2008-12-29 14:54:39.571 Loading from: /usr/share/mythtv/themes/neon-wide/base.xml
2008-12-29 14:54:39.727 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-12-29 14:54:39.840 Registering Internal as a media playback plugin.
2008-12-29 14:54:40.182 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-12-29 14:54:42.053 Failed to run 'cdrecord --scanbus'
2008-12-29 14:54:42.123 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 10.0.0.1:5060 NAT address 10.0.0.1
SIP: Cannot register; proxy, username or password not set
2008-12-29 14:54:42.479 No theme dir: /home/thijs/.mythtv/themes/neon-wide
2008-12-29 14:54:44.934 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-12-29 14:54:44.936 Using protocol version 40
2008-12-29 14:54:44.961 TV: Attempting to change from None to WatchingLiveTV
2008-12-29 14:54:44.962 Using protocol version 40
2008-12-29 14:54:46.151 GetEntryAt(-1) failed.
2008-12-29 14:54:46.164 EntryToProgram(0@do jan 1 01:00:00 1970) failed to get pginfo
2008-12-29 14:54:46.170 TV Error: LiveTV not successfully started
2008-12-29 14:54:46.170 TV Error: LiveTV not successfully started
2008-12-29 14:54:46.252 TV: Deleting TV Chain in destructor
2008-12-29 14:54:46.262 DPMS Deactivated 
2008-12-29 14:54:46.263 DPMS Reactivated.
2008-12-29 14:54:48.007 TV: Attempting to change from None to WatchingLiveTV
2008-12-29 14:54:48.008 Using protocol version 40
2008-12-29 14:54:49.120 GetEntryAt(-1) failed.
2008-12-29 14:54:49.121 EntryToProgram(0@do jan 1 01:00:00 1970) failed to get pginfo
2008-12-29 14:54:49.121 TV Error: LiveTV not successfully started
2008-12-29 14:54:49.121 TV Error: LiveTV not successfully started
2008-12-29 14:54:49.249 TV: Deleting TV Chain in destructor
2008-12-29 14:54:49.259 DPMS Deactivated 
2008-12-29 14:54:49.259 DPMS Reactivated.
Destroying SipFsm object 
2008-12-29 14:54:51.314 Deleting UPnP client...

```

It's a SAA7134 chip and I hope anyone comes with an answer soon.

---

### Post by TheDarkMaster on 2008-12-29
By messing around some more I found that it was MythTv's configuration due to the fact that TvTime worked very well. BUT I still prefer the interface that MythTv provides and would like to get that working. So could anyone give me some info about how to config it??

---

### Post by TheDarkMaster on 2008-12-30
Anyone Please?

---

### Post by NauTiluS1 on 2009-01-07
> **TheDarkMaster said:**
> Anyone Please?

 17.682755] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 20, latency: 32, mmio: 0xe4007000
[   17.682764] saa7134[0]: subsystem: 4e42:0138, board: LifeView FlyVIDEO3000 [card=2,insmod option]
[   17.682775] saa7134[0]: board init: gpio is 39000
[   17.682778] saa7134[0]: there are different flyvideo cards with different tuners
[   17.682780] saa7134[0]: out there, you might have to use the tuner=<nr> insmod
[   17.682781] saa7134[0]: option to override the default value.


Fijate que dice que no hay concordancia con el "tuner", tienes que tratar de buscar la configuracion buena para el tuner.

Mas informacion [aqui]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134") y [aqui]("http://tvtime.sourceforge.net/problems.html#undetected").

Perdona no hablo ingles

---

### Post by TheDarkMaster on 2009-01-21
Didnt visit this thread in a while but, Nautilus1 I dont understand exactly what you're saying but I assume it's about the radio. And that's just the one which worked fine:o. But I found the source of the problem and that's MythTv. I installed tvtime, figured out how it works. And got working.
So if anyone wanna delete this thread. Go on. I was complainning about nothing:O

---

