---
title: "dmesg output"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by tech4me on 2007-04-09
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:
28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001efc0000 (usable)
[17179569.184000]  BIOS-e820: 000000001efc0000 - 000000001efce000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001efce000 - 000000001eff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001eff0000 - 000000001f000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 495MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 126912
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 122816 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f8720
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x09000613 MSFT 0x00000097) @ 0x1efc0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x09000613 MSFT 0x00000097) @ 0x1efc0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x09000613 MSFT 0x00000097) @ 0x1efc0390
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x09000613 MSFT 0x00000097) @ 0x1efce040
[17179569.184000] ACPI: DSDT (v001  12345 12345123 0x00000123 INTL 0x20051117) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:6 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:6 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1f000000:dfc00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 3001.081 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.100000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.100000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.108000] Memory: 493536k/507648k available (1911k kernel code, 13512k reserved, 1073k data, 308k init, 0k highmem)
[17179571.108000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.188000] Calibrating delay using timer specific routine.. 6009.49 BogoMIPS (lpj=12018989)
[17179571.188000] Security Framework v1.0.0 initialized
[17179571.188000] SELinux:  Disabled at boot.
[17179571.188000] Mount-cache hash table entries: 512
[17179571.188000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e59d 00000000 00000001
[17179571.188000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000e59d 00000000 00000001
[17179571.188000] monitor/mwait feature present.
[17179571.188000] using mwait in idle threads.
[17179571.188000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179571.188000] CPU: L2 cache: 2048K
[17179571.188000] CPU: Hyper-Threading is disabled
[17179571.188000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000180 0000e59d 00000000 00000001
[17179571.188000] Checking 'hlt' instruction... OK.
[17179571.204000] SMP alternatives: switching to UP code
[17179571.204000] checking if image is initramfs... it is
[17179571.640000] Freeing initrd memory: 5326k freed
[17179571.640000] ACPI: Core revision 20060707
[17179571.644000] ACPI: Looking for DSDT ... not found!
[17179571.644000] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[17179571.644000] SMP alternatives: switching to SMP code
[17179571.644000] Booting processor 1/1 eip 3000
[17179571.656000] Initializing CPU#1
[17179571.736000] Calibrating delay using timer specific routine.. 6000.80 BogoMIPS (lpj=12001618)  **** face shld be replaced by 8**********
[17179571.736000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e59d 00000000 00000001
[17179571.736000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000e59d 00000000 00000001
[17179571.736000] monitor/mwait feature present.
[17179571.736000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179571.736000] CPU: L2 cache: 2048K
[17179571.736000] CPU: Hyper-Threading is disabled
[17179571.736000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000180 0000e59d 00000000 00000001
[17179571.736000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[17179571.736000] Total of 2 processors activated (12010.30 BogoMIPS).
[17179571.736000] ENABLING IO-APIC IRQs
[17179571.736000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.880000] checking TSC synchronization across 2 CPUs: passed.
[17179571.884000] Brought up 2 CPUs
[17179572.236000] migration_cost=4000
[17179572.236000] NET: Registered protocol family 16
[17179572.236000] EISA bus registered
[17179572.236000] ACPI: bus type pci registered
[17179572.236000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[17179572.236000] PCI: Using configuration type 1
[17179572.236000] Setting up standard PCI resources
[17179572.244000] ACPI: Interpreter enabled
[17179572.244000] ACPI: Using IOAPIC for interrupt routing
[17179572.248000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.248000] PCI: Probing PCI hardware (bus 00)
[17179572.252000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.1
[17179572.252000] PCI: Quirk-MSI-K8T Soundcard On
[17179572.252000] PCI: Unexpected Value in PCI-Register: no Change!
[17179572.252000] Boot video device is 0000:01:00.0
[17179572.252000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.268000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179572.276000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179572.280000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.280000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.280000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.280000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.280000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.280000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.280000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.280000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.280000] pnp: PnP ACPI init
[17179572.288000] pnp: PnP ACPI: found 13 devices
[17179572.288000] PnPBIOS: Disabled by ACPI PNP
[17179572.288000] PCI: Using ACPI for IRQ routing
[17179572.288000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.296000] pnp: 00:08: ioport range 0xa00-0xa0f has been reserved
[17179572.296000] pnp: 00:08: ioport range 0x290-0x29f has been reserved
[17179572.296000] pnp: 00:08: ioport range 0xa20-0xa2f has been reserved
[17179572.296000] pnp: 00:08: ioport range 0xa30-0xa3f has been reserved
[17179572.296000] pnp: 00:08: ioport range 0xa40-0xa4f has been reserved
[17179572.296000] PCI: Bridge: 0000:00:01.0
[17179572.296000]   IO window: disabled.
[17179572.296000]   MEM window: fca00000-feafffff
[17179572.296000]   PREFETCH window: e7f00000-efefffff
[17179572.296000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.296000] NET: Registered protocol family 2
[17179572.336000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.336000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179572.336000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179572.336000] TCP: Hash tables configured (established 16384 bind 8192)
[17179572.336000] TCP reno registered
[17179572.336000] audit: initializing netlink socket (disabled)
[17179572.336000] audit(1176159052.336:1): initialized
[17179572.336000] VFS: Disk quotas dquot_6.5.1
[17179572.336000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.336000] Initializing Cryptographic API
[17179572.336000] io scheduler noop registered
[17179572.336000] io scheduler anticipatory registered
[17179572.336000] io scheduler deadline registered
[17179572.336000] io scheduler cfq registered (default)
[17179572.336000] PCI: Bypassing VIA 8237 APIC De-Assert Message
[17179572.336000] isapnp: Scanning for PnP cards...
[17179572.688000] isapnp: No Plug & Play device found
[17179572.712000] Real Time Clock Driver v1.12ac
[17179572.712000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.716000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.716000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.716000] mice: PS/2 mouse device common for all mice
[17179572.716000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.716000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.716000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.716000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179572.716000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.716000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.716000] EISA: Probing bus 0 at eisa.0
[17179572.716000] EISA: Detected 0 cards.
[17179572.716000] TCP bic registered
[17179572.716000] NET: Registered protocol family 1
[17179572.716000] NET: Registered protocol family 8
[17179572.716000] NET: Registered protocol family 20
[17179572.716000] Starting balanced_irq
[17179572.716000] Using IPI No-Shortcut mode
[17179572.716000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.716000] Freeing unused kernel memory: 308k freed
[17179572.740000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.780000] Capability LSM initialized
[17179573.812000] ACPI: Processor [CPU1] (supports 16 throttling states)
[17179573.812000] ACPI: Processor [CPU2] (supports 16 throttling states)
[17179573.812000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179573.812000] ACPI: Getting cpuindex for acpiid 0x3
[17179573.812000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179573.812000] ACPI: Getting cpuindex for acpiid 0x4
[17179574.152000] SCSI subsystem initialized
[17179574.152000] libata version 1.20 loaded.
[17179574.156000] sata_via 0000:00:0f.0: version 1.1
[17179574.156000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 169
[17179574.156000] PCI: Via IRQ fixup for 0000:00:0f.0, from 11 to 9
[17179574.156000] sata_via 0000:00:0f.0: routed to hard irq line 9
[17179574.156000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE882 bmdma 0xE400 irq 169
[17179574.156000] ata2: SATA max UDMA/133 cmd 0xE800 ctl 0xE482 bmdma 0xE408 irq 169
[17179574.320000] scsi0 : sata_via
[17179574.484000] scsi1 : sata_via
[17179574.520000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[17179574.520000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 169
[17179574.520000] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 9
[17179574.520000] VP_IDE: chipset revision 6
[17179574.520000] VP_IDE: not 100% native mode: will probe irqs later
[17179574.520000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[17179574.520000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA,hdb:pio ****** first face replaced with D , second with p********
[17179574.520000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio   ************* both are replaced with 'p'************
[17179574.520000] Probing IDE interface ide0...
[17179574.936000] hda: ST380215A, ATA DISK drive
[17179575.608000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.608000] Probing IDE interface ide1...
[17179576.180000] hda: max request size: 512KiB
[17179576.220000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.244000] hda: cache flushes supported
[17179576.244000]  hda: hda2 hda3
[17179576.448000] Probing IDE interface ide1...
[17179576.500000] usbcore: registered new driver usbfs
[17179576.500000] usbcore: registered new driver hub
[17179576.512000] USB Universal Host Controller Interface driver v3.0
[17179576.512000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 177
[17179576.512000] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 1
[17179576.512000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179576.512000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179576.512000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000dc00
[17179576.512000] usb usb1: configuration #1 chosen from 1 choice
[17179576.512000] hub 1-0:1.0: USB hub found
[17179576.512000] hub 1-0:1.0: 2 ports detected
[17179576.616000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 177
[17179576.616000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 1
[17179576.616000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179576.616000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179576.616000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000d880
[17179576.616000] usb usb2: configuration #1 chosen from 1 choice
[17179576.616000] hub 2-0:1.0: USB hub found
[17179576.616000] hub 2-0:1.0: 2 ports detected
[17179576.720000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 177
[17179576.720000] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 1
[17179576.720000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179576.720000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179576.720000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000d800
[17179576.720000] usb usb3: configuration #1 chosen from 1 choice
[17179576.720000] hub 3-0:1.0: USB hub found
[17179576.720000] hub 3-0:1.0: 2 ports detected
[17179576.824000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 177
[17179576.824000] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 1
[17179576.824000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179576.824000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179576.824000] uhci_hcd 0000:00:10.3: irq 177, io base 0x0000d480
[17179576.824000] usb usb4: configuration #1 chosen from 1 choice
[17179576.824000] hub 4-0:1.0: USB hub found
[17179576.824000] hub 4-0:1.0: 2 ports detected
[17179576.928000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 177
[17179576.928000] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 1
[17179576.928000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179576.928000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179576.928000] ehci_hcd 0000:00:10.4: irq 177, io mem 0xfebefc00
[17179576.928000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.928000] usb usb5: configuration #1 chosen from 1 choice
[17179576.928000] hub 5-0:1.0: USB hub found
[17179576.928000] hub 5-0:1.0: 8 ports detected
[17179577.104000] Attempting manual resume
[17179577.136000] kjournald starting.  Commit interval 5 seconds
[17179577.136000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.944000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[17179578.076000] usb 5-3: configuration #1 chosen from 1 choice
[17179586.436000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.440000] agpgart: Detected VIA P4M800CE chipset
[17179586.448000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179586.764000] parport: PnPBIOS parport detected.
[17179586.764000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA] ************replaced with 8**********
[17179586.812000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179586.812000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179586.812000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 9
[17179586.816000] eth0: VIA Rhine II at 0x1ee00, 00:19:21:3c:93:f7, IRQ 185.
[17179586.820000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[17179586.840000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.848000] input: PC Speaker as /class/input/input1
[17179587.100000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179587.136000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.156000] usbcore: registered new driver libusual
[17179587.176000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 193
[17179587.176000] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 1
[17179587.176000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179587.196000] Initializing USB Mass Storage driver...
[17179587.196000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179587.196000] usb-storage: device found at 2
[17179587.196000] usbcore: registered new driver usb-storage
[17179587.196000] usb-storage: waiting for device to settle before scanning
[17179587.196000] USB Mass Storage support registered.
[17179587.520000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179587.548000] ts: Compaq touchscreen protocol output
[17179587.888000] lp0: using parport0 (interrupt-driven).
[17179587.912000] Adding 24088k swap on /dev/disk/by-uuid/d6f8e648-9dcf-42f0-b078-c94a788b784c.  Priority:-1 extents:1 across:24088k
[17179587.976000] EXT3 FS on hda2, internal journal
[17179588.196000] NET: Registered protocol family 17
[17179588.212000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179590.164000] ACPI: Power Button (FF) [PWRF]
[17179590.164000] ACPI: Sleep Button (CM) [SLPB]
[17179590.164000] ACPI: Power Button (CM) [PWRB]
[17179590.284000] ibm_acpi: ec object not found
[17179590.324000] pcc_acpi: loading...
[17179591.272000] NET: Registered protocol family 10
[17179591.272000] lo: Disabled Privacy Extensions
[17179591.272000] IPv6 over IPv4 tunneling driver
[17179592.196000] usb-storage: device scan complete
[17179592.200000]   Vendor: HL-DT-ST  Model: DVDRAM GSA-H42N   Rev: RL00
[17179592.200000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17179592.264000] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[17179592.264000] Uniform CD-ROM driver Revision: 3.20
[17179592.264000] sr 2:0:0:0: Attached scsi CD-ROM sr0
[17179592.280000] sr 2:0:0:0: Attached scsi generic sg0 type 5
[17179594.228000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179594.228000] apm: disabled - APM is not SMP safe.
[17179602.872000] Bluetooth: Core ver 2.8
[17179602.872000] NET: Registered protocol family 31
[17179602.872000] Bluetooth: HCI device and connection manager initialized
[17179602.872000] Bluetooth: HCI socket layer initialized
[17179602.908000] Bluetooth: L2CAP ver 2.8
[17179602.908000] Bluetooth: L2CAP socket layer initialized
[17179602.912000] Bluetooth: RFCOMM socket layer initialized
[17179602.912000] Bluetooth: RFCOMM TTY layer initialized
[17179602.912000] Bluetooth: RFCOMM ver 1.7
[17179611.120000] eth0: no IPv6 routers present
[17180622.964000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17180640.808000] eth0: no IPv6 routers present
















when it works fine
:lolflag:

---

### Post by chili555 on 2007-04-10
Not sure we can understand what your question may be. Could you please tell us more? Thanks.

---

### Post by tech4me on 2007-04-15
A strange problem, my network interface sometimes detected by Ubuntu and sometimes not

automatically (at the time of boot up ) it is not detecting network interface, but sometimes it 

detects( Dont get confuse) :confused: 

i dont know why it happens...

---

### Post by chili555 on 2007-04-17
Well, it surely is hard to decipher from your original post!

These things, failure to detect hardware and load the correct module, happens sometimes and I'm not sure anyone knows why, exactly. You can try telling the kernel to load the module explicitly and associate it with your ethernet interface. You would add a line to /etc/modules something like *alias eth0 <module>*

The trick is to find the correct module to associate. I think it may be via-rhine. We must confirm it, otherwise we create more problems then we solve. When the ethernet adapter is detected and running correctly, do this in a terminal:```
sudo lshw -C network
```Under 'ethernet' it will show the driver associated with your adapter.

You can then:```
sudo gedit /etc/modules
```to add a line:```
alias eth0 <module_u_found>
```Save and close gedit. Let us know if this helps.

---

