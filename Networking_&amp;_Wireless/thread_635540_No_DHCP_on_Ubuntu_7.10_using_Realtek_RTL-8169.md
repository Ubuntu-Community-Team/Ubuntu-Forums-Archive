---
title: "No DHCP on Ubuntu 7.10 using Realtek RTL-8169"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by shinobitux on 2007-12-08
Hey, I registered because after reading all the forum entries I still couldn't get my network card to work.

I'm running Ubuntu 7.10 and using a new gigabit Netgear network card using the Realtek RTL-8169 chipset. I'm not an expert at all, but here's what I've tried.

I done research and have found multiple problems with the dual-booting wake-on-lan settings. I've tried some proposed solutions like power down and unplug for 15 seconds.

I've compiled the realtek r8169 module and reinstalled it.

My link appears to be active, but I only get an "No DHCPOFFERS received" error.

I've attempted a proposed "ethtool -s eth0 duplex half speed 10 autoneg off" solution proposed on another forum. I've done this while the interface was up and I've brought the interface up after as well.

I haven't tried installing the r1000 module since I haven't seen much success with that on the forums.

I'm not trying to bother anybody, but I'd like to see if I can fix this issue. Is there anybody who has a  solution? If you'd like any additional information I've forgotten, just say so.

If you can find time to look at my problem, I'd really appreciate it. I've never posted on a forum before, so I apologize if I do this poorly. I'm going to include the output from dmesg, lsmod, ifconfig -a, a copy of my interfaces file, and a copy of my dhclient.conf.

