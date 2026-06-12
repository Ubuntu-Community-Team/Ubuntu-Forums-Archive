---
title: "Atheros AR5008 suddenly stopped working"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by 636cc of fury on 2007-11-15
Well as the title states, I have been using an Atheros AR5008 wifi card (Gigabyte) with no avail for about 3 months now and today after I booted up my computer I was unable to connect as my card is not working for whatever reason. The card does work in windows so I am perplexed as to why this would happen.

here is my dmesg:

[   14.047214]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   14.047216]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   14.047222] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.047274] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.047477] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.047484] hpet0: 3 64-bit timers, 14318180 Hz
[   14.128487] Calibrating delay using timer specific routine.. 2397.56 BogoMIPS (lpj=4795123)
[   14.128519] Security Framework v1.0.0 initialized
[   14.128531] SELinux:  Disabled at boot.
[   14.128552] Mount-cache hash table entries: 512
[   14.128729] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   14.128741] monitor/mwait feature present.
[   14.128744] using mwait in idle threads.
[   14.128750] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.128753] CPU: L2 cache: 2048K
[   14.128757] CPU: Physical Processor ID: 0
[   14.128760] CPU: Processor Core ID: 0
[   14.128763] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   14.128776] Compat vDSO mapped to ffffe000.
[   14.128794] Checking 'hlt' instruction... OK.
[   14.144651] SMP alternatives: switching to UP code
[   14.145306] Early unpacking initramfs... done
[   14.642449] ACPI: Core revision 20070126
[   14.642531] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.646261] CPU0: Intel Genuine Intel(R) CPU           U2500  @ 1.20GHz stepping 08
[   14.646284] SMP alternatives: switching to SMP code
[   14.646421] Booting processor 1/1 eip 3000
[   16.520747] Initializing CPU#1
[   16.600265] Calibrating delay using timer specific routine.. 2394.67 BogoMIPS (lpj=4789349)
[   16.600274] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   16.600281] monitor/mwait feature present.
[   16.600287] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.600290] CPU: L2 cache: 2048K
[   16.600293] CPU: Physical Processor ID: 0
[   16.600295] CPU: Processor Core ID: 1
[   16.600297] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   14.737067] CPU1: Intel Genuine Intel(R) CPU           U2500  @ 1.20GHz stepping 08
[   14.737097] Total of 2 processors activated (4792.23 BogoMIPS).
[   14.737308] ENABLING IO-APIC IRQs
[   14.737530] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.884376] checking TSC synchronization [CPU#0 -> CPU#1]:
[   14.904383] Measured 2232397971 cycles TSC warp between CPUs, turning off TSC clock.
[    0.728000] Marking TSC unstable due to: check_tsc_sync_source failed.
[    0.732000] Brought up 2 CPUs
[    0.792000] migration_cost=4000
[    0.792000] Booting paravirtualized kernel on bare hardware
[    0.792000] Time:  4:18:35  Date: 10/15/107
[    0.792000] NET: Registered protocol family 16
[    0.792000] EISA bus registered
[    0.792000] ACPI: bus type pci registered
[    0.820000] PCI: PCI BIOS revision 2.10 entry at 0xface6, last bus=12
[    0.820000] PCI: Using configuration type 1
[    0.820000] Setting up standard PCI resources
[    0.828000] ACPI: EC: Look up EC in DSDT
[    0.848000] ACPI Warning (tbutils-0217): Incorrect checksum in table [TCPA] -  00, should be 92 [20070126]
[    0.848000] ACPI: SSDT 7F681A52, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[    0.848000] ACPI: Interpreter enabled
[    0.848000] ACPI: (supports S0 S3 S4 S5)
[    0.848000] ACPI: Using IOAPIC for interrupt routing
[    0.884000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.884000] PCI: Probing PCI hardware (bus 00)
[    0.884000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.884000] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.884000] PCI: Transparent bridge - 0000:00:1e.0
[    0.884000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.884000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.884000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.884000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.884000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PXP0._PRT]
[    0.908000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.908000] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[    0.908000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *3
[    0.908000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.908000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.908000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.908000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.908000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.908000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.908000] pnp: PnP ACPI init
[    0.908000] ACPI: bus type pnp registered
[    0.964000] pnp: PnP ACPI: found 13 devices
[    0.964000] ACPI: ACPI bus type pnp unregistered
[    0.964000] PnPBIOS: Disabled by ACPI PNP
[    0.964000] PCI: Using ACPI for IRQ routing
[    0.964000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    1.012000] NET: Registered protocol family 8
[    1.012000] NET: Registered protocol family 20
[    1.012000] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
[    1.012000] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    1.012000] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    1.012000] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    1.012000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    1.012000] pnp: 00:02: ioport range 0x1000-0x1005 has been reserved
[    1.012000] pnp: 00:02: ioport range 0x1008-0x100f has been reserved
[    1.012000] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    1.012000] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    1.012000] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    1.012000] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    1.012000] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    1.012000] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    1.012000] pnp: 00:08: ioport range 0xc80-0xcaf has been reserved
[    1.012000] pnp: 00:08: ioport range 0xcc0-0xcff could not be reserved
[    1.012000] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    1.012000] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    1.012000] pnp: 00:08: ioport range 0xcbc-0xcbf has been reserved
[    1.012000] pnp: 00:08: ioport range 0x930-0x97f has been reserved
[    1.012000] pnp: 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    1.012000] pnp: 00:0c: ioport range 0xcb0-0xcbb has been reserved
[    1.012000] pnp: 00:0c: iomem range 0xfed40000-0xfed44fff could not be reserved
[    1.016000] Time: hpet clocksource has been installed.
[    1.016000] Switched to high resolution mode on CPU 0
[    1.016000] Switched to high resolution mode on CPU 1
[    1.040000] PCI: Bridge: 0000:00:1c.0
[    1.040000]   IO window: disabled.
[    1.040000]   MEM window: disabled.
[    1.040000]   PREFETCH window: disabled.
[    1.040000] PCI: Bridge: 0000:00:1c.1
[    1.040000]   IO window: disabled.
[    1.040000]   MEM window: efd00000-efdfffff
[    1.040000]   PREFETCH window: disabled.
[    1.040000] PCI: Bridge: 0000:00:1c.2
[    1.040000]   IO window: disabled.
[    1.040000]   MEM window: efc00000-efcfffff
[    1.040000]   PREFETCH window: disabled.
[    1.040000] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[    1.040000]   IO window: 00002000-000020ff
[    1.040000]   IO window: 00002400-000024ff
[    1.040000]   PREFETCH window: 88000000-8bffffff
[    1.040000]   MEM window: 8c000000-8fffffff
[    1.040000] PCI: Bridge: 0000:00:1e.0
[    1.040000]   IO window: 2000-2fff
[    1.040000]   MEM window: efb00000-efbfffff
[    1.040000]   PREFETCH window: 88000000-8bffffff
[    1.040000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    1.040000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.040000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    1.040000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.040000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    1.040000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    1.040000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    1.040000] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[    1.040000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[    1.040000] NET: Registered protocol family 2
[    1.080000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.080000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    1.080000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.080000] TCP: Hash tables configured (established 131072 bind 65536)
[    1.080000] TCP reno registered
[    1.096000] checking if image is initramfs... it is
[    2.088000] Freeing initrd memory: 7289k freed
[    2.088000] audit: initializing netlink socket (disabled)
[    2.088000] audit(1195100316.016:1): initialized
[    2.088000] highmem bounce pool size: 64 pages
[    2.088000] VFS: Disk quotas dquot_6.5.1
[    2.088000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.092000] io scheduler noop registered
[    2.092000] io scheduler anticipatory registered
[    2.092000] io scheduler deadline registered
[    2.092000] io scheduler cfq registered (default)
[    2.092000] Boot video device is 0000:00:02.0
[    2.092000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    2.092000] assign_interrupt_mode Found MSI capability
[    2.092000] Allocate Port Service[0000:00:1c.0:pcie00]
[    2.092000] Allocate Port Service[0000:00:1c.0:pcie02]
[    2.092000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    2.092000] assign_interrupt_mode Found MSI capability
[    2.092000] Allocate Port Service[0000:00:1c.1:pcie00]
[    2.092000] Allocate Port Service[0000:00:1c.1:pcie02]
[    2.092000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    2.092000] assign_interrupt_mode Found MSI capability
[    2.092000] Allocate Port Service[0000:00:1c.2:pcie00]
[    2.092000] Allocate Port Service[0000:00:1c.2:pcie02]
[    2.092000] isapnp: Scanning for PnP cards...
[    2.444000] isapnp: No Plug & Play device found
[    2.476000] Real Time Clock Driver v1.12ac
[    2.476000] hpet_resources: 0xfed00000 is busy
[    2.476000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.480000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.480000] input: Macintosh mouse button emulation as /class/input/input0
[    2.480000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.484000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.484000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.484000] mice: PS/2 mouse device common for all mice
[    2.484000] EISA: Probing bus 0 at eisa.0
[    2.484000] EISA: Cannot allocate resource for mainboard
[    2.484000] Cannot allocate resource for EISA slot 1
[    2.484000] Cannot allocate resource for EISA slot 2
[    2.484000] EISA: Detected 0 cards.
[    2.484000] TCP cubic registered
[    2.484000] NET: Registered protocol family 1
[    2.484000] Using IPI No-Shortcut mode
[    2.484000]   Magic number: 15:848:312
[    2.484000]   hash matches device ttyxf
[    2.484000] Freeing unused kernel memory: 364k freed
[    2.492000] input: AT Translated Set 2 keyboard as /class/input/input1
[    3.776000] AppArmor: AppArmor initialized<5>audit(1195100317.516:2):  type=1505 info="AppArmor initialized" pid=1249
[    3.788000] fuse init (API version 7.8)
[    3.796000] Failure registering capabilities with primary security module.
[    3.836000] ACPI: SSDT 7F6821BC, 01C0 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    3.836000] ACPI: SSDT 7F681F71, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    3.836000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.836000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.836000] ACPI: SSDT 7F68237C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    3.836000] ACPI: SSDT 7F682137, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    3.836000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.836000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.840000] ACPI: Thermal Zone [THM] (63 C)
[    4.480000] usbcore: registered new interface driver usbfs
[    4.480000] usbcore: registered new interface driver hub
[    4.480000] usbcore: registered new device driver usb
[    4.480000] USB Universal Host Controller Interface driver v3.0
[    4.480000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[    4.480000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.480000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.480000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.480000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    4.480000] usb usb1: configuration #1 chosen from 1 choice
[    4.480000] hub 1-0:1.0: USB hub found
[    4.480000] hub 1-0:1.0: 2 ports detected
[    4.508000] SCSI subsystem initialized
[    4.516000] libata version 2.21 loaded.
[    4.584000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
[    4.584000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.584000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.584000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.584000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    4.584000] usb usb2: configuration #1 chosen from 1 choice
[    4.584000] hub 2-0:1.0: USB hub found
[    4.584000] hub 2-0:1.0: 2 ports detected
[    4.688000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
[    4.688000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.688000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.688000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.688000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    4.688000] usb usb3: configuration #1 chosen from 1 choice
[    4.688000] hub 3-0:1.0: USB hub found
[    4.688000] hub 3-0:1.0: 2 ports detected
[    4.792000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
[    4.792000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.792000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.792000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.792000] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    4.792000] usb usb4: configuration #1 chosen from 1 choice
[    4.792000] hub 4-0:1.0: USB hub found
[    4.792000] hub 4-0:1.0: 2 ports detected
[    4.824000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    4.900000] ata_piix 0000:00:1f.1: version 2.11
[    4.900000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[    4.900000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.900000] scsi0 : ata_piix
[    4.900000] scsi1 : ata_piix
[    4.900000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    4.900000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    4.968000] usb 1-2: configuration #1 chosen from 1 choice
[    4.972000] hub 1-2:1.0: USB hub found
[    4.976000] hub 1-2:1.0: 4 ports detected
[    5.000000] Clocksource tsc unstable (delta = -196691763 ns)
[    5.064000] ata1.00: ATA-7: SanDisk SSD UATA 5000 1.8, 1.26, max UDMA/100
[    5.064000] ata1.00: 61734912 sectors, multi 1: LBA48 
[    5.064000] ata1.00: limited to UDMA/33 due to 40-wire cable
[    5.072000] ata1.00: configured for UDMA/33
[    5.072000] ata2: port disabled. ignoring.
[    5.072000] scsi 0:0:0:0: Direct-Access     ATA      SanDisk SSD UATA 1.26 PQ: 0 ANSI: 5
[    5.072000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[    5.072000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.072000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.072000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    5.072000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.072000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    5.072000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    5.076000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.076000] usb usb5: configuration #1 chosen from 1 choice
[    5.076000] hub 5-0:1.0: USB hub found
[    5.076000] hub 5-0:1.0: 8 ports detected
[    5.084000] usb 1-2: USB disconnect, address 2
[    5.084000] sd 0:0:0:0: [sda] 61734912 512-byte hardware sectors (31608 MB)
[    5.084000] sd 0:0:0:0: [sda] Write Protect is off
[    5.084000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.084000] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    5.084000] sd 0:0:0:0: [sda] 61734912 512-byte hardware sectors (31608 MB)
[    5.084000] sd 0:0:0:0: [sda] Write Protect is off
[    5.084000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.084000] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    5.084000]  sda: sda1 sda2
[    5.084000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.092000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.180000] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 17 (level, low) -> IRQ 17
[    5.232000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[efbff800-efbfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.240000] tg3.c:v3.77 (May 31, 2007)
[    5.240000] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[    5.240000] PCI: Setting latency timer of device 0000:09:00.0 to 64
[    5.256000] eth0: Tigon3 [partno(BCM5752KFBG) rev 6002 PHY(5752)] (PCI Express) 10/100/1000Base-T Ethernet 00:18:8b:b3:9c:55
[    5.256000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    5.256000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    5.836000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[    5.968000] usb 5-6: configuration #1 chosen from 1 choice
[    6.208000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    6.360000] usb 1-2: configuration #1 chosen from 1 choice
[    6.360000] hub 1-2:1.0: USB hub found
[    6.364000] hub 1-2:1.0: 4 ports detected
[    6.512000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[644fc00008207fff]
[    6.696000] usb 1-2.3: new full speed USB device using uhci_hcd and address 4
[    6.808000] usb 1-2.3: configuration #1 chosen from 1 choice
[    6.808000] hub 1-2.3:1.0: USB hub found
[    6.812000] hub 1-2.3:1.0: 3 ports detected
[    7.124000] usb 1-2.3.1: new full speed USB device using uhci_hcd and address 5
[    7.260000] usb 1-2.3.1: configuration #1 chosen from 1 choice
[    7.468000] usb 1-2.3.2: new full speed USB device using uhci_hcd and address 6
[    7.584000] usb 1-2.3.2: configuration #1 chosen from 1 choice
[   13.876000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.076000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.288000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.292000] agpgart: Detected an Intel 945GM Chipset.
[   14.296000] agpgart: Detected 7932K stolen memory.
[   14.312000] agpgart: AGP aperture is 256M @ 0xd0000000
[   14.452000] sdhci: Secure Digital Host Controller Interface driver
[   14.452000] sdhci: Copyright(c) Pierre Ossman
[   14.452000] sdhci: SDHCI controller found at 0000:02:01.2 [1180:0822] (rev 18)
[   14.452000] ACPI: PCI Interrupt 0000:02:01.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.456000] mmc0: SDHCI at 0xefbff700 irq 18 DMA
[   14.516000] iTCO_vendor_support: vendor-support=0
[   14.516000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.516000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   14.516000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.536000] intel_rng: FWH not detected
[   14.788000] input: PC Speaker as /class/input/input2
[   14.812000] usbcore: registered new interface driver libusual
[   14.820000] mmcblk0: mmc0:1234 SD08G 8003584KiB 
[   14.820000]  mmcblk0: p1
[   14.832000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.832000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.836000] Initializing USB Mass Storage driver...
[   14.836000] scsi2 : SCSI emulation for USB Mass Storage devices
[   14.840000] usbcore: registered new interface driver usb-storage
[   14.840000] USB Mass Storage support registered.
[   14.840000] usb-storage: device found at 3
[   14.840000] usb-storage: waiting for device to settle before scanning
[   14.908000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:01d6]
[   15.036000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
[   15.036000] Socket status: 30000006
[   15.036000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   15.036000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   15.036000] cs: IO port probe 0x2000-0x2fff: clean.
[   15.036000] pcmcia: parent PCI bridge Memory window: 0xefb00000 - 0xefbfffff
[   15.036000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   15.116000] input: PS/2 Mouse as /class/input/input3
[   15.136000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   15.292000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   15.292000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.332000] cs: IO port probe 0x100-0x3af: clean.
[   15.332000] cs: IO port probe 0x3e0-0x4ff: clean.
[   15.332000] cs: IO port probe 0x820-0x8ff: clean.
[   15.332000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.336000] cs: IO port probe 0xa00-0xaff: clean.
[   15.904000] lp: driver loaded but no devices found
[   19.840000] usb-storage: device scan complete
[   19.840000] scsi 2:0:0:0: CD-ROM            MATSHITA CDRW/DVD UJDA740 1.03 PQ: 0 ANSI: 0
[   19.840000] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[   19.876000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   19.876000] Uniform CD-ROM driver Revision: 3.20
[   19.876000] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   25.436000] ACPI: AC Adapter [AC] (on-line)
[   25.540000] ACPI: Battery Slot [BAT0] (battery present)
[   25.564000] ACPI: ACPI Dock Station Driver 
[   25.612000] input: Lid Switch as /class/input/input5
[   25.612000] ACPI: Lid Switch [LID]
[   25.612000] input: Power Button (CM) as /class/input/input6
[   25.612000] ACPI: Power Button (CM) [PBTN]
[   25.612000] input: Sleep Button (CM) as /class/input/input7
[   25.612000] ACPI: Sleep Button (CM) [SBTN]
[   25.868000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.868000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   26.892000] ppdev: user-space parallel port driver
[   27.000000] audit(1195121940.784:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5090 profile="/usr/sbin/cupsd"
[   27.044000] apm: BIOS not found.
[   27.292000] Failure registering capabilities with primary security module.
[   27.556000] Bluetooth: Core ver 2.11
[   27.556000] NET: Registered protocol family 31
[   27.556000] Bluetooth: HCI device and connection manager initialized
[   27.556000] Bluetooth: HCI socket layer initialized
[   27.576000] Bluetooth: L2CAP ver 2.8
[   27.576000] Bluetooth: L2CAP socket layer initialized
[   27.600000] Bluetooth: RFCOMM socket layer initialized
[   27.600000] Bluetooth: RFCOMM TTY layer initialized
[   27.600000] Bluetooth: RFCOMM ver 1.8
[   29.044000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   29.044000] tg3: eth0: Flow control is on for TX and on for RX.
[   32.212000] NET: Registered protocol family 17
[   32.464000] [drm] Initialized drm 1.1.0 20060810
[   32.468000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.472000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   36.456000] NET: Registered protocol family 10
[   36.456000] lo: Disabled Privacy Extensions
[   46.720000] eth0: no IPv6 routers present
[  153.536000] UDF-fs: No VRS found
[  153.572000] ISO 9660 Extensions: Microsoft Joliet Level 3
[  153.620000] ISO 9660 Extensions: RRIP_1991A
[  338.700000] tg3: eth0: Link is down.
[  384.752000] usb 5-6: USB disconnect, address 3
[  397.588000] ath_hal: module license 'Proprietary' taints kernel.
[  397.588000] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[  397.604000] wlan: 0.8.4.2 (svn r2852)
[  397.608000] ath_pci: 0.9.4.5 (svn r2852)
[  397.608000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  397.608000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[  397.748000] ath_pci: switching rfkill capability off
[  397.756000] ath_rate_sample: 1.2 (svn r2852)
[  397.756000] ath_pci: switching per-packet transmit power control off
[  397.756000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  397.756000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[  397.756000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  397.756000] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  397.756000] wifi0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  397.756000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[  397.756000] wifi0: mac 12.10 phy 8.1 radio 12.0
[  397.756000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[  397.756000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[  397.756000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[  397.756000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[  397.756000] wifi0: Use hw queue 8 for CAB traffic
[  397.756000] wifi0: Use hw queue 9 for beacons
[  397.768000] wifi0: Atheros 5418: mem=0xefdf0000, irq=17
[  512.280000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  512.280000] tg3: eth0: Flow control is on for TX and on for RX.
[  512.284000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  528.544000] eth0: no IPv6 routers present






I am stumped and I do not want to go back to using the IPW3945 so anybody have any ideas? Also I notice that when I reboot there is a new wifi device created (ath0, ath1, ath2, ath3, ath4 etc . . . .) under iwconfig. What is going on?

---

