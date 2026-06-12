---
title: "r8169 1000Mb/s working at sub 100Mb/s speeds"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by nickgraber on 2007-07-25
I got on the Ubuntu website and looked under supported hardware to find that that the RTL8169 was supported so I ordered some enlga-1320's that contain that chipset so someone must have this card working.  I removed the kernel module that was included because it didn't work for me and compiled the current driver from realtek's web page.  After doing that the card worked at above 100Mb/s speeds until I did a restart and now I cant seem to get it working again.  Below you will find my dmesg, lspci, ethtool, and interfaces print outs.

**_dmesg_**

[    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:26:23 UTC 2007 (Ubuntu 2.6.20-16.29-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009b000 end: 000000000009b000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003bef0000 end: 000000003bff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003bff0000 size: 0000000000003000 end: 000000003bff3000 type: 4
[    0.000000] copy_e820_map() start: 000000003bff3000 size: 000000000000d000 end: 000000003c000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bff0000 (usable)
[    0.000000]  BIOS-e820: 000000003bff0000 - 000000003bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bff3000 - 000000003c000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 63MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5130
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] Entering add_active_range(0, 0, 245744) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245744
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245744
[    0.000000] On node 0 totalpages: 245744
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 127 pages used for memmap
[    0.000000]   HighMem zone: 16241 pages, LIFO batch:3
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 VIAK8                                 ) @ 0x000f6ab0
[    0.000000] ACPI: RSDT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3bff3000
[    0.000000] ACPI: FADT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3bff3040
[    0.000000] ACPI: MADT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3bff75c0
[    0.000000] ACPI: DSDT (v001 VIAK8  AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3c000000:c2c00000)
[    0.000000] Detected 2009.326 MHz processor.
[   31.930561] Built 1 zonelists.  Total pages: 243825
[   31.930564] Kernel command line: root=UUID=49b7d0fe-dfad-4ca6-8356-e43e2a7e7d8f ro quiet splash acpi=ht
[   31.930706] mapped APIC to ffffd000 (fee00000)
[   31.930708] mapped IOAPIC to ffffc000 (fec00000)
[   31.930711] Enabling fast FPU save and restore... done.
[   31.930713] Enabling unmasked SIMD FPU exception support... done.
[   31.930721] Initializing CPU#0
[   31.930799] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   31.932503] Console: colour VGA+ 80x25
[   31.932964] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   31.933693] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.949937] Memory: 963212k/982976k available (2020k kernel code, 19100k reserved, 897k data, 332k init, 65472k highmem)
[   31.949947] virtual kernel memory layout:
[   31.949948]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
[   31.949949]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   31.949950]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   31.949951]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   31.949953]       .init : 0xc03df000 - 0xc0432000   ( 332 kB)
[   31.949954]       .data : 0xc02f9234 - 0xc03d9754   ( 897 kB)
[   31.949955]       .text : 0xc0100000 - 0xc02f9234   (2020 kB)
[   31.949958] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   32.090608] Calibrating delay using timer specific routine.. 4022.27 BogoMIPS (lpj=20111379)
[   32.090650] Security Framework v1.0.0 initialized
[   32.090656] SELinux:  Disabled at boot.
[   32.090670] Mount-cache hash table entries: 512
[   32.090799] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   32.090807] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   32.090809] CPU: L2 Cache: 256K (64 bytes/line)
[   32.090812] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   32.090822] Compat vDSO mapped to ffffe000.
[   32.090827] Remapping vsyscall page to ffffe000
[   32.090836] Checking 'hlt' instruction... OK.
[   32.130691] SMP alternatives: switching to UP code
[   32.130908] Freeing SMP alternatives: 11k freed
[   32.131106] Early unpacking initramfs... done
[   32.398285] CPU0: AMD Sempron(tm) Processor 3400+ stepping 02
[   32.398304] Total of 1 processors activated (4022.27 BogoMIPS).
[   32.398805] ENABLING IO-APIC IRQs
[   32.399170] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   32.609994] Brought up 1 CPUs
[   32.610243] Booting paravirtualized kernel on bare hardware
[   32.610338] Time:  0:14:32  Date: 06/26/107
[   32.610364] NET: Registered protocol family 16
[   32.610435] EISA bus registered
[   32.617992] PCI: PCI BIOS revision 2.10 entry at 0xfb0a0, last bus=1
[   32.617994] PCI: Using configuration type 1
[   32.617996] Setting up standard PCI resources
[   32.618575] ACPI: Interpreter disabled.
[   32.618578] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.618584] pnp: PnP ACPI: disabled
[   32.618587] PnPBIOS: Scanning system for PnP BIOS support...
[   32.618838] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbb20
[   32.618845] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbb50, dseg 0xf0000
[   32.619568] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   32.619603] PCI: Probing PCI hardware
[   32.619606] PCI: Probing PCI hardware (bus 00)
[   32.620459] Boot video device is 0000:01:00.0
[   32.621433] PCI: Using IRQ router VIA [1106/3227] at 0000:00:11.0
[   32.621448] PCI->APIC IRQ transform: 0000:00:09.0[A] -> IRQ 17
[   32.621451] PCI->APIC IRQ transform: 0000:00:0a.0[A] -> IRQ 18
[   32.621454] PCI->APIC IRQ transform: 0000:00:0b.0[A] -> IRQ 19
[   32.621457] PCI->APIC IRQ transform: 0000:00:0f.0[B] -> IRQ 20
[   32.621460] PCI->APIC IRQ transform: 0000:00:0f.1[A] -> IRQ 20
[   32.621464] PCI->APIC IRQ transform: 0000:00:10.0[A] -> IRQ 21
[   32.621466] PCI->APIC IRQ transform: 0000:00:10.1[A] -> IRQ 21
[   32.621469] PCI->APIC IRQ transform: 0000:00:10.2[B] -> IRQ 21
[   32.621472] PCI->APIC IRQ transform: 0000:00:10.3[B] -> IRQ 21
[   32.621476] PCI->APIC IRQ transform: 0000:00:10.4[C] -> IRQ 21
[   32.621479] PCI->APIC IRQ transform: 0000:00:11.5[C] -> IRQ 22
[   32.621483] PCI->APIC IRQ transform: 0000:00:12.0[A] -> IRQ 23
[   32.621487] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 16
[   32.647633] NET: Registered protocol family 8
[   32.647635] NET: Registered protocol family 20
[   32.647642] NetLabel: Initializing
[   32.647644] NetLabel:  domain hash size = 128
[   32.647645] NetLabel:  protocols = UNLABELED CIPSOv4
[   32.647656] NetLabel:  unlabeled traffic allowed by default
[   32.647913] PCI: Bridge: 0000:00:01.0
[   32.647914]   IO window: disabled.
[   32.647918]   MEM window: e8000000-e9ffffff
[   32.647922]   PREFETCH window: e4000000-e7ffffff
[   32.647936] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   32.647956] NET: Registered protocol family 2
[   32.719886] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.720043] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   32.721050] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   32.721548] TCP: Hash tables configured (established 131072 bind 65536)
[   32.721552] TCP reno registered
[   32.749898] checking if image is initramfs... it is
[   33.272741] Freeing initrd memory: 6891k freed
[   33.273098] audit: initializing netlink socket (disabled)
[   33.273109] audit(1185408874.200:1): initialized
[   33.273152] highmem bounce pool size: 64 pages
[   33.273197] VFS: Disk quotas dquot_6.5.1
[   33.273212] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.273263] io scheduler noop registered
[   33.273264] io scheduler anticipatory registered
[   33.273266] io scheduler deadline registered (default)
[   33.273275] io scheduler cfq registered
[   33.273529] isapnp: Scanning for PnP cards...
[   33.630012] isapnp: No Plug & Play device found
[   33.654003] Real Time Clock Driver v1.12ac
[   33.654052] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.654155] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.654355] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.654919] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.655178] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.655370] mice: PS/2 mouse device common for all mice
[   33.655759] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.655907] input: Macintosh mouse button emulation as /class/input/input0
[   33.655936] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.655939] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.656201] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   33.656203] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   33.898433] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.898569] EISA: Probing bus 0 at eisa.0
[   33.898609] EISA: Detected 0 cards.
[   33.928658] TCP cubic registered
[   33.928666] NET: Registered protocol family 1
[   33.928684] Using IPI No-Shortcut mode
[   33.928702]   Magic number: 15:124:204
[   33.928739]   hash matches device ttyt2
[   33.929035] Freeing unused kernel memory: 332k freed
[   33.938297] Time: tsc clocksource has been installed.
[   33.947130] input: AT Translated Set 2 keyboard as /class/input/input1
[   34.089570] Capability LSM initialized
[   34.168472] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   34.231058] raid5: automatically using best checksumming function: pIII_sse
[   34.277861]    pIII_sse  :  6160.400 MB/sec
[   34.277863] raid5: using function: pIII_sse (6160.400 MB/sec)
[   34.457687] raid6: int32x1    859 MB/s
[   34.627478] raid6: int32x2    872 MB/s
[   34.797272] raid6: int32x4    727 MB/s
[   34.967030] raid6: int32x8    540 MB/s
[   35.136812] raid6: mmxx1     1614 MB/s
[   35.306580] raid6: mmxx2     3043 MB/s
[   35.476373] raid6: sse1x1    1518 MB/s
[   35.646168] raid6: sse1x2    2466 MB/s
[   35.815938] raid6: sse2x1    2596 MB/s
[   35.985721] raid6: sse2x2    3318 MB/s
[   35.985723] raid6: using algorithm sse2x2 (3318 MB/s)
[   35.985726] md: raid6 personality registered for level 6
[   35.985728] md: raid5 personality registered for level 5
[   35.985729] md: raid4 personality registered for level 4
[   36.457306] SCSI subsystem initialized
[   36.462172] libata version 2.20 loaded.
[   36.462206] r8169 Gigabit Ethernet driver 2.2LK loaded
[   36.462374] eth0: RTL8169sb/8110sb at 0xf8826000, 00:06:4f:51:9c:47, IRQ 19
[   36.465501] sata_sil 0000:00:09.0: version 2.2
[   36.465530] sata_sil 0000:00:09.0: Applying R_ERR on DMA activate FIS errata fix
[   36.465642] ata1: SATA max UDMA/100 cmd 0xf8828080 ctl 0xf882808a bmdma 0xf8828000 irq 17
[   36.465715] ata2: SATA max UDMA/100 cmd 0xf88280c0 ctl 0xf88280ca bmdma 0xf8828008 irq 17
[   36.466721] ata3: SATA max UDMA/100 cmd 0xf8828280 ctl 0xf882828a bmdma 0xf8828200 irq 17
[   36.466753] ata4: SATA max UDMA/100 cmd 0xf88282c0 ctl 0xf88282ca bmdma 0xf8828208 irq 17
[   36.466770] scsi0 : sata_sil
[   36.513557] usbcore: registered new interface driver usbfs
[   36.513576] usbcore: registered new interface driver hub
[   36.513595] usbcore: registered new device driver usb
[   36.514373] USB Universal Host Controller Interface driver v3.0
[   36.565791] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   36.728659] FDC 0 is a post-1991 82077
[   36.974475] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   37.015702] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   37.015707] ata1.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133
[   37.015710] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.044785] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   37.044789] ata1.00: configured for UDMA/100
[   37.044800] scsi1 : sata_sil
[   37.553742] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   37.591185] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   37.591190] ata2.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133
[   37.591192] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.614824] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   37.614827] ata2.00: configured for UDMA/100
[   37.614838] scsi2 : sata_sil
[   38.123024] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   38.163769] ata3.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   38.163774] ata3.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133
[   38.163776] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   38.193339] ata3.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   38.193342] ata3.00: configured for UDMA/100
[   38.193353] scsi3 : sata_sil
[   38.702291] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   38.737640] ata4.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   38.737646] ata4.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133
[   38.737649] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   38.762816] ata4.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   38.762820] ata4.00: configured for UDMA/100
[   38.762912] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   38.763212] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   38.763435] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   38.763642] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   38.763709] sata_sil 0000:00:0a.0: Applying R_ERR on DMA activate FIS errata fix
[   38.763904] ata5: SATA max UDMA/100 cmd 0xf88c0080 ctl 0xf88c008a bmdma 0xf88c0000 irq 18
[   38.763928] ata6: SATA max UDMA/100 cmd 0xf88c00c0 ctl 0xf88c00ca bmdma 0xf88c0008 irq 18
[   38.763948] ata7: SATA max UDMA/100 cmd 0xf88c0280 ctl 0xf88c028a bmdma 0xf88c0200 irq 18
[   38.763969] ata8: SATA max UDMA/100 cmd 0xf88c02c0 ctl 0xf88c02ca bmdma 0xf88c0208 irq 18
[   38.763985] scsi4 : sata_sil
[   39.271571] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   39.308628] ata5.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   39.308632] ata5.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133
[   39.308635] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   39.332209] ata5.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   39.332213] ata5.00: configured for UDMA/100
[   39.332223] scsi5 : sata_sil
[   39.671049] ata6: SATA link down (SStatus 0 SControl 310)
[   39.671066] scsi6 : sata_sil
[   40.010617] ata7: SATA link down (SStatus 0 SControl 310)
[   40.010632] scsi7 : sata_sil
[   40.350187] ata8: SATA link down (SStatus 0 SControl 310)
[   40.350298] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   40.354236] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   40.354258] VP_IDE: chipset revision 6
[   40.354260] VP_IDE: not 100% native mode: will probe irqs later
[   40.354270] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   40.354277]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:pio
[   40.354289]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:pio
[   40.354297] Probing IDE interface ide0...
[   40.377334] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[   40.377345] sda: Write Protect is off
[   40.377347] sda: Mode Sense: 00 3a 00 00
[   40.377357] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.377398] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[   40.377404] sda: Write Protect is off
[   40.377406] sda: Mode Sense: 00 3a 00 00
[   40.377415] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.377419]  sda: sda1
[   40.381310] sd 0:0:0:0: Attached scsi disk sda
[   40.384562] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[   40.384573] sdb: Write Protect is off
[   40.384575] sdb: Mode Sense: 00 3a 00 00
[   40.384585] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.384631] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[   40.384637] sdb: Write Protect is off
[   40.384639] sdb: Mode Sense: 00 3a 00 00
[   40.384648] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.384651]  sdb: sdb1
[   40.390860] sd 1:0:0:0: Attached scsi disk sdb
[   40.391251] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[   40.391260] sdc: Write Protect is off
[   40.391262] sdc: Mode Sense: 00 3a 00 00
[   40.391273] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.391310] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[   40.391316] sdc: Write Protect is off
[   40.391318] sdc: Mode Sense: 00 3a 00 00
[   40.391329] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.391331]  sdc: sdc1
[   40.397527] sd 2:0:0:0: Attached scsi disk sdc
[   40.397882] SCSI device sdd: 976773168 512-byte hdwr sectors (500108 MB)
[   40.397890] sdd: Write Protect is off
[   40.397892] sdd: Mode Sense: 00 3a 00 00
[   40.397902] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.397929] SCSI device sdd: 976773168 512-byte hdwr sectors (500108 MB)
[   40.397936] sdd: Write Protect is off
[   40.397937] sdd: Mode Sense: 00 3a 00 00
[   40.397948] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.397950]  sdd: sdd1
[   40.405482] sd 3:0:0:0: Attached scsi disk sdd
[   40.405882] SCSI device sde: 976773168 512-byte hdwr sectors (500108 MB)
[   40.405890] sde: Write Protect is off
[   40.405892] sde: Mode Sense: 00 3a 00 00
[   40.405902] SCSI device sde: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.405934] SCSI device sde: 976773168 512-byte hdwr sectors (500108 MB)
[   40.405941] sde: Write Protect is off
[   40.405943] sde: Mode Sense: 00 3a 00 00
[   40.405953] SCSI device sde: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.405956]  sde: sde1
[   40.410535] sd 4:0:0:0: Attached scsi disk sde
[   40.415687] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   40.415705] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   40.415723] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   40.415744] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   40.415759] sd 4:0:0:0: Attached scsi generic sg4 type 0
[   40.571466] md: md0 stopped.
[   40.620011] md: bind<sdb1>
[   40.678858] md: md0 stopped.
[   40.678867] md: unbind<sdb1>
[   40.678876] md: export_rdev(sdb1)
[   40.692786] md: bind<sdb1>
[   40.692981] md: bind<sdc1>
[   40.693167] md: bind<sdd1>
[   40.693347] md: bind<sde1>
[   40.693535] md: bind<sda1>
[   40.700133] raid5: device sda1 operational as raid disk 0
[   40.700137] raid5: device sde1 operational as raid disk 4
[   40.700139] raid5: device sdd1 operational as raid disk 3
[   40.700141] raid5: device sdc1 operational as raid disk 2
[   40.700143] raid5: device sdb1 operational as raid disk 1
[   40.700493] raid5: allocated 5245kB for md0
[   40.700496] raid5: raid level 5 set md0 active with 5 out of 5 devices, algorithm 2
[   40.700498] RAID5 conf printout:
[   40.700500]  --- rd:5 wd:5
[   40.700502]  disk 0, o:1, dev:sda1
[   40.700503]  disk 1, o:1, dev:sdb1
[   40.700505]  disk 2, o:1, dev:sdc1
[   40.700506]  disk 3, o:1, dev:sdd1
[   40.700508]  disk 4, o:1, dev:sde1
[   40.829674] hda: SAMSUNG SV2042H, ATA DISK drive
[   41.558834] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   41.558880] Probing IDE interface ide1...
[   42.507553] hdc: PIONEER DVD-RW DVR-111D, ATAPI CD/DVD-ROM drive
[   43.236900] ide1 at 0x170-0x177,0x376 on irq 15
[   43.238207] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   43.238357] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   43.238386] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d800
[   43.238495] usb usb1: configuration #1 chosen from 1 choice
[   43.238519] hub 1-0:1.0: USB hub found
[   43.238525] hub 1-0:1.0: 2 ports detected
[   43.248965] hda: max request size: 128KiB
[   43.251664] hda: Host Protected Area detected.
[   43.251666] 	current capacity is 39863279 sectors (20409 MB)
[   43.251668] 	native  capacity is 39865392 sectors (20411 MB)
[   43.251756] hda: Host Protected Area disabled.
[   43.251759] hda: 39865392 sectors (20411 MB) w/426KiB Cache, CHS=39549/16/63, UDMA(100)
[   43.251763] hda: cache flushes not supported
[   43.251811]  hda: hda1 hda2 < hda5 >
[   43.288175] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[   43.288183] Uniform CD-ROM driver Revision: 3.20
[   43.356519] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   43.356539] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   43.356560] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000dc00
[   43.356645] usb usb2: configuration #1 chosen from 1 choice
[   43.356667] hub 2-0:1.0: USB hub found
[   43.356674] hub 2-0:1.0: 2 ports detected
[   43.476347] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   43.476368] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   43.476389] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[   43.476465] usb usb3: configuration #1 chosen from 1 choice
[   43.476485] hub 3-0:1.0: USB hub found
[   43.476492] hub 3-0:1.0: 2 ports detected
[   43.596199] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   43.596218] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   43.596240] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e400
[   43.596316] usb usb4: configuration #1 chosen from 1 choice
[   43.596338] hub 4-0:1.0: USB hub found
[   43.596344] hub 4-0:1.0: 2 ports detected
[   43.716137] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   43.716160] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   43.716198] ehci_hcd 0000:00:10.4: irq 21, io mem 0xeb003000
[   43.716204] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   43.716260] usb usb5: configuration #1 chosen from 1 choice
[   43.716282] hub 5-0:1.0: USB hub found
[   43.716289] hub 5-0:1.0: 8 ports detected
[   43.836066] eth1: VIA Rhine II at 0x1ec00, 00:14:85:c0:21:73, IRQ 23.
[   43.836777] eth1: MII PHY found at address 1, status 0x786d advertising 05e1 Link c1e1.
[   43.836842] sata_via 0000:00:0f.0: version 2.1
[   43.836866] sata_via 0000:00:0f.0: routed to hard irq line 11
[   43.837207] ata9: SATA max UDMA/133 cmd 0x0001bc00 ctl 0x0001c002 bmdma 0x0001cc00 irq 20
[   43.837232] ata10: SATA max UDMA/133 cmd 0x0001c400 ctl 0x0001c802 bmdma 0x0001cc08 irq 20
[   43.837246] scsi8 : sata_via
[   43.860412] Attempting manual resume
[   43.860415] swsusp: Resume From Partition 3:5
[   43.860417] PM: Checking swsusp image.
[   43.882049] PM: Resume from disk failed.
[   43.926867] kjournald starting.  Commit interval 5 seconds
[   43.926877] EXT3-fs: mounted filesystem with ordered data mode.
[   44.055520] ata9: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   44.066208] ATA: abnormal status 0x7F on port 0x0001bc07
[   44.066335] scsi9 : sata_via
[   44.285208] ata10: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   44.295892] ATA: abnormal status 0x7F on port 0x0001c407
[   47.437121] eth0: link up, 100Mbps, full-duplex, lpa 0xC1E1
[   49.287585] NET: Registered protocol family 10
[   49.287668] lo: Disabled Privacy Extensions
[   49.455246] input: PC Speaker as /class/input/input2
[   49.624210] parport: PnPBIOS parport detected.
[   49.624262] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   49.689133] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   49.716041] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   49.757841] Linux agpgart interface v0.102 (c) Dave Jones
[   49.925562] agpgart: Detected AGP bridge 0
[   49.927620] agpgart: AGP aperture is 64M @ 0xe0000000
[   50.888524] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   52.636631] lp0: using parport0 (interrupt-driven).
[   52.861361] Adding 875500k swap on /dev/disk/by-uuid/d17c4816-b76b-48a7-9186-d2ca93f41af1.  Priority:-1 extents:1 across:875500k
[   53.031198] EXT3 FS on hda1, internal journal
[   53.334188] kjournald starting.  Commit interval 5 seconds
[   53.334197] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   53.368118] EXT3 FS on md0, internal journal
[   53.368123] EXT3-fs: mounted filesystem with ordered data mode.
[   60.244979] eth0: no IPv6 routers present
[  836.473449] r8169: eth1: link up
[  847.380180] eth1: no IPv6 routers present
[ 1236.379476] r8169: eth1: link down
[ 1239.540760] r8169: eth1: link up
[ 1277.028094] r8169: eth1: link down
[ 1279.827735] r8169: eth1: link up
[ 1291.361542] r8169: eth1: link down
[ 1294.421710] r8169: eth1: link up
[ 1306.525779] r8169: eth1: link down
[ 1309.289220] r8169: eth1: link up
[ 1326.539987] r8169: eth1: link down
[ 1329.640651] r8169: eth1: link up
[ 1383.853415] r8169: eth1: link down
[ 1386.565191] r8169: eth1: link up
[ 1397.049667] r8169: eth1: link down
[ 1400.188855] r8169: eth1: link up
[ 1414.410076] r8169: eth1: link down
[ 1417.108108] r8169: eth1: link up
[ 1504.605391] r8169: eth1: link down
[ 1507.193957] r8169: eth1: link up
[ 1512.882548] r8169: eth1: link down
[ 1515.521308] r8169: eth1: link up
[ 1524.963673] r8169: eth1: link down
[ 1527.982855] r8169: eth1: link up
[ 1620.383300] r8169: eth1: link down
[ 1623.030161] r8169: eth1: link up
[ 1645.726566] r8169: eth1: link down
[ 1648.140143] r8169: eth1: link up
[ 1658.031069] r8169: eth1: link down
[ 1659.721850] r8169: eth1: link up
[ 1725.368070] eth0: link down
[ 1725.390848] r8169: eth1: link down
[ 1727.096599] r8169: eth1: link up
[ 1727.720511] eth0: link up, 100Mbps, full-duplex, lpa 0xC1E1
[ 3102.903714] r8169: eth1: link down
[ 3105.214087] r8169: eth1: link up
[ 3149.511116] r8169: eth1: link down
[ 3152.328064] r8169: eth1: link up
[ 3153.842255] r8169: eth1: link down
[ 3156.104774] r8169: eth1: link up
[ 3182.069016] r8169: eth1: link down
[ 3184.751346] r8169: eth1: link up
[ 3186.454992] r8169: eth1: link down
[ 3189.134250] r8169: eth1: link up