```
dmesg:

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6860 checksum 0
[    0.000000] ACPI: RSDP 000F6860, 0014 (r0 AOPEN )
[    0.000000] ACPI: RSDT 3FFF3000, 0028 (r1 AOPEN  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 AOPEN  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF30C0, 34DF (r1 AOPEN  AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfff0000)
[    0.000000] Built 1 zonelists.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=e8686ee6-8274-4f91-9df5-cea7b9931573 ro
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0180e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.488 MHz processor.
[   25.032516] Console: colour VGA+ 80x25
[   25.035200] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.036712] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.073341] Memory: 1027880k/1048512k available (2015k kernel code, 19924k reserved, 916k data, 364k init, 131008k highmem)
[   25.073424] virtual kernel memory layout:
[   25.073425]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   25.073426]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.073428]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   25.073429]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   25.073430]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   25.073431]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   25.073433]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   25.073875] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.074037] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   25.154104] Calibrating delay using timer specific routine.. 3994.55 BogoMIPS (lpj=7989112)
[   25.154256] Security Framework v1.0.0 initialized
[   25.154321] SELinux:  Disabled at boot.
[   25.154394] Mount-cache hash table entries: 512
[   25.154644] CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[   25.154653] CPU: CLK_CTL MSR was 60031223. Reprogramming to 20031223
[   25.154714] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.154774] CPU: L2 Cache: 256K (64 bytes/line)
[   25.154831] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[   25.154846] Compat vDSO mapped to ffffe000.
[   25.154916] Checking 'hlt' instruction... OK.
[   25.170333] SMP alternatives: switching to UP code
[   25.170729] Freeing SMP alternatives: 11k freed
[   25.171194] Early unpacking initramfs... done
[   25.489234] ACPI: Core revision 20070126
[   25.489386] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.490854] ACPI: setting ELCR to 0200 (from 0ea0)
[   25.492811] CPU0: AMD Athlon(tm) XP 2400+ stepping 01
[   25.492963] SMP motherboard not detected.
[   25.493019] Local APIC not detected. Using dummy APIC emulation.
[   25.493126] Brought up 1 CPUs
[   25.493336] Booting paravirtualized kernel on bare hardware
[   25.493476] Time: 17:43:44  Date: 11/08/107
[   25.493565] NET: Registered protocol family 16
[   25.493737] EISA bus registered
[   25.493805] ACPI: bus type pci registered
[   25.535942] PCI: PCI BIOS revision 2.10 entry at 0xfb460, last bus=1
[   25.536001] PCI: Using configuration type 1
[   25.536056] Setting up standard PCI resources
[   25.544350] ACPI: EC: Look up EC in DSDT
[   25.547467] ACPI: Interpreter enabled
[   25.547528] ACPI: (supports S0 S1 S4 S5)
[   25.547805] ACPI: Using PIC for interrupt routing
[   25.551603] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.551677] PCI: Probing PCI hardware (bus 00)
[   25.552463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.568376] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   25.569112] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *7 10 11 12 14 15)
[   25.569837] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   25.570603] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   25.571291] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.571360] pnp: PnP ACPI init
[   25.571429] ACPI: bus type pnp registered
[   25.573754] pnp: PnP ACPI: found 12 devices
[   25.573812] ACPI: ACPI bus type pnp unregistered
[   25.573874] PnPBIOS: Disabled by ACPI PNP
[   25.574003] PCI: Using ACPI for IRQ routing
[   25.574061] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.597085] NET: Registered protocol family 8
[   25.597142] NET: Registered protocol family 20
[   25.597279] pnp: 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   25.597340] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   25.597400] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   25.597459] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   25.597959] Time: tsc clocksource has been installed.
[   25.627859] PCI: Bridge: 0000:00:01.0
[   25.627915]   IO window: disabled.
[   25.627973]   MEM window: e4000000-e6ffffff
[   25.628030]   PREFETCH window: d0000000-dfffffff
[   25.628101] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.628115] NET: Registered protocol family 2
[   25.666010] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.666310] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   25.669393] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.670500] TCP: Hash tables configured (established 131072 bind 65536)
[   25.670564] TCP reno registered
[   25.682124] checking if image is initramfs... it is
[   26.129826] Switched to high resolution mode on CPU 0
[   26.282521] Freeing initrd memory: 7054k freed
[   26.283060] audit: initializing netlink socket (disabled)
[   26.283134] audit(1197135825.028:1): initialized
[   26.283269] highmem bounce pool size: 64 pages
[   26.285320] VFS: Disk quotas dquot_6.5.1
[   26.285439] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.285610] io scheduler noop registered
[   26.285667] io scheduler anticipatory registered
[   26.285758] io scheduler deadline registered
[   26.285826] io scheduler cfq registered (default)
[   26.285896] PCI: VIA PCI bridge detected. Disabling DAC.
[   26.286027] Boot video device is 0000:01:00.0
[   26.286235] isapnp: Scanning for PnP cards...
[   26.640153] isapnp: No Plug & Play device found
[   26.671722] Real Time Clock Driver v1.12ac
[   26.671881] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.672045] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.672412] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.673325] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.673854] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.674808] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.675122] input: Macintosh mouse button emulation as /class/input/input0
[   26.675272] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   26.675678] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.675740] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.675968] mice: PS/2 mouse device common for all mice
[   26.676157] EISA: Probing bus 0 at eisa.0
[   26.676232] Cannot allocate resource for EISA slot 4
[   26.676304] EISA: Detected 0 cards.
[   26.676567] TCP cubic registered
[   26.676631] NET: Registered protocol family 1
[   26.676709] Using IPI No-Shortcut mode
[   26.676960]   Magic number: 3:126:744
[   26.677853] Freeing unused kernel memory: 364k freed
[   26.721689] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.886485] AppArmor: AppArmor initialized<5>audit(1197135825.528:2):  type=1505 info="AppArmor initialized" pid=1154
[   26.893773] fuse init (API version 7.8)
[   26.899166] Failure registering capabilities with primary security module.
[   26.910183] ACPI: Fan [FAN] (on)
[   26.915664] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   26.917366] ACPI: Thermal Zone [THRM] (36 C)
[   27.537367] usbcore: registered new interface driver usbfs
[   27.537461] usbcore: registered new interface driver hub
[   27.537543] usbcore: registered new device driver usb
[   27.538584] USB Universal Host Controller Interface driver v3.0
[   27.539057] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[   27.539117] PCI: setting IRQ 7 as level-triggered
[   27.539123] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   27.539284] uhci_hcd 0000:00:06.0: UHCI Host Controller
[   27.539523] uhci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 1
[   27.539620] uhci_hcd 0000:00:06.0: irq 7, io base 0x0000d000
[   27.539836] usb usb1: configuration #1 chosen from 1 choice
[   27.539929] hub 1-0:1.0: USB hub found
[   27.539993] hub 1-0:1.0: 2 ports detected
[   27.621352] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.641816] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   27.641884] PCI: setting IRQ 10 as level-triggered
[   27.641890] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   27.642052] uhci_hcd 0000:00:06.1: UHCI Host Controller
[   27.642134] uhci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[   27.642227] uhci_hcd 0000:00:06.1: irq 10, io base 0x0000d400
[   27.642399] usb usb2: configuration #1 chosen from 1 choice
[   27.643591] hub 2-0:1.0: USB hub found
[   27.643660] hub 2-0:1.0: 2 ports detected
[   27.661762] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.661833] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   27.745706] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[   27.745774] PCI: setting IRQ 5 as level-triggered
[   27.745779] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   27.745942] uhci_hcd 0000:00:11.2: UHCI Host Controller
[   27.746026] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 3
[   27.746118] uhci_hcd 0000:00:11.2: irq 5, io base 0x0000e800
[   27.746296] usb usb3: configuration #1 chosen from 1 choice
[   27.746382] hub 3-0:1.0: USB hub found
[   27.746447] hub 3-0:1.0: 2 ports detected
[   27.802528] FDC 0 is a post-1991 82077
[   27.849325] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   27.849499] uhci_hcd 0000:00:11.3: UHCI Host Controller
[   27.849590] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 4
[   27.849680] uhci_hcd 0000:00:11.3: irq 5, io base 0x0000ec00
[   27.849846] usb usb4: configuration #1 chosen from 1 choice
[   27.849936] hub 4-0:1.0: USB hub found
[   27.850000] hub 4-0:1.0: 2 ports detected
[    2.824000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.828000] Time: acpi_pm clocksource has been installed.
[    2.884000] r8169 Gigabit Ethernet driver 6.004.00 loaded
[    2.884000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    2.884000] PCI: setting IRQ 11 as level-triggered
[    2.884000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.884000] eth0: RTL8169S/8110S at 0xf8814000, 00:1b:2f:be:dc:e9, IRQ 11
[    2.888000] ACPI: PCI Interrupt 0000:00:06.2[C] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[    2.888000] ehci_hcd 0000:00:06.2: EHCI Host Controller
[    2.888000] ehci_hcd 0000:00:06.2: new USB bus registered, assigned bus number 5
[    2.888000] ehci_hcd 0000:00:06.2: irq 5, io mem 0xe8001000
[    2.888000] ehci_hcd 0000:00:06.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[    2.888000] usb usb5: configuration #1 chosen from 1 choice
[    2.892000] hub 5-0:1.0: USB hub found
[    2.892000] hub 5-0:1.0: 4 ports detected
[    2.996000] ACPI: PCI Interrupt 0000:00:0a.3[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    2.996000] ehci_hcd 0000:00:0a.3: EHCI Host Controller
[    2.996000] ehci_hcd 0000:00:0a.3: new USB bus registered, assigned bus number 6
[    2.996000] ehci_hcd 0000:00:0a.3: debug port 1
[    3.020000] ehci_hcd 0000:00:0a.3: irq 7, io mem 0xe8003000
[    3.020000] ehci_hcd 0000:00:0a.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.020000] usb usb6: configuration #1 chosen from 1 choice
[    3.020000] hub 6-0:1.0: USB hub found
[    3.020000] hub 6-0:1.0: 6 ports detected
[    3.124000] ACPI: PCI Interrupt 0000:00:0a.0[B] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[    3.124000] ohci_hcd 0000:00:0a.0: OHCI Host Controller
[    3.124000] ohci_hcd 0000:00:0a.0: new USB bus registered, assigned bus number 7
[    3.124000] ohci_hcd 0000:00:0a.0: irq 10, io mem 0xe8002000
[    3.180000] usb usb7: configuration #1 chosen from 1 choice
[    3.180000] hub 7-0:1.0: USB hub found
[    3.180000] hub 7-0:1.0: 2 ports detected
[    3.284000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[    3.284000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.284000] PCI: VIA VLink IRQ fixup for 0000:00:11.1, from 255 to 11
[    3.284000] VP_IDE: chipset revision 6
[    3.284000] VP_IDE: not 100% native mode: will probe irqs later
[    3.284000] VP_IDE: VIA vt8233a (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[    3.284000]     ide0: BM-DMA at 0xe400-0xe407, BIOS settings: hda:DMA, hdb:pio
[    3.284000]     ide1: BM-DMA at 0xe408-0xe40f, BIOS settings: hdc:DMA, hdd:DMA
[    3.284000] Probing IDE interface ide0...
[    4.148000] hda: PIONEER DVD-RW DVR-109, ATAPI CD/DVD-ROM drive
[    4.820000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.820000] Probing IDE interface ide1...
[    5.236000] hdc: ST3250820A, ATA DISK drive
[    5.516000] hdd: ST3320620A, ATA DISK drive
[    5.572000] ide1 at 0x170-0x177,0x376 on irq 15
[    5.584000] SCSI subsystem initialized
[    5.588000] libata version 2.21 loaded.
[    5.612000] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[    5.616000] Uniform CD-ROM driver Revision: 3.20
[    6.040000] hdc: max request size: 512KiB
[    6.076000] hdc: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[    6.100000] hdc: cache flushes supported
[    6.100000]  hdc: hdc1 hdc2 hdc3 < hdc5 >
[    6.144000] hdd: max request size: 512KiB
[    6.188000] hdd: 625142448 sectors (320072 MB) w/16384KiB Cache, CHS=38913/255/63, UDMA(100)
[    6.212000] hdd: cache flushes supported
[    6.212000]  hdd: hdd1 hdd2 < hdd5 >
[    6.720000] Attempting manual resume
[    6.720000] swsusp: Resume From Partition 22:5
[    6.720000] PM: Checking swsusp image.
[    6.720000] PM: Resume from disk failed.
[    6.768000] kjournald starting.  Commit interval 5 seconds
[    6.768000] EXT3-fs: mounted filesystem with ordered data mode.
[   13.108000] r8169: eth0: link up
[   13.108000] r8169: eth0: link up
[   13.108000] r8169: eth0: link up
[   13.108000] r8169: eth0: link up
[   13.108000] r8169: eth0: link up
[   13.108000] r8169: eth0: link up
[   13.108000] r8169: eth0: link up
[   13.108000] r8169: eth0: link up
[   13.108000] r8169: eth0: link up
[   13.108000] r8169: eth0: link up
[   13.108000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.112000] r8169: eth0: link up
[   13.116000] r8169: eth0: link up
[   14.752000] NET: Registered protocol family 17
[   14.860000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.944000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[   14.948000] agpgart: AGP aperture is 64M @ 0xe0000000
[   14.956000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.956000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.740000] gameport: EMU10K1 is pci0000:00:09.1/gameport0, io 0xe000, speed 1193kHz
[   15.804000] irda_init()
[   15.804000] NET: Registered protocol family 23
[   16.196000] input: PC Speaker as /class/input/input2
[   16.344000] nvidia: module license 'NVIDIA' taints kernel.
[   16.620000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   16.620000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   16.680000] input: PS/2 Generic Mouse as /class/input/input3
[   16.940000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   17.852000] lp: driver loaded but no devices found
[   17.912000] Adding 2000052k swap on /dev/hdc5.  Priority:-1 extents:1 across:2000052k
[   18.400000] EXT3 FS on hdc2, internal journal
[   19.772000] kjournald starting.  Commit interval 5 seconds
[   19.780000] EXT3 FS on hdd1, internal journal
[   19.780000] EXT3-fs: mounted filesystem with ordered data mode.
[   23.984000] No dock devices found.
[   24.048000] input: Power Button (FF) as /class/input/input4
[   24.052000] ACPI: Power Button (FF) [PWRF]
[   24.096000] input: Power Button (CM) as /class/input/input5
[   24.100000] ACPI: Power Button (CM) [PWRB]
[   24.140000] input: Sleep Button (CM) as /class/input/input6
[   24.140000] ACPI: Sleep Button (CM) [SLPB]
[   25.988000] NET: Registered protocol family 10
[   25.988000] lo: Disabled Privacy Extensions
[   26.324000] ppdev: user-space parallel port driver
[   26.412000] audit(1197164650.624:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5043 profile="/usr/sbin/cupsd"
[   26.460000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   26.460000] apm: overridden by ACPI.
[   27.216000] Failure registering capabilities with primary security module.
[   27.456000] Bluetooth: Core ver 2.11
[   27.456000] NET: Registered protocol family 31
[   27.456000] Bluetooth: HCI device and connection manager initialized
[   27.456000] Bluetooth: HCI socket layer initialized
[   27.468000] Bluetooth: L2CAP ver 2.8
[   27.468000] Bluetooth: L2CAP socket layer initialized
[   27.588000] Bluetooth: RFCOMM socket layer initialized
[   27.588000] Bluetooth: RFCOMM TTY layer initialized
[   27.588000] Bluetooth: RFCOMM ver 1.8
[   29.444000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   29.444000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   29.444000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   36.708000] eth0: no IPv6 routers present
[   75.296000] UDF-fs: No VRS found
[   75.368000] ISO 9660 Extensions: Microsoft Joliet Level 1
[   75.412000] ISOFS: changing to secondary root
[   79.816000] NETDEV WATCHDOG: eth0: transmit timed out
```

