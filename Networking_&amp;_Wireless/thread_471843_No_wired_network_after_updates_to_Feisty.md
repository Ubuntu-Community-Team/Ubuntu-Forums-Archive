---
title: "No wired network after updates to Feisty"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by luishrd on 2007-06-12
Hello,

Dell Poweredge 400SC, Feiysty Fawn 7.04, Ethernet card shows up as ' Intel 8254OEM Gigabit Ethernet Controller', in the 'Hardware Information' but its not present on 'Network Settings'. I get a 'No network connection' tooltip when i hover over the network indicator next to the clock.

It was working fine until i rebooted for the last updates.

I am sooooooo lost.

BTW: If i boot from my old windows partition, the network works fine, wich means its all on the linux part.

Thanks

Edit: tried booting to the previous 2.6.20.15 kernel and no network either, I really did break my system this time LOL.

---

### Post by arunkv on 2007-06-13
Can you provide the outputs of **dmesg** and **lspci** to see if there's some issue being reported?

---

### Post by Frankenfatz on 2007-06-13
I've got an Intel 82541 Gigabit card, and had the exact same problem this morning, so at the very least you're not alone.

But being that I very recently (days ago) switched to Ubuntu I am also totally lost as to a solution.

---

### Post by luishrd on 2007-06-16
Here it is:

:~$ dmesg

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fe74000 end: 000000003ff74000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003ff74000 size: 0000000000002000 end: 000000003ff76000 type: 4
[    0.000000] copy_e820_map() start: 000000003ff76000 size: 0000000000021000 end: 000000003ff97000 type: 3
[    0.000000] copy_e820_map() start: 000000003ff97000 size: 0000000000069000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fecf0000 size: 0000000000001000 end: 00000000fecf1000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000070000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000010000 end: 00000000fee10000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff74000 (usable)
[    0.000000]  BIOS-e820: 000000003ff74000 - 000000003ff76000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff76000 - 000000003ff97000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff97000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 262004) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262004
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262004
[    0.000000] On node 0 totalpages: 262004
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32374 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000feb90
[    0.000000] ACPI: RSDT (v001 DELL    PE400SC 0x00000007 ASL  0x00000061) @ 0x000fd146
[    0.000000] ACPI: FADT (v001 DELL    PE400SC 0x00000007 ASL  0x00000061) @ 0x000fd17e
[    0.000000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffc8cf6
[    0.000000] ACPI: MADT (v001 DELL    PE400SC 0x00000007 ASL  0x00000061) @ 0x000fd1f2
[    0.000000] ACPI: BOOT (v001 DELL    PE400SC 0x00000007 ASL  0x00000061) @ 0x000fd25e
[    0.000000] ACPI: ASF! (v016 DELL    PE400SC 0x00000007 ASL  0x00000061) @ 0x000fd286
[    0.000000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Detected 2394.072 MHz processor.
[   12.583002] Built 1 zonelists.  Total pages: 259958
[   12.583005] Kernel command line: root=UUID=f45abacd-1a60-4da4-bbbe-b69a1e003a6b ro quiet splash
[   12.583172] mapped APIC to ffffd000 (fee00000)
[   12.583175] mapped IOAPIC to ffffc000 (fec00000)
[   12.583178] Enabling fast FPU save and restore... done.
[   12.583181] Enabling unmasked SIMD FPU exception support... done.
[   12.583191] Initializing CPU#0
[   12.583257] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   12.585005] Console: colour VGA+ 80x25
[   12.585372] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.585787] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.612793] Memory: 1027584k/1048016k available (1992k kernel code, 19724k reserved, 893k data, 328k init, 130512k highmem)
[   12.612804] virtual kernel memory layout:
[   12.612805]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   12.612807]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.612808]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   12.612809]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   12.612810]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   12.612811]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   12.612813]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   12.612816] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.691214] Calibrating delay using timer specific routine.. 4807.71 BogoMIPS (lpj=9615432)
[   12.691262] Security Framework v1.0.0 initialized
[   12.691270] SELinux:  Disabled at boot.
[   12.691288] Mount-cache hash table entries: 512
[   12.691450] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   12.691464] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   12.691467] CPU: L2 cache: 512K
[   12.691469] CPU: Physical Processor ID: 0
[   12.691472] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   12.691484] Compat vDSO mapped to ffffe000.
[   12.691488] Remapping vsyscall page to ffffe000
[   12.691502] Checking 'hlt' instruction... OK.
[   12.707160] SMP alternatives: switching to UP code
[   12.707541] Early unpacking initramfs... done
[   13.038482] ACPI: Core revision 20060707
[   13.038937] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   13.063005] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[   13.063028] SMP alternatives: switching to SMP code
[   13.063147] Booting processor 1/1 eip 3000
[   13.073405] Initializing CPU#1
[   13.154309] Calibrating delay using timer specific routine.. 4788.35 BogoMIPS (lpj=9576703)
[   13.154319] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   13.154331] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   13.154334] CPU: L2 cache: 512K
[   13.154336] CPU: Physical Processor ID: 0
[   13.154339] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   13.154533] CPU1: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[   13.154578] Total of 2 processors activated (9596.06 BogoMIPS).
[   13.154711] ENABLING IO-APIC IRQs
[   13.154899] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.302070] checking TSC synchronization across 2 CPUs: passed.
[    0.003999] Brought up 2 CPUs
[    0.050361] migration_cost=189
[    0.050702] Booting paravirtualized kernel on bare hardware
[    0.050792] Time: 11:33:00  Date: 05/16/107
[    0.050826] NET: Registered protocol family 16
[    0.050938] EISA bus registered
[    0.050944] ACPI: bus type pci registered
[    0.051013] PCI: PCI BIOS revision 2.10 entry at 0xfba64, last bus=2
[    0.051015] PCI: Using configuration type 1
[    0.051017] Setting up standard PCI resources
[    0.077168] ACPI: Interpreter enabled
[    0.077172] ACPI: Using IOAPIC for interrupt routing
[    0.081702] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.081712] PCI: Probing PCI hardware (bus 00)
[    0.081736] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.084113] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.084117] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.084414] Boot video device is 0000:01:00.0
[    0.084598] PCI: Transparent bridge - 0000:00:1e.0
[    0.084627] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.252820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.269668] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.270422] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.271179] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.271950] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.272729] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.273504] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.274276] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.275034] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.275231] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.275244] pnp: PnP ACPI init
[    0.304642] pnp: PnP ACPI: found 13 devices
[    0.304648] PnPBIOS: Disabled by ACPI PNP
[    0.304724] PCI: Using ACPI for IRQ routing
[    0.304729] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.310941] NET: Registered protocol family 8
[    0.310943] NET: Registered protocol family 20
[    0.315990] pnp: 00:0c: ioport range 0x800-0x85f could not be reserved
[    0.315994] pnp: 00:0c: ioport range 0xc00-0xc7f has been reserved
[    0.315997] pnp: 00:0c: ioport range 0x860-0x8ff could not be reserved
[    0.316438] PCI: Bridge: 0000:00:01.0
[    0.316440]   IO window: disabled.
[    0.316446]   MEM window: fc000000-feafffff
[    0.316450]   PREFETCH window: e0000000-efffffff
[    0.316455] PCI: Bridge: 0000:00:1e.0
[    0.316459]   IO window: d000-dfff
[    0.316465]   MEM window: fbf00000-fbffffff
[    0.316469]   PREFETCH window: disabled.
[    0.316487] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.316525] NET: Registered protocol family 2
[    0.363468] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.363628] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.364182] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.364481] TCP: Hash tables configured (established 131072 bind 65536)
[    0.364485] TCP reno registered
[    0.375546] checking if image is initramfs... it is
[    1.031571] Freeing initrd memory: 7004k freed
[    1.031766] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    1.031769] Simple Boot Flag at 0x7a set to 0x1
[    1.032058] audit: initializing netlink socket (disabled)
[    1.032070] audit(1181993580.836:1): initialized
[    1.032226] highmem bounce pool size: 64 pages
[    1.032350] VFS: Disk quotas dquot_6.5.1
[    1.032374] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.032430] io scheduler noop registered
[    1.032434] io scheduler anticipatory registered
[    1.032437] io scheduler deadline registered
[    1.032450] io scheduler cfq registered (default)
[    1.032794] isapnp: Scanning for PnP cards...
[    1.387307] isapnp: No Plug & Play device found
[    1.421408] Real Time Clock Driver v1.12ac
[    1.421470] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.421594] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.421793] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.422545] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.422857] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.423139] mice: PS/2 mouse device common for all mice
[    1.423963] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.424145] input: Macintosh mouse button emulation as /class/input/input0
[    1.424197] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.424201] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.424483] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.427503] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.427510] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.427665] EISA: Probing bus 0 at eisa.0
[    1.427708] EISA: Detected 0 cards.
[    1.457766] TCP cubic registered
[    1.457775] NET: Registered protocol family 1
[    1.457803] Starting balanced_irq
[    1.457811] Using IPI No-Shortcut mode
[    1.457930] ACPI: (supports S0 S1 S4 S5)
[    1.457981]   Magic number: 11:396:580
[    1.458357] Freeing unused kernel memory: 328k freed
[    1.461562] Time: tsc clocksource has been installed.
[    2.733650] Capability LSM initialized
[    3.398751] SCSI subsystem initialized
[    3.407046] libata version 2.20 loaded.
[    3.414092] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.414117] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 16
[    3.414144] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.414223] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    3.414272] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    3.414299] scsi0 : ata_piix
[    3.414383] ata1: port disabled. ignoring.
[    3.426066] scsi1 : ata_piix
[    3.430016] usbcore: registered new interface driver usbfs
[    3.430054] usbcore: registered new interface driver hub
[    3.430098] usbcore: registered new device driver usb
[    3.517743] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[    3.517749] Copyright (c) 1999-2006 Intel Corporation.
[    3.589892] USB Universal Host Controller Interface driver v3.0
[    3.620723] FDC 0 is a post-1991 82077
[    3.905783] ata2.00: ATAPI, max UDMA/66
[    3.905788] ata2.01: ATAPI, max UDMA/33
[    4.069525] ata2.00: configured for UDMA/66
[    4.233232] ata2.01: configured for UDMA/33
[    4.242428] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DRU-820A  1.0b PQ: 0 ANSI: 5
[    4.243559] scsi 1:0:1:0: CD-ROM            _NEC     DVD_RW ND-2500A  1.07 PQ: 0 ANSI: 5
[    4.251553] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    4.251573] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 16
[    4.251592] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.251643] ata3: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fe12 bmdma 0x0001fea0 irq 16
[    4.251690] ata4: SATA max UDMA/133 cmd 0x0001fe20 ctl 0x0001fe32 bmdma 0x0001fea8 irq 16
[    4.251706] scsi2 : ata_piix
[    4.413847] ata3.00: ata_hpa_resize 1: sectors = 398297088, hpa_sectors = 398297088
[    4.413855] ata3.00: ATA-7: Maxtor 6V200E0, VA111680, max UDMA/133
[    4.413858] ata3.00: 398297088 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    4.421842] ata3.00: ata_hpa_resize 1: sectors = 398297088, hpa_sectors = 398297088
[    4.421847] ata3.00: configured for UDMA/133
[    4.421860] scsi3 : ata_piix
[    4.585554] ata4.00: ata_hpa_resize 1: sectors = 490234752, hpa_sectors = 490234752
[    4.585560] ata4.00: ATA-7: Maxtor 7L250S0, BACE1G20, max UDMA/133
[    4.585563] ata4.00: 490234752 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    4.593508] ata4.00: ata_hpa_resize 1: sectors = 490234752, hpa_sectors = 490234752
[    4.593513] ata4.00: configured for UDMA/133
[    4.593658] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6V200E0   VA11 PQ: 0 ANSI: 5
[    4.601807] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 7L250S0   BACE PQ: 0 ANSI: 5
[    4.610336] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 17
[    4.610358] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.610365] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.610522] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.610567] ehci_hcd 0000:00:1d.7: debug port 1
[    4.610577] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    4.610591] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xffa80800
[    4.614462] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.614616] usb usb1: configuration #1 chosen from 1 choice
[    4.614661] hub 1-0:1.0: USB hub found
[    4.614673] hub 1-0:1.0: 8 ports detected
[    4.640534] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.640540] Uniform CD-ROM driver Revision: 3.20
[    4.640608] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.644040] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    4.644097] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    4.644627] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[    4.644649] sda: Write Protect is off
[    4.644654] sda: Mode Sense: 00 3a 00 00
[    4.644695] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.648352] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[    4.648374] sda: Write Protect is off
[    4.648378] sda: Mode Sense: 00 3a 00 00
[    4.648408] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.648414]  sda:<5>sr 1:0:0:0: Attached scsi generic sg0 type 5
[    4.652766] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    4.652998] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    4.653227] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[    4.672467]  sda1
[    4.673134] sd 2:0:0:0: Attached scsi disk sda
[    4.673561] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
[    4.673583] sdb: Write Protect is off
[    4.673587] sdb: Mode Sense: 00 3a 00 00
[    4.673620] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.673704] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
[    4.673725] sdb: Write Protect is off
[    4.673728] sdb: Mode Sense: 00 3a 00 00
[    4.673760] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.673764]  sdb: sdb1 sdb2 < sdb5 >
[    4.714285] sd 3:0:0:0: Attached scsi disk sdb
[    4.716413] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 18 (level, low) -> IRQ 16
[    4.955769] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    4.958079] e1000: 0000:02:0c.0: e1000_probe: The EEPROM Checksum Is Not Valid
[    4.981881] ACPI: PCI interrupt for device 0000:02:0c.0 disabled
[    4.981891] e1000: probe of 0000:02:0c.0 failed with error -5
[    4.982091] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 18
[    4.982109] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.982116] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.982182] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.982221] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000ff80
[    4.982392] usb usb2: configuration #1 chosen from 1 choice
[    4.982446] hub 2-0:1.0: USB hub found
[    4.982461] hub 2-0:1.0: 2 ports detected
[    5.083682] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    5.083700] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    5.083706] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.083745] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    5.083776] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    5.083945] usb usb3: configuration #1 chosen from 1 choice
[    5.084004] hub 3-0:1.0: USB hub found
[    5.084018] hub 3-0:1.0: 2 ports detected
[    5.087960] usb 1-1: configuration #1 chosen from 1 choice
[    5.088158] hub 1-1:1.0: USB hub found
[    5.088231] hub 1-1:1.0: 4 ports detected
[    5.115957] Attempting manual resume
[    5.115961] swsusp: Resume From Partition 8:21
[    5.115964] PM: Checking swsusp image.
[    5.116129] PM: Resume from disk failed.
[    5.145601] kjournald starting.  Commit interval 5 seconds
[    5.145617] EXT3-fs: mounted filesystem with ordered data mode.
[    5.187519] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 16
[    5.187532] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    5.187536] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.187565] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    5.187588] uhci_hcd 0000:00:1d.2: irq 16, io base 0x0000ff40
[    5.187696] usb usb4: configuration #1 chosen from 1 choice
[    5.187728] hub 4-0:1.0: USB hub found
[    5.187736] hub 4-0:1.0: 2 ports detected
[    5.291307] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 18
[    5.291320] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    5.291324] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    5.291352] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    5.291375] uhci_hcd 0000:00:1d.3: irq 18, io base 0x0000ff20
[    5.291482] usb usb5: configuration #1 chosen from 1 choice
[    5.291515] hub 5-0:1.0: USB hub found
[    5.291523] hub 5-0:1.0: 2 ports detected
[    5.742465] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    5.919326] usb 4-2: configuration #1 chosen from 1 choice
[   13.498626] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.508775] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.807328] intel_rng: Firmware space is locked read-only. If you can't or
[   13.807333] intel_rng: don't want to disable this in firmware setup, and if
[   13.807336] intel_rng: you are certain that your system has a functional
[   13.807339] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   13.817308] input: PC Speaker as /class/input/input1
[   13.902192] EDAC MC: Ver: 2.0.1 Apr 15 2007
[   13.905837] EDAC i82875p: i82875p init one
[   13.905918] PCI: Unable to reserve mem region #1:1000@fecf0000 for device 0000:00:06.0
[   13.906056] EDAC MC0: Giving out device to i82875p_edac i82875p: DEV 0000:00:00.0
[   14.014331] iTCO_vendor_support: vendor-support=0
[   14.015807] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   14.015937] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   14.015997] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.058975] parport: PnPBIOS parport detected.
[   14.059028] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   14.287773] Linux agpgart interface v0.102 (c) Dave Jones
[   14.529353] usbcore: registered new interface driver hiddev
[   14.636304] input: Logitech USB Receiver as /class/input/input2
[   14.636555] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2
[   14.664958] input: Logitech USB Receiver as /class/input/input3
[   14.665106] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2
[   14.665130] usbcore: registered new interface driver usbhid
[   14.665135] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   14.733325] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   14.733361] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   15.050968] intel8x0_measure_ac97_clock: measured 55612 usecs
[   15.050972] intel8x0: clocking to 48000
[   15.244553] fuse init (API version 7.8)
[   15.269331] lp0: using parport0 (interrupt-driven).
[   15.309475] Adding 3028212k swap on /dev/disk/by-uuid/60bdaa37-4064-4797-bdd6-decd7469755f.  Priority:-1 extents:1 across:3028212k
[   15.452398] EXT3 FS on sdb1, internal journal
[   17.063502] NET: Registered protocol family 17
[   22.354555] input: Power Button (FF) as /class/input/input4
[   22.354596] ACPI: Power Button (FF) [PWRF]
[   22.354665] input: Power Button (CM) as /class/input/input5
[   22.354700] ACPI: Power Button (CM) [VBTN]
[   22.466957] Using specific hotkey driver
[   22.612551] ibm_acpi: ec object not found
[   22.748022] No dock devices found.
[   22.830181] pcc_acpi: loading...
[   29.045749] ppdev: user-space parallel port driver
[   29.584188] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   29.584195] apm: disabled - APM is not SMP safe.
[   29.840889] Bluetooth: Core ver 2.11
[   29.840965] NET: Registered protocol family 31
[   29.840969] Bluetooth: HCI device and connection manager initialized
[   29.840974] Bluetooth: HCI socket layer initialized
[   29.866907] Bluetooth: L2CAP ver 2.8
[   29.866914] Bluetooth: L2CAP socket layer initialized
[   30.030819] Bluetooth: RFCOMM socket layer initialized
[   30.030843] Bluetooth: RFCOMM TTY layer initialized
[   30.030847] Bluetooth: RFCOMM ver 1.8
[   40.366726] NET: Registered protocol family 10
[   40.366875] lo: Disabled Privacy Extensions