**_lspci_**

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
00:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

[B][U]
ethtool[/U][/B]

Settings for eth1:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000033 (51)
	Link detected: yes

[B][U]
interfaces[/U][/B]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 10.0.0.1
netmask 255.255.255.0
gateway 0.0.0.0

---

### Post by brander on 2007-07-26
I can`t help you with a solution but I can add that I have the same problem with Linux connecting to Windows PCs. Using a 100 Mb network card (8139) I can only get 3 MB/S per second transferring files either way, while between Windows PCs this is normally 10MB/S

So I upgraded the nic to 8169 and was surprised to find that the speed was exactly the same, 3MB/S while between Windows PCs with IGb nics this is more like 30MB/s(limited by HD and processor speed).

The hard drive in my Linux PC can copy files around its drive at 40MB/S so that is not a problem and the PC is dual-boot with XP and when booted to that system I get 35MB/S network speed.

I was interested that you got good speed for a while using a compiled driver, but unless it is permanent it is no good.

It is perhaps my main gripe about Linux because most other things work just as well in Linux as XP. This network speed restriction makes, say,  copying a bunch of DVDs really tedious and watching a HD movie down the local network impossible. I look forward to hearing if anyone else gets a solution to this.

---

### Post by nickgraber on 2007-07-26
Try running ethtool where X is your eth device number. 

ethtool -s ethX speed 100 duplex full port mii wol g autoneg off

that will get your card running at the full 100Mb/s speeds.  I have set mine up that way several times and it seems run solid with that configuration.  I haven't tried it with the Ubuntu supplied driver but I hink it should work on it as well.

---

### Post by MrHippocampus on 2007-07-26
Ive personally found that using nautilus and dragging files to/from another computer using samba is slow, but if I mount the windows network as a folder using fusesmb (youll probably have to google/search the forums to find out how to set it up) and copy files from there its much faster.

---