```
lsmod:

Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
ipv6                  273892  10 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
button                  8976  0 
dock                   10656  0 
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
video                  18060  0 
battery                11012  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           137248  2 snd_emu10k1_synth
snd_ac97_codec        100644  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
nvidia               6221648  34 
pcspkr                  4224  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_viapro             10004  0 
via_ircc               27668  0 
i2c_core               26112  2 nvidia,i2c_viapro
psmouse                39952  0 
snd                    54660  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
irda                  202300  1 via_ircc
serio_raw               8068  0 
crc_ccitt               3072  1 irda
emu10k1_gp              4736  0 
gameport               16776  2 emu10k1_gp
soundcore               8800  1 snd
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
via_agp                11264  1 
agpgart                35016  2 nvidia,via_agp
af_packet              24840  4 
evdev                  11136  4 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_disk               18560  6 
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
floppy                 60004  0 
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_disk,ide_cd,via82cxxx
ohci_hcd               22916  0 
ehci_hcd               36492  0 
r8169                  31760  0 
uhci_hcd               26640  0 
usbcore               138632  4 ohci_hcd,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

```
ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:1B:2F:BE:DC:E9  
          inet6 addr: fe80::21b:2fff:febe:dce9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:974 overruns:0 frame:0
          TX packets:0 errors:0 dropped:322 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:2F:BE:DC:E9  
          inet addr:169.254.10.177  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1744 (1.7 KB)  TX bytes:1744 (1.7 KB)

