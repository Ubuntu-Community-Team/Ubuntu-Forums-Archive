---
title: "having trouble compiling Madwifi driver"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by Dopaque on 2008-08-25
Hello. I'm a relatively new Ubuntu user... I have Hardy Heron 32-bit.

I've been trying for a week now to get my wireless internet working. Atheros AR5007 802.11b/g chipset (I think that's right) according to Vista. Unfortunately, my Vista partition is now down so I can't doublecheck.

Anyway, until my Vista partition crashed, I could use my wireless internet on it. Now I really need my wireless internet on Ubuntu. I've been trying to install a Madwifi driver and have installed several, just to be met with error messages at every turn. I FINALLY got these commands to work:

sudo make
sudo make install

BUT I get an error at the last step in the process.

```
user@user-laptop:~/madwifi-hal-0.10.5.6-r3835-20080801$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

here is the dmesg:
```

[   17.848850] Time: 13:47:56  Date: 08/25/08
[   17.848875] NET: Registered protocol family 16
[   17.849049] EISA bus registered
[   17.849053] ACPI: bus type pci registered
[   17.870029] PCI: PCI BIOS revision 3.00 entry at 0xfddad, last bus=5
[   17.870031] PCI: Using configuration type 1
[   17.870038] Setting up standard PCI resources
[   17.871712] ACPI: EC: Look up EC in DSDT
[   17.873384] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   17.873933] ACPI: Interpreter enabled
[   17.873936] ACPI: (supports S0 S3 S4 S5)
[   17.873947] ACPI: Using IOAPIC for interrupt routing
[   17.873339] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.880780] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   17.880783] ACPI: EC: driver started in interrupt mode
[   17.880838] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.881718] PCI: Transparent bridge - 0000:00:08.0
[   17.881895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.881974] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   17.881993] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   17.882021] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   17.911428] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[   17.911615] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[   17.911798] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[   17.911986] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[   17.912170] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[   17.912352] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[   17.912534] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[   17.912717] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[   17.912899] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[   17.913080] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[   17.913263] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[   17.913445] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[   17.913627] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[   17.913810] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[   17.913993] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[   17.914175] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[   17.914357] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[   17.914540] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[   17.914723] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[   17.914853] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.914880] pnp: PnP ACPI init
[   17.914888] ACPI: bus type pnp registered
[   17.916699] pnp: PnP ACPI: found 12 devices
[   17.916702] ACPI: ACPI bus type pnp unregistered
[   17.916705] PnPBIOS: Disabled by ACPI PNP
[   17.916932] PCI: Using ACPI for IRQ routing
[   17.916935] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.950783] NET: Registered protocol family 8
[   17.950784] NET: Registered protocol family 20
[   17.950816] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   17.950820] hpet0: 3 32-bit timers, 25000000 Hz
[   17.951859] AppArmor: AppArmor Filesystem Enabled
[   17.955869] Time: hpet clocksource has been installed.
[   17.955873] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   17.955876] Could not switch to high resolution mode on CPU 0
[   17.958764] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   17.958767] Could not switch to high resolution mode on CPU 1
[   17.966783] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[   17.966789] system 00:03: ioport range 0x1000-0x107f has been reserved
[   17.966791] system 00:03: ioport range 0x1080-0x10ff has been reserved
[   17.966794] system 00:03: ioport range 0x1400-0x147f has been reserved
[   17.966796] system 00:03: ioport range 0x1480-0x14ff has been reserved
[   17.966799] system 00:03: ioport range 0x1800-0x187f has been reserved
[   17.966801] system 00:03: ioport range 0x1880-0x18ff has been reserved
[   17.966806] system 00:04: ioport range 0x360-0x361 has been reserved
[   17.966808] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   17.966816] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[   17.966819] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   17.966822] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[   17.966825] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[   17.966827] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   17.966830] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[   17.997183] PCI: Bridge: 0000:00:08.0
[   17.997184]   IO window: disabled.
[   17.997187]   MEM window: f6100000-f61fffff
[   17.997190]   PREFETCH window: disabled.
[   17.997193] PCI: Bridge: 0000:00:0c.0
[   17.997194]   IO window: 4000-4fff
[   17.997197]   MEM window: f2000000-f3ffffff
[   17.997199]   PREFETCH window: f0000000-f1ffffff
[   17.997201] PCI: Bridge: 0000:00:0d.0
[   17.997203]   IO window: disabled.
[   17.997205]   MEM window: f6000000-f60fffff
[   17.997207]   PREFETCH window: disabled.
[   17.997217] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   17.997225] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   17.997232] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   17.997242] NET: Registered protocol family 2
[   18.038677] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.038925] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.039738] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   18.040181] TCP: Hash tables configured (established 131072 bind 65536)
[   18.040183] TCP reno registered
[   18.054729] checking if image is initramfs... it is
[   18.643134] Freeing initrd memory: 7304k freed
[   18.643232] Simple Boot Flag at 0x36 set to 0x1
[   18.643840] audit: initializing netlink socket (disabled)
[   18.643852] audit(1219672076.332:1): initialized
[   18.644046] highmem bounce pool size: 64 pages
[   18.645819] VFS: Disk quotas dquot_6.5.1
[   18.645884] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.645998] io scheduler noop registered
[   18.646000] io scheduler anticipatory registered
[   18.646002] io scheduler deadline registered
[   18.646011] io scheduler cfq registered (default)
[   18.646041] pci 0000:00:00.0: Enabling HT MSI Mapping
[   18.646174] pci 0000:00:07.0: Enabling HT MSI Mapping
[   18.646187] pci 0000:00:08.0: Enabling HT MSI Mapping
[   18.646202] pci 0000:00:09.0: Enabling HT MSI Mapping
[   18.646217] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   18.646231] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   18.646244] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   18.646258] Boot video device is 0000:00:12.0
[   18.646366] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   18.646389] assign_interrupt_mode Found MSI capability
[   18.646409] Allocate Port Service[0000:00:0c.0:pcie00]
[   18.646470] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   18.646491] assign_interrupt_mode Found MSI capability
[   18.646506] Allocate Port Service[0000:00:0d.0:pcie00]
[   18.646714] isapnp: Scanning for PnP cards...
[   18.998628] isapnp: No Plug & Play device found
[   19.024899] Real Time Clock Driver v1.12ac
[   19.025091] hpet_resources: 0xfed00000 is busy
[   19.025129] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.026196] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.026256] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.026344] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   19.053720] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.053725] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.064755] mice: PS/2 mouse device common for all mice
[   19.064870] EISA: Probing bus 0 at eisa.0
[   19.064875] Cannot allocate resource for EISA slot 1
[   19.064879] Cannot allocate resource for EISA slot 3
[   19.064881] Cannot allocate resource for EISA slot 4
[   19.064893] EISA: Detected 0 cards.
[   19.064896] cpuidle: using governor ladder
[   19.064898] cpuidle: using governor menu
[   19.064978] NET: Registered protocol family 1
[   19.065001] Using IPI No-Shortcut mode
[   19.065032] registered taskstats version 1
[   19.065147]   Magic number: 4:505:787
[   19.065260]   hash matches device ptyq9
[   19.065314] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.065315] EDD information not available.
[   19.065552] Freeing unused kernel memory: 368k freed
[   19.101729] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.315811] fuse init (API version 7.9)
[   20.338248] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   20.338255] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.337292] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   20.337300] ACPI: Processor [CPU1] (supports 8 throttling states)
[   20.339041] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
[   20.795577] usbcore: registered new interface driver usbfs
[   20.795599] usbcore: registered new interface driver hub
[   20.795625] usbcore: registered new device driver usb
[   20.806834] SCSI subsystem initialized
[   20.817958] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   20.817969] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 16
[   20.817981] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   20.817984] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   20.818242] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   20.818271] ehci_hcd 0000:00:02.1: debug port 1
[   20.818275] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   20.818285] ehci_hcd 0000:00:02.1: irq 16, io mem 0xf6489000
[   20.833376] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.833509] usb usb1: configuration #1 chosen from 1 choice
[   20.833530] hub 1-0:1.0: USB hub found
[   20.833536] hub 1-0:1.0: 7 ports detected
[   20.839736] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.852779] libata version 3.00 loaded.
[   20.938249] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[   20.938254] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [Z019] -> GSI 22 (level, low) -> IRQ 16
[   20.938267] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   20.938270] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   20.938292] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[   20.938320] ehci_hcd 0000:00:04.1: debug port 1
[   20.938323] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   20.938330] ehci_hcd 0000:00:04.1: irq 16, io mem 0xf6489400
[   20.949198] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.949317] usb usb2: configuration #1 chosen from 1 choice
[   20.949338] hub 2-0:1.0: USB hub found
[   20.949345] hub 2-0:1.0: 2 ports detected
[   21.054143] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   21.054478] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   21.054488] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 17
[   21.054494] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   21.293590] usb 2-2: new high speed USB device using ehci_hcd and address 2
[   21.437615] usb 2-2: configuration #1 chosen from 1 choice
[   21.573488] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1e:68:32:43:8b
[   21.573493] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   21.572526] ahci 0000:00:09.0: version 3.0
[   21.572855] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[   21.572864] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 23 (level, low) -> IRQ 18
[   22.578692] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   22.578697] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[   22.578701] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.579043] scsi0 : ahci
[   22.579317] scsi1 : ahci
[   22.579456] scsi2 : ahci
[   22.579592] scsi3 : ahci
[   22.579664] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 221
[   22.579667] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 221
[   22.579670] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 221
[   22.579672] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 221
[   23.236839] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.240291] ata1.00: ATA-8: SAMSUNG HM250JI, HS100-10, max UDMA/100
[   23.240294] ata1.00: 488397168 sectors, multi 16: LBA48 
[   23.243813] ata1.00: configured for UDMA/100
[   23.560231] ata2: SATA link down (SStatus 0 SControl 300)
[   23.891608] ata3: SATA link down (SStatus 0 SControl 300)
[   24.222988] ata4: SATA link down (SStatus 0 SControl 300)
[   24.223086] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM250JI  HS10 PQ: 0 ANSI: 5
[   24.224257] PCI: Enabling device 0000:02:05.0 (0100 -> 0102)
[   24.223461] pata_amd 0000:00:06.0: version 0.3.10
[   24.224577] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   24.224590] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNK1] -> GSI 5 (level, low) -> IRQ 5
[   24.223545] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.223799] scsi4 : pata_amd
[   24.223942] scsi5 : pata_amd
[   24.224200] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[   24.224203] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[   24.276284] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   24.550658] ata5.00: ATAPI: Optiarc DVD RW AD-7560A, DH10, max MWDMA2
[   24.730249] ata5.00: configured for MWDMA2
[   24.730279] ata6: port disabled. ignoring.
[   24.731441] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560A  DH10 PQ: 0 ANSI: 5
[   24.735696] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[   24.735707] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 18 (level, low) -> IRQ 19
[   24.735720] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.735723] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   24.735753] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[   24.735772] ohci_hcd 0000:00:02.0: irq 19, io mem 0xf6486000
[   24.793083] usb usb3: configuration #1 chosen from 1 choice
[   24.793107] hub 3-0:1.0: USB hub found
[   24.793114] hub 3-0:1.0: 7 ports detected
[   24.895191] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[   24.895195] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [Z018] -> GSI 18 (level, low) -> IRQ 19
[   24.895210] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   24.895214] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   24.895241] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[   24.895257] ohci_hcd 0000:00:04.0: irq 19, io mem 0xf6487000
[   24.952764] usb usb4: configuration #1 chosen from 1 choice
[   24.952785] hub 4-0:1.0: USB hub found
[   24.952795] hub 4-0:1.0: 2 ports detected
[   25.079080] Driver 'sd' needs updating - please use bus_type methods
[   25.079165] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   25.079176] sd 0:0:0:0: [sda] Write Protect is off
[   25.079179] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.079193] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.079238] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   25.079246] sd 0:0:0:0: [sda] Write Protect is off
[   25.079248] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.079262] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.079265]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   25.556575] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0065c1c900]
[   25.695254]  sda1 < sda5 sda6 sda7 > sda2
[   25.743915] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.749799] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.749819] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   25.750753] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   25.750759] Uniform CD-ROM driver Revision: 3.20
[   25.750813] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   26.067737] Attempting manual resume
[   26.067741] swsusp: Resume From Partition 8:7
[   26.067743] PM: Checking swsusp image.
[   26.067910] PM: Resume from disk failed.
[   26.099185] kjournald starting.  Commit interval 5 seconds
[   26.099202] EXT3-fs: mounted filesystem with ordered data mode.
[   34.455906] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   34.648502] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.700410] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.865117] input: Power Button (FF) as /devices/virtual/input/input3
[   34.915993] ACPI: Power Button (FF) [PWRF]
[   34.916063] input: Sleep Button (CM) as /devices/virtual/input/input4
[   34.979816] ACPI: Sleep Button (CM) [SLPB]
[   34.979872] input: Lid Switch as /devices/virtual/input/input5
[   34.997447] Linux agpgart interface v0.102
[   35.012789] ACPI: Lid Switch [LID]
[   35.012876] input: Power Button (CM) as /devices/virtual/input/input6
[   35.075665] ACPI: Power Button (CM) [PWRB]
[   35.076163] ACPI: AC Adapter [ACAD] (off-line)
[   35.076252] ACPI: WMI-Acer: Mapper loaded
[   35.120661] nvidia: module license 'NVIDIA' taints kernel.
[   35.334420] ACPI: Battery Slot [BAT0] (battery present)
[   35.588283] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   35.646593] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   35.929376] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   35.929387] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LGPU] -> GSI 16 (level, low) -> IRQ 20
[   35.929395] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   35.929603] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   36.125312] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   36.125323] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 21
[   36.125346] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   36.201912] sdhci: Secure Digital Host Controller Interface driver
[   36.201917] sdhci: Copyright(c) Pierre Ossman
[   36.205571] sdhci: SDHCI controller found at 0000:02:05.1 [1180:0822] (rev 22)
[   36.205879] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   36.205891] ACPI: PCI Interrupt 0000:02:05.1[B] -> Link [LNK2] -> GSI 7 (level, low) -> IRQ 7
[   36.205908] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   36.205949] mmc0: SDHCI at 0xf6100800 irq 7 DMA
[   36.214575] ricoh-mmc: Ricoh MMC Controller disabling driver
[   36.214579] ricoh-mmc: Copyright(c) Philip Langdale
[   36.214633] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   36.214643] ricoh-mmc: Controller is now disabled.
[   36.256580] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   36.505638] Linux video capture interface: v2.00
[   36.527444] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b015)
[   36.529511] usbcore: registered new interface driver uvcvideo
[   36.529514] USB Video Class driver (v0.1.0)
[   37.153456] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   37.232594] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   37.799396] lp: driver loaded but no devices found
[   37.923890] Adding 5574512k swap on /dev/sda7.  Priority:-1 extents:1 across:5574512k
[   37.948132] EXT3 FS on sda6, internal journal
[   38.583615] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.026641] No dock devices found.
[   39.379025] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[   39.380097] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x12
[   39.380101] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[   39.380104] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   39.380106] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   40.175963] apm: BIOS not found.
[   40.314494] ppdev: user-space parallel port driver
[   40.453587] audit(1219690098.811:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5197 profile="/usr/sbin/cupsd" namespace="default"
[   41.133847] Clocksource tsc unstable (delta = -134362326 ns)
[   41.871002] Bluetooth: Core ver 2.11
[   41.871238] NET: Registered protocol family 31
[   41.871241] Bluetooth: HCI device and connection manager initialized
[   41.871245] Bluetooth: HCI socket layer initialized
[   41.900641] Bluetooth: L2CAP ver 2.9
[   41.900646] Bluetooth: L2CAP socket layer initialized
[   41.952353] Bluetooth: RFCOMM socket layer initialized
[   41.952370] Bluetooth: RFCOMM TTY layer initialized
[   41.952372] Bluetooth: RFCOMM ver 1.8
[   43.300617] NET: Registered protocol family 17
[   45.979923] NET: Registered protocol family 10
[   45.980303] lo: Disabled Privacy Extensions
[   51.364794] eth0: no IPv6 routers present
[   56.652181] CPU0 attaching NULL sched-domain.
[   56.652190] CPU1 attaching NULL sched-domain.
[   56.661579] CPU0 attaching sched-domain:
[   56.661583]  domain 0: span 03
[   56.661587]   groups: 01 02
[   56.661590]   domain 1: span 03
[   56.661592]    groups: 03
[   56.661596] CPU1 attaching sched-domain:
[   56.661598]  domain 0: span 03
[   56.661600]   groups: 02 01
[   56.661603]   domain 1: span 03
[   56.661606]    groups: 03
[  461.926238] ath_pci: disagrees about version of symbol _ath_hal_attach
[  461.926247] ath_pci: Unknown symbol _ath_hal_attach
[  461.926347] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  461.926349] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  461.926731] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  461.926733] ath_pci: Unknown symbol ath_hal_computetxtime
[  461.927008] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  461.927010] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  461.927191] ath_pci: Unknown symbol _ath_hal_detach
[  461.927797] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  461.928331] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  461.928334] ath_pci: Unknown symbol ath_hal_init_channels
[  461.928568] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  461.928570] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[  493.730014] ath_pci: disagrees about version of symbol _ath_hal_attach
[  493.730025] ath_pci: Unknown symbol _ath_hal_attach
[  493.730124] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  493.730126] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  493.730509] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  493.730511] ath_pci: Unknown symbol ath_hal_computetxtime
[  493.730765] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  493.730767] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  493.730954] ath_pci: Unknown symbol _ath_hal_detach
[  493.731526] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  493.732102] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  493.732104] ath_pci: Unknown symbol ath_hal_init_channels
[  493.732339] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  493.732341] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[  723.873733] CPU0 attaching NULL sched-domain.
[  723.873743] CPU1 attaching NULL sched-domain.
[  723.885272] CPU0 attaching sched-domain:
[  723.885278]  domain 0: span 03
[  723.885280]   groups: 01 02
[  723.885285] CPU1 attaching sched-domain:
[  723.885287]  domain 0: span 03
[  723.885288]   groups: 02 01
[ 1874.626493] ath_pci: disagrees about version of symbol _ath_hal_attach
[ 1874.626502] ath_pci: Unknown symbol _ath_hal_attach
[ 1874.626602] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[ 1874.626605] ath_pci: Unknown symbol ath_hal_process_noisefloor
[ 1874.626986] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[ 1874.626989] ath_pci: Unknown symbol ath_hal_computetxtime
[ 1874.627241] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[ 1874.627243] ath_pci: Unknown symbol ath_hal_mhz2ieee
[ 1874.627423] ath_pci: Unknown symbol _ath_hal_detach
[ 1874.627991] ath_pci: Unknown symbol ath_hal_print_decoded_register
[ 1874.628528] ath_pci: disagrees about version of symbol ath_hal_init_channels
[ 1874.628530] ath_pci: Unknown symbol ath_hal_init_channels
[ 1874.628768] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[ 1874.628770] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[ 1877.016381] ath_pci: disagrees about version of symbol _ath_hal_attach
[ 1877.016393] ath_pci: Unknown symbol _ath_hal_attach
[ 1877.016493] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[ 1877.016497] ath_pci: Unknown symbol ath_hal_process_noisefloor
[ 1877.016889] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[ 1877.016893] ath_pci: Unknown symbol ath_hal_computetxtime
[ 1877.017145] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[ 1877.017149] ath_pci: Unknown symbol ath_hal_mhz2ieee
[ 1877.017329] ath_pci: Unknown symbol _ath_hal_detach
[ 1877.017896] ath_pci: Unknown symbol ath_hal_print_decoded_register
[ 1877.018438] ath_pci: disagrees about version of symbol ath_hal_init_channels
[ 1877.018440] ath_pci: Unknown symbol ath_hal_init_channels
[ 1877.018674] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[ 1877.018676] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[ 2039.342648] ath_pci: disagrees about version of symbol _ath_hal_attach
[ 2039.342658] ath_pci: Unknown symbol _ath_hal_attach
[ 2039.342757] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[ 2039.342759] ath_pci: Unknown symbol ath_hal_process_noisefloor
[ 2039.343151] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[ 2039.343153] ath_pci: Unknown symbol ath_hal_computetxtime
[ 2039.343406] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[ 2039.343408] ath_pci: Unknown symbol ath_hal_mhz2ieee
[ 2039.343588] ath_pci: Unknown symbol _ath_hal_detach
[ 2039.344151] ath_pci: Unknown symbol ath_hal_print_decoded_register
[ 2039.344690] ath_pci: disagrees about version of symbol ath_hal_init_channels
[ 2039.344692] ath_pci: Unknown symbol ath_hal_init_channels
[ 2039.344926] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[ 2039.344929] ath_pci: Unknown symbol ath_hal_getwirelessmodes
```

I'm pretty sure I have uninstalled and made clean all the prior versions of madwifi I tried. I have also read every thread on these forums regarding Atheros wireless in full, it seems. I can't figure it out, but I am much closer than I was at first. Help is greatly appreciated!

---

### Post by Dopaque on 2008-08-25
Nevermind -- I figured out the problem. I hadn't disabled the HAL driver what came with my windows and it was interfering. I thought I had disabled it but I must have renabled it at some point.

Problem solved. My wireless works now!

---

