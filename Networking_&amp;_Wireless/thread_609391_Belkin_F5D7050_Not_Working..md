---
title: "Belkin F5D7050 Not Working."
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by Cenkic on 2007-11-10
Heyas, fellow UBUNTU users, I'm having some complications in getting the wireless Belkin F5D7050 with driver RT73.  i'm wondering if anyone might know a way to make this little bugger to work properly.  My current attempts have included using NDISWRAPPER with the driver, but that doesn't want to work.  Heres some other info on the specs of my Belkin:


dmesg:
```
0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bee0000 (usable)
[    0.000000]  BIOS-e820: 000000003bee0000 - 000000003bee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bee3000 - 000000003bef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bf00000 (reserved)
[    0.000000]  BIOS-e820: 000000003c000000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3cc0
[    0.000000] Entering add_active_range(0, 0, 245472) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245472
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245472
[    0.000000] On node 0 totalpages: 245472
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 125 pages used for memmap
[    0.000000]   HighMem zone: 15971 pages, LIFO batch:3
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F83D0 checksum 0
[    0.000000] ACPI: RSDP 000F83D0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 3BEE3040, 0040 (r1 DELL    bMk     42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3BEE3100, 0074 (r1 DELL    bMk     42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3BEE31C0, 592F (r1 DELL    BMK         1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BEE0000, 0040
[    0.000000] ACPI: BOOT 3BEE8B40, 0028 (r1 DELL    bMk     42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 3BEE8C80, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 3BEE8DC0, 0038 (r1 DELL    bMk     42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 3BEE8E40, 003C (r1 DELL    bMk     42302E31 AWRD        0)
[    0.000000] ACPI: SLIC 3BEE8EC0, 0176 (r1 DELL    bMk     42302E31 AWRD  100000E)
[    0.000000] ACPI: APIC 3BEE8BC0, 0072 (r1 DELL    bMk     42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] Built 1 zonelists.  Total pages: 243555
[    0.000000] Kernel command line: root=UUID=5a34085f-45f2-4497-851d-564ba39fa06b ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1803.941 MHz processor.
[   13.645385] spurious 8259A interrupt: IRQ7.
[   13.648552] Console: colour VGA+ 80x25
[   13.648883] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.649450] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.667914] Memory: 961612k/981888k available (2015k kernel code, 19700k reserved, 916k data, 364k init, 64384k highmem)
[   13.667925] virtual kernel memory layout:
[   13.667926]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   13.667928]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.667929]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.667930]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.667932]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   13.667933]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   13.667934]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   13.667937] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.667975] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.668120] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   13.668126] hpet0: 3 32-bit timers, 25000000 Hz
[   13.749051] Calibrating delay using timer specific routine.. 3610.70 BogoMIPS (lpj=7221405)
[   13.749074] Security Framework v1.0.0 initialized
[   13.749082] SELinux:  Disabled at boot.
[   13.749095] Mount-cache hash table entries: 512
[   13.749214] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019
[   13.749223] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   13.749226] CPU: L2 Cache: 256K (64 bytes/line)
[   13.749229] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 00000019
[   13.749239] Compat vDSO mapped to ffffe000.
[   13.749250] Checking 'hlt' instruction... OK.
[   13.765158] SMP alternatives: switching to UP code
[   13.765331] Freeing SMP alternatives: 11k freed
[   13.765613] Early unpacking initramfs... done
[   14.096152] ACPI: Core revision 20070126
[   14.096226] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.100746] CPU0: AMD Sempron(tm) Processor 3400+ stepping 02
[   14.100765] Total of 1 processors activated (3610.70 BogoMIPS).
[   14.101066] ENABLING IO-APIC IRQs
[   14.101323] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   14.463711] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   14.463757] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   14.463759] ...trying to set up timer as Virtual Wire IRQ... failed.
[   14.503431] ...trying to set up timer as ExtINT IRQ... works.
[   14.747850] Brought up 1 CPUs
[   14.747978] Booting paravirtualized kernel on bare hardware
[   14.748057] Time:  4:26:15  Date: 10/06/107
[   14.748080] NET: Registered protocol family 16
[   14.748163] EISA bus registered
[   14.748167] ACPI: bus type pci registered
[   14.749203] PCI: PCI BIOS revision 3.00 entry at 0xfaea0, last bus=4
[   14.749206] PCI: Using configuration type 1
[   14.749207] Setting up standard PCI resources
[   14.752642] ACPI: EC: Look up EC in DSDT
[   14.758235] ACPI: Interpreter enabled
[   14.758238] ACPI: (supports S0 S1 S3 S4 S5)
[   14.758253] ACPI: Using IOAPIC for interrupt routing
[   14.767430] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.767440] PCI: Probing PCI hardware (bus 00)
[   14.768420] PCI: Transparent bridge - 0000:00:10.0
[   14.768457] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.768767] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   14.847089] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.847293] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
[   14.847491] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.847696] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
[   14.847894] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.848092] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.848291] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 *7 9 10 11 14 15)
[   14.848488] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.848687] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[   14.848891] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.849090] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   14.849288] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.849487] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   14.849686] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 *7 9 10 11 14 15)
[   14.849883] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.850083] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   14.850281] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 *15)
[   14.850478] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.850678] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[   14.850882] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[   14.851124] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   14.851351] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   14.851576] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   14.851807] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   14.852032] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   14.852257] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   14.852486] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[   14.852711] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   14.852936] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   14.853162] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   14.853389] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   14.853615] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   14.853842] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[   14.854067] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   14.854293] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   14.854520] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   14.854746] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   14.854972] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   14.855199] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   14.855425] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   14.855652] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   14.855767] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.855778] pnp: PnP ACPI init
[   14.855788] ACPI: bus type pnp registered
[   14.859906] pnp: PnP ACPI: found 9 devices
[   14.859909] ACPI: ACPI bus type pnp unregistered
[   14.859912] PnPBIOS: Disabled by ACPI PNP
[   14.859961] PCI: Using ACPI for IRQ routing
[   14.859966] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.948551] NET: Registered protocol family 8
[   14.948553] NET: Registered protocol family 20
[   14.948608] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   14.948611] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   14.948614] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   14.948617] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   14.948620] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   14.948623] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   14.948626] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[   14.948629] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[   14.948633] pnp: 00:01: iomem range 0xfec80000-0xfecbffff could not be reserved
[   14.948636] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[   14.948640] pnp: 00:01: iomem range 0x3c000000-0x3fffffff could not be reserved
[   14.948649] pnp: 00:07: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   14.948654] pnp: 00:08: iomem range 0xcec00-0xcffff has been reserved
[   14.948657] pnp: 00:08: iomem range 0xf0000-0xf7fff could not be reserved
[   14.948660] pnp: 00:08: iomem range 0xf8000-0xfbfff could not be reserved
[   14.948663] pnp: 00:08: iomem range 0xfc000-0xfffff could not be reserved
[   14.951559] Time: tsc clocksource has been installed.
[   14.951571] Switched to high resolution mode on CPU 0
[   14.978874] PCI: Bridge: 0000:00:02.0
[   14.978876]   IO window: a000-afff
[   14.978880]   MEM window: fd800000-fd8fffff
[   14.978883]   PREFETCH window: fd700000-fd7fffff
[   14.978886] PCI: Bridge: 0000:00:03.0
[   14.978888]   IO window: 8000-8fff
[   14.978891]   MEM window: fde00000-fdefffff
[   14.978893]   PREFETCH window: fdd00000-fddfffff
[   14.978896] PCI: Bridge: 0000:00:04.0
[   14.978898]   IO window: b000-bfff
[   14.978901]   MEM window: fdc00000-fdcfffff
[   14.978904]   PREFETCH window: fd900000-fd9fffff
[   14.978907] PCI: Bridge: 0000:00:10.0
[   14.978909]   IO window: 9000-9fff
[   14.978912]   MEM window: fdb00000-fdbfffff
[   14.978916]   PREFETCH window: fda00000-fdafffff
[   14.978929] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   14.978935] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   14.978942] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   14.978949] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   14.978962] NET: Registered protocol family 2
[   15.015480] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.015586] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   15.016862] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.017299] TCP: Hash tables configured (established 131072 bind 65536)
[   15.017303] TCP reno registered
[   15.027547] checking if image is initramfs... it is
[   15.674277] Freeing initrd memory: 7341k freed
[   15.674374] Simple Boot Flag at 0x3a set to 0x1
[   15.674654] audit: initializing netlink socket (disabled)
[   15.674667] audit(1194323175.288:1): initialized
[   15.674730] highmem bounce pool size: 64 pages
[   15.676244] VFS: Disk quotas dquot_6.5.1
[   15.676287] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.676376] io scheduler noop registered
[   15.676378] io scheduler anticipatory registered
[   15.676380] io scheduler deadline registered
[   15.676395] io scheduler cfq registered (default)
[   15.676414] Boot video device is 0000:00:05.0
[   15.690750] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   15.690772] assign_interrupt_mode Found MSI capability
[   15.690775] Allocate Port Service[0000:00:02.0:pcie00]
[   15.690830] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   15.690850] assign_interrupt_mode Found MSI capability
[   15.690853] Allocate Port Service[0000:00:03.0:pcie00]
[   15.690902] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.690923] assign_interrupt_mode Found MSI capability
[   15.690925] Allocate Port Service[0000:00:04.0:pcie00]
[   15.691034] isapnp: Scanning for PnP cards...
[   16.043746] isapnp: No Plug & Play device found
[   16.068841] Real Time Clock Driver v1.12ac
[   16.068920] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.070022] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.070233] input: Macintosh mouse button emulation as /class/input/input0
[   16.070334] PNP: No PS/2 controller found. Probing ports directly.
[   16.073077] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.073083] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.073243] mice: PS/2 mouse device common for all mice
[   16.073348] EISA: Probing bus 0 at eisa.0
[   16.073356] Cannot allocate resource for EISA slot 1
[   16.073359] Cannot allocate resource for EISA slot 2
[   16.073374] Cannot allocate resource for EISA slot 8
[   16.073376] EISA: Detected 0 cards.
[   16.073462] TCP cubic registered
[   16.073477] NET: Registered protocol family 1
[   16.073501] Using IPI No-Shortcut mode
[   16.073673]   Magic number: 15:276:413
[   16.074042] Freeing unused kernel memory: 364k freed
[   17.307222] AppArmor: AppArmor initialized<5>audit(1194323176.788:2):  type=1505 info="AppArmor initialized" pid=1245
[   17.314087] fuse init (API version 7.8)
[   17.319264] Failure registering capabilities with primary security module.
[   17.333168] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.218555] usbcore: registered new interface driver usbfs
[   18.218584] usbcore: registered new interface driver hub
[   18.218603] usbcore: registered new device driver usb
[   18.219303] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   18.219759] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   18.219771] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   18.219784] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   18.219788] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   18.239827] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   18.239851] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfe02f000
[   18.250504] SCSI subsystem initialized
[   18.254965] libata version 2.21 loaded.
[   18.298007] usb usb1: configuration #1 chosen from 1 choice
[   18.298036] hub 1-0:1.0: USB hub found
[   18.298046] hub 1-0:1.0: 8 ports detected
[   18.400115] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   18.400128] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[   18.400141] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   18.400144] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   18.400170] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   18.400201] ehci_hcd 0000:00:0b.1: debug port 1
[   18.400205] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   18.400218] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xfe02e000
[   18.400226] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.400305] usb usb2: configuration #1 chosen from 1 choice
[   18.400333] hub 2-0:1.0: USB hub found
[   18.400340] hub 2-0:1.0: 8 ports detected
[   18.506295] sata_nv 0000:00:0e.0: version 3.4
[   18.506727] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   18.506739] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
[   18.506779] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   18.506846] scsi0 : sata_nv
[   18.506889] scsi1 : sata_nv
[   18.506951] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001e000 irq 18
[   18.506955] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001e008 irq 18
[   18.970759] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   18.978989] ata1.00: ATA-7: WDC WD800JD-75MSA3, 10.01E04, max UDMA/133
[   18.978992] ata1.00: 156250000 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   18.986968] ata1.00: configured for UDMA/133
[   19.054637] usb 2-4: new high speed USB device using ehci_hcd and address 2
[   19.358135] usb 2-4: configuration #1 chosen from 1 choice
[   19.454175] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.618122] ata2.00: ATAPI: HL-DT-STDVD-ROM GDRH10N, 0D04, max UDMA/100
[   19.789925] ata2.00: configured for UDMA/100
[   19.790039] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JD-75MS 10.0 PQ: 0 ANSI: 5
[   19.793670] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDRH10N  0D04 PQ: 0 ANSI: 5
[   19.794146] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   19.794158] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 19
[   19.794201] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   19.794254] scsi2 : sata_nv
[   19.794294] scsi3 : sata_nv
[   19.794354] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001cc00 irq 19
[   19.794357] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001cc08 irq 19
[   20.029474] usb 1-5: new low speed USB device using ohci_hcd and address 2
[   20.105382] ata3: SATA link down (SStatus 0 SControl 300)
[   20.243547] usb 1-5: configuration #1 chosen from 1 choice
[   20.424999] ata4: SATA link down (SStatus 0 SControl 300)
[   20.435577] b44.c:v1.01 (Jun 16, 2006)
[   20.435999] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   20.436011] ACPI: PCI Interrupt 0000:04:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
[   20.436022] PCI: Setting latency timer of device 0000:04:07.0 to 64
[   20.439688] eth0: Broadcom 4400 10/100BaseT Ethernet 00:13:72:3b:31:a6
[   20.451480] sd 0:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
[   20.451510] sd 0:0:0:0: [sda] Write Protect is off
[   20.451513] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.451528] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.451586] sd 0:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
[   20.451595] sd 0:0:0:0: [sda] Write Protect is off
[   20.451597] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.451609] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.451615]  sda: sda1 sda2 < sda5 >
[   20.503460] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.507511] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   20.507531] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   20.529768] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   20.529773] Uniform CD-ROM driver Revision: 3.20
[   20.530059] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   20.548893] usb 1-6: new low speed USB device using ohci_hcd and address 3
[   20.714110] Attempting manual resume
[   20.714114] swsusp: Resume From Partition 8:5
[   20.714116] PM: Checking swsusp image.
[   20.714295] PM: Resume from disk failed.
[   20.756987] kjournald starting.  Commit interval 5 seconds
[   20.757000] EXT3-fs: mounted filesystem with ordered data mode.
[   20.763917] usb 1-6: configuration #1 chosen from 1 choice
[   20.771137] usbcore: registered new interface driver hiddev
[   20.776017] input: DELL DELL USB Keyboard as /class/input/input1
[   20.776030] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:0b.0-5
[   20.781953] input: A4Tech Wireless Battery Free Optical Mouse as /class/input/input2
[   20.781973] input: USB HID v1.10 Mouse [A4Tech Wireless Battery Free Optical Mouse] on usb-0000:00:0b.0-6
[   20.781989] usbcore: registered new interface driver usbhid
[   20.781993] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   27.175189] input: PC Speaker as /class/input/input3
[   29.699799] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.705220] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.763686] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   29.763715] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   29.774771] Linux agpgart interface v0.102 (c) Dave Jones
[   29.899840] nvidia: module license 'NVIDIA' taints kernel.
[   30.189518] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   30.189533] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 21
[   30.189541] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   30.189783] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   30.746653] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   30.746659] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 16
[   30.746679] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   30.833499] ieee80211_init: failed to initialize WME (err=-17)
[   30.845514] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   30.845552] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   30.845582] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   30.845631] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   30.851998] wmaster0: Selected rate control algorithm 'simple'
[   30.921730] usbcore: registered new interface driver rt2500usb
[   30.924236] usbcore: registered new interface driver rt73usb
[   31.611376] lp: driver loaded but no devices found
[   31.663089] Adding 2835432k swap on /dev/sda5.  Priority:-1 extents:1 across:2835432k
[   31.885418] EXT3 FS on sda1, internal journal
[   32.979747] No dock devices found.
[   33.093308] input: Power Button (FF) as /class/input/input4
[   33.097603] ACPI: Power Button (FF) [PWRF]
[   33.137486] input: Power Button (CM) as /class/input/input5
[   33.141722] ACPI: Power Button (CM) [PWRB]
[   33.389154] powernow-k8: Found 1 AMD Sempron(tm) Processor 3400+ processors (version 2.00.00)
[   33.389190] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xc
[   33.389193] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   34.826156] ppdev: user-space parallel port driver
[   34.950589] phy0 -> rt2500usb_enable_radio: Error - Register initialization failed.
[   35.000941] audit(1194323195.644:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4884 profile="/usr/sbin/cupsd"
[   35.065847] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   35.065853] apm: overridden by ACPI.
[   35.986549] Failure registering capabilities with primary security module.
[   18.176000] Marking TSC unstable due to: cpufreq changes.
[   18.180000] Time: hpet clocksource has been installed.
[   18.500000] Clocksource tsc unstable (delta = -145424697 ns)
[   19.268000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   19.268000] b44: eth0: Flow control is off for TX and off for RX.
[   21.312000] /dev/vmmon[5359]: Module vmmon: registered with major=10 minor=165
[   21.312000] /dev/vmmon[5359]: Module vmmon: initialized
[   23.764000] NET: Registered protocol family 17
[  122.104000] b44: eth0: Link is up at 100 Mbps, full duplex.
[  122.104000] b44: eth0: Flow control is off for TX and off for RX.
[246620.960000] audit(1194569799.144:4):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=7336 profile="/usr/sbin/cupsd"
[331222.104000] b44: eth0: Link is down.
[331255.104000] b44: eth0: Link is up at 100 Mbps, full duplex.
[331255.104000] b44: eth0: Flow control is off for TX and off for RX.
[331270.104000] b44: eth0: Link is down.
[331273.104000] b44: eth0: Link is up at 100 Mbps, full duplex.
[331273.104000] b44: eth0: Flow control is off for TX and off for RX.

```

Iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:13:72:3B:31:A6  
          inet addr:###.###.#.##  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:543370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27353 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46108351 (43.9 MB)  TX bytes:2327887 (2.2 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:###.#.#.#  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Any help would be greatly appriciated, Thank you!

~Cenkic

---

### Post by Goop on 2007-11-11
Sorry I can't help here, but I also have this problem, although I have not tried ndiswrapper. The list of supported WiFi cards says it can just be plugged in and used, but I get almost the same iwconfig result as the previous poster, apart from the fact that mine seems to already have associated.

---