```

```
/etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
#iface eth1 inet static
#address 192.168.0.1
#network 192.168.0.0
#netmask 255.255.255.0
#broadcast 192.168.0.255

#auto br0
#iface br0 inet static
#address 192.168.0.1
#network 192.168.0.0
#netmask 255.255.255.0
#broadcast 192.168.0.255
#bridge-ports eth1

auto eth2
iface eth2 inet dhcp
```

```
/etc/dhcp3/dhclient.conf:

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

### Post by santosh_gr on 2007-12-09
try disabling the firewall setting if you have any.

---

### Post by shinobitux on 2007-12-09
Thank you for the response.

I don't have any local firewall that I'm aware of, but I hadn't gotten that far into researching DHCP/firewall capabilities with Ubuntu, so it's possible that I have something I don't know about.

I'm fairly confident that the problem is with the hardware I'm using, since replacing the realtek 8169 with a 8139 card works just fine.

Since posting my original thread I've downloaded a nic diagnostic tool from the Ubuntu repositories originally designed for the 8139 chipset. It doesn't recognize the 8169 very well, but tomorrow I'll post its output if it'll help.

What would you suggest I do? And if you'd like, where should I look for firewall settings?

Thanks.

---

### Post by santosh_gr on 2007-12-09
If another network card works on the same box i dont think it is related to firewall.  You can check by using 

