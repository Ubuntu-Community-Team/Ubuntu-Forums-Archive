---
title: "sagem f@st 800 problem"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by plasma3d on 2006-12-15
```
plasma3d@plasma3d-desktop:~$ dmesg

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f4c60
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f65d0
[17179569.184000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff3040
[17179569.184000] ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff6cc0
[17179569.184000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 2086.888 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.772000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.772000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.788000] Memory: 509800k/524224k available (1910k kernel code, 13844k reserved, 1070k data, 308k init, 0k highmem)
[17179569.788000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.868000] Calibrating delay using timer specific routine.. 4177.65 BogoMIPS (lpj=8355300)
[17179569.868000] Security Framework v1.0.0 initialized
[17179569.868000] SELinux:  Disabled at boot.
[17179569.868000] Mount-cache hash table entries: 512
[17179569.868000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.868000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.868000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.868000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.868000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179569.868000] Checking 'hlt' instruction... OK.
[17179569.884000] SMP alternatives: switching to UP code
[17179569.884000] Freeing SMP alternatives: 16k freed
[17179569.884000] checking if image is initramfs... it is
[17179570.344000] Freeing initrd memory: 5564k freed
[17179570.344000] ACPI: Core revision 20060707
[17179570.348000] ACPI: Looking for DSDT ... not found!
[17179570.352000] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
[17179570.352000] Total of 1 processors activated (4177.65 BogoMIPS).
[17179570.352000] ENABLING IO-APIC IRQs
[17179570.352000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.496000] Brought up 1 CPUs
[17179570.496000] migration_cost=0
[17179570.496000] NET: Registered protocol family 16
[17179570.496000] EISA bus registered
[17179570.496000] ACPI: bus type pci registered
[17179570.500000] PCI: PCI BIOS revision 2.10 entry at 0xf9f10, last bus=1
[17179570.500000] PCI: Using configuration type 1
[17179570.500000] Setting up standard PCI resources
[17179570.508000] ACPI: Interpreter enabled
[17179570.508000] ACPI: Using IOAPIC for interrupt routing
[17179570.508000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.508000] PCI: Probing PCI hardware (bus 00)
[17179570.508000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.512000] PCI quirk: region 4000-407f claimed by vt8235 PM
[17179570.512000] PCI quirk: region 5000-500f claimed by vt8235 SMB
[17179570.512000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179570.512000] Boot video device is 0000:01:00.0
[17179570.512000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.532000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[17179570.532000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[17179570.532000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[17179570.536000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179570.536000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179570.536000] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[17179570.536000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[17179570.536000] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[17179570.536000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.536000] pnp: PnP ACPI init
[17179570.540000] pnp: PnP ACPI: found 12 devices
[17179570.540000] PnPBIOS: Disabled by ACPI PNP
[17179570.540000] PCI: Using ACPI for IRQ routing
[17179570.540000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.568000] PCI: Bridge: 0000:00:01.0
[17179570.568000]   IO window: disabled.
[17179570.568000]   MEM window: e8000000-eaffffff
[17179570.568000]   PREFETCH window: d0000000-dfffffff
[17179570.568000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.568000] NET: Registered protocol family 2
[17179570.600000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.600000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.600000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.600000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.600000] TCP reno registered
[17179570.600000] audit: initializing netlink socket (disabled)
[17179570.600000] audit(1166242734.600:1): initialized
[17179570.600000] VFS: Disk quotas dquot_6.5.1
[17179570.600000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.600000] Initializing Cryptographic API
[17179570.600000] io scheduler noop registered
[17179570.600000] io scheduler anticipatory registered
[17179570.600000] io scheduler deadline registered
[17179570.600000] io scheduler cfq registered (default)
[17179570.600000] isapnp: Scanning for PnP cards...
[17179570.952000] isapnp: No Plug & Play device found
[17179570.976000] Real Time Clock Driver v1.12ac
[17179570.976000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.976000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.976000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.976000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.976000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.976000] mice: PS/2 mouse device common for all mice
[17179570.976000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.976000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.976000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.976000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179570.976000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179570.984000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.984000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.984000] EISA: Probing bus 0 at eisa.0
[17179570.984000] Cannot allocate resource for EISA slot 4
[17179570.984000] Cannot allocate resource for EISA slot 5
[17179570.984000] EISA: Detected 0 cards.
[17179570.984000] TCP bic registered
[17179570.984000] NET: Registered protocol family 1
[17179570.984000] NET: Registered protocol family 8
[17179570.984000] NET: Registered protocol family 20
[17179570.984000] Using IPI No-Shortcut mode
[17179570.984000] ACPI: (supports S0 S1 S4 S5)
[17179570.988000] Freeing unused kernel memory: 308k freed
[17179571.072000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.140000] Capability LSM initialized
[17179572.172000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.172000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179572.468000] SCSI subsystem initialized
[17179572.472000] libata version 1.20 loaded.
[17179572.472000] sata_sil 0000:00:08.0: version 0.9
[17179572.472000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179572.472000] ata1: SATA max UDMA/100 cmd 0xE0830080 ctl 0xE083008A bmdma 0xE0830000 irq 169
[17179572.472000] ata2: SATA max UDMA/100 cmd 0xE08300C0 ctl 0xE08300CA bmdma 0xE0830008 irq 169
[17179572.680000] ata1: SATA link down (SStatus 0)
[17179572.688000] scsi0 : sata_sil
[17179572.896000] ata2: SATA link down (SStatus 0)
[17179572.904000] scsi1 : sata_sil
[17179572.928000] PDC20276: IDE controller at PCI slot 0000:00:0f.0
[17179572.928000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179572.928000] PDC20276: chipset revision 1
[17179572.928000] PDC20276: 100% native mode on irq 177
[17179572.928000]     ide2: BM-DMA at 0xb400-0xb407, BIOS settings: hde:pio, hdf:pio
[17179572.928000]     ide3: BM-DMA at 0xb408-0xb40f, BIOS settings: hdg:pio, hdh:pio
[17179572.928000] Probing IDE interface ide2...
[17179573.532000] Probing IDE interface ide3...
[17179574.608000] hdh: SONY CD-RW CRX230E, ATAPI CD/DVD-ROM drive
[17179574.668000] ide3 at 0xac00-0xac07,0xb002 on irq 177
[17179574.676000] hdh: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[17179574.676000] Uniform CD-ROM driver Revision: 3.20
[17179574.712000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179574.712000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[17179574.712000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179574.712000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 185
[17179574.712000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 9
[17179574.712000] VP_IDE: chipset revision 6
[17179574.712000] VP_IDE: not 100% native mode: will probe irqs later
[17179574.712000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179574.712000]     ide0: BM-DMA at 0xc400-0xc407, BIOS settings: hda:DMA, hdb:DMA
[17179574.712000]     ide1: BM-DMA at 0xc408-0xc40f, BIOS settings: hdc:DMA, hdd:DMA
[17179574.712000] Probing IDE interface ide0...
[17179575.144000] hda: ST3320620A, ATA DISK drive
[17179575.424000] hdb: WDC WD800BB-00FRA0, ATA DISK drive
[17179575.480000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.492000] Probing IDE interface ide1...
[17179576.412000] hdc: _NEC DVD_RW ND-3500AG, ATAPI CD/DVD-ROM drive
[17179577.248000] hdd: TOSHIBA ODD-DVD SD-M1802, ATAPI CD/DVD-ROM drive
[17179577.308000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.320000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.324000] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179577.332000] hda: max request size: 512KiB
[17179577.380000] hda: 625142448 sectors (320072 MB) w/16384KiB Cache, CHS=38913/255/63, UDMA(100)
[17179577.404000] hda: cache flushes supported
[17179577.404000]  hda: hda1 hda2 hda3 hda4
[17179577.428000] hdb: max request size: 512KiB
[17179577.428000] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.428000] hdb: cache flushes supported
[17179577.428000]  hdb: hdb1 hdb2 < hdb5 >
[17179578.012000] Probing IDE interface ide2...
[17179578.048000] usbcore: registered new driver usbfs
[17179578.048000] usbcore: registered new driver hub
[17179578.048000] USB Universal Host Controller Interface driver v3.0
[17179578.048000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[17179578.048000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179578.048000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 193
[17179578.048000] PCI: Via IRQ fixup for 0000:00:10.0, from 5 to 1
[17179578.048000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179578.052000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179578.052000] uhci_hcd 0000:00:10.0: irq 193, io base 0x0000b800
[17179578.052000] usb usb1: configuration #1 chosen from 1 choice
[17179578.052000] hub 1-0:1.0: USB hub found
[17179578.052000] hub 1-0:1.0: 2 ports detected
[17179578.160000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 193
[17179578.160000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 1
[17179578.160000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179578.160000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179578.160000] uhci_hcd 0000:00:10.1: irq 193, io base 0x0000bc00
[17179578.160000] usb usb2: configuration #1 chosen from 1 choice
[17179578.160000] hub 2-0:1.0: USB hub found
[17179578.160000] hub 2-0:1.0: 2 ports detected
[17179578.268000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 193
[17179578.268000] PCI: Via IRQ fixup for 0000:00:10.2, from 12 to 1
[17179578.268000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179578.268000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179578.268000] uhci_hcd 0000:00:10.2: irq 193, io base 0x0000c000
[17179578.268000] usb usb3: configuration #1 chosen from 1 choice
[17179578.268000] hub 3-0:1.0: USB hub found
[17179578.268000] hub 3-0:1.0: 2 ports detected
[17179578.372000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 193
[17179578.372000] PCI: Via IRQ fixup for 0000:00:10.3, from 11 to 1
[17179578.372000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179578.372000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179578.372000] ehci_hcd 0000:00:10.3: irq 193, io mem 0xec005000
[17179578.372000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.372000] usb usb4: configuration #1 chosen from 1 choice
[17179578.372000] hub 4-0:1.0: USB hub found
[17179578.372000] hub 4-0:1.0: 6 ports detected
[17179578.684000] Attempting manual resume
[17179578.760000] kjournald starting.  Commit interval 5 seconds
[17179578.760000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.908000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[17179580.092000] usb 1-2: configuration #1 chosen from 1 choice
[17179580.352000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179580.536000] usb 2-1: configuration #1 chosen from 1 choice
[17179580.796000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17179580.968000] usb 3-1: configuration #1 chosen from 1 choice
[17179588.156000] Floppy drive(s): fd0 is 1.44M
[17179588.176000] 8139too Fast Ethernet driver 0.9.27
[17179588.176000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 201
[17179588.176000] eth0: RealTek RTL8139 at 0xe08a8000, 00:20:ed:73:02:cb, IRQ 201
[17179588.176000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179588.192000] FDC 0 is a post-1991 82077
[17179588.208000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179588.540000] input: PC Speaker as /class/input/input1
[17179588.916000] usbcore: registered new driver libusual
[17179588.980000] Initializing USB Mass Storage driver...
[17179588.980000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179588.980000] usb-storage: device found at 2
[17179588.980000] usb-storage: waiting for device to settle before scanning
[17179588.980000] scsi3 : SCSI emulation for USB Mass Storage devices
[17179588.980000] usbcore: registered new driver usb-storage
[17179588.980000] USB Mass Storage support registered.
[17179588.980000] usb-storage: device found at 2
[17179588.980000] usb-storage: waiting for device to settle before scanning
[17179589.052000] irda_init()
[17179589.052000] NET: Registered protocol family 23
[17179589.132000] eth0: link down
[17179589.156000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.168000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[17179589.176000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179589.188000] parport: PnPBIOS parport detected.
[17179589.188000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179589.264000] [eagle-usb] driver V2.3.2 loaded
[17179589.264000] [eagle-usb] New USB ADSL device detected, waiting for DSP code...
[17179589.264000] [eagle-usb] Interface 0 accepted.
[17179589.268000] [eagle-usb] created proc entry at : /proc/driver/eagle-usb/003-002
[17179589.268000] usbcore: registered new driver eagle-usb
[17179589.296000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.320000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.400000] [ueagle-atm] driver ueagle 1.3 loaded
[17179589.400000] usbcore: registered new driver ueagle-atm
[17179589.444000] usbcore: registered new driver hiddev
[17179589.468000] input: Microsoft Basic Optical Mouse as /class/input/input2
[17179589.468000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:10.0-2
[17179589.468000] usbcore: registered new driver usbhid
[17179589.468000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.520000] ts: Compaq touchscreen protocol output
[17179589.796000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179589.796000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179589.796000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 209
[17179589.796000] PCI: Via IRQ fixup for 0000:00:11.5, from 12 to 1
[17179589.796000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179590.180000] NET: Registered protocol family 17
[17179590.532000] lp0: using parport0 (interrupt-driven).
[17179590.564000] Adding 1510068k swap on /dev/disk/by-uuid/c7c1b8df-e18e-4e05-a47a-c3d38a856b88.  Priority:-1 extents:1 across:1510068k
[17179590.616000] EXT3 FS on hdb1, internal journal
[17179593.984000] usb-storage: device scan complete
[17179593.984000] usb-storage: device scan complete
[17179593.988000]   Vendor: SEMC      Model: Int.Memory        Rev: 0000
[17179593.988000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179593.988000]   Vendor: SEMC      Model: Mem-Stick         Rev: 0000
[17179593.988000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.024000] SCSI device sda: 53996 512-byte hdwr sectors (28 MB)
[17179594.032000] sda: Write Protect is off
[17179594.032000] sda: Mode Sense: 00 6a 00 00
[17179594.032000] sda: assuming drive cache: write through
[17179594.040000] SCSI device sda: 53996 512-byte hdwr sectors (28 MB)
[17179594.044000] sda: Write Protect is off
[17179594.044000] sda: Mode Sense: 00 6a 00 00
[17179594.044000] sda: assuming drive cache: write through
[17179594.044000]  sda: sda1
[17179594.060000] sd 2:0:0:0: Attached scsi removable disk sda
[17179594.072000] SCSI device sdb: 958999 512-byte hdwr sectors (491 MB)
[17179594.076000] sdb: Write Protect is off
[17179594.076000] sdb: Mode Sense: 00 6a 00 00
[17179594.076000] sdb: assuming drive cache: write through
[17179594.084000] SCSI device sdb: 958999 512-byte hdwr sectors (491 MB)
[17179594.088000] sdb: Write Protect is off
[17179594.088000] sdb: Mode Sense: 00 6a 00 00
[17179594.088000] sdb: assuming drive cache: write through
[17179594.088000]  sdb: sdb1
[17179594.116000] sd 3:0:0:0: Attached scsi removable disk sdb
[17179594.132000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17179594.132000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[17179594.148000] Buffer I/O error on device sdb1, logical block 958848
[17179594.148000] Buffer I/O error on device sdb1, logical block 958849
[17179594.148000] Buffer I/O error on device sdb1, logical block 958850
[17179594.148000] Buffer I/O error on device sdb1, logical block 958851
[17179594.148000] Buffer I/O error on device sdb1, logical block 958852
[17179594.148000] Buffer I/O error on device sdb1, logical block 958853
[17179594.148000] Buffer I/O error on device sdb1, logical block 958854
[17179594.148000] Buffer I/O error on device sdb1, logical block 958855
[17179594.148000] Buffer I/O error on device sdb1, logical block 958848
[17179594.148000] Buffer I/O error on device sdb1, logical block 958849
[17179596.316000] ACPI: Power Button (FF) [PWRF]
[17179596.316000] ACPI: Power Button (CM) [PWRB]
[17179596.436000] ibm_acpi: ec object not found
[17179596.468000] pcc_acpi: loading...
[17179599.496000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179599.496000] apm: overridden by ACPI.
[17179602.656000] printk: 94 messages suppressed.
[17179602.656000] Buffer I/O error on device sdb1, logical block 958848
[17179605.024000] Bluetooth: Core ver 2.8
[17179605.024000] NET: Registered protocol family 31
[17179605.024000] Bluetooth: HCI device and connection manager initialized
[17179605.024000] Bluetooth: HCI socket layer initialized
[17179605.052000] Bluetooth: L2CAP ver 2.8
[17179605.052000] Bluetooth: L2CAP socket layer initialized
[17179605.088000] Bluetooth: RFCOMM socket layer initialized
[17179605.088000] Bluetooth: RFCOMM TTY layer initialized
[17179605.088000] Bluetooth: RFCOMM ver 1.7
[17179616.676000] NET: Registered protocol family 10
[17179616.676000] lo: Disabled Privacy Extensions
[17179616.676000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179616.676000] IPv6 over IPv4 tunneling driver
[17179620.800000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179621.312000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179674.708000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179674.780000] ISO 9660 Extensions: RRIP_1991A
[17179980.124000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179980.300000] ISO 9660 Extensions: RRIP_1991A
[17180002.300000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180002.388000] ISO 9660 Extensions: RRIP_1991A
[17181343.092000] CSLIP: code copyright 1989 Regents of the University of California
[17181343.120000] PPP generic driver version 2.4.2
[17181619.260000] usb 3-1: USB disconnect, address 2
[17181619.260000] [eagle-usb] ADSL device removed
[17181620.536000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[17181620.696000] usb 3-1: configuration #1 chosen from 1 choice
[17181620.700000] [eagle-usb] New pre-firmware modem detected
[17181620.700000] [eagle-usb] Uploading firmware..
[17181621.332000] [eagle-usb] Binding eu_instance_t to USB 003/003
[17181621.544000] usb 3-1: USB disconnect, address 3
[17181621.544000] [eagle-usb] Pre-firmware modem removed
[17181624.040000] usb 3-1: new full speed USB device using uhci_hcd and address 4
[17181624.212000] usb 3-1: configuration #1 chosen from 1 choice
[17181624.264000] [eagle-usb] New USB ADSL device detected, waiting for DSP code...
[17181624.264000] [eagle-usb] Interface 0 accepted.
[17181624.268000] [eagle-usb] created proc entry at : /proc/driver/eagle-usb/003-004
[17182537.720000] eth0: link down
[17182537.720000] ADDRCONF(NETDEV_UP): eth0: link is not ready
plasma3d@plasma3d-desktop:~$ 
plasma3d@plasma3d-desktop:~$ 

```

if eny one now how to make my modem work pls help](*,) ](*,)

---

### Post by plasma3d on 2006-12-16
helpppppppppp!!!!!!!!!

---

