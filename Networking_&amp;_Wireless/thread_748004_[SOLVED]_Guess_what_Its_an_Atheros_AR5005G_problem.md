---
title: "[SOLVED] Guess what? Its an Atheros AR5005G problem!"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by gaz51 on 2008-04-07
Hello all, 
I'm having a mare trying to get my wifi to connect. My friend installed ubuntu 7.04 on my Fujitsu Siemens Amilo laptop on a partition of the harddrive. Windows XP Home is still operating and has full wifi connectivity. I really like the feel of ubuntu but obviously wont remove the windows partition until i have it all up n running in ubuntu. 
I have, (yesterday) upgraded to 7.10 via download .... ethernet connection works fine in ubuntu .... in the hope this would resolve the issue, but alas not. 
I've also waded my way through reams of info on this matter from this forum but it either doesn't work or i'm getting lost in the explanations (entirely possibly given i'm far from a computer expert).

From what i've read so far you might find the following info useful:

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

dmesg:
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000017ea0000 - 0000000017eaf000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017eaf000 - 0000000017f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017f00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 382MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7f10
[    0.000000] Entering add_active_range(0, 0, 97952) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    97952
[    0.000000]   HighMem     97952 ->    97952
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    97952
[    0.000000] On node 0 totalpages: 97952
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 733 pages used for memmap
[    0.000000]   Normal zone: 93123 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7EE0 checksum 0
[    0.000000] ACPI: RSDP 000F7EE0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 17EAA49F, 0034 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 17EAEDDE, 0074 (r1 FUJ    W37       6040000 W37     F4240)
[    0.000000] ACPI: DSDT 17EAA4D3, 490B (r1 FUJ    W37       6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 17EAFFC0, 0040
[    0.000000] ACPI: SSDT 17EAEE52, 0118 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 17EAEF6A, 005A (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 17EAEFC4, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 97187
[    0.000000] Kernel command line: root=UUID=215f1ec2-8f46-42a1-8608-641db237d39e ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 800.095 MHz processor.
[   57.572424] Console: colour VGA+ 80x25
[   57.572815] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   57.573262] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   57.587162] Memory: 376700k/391808k available (2015k kernel code, 14460k reserved, 915k data, 364k init, 0k highmem)
[   57.587186] virtual kernel memory layout:
[   57.587188]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   57.587191]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   57.587194]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   57.587198]     lowmem  : 0xc0000000 - 0xd7ea0000   ( 382 MB)
[   57.587201]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   57.587204]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   57.587207]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   57.587213] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   57.587282] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   57.667260] Calibrating delay using timer specific routine.. 1602.33 BogoMIPS (lpj=3204664)
[   57.667304] Security Framework v1.0.0 initialized
[   57.667314] SELinux:  Disabled at boot.
[   57.667341] Mount-cache hash table entries: 512
[   57.667536] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   57.667554] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   57.667560] CPU: L2 Cache: 1024K (64 bytes/line)
[   57.667566] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   57.667583] Compat vDSO mapped to ffffe000.
[   57.667601] Checking 'hlt' instruction... OK.
[   57.683452] SMP alternatives: switching to UP code
[   57.683733] Freeing SMP alternatives: 11k freed
[   57.684223] Early unpacking initramfs... done
[   58.396543] ACPI: Core revision 20070126
[   58.396680] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   58.403134] CPU0: AMD Mobile AMD Athlon(tm) 64 Processor 3400+ stepping 02
[   58.403169] Total of 1 processors activated (1602.33 BogoMIPS).
[   58.403363] ENABLING IO-APIC IRQs
[   58.403603] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   58.443322] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   58.443379] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   58.443384] ...trying to set up timer as Virtual Wire IRQ... works.
[   58.590670] Brought up 1 CPUs
[   58.590845] Booting paravirtualized kernel on bare hardware
[   58.590953] Time:  8:45:49  Date: 03/07/108
[   58.590987] NET: Registered protocol family 16
[   58.591115] EISA bus registered
[   58.591135] ACPI: bus type pci registered
[   58.618603] PCI: PCI BIOS revision 2.10 entry at 0xfd6ac, last bus=2
[   58.618607] PCI: Using configuration type 1
[   58.618611] Setting up standard PCI resources
[   58.621591] ACPI: EC: Look up EC in DSDT
[   58.623409] ACPI: EC: GPE=0x03, ports=0x66, 0x62
[   58.663410] ACPI: Interpreter enabled
[   58.663415] ACPI: (supports S0 S3 S4 S5)
[   58.663442] ACPI: Using IOAPIC for interrupt routing
[   58.684382] ACPI: EC: GPE=0x03, ports=0x66, 0x62
[   58.684461] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   58.684478] PCI: Probing PCI hardware (bus 00)
[   58.686276] PCI: Transparent bridge - 0000:00:14.4
[   58.686418] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   58.686724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   58.686968] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   58.690990] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   58.691202] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   58.691410] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   58.691618] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   58.691825] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   58.692032] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   58.692238] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   58.692448] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   58.692614] Linux Plug and Play Support v0.97 (c) Adam Belay
[   58.692630] pnp: PnP ACPI init
[   58.692643] ACPI: bus type pnp registered
[   58.702762] pnp: PnP ACPI: found 10 devices
[   58.702767] ACPI: ACPI bus type pnp unregistered
[   58.702774] PnPBIOS: Disabled by ACPI PNP
[   58.702847] PCI: Using ACPI for IRQ routing
[   58.702853] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   58.714562] NET: Registered protocol family 8
[   58.714567] NET: Registered protocol family 20
[   58.714652] pnp: 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   58.714660] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   58.714667] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   58.714683] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   58.714690] pnp: 00:08: ioport range 0x1200-0x120f has been reserved
[   58.714696] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   58.714702] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   58.714712] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   58.714720] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   58.714726] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   58.718524] Time: tsc clocksource has been installed.
[   58.745201] PCI: Bridge: 0000:00:01.0
[   58.745206]   IO window: 9000-9fff
[   58.745212]   MEM window: c0100000-c01fffff
[   58.745219]   PREFETCH window: c8000000-cfffffff
[   58.745236] PCI: Bus 3, cardbus bridge: 0000:02:09.0
[   58.745241]   IO window: 0000a400-0000a4ff
[   58.745250]   IO window: 0000a800-0000a8ff
[   58.745259]   PREFETCH window: 30000000-33ffffff
[   58.745271]   MEM window: 34000000-37ffffff
[   58.745279] PCI: Bridge: 0000:00:14.4
[   58.745285]   IO window: a000-afff
[   58.745295]   MEM window: c0200000-c02fffff
[   58.745304]   PREFETCH window: 30000000-33ffffff
[   58.745358] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 20 (level, low) -> IRQ 16
[   58.745386] NET: Registered protocol family 2
[   58.782531] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   58.782597] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   58.782871] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   58.783059] TCP: Hash tables configured (established 16384 bind 16384)
[   58.783065] TCP reno registered
[   58.794675] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   59.471848]  it is
[   60.196418] Freeing initrd memory: 7110k freed
[   60.197084] audit: initializing netlink socket (disabled)
[   60.197104] audit(1207557948.992:1): initialized
[   60.200522] VFS: Disk quotas dquot_6.5.1
[   60.200609] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   60.200759] io scheduler noop registered
[   60.200764] io scheduler anticipatory registered
[   60.200768] io scheduler deadline registered
[   60.200803] io scheduler cfq registered (default)
[   60.200818] PCI: MSI quirk detected. MSI deactivated.
[   60.633196] Boot video device is 0000:01:05.0
[   60.633448] isapnp: Scanning for PnP cards...
[   60.988447] isapnp: No Plug & Play device found
[   61.035171] Real Time Clock Driver v1.12ac
[   61.035323] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   61.036320] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   61.036335] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   61.037274] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   61.037602] input: Macintosh mouse button emulation as /class/input/input0
[   61.037721] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   61.038689] i8042.c: Detected active multiplexing controller, rev 1.1.
[   61.038783] serio: i8042 KBD port at 0x60,0x64 irq 1
[   61.038791] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   61.038797] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   61.038803] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   61.038808] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   61.039095] mice: PS/2 mouse device common for all mice
[   61.039423] EISA: Probing bus 0 at eisa.0
[   61.039437] Cannot allocate resource for EISA slot 1
[   61.039476] Cannot allocate resource for EISA slot 8
[   61.039481] EISA: Detected 0 cards.
[   61.039632] TCP cubic registered
[   61.039654] NET: Registered protocol family 1
[   61.039692] Using IPI No-Shortcut mode
[   61.039957]   Magic number: 4:594:775
[   61.039964]   hash matches device psaux
[   61.040689] Freeing unused kernel memory: 364k freed
[   61.076883] input: AT Translated Set 2 keyboard as /class/input/input1
[   62.427632] AppArmor: AppArmor initialized<5>audit(1207557951.492:2):  type=1505 info="AppArmor initialized" pid=1206
[   62.438339] fuse init (API version 7.8)
[   62.446234] Failure registering capabilities with primary security module.
[   62.465065] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    4.760000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.764000] Time: acpi_pm clocksource has been installed.
[    4.808000] ACPI: Thermal Zone [TZS0] (26 C)
[    4.836000] ACPI: Thermal Zone [TZS2] (26 C)
[    5.684000] usbcore: registered new interface driver usbfs
[    5.684000] usbcore: registered new interface driver hub
[    5.684000] usbcore: registered new device driver usb
[    5.688000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.688000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[    5.688000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.688000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    5.688000] ohci_hcd 0000:00:13.0: irq 18, io mem 0xc0000000
[    5.780000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    5.780000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    5.788000] usb usb1: configuration #1 chosen from 1 choice
[    5.788000] hub 1-0:1.0: USB hub found
[    5.788000] hub 1-0:1.0: 4 ports detected
[    5.892000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[    5.892000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.892000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    5.892000] ohci_hcd 0000:00:13.1: irq 18, io mem 0xc0001000
[    5.896000] 8139too Fast Ethernet driver 0.9.28
[    5.952000] usb usb2: configuration #1 chosen from 1 choice
[    5.952000] hub 2-0:1.0: USB hub found
[    5.952000] hub 2-0:1.0: 4 ports detected
[    6.056000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[    6.056000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    6.056000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    6.056000] ehci_hcd 0000:00:13.2: irq 18, io mem 0xc0002000
[    6.056000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.056000] usb usb3: configuration #1 chosen from 1 choice
[    6.056000] hub 3-0:1.0: USB hub found
[    6.056000] hub 3-0:1.0: 8 ports detected
[    6.160000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    6.160000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[    6.160000] ATIIXP: chipset revision 0
[    6.160000] ATIIXP: not 100% native mode: will probe irqs later
[    6.160000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[    6.160000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[    6.160000] Probing IDE interface ide0...
[    6.448000] hda: ST9100825A, ATA DISK drive
[    7.120000] hda: selected mode 0x45
[    7.120000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.192000] Probing IDE interface ide1...
[    7.932000] hdc: _NEC DVD+/-RW ND-6650A, ATAPI CD/DVD-ROM drive
[    8.604000] hdc: selected mode 0x42
[    8.604000] ide1 at 0x170-0x177,0x376 on irq 15
[    8.624000] SCSI subsystem initialized
[    8.632000] libata version 2.21 loaded.
[    8.636000] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 23 (level, low) -> IRQ 20
[    8.636000] eth0: RealTek RTL8139 at 0xd8840000, 00:0a:e4:ab:5f:5f, IRQ 20
[    8.636000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    8.640000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    8.640000] ACPI: PCI Interrupt 0000:02:09.2[C] -> GSI 21 (level, low) -> IRQ 21
[    8.688000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[c0216800-c0216fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    8.708000] hda: max request size: 512KiB
[    8.720000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[    8.724000] hda: cache flushes supported
[    8.724000]  hda: hda1 hda2 hda3
[    8.872000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[    8.872000] Uniform CD-ROM driver Revision: 3.20
[    9.072000] Attempting manual resume
[    9.072000] swsusp: Resume From Partition 3:3
[    9.072000] PM: Checking swsusp image.
[    9.072000] PM: Resume from disk failed.
[    9.128000] kjournald starting.  Commit interval 5 seconds
[    9.128000] EXT3-fs: mounted filesystem with ordered data mode.
[    9.960000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae40532104196]
[   23.240000] Linux agpgart interface v0.102 (c) Dave Jones
[   23.644000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.724000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.776000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   24.264000] ath_hal: module license 'Proprietary' taints kernel.
[   24.264000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   24.868000] Yenta: CardBus bridge found at 0000:02:09.0 [1734:1092]
[   24.868000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   24.868000] Yenta: Routing CardBus interrupts to PCI
[   24.868000] Yenta TI: socket 0000:02:09.0, mfunc 0x010a1b22, devctl 0x64
[   25.100000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
[   25.100000] Socket status: 30000006
[   25.100000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   25.100000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   25.100000] cs: IO port probe 0xa000-0xafff: clean.
[   25.100000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   25.100000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   26.148000] wlan: 0.8.4.2 (0.9.3.2)
[   26.196000] ath_pci: 0.9.4.5 (0.9.3.2)
[   26.196000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 16
[   26.840000] input: PC Speaker as /class/input/input2
[   26.968000] ath_rate_sample: 1.2 (0.9.3.2)
[   26.968000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   26.968000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   26.968000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   26.968000] wifi0: mac 7.8 phy 4.5 radio 5.6
[   26.968000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   26.968000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   26.968000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   26.968000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   26.968000] wifi0: Use hw queue 8 for CAB traffic
[   26.968000] wifi0: Use hw queue 9 for beacons
[   27.136000] wifi0: Atheros 5212: mem=0xc0200000, irq=16
[   27.360000] ACPI: PCI Interrupt 0000:02:09.3[A] -> GSI 20 (level, low) -> IRQ 16
[   27.364000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x92a0b1, caps: 0xa04713/0x200000
[   27.392000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   27.684000] cs: IO port probe 0x100-0x3af: clean.
[   27.688000] cs: IO port probe 0x3e0-0x4ff: clean.
[   27.688000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   27.692000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   27.692000] cs: IO port probe 0xa00-0xaff: clean.
[   27.760000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   27.872000] MC'97 1 converters and GPIO not ready (0xff00)
[   27.872000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   29.040000] lp: driver loaded but no devices found
[   29.128000] Adding 979956k swap on /dev/hda3.  Priority:-1 extents:1 across:979956k
[  168.700000] EXT3 FS on hda2, internal journal
[  171.960000] ACPI: Battery Slot [BAT0] (battery present)
[  172.024000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  172.024000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  172.048000] No dock devices found.
[  172.172000] ACPI: AC Adapter [ADP1] (on-line)
[  172.324000] input: Power Button (FF) as /class/input/input4
[  172.324000] ACPI: Power Button (FF) [PWRF]
[  172.364000] input: Lid Switch as /class/input/input5
[  172.364000] ACPI: Lid Switch [LID0]
[  172.412000] input: Sleep Button (CM) as /class/input/input6
[  172.412000] ACPI: Sleep Button (CM) [SLPB]
[  172.964000] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3400+ processors (version 2.00.00)
[  172.964000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[  172.964000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[  172.964000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[  172.964000] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0xe
[  172.964000] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[  173.516000] Clocksource tsc unstable (delta = 874830736 ns)
[  176.104000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  177.124000] ppdev: user-space parallel port driver
[  178.060000] audit(1207554525.973:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4852 profile="/usr/sbin/cupsd"
[  178.524000] apm: BIOS not found.
[  179.316000] [fglrx] Maximum main memory to use for locked dma buffers: 313 MBytes.
[  179.316000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[  179.336000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[  181.928000] Failure registering capabilities with primary security module.
[  182.644000] [fglrx] total      GART = 130023424
[  182.644000] [fglrx] free       GART = 114032640
[  182.644000] [fglrx] max single GART = 114032640
[  182.644000] [fglrx] total      LFB  = 134217728
[  182.644000] [fglrx] free       LFB  = 119828480
[  182.644000] [fglrx] max single LFB  = 119828480
[  182.644000] [fglrx] total      Inv  = 0
[  182.644000] [fglrx] free       Inv  = 0
[  182.644000] [fglrx] max single Inv  = 0
[  182.644000] [fglrx] total      TIM  = 0
[  183.228000] Bluetooth: Core ver 2.11
[  183.228000] NET: Registered protocol family 31
[  183.228000] Bluetooth: HCI device and connection manager initialized
[  183.228000] Bluetooth: HCI socket layer initialized
[  183.388000] Bluetooth: L2CAP ver 2.8
[  183.388000] Bluetooth: L2CAP socket layer initialized
[  183.636000] Bluetooth: RFCOMM socket layer initialized
[  183.636000] Bluetooth: RFCOMM TTY layer initialized
[  183.636000] Bluetooth: RFCOMM ver 1.8
[  187.488000] NET: Registered protocol family 17
[  189.436000] NET: Registered protocol family 10
[  189.436000] lo: Disabled Privacy Extensions
[  199.856000] ath0: no IPv6 routers present
[  199.972000] eth0: no IPv6 routers present
[ 1351.796000] APIC error on CPU0: 00(40)
[ 1364.396000] eth0: link down
[ 1565.156000] ath0: no IPv6 routers present
[ 1948.576000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1962.996000] eth0: no IPv6 routers present
[ 2162.196000] ACPI: PCI interrupt for device 0000:02:05.0 disabled
[ 2162.196000] ath_pci: driver unloaded
[ 2763.176000] eth0: link down
[ 2839.260000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2839.260000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2852.896000] eth0: no IPv6 routers present
[ 3916.168000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3934.508000] eth0: no IPv6 routers present
[ 4232.532000] eth0: link down
[ 4413.172000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 4413.172000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4427.396000] eth0: no IPv6 routers present

lshw -C network
 *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:ab:5f:5f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=82.23.23.110 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

I hope this gives you guys something to go on, 'cos I'm pulling my hair out here.

I see the driver doesn't mention ndiswrapper or madwifi so i'll look into installing these as a start - if i can find out how.

Any help very gratefully accepted.

---

### Post by gaz51 on 2008-04-07
Right.
installed - i think? - a suitable driver via synaptic for the kernal I'm using (2.6.22-14 generic) and rebooted. Although the driver details in lshw -C network haven't changed, i can now see my wireless network, but it wont let me join even though I'm entering the corrrect WEP details when requested. 
Any ideas?

---

### Post by gaz51 on 2008-04-07
Here's the latest iwconfig / lshw -C network info. Still "seeing" the available wireless networks but wont join. ??? 
I haven't installed the relevant ndiswrapper 'cos i can't tell which one i'm meant to install from the website, so don't know if that is what's causing the problem. 
Or is it something as basic as my settings?

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"default"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:10:73:0A:A1:6A   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-99 dBm  Noise level=-99 dBm
          Rx invalid nwid:37635  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



lshw -C network:
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: wifi0
       version: 01
       serial: 00:02:e3:45:ee:c4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:ab:5f:5f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

---

### Post by davejrice on 2008-04-07
Gaz,

looks like everything is installed ok - as long as the driver is fully working  - there are issues with your card as we know!

first thing to try is turn off WEP temporarily on the router and try connecting with no security.  That takes away a layer of configuration.  could you also pop the output of
```

lspci

```
here so we can be sure exactly what sort of atheros card it is.

cheers

;)

---

### Post by gaz51 on 2008-04-07
No luck with WEP disabled.

lspci:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
02:05.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

This is just silly... it shouldn't be this difficult! Just want to get it sorted 'cos it's like having unfinished work... it just winds me up. Plus, i want to wipe my mrs' computer and install ubuntu on there, but i wont try that til i've got this sorted. Grrrrr, n all that. 
Oh, by the way, Nutty came off his bike yesterday. He's ok, but new bike is trashed. Mustn't snigger now!

---

### Post by kevdog on 2008-04-07
How are you trying to connect?? What program or at the command line?

Can you post iwlist scan?

---

### Post by gaz51 on 2008-04-08
Thanks for taking the time Kevdog, you seem to almost single-handedly help out on these issues. 

I try to connect by using the network button, top right, next to battery status. When i left click it, it drops down a menu of available wireless networks and i click on my one. It then asks for WEP details which i give but it fails to connect. As you see I've tried it with switching off the WEP at the router, but it still wont join. 
I've also tried to manually configure it, but no joy.

Here's the iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0F:B5:69:51:54
                    ESSID:"NETGEARWGT624"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-47 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f010100060000
          Cell 02 - Address: 00:18:F8:39:55:D9
                    ESSID:"linksys_SES_58855"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/70  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

My Network is CELL 01 - NETGEAR. 

Don't get it. If i can see the network, why wont it join? Is there another way to try to connect?

---

### Post by kevdog on 2008-04-08
The face you can see your network is a good sign.

Is this your network?
ESSID:"linksys_SES_58855"

Can you try connecting through the command line?
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

Of course your interface is ath0

With the WEP setup in the router, can you explain it to me just a little.  Are you using a key index or is it simply a ascii password?  How many characters in length? Is your wep open or shared key?

---

### Post by gaz51 on 2008-04-08
No joy. Tried it twice, once with the WEP control on the router set to on, and then with the WEP off to see if that would make a difference. Failed to connect both times. Here's the results with the WEP off:

There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:02:e3:45:ee:c4
Sending on   LPF/ath0/00:02:e3:45:ee:c4
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I'm now connected to the router via ethernet and here's my current iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEARWGT624"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:2170  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and lshw -C network:

 *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: wifi0
       version: 01
       serial: 00:02:e3:45:ee:c4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:ab:5f:5f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.4 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

and ifconfig:
ath0      Link encap:Ethernet  HWaddr 00:02:E3:45:EE:C4  
          inet6 addr: fe80::202:e3ff:fe45:eec4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:02:E3:45:EE:C4  
          inet addr:169.254.10.36  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:0A:E4:AB:5F:5F  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:feab:5f5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:968522 (945.8 KB)  TX bytes:184940 (180.6 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-02-E3-45-EE-C4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4819 errors:0 dropped:0 overruns:0 frame:271
          TX packets:2283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:416716 (406.9 KB)  TX bytes:111440 (108.8 KB)
          Interrupt:16 

I cant understand it. I've got an ASUS eeePC which is running ubuntu with an atheros card with no problems - obviously a different chipset, but nonetheless, if that can work why cant this. What about anotherdebian platform - might it better on one of those, say kubuntu or something??

---

### Post by gaz51 on 2008-04-08
Yea, solved. Well, my mate Dave solved it anyway. davejrice (above). Quite straight forward in the end. 

Follow the link below

[http://wiki.eeeuser.com/ubuntu](http://wiki.eeeuser.com/ubuntu)

and follow the instructions under the section: Wireless internet using native Madwifi drivers. It gives a step by step guide on installing the drivers for the 5007 but seems to work on the 5005g too. 

Oh happy days. I can finally cast off the money-grabbing shackles that is Windows!

Thanks to all who helped. Keep the the good fight!

---