iptables -L 

Its highly unlikely that a firewall is configured.

Does the nic work with a static ip?  Update the /etc/networks/interfaces file with static entries as shown below for eth0 section.  Just modify the address to your specific settings.

auto eth0
iface eth0 inet static
     address 192.168.0.2
     netmask 255.255.255.0
     gateway 192.168.0.1


You will need to restart networking service.  See if it comes up okay.

/etc/init.d/networking restart

---

### Post by santosh_gr on 2007-12-09
also it may be worth disabling ipv6 from the /etc/modprobe.d/aliases file.

Look for 
alias net-pf-10 ipv6 

and comment it out.  Reboot the box to see if dhcp picks up an ip address.

---

### Post by shinobitux on 2007-12-09
Here's my iptables -L output:

Chain INPUT (policy ACCEPT)
taret prot opt source destination

Chain FORWARD (policy ACCEPT)
taret prot opt source destination

Chain OUTPUT (policy ACCEPT)
taret prot opt source destination

Ok, tried static ip, but had no luck.

Tried editing the /etc/modprobe.d/aliases file...still no go.

I just tried booting the Windows side with this NIC and even with the native Windows drivers installed it wouldn't work.

So, unless you can think of something else I think I just have a bad card.

What do you think?

Thanks for helping me out, agian.

---

### Post by santosh_gr on 2007-12-10
it may just be a bad card.  most settings look ok, cant think of anything else.

one thing to do would be to set static ip on the box. try pinging the lo0 ip address and eth0 ip address to see if it responds ok. if it does then, you can also install ethereal on another system and try to sniff for network traffic. It will tell you if you have a faulty card or a misconfiguration on your system.

---

### Post by shinobitux on 2007-12-11
Ethereal, huh?

Ok, thanks. I appreciate all the help you've given me.

I think I've successfully pinged the loopback interface, but I'll try your suggestion.

Have a good one!

---

