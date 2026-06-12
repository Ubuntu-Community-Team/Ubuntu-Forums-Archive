---
title: "C300A/Abit BH6 Xubuntu box won't see wireless card"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Robotech_Master on 2007-12-19
I have an old computer that I've been setting up with Xubuntu Linux 7.10 as a Christmas surprise for my Dad. It's an old old Celeron 300A, with 192 megs of RAM and an Abit BH-6 motherboard.

The wireless card I put in is a Dynex DX-WGDTC, which is, according to the reviews I find on the 'net, supposed to be one of the best wireless cards it's possible to get for Linux, and it's supposed to work for Ubuntu right out of the box. And in the Xubuntu box it used to be in, my newer Athlon 2600+ machine, it did indeed work.

But in this older one, Xubuntu won't notice it at all, either the installation on the hard drive or if I boot the CD as a LiveCD. When I do a lspci on the machine it doesn't even notice the card is there, and I've tried it in three different slots, including one that I took its working wired Ethernet card out of a moment ago. And I've verified that the wireless card still works by remounting it in my newer Linux box, and it detected it just fine.

(Unfortunately the old machine isn't currently connected to the Internet at the moment, as it's a room away from my Ethernet box, so I can't copy and paste stuff. I guess I'll have to move it back tomorrow so I can.)

Is the mobo just too old to work with this kind of card? Or is there something else I need to do to get it to work? Any alternate wireless solutions for the old Abit?

---

### Post by Robotech_Master on 2007-12-21
Here's the lspci:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04)


