---
title: "how to configure dwlg510 in ubuntu edgy"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by netkracker on 2006-12-02
I am trying to configure Dlink DWL G510 wireless card (rev c2) in ubuntu edgy. I connected the card, but when i check in Device Manager  it is shown as **unknown device**. I checked under wireless settings, i can see 2 wireless connections there: **wmaster0** and **wlan0**. How do I configure dwl g510. I had tried netgear wg311v3 before moving to dlink dwl g510, but that also didnt work

I am using an AMD64 machine

Thanks

---

### Post by FrodoB on 2006-12-02
Publish the outputs from:

lspci

iwconfig

dmesg

---

### Post by netkracker on 2006-12-02
I have no clue what dmesg is showing

lspci:
> 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
02:00.0 Network controller: RaLink Unknown device 0302
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.


dmesg:
> [17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000017fd0000 (usable)
[17179569.184000]  BIOS-e820: 0000000017fd0000 - 0000000017fde000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000017fde000 - 0000000018000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 383MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 98256
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 94160 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f96e0
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x11000514 MSFT 0x00000097) @ 0x17fd0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x11000514 MSFT 0x00000097) @ 0x17fd0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x11000514 MSFT 0x00000097) @ 0x17fd0390
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x11000514 MSFT 0x00000097) @ 0x17fd03f0
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x11000514 MSFT 0x00000097) @ 0x17fde040
[17179569.184000] ACPI: DSDT (v001  1ABZR 1ABZRB49 0x00000b49 INTL 0x02002026) @ 0x00000000
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:15 APIC version 16
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7780000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1795.154 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.504000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.504000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.508000] Memory: 379624k/393024k available (1910k kernel code, 12812k reserved, 1070k data, 308k init, 0k highmem)
[17179569.508000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.588000] Calibrating delay using timer specific routine.. 3595.32 BogoMIPS (lpj=7190651)
[17179569.588000] Security Framework v1.0.0 initialized
[17179569.588000] SELinux:  Disabled at boot.
[17179569.588000] Mount-cache hash table entries: 512
[17179569.588000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179569.588000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179569.588000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.588000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.588000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179569.588000] Checking 'hlt' instruction... OK.
[17179569.604000] SMP alternatives: switching to UP code
[17179569.604000] Freeing SMP alternatives: 16k freed
[17179569.604000] checking if image is initramfs... it is
[17179570.112000] Freeing initrd memory: 5563k freed
[17179570.112000] ACPI: Core revision 20060707
[17179570.116000] ACPI: Looking for DSDT ... not found!
[17179570.116000] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 02
[17179570.116000] Total of 1 processors activated (3595.32 BogoMIPS).
[17179570.116000] ENABLING IO-APIC IRQs
[17179570.116000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.116000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179570.116000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[17179570.116000] ...trying to set up timer as Virtual Wire IRQ... works.
[17179570.300000] Brought up 1 CPUs
[17179570.300000] migration_cost=0
[17179570.300000] NET: Registered protocol family 16
[17179570.300000] EISA bus registered
[17179570.300000] ACPI: bus type pci registered
[17179570.300000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179570.300000] PCI: Not using MMCONFIG.
[17179570.300000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[17179570.300000] PCI: Using configuration type 1
[17179570.300000] Setting up standard PCI resources
[17179570.308000] ACPI: Interpreter enabled
[17179570.308000] ACPI: Using IOAPIC for interrupt routing
[17179570.308000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.308000] PCI: Probing PCI hardware (bus 00)
[17179570.312000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179570.312000] Boot video device is 0000:01:05.0
[17179570.312000] PCI: Transparent bridge - 0000:00:14.4
[17179570.312000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.320000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179570.324000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[17179570.328000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.328000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.328000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.328000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.328000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.328000] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[17179570.328000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.328000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.328000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.328000] pnp: PnP ACPI init
[17179570.332000] pnp: PnP ACPI: found 15 devices
[17179570.332000] PnPBIOS: Disabled by ACPI PNP
[17179570.332000] PCI: Using ACPI for IRQ routing
[17179570.332000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.340000] pnp: 00:0c: ioport range 0x600-0x60f has been reserved
[17179570.340000] PCI: Bridge: 0000:00:01.0
[17179570.340000]   IO window: d000-dfff
[17179570.340000]   MEM window: fea00000-feafffff
[17179570.340000]   PREFETCH window: d0000000-dfffffff
[17179570.340000] PCI: Bridge: 0000:00:14.4
[17179570.340000]   IO window: e000-efff
[17179570.340000]   MEM window: feb00000-febfffff
[17179570.340000]   PREFETCH window: 20000000-200fffff
[17179570.344000] NET: Registered protocol family 2
[17179570.380000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.380000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.380000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.380000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.380000] TCP reno registered
[17179570.380000] audit: initializing netlink socket (disabled)
[17179570.380000] audit(1165071314.380:1): initialized
[17179570.380000] VFS: Disk quotas dquot_6.5.1
[17179570.380000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.380000] Initializing Cryptographic API
[17179570.380000] io scheduler noop registered
[17179570.380000] io scheduler anticipatory registered
[17179570.380000] io scheduler deadline registered
[17179570.380000] io scheduler cfq registered (default)
[17179570.380000] isapnp: Scanning for PnP cards...
[17179570.732000] isapnp: No Plug & Play device found
[17179570.752000] Real Time Clock Driver v1.12ac
[17179570.752000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.752000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.752000] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.752000] mice: PS/2 mouse device common for all mice
[17179570.752000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.756000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.756000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.756000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179570.756000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.756000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.756000] EISA: Probing bus 0 at eisa.0
[17179570.756000] Cannot allocate resource for EISA slot 8
[17179570.756000] EISA: Detected 0 cards.
[17179570.756000] TCP bic registered
[17179570.756000] NET: Registered protocol family 1
[17179570.756000] NET: Registered protocol family 8
[17179570.756000] NET: Registered protocol family 20
[17179570.756000] Using IPI No-Shortcut mode
[17179570.756000] ACPI: (supports S0 S1 S3 S4 S5)
[17179570.756000] Freeing unused kernel memory: 308k freed
[17179570.780000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.884000] Capability LSM initialized
[17179571.912000] ACPI: duty_cycle spans bit 4
[17179571.912000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179571.912000] ACPI: Getting cpuindex for acpiid 0x2
[17179572.212000] SCSI subsystem initialized
[17179572.216000] libata version 1.20 loaded.
[17179572.216000] sata_sil 0000:00:11.0: version 0.9
[17179572.216000] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179572.216000] ata1: SATA max UDMA/100 cmd 0xD8834C80 ctl 0xD8834C8A bmdma 0xD8834C00 irq 177
[17179572.216000] ata2: SATA max UDMA/100 cmd 0xD8834CC0 ctl 0xD8834CCA bmdma 0xD8834C08 irq 177
[17179572.420000] ata1: SATA link down (SStatus 0)
[17179572.420000] scsi0 : sata_sil
[17179572.628000] ata2: SATA link down (SStatus 0)
[17179572.628000] scsi1 : sata_sil
[17179572.632000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 185
[17179572.632000] ata3: SATA max UDMA/100 cmd 0xD8836880 ctl 0xD883688A bmdma 0xD8836800 irq 185
[17179572.632000] ata4: SATA max UDMA/100 cmd 0xD88368C0 ctl 0xD88368CA bmdma 0xD8836808 irq 185
[17179572.992000] ata3: SATA link up 1.5 Gbps (SStatus 113)
[17179573.008000] ata3: dev 0 cfg 49:2f00 82:7469 83:7f01 84:4023 85:7469 86:3c01 87:4023 88:407f
[17179573.008000] ata3: dev 0 ATA-7, max UDMA/133, 156301488 sectors: LBA48
[17179573.020000] ata3: dev 0 configured for UDMA/100
[17179573.020000] scsi2 : sata_sil
[17179573.224000] ata4: SATA link down (SStatus 0)
[17179573.224000] scsi3 : sata_sil
[17179573.228000]   Vendor: ATA       Model: WDC WD800BD-22LR  Rev: 06.0
[17179573.228000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179573.232000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179573.232000] sda: Write Protect is off
[17179573.232000] sda: Mode Sense: 00 3a 00 00
[17179573.232000] SCSI device sda: drive cache: write back
[17179573.232000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179573.232000] sda: Write Protect is off
[17179573.232000] sda: Mode Sense: 00 3a 00 00
[17179573.232000] SCSI device sda: drive cache: write back
[17179573.232000]  sda: sda1 sda2 sda3
[17179573.272000] sd 2:0:0:0: Attached scsi disk sda
[17179573.608000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179573.608000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 193
[17179573.608000] ATIIXP: chipset revision 128
[17179573.608000] ATIIXP: not 100% native mode: will probe irqs later
[17179573.608000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:pio
[17179573.608000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[17179573.608000] Probing IDE interface ide0...
[17179574.176000] Probing IDE interface ide1...
[17179574.920000] hdc: TSSTcorp CDW/DVD SH-M522C, ATAPI CD/DVD-ROM drive
[17179575.596000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.600000] hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[17179575.600000] Uniform CD-ROM driver Revision: 3.20
[17179575.644000] Probing IDE interface ide0...
[17179575.704000] usbcore: registered new driver usbfs
[17179575.708000] usbcore: registered new driver hub
[17179575.708000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179575.708000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179575.708000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179575.708000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179575.708000] ohci_hcd 0000:00:13.0: irq 201, io mem 0xfe9fa000
[17179575.768000] usb usb1: configuration #1 chosen from 1 choice
[17179575.768000] hub 1-0:1.0: USB hub found
[17179575.768000] hub 1-0:1.0: 4 ports detected
[17179575.872000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 201
[17179575.872000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179575.872000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179575.872000] ohci_hcd 0000:00:13.1: irq 201, io mem 0xfe9f9000
[17179575.932000] usb usb2: configuration #1 chosen from 1 choice
[17179575.932000] hub 2-0:1.0: USB hub found
[17179575.932000] hub 2-0:1.0: 4 ports detected
[17179576.040000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 201
[17179576.040000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179576.040000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[17179576.040000] ehci_hcd 0000:00:13.2: irq 201, io mem 0xfe9f8000
[17179576.040000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.040000] usb usb3: configuration #1 chosen from 1 choice
[17179576.040000] hub 3-0:1.0: USB hub found
[17179576.040000] hub 3-0:1.0: 8 ports detected
[17179576.288000] Attempting manual resume
[17179576.296000] APIC error on CPU0: 00(40)
[17179576.308000] kjournald starting.  Commit interval 5 seconds
[17179576.308000] EXT3-fs: mounted filesystem with ordered data mode.
[17179584.428000] input: PC Speaker as /class/input/input1
[17179584.788000] Floppy drive(s): fd0 is 1.44M
[17179584.800000] Linux agpgart interface v0.101 (c) Dave Jones
[17179584.824000] FDC 0 is a post-1991 82077
[17179584.852000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179584.856000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.200000] parport: PnPBIOS parport detected.
[17179585.200000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179585.324000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17179585.324000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 209
[17179585.324000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17179585.324000] eth0: RTL8169 at 0xd8860c00, 00:13:d3:d4:3e:a4, IRQ 209
[17179585.536000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17179585.632000] Loading module: rt61pci - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[17179585.632000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 209
[17179585.680000] r8169: eth0: link down
[17179585.684000] wmaster0: Selected rate control algorithm 'simple'
[17179585.840000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 193
[17179586.176000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[17179586.552000] lp0: using parport0 (interrupt-driven).
[17179586.576000] Adding 5124724k swap on /dev/disk/by-uuid/f143ddb6-8aa4-4295-a7da-07061797c14f.  Priority:-1 extents:1 across:5124724k
[17179586.668000] EXT3 FS on sda1, internal journal
[17179586.688000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179586.744000] ts: Compaq touchscreen protocol output
[17179586.764000] NET: Registered protocol family 17
[17179586.968000] r8169: eth0: link up
[17179587.004000] kjournald starting.  Commit interval 5 seconds
[17179587.012000] EXT3 FS on sda2, internal journal
[17179587.012000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.364000] ACPI: Power Button (FF) [PWRF]
[17179591.364000] ACPI: Power Button (CM) [PWRB]
[17179591.484000] ibm_acpi: ec object not found
[17179591.508000] pcc_acpi: loading...
[17179591.856000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179591.864000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[17179594.724000] NET: Registered protocol family 10
[17179594.724000] lo: Disabled Privacy Extensions
[17179594.728000] IPv6 over IPv4 tunneling driver
[17179597.352000] hda-intel: Invalid position buffer, using LPIB read method instead.
[17179597.364000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179597.364000] apm: overridden by ACPI.
[17179601.180000] Bluetooth: Core ver 2.8
[17179601.180000] NET: Registered protocol family 31
[17179601.180000] Bluetooth: HCI device and connection manager initialized
[17179601.180000] Bluetooth: HCI socket layer initialized
[17179601.192000] Bluetooth: L2CAP ver 2.8
[17179601.192000] Bluetooth: L2CAP socket layer initialized
[17179601.208000] Bluetooth: RFCOMM socket layer initialized
[17179601.208000] Bluetooth: RFCOMM TTY layer initialized
[17179601.208000] Bluetooth: RFCOMM ver 1.7
[17179617.120000] eth0: no IPv6 routers present
[17179809.176000] APIC error on CPU0: 40(40)
[17180137.084000] APIC error on CPU0: 40(40)
[17181124.348000] wlan0: no IPv6 routers present
[17181229.500000] r8169: eth0: link up
[17181240.472000] eth0: no IPv6 routers present
[17181250.336000] wlan0: no IPv6 routers present
[17181308.172000] APIC error on CPU0: 40(40)
[17181369.188000] wlan0: no IPv6 routers present
[17181404.792000] APIC error on CPU0: 40(40)
[17181425.376000] eth0: no IPv6 routers present
[17181439.212000] APIC error on CPU0: 40(40)
[17181501.424000] APIC error on CPU0: 40(40)



---

### Post by FrodoB on 2006-12-02
So what sort of Access Point setup do you have.  Is it using WEP for security?

---

### Post by netkracker on 2006-12-02
Yes. its WEP. will disabling it help?

---

### Post by FrodoB on 2006-12-02
It would not hurt, but not necessary. I just wanted to know if you were trying to use some form of WPA perhaps.

You need to put a record like this in /etc/network/interfaces:

iface wlan0 inet dhcp
wireless-essid Your_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

This example assumes that you are using a 128bit Hex WEP key of 26 characters. For entering ASCII prepend the key with s: and then 13 ASCII characters.

Then you can control it with the ifdown and ifup commands.

---

