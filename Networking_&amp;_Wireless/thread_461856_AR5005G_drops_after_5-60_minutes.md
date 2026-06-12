---
title: "AR5005G drops after 5-60 minutes"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by seanp2k on 2007-06-02
It seems the more things I do (ssh, FTP, web browsing) at the same time the faster it stops working, but basically I have an IP and it says connected, but the signal strength drops to 0 and  dhclient fails.

Please note that all these are taken while it is still working.


Computer:  Toshiba L25-S1192
Chipset: ATI Radeon Mobility 200M

lspci:
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Contro
ller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio 
Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200
M]
09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139
C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC 
(rev 01)


dmesg:

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed May 23 01:46:23 UTC 2007 (Ubuntu 2.6.20-16.28-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000057da0000 end: 0000000057ea0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000057ea0000 size: 0000000000013000 end: 0000000057eb3000 type: 3
[    0.000000] copy_e820_map() start: 0000000057eb3000 size: 000000000004d000 end: 0000000057f00000 type: 4
[    0.000000] copy_e820_map() start: 0000000057f00000 size: 0000000000100000 end: 0000000058000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000057ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000057ea0000 - 0000000057eb3000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000057eb3000 - 0000000057f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000057f00000 - 0000000058000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 510MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f73b0
[    0.000000] Entering add_active_range(0, 0, 360096) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   360096
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   360096
[    0.000000] On node 0 totalpages: 360096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1021 pages used for memmap
[    0.000000]   HighMem zone: 129699 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7450
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x57eae32a
[    0.000000] ACPI: FADT (v001 ATI    Goldfish 0x06040000 ATI  0x000f4240) @ 0x57eb2f00
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x57eb2f74
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x57eb2fc4
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x57eae564
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x57eae362
[    0.000000] ACPI: DSDT (v001    ATI    SB400 0x06040000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 58000000:88000000)
[    0.000000] Detected 1496.388 MHz processor.
[   12.123406] Built 1 zonelists.  Total pages: 357283
[   12.123411] Kernel command line: root=UUID=2c13d1b4-f8ef-4903-91c0-fe2fbd52c69d ro quiet splash
[   12.123610] mapped APIC to ffffd000 (fee00000)
[   12.123613] mapped IOAPIC to ffffc000 (fec00000)
[   12.123617] Enabling fast FPU save and restore... done.
[   12.123621] Enabling unmasked SIMD FPU exception support... done.
[   12.123640] Initializing CPU#0
[   12.123744] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   12.124976] Console: colour VGA+ 80x25
[   12.126032] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.127056] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.204420] Memory: 1416556k/1440384k available (1992k kernel code, 22548k reserved, 896k data, 328k init, 522880k highmem)
[   12.204433] virtual kernel memory layout:
[   12.204434]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   12.204436]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.204437]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   12.204438]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   12.204440]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   12.204441]       .data : 0xc02f2354 - 0xc03d26d4   ( 896 kB)
[   12.204443]       .text : 0xc0100000 - 0xc02f2354   (1992 kB)
[   12.204447] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.283673] Calibrating delay using timer specific routine.. 2996.09 BogoMIPS (lpj=5992181)
[   12.283743] Security Framework v1.0.0 initialized
[   12.283763] SELinux:  Disabled at boot.
[   12.283788] Mount-cache hash table entries: 512
[   12.284057] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   12.284076] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.284079] CPU: L2 cache: 1024K
[   12.284084] CPU: After all inits, caps: afe9fbff 00000000 00000000 00002040 00000000 00000000 00000000
[   12.284105] Compat vDSO mapped to ffffe000.
[   12.284114] Remapping vsyscall page to ffffe000
[   12.284134] Checking 'hlt' instruction... OK.
[   12.299910] SMP alternatives: switching to UP code
[   12.300371] Freeing SMP alternatives: 11k freed
[   12.300679] Early unpacking initramfs... done
[   12.679304] ACPI: Core revision 20060707
[   12.679622] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   12.691750] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
[   12.691779] Total of 1 processors activated (2996.09 BogoMIPS).
[   12.691972] ENABLING IO-APIC IRQs
[   12.692183] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.731901] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   12.731953] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   12.731956] ...trying to set up timer as Virtual Wire IRQ... works.
[   12.879425] Brought up 1 CPUs
[   12.879710] Booting paravirtualized kernel on bare hardware
[   12.879818] Time:  4:36:04  Date: 05/02/107
[   12.879852] NET: Registered protocol family 16
[   12.879955] EISA bus registered
[   12.879960] ACPI: bus type pci registered
[   12.880074] PCI: PCI BIOS revision 2.10 entry at 0xfd69c, last bus=14
[   12.880076] PCI: Using configuration type 1
[   12.880078] Setting up standard PCI resources
[   12.883653] ACPI: Interpreter enabled
[   12.883657] ACPI: Using IOAPIC for interrupt routing
[   12.884112] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.884118] PCI: Probing PCI hardware (bus 00)
[   12.885663] Boot video device is 0000:01:05.0
[   12.886059] PCI: Transparent bridge - 0000:00:14.4
[   12.886175] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.890021] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   12.890285] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   12.890550] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   12.890809] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   12.891068] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   12.891328] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   12.891597] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   12.891858] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   12.954426] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   12.954967] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   12.955455] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.955465] pnp: PnP ACPI init
[   12.957625] pnp: PnP ACPI: found 10 devices
[   12.957630] PnPBIOS: Disabled by ACPI PNP
[   12.957686] PCI: Using ACPI for IRQ routing
[   12.957689] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.991410] NET: Registered protocol family 8
[   12.991413] NET: Registered protocol family 20
[   12.991634] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   12.991638] pnp: 00:08: ioport range 0x200-0x20f has been reserved
[   12.991641] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   12.991928] PCI: Bridge: 0000:00:01.0
[   12.991931]   IO window: 9000-9fff
[   12.991936]   MEM window: c0100000-c01fffff
[   12.991940]   PREFETCH window: d0000000-dfffffff
[   12.991952] PCI: Bus 10, cardbus bridge: 0000:09:01.0
[   12.991955]   IO window: 0000a400-0000a4ff
[   12.991962]   IO window: 0000a800-0000a8ff
[   12.991969]   PREFETCH window: 60000000-63ffffff
[   12.991976]   MEM window: 64000000-67ffffff
[   12.991982] PCI: Bridge: 0000:00:14.4
[   12.991986]   IO window: a000-afff
[   12.991994]   MEM window: c0200000-c02fffff
[   12.992000]   PREFETCH window: 60000000-63ffffff
[   12.992047] PCI: Enabling device 0000:09:01.0 (0000 -> 0003)
[   12.992057] ACPI: PCI Interrupt 0000:09:01.0[A] -> GSI 20 (level, low) -> IRQ 16
[   12.992094] NET: Registered protocol family 2
[   13.031403] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.031623] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.033552] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.034986] TCP: Hash tables configured (established 131072 bind 65536)
[   13.034992] TCP reno registered
[   13.043529] checking if image is initramfs... it is
[   13.790187] Freeing initrd memory: 6781k freed
[   13.790884] audit: initializing netlink socket (disabled)
[   13.790908] audit(1180758964.700:1): initialized
[   13.791040] highmem bounce pool size: 64 pages
[   13.791132] VFS: Disk quotas dquot_6.5.1
[   13.791164] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.791242] io scheduler noop registered
[   13.791246] io scheduler anticipatory registered
[   13.791248] io scheduler deadline registered
[   13.791261] io scheduler cfq registered (default)
[   14.466922] isapnp: Scanning for PnP cards...
[   14.821811] isapnp: No Plug & Play device found
[   14.858915] Real Time Clock Driver v1.12ac
[   14.858984] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.859950] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   14.859964] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   14.860047] mice: PS/2 mouse device common for all mice
[   14.860712] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.861027] input: Macintosh mouse button emulation as /class/input/input0
[   14.861067] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.861072] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.861420] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   14.865550] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.865556] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.865724] EISA: Probing bus 0 at eisa.0
[   14.865739] Cannot allocate resource for EISA slot 1
[   14.865771] Cannot allocate resource for EISA slot 8
[   14.865774] EISA: Detected 0 cards.
[   14.895898] TCP cubic registered
[   14.895912] NET: Registered protocol family 1
[   14.895943] Using IPI No-Shortcut mode
[   14.896034] ACPI: (supports S0 S3 S4 S5)
[   14.896095]   Magic number: 11:151:615
[   14.896207]   hash matches device ptye5
[   14.896767] Freeing unused kernel memory: 328k freed
[   14.898380] Time: tsc clocksource has been installed.
[   14.912897] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.124279] Capability LSM initialized
[   16.163762] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.163770] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.163778] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   16.175202] ACPI: Thermal Zone [THRM] (51 C)
[   16.611560] usbcore: registered new interface driver usbfs
[   16.611596] usbcore: registered new interface driver hub
[   16.611624] usbcore: registered new device driver usb
[   16.612469] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.612522] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[   16.612540] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   16.612754] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   16.612779] ohci_hcd 0000:00:13.0: irq 18, io mem 0xc0000000
[   16.701826] usb usb1: configuration #1 chosen from 1 choice
[   16.701861] hub 1-0:1.0: USB hub found
[   16.701877] hub 1-0:1.0: 4 ports detected
[   16.805647] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[   16.805672] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   16.805699] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   16.805721] ohci_hcd 0000:00:13.1: irq 18, io mem 0xc0001000
[   16.840855] 8139too Fast Ethernet driver 0.9.28
[   16.865649] usb usb2: configuration #1 chosen from 1 choice
[   16.865685] hub 2-0:1.0: USB hub found
[   16.865701] hub 2-0:1.0: 4 ports detected
[    3.976000] Time: acpi_pm clocksource has been installed.
[    4.064000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[    4.064000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.064000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    4.064000] ehci_hcd 0000:00:13.2: irq 18, io mem 0xc0002000
[    4.064000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.064000] usb usb3: configuration #1 chosen from 1 choice
[    4.064000] hub 3-0:1.0: USB hub found
[    4.064000] hub 3-0:1.0: 8 ports detected
[    4.168000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.168000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[    4.168000] ATIIXP: chipset revision 0
[    4.168000] ATIIXP: not 100% native mode: will probe irqs later
[    4.168000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[    4.168000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[    4.168000] Probing IDE interface ide0...
[    4.456000] hda: TOSHIBA MK6026GAX, ATA DISK drive
[    5.128000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.176000] Probing IDE interface ide1...
[    5.912000] hdc: TSSTcorpCDW/DVD TS-L462C, ATAPI CD/DVD-ROM drive
[    6.584000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.644000] SCSI subsystem initialized
[    6.648000] libata version 2.20 loaded.
[    6.652000] ACPI: PCI Interrupt 0000:09:02.0[A] -> GSI 21 (level, low) -> IRQ 20
[    6.652000] eth0: RealTek RTL8139 at 0xf885c000, 00:c0:9f:dc:d7:91, IRQ 20
[    6.652000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.656000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    6.668000] hda: max request size: 128KiB
[    6.700000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
[    6.700000] hda: cache flushes supported
[    6.700000]  hda: hda1 hda2 hda3
[    6.780000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[    6.780000] Uniform CD-ROM driver Revision: 3.20
[    7.036000] Attempting manual resume
[    7.036000] swsusp: Resume From Partition 3:3
[    7.036000] PM: Checking swsusp image.
[    7.036000] PM: Resume from disk failed.
[    7.068000] kjournald starting.  Commit interval 5 seconds
[    7.068000] EXT3-fs: mounted filesystem with ordered data mode.
[   19.336000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.648000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.664000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.676000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   20.036000] ath_hal: module license 'Proprietary' taints kernel.
[   20.036000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   20.108000] Yenta: CardBus bridge found at 0000:09:01.0 [1179:ff31]
[   20.108000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.108000] Yenta: Routing CardBus interrupts to PCI
[   20.108000] Yenta TI: socket 0000:09:01.0, mfunc 0x015c1d22, devctl 0x44
[   20.124000] input: PC Speaker as /class/input/input2
[   20.248000] wlan: 0.8.4.2 (0.9.3)
[   20.280000] ath_pci: 0.9.4.5 (0.9.3)
[   20.340000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   20.340000] Socket status: 30000010
[   20.340000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   20.340000] cs: IO port probe 0xa000-0xafff: clean.
[   20.340000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   20.340000] pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x63ffffff
[   20.340000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   20.468000] MC'97 0 converters and GPIO not ready (0x1)
[   20.468000] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 22 (level, low) -> IRQ 21
[   21.156000] ath_rate_sample: 1.2 (0.9.3)
[   21.156000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   21.156000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   21.156000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   21.156000] wifi0: mac 7.8 phy 4.5 radio 5.6
[   21.156000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   21.156000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   21.156000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   21.156000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   21.156000] wifi0: Use hw queue 8 for CAB traffic
[   21.156000] wifi0: Use hw queue 9 for beacons
[   21.192000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   21.192000] synaptics: Toshiba Satellite L25                     detected, limiting rate to 40pps.
[   21.196000] wifi0: Atheros 5212: mem=0xc0200000, irq=21
[   21.236000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   21.244000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   21.448000] NET: Registered protocol family 10
[   21.448000] lo: Disabled Privacy Extensions
[   21.584000] pccard: PCMCIA card inserted into slot 0
[   21.584000] cs: memory probe 0xc0200000-0xc02fffff: excluding 0xc0200000-0xc021ffff
[   21.596000] pcmcia: registering new device pcmcia0.0
[   21.636000] cs: IO port probe 0x100-0x3af: clean.
[   21.640000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   21.640000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   21.640000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   21.644000] cs: IO port probe 0xa00-0xaff: clean.
[   21.792000] lp: driver loaded but no devices found
[   21.820000] Adding 506036k swap on /dev/disk/by-uuid/9c6d9bfc-f214-4086-bdbe-d4c856eb1c52.  Priority:-1 extents:1 across:506036k
[   21.932000] EXT3 FS on hda2, internal journal
[   22.152000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   22.216000] NTFS volume version 3.1.
[   22.936000] No dock devices found.
[   23.036000] ACPI: Battery Slot [BAT1] (battery present)
[   23.084000] ibm_acpi: ec object not found
[   23.132000] Using specific hotkey driver
[   23.208000] input: Power Button (FF) as /class/input/input4
[   23.212000] ACPI: Power Button (FF) [PWRF]
[   23.256000] input: Lid Switch as /class/input/input5
[   23.264000] ACPI: Lid Switch [LID]
[   23.308000] input: Power Button (CM) as /class/input/input6
[   23.312000] ACPI: Power Button (CM) [PWRB]
[   23.380000] ACPI: AC Adapter [ACAD] (on-line)
[   23.460000] pcc_acpi: loading...
[   27.748000] eth0: link down
[   27.752000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.436000] [fglrx] Maximum main memory to use for locked dma buffers: 1292 MBytes.
[   29.440000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   29.488000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   29.848000] ppdev: user-space parallel port driver
[   31.140000] [fglrx] total      GART = 130023424
[   31.140000] [fglrx] free       GART = 114032640
[   31.140000] [fglrx] max single GART = 114032640
[   31.140000] [fglrx] total      LFB  = 134217728
[   31.140000] [fglrx] free       LFB  = 122679296
[   31.140000] [fglrx] max single LFB  = 122679296
[   31.140000] [fglrx] total      Inv  = 0
[   31.140000] [fglrx] free       Inv  = 0
[   31.140000] [fglrx] max single Inv  = 0
[   31.140000] [fglrx] total      TIM  = 0
[   31.928000] ath0: no IPv6 routers present
[   32.668000] apm: BIOS not found.
[   32.876000] Bluetooth: Core ver 2.11
[   32.876000] NET: Registered protocol family 31
[   32.876000] Bluetooth: HCI device and connection manager initialized
[   32.876000] Bluetooth: HCI socket layer initialized
[   32.924000] Bluetooth: L2CAP ver 2.8
[   32.924000] Bluetooth: L2CAP socket layer initialized
[   33.076000] Bluetooth: RFCOMM socket layer initialized
[   33.076000] Bluetooth: RFCOMM TTY layer initialized
[   33.076000] Bluetooth: RFCOMM ver 1.8



ifconfig:
ath0      Link encap:Ethernet  HWaddr 00:11:F5:92:25:54  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f5ff:fe92:2554/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2078387 (1.9 MiB)  TX bytes:325298 (317.6 KiB)

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:DC:D7:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-92-25-54-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10064 errors:0 dropped:0 overruns:0 frame:37
          TX packets:1809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2836906 (2.7 MiB)  TX bytes:380936 (372.0 KiB)
          Interrupt:21 





iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"wrtlol"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:16:B6:18:21:BA   
          Bit Rate:48 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/94  Signal level=-54 dBm  Noise level=-95 dBm
          Rx invalid nwid:3  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ugm6hr on 2007-06-02
Do you use Network Manager to auto-connect with a WPA wireless router?  If so - I think it is a known issue with Network Manager that has been reported.  They feel it is some kind of conflict between the wireless driver for Atheros5005G and Network Manager.

I had the same problem - but stuck with Network Manager because it's so easy to use, and just went for WEP instead.  If you think that level of security is enough, it's the easiest way to sort it.

Otherwise, check the advice here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37821](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37821)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/64173](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/64173)

---

### Post by seanp2k on 2007-06-02
I do use WEP.  By "Network Manager" do you mean the two computers in the launchbar tray area that bring up a window that says "network settings"?  I used that to enter my wep code, but if that's the problem I can uninstall it and just configure through CLI.

---

### Post by ugm6hr on 2007-06-02
> **seanp2k said:**
> I do use WEP.  By "Network Manager" do you mean the two computers in the launchbar tray area that bring up a window that says "network settings"?  I used that to enter my wep code, but if that's the problem I can uninstall it and just configure through CLI.

If you use WEP, then Network Manager isn't the problem (I think).  And yes - it is the 2 computers that bring up a list of networks when you click on it.  Although I believe it should be 4 grey vertical bars if you use it in "roaming" mode.

---

### Post by seanp2k on 2007-06-03
I think I have resolved this issue by
-disabling Legacy USB support in BIOS
-Hardcoding an IP address through Network Manager
-Hardcoding a gateway and subnet mask through Network Manager

Basically it avoids DHCP.  It could also have been the legacy USB support, I was reading other people having problems with the ATI Mobility chipset's northbridge or southbridge (i forget which) that they resolved by disabling legacy USB support.

Now to see if my Logitech MX510 will last more than 20-50 clicks.  Hopefully that is resolved as well.

Thread changed to Resolved.  Thanks.  Hope this helps anyone with a similar problem.

---

