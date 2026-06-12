---
title: "Wired network adaptor not enabled following update"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by platinumwolf on 2007-11-03
Greetings. I appear to be having difficulty with my desktop (I'm on my laptop at the moment).  A little information first. I'm running 7.10, upgraded recently from 6.06 through each intervening version. I'm running a systemax computer that I got for free with a course in networking from Vincennes University (US Navy paid for it). It has a Silicon Integrated Systems 900 Fast Ethernet adapter on the motherboard. I installed the latest and greatest updates last night through update manager, and when I turned on the computer this morning it wouldn't recognize that it's plugged into the network. I'm seriously considering a fresh installation, but thought I'd ask on here to see if anyone had any input for me. Here's some commonly asked for output from the computer in question:

 lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       version: 90
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=11 mingnt=52
root@darkeyedbunny:/home/lan# ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@darkeyedbunny:/home/lan# dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004fff0000 (usable)
[    0.000000]  BIOS-e820: 000000004fff0000 - 000000004fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004fff3000 - 0000000050000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 383MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5710
[    0.000000] Entering add_active_range(0, 0, 327664) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   327664
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   327664
[    0.000000] On node 0 totalpages: 327664
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 767 pages used for memmap
[    0.000000]   HighMem zone: 97521 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F71A0 checksum 0
[    0.000000] ACPI: RSDP 000F71A0, 0014 (r0 AWARD )
[    0.000000] ACPI: RSDT 4FFF3000, 002C (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 4FFF3040, 0074 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 4FFF30C0, 3692 (r1 AWARD  AWRDACPI     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 4FFF0000, 0040
[    0.000000] ACPI: APIC 4FFF6780, 0068 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[    0.000000] Built 1 zonelists.  Total pages: 325105
[    0.000000] Kernel command line: root=UUID=516f21d2-9b2d-410e-bd44-ecf06ed25f07 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2933.685 MHz processor.
[   16.118390] Console: colour VGA+ 80x25
[   16.119100] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.120182] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.166309] Memory: 1287448k/1310656k available (2015k kernel code, 22000k reserved, 916k data, 364k init, 393152k highmem)
[   16.166321] virtual kernel memory layout:
[   16.166322]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   16.166324]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.166325]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.166326]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.166327]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   16.166328]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   16.166329]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   16.166333] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.166398] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.246417] Calibrating delay using timer specific routine.. 5871.18 BogoMIPS (lpj=11742366)
[   16.246462] Security Framework v1.0.0 initialized
[   16.246472] SELinux:  Disabled at boot.
[   16.246489] Mount-cache hash table entries: 512
[   16.246691] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   16.246701] monitor/mwait feature present.
[   16.246703] using mwait in idle threads.
[   16.246711] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   16.246714] CPU: L2 cache: 256K
[   16.246718] CPU: Hyper-Threading is disabled
[   16.246720] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000
[   16.246733] Compat vDSO mapped to ffffe000.
[   16.246755] Checking 'hlt' instruction... OK.
[   16.262554] SMP alternatives: switching to UP code
[   16.262872] Freeing SMP alternatives: 11k freed
[   16.263235] Early unpacking initramfs... done
[   16.566849] ACPI: Core revision 20070126
[   16.566919] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.569953] CPU0: Intel(R) Celeron(R) CPU 2.93GHz stepping 01
[   16.569996] Total of 1 processors activated (5871.18 BogoMIPS).
[   16.570104] ENABLING IO-APIC IRQs
[   16.570285] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.714406] Brought up 1 CPUs
[   16.714570] Booting paravirtualized kernel on bare hardware
[   16.714655] Time:  7:49:47  Date: 10/03/107
[   16.714690] NET: Registered protocol family 16
[   16.714845] EISA bus registered
[   16.714865] ACPI: bus type pci registered
[   16.751812] PCI: PCI BIOS revision 2.10 entry at 0xfbaf0, last bus=1
[   16.751814] PCI: Using configuration type 1
[   16.751816] Setting up standard PCI resources
[   16.760300] ACPI: EC: Look up EC in DSDT
[   16.763798] ACPI: Interpreter enabled
[   16.763804] ACPI: (supports S0 S3 S4 S5)
[   16.763828] ACPI: Using IOAPIC for interrupt routing
[   16.770867] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.770876] PCI: Probing PCI hardware (bus 00)
[   16.771814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.786150] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   16.786264] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.786432] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   16.786550] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.786657] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   16.786765] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.786874] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   16.786979] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   16.787167] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.787184] pnp: PnP ACPI init
[   16.787198] ACPI: bus type pnp registered
[   16.790311] pnp: PnP ACPI: found 11 devices
[   16.790316] ACPI: ACPI bus type pnp unregistered
[   16.790322] PnPBIOS: Disabled by ACPI PNP
[   16.790430] PCI: Using ACPI for IRQ routing
[   16.790434] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.797402] NET: Registered protocol family 8
[   16.797405] NET: Registered protocol family 20
[   16.797532] pnp: 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   16.797536] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   16.797539] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   16.797542] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   16.798348] Time: tsc clocksource has been installed.
[   16.828089] PCI: Bridge: 0000:00:01.0
[   16.828091]   IO window: disabled.
[   16.828098]   MEM window: e4000000-e5ffffff
[   16.828103]   PREFETCH window: d0000000-dfffffff
[   16.828134] NET: Registered protocol family 2
[   16.866396] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.866607] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.868773] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.869522] TCP: Hash tables configured (established 131072 bind 65536)
[   16.869528] TCP reno registered
[   16.878557] checking if image is initramfs... it is
[   17.330280] Switched to high resolution mode on CPU 0
[   17.462893] Freeing initrd memory: 7082k freed
[   17.463553] audit: initializing netlink socket (disabled)
[   17.463574] audit(1194076188.028:1): initialized
[   17.463671] highmem bounce pool size: 64 pages
[   17.466616] VFS: Disk quotas dquot_6.5.1
[   17.466704] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.466862] io scheduler noop registered
[   17.466865] io scheduler anticipatory registered
[   17.466867] io scheduler deadline registered
[   17.466899] io scheduler cfq registered (default)
[   17.550218] Boot video device is 0000:01:00.0
[   17.550499] isapnp: Scanning for PnP cards...
[   17.902355] isapnp: No Plug & Play device found
[   17.993999] Real Time Clock Driver v1.12ac
[   17.994193] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.994322] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.996194] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.997562] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.997905] input: Macintosh mouse button emulation as /class/input/input0
[   17.998043] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   17.998047] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   17.998475] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.998484] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.998800] mice: PS/2 mouse device common for all mice
[   17.999001] EISA: Probing bus 0 at eisa.0
[   17.999012] Cannot allocate resource for EISA slot 1
[   17.999021] Cannot allocate resource for EISA slot 4
[   17.999037] EISA: Detected 0 cards.
[   17.999258] TCP cubic registered
[   17.999288] NET: Registered protocol family 1
[   17.999318] Using IPI No-Shortcut mode
[   17.999546]   Magic number: 15:781:823
[   17.999693]   hash matches device ptyt3
[   18.000236] Freeing unused kernel memory: 364k freed
[   18.022215] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.305179] AppArmor: AppArmor initialized<5>audit(1194076190.028:2):  type=1505 info="AppArmor initialized" pid=1179
[   19.316500] fuse init (API version 7.8)
[   19.325007] Failure registering capabilities with primary security module.
[   19.336138] ACPI: Fan [FAN] (on)
[   19.343571] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.345087] ACPI: Thermal Zone [THRM] (57 C)
[   20.250499] SCSI subsystem initialized
[   20.257963] libata version 2.21 loaded.
[   20.262048] pata_sis 0000:00:02.5: version 0.5.1
[   20.262100] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 16
[   20.262268] scsi0 : pata_sis
[   20.262348] scsi1 : pata_sis
[   20.262488] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014000 irq 14
[   20.262493] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014008 irq 15
[   20.297068] usbcore: registered new interface driver usbfs
[   20.297112] usbcore: registered new interface driver hub
[   20.297154] usbcore: registered new device driver usb
[   20.298221] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.416265] sis900.c: v1.08.10 Apr. 2 2006
[   20.434043] ata1.00: Host Protected Area detected:
[   20.434045]  current size: 56693386 sectors
[   20.434047]  native size: 78165360 sectors
[   20.434173] ata1.00: native size increased to 78165360 sectors
[   20.434177] ata1.00: ATA-6: WDC WD400BB-00JHC0, 05.01C05, max UDMA/100
[   20.434180] ata1.00: 78165360 sectors, multi 16: LBA 
[   20.434426] ata1.01: ATA-6: Maxtor 4D040H2, DAH017K0, max UDMA/100
[   20.434430] ata1.01: 80043264 sectors, multi 16: LBA 
[   20.442064] ata1.00: configured for UDMA/100
[   20.458178] ata1.01: configured for UDMA/100
[   20.475321] Floppy drive(s): fd0 is 1.44M
[   20.515149] FDC 0 is a post-1991 82077
[   20.793822] ata2.00: ATAPI: SONY    DVD RW DW-G120A, MYS2, max UDMA/66
[   20.793833] ata2.00: limited to UDMA/33 due to 40-wire cable
[   20.981773] ata2.00: configured for UDMA/33
[   20.981950] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-00JH 05.0 PQ: 0 ANSI: 5
[   20.982609] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 4D040H2   DAH0 PQ: 0 ANSI: 5
[   20.983737] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DW-G120A  MYS2 PQ: 0 ANSI: 5
[   20.984451] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 17
[   20.984473] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   20.984698] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   20.984725] ohci_hcd 0000:00:03.0: irq 17, io mem 0xe7004000
[   21.009319] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   21.009571] sd 0:0:0:0: [sda] Write Protect is off
[   21.009576] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.011104] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.011203] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   21.011218] sd 0:0:0:0: [sda] Write Protect is off
[   21.011220] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.011240] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.011247]  sda: sda1 sda2
[   21.024533] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.024885] sd 0:0:1:0: [sdb] 80043264 512-byte hardware sectors (40982 MB)
[   21.024903] sd 0:0:1:0: [sdb] Write Protect is off
[   21.024906] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   21.024924] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.025007] sd 0:0:1:0: [sdb] 80043264 512-byte hardware sectors (40982 MB)
[   21.025020] sd 0:0:1:0: [sdb] Write Protect is off
[   21.025023] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   21.025041] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.025045]  sdb: sdb1 sdb2 sdb3
[   21.039673] usb usb1: configuration #1 chosen from 1 choice
[   21.039708] hub 1-0:1.0: USB hub found
[   21.039723] hub 1-0:1.0: 3 ports detected
[   21.041275] sd 0:0:1:0: [sdb] Attached SCSI disk
[   21.047881] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.048183] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   21.048466] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   21.125468] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.125477] Uniform CD-ROM driver Revision: 3.20
[   21.125928] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.141732] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 18
[   21.141756] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   21.141792] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   21.141814] ohci_hcd 0000:00:03.1: irq 18, io mem 0xe7000000
[   21.199631] usb usb2: configuration #1 chosen from 1 choice
[   21.199669] hub 2-0:1.0: USB hub found
[   21.199684] hub 2-0:1.0: 3 ports detected
[   21.301765] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 19
[   21.301788] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   21.301823] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   21.301846] ohci_hcd 0000:00:03.2: irq 19, io mem 0xe7001000
[   21.359595] usb usb3: configuration #1 chosen from 1 choice
[   21.359632] hub 3-0:1.0: USB hub found
[   21.359647] hub 3-0:1.0: 2 ports detected
[   21.445445] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   21.461783] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 20
[   21.461803] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   21.461847] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   21.461895] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   21.461910] ehci_hcd 0000:00:03.3: irq 20, io mem 0xe7002000
[   21.589041] Attempting manual resume
[   21.589047] swsusp: Resume From Partition 8:17
[   21.589049] PM: Checking swsusp image.
[   21.604175] PM: Resume from disk failed.
[   21.621479] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.621616] usb usb4: configuration #1 chosen from 1 choice
[   21.621655] hub 4-0:1.0: USB hub found
[   21.621668] hub 4-0:1.0: 8 ports detected
[   21.635986] kjournald starting.  Commit interval 5 seconds
[   21.636006] EXT3-fs: mounted filesystem with ordered data mode.
[   21.725720] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 21
[   21.725739] PCI: Unable to reserve I/O region #1:100@1000 for device 0000:00:04.0
[   21.725747] sis900: probe of 0000:00:04.0 failed with error -16
[   22.029325] usb 1-1: device not accepting address 2, error -62
[   23.069132] usb 1-1: new low speed USB device using ohci_hcd and address 4
[   23.283693] usb 1-1: configuration #1 chosen from 1 choice
[   23.589021] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   23.801465] usb 2-1: configuration #1 chosen from 1 choice
[   23.804386] hub 2-1:1.0: USB hub found
[   23.807343] hub 2-1:1.0: 2 ports detected
[   24.130206] usb 2-1.1: new full speed USB device using ohci_hcd and address 3
[   24.244269] usb 2-1.1: configuration #1 chosen from 1 choice
[   24.462059] usb 2-1.2: new full speed USB device using ohci_hcd and address 4
[   24.576116] usb 2-1.2: configuration #1 chosen from 1 choice
[   33.689163] Linux agpgart interface v0.102 (c) Dave Jones
[   33.718254] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.728304] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.818795] agpgart: Detected SiS chipset - id:1633
[   33.823762] agpgart: AGP aperture is 64M @ 0xe0000000
[   34.676757] input: PC Speaker as /class/input/input2
[   34.743858] nvidia: module license 'NVIDIA' taints kernel.
[   35.002964] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.003346] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   35.181887] parport_pc 00:09: reported by Plug and Play ACPI
[   35.181965] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   35.407315] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 22
[   35.410316] Audigy2 value: Special config.
[   35.657734] usbcore: registered new interface driver hiddev
[   35.676036] input: Dell Dell USB Mouse as /class/input/input3
[   35.676137] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:03.0-1
[   35.676166] usbcore: registered new interface driver usbhid
[   35.676171] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   35.697700] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 22
[   35.702860] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x413C pid 0x5106
[   35.702886] usbcore: registered new interface driver usblp
[   35.702890] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   36.018569] intel8x0_measure_ac97_clock: measured 54776 usecs
[   36.018574] intel8x0: clocking to 48000
[   37.139992] lp0: using parport0 (interrupt-driven).
[   37.258559] Adding 449780k swap on /dev/sdb1.  Priority:-1 extents:1 across:449780k
[   38.091563] EXT3 FS on sdb2, internal journal
[   82.290022] kjournald starting.  Commit interval 5 seconds
[   82.290259] EXT3 FS on sda2, internal journal
[   82.290267] EXT3-fs: mounted filesystem with ordered data mode.
[   83.425896] No dock devices found.
[   83.506984] input: Power Button (FF) as /class/input/input4
[   83.513497] ACPI: Power Button (FF) [PWRF]
[   83.553860] input: Power Button (CM) as /class/input/input5
[   83.560344] ACPI: Power Button (CM) [PWRB]
[   86.379811] ppdev: user-space parallel port driver
[   87.882885] audit(1194101458.777:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4652 profile="/usr/sbin/cupsd"
[   88.874691] Failure registering capabilities with primary security module.
[   94.087675] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   94.087702] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   94.088695] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 1235.618873] ip_tables: (C) 2000-2006 Netfilter Core Team

Hope someone can help.

Namaste,
Platinumwolf

---

### Post by Lambert on 2007-11-03
check to see if the sis900 module is loaded

```

lsmod | grep sis900

```

If you get no output then run this command.

```

sudo modprobe sis900

```

you can see if you have an interface to configure or run the lshw command again to see if the unclaimed part goes away.

---

### Post by platinumwolf on 2007-11-26
I'm not sure what happened, but it seems to work again. I tried what you said, but got no resolution. So I walked away for a few hours and came back and it worked. Go figure.

---

