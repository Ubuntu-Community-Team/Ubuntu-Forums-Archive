---
title: "No Wifi on D-Link DWL-G520, HELP!"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by koffe on 2006-08-27
uname -r says: 
2.6.15-26-386.

iwconfig says:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

modprobe ath_pci says:
WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.15-26-386/madwifi/ath_rate_sample.ko): Operation not permitted
FATAL: Error inserting ath_pci (/lib/modules/2.6.15-26-386/madwifi/ath_pci.ko): Operation not permitted

What is this? I am new to Linux/Ubuntu (1 week). When I installed the system, the wifi just worked, the problem may be with some update... please help.

dmesg prints:
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003f7f0000 (usable)
[17179569.184000]  BIOS-e820: 000000003f7f0000 - 000000003f7f3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003f7f3000 - 000000003f800000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 119MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5760
[17179569.184000] On node 0 totalpages: 260080
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 30704 pages, LIFO batch:7
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 XPC                                   ) @ 0x000f9360
[17179569.184000] ACPI: RSDT (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3f7f3040
[17179569.184000] ACPI: FADT (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3f7f30c0
[17179569.184000] ACPI: MCFG (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3f7f7440
[17179569.184000] ACPI: MADT (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3f7f7340
[17179569.184000] ACPI: DSDT (v001 XPC     SB81V10 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:3 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:3 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3f800000:a0800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3416.043 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.780000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.780000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.800000] Memory: 1020512k/1040320k available (1976k kernel code, 19096k reserved, 606k data, 288k init, 122816k highmem)
[17179569.800000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.880000] Calibrating delay using timer specific routine.. 6838.59 BogoMIPS (lpj=13677190)
[17179569.880000] Security Framework v1.0.0 initialized
[17179569.880000] SELinux:  Disabled at boot.
[17179569.880000] Mount-cache hash table entries: 512
[17179569.880000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179569.880000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179569.880000] monitor/mwait feature present.
[17179569.880000] using mwait in idle threads.
[17179569.880000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.880000] CPU: L2 cache: 1024K
[17179569.880000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000 00000000
[17179569.880000] mtrr: v2.0 (20020519)
[17179569.880000] CPU: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 04
[17179569.880000] Enabling fast FPU save and restore... done.
[17179569.880000] Enabling unmasked SIMD FPU exception support... done.
[17179569.880000] Checking 'hlt' instruction... OK.
[17179569.896000] checking if image is initramfs... it is
[17179570.356000] Freeing initrd memory: 6840k freed
[17179570.368000] ACPI: Looking for DSDT ... not found!
[17179570.372000] ENABLING IO-APIC IRQs
[17179570.372000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.516000] NET: Registered protocol family 16
[17179570.516000] EISA bus registered
[17179570.516000] ACPI: bus type pci registered
[17179570.528000] PCI: PCI BIOS revision 3.00 entry at 0xfb5b0, last bus=2
[17179570.528000] PCI: Using MMCONFIG
[17179570.528000] ACPI: Subsystem revision 20051216
[17179570.536000] ACPI: Interpreter enabled
[17179570.536000] ACPI: Using IOAPIC for interrupt routing
[17179570.536000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.536000] PCI: Probing PCI hardware (bus 00)
[17179570.540000] Boot video device is 0000:00:02.0
[17179570.540000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.540000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.540000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.548000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[17179570.548000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.552000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[17179570.552000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179570.552000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179570.552000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179570.552000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.552000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.552000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.552000] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[17179570.552000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.552000] pnp: PnP ACPI init
[17179570.556000] pnp: PnP ACPI: found 13 devices
[17179570.556000] PnPBIOS: Disabled by ACPI PNP
[17179570.556000] PCI: Using ACPI for IRQ routing
[17179570.556000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.576000] pnp: 00:09: ioport range 0x400-0x4bf could not be reserved
[17179570.576000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.576000] PCI: Bridge: 0000:00:1c.0
[17179570.576000]   IO window: disabled.
[17179570.576000]   MEM window: d0000000-d00fffff
[17179570.576000]   PREFETCH window: 40000000-400fffff
[17179570.576000] PCI: Bridge: 0000:00:1e.0
[17179570.576000]   IO window: d000-dfff
[17179570.576000]   MEM window: d0100000-d01fffff
[17179570.576000]   PREFETCH window: disabled.
[17179570.576000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.576000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.576000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.576000] audit: initializing netlink socket (disabled)
[17179570.576000] audit(1156708595.576:1): initialized
[17179570.576000] highmem bounce pool size: 64 pages
[17179570.576000] VFS: Disk quotas dquot_6.5.1
[17179570.576000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.576000] Initializing Cryptographic API
[17179570.576000] io scheduler noop registered
[17179570.576000] io scheduler anticipatory registered
[17179570.576000] io scheduler deadline registered
[17179570.576000] io scheduler cfq registered
[17179570.576000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.576000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.576000] assign_interrupt_mode Found MSI capability
[17179570.576000] Allocate Port Service[pcie00]
[17179570.576000] Allocate Port Service[pcie02]
[17179570.576000] Allocate Port Service[pcie03]
[17179570.576000] isapnp: Scanning for PnP cards...
[17179570.928000] isapnp: No Plug & Play device found
[17179570.944000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179570.944000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179570.948000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.948000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.948000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.948000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.948000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.948000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.948000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.948000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.948000] mice: PS/2 mouse device common for all mice
[17179570.952000] EISA: Probing bus 0 at eisa.0
[17179570.952000] EISA: Detected 0 cards.
[17179570.952000] NET: Registered protocol family 2
[17179570.988000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.988000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.988000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.988000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.988000] TCP reno registered
[17179570.988000] TCP bic registered
[17179570.988000] NET: Registered protocol family 1
[17179570.988000] NET: Registered protocol family 8
[17179570.988000] NET: Registered protocol family 20
[17179570.988000] Using IPI Shortcut mode
[17179570.988000] ACPI wakeup devices: 
[17179570.988000] PCI0 PEX0 PEX1 PEX2 PEX3 HUB0 UAR1 USB0 USB1 USB2 USB3 USBE AC97 AZAL 
[17179570.988000] ACPI: (supports S0 S1 S4 S5)
[17179570.988000] Freeing unused kernel memory: 288k freed
[17179571.028000] vga16fb: initializing
[17179571.028000] vga16fb: mapped to 0xc00a0000
[17179571.128000] Console: switching to colour frame buffer device 80x25
[17179571.128000] fb0: VGA16 VGA frame buffer device
[17179571.276000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.204000] Capability LSM initialized
[17179572.228000] ACPI: Fan [FAN] (on)
[17179572.232000] ACPI: Thermal Zone [THRM] (42 C)
[17179572.656000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179572.656000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 193
[17179572.656000] ICH6: chipset revision 3
[17179572.656000] ICH6: not 100% native mode: will probe irqs later
[17179572.656000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:pio, hdb:pio
[17179572.656000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:DMA
[17179572.656000] Probing IDE interface ide0...
[17179573.672000] hdb: _NEC DVD_RW ND-3500AG, ATAPI CD/DVD-ROM drive
[17179573.728000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.728000] Probing IDE interface ide1...
[17179574.300000] hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.300000] Uniform CD-ROM driver Revision: 3.20
[17179574.336000] SCSI subsystem initialized
[17179574.336000] ACPI: bus type scsi registered
[17179574.336000] libata version 1.20 loaded.
[17179574.336000] ahci 0000:00:1f.2: version 1.2
[17179574.336000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 201
[17179580.156000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179580.156000] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl IDE mode
[17179580.156000] ahci 0000:00:1f.2: flags: 64bit ncq pm led slum part 
[17179580.156000] ata1: SATA max UDMA/133 cmd 0xF8860100 ctl 0x0 bmdma 0x0 irq 201
[17179580.156000] ata2: SATA max UDMA/133 cmd 0xF8860180 ctl 0x0 bmdma 0x0 irq 201
[17179580.156000] ata3: SATA max UDMA/133 cmd 0xF8860200 ctl 0x0 bmdma 0x0 irq 201
[17179580.156000] ata4: SATA max UDMA/133 cmd 0xF8860280 ctl 0x0 bmdma 0x0 irq 201
[17179580.360000] ata1: no device found (phy stat 00000000)
[17179580.360000] scsi0 : ahci
[17179580.564000] ata2: no device found (phy stat 00000000)
[17179580.564000] scsi1 : ahci
[17179580.768000] ata3: no device found (phy stat 00000000)
[17179580.768000] scsi2 : ahci
[17179581.028000] ata4: dev 0 cfg 00:0c5a 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:007f 93:0000
[17179581.028000] ata4: dev 0 ATA-6, max UDMA/133, 390721968 sectors: LBA48
[17179581.032000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe7700
[17179581.032000] ata4: dev 0 configured for UDMA/133
[17179581.032000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe7700
[17179581.036000] scsi3 : ahci
[17179581.036000]   Vendor: ATA       Model: ST3200822AS       Rev: 3.01
[17179581.036000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179581.044000] Driver 'sd' needs updating - please use bus_type methods
[17179581.048000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[17179581.048000] SCSI device sda: drive cache: write back
[17179581.048000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[17179581.048000] SCSI device sda: drive cache: write back
[17179581.048000]  sda: sda1 sda2 < sda5 >
[17179581.084000] sd 3:0:0:0: Attached scsi disk sda
[17179581.216000] usbcore: registered new driver usbfs
[17179581.216000] usbcore: registered new driver hub
[17179581.220000] USB Universal Host Controller Interface driver v2.3
[17179581.220000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 209
[17179581.220000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179581.220000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179581.220000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179581.220000] uhci_hcd 0000:00:1d.0: irq 209, io base 0x0000e000
[17179581.220000] hub 1-0:1.0: USB hub found
[17179581.220000] hub 1-0:1.0: 2 ports detected
[17179581.264000] ieee1394: Initialized config rom entry `ip1394'
[17179581.324000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 201
[17179581.324000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179581.324000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179581.324000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179581.324000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x0000e100
[17179581.324000] hub 2-0:1.0: USB hub found
[17179581.324000] hub 2-0:1.0: 2 ports detected
[17179581.428000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 193
[17179581.428000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179581.428000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179581.428000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179581.428000] uhci_hcd 0000:00:1d.2: irq 193, io base 0x0000e200
[17179581.428000] hub 3-0:1.0: USB hub found
[17179581.428000] hub 3-0:1.0: 2 ports detected
[17179581.532000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179581.532000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179581.532000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179581.532000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179581.532000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000e300
[17179581.532000] hub 4-0:1.0: USB hub found
[17179581.532000] hub 4-0:1.0: 2 ports detected
[17179581.564000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179581.636000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179581.636000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 18 (level, low) -> IRQ 193
[17179581.660000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 209
[17179581.660000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179581.660000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179581.660000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179581.660000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179581.660000] ehci_hcd 0000:00:1d.7: irq 209, io mem 0xd02c4000
[17179581.664000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179581.664000] hub 5-0:1.0: USB hub found
[17179581.664000] hub 5-0:1.0: 8 ports detected
[17179581.692000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[193]  MMIO=[d0110000-d01107ff]  Max Packet=[2048]
[17179581.788000] Probing IDE interface ide1...
[17179582.088000] usb 1-1: device not accepting address 2, error -71
[17179582.372000] Attempting manual resume
[17179582.408000] EXT3-fs: mounted filesystem with ordered data mode.
[17179582.424000] kjournald starting.  Commit interval 5 seconds
[17179582.768000] usb 5-1: new high speed USB device using ehci_hcd and address 2
[17179582.972000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00301bb600002774]
[17179583.152000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[17179583.892000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[17179584.276000] usb 4-2: new low speed USB device using uhci_hcd and address 3
[17179590.184000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17179590.396000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.524000] agpgart: Detected an Intel 915G Chipset.
[17179590.524000] agpgart: Detected 7932K stolen memory.
[17179590.524000] hw_random: RNG not detected
[17179590.536000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179590.800000] Real Time Clock Driver v1.12
[17179590.904000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179590.908000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[17179590.912000] ath_pci: Unknown symbol ath_rate_tx_complete
[17179590.912000] ath_pci: Unknown symbol _ath_hal_attach
[17179590.912000] ath_pci: Unknown symbol ath_rate_attach
[17179590.912000] ath_pci: Unknown symbol ath_rate_newassoc
[17179590.912000] ath_pci: Unknown symbol ath_hal_computetxtime
[17179590.912000] ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
[17179590.912000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[17179590.912000] ath_pci: Unknown symbol ath_hal_detach
[17179590.912000] ath_pci: Unknown symbol ath_hal_probe
[17179590.912000] ath_pci: Unknown symbol ath_rate_node_cleanup
[17179590.912000] ath_pci: Unknown symbol ath_rate_detach
[17179590.912000] ath_pci: Unknown symbol ath_rate_node_init
[17179590.912000] ath_pci: Unknown symbol ath_rate_findrate
[17179590.912000] ath_pci: Unknown symbol ath_hal_init_channels
[17179590.912000] ath_pci: Unknown symbol ath_rate_newstate
[17179590.912000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[17179590.912000] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[17179591.000000] parport: PnPBIOS parport detected.
[17179591.000000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179591.008000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.008000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.148000] input: PC Speaker as /class/input/input1
[17179591.160000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179591.160000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179591.208000] FDC 0 is a post-1991 82077
[17179591.504000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[17179591.600000] hda_codec: Cannot set up configuration from BIOS.  Using 3-stack mode...
[17179591.696000] tg3.c:v3.47 (Dec 28, 2005)
[17179591.696000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179591.696000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179591.716000] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:30:1b:b6:27:10
[17179591.716000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[17179591.716000] eth0: dma_rwctrl[76180000]
[17179591.760000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0C17
[17179591.764000] usbcore: registered new driver usblp
[17179591.764000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179591.764000] usbcore: registered new driver hiddev
[17179591.768000] Initializing USB Mass Storage driver...
[17179591.784000] input: Logitech USB Receiver as /class/input/input2
[17179591.784000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-2
[17179591.784000] usbcore: registered new driver usbhid
[17179591.784000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179591.784000] scsi4 : SCSI emulation for USB Mass Storage devices
[17179591.784000] usb-storage: device found at 2
[17179591.784000] usb-storage: waiting for device to settle before scanning
[17179591.784000] scsi5 : SCSI emulation for USB Mass Storage devices
[17179591.784000] usb-storage: device found at 3
[17179591.784000] usb-storage: waiting for device to settle before scanning
[17179591.784000] usbcore: registered new driver usb-storage
[17179591.784000] USB Mass Storage support registered.
[17179591.880000] ts: Compaq touchscreen protocol output
[17179592.324000] lp0: using parport0 (interrupt-driven).
[17179592.352000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179592.352000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179592.352000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179592.396000] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[17179592.496000] EXT3 FS on sda1, internal journal
[17179592.628000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179592.628000] md: bitmap version 4.39
[17179592.940000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179593.588000] NET: Registered protocol family 17
[17179593.948000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[17179593.948000] tg3: eth0: Flow control is off for TX and off for RX.
[17179596.788000]   Vendor: USB2.0    Model: CF  CardReader    Rev:     
[17179596.788000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179596.788000]   Vendor: WDC WD20  Model: 00JB-00GVC0       Rev: 0000
[17179596.788000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179596.788000] SCSI device sdc: 390721968 512-byte hdwr sectors (200050 MB)
[17179596.788000] sdc: assuming drive cache: write through
[17179596.788000] SCSI device sdc: 390721968 512-byte hdwr sectors (200050 MB)
[17179596.788000] sdc: assuming drive cache: write through
[17179596.788000]  sdc:<5>sd 4:0:0:0: Attached scsi removable disk sdb
[17179596.792000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[17179596.796000]   Vendor: USB2.0    Model: CBO CardReader    Rev:     
[17179596.796000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179596.800000] sd 4:0:0:1: Attached scsi removable disk sdd
[17179596.800000] sd 4:0:0:1: Attached scsi generic sg2 type 0
[17179596.800000] usb-storage: device scan complete
[17179596.800000]  sdc1
[17179596.800000] sd 5:0:0:0: Attached scsi disk sdc
[17179596.800000] sd 5:0:0:0: Attached scsi generic sg3 type 0
[17179596.800000] usb-storage: device scan complete

---

### Post by funchords on 2006-08-27
Hmmm strange.

Other than the automatic updates, have you done any other modifications to your system?  This was working a week ago?

If so, there is a log in /var/log/dpkg.log that you can read.  This will tell you of your most recent updates.  Perhaps that will yield a clue.

---

### Post by funchords on 2006-08-27
Maybe something removed it...

sudo modprobe -v ath_pci

...anything reported?

---

### Post by koffe on 2006-08-28
Very strange, I did nothing, the system works, long idle times are a problem, but that might be fixed with driver updates, thank's for the help!

---