========================== and lspci

:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GS] (rev a1)
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)


Thanks a lot for your help.

---

### Post by luishrd on 2007-06-16
Today I completely reinstalled Ubuntu using the Guided - Use entire disk option for partitioning to make sure everything was gone from the disk. Still no network, but the windows i have installed on the other HD works fine.

---

### Post by arunkv on 2007-06-16
Sorry, I got to look at the dmesg output only right now.

From dmesg, the lines relevant to networking are:

[INDENT][ 3.517743] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[ 3.517749] Copyright (c) 1999-2006 Intel Corporation.

[ 13.807328] intel_rng: Firmware space is locked read-only. If you can't or
[ 13.807333] intel_rng: don't want to disable this in firmware setup, and if
[ 13.807336] intel_rng: you are certain that your system has a functional
[ 13.807339] intel_rng: RNG, try using the 'no_fwh_detect' option.
[/INDENT]

The first set is for wired networking and the second set seems to wireless related. Since the Intel driver is loaded and yet your controller is not active, I have a feeling that the driver provided by default - version 7.3.15 - is not new enough to work with the 82540EM controller that you have. (This is my guess.) Intel has a newer driver at [http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=983&DwnldID=9180&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=983&DwnldID=9180&lang=eng) (version 7.5.5) which explicitly states that it supports your 82540EM controller. I would suggest that you install that version of the driver.

---