Here's the dmesg:

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000c000000 (usable)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 192MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 49152) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    49152
[    0.000000]   HighMem     49152 ->    49152
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    49152
[    0.000000] On node 0 totalpages: 49152
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 352 pages used for memmap
[    0.000000]   Normal zone: 44704 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3ff0000)
[    0.000000] Built 1 zonelists.  Total pages: 48768
[    0.000000] Kernel command line: root=UUID=467b13e0-1a0f-46ab-85f7-738cf2d74b63 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0118c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 451.042 MHz processor.
[   37.742619] Console: colour VGA+ 80x25
[   37.743321] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   37.744065] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   37.769840] Memory: 183180k/196608k available (2015k kernel code, 12976k reserved, 916k data, 364k init, 0k highmem)
[   37.769886] virtual kernel memory layout:
[   37.769891]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   37.769898]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   37.769905]     vmalloc : 0xcc800000 - 0xff7fe000   ( 815 MB)
[   37.769911]     lowmem  : 0xc0000000 - 0xcc000000   ( 192 MB)
[   37.769918]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   37.769924]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   37.769931]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   37.769946] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   37.770087] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   37.850118] Calibrating delay using timer specific routine.. 903.06 BogoMIPS (lpj=1806128)
[   37.850214] Security Framework v1.0.0 initialized
[   37.850239] SELinux:  Disabled at boot.
[   37.850298] Mount-cache hash table entries: 512
[   37.850751] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   37.850798] CPU: L1 I cache: 16K, L1 D cache: 16K
[   37.850810] CPU: L2 cache: 128K
[   37.850822] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   37.850867] Compat vDSO mapped to ffffe000.
[   37.850916] Checking 'hlt' instruction... OK.
[   37.866218] SMP alternatives: switching to UP code
[   37.866848] Freeing SMP alternatives: 11k freed
[   37.867987] Early unpacking initramfs... done
[   39.353461] CPU0: Intel Celeron (Mendocino) stepping 00
[   39.353486] SMP motherboard not detected.
[   39.353496] Local APIC not detected. Using dummy APIC emulation.
[   39.353663] Brought up 1 CPUs
[   39.354151] Booting paravirtualized kernel on bare hardware
[   39.354336] Time:  1:25:38  Date: 11/22/107
[   39.354437] NET: Registered protocol family 16
[   39.354850] EISA bus registered
[   39.385357] PCI: PCI BIOS revision 2.10 entry at 0xfb460, last bus=1
[   39.385369] PCI: Using configuration type 1
[   39.385378] Setting up standard PCI resources
[   39.390450] ACPI: Interpreter disabled.
[   39.390470] Linux Plug and Play Support v0.97 (c) Adam Belay
[   39.390514] pnp: PnP ACPI: disabled
[   39.390530] PnPBIOS: Scanning system for PnP BIOS support...
[   39.391067] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc000
[   39.391089] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc028, dseg 0xf0000
[   39.396218] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   39.396461] PCI: Probing PCI hardware
[   39.396484] PCI: Probing PCI hardware (bus 00)
[   39.397038] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   39.397046] * this clock source is slow. Consider trying other clock sources
[   39.397115] PCI quirk: region 4000-403f claimed by PIIX4 ACPI
[   39.397128] PCI quirk: region 5000-500f claimed by PIIX4 SMB
[   39.400570] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   39.419404] NET: Registered protocol family 8
[   39.419417] NET: Registered protocol family 20
[   39.419771] pnp: 00:07: iomem range 0x0-0x9ffff could not be reserved
[   39.419791] pnp: 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[   39.419806] pnp: 00:07: iomem range 0x100000-0xbffffff could not be reserved
[   39.419835] pnp: 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[   39.419850] pnp: 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[   39.419864] pnp: 00:08: iomem range 0xf8000-0xfffff could not be reserved
[   39.419878] pnp: 00:08: iomem range 0xc9000-0xcbfff has been reserved
[   39.421594] PCI: Bridge: 0000:00:01.0
[   39.421610]   IO window: d000-dfff
[   39.421624]   MEM window: e4000000-e5ffffff
[   39.421637]   PREFETCH window: e6000000-e6ffffff
[   39.421703] NET: Registered protocol family 2
[   39.421942] Time: tsc clocksource has been installed.
[   39.458121] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   39.458291] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[   39.458682] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   39.459085] TCP: Hash tables configured (established 8192 bind 8192)
[   39.459099] TCP reno registered
[   39.470500] checking if image is initramfs... it is
[   42.289371] Freeing initrd memory: 7358k freed
[   42.290676] audit: initializing netlink socket (disabled)
[   42.290724] audit(1198286741.156:1): initialized
[   42.302605] VFS: Disk quotas dquot_6.5.1
[   42.302955] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   42.303696] io scheduler noop registered
[   42.303711] io scheduler anticipatory registered
[   42.303720] io scheduler deadline registered
[   42.303839] io scheduler cfq registered (default)
[   42.303872] Limiting direct PCI/PCI transfers.
[   42.303930] Boot video device is 0000:01:00.0
[   42.304557] isapnp: Scanning for PnP cards...
[   42.659277] isapnp: No Plug & Play device found
[   42.861421] Real Time Clock Driver v1.12ac
[   42.861910] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   42.862111] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.862861] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   42.865988] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.867156] 00:10: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   42.871256] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   42.871918] input: Macintosh mouse button emulation as /class/input/input0
[   42.872344] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   42.875492] serio: i8042 KBD port at 0x60,0x64 irq 1
[   42.875516] serio: i8042 AUX port at 0x60,0x64 irq 12
[   42.876486] mice: PS/2 mouse device common for all mice
[   42.877100] EISA: Probing bus 0 at eisa.0
[   42.877148] Cannot allocate resource for EISA slot 4
[   42.877159] Cannot allocate resource for EISA slot 5
[   42.877188] EISA: Detected 0 cards.
[   42.877711] TCP cubic registered
[   42.877781] NET: Registered protocol family 1
[   42.877877] Using IPI No-Shortcut mode
[   42.878197]   Magic number: 3:168:408
[   42.880439] Freeing unused kernel memory: 364k freed
[   42.929746] input: AT Translated Set 2 keyboard as /class/input/input1
[   44.868070] AppArmor: AppArmor initialized<5>audit(1198286743.656:2):  type=1505 info="AppArmor initialized" pid=1061
[   44.900498] fuse init (API version 7.8)
[   44.925660] Failure registering capabilities with primary security module.
[   45.021219] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   47.602154] SCSI subsystem initialized
[   47.647344] libata version 2.21 loaded.
[   47.660514] ata_piix 0000:00:07.1: version 2.11
[   47.661163] scsi0 : ata_piix
[   47.661363] scsi1 : ata_piix
[   47.661481] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   47.661499] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   47.732327] usbcore: registered new interface driver usbfs
[   47.732416] usbcore: registered new interface driver hub
[   47.732530] usbcore: registered new device driver usb
[   47.739008] USB Universal Host Controller Interface driver v3.0
[   47.838962] ata1.00: ATA-4: WDC WD205BA, P76OA30A, max UDMA/66
[   47.838980] ata1.00: 40088160 sectors, multi 16: LBA 
[   47.840069] ata1.01: ATA-5: WDC WD300AB-00BVA0, 21.01H21, max UDMA/100
[   47.840085] ata1.01: 58633344 sectors, multi 16: LBA 
[   47.872187] ata1.00: configured for UDMA/33
[   47.886386] ata1.01: configured for UDMA/33
[   48.200296] 8139too Fast Ethernet driver 0.9.28
[   48.493187] ata2.00: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-106S 0122, E1.22, max UDMA/66
[   48.657136] ata2.00: configured for UDMA/33
[   48.664961] scsi 0:0:0:0: Direct-Access     ATA      WDC WD205BA      P76O PQ: 0 ANSI: 5
[   48.671132] scsi 0:0:1:0: Direct-Access     ATA      WDC WD300AB-00BV 21.0 PQ: 0 ANSI: 5
[   48.673080] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-ROM DVD-106  1.22 PQ: 0 ANSI: 5
[   48.688933] PCI: setting IRQ 10 as level-triggered
[   48.688950] PCI: Found IRQ 10 for device 0000:00:07.2
[   48.688979] PCI: Sharing IRQ 10 with 0000:00:09.0
[   48.689017] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   48.689418] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   48.689478] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000e000
[   48.690014] usb usb1: configuration #1 chosen from 1 choice
[   48.690137] hub 1-0:1.0: USB hub found
[   48.690177] hub 1-0:1.0: 2 ports detected
[   48.752943] sd 0:0:0:0: [sda] 40088160 512-byte hardware sectors (20525 MB)
[   48.753213] sd 0:0:0:0: [sda] Write Protect is off
[   48.753228] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   48.753323] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.753583] sd 0:0:0:0: [sda] 40088160 512-byte hardware sectors (20525 MB)
[   48.753636] sd 0:0:0:0: [sda] Write Protect is off
[   48.753649] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   48.753729] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.753751]  sda: sda1 sda2 sda3
[   48.794181] PCI: Found IRQ 10 for device 0000:00:09.0
[   48.794213] PCI: Sharing IRQ 10 with 0000:00:07.2
[   48.794752] eth0: RealTek RTL8139 at 0xcc80e000, 00:48:54:4b:d0:2c, IRQ 10
[   48.794765] eth0:  Identified 8139 chip type 'RTL-8139A'
[   48.806663] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   48.820770] sd 0:0:0:0: [sda] Attached SCSI disk
[   48.886618] sd 0:0:1:0: [sdb] 58633344 512-byte hardware sectors (30020 MB)
[   48.888973] sd 0:0:1:0: [sdb] Write Protect is off
[   48.888992] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   48.890987] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.891233] sd 0:0:1:0: [sdb] 58633344 512-byte hardware sectors (30020 MB)
[   48.891286] sd 0:0:1:0: [sdb] Write Protect is off
[   48.891299] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   48.891380] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.891396]  sdb: sdb1
[   48.912094] sd 0:0:1:0: [sdb] Attached SCSI disk
[   48.916877] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[   48.916894] Uniform CD-ROM driver Revision: 3.20
[   48.917848] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   48.959386] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   48.960257] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   48.961338] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   49.722141] Attempting manual resume
[   49.722157] swsusp: Resume From Partition 8:2
[   49.722166] PM: Checking swsusp image.
[   49.722587] PM: Resume from disk failed.
[   49.830465] kjournald starting.  Commit interval 5 seconds
[   49.830515] EXT3-fs: mounted filesystem with ordered data mode.
[   66.106231] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   66.116273] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   69.026509] gameport: EMU10K1 is pci0000:00:0b.1/gameport0, io 0xec00, speed 1217kHz
[   69.098847] Linux agpgart interface v0.102 (c) Dave Jones
[   69.116531] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   69.472194] agpgart: Detected an Intel 440BX Chipset.
[   69.477311] agpgart: AGP aperture is 64M @ 0xe0000000
[   69.489766] input: PC Speaker as /class/input/input2
[   70.127600] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   70.825387] nvidia: module license 'NVIDIA' taints kernel.
[   70.845887] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7185  Mon Apr  2 18:29:54 PDT 2007
[   70.969553] parport_pc 00:0e: reported by Plug and Play BIOS
[   70.969625] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   73.183090] PCI: setting IRQ 5 as level-triggered
[   73.183106] PCI: Found IRQ 5 for device 0000:00:0b.0
[   74.765671] lp0: using parport0 (interrupt-driven).
[   74.916695] Adding 1076344k swap on /dev/sda2.  Priority:-1 extents:1 across:1076344k
[   75.341996] EXT3 FS on sda3, internal journal
[   76.564998] kjournald starting.  Commit interval 5 seconds
[   76.566318] EXT3 FS on sda1, internal journal
[   76.566340] EXT3-fs: mounted filesystem with ordered data mode.
[   76.599275] kjournald starting.  Commit interval 5 seconds
[   76.605920] EXT3 FS on sdb1, internal journal
[   76.605942] EXT3-fs: mounted filesystem with ordered data mode.
[   81.338164] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   81.338631] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   81.339706] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   81.340268] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   84.713895] eth0: link down
[   85.122107] NET: Registered protocol family 10
[   85.123317] lo: Disabled Privacy Extensions
[   85.124236] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   85.655831] ppdev: user-space parallel port driver
[   85.855441] audit(1198286785.023:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4280 profile="/usr/sbin/cupsd"
[   85.998012] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   86.921125] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   87.261715] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   87.286576] NFSD: starting 90-second grace period
[   89.544734] Failure registering capabilities with primary security module.
[   92.372984] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   92.373425] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   92.373829] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   92.753321] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   92.753780] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   92.754188] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[ 1952.105966] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 1952.286219] usb 1-1: configuration #1 chosen from 1 choice
[ 1952.607837] usbcore: registered new interface driver libusual
[ 1952.848786] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 1952.849669] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 1952.884922] Initializing USB Mass Storage driver...
[ 1952.891943] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1952.900499] usb-storage: device found at 2
[ 1952.900517] usb-storage: waiting for device to settle before scanning
[ 1952.902044] usbcore: registered new interface driver usb-storage
[ 1952.902819] USB Mass Storage support registered.
[ 1957.899070] usb-storage: device scan complete
[ 1957.902123] scsi 2:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9407 PQ: 0 ANSI: 0
[ 1958.224886] sd 2:0:0:0: [sdc] 3935232 512-byte hardware sectors (2015 MB)
[ 1958.229904] sd 2:0:0:0: [sdc] Write Protect is off
[ 1958.229926] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1958.229938] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1958.241897] sd 2:0:0:0: [sdc] 3935232 512-byte hardware sectors (2015 MB)
[ 1958.246896] sd 2:0:0:0: [sdc] Write Protect is off
[ 1958.246919] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1958.246930] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1958.246948]  sdc: sdc1
[ 1958.253279] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[ 1958.253457] sd 2:0:0:0: Attached scsi generic sg3 type 0

---

