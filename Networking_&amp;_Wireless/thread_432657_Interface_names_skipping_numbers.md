---
title: "Interface names skipping numbers?"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by pepolez on 2007-05-04
After a reinstall of ubuntu edgy, I've found that my network interface numbering has messed up.

Currently, I have a Realtek 8139too compatible PCI network card, which should be eth0 and an onboard VIA Rhine network card that should be eth1. My system is reporting the Realtek card as eth2, which I can enable (ifup) but not use. It is also reporting the VIA Rhine card as eth0, which I can enable and use. There is no eth1.

I've already tried swapping out the Realtek card for an identical one, which I know is working fine, but that did not help.

uname -a:
> 
Linux nibbler 2.6.17-11-386 #2 Tue Mar 13 23:30:30 UTC 2007 i686 GNU/Linux


dmesg:
> 
[17179569.184000] Linux version 2.6.17-11-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Mar 13 23:30:30 UTC 2007 (Ubuntu 2.6.17-11.37-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6560
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 KM400                                 ) @ 0x000f7f80
[17179569.184000] ACPI: RSDT (v001 KM400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[17179569.184000] ACPI: FADT (v001 KM400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[17179569.184000] ACPI: MADT (v001 KM400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff7800
[17179569.184000] ACPI: DSDT (v001 KM400  AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=86489ac5-7663-468c-9ec2-389b9aa92513 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1665.973 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.804000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.804000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.836000] Memory: 1028528k/1048512k available (1829k kernel code, 19276k reserved, 1041k data, 288k init, 131008k highmem)
[17179569.836000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.916000] Calibrating delay using timer specific routine.. 3335.34 BogoMIPS (lpj=6670680)
[17179569.916000] Security Framework v1.0.0 initialized
[17179569.916000] SELinux:  Disabled at boot.
[17179569.916000] Mount-cache hash table entries: 512
[17179569.916000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179569.916000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179569.916000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.916000] CPU: L2 Cache: 256K (64 bytes/line)
[17179569.916000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[17179569.916000] CPU: AMD Sempron(tm)   2400+ stepping 01
[17179569.916000] Checking 'hlt' instruction... OK.
[17179569.932000] SMP alternatives: switching to UP code
[17179569.932000] Freeing SMP alternatives: 0k freed
[17179569.932000] checking if image is initramfs... it is
[17179570.600000] Freeing initrd memory: 6713k freed
[17179570.600000] ACPI: Core revision 20060707
[17179570.608000] ACPI: Looking for DSDT ... not found!
[17179570.612000] ENABLING IO-APIC IRQs
[17179570.612000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.756000] NET: Registered protocol family 16
[17179570.756000] EISA bus registered
[17179570.756000] ACPI: bus type pci registered
[17179570.776000] PCI: PCI BIOS revision 2.10 entry at 0xfbcf0, last bus=1
[17179570.776000] PCI: Using configuration type 1
[17179570.776000] Setting up standard PCI resources
[17179570.800000] ACPI: Interpreter enabled
[17179570.800000] ACPI: Using IOAPIC for interrupt routing
[17179570.800000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.800000] PCI: Probing PCI hardware (bus 00)
[17179570.800000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.800000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.0
[17179570.800000] PCI: Quirk-MSI-K8T Soundcard On
[17179570.800000] PCI: MSI-K8T soundcard on
[17179570.804000] Boot video device is 0000:01:00.0
[17179570.804000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.832000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[17179570.832000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
[17179570.832000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[17179570.832000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.832000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.832000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.832000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.832000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.836000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *15, disabled.
[17179570.836000] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[17179570.836000] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[17179570.836000] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[17179570.840000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.840000] pnp: PnP ACPI init
[17179570.844000] pnp: PnP ACPI: found 11 devices
[17179570.844000] PnPBIOS: Disabled by ACPI PNP
[17179570.844000] PCI: Using ACPI for IRQ routing
[17179570.844000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.868000] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[17179570.868000] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[17179570.868000] PCI: Bridge: 0000:00:01.0
[17179570.868000]   IO window: disabled.
[17179570.868000]   MEM window: e0000000-e2ffffff
[17179570.868000]   PREFETCH window: d0000000-dfffffff
[17179570.868000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.868000] NET: Registered protocol family 2
[17179570.908000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.908000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.908000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.908000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.908000] TCP reno registered
[17179570.908000] audit: initializing netlink socket (disabled)
[17179570.908000] audit(1178311719.908:1): initialized
[17179570.908000] highmem bounce pool size: 64 pages
[17179570.908000] VFS: Disk quotas dquot_6.5.1
[17179570.908000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.908000] Initializing Cryptographic API
[17179570.908000] io scheduler noop registered
[17179570.908000] io scheduler anticipatory registered
[17179570.908000] io scheduler deadline registered
[17179570.908000] io scheduler cfq registered (default)
[17179570.908000] PCI: Bypassing VIA 8237 APIC De-Assert Message
[17179570.908000] isapnp: Scanning for PnP cards...
[17179571.264000] isapnp: No Plug & Play device found
[17179571.288000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.288000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.292000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.292000] mice: PS/2 mouse device common for all mice
[17179571.292000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.292000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.292000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.292000] PNP: No PS/2 controller found. Probing ports directly.
[17179571.292000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.292000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.292000] EISA: Probing bus 0 at eisa.0
[17179571.292000] Cannot allocate resource for EISA slot 4
[17179571.292000] Cannot allocate resource for EISA slot 5
[17179571.292000] EISA: Detected 0 cards.
[17179571.292000] TCP bic registered
[17179571.292000] NET: Registered protocol family 1
[17179571.292000] NET: Registered protocol family 8
[17179571.292000] NET: Registered protocol family 20
[17179571.292000] Using IPI Shortcut mode
[17179571.292000] ACPI: (supports S0 S1 S4 S5)
[17179571.292000] Freeing unused kernel memory: 288k freed
[17179572.432000] Capability LSM initialized
[17179572.468000] ACPI: Fan [FAN] (on)
[17179572.476000] ACPI: Thermal Zone [THRM] (48 C)
[17179572.984000] SiI680: IDE controller at PCI slot 0000:00:07.0
[17179572.984000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 18 (level, low) -> IRQ 169
[17179572.984000] SiI680: chipset revision 2
[17179572.984000] SiI680: BASE CLOCK == 133
[17179572.984000] SiI680: 100% native mode on irq 169
[17179572.984000]     ide0: MMIO-DMA , BIOS settings: hda:pio, hdb:pio
[17179572.984000]     ide1: MMIO-DMA , BIOS settings: hdc:pio, hdd:pio
[17179572.984000] Probing IDE interface ide0...
[17179573.276000] hda: ST3120022A, ATA DISK drive
[17179573.556000] hdb: WDC WD2000JB-00GVA0, ATA DISK drive
[17179573.612000] ide0 at 0xf8802080-0xf8802087,0xf880208a on irq 169
[17179573.612000] Probing IDE interface ide1...
[17179574.184000] hda: max request size: 64KiB
[17179574.188000] hda: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179574.188000] hda: cache flushes supported
[17179574.188000]  hda: hda1 hda2 hda3 hda4 < hda5 hda6 hda7 >
[17179574.248000] hdb: max request size: 64KiB
[17179574.268000] hdb: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[17179574.268000] hdb: cache flushes supported
[17179574.268000]  hdb: hdb1
[17179574.756000] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[17179574.756000] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[17179574.756000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 15, using IRQ 20
[17179574.756000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179574.756000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 177
[17179574.756000] PCI: Via IRQ fixup for 0000:00:0f.0, from 255 to 1
[17179574.756000] VP_IDE: chipset revision 6
[17179574.756000] VP_IDE: not 100% native mode: will probe irqs later
[17179574.756000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[17179574.756000]     ide2: BM-DMA at 0xa800-0xa807, BIOS settings: hde:DMA, hdf:DMA
[17179574.756000]     ide3: BM-DMA at 0xa808-0xa80f, BIOS settings: hdg:DMA, hdh:pio
[17179574.756000] Probing IDE interface ide2...
[17179575.176000] hde: WDC WD1200BB-00DAA0, ATA DISK drive
[17179575.624000] hdf: HL-DT-STDVD-ROM GDR8161B, ATAPI CD/DVD-ROM drive
[17179575.688000] ide2 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.708000] hde: max request size: 512KiB
[17179575.708000] hde: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179575.712000] hde: cache flushes supported
[17179575.712000]  hde: hde1
[17179575.720000] Probing IDE interface ide3...
[17179576.024000] hdg: probing with STATUS(0x50) instead of ALTSTATUS(0x08)
[17179576.192000] hdg: probing with STATUS(0x51) instead of ALTSTATUS(0x0a)
[17179576.472000] hdg: probing with STATUS(0x51) instead of ALTSTATUS(0x0a)
[17179576.584000] hdg: HL-DT-ST DVDRAM GSA-4163B, ATAPI CD/DVD-ROM drive
[17179576.920000] ide3 at 0x170-0x177,0x376 on irq 15
[17179576.952000] hdf: ATAPI 48X DVD-ROM drive, 256kB Cache, UDMA(33)
[17179576.952000] Uniform CD-ROM driver Revision: 3.20
[17179577.004000] hdg: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.200000] Probing IDE interface ide1...
[17179577.236000] usbcore: registered new driver usbfs
[17179577.236000] usbcore: registered new driver hub
[17179577.240000] USB Universal Host Controller Interface driver v3.0
[17179577.240000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179577.240000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
[17179577.240000] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 9
[17179577.240000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179577.240000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179577.240000] uhci_hcd 0000:00:10.0: irq 185, io base 0x0000ac00
[17179577.240000] usb usb1: configuration #1 chosen from 1 choice
[17179577.240000] hub 1-0:1.0: USB hub found
[17179577.240000] hub 1-0:1.0: 2 ports detected
[17179577.344000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
[17179577.344000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 9
[17179577.344000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179577.344000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179577.344000] uhci_hcd 0000:00:10.1: irq 185, io base 0x0000b000
[17179577.344000] usb usb2: configuration #1 chosen from 1 choice
[17179577.344000] hub 2-0:1.0: USB hub found
[17179577.344000] hub 2-0:1.0: 2 ports detected
[17179577.448000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
[17179577.448000] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 9
[17179577.448000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179577.448000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179577.448000] uhci_hcd 0000:00:10.2: irq 185, io base 0x0000b400
[17179577.448000] usb usb3: configuration #1 chosen from 1 choice
[17179577.448000] hub 3-0:1.0: USB hub found
[17179577.448000] hub 3-0:1.0: 2 ports detected
[17179577.552000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
[17179577.552000] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 9
[17179577.552000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179577.552000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179577.552000] uhci_hcd 0000:00:10.3: irq 185, io base 0x0000b800
[17179577.552000] usb usb4: configuration #1 chosen from 1 choice
[17179577.552000] hub 4-0:1.0: USB hub found
[17179577.552000] hub 4-0:1.0: 2 ports detected
[17179577.676000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
[17179577.676000] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 9
[17179577.676000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179577.676000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179577.676000] ehci_hcd 0000:00:10.4: irq 185, io mem 0xe4002000
[17179577.676000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.676000] usb usb5: configuration #1 chosen from 1 choice
[17179577.676000] hub 5-0:1.0: USB hub found
[17179577.676000] hub 5-0:1.0: 8 ports detected
[17179578.668000] ReiserFS: hda5: found reiserfs format "3.6" with standard journal
[17179579.072000] usb 5-7: new high speed USB device using ehci_hcd and address 4
[17179579.204000] usb 5-7: configuration #1 chosen from 1 choice
[17179579.204000] hub 5-7:1.0: USB hub found
[17179579.204000] hub 5-7:1.0: 4 ports detected
[17179579.252000] ReiserFS: hda5: using ordered data mode
[17179579.268000] ReiserFS: hda5: journal params: device hda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[17179579.268000] ReiserFS: hda5: checking transaction log (hda5)
[17179579.308000] ReiserFS: hda5: Using r5 hash to sort names
[17179579.548000] usb 5-8: new high speed USB device using ehci_hcd and address 5
[17179579.684000] usb 5-8: configuration #1 chosen from 1 choice
[17179579.924000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179580.088000] usb 2-1: configuration #1 chosen from 1 choice
[17179580.092000] hub 2-1:1.0: USB hub found
[17179580.096000] hub 2-1:1.0: 4 ports detected
[17179580.444000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[17179580.620000] usb 2-2: configuration #1 chosen from 1 choice
[17179580.828000] usb 2-1.1: new low speed USB device using uhci_hcd and address 4
[17179580.960000] usb 2-1.1: configuration #1 chosen from 1 choice
[17179581.168000] usb 2-1.4: new full speed USB device using uhci_hcd and address 5
[17179581.304000] usb 2-1.4: configuration #1 chosen from 1 choice
[17179589.888000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.924000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179590.300000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.716000] agpgart: Detected VIA KM400/KM400A chipset
[17179590.732000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179590.996000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179590.996000] 8139cp: pci dev 0000:00:06.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[17179590.996000] 8139cp: Try the "8139too" driver instead.
[17179591.012000] 8139too Fast Ethernet driver 0.9.27
[17179591.012000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 193
[17179591.012000] eth0: RealTek RTL8139 at 0xf88f8000, 00:e0:4c:33:3b:93, IRQ 193
[17179591.012000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179591.112000] nvidia: module license 'NVIDIA' taints kernel.
[17179591.116000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[17179591.116000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179591.364000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179591.364000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[17179591.364000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 209
[17179591.364000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 1
[17179591.364000] eth1: VIA Rhine II at 0x1c000, 00:11:09:2c:59:e6, IRQ 209.
[17179591.368000] eth1: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179591.484000] Floppy drive(s): fd0 is 1.44M
[17179591.500000] FDC 0 is a post-1991 82077
[17179591.708000] Real Time Clock Driver v1.12ac
[17179591.732000] input: PC Speaker as /class/input/input0
[17179591.820000] parport: PnPBIOS parport detected.
[17179591.820000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179591.852000] usbcore: registered new driver hiddev
[17179591.868000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
[17179591.868000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.1-2
[17179591.884000] input: Gaming Keyboard as /class/input/input2
[17179591.884000] input: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:10.1-1.1
[17179591.944000] input: Gaming Keyboard as /class/input/input3
[17179591.944000] input,hiddev96: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:10.1-1.1
[17179591.952000] input: G11 Keyboard as /class/input/input4
[17179591.952000] input,hiddev97: USB HID v1.11 Keypad [G11 Keyboard] on usb-0000:00:10.1-1.4
[17179591.952000] usbcore: registered new driver usbhid
[17179591.952000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179592.068000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179592.068000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 217
[17179592.068000] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 9
[17179592.068000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179592.268000] eth2: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179592.364000] usbcore: registered new driver libusual
[17179592.772000] ts: Compaq touchscreen protocol output
[17179592.792000] SCSI subsystem initialized
[17179592.796000] Initializing USB Mass Storage driver...
[17179592.796000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179592.796000] usb-storage: device found at 5
[17179592.796000] usb-storage: waiting for device to settle before scanning
[17179592.796000] usbcore: registered new driver usb-storage
[17179592.796000] USB Mass Storage support registered.
[17179593.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179593.380000] lp0: using parport0 (interrupt-driven).
[17179593.468000] Adding 522104k swap on /dev/disk/by-uuid/fb79acb2-f87a-4fa3-a9cf-c4cbd42551a3.  Priority:-1 extents:1 across:522104k
[17179594.228000] NET: Registered protocol family 17
[17179594.340000] NET: Registered protocol family 10
[17179594.340000] lo: Disabled Privacy Extensions
[17179594.340000] IPv6 over IPv4 tunneling driver
[17179597.796000] usb-storage: device scan complete
[17179597.796000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
[17179597.796000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179597.796000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
[17179597.796000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179597.800000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
[17179597.800000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179597.800000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
[17179597.800000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179597.836000] sd 0:0:0:0: Attached scsi removable disk sda
[17179597.844000] sd 0:0:0:1: Attached scsi removable disk sdb
[17179597.856000] sd 0:0:0:2: Attached scsi removable disk sdc
[17179597.864000] sd 0:0:0:3: Attached scsi removable disk sdd
[17179597.892000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179597.892000] sd 0:0:0:1: Attached scsi generic sg1 type 0
[17179597.892000] sd 0:0:0:2: Attached scsi generic sg2 type 0
[17179597.892000] sd 0:0:0:3: Attached scsi generic sg3 type 0
[17179598.996000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179598.996000] md: bitmap version 4.39
[17179599.168000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[17179604.508000] eth2: no IPv6 routers present
[17179605.204000] eth0: no IPv6 routers present
[17179609.536000] ReiserFS: hda6: found reiserfs format "3.6" with standard journal
[17179610.420000] ReiserFS: hda6: using ordered data mode
[17179610.436000] ReiserFS: hda6: journal params: device hda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[17179610.436000] ReiserFS: hda6: checking transaction log (hda6)
[17179610.740000] ReiserFS: hda6: Using r5 hash to sort names
[17179610.812000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179610.864000] NTFS volume version 3.1.
[17179613.236000] pcc_acpi: loading...
[17179613.252000] ACPI: Power Button (FF) [PWRF]
[17179613.252000] ACPI: Power Button (CM) [PWRB]
[17179613.252000] ACPI: Sleep Button (CM) [SLPB]
[17179613.300000] ibm_acpi: ec object not found
[17179613.604000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179623.476000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179623.476000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179623.476000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179624.316000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179624.316000] apm: overridden by ACPI.
[17179624.560000] Bluetooth: Core ver 2.8
[17179624.560000] NET: Registered protocol family 31
[17179624.560000] Bluetooth: HCI device and connection manager initialized
[17179624.560000] Bluetooth: HCI socket layer initialized
[17179624.600000] Bluetooth: L2CAP ver 2.8
[17179624.600000] Bluetooth: L2CAP socket layer initialized
[17179624.640000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179624.672000] Bluetooth: RFCOMM socket layer initialized
[17179624.672000] Bluetooth: RFCOMM TTY layer initialized
[17179624.672000] Bluetooth: RFCOMM ver 1.7


lspci:
> 
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:07.0 RAID bus controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)


---

### Post by pepolez on 2007-05-04
And lshw, which wouldn't fit in the first post:
> 
nibbler                   
    description: Desktop Computer
    product: KM400-8237
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MS-6734
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/28/2004)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy288
0 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm)   2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1666MHz
          capacity: 2100MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dno
w up ts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 1GB
          capacity: 2GB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: c0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:c0000000-cfffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV43 [GeForce 6600/GeForce 6600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a2
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master vga_palette cap_list
                configuration: driver=nvidia
                resources: iomemory:e0000000-e0ffffff iomemory:d0000000-dfffffff iomemory:e1000000-e1ffffff irq:201
        *-network:0
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 6
             bus info: pci@00:06.0
             logical name: eth2
             version: 10
             serial: 00:e0:4c:33:3b:93
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.2.3 link=yes multicast=yes port=MII s
peed=100MB/s
             resources: ioport:9000-90ff iomemory:e4001000-e40010ff irq:193
        *-storage
             description: RAID bus controller
             product: PCI0680 Ultra ATA-133 Host Controller
             vendor: Silicon Image, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             configuration: driver=SiI_IDE
             resources: ioport:9400-9407 ioport:9800-9803 ioport:9c00-9c07 ioport:a000-a003 ioport:a400-a40f iomemory:e4000000-e40000ff irq:169
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: ST3120022A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 8.54
                   serial: 5JS3GA1M
                   size: 111GB
                   capacity: 111GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 14GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 101MB
                      capabilities: primary
                 *-volume:2
                      description: Linux swap / Solaris partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 509MB
                      capabilities: primary nofs
                 *-volume:3
                      description: Extended partition
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      capacity: 96GB
                      capabilities: extended partitioned partitioned:extended
              *-disk:1
                   description: ATA Disk
                   product: WDC WD2000JB-00GVA0
                   vendor: Western Digital
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 08.02D08
                   serial: WD-WCALL1040568
                   size: 186GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 186GB
                      capabilities: primary
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@00:0f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:a800-a80f irq:177
           *-ide:0
                description: IDE Channel 0
                physical id: 2
                bus info: ide@2
                logical name: ide2
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD1200BB-00DAA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@2.0
                   logical name: /dev/hde
                   version: 65.13G65
                   serial: WD-WMACK1255227
                   size: 111GB
                   capacity: 111GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@2.0,1
                      logical name: /dev/hde1
                      capacity: 111GB
                      capabilities: primary
              *-cdrom
                   description: DVD reader
                   product: HL-DT-STDVD-ROM GDR8161B
                   physical id: 1
                   bus info: ide@2.1
                   logical name: /dev/hdf
                   version: 0100
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdf
           *-ide:1
                description: IDE Channel 1
                physical id: 3
                bus info: ide@3
                logical name: ide3
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-4163B
                   physical id: 0
                   bus info: ide@3.0
                   logical name: /dev/hdg
                   version: A103
                   serial: K2653HC0948
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdg
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:ac00-ac1f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:b000-b01f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: USB hub
                   product: G11 Keyboard
                   vendor: Logitech, Inc.
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.71
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                 *-usb:0
                      description: Keyboard
                      product: Gaming Keyboard
                      vendor: Logitech, Inc.
                      physical id: 1
                      bus info: usb@2:1.1
                      version: 1.90
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
                 *-usb:1
                      description: Human interface device
                      product: G11 Keyboard
                      vendor: Logitech, Inc.
                      physical id: 4
                      bus info: usb@2:1.4
                      version: 1.71
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=12.0MB/s
              *-usb:1
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@2:2
                   version: 27.10
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:b400-b41f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:b800-b81f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e4002000-e40020ff irq:185
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-11-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb:0
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 7
                   bus info: usb@5:7
                   version: 6.0b
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
              *-usb:1
                   description: Mass storage device
                   product: USB Storage
                   vendor: Genesys Logic, Inc.
                   physical id: 8
                   bus info: usb@5:8
                   logical name: scsi0
                   version: 91.44
                   serial: 000000009144
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480.0MB/s
                 *-disk:0
                      description: SCSI Disk
                      product: STORAGE DEVICE
                      vendor: Generic
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 9144
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sda
                 *-disk:1
                      description: SCSI Disk
                      product: STORAGE DEVICE
                      vendor: Generic
                      physical id: 0.0.1
                      bus info: scsi@0:0.0.1
                      logical name: /dev/sdb
                      version: 9144
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdb
                 *-disk:2
                      description: SCSI Disk
                      product: STORAGE DEVICE
                      vendor: Generic
                      physical id: 0.0.2
                      bus info: scsi@0:0.0.2
                      logical name: /dev/sdc
                      version: 9144
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdc
                 *-disk:3
                      description: SCSI Disk
                      product: STORAGE DEVICE
                      vendor: Generic
                      physical id: 0.0.3
                      bus info: scsi@0:0.0.3
                      logical name: /dev/sdd
                      version: 9144
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdd
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:bc00-bcff irq:217
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 78
             serial: 00:11:09:2c:59:e6
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full ip=172.20.0.205 link=yes multicast=yes port
=MII speed=100MB/s
             resources: ioport:c000-c0ff iomemory:e4003000-e40030ff irq:209


---

### Post by pepolez on 2007-05-04
Nevermind, I was able to get the network cards working fine by manually adding them to /etc/iftab . I also found my inability to use the Realtek card was due to a misconfiguration on the other end that resulted in two computers trying to use the same address :x

---

