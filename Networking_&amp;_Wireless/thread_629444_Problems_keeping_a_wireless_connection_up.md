---
title: "Problems keeping a wireless connection up"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by dean20007 on 2007-12-02
Hi Folks

I am having problems keeping my wireless connection up and by the output of dmesg it looks as though my Belkin FSD7050 USB stick is becoming unrecognized (due to some modules conflicting?) 

when it drops I have to unplug the USB stick and restart the network. Equally confusing is the fct that I have tried blacklisting the rt2x00_usb module that seems to me to be casuing the problems but it atill appears to be getting loaded? 

Below is the output of dmesg and /etc/modprobe.d/blacklist

blacklist 

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist rt73

blacklist rt2500usb

```

dmesg:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
[    0.000000]  BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5570
[    0.000000] Entering add_active_range(0, 0, 393200) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   393200
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   393200
[    0.000000] On node 0 totalpages: 393200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1279 pages used for memmap
[    0.000000]   HighMem zone: 162545 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6EB0 checksum 0
[    0.000000] ACPI: RSDP 000F6EB0, 0014 (r0 AWARD )
[    0.000000] ACPI: RSDT 5FFF3000, 002C (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 5FFF3040, 0074 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 5FFF30C0, 3AA4 (r1 AWARD  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 5FFF0000, 0040
[    0.000000] ACPI: APIC 5FFF6B80, 005A (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[    0.000000] Built 1 zonelists.  Total pages: 390129
[    0.000000] Kernel command line: root=UUID=c8d2a386-fa3e-42c1-bd03-67633e7ccf6c ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1999.550 MHz processor.
[   11.980951] Console: colour VGA+ 80x25
[   11.981382] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.981807] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.026033] Memory: 1547280k/1572800k available (2015k kernel code, 24328k reserved, 916k data, 364k init, 655296k highmem)
[   12.026044] virtual kernel memory layout:
[   12.026045]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   12.026046]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.026047]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   12.026048]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   12.026049]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   12.026051]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   12.026052]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   12.026055] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.026092] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   12.106091] Calibrating delay using timer specific routine.. 4000.82 BogoMIPS (lpj=8001651)
[   12.106119] Security Framework v1.0.0 initialized
[   12.106128] SELinux:  Disabled at boot.
[   12.106140] Mount-cache hash table entries: 512
[   12.106266] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[   12.106274] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.106277] CPU: L2 Cache: 512K (64 bytes/line)
[   12.106279] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[   12.106289] Compat vDSO mapped to ffffe000.
[   12.106301] Checking 'hlt' instruction... OK.
[   12.122218] SMP alternatives: switching to UP code
[   12.122413] Freeing SMP alternatives: 11k freed
[   12.122674] Early unpacking initramfs... done
[   12.423482] ACPI: Core revision 20070126
[   12.423541] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.425201] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[   12.425217] Total of 1 processors activated (4000.82 BogoMIPS).
[   12.425307] ENABLING IO-APIC IRQs
[   12.425467] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.570033] Brought up 1 CPUs
[   12.570121] Booting paravirtualized kernel on bare hardware
[   12.570178] Time: 16:28:15  Date: 11/02/107
[   12.570198] NET: Registered protocol family 16
[   12.570267] EISA bus registered
[   12.570277] ACPI: bus type pci registered
[   12.605988] PCI: PCI BIOS revision 2.10 entry at 0xfb4f0, last bus=1
[   12.605990] PCI: Using configuration type 1
[   12.605992] Setting up standard PCI resources
[   12.609917] ACPI: EC: Look up EC in DSDT
[   12.612858] ACPI: Interpreter enabled
[   12.612863] ACPI: (supports S0 S1 S4 S5)
[   12.612878] ACPI: Using IOAPIC for interrupt routing
[   12.616393] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.616397] PCI: Probing PCI hardware (bus 00)
[   12.616852] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.633686] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
[   12.633766] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   12.633844] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   12.633938] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   12.634021] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   12.634101] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   12.634181] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   12.634259] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   12.634328] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.634336] pnp: PnP ACPI init
[   12.634343] ACPI: bus type pnp registered
[   12.636196] pnp: PnP ACPI: found 11 devices
[   12.636198] ACPI: ACPI bus type pnp unregistered
[   12.636201] PnPBIOS: Disabled by ACPI PNP
[   12.636242] PCI: Using ACPI for IRQ routing
[   12.636244] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.641159] NET: Registered protocol family 8
[   12.641161] NET: Registered protocol family 20
[   12.641210] pnp: 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   12.641213] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   12.641216] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   12.641219] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   12.641986] Time: tsc clocksource has been installed.
[   12.671432] PCI: Bridge: 0000:00:01.0
[   12.671434]   IO window: d000-dfff
[   12.671438]   MEM window: e8000000-e80fffff
[   12.671441]   PREFETCH window: c0000000-dfffffff
[   12.671459] NET: Registered protocol family 2
[   12.702014] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.702151] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   12.703632] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   12.704157] TCP: Hash tables configured (established 131072 bind 65536)
[   12.704160] TCP reno registered
[   12.714091] checking if image is initramfs... it is
[   13.173879] Switched to high resolution mode on CPU 0
[   13.305023] Freeing initrd memory: 7355k freed
[   13.305347] audit: initializing netlink socket (disabled)
[   13.305360] audit(1196612895.012:1): initialized
[   13.305416] highmem bounce pool size: 64 pages
[   13.306780] VFS: Disk quotas dquot_6.5.1
[   13.306822] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.306901] io scheduler noop registered
[   13.306903] io scheduler anticipatory registered
[   13.306904] io scheduler deadline registered
[   13.306916] io scheduler cfq registered (default)
[   13.365794] Boot video device is 0000:01:00.0
[   13.365899] isapnp: Scanning for PnP cards...
[   13.719156] isapnp: No Plug & Play device found
[   13.736967] Real Time Clock Driver v1.12ac
[   13.737041] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.737123] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.737582] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.737733] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.737922] 0000:00:0c.0: ttyS1 at I/O 0xe908 (irq = 16) is a 16450
[   13.738040] 0000:00:0c.0: ttyS2 at I/O 0xe910 (irq = 16) is a 8250
[   13.738160] 0000:00:0c.0: ttyS3 at I/O 0xe918 (irq = 16) is a 16450
[   13.738212] Couldn't register serial port 0000:00:0c.0: -28
[   13.738612] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.738782] input: Macintosh mouse button emulation as /class/input/input0
[   13.738835] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   13.738837] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   13.739100] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.739104] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.739221] mice: PS/2 mouse device common for all mice
[   13.739298] EISA: Probing bus 0 at eisa.0
[   13.739306] Cannot allocate resource for EISA slot 1
[   13.739315] Cannot allocate resource for EISA slot 4
[   13.739329] EISA: Detected 0 cards.
[   13.739471] TCP cubic registered
[   13.739486] NET: Registered protocol family 1
[   13.739505] Using IPI No-Shortcut mode
[   13.739646]   Magic number: 3:808:488
[   13.740072] Freeing unused kernel memory: 364k freed
[   13.818657] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.948205] AppArmor: AppArmor initialized<5>audit(1196612896.512:2):  type=1505 info="AppArmor initialized" pid=1195
[   14.954340] fuse init (API version 7.8)
[   14.958799] Failure registering capabilities with primary security module.
[   14.969297] ACPI: Fan [FAN] (on)
[   14.974828] ACPI: Thermal Zone [THRM] (40 C)
[   15.491873] SCSI subsystem initialized
[   15.495765] libata version 2.21 loaded.
[   15.498019] pata_sis 0000:00:02.5: version 0.5.1
[   15.498129] scsi0 : pata_sis
[   15.498167] scsi1 : pata_sis
[   15.498252] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014000 irq 14
[   15.498255] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014008 irq 15
[   15.534767] usbcore: registered new interface driver usbfs
[   15.534788] usbcore: registered new interface driver hub
[   15.534806] usbcore: registered new device driver usb
[   15.539227] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   15.598273] sis900.c: v1.08.10 Apr. 2 2006
[   15.713094] Floppy drive(s): fd0 is 1.44M
[   15.757812] FDC 0 is a post-1991 82077
[   15.973264] ata2.00: ATAPI: DVDRW IDE 16X, VER A07F, max UDMA/66
[   15.973271] ata2.00: limited to UDMA/33 due to 40-wire cable
[   16.145210] ata2.00: configured for UDMA/33
[   16.145544] scsi 1:0:0:0: CD-ROM            DVDRW    IDE 16X          A07F PQ: 0 ANSI: 5
[   16.145686] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 17
[   16.145697] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   16.145813] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   16.145828] ohci_hcd 0000:00:03.0: irq 17, io mem 0xe8124000
[   16.161461] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[   16.161467] Uniform CD-ROM driver Revision: 3.20
[   16.161636] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   16.165683] sr 1:0:0:0: Attached scsi generic sg0 type 5
[   16.203103] usb usb1: configuration #1 chosen from 1 choice
[   16.203129] hub 1-0:1.0: USB hub found
[   16.203139] hub 1-0:1.0: 3 ports detected
[   16.305048] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 18
[   16.305061] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   16.305083] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   16.305097] ohci_hcd 0000:00:03.1: irq 18, io mem 0xe8120000
[   16.362996] usb usb2: configuration #1 chosen from 1 choice
[   16.363021] hub 2-0:1.0: USB hub found
[   16.363028] hub 2-0:1.0: 3 ports detected
[   16.464976] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 19
[   16.464986] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   16.465007] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   16.465020] ohci_hcd 0000:00:03.2: irq 19, io mem 0xe8121000
[   16.522942] usb usb3: configuration #1 chosen from 1 choice
[   16.522961] hub 3-0:1.0: USB hub found
[   16.522969] hub 3-0:1.0: 2 ports detected
[   16.608870] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   16.625287] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 20
[   16.625298] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   16.625318] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   16.625345] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   16.625354] ehci_hcd 0000:00:03.3: irq 20, io mem 0xe8122000
[   16.784832] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.784926] usb usb4: configuration #1 chosen from 1 choice
[   16.784949] hub 4-0:1.0: USB hub found
[   16.784957] hub 4-0:1.0: 8 ports detected
[   16.888952] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 21
[   16.890002] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   16.898766] 0000:00:04.0: Using transceiver found at address 1 as default
[   16.899370] eth0: SiS 900 PCI Fast Ethernet at 0xe200, IRQ 21, 00:11:5b:33:b0:3b.
[   16.899438] sata_sis 0000:00:05.0: version 0.8
[   16.899449] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 22
[   16.899454] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[   16.899516] scsi2 : sata_sis
[   16.899547] scsi3 : sata_sis
[   16.899573] ata3: SATA max UDMA/133 cmd 0x0001e300 ctl 0x0001e402 bmdma 0x0001e700 irq 22
[   16.899577] ata4: SATA max UDMA/133 cmd 0x0001e500 ctl 0x0001e602 bmdma 0x0001e708 irq 22
[   17.192704] usb 1-1: device not accepting address 2, error -62
[   17.364669] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   17.373777] ata3.00: ATA-7: Maxtor 6B200M0, BANC1B70, max UDMA/133
[   17.373780] ata3.00: 398297088 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   17.389761] ata3.00: configured for UDMA/133
[   17.700565] ata4: SATA link down (SStatus 0 SControl 300)
[   17.711134] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6B200M0   BANC PQ: 0 ANSI: 5
[   17.711518] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   17.718525] sd 2:0:0:0: [sda] 398297088 512-byte hardware sectors (203928 MB)
[   17.718537] sd 2:0:0:0: [sda] Write Protect is off
[   17.718540] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.718552] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.718593] sd 2:0:0:0: [sda] 398297088 512-byte hardware sectors (203928 MB)
[   17.718600] sd 2:0:0:0: [sda] Write Protect is off
[   17.718602] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.718613] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.718617]  sda: sda1 sda2 sda3 sda4
[   17.736414] sd 2:0:0:0: [sda] Attached SCSI disk
[   18.016375] Attempting manual resume
[   18.016378] swsusp: Resume From Partition 8:1
[   18.016380] PM: Checking swsusp image.
[   18.027750] PM: Resume from disk failed.
[   18.041551] EXT3-fs: INFO: recovery required on readonly filesystem.
[   18.041555] EXT3-fs: write access will be enabled during recovery.
[   18.240411] usb 4-3: new high speed USB device using ehci_hcd and address 3
[   18.544160] usb 4-3: configuration #1 chosen from 1 choice
[   18.968237] usb 4-7: new high speed USB device using ehci_hcd and address 5
[   19.101203] usb 4-7: configuration #1 chosen from 1 choice
[   19.404083] usb 1-1: new full speed USB device using ohci_hcd and address 4
[   19.618478] usb 1-1: configuration #1 chosen from 1 choice
[   19.927946] usb 1-2: new low speed USB device using ohci_hcd and address 5
[   20.146229] usb 1-2: configuration #1 chosen from 1 choice
[   20.150029] usbcore: registered new interface driver hiddev
[   20.158189] input: Logitech Logitech USB Speaker as /class/input/input2
[   20.158202] input: USB HID v1.00 Device [Logitech Logitech USB Speaker] on usb-0000:00:03.0-1
[   20.169401] input: Microsoft Microsoft Wireless Optical Desktop® 1.00 as /class/input/input3
[   20.169419] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 1.00] on usb-0000:00:03.0-2
[   20.169433] usbcore: registered new interface driver usbhid
[   20.169436] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   21.859192] kjournald starting.  Commit interval 5 seconds
[   21.859208] EXT3-fs: sda3: orphan cleanup on readonly fs
[   21.859214] ext3_orphan_cleanup: deleting unreferenced inode 4554763
[   21.859278] ext3_orphan_cleanup: deleting unreferenced inode 2244926
[   22.134556] ext3_orphan_cleanup: deleting unreferenced inode 1393380
[   22.134573] EXT3-fs: sda3: 3 orphan inodes deleted
[   22.134575] EXT3-fs: recovery complete.
[   22.136879] EXT3-fs: mounted filesystem with ordered data mode.
[   29.116540] Linux agpgart interface v0.102 (c) Dave Jones
[   29.151273] agpgart: Detected AGP bridge 0
[   29.154997] agpgart: AGP aperture is 128M @ 0xe0000000
[   29.171215] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.177906] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.427068] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x03F0 pid 0x8904
[   30.427085] usbcore: registered new interface driver usblp
[   30.427089] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   30.485435] parport_pc 00:09: reported by Plug and Play ACPI
[   30.485484] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   30.530112] input: PC Speaker as /class/input/input4
[   30.555198] usbcore: registered new interface driver xpad
[   30.555202] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   30.599781] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
[   30.928839] intel8x0_measure_ac97_clock: measured 62919 usecs
[   30.928843] intel8x0: clocking to 48000
[   30.965149] ieee80211_init: failed to initialize WME (err=-17)
[   30.981532] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   30.981565] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   30.981592] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   30.981636] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   30.989603] wmaster0: Selected rate control algorithm 'simple'
[   31.070215] usbcore: registered new interface driver rt73usb
[   31.267131] usbcore: registered new interface driver snd-usb-audio
[   31.611778] lp0: using parport0 (interrupt-driven).
[   31.642052] ndiswrapper version 1.45 loaded (smp=yes)
[   31.687262] usbcore: registered new interface driver ndiswrapper
[   31.734145] Adding 979924k swap on /dev/sda1.  Priority:-1 extents:1 across:979924k
[   31.987761] wlan0: Initial auth_alg=0
[   31.987767] wlan0: authenticate with AP 00:01:38:47:29:db
[   31.995178] EXT3 FS on sda3, internal journal
[   32.040395] wlan0: RX authentication from 00:01:38:47:29:db (alg=0 transaction=2 status=0)
[   32.040400] wlan0: authenticated
[   32.040403] wlan0: associate with AP 00:01:38:47:29:db
[   32.091989] wlan0: RX AssocResp from 00:01:38:47:29:db (capab=0x431 status=0 aid=5)
[   32.091993] wlan0: associated
[   32.390022] NET: Registered protocol family 17
[   34.566289] No dock devices found.
[   34.648045] input: Power Button (FF) as /class/input/input5
[   34.652103] ACPI: Power Button (FF) [PWRF]
[   34.683184] input: Power Button (CM) as /class/input/input6
[   34.687185] ACPI: Power Button (CM) [PWRB]
[   34.717911] input: Sleep Button (CM) as /class/input/input7
[   34.721974] ACPI: Sleep Button (CM) [FUTS]
[   34.934083] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   34.934118] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
[   34.934120] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
[   34.934122] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x6
[   35.781716] ppdev: user-space parallel port driver
[   35.959966] NET: Registered protocol family 10
[   35.960322] lo: Disabled Privacy Extensions
[   36.066884] audit(1196612918.126:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4832 profile="/usr/sbin/cupsd"
[   36.115334] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   36.115339] apm: overridden by ACPI.
[   36.487437] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   36.657243] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   36.677086] NFSD: starting 90-second grace period
[   25.696000] Marking TSC unstable due to: cpufreq changes.
[   25.700000] Time: acpi_pm clocksource has been installed.
[   25.912000] Failure registering capabilities with primary security module.
[   27.964000] [fglrx] Maximum main memory to use for locked dma buffers: 1414 MBytes.
[   27.964000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   28.208000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.776000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   30.776000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   30.776000] [fglrx] AGP detected, AgpState   = 0x1f004e0b (hardware caps of chipset)
[   30.780000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   30.780000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   30.780000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   30.780000] [fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
[   30.788000] [fglrx] total      GART = 134217728
[   30.788000] [fglrx] free       GART = 118222848
[   30.788000] [fglrx] max single GART = 118222848
[   30.788000] [fglrx] total      LFB  = 134217728
[   30.788000] [fglrx] free       LFB  = 116387840
[   30.788000] [fglrx] max single LFB  = 116387840
[   30.788000] [fglrx] total      Inv  = 134217728
[   30.788000] [fglrx] free       Inv  = 134217728
[   30.788000] [fglrx] max single Inv  = 134217728
[   30.788000] [fglrx] total      TIM  = 0
[   33.908000] wlan0: no IPv6 routers present
[   37.616000] atkbd.c: Unknown key released (translated set 2, code 0x82 on isa0060/serio0).
[   37.616000] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[   38.192000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   38.192000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   93.844000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   93.860000] wlan0: Initial auth_alg=0
[   93.860000] wlan0: authenticate with AP 00:01:38:47:29:db
[   93.912000] wlan0: RX authentication from 00:01:38:47:29:db (alg=0 transaction=2 status=0)
[   93.912000] wlan0: authenticated
[   93.912000] wlan0: associate with AP 00:01:38:47:29:db
[   93.964000] wlan0: RX AssocResp from 00:01:38:47:29:db (capab=0x431 status=0 aid=5)
[   93.964000] wlan0: associated
[   93.964000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   94.132000] wlan0: duplicate address detected!
[  223.688000] atkbd.c: Unknown key released (translated set 2, code 0x82 on isa0060/serio0).
[  223.688000] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  223.692000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  223.692000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  335.224000] atkbd.c: Unknown key released (translated set 2, code 0x82 on isa0060/serio0).
[  335.224000] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  410.904000] atkbd.c: Unknown key released (translated set 2, code 0x82 on isa0060/serio0).
[  410.904000] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  411.184000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  411.184000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  424.352000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  424.352000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  431.388000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  431.388000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  439.532000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  439.532000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  442.816000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  442.816000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  457.632000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  457.632000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  471.636000] atkbd.c: Unknown key released (translated set 2, code 0x82 on isa0060/serio0).
[  471.636000] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  639.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  640.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  640.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  641.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  641.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  641.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  641.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  641.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  641.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  642.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  642.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  643.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  644.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  644.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  644.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  644.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  644.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  644.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  644.660000] wlan0: No ProbeResp from current AP 00:01:38:47:29:db - assume out of range
[  645.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  645.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  645.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  646.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  646.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  646.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  647.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  647.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  647.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  647.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  647.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  647.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  648.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  649.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  649.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  649.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  649.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  649.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  650.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  650.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  650.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  650.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  650.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  651.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  652.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  652.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  652.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  652.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  652.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  652.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  653.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  653.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  653.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  654.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  654.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  654.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  655.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  655.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  655.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  655.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  655.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  655.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  656.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  657.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  657.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  657.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  657.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  657.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  658.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  658.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  658.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  658.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  658.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  659.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  660.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  660.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  660.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  660.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  660.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  660.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  661.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  661.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  661.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  662.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  662.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  662.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  663.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  663.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  663.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  663.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  663.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  663.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  664.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  665.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  665.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  665.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  665.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  665.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  665.916000] atkbd.c: Unknown key released (translated set 2, code 0x82 on isa0060/serio0).
[  665.916000] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  666.048000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  666.048000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  666.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  666.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  666.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  666.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  666.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  667.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  668.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  668.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  668.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  668.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  668.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  668.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  669.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  669.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  669.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  670.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  670.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  670.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  671.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  671.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  671.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  671.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  671.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  671.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  672.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  673.012000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  673.012000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  673.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  673.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  673.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  673.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  673.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  674.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  674.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  674.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  674.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  674.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  675.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  676.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  676.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  676.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  676.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  676.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  676.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  676.660000] wlan0: No STA entry for own AP 00:01:38:47:29:db
[  677.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  677.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  677.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  678.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  678.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  678.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  678.844000] usb 4-3: USB disconnect, address 3
[  678.848000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[  678.848000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[  678.848000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[  678.848000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[  678.848000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[  678.848000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[  692.096000] usb 4-3: new high speed USB device using ehci_hcd and address 6
[  692.396000] usb 4-3: configuration #1 chosen from 1 choice
[  692.660000] wmaster0: Selected rate control algorithm 'simple'
[  697.736000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  697.736000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  707.500000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  707.500000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  721.880000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  721.880000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  725.476000] atkbd.c: Unknown key released (translated set 2, code 0x82 on isa0060/serio0).
[  725.476000] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  893.232000] usb 4-3: USB disconnect, address 6
[  896.004000] usb 4-3: new high speed USB device using ehci_hcd and address 7
[  896.304000] usb 4-3: configuration #1 chosen from 1 choice
[  896.568000] wmaster0: Selected rate control algorithm 'simple'
[  946.412000] atkbd.c: Unknown key released (translated set 2, code 0x82 on isa0060/serio0).
[  946.412000] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  947.764000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  947.872000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  948.652000] wlan0: Initial auth_alg=0
[  948.652000] wlan0: authenticate with AP 00:01:38:47:29:db
[  948.708000] wlan0: RX authentication from 00:01:38:47:29:db (alg=0 transaction=2 status=0)
[  948.708000] wlan0: authenticated
[  948.708000] wlan0: associate with AP 00:01:38:47:29:db
[  948.740000] wlan0: RX AssocResp from 00:01:38:47:29:db (capab=0x431 status=0 aid=5)
[  948.740000] wlan0: associated
[  948.744000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  949.736000] wlan0: duplicate address detected!
[  971.752000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  971.852000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  971.952000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  973.052000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  973.152000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[  973.252000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  973.352000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[  973.452000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  973.552000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  973.652000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  973.752000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  973.852000] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[  973.852000] phy2 -> rt73usb_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 1281.520000] atkbd.c: Unknown key released (translated set 2, code 0x82 on isa0060/serio0).
[ 1281.520000] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
```

---

### Post by dean20007 on 2007-12-02
bump

---

### Post by registering on 2007-12-03
I don't know, but I my network (wired OR wireless) will drop out randomly. When it happens to my wireless, my WPA passphrase is forgotten and I'm prompted for it. Rebooting, it's found again miraculously. Even turning off wirelessly hardware-wise, my wired network will usually stop working after 20-30 minutes. Good luck.

---

### Post by dean20007 on 2007-12-04
anyone?

---

