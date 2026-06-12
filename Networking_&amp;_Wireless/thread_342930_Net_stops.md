---
title: "Net stops"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by Ashton K. on 2007-01-20
For some reason, when I'm downloading something relatively large (like say, the Kernel source for another machine that doesn't have internet yet), firefox eventually stops the download, about halfway through. After which, the internet doesn't work for anything. And attempts to restart the card interfaces through the System>Administration>Networking panel freezes the computer outright. Any clue to why this is? (I use a Netgear WG311T card that works fine off of the madwifi drivers that come in the Linux-Restricted-Modules repository).

---

### Post by Ashton K. on 2007-01-21
I removed the Linux-Restricted-Modules (to ensure I'm not using the stock wireless drivers that came with Edgy), and recompiled madwifi-ng. Sadly, I'm still experiencing the same thing, however only when using Firefox to download something. Is it the driver, or is it an instability in Firefox?

Here's the output of lspci: 
```
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation M5263 Ethernet Controller (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:05.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:07.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

And here's dmesg:

```
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffd0000 (usable)
[17179569.184000]  BIOS-e820: 000000003ffd0000 - 000000003ffdf000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffdf000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 262096
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32720 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fa7f0
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x12000505 MSFT 0x00000097) @ 0x3ffd0000
[17179569.184000] ACPI: FADT (v001 A M I  OEMFACP  0x12000505 MSFT 0x00000097) @ 0x3ffd0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x12000505 MSFT 0x00000097) @ 0x3ffd0390
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x12000505 MSFT 0x00000097) @ 0x3ffdf040
[17179569.184000] ACPI: DSDT (v001  A0158 A0158000 0x00000000 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda4 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1600.131 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.872000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.872000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.892000] Memory: 1029524k/1048384k available (1910k kernel code, 18096k reserved, 1069k data, 308k init, 130880k highmem)
[17179572.892000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.972000] Calibrating delay using timer specific routine.. 3202.41 BogoMIPS (lpj=6404836)
[17179572.972000] Security Framework v1.0.0 initialized
[17179572.972000] SELinux:  Disabled at boot.
[17179572.972000] Mount-cache hash table entries: 512
[17179572.972000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179572.972000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179572.972000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.972000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.972000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179572.972000] Checking 'hlt' instruction... OK.
[17179572.988000] SMP alternatives: switching to UP code
[17179572.988000] Freeing SMP alternatives: 16k freed
[17179572.988000] checking if image is initramfs... it is
[17179573.540000] Freeing initrd memory: 5323k freed
[17179573.540000] ACPI: Core revision 20060707
[17179573.540000] ACPI: Looking for DSDT ... not found!
[17179573.540000] CPU0: AMD Sempron(tm) Processor 2800+ stepping 02
[17179573.540000] Total of 1 processors activated (3202.41 BogoMIPS).
[17179573.540000] ENABLING IO-APIC IRQs
[17179573.544000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.684000] Brought up 1 CPUs
[17179573.684000] migration_cost=0
[17179573.684000] NET: Registered protocol family 16
[17179573.684000] EISA bus registered
[17179573.684000] ACPI: bus type pci registered
[17179573.684000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[17179573.684000] PCI: Using configuration type 1
[17179573.684000] Setting up standard PCI resources
[17179573.692000] ACPI: Interpreter enabled
[17179573.692000] ACPI: Using IOAPIC for interrupt routing
[17179573.692000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.692000] PCI: Probing PCI hardware (bus 00)
[17179573.696000] PCI quirk: region 0800-083f claimed by ali7101 ACPI
[17179573.696000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0e.0
[17179573.696000] Boot video device is 0000:01:00.0
[17179573.696000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.708000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179573.708000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HTT_._PRT]
[17179573.716000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.716000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[17179573.716000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.716000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.716000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.716000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.716000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.716000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[17179573.716000] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.716000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.716000] pnp: PnP ACPI init
[17179573.724000] pnp: PnP ACPI: found 14 devices
[17179573.724000] PnPBIOS: Disabled by ACPI PNP
[17179573.724000] PCI: Using ACPI for IRQ routing
[17179573.724000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.736000] pnp: 00:0a: ioport range 0xc00-0xc0f has been reserved
[17179573.736000] pnp: 00:0a: ioport range 0xd00-0xd0f has been reserved
[17179573.736000] pnp: 00:0a: ioport range 0xa20-0xa2f has been reserved
[17179573.736000] pnp: 00:0a: ioport range 0xa30-0xa3f has been reserved
[17179573.736000] PCI: Bridge: 0000:00:01.0
[17179573.736000]   IO window: d000-dfff
[17179573.736000]   MEM window: fa000000-fbefffff
[17179573.736000]   PREFETCH window: e0000000-f8ffffff
[17179573.736000] PCI: Bridge: 0000:00:02.0
[17179573.736000]   IO window: e000-efff
[17179573.736000]   MEM window: fbf00000-fbffffff
[17179573.736000]   PREFETCH window: disabled.
[17179573.736000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.736000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179573.736000] NET: Registered protocol family 2
[17179573.776000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.776000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179573.776000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179573.776000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.776000] TCP reno registered
[17179573.776000] audit: initializing netlink socket (disabled)
[17179573.776000] audit(1169396088.776:1): initialized
[17179573.776000] highmem bounce pool size: 64 pages
[17179573.776000] VFS: Disk quotas dquot_6.5.1
[17179573.776000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.776000] Initializing Cryptographic API
[17179573.776000] io scheduler noop registered
[17179573.776000] io scheduler anticipatory registered
[17179573.776000] io scheduler deadline registered
[17179573.776000] io scheduler cfq registered (default)
[17179581.784000] 0000:00:0f.3 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[17179581.788000] isapnp: Scanning for PnP cards...
[17179582.140000] isapnp: No Plug & Play device found
[17179582.160000] Real Time Clock Driver v1.12ac
[17179582.160000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179582.160000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179582.160000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179582.160000] mice: PS/2 mouse device common for all mice
[17179582.160000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179582.160000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179582.160000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179582.160000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179582.164000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179582.164000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179582.164000] EISA: Probing bus 0 at eisa.0
[17179582.164000] EISA: Detected 0 cards.
[17179582.164000] TCP bic registered
[17179582.164000] NET: Registered protocol family 1
[17179582.164000] NET: Registered protocol family 8
[17179582.164000] NET: Registered protocol family 20
[17179582.164000] Using IPI No-Shortcut mode
[17179582.164000] ACPI: (supports S0 S1 S3 S4 S5)
[17179582.164000] Freeing unused kernel memory: 308k freed
[17179582.252000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179583.308000] Capability LSM initialized
[17179583.856000] ALI15X3: IDE controller at PCI slot 0000:00:0e.0
[17179583.856000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179583.856000] ALI15X3: chipset revision 199
[17179583.856000] ALI15X3: not 100% native mode: will probe irqs later
[17179583.856000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[17179583.856000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[17179583.856000] Probing IDE interface ide0...
[17179584.144000] hda: WDC WD1600JB-00REA0, ATA DISK drive
[17179584.424000] hdb: WDC WD1600JB-00REA0, ATA DISK drive
[17179584.480000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179584.484000] Probing IDE interface ide1...
[17179585.220000] hdc: Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive
[17179585.892000] ide1 at 0x170-0x177,0x376 on irq 15
[17179585.904000] hda: max request size: 512KiB
[17179585.916000] hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[17179585.916000] hda: cache flushes supported
[17179585.916000]  hda: hda1 hda2 hda3 hda4
[17179585.936000] hdb: max request size: 512KiB
[17179585.948000] hdb: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[17179585.948000] hdb: cache flushes supported
[17179585.948000]  hdb:
[17179585.972000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179585.972000] Uniform CD-ROM driver Revision: 3.20
[17179586.272000] SCSI subsystem initialized
[17179586.276000] libata version 1.20 loaded.
[17179586.276000] sata_uli 0000:00:0e.1: version 0.5
[17179586.276000] ACPI: PCI Interrupt 0000:00:0e.1[A] -> GSI 19 (level, low) -> IRQ 169
[17179586.276000] ata1: SATA max UDMA/133 cmd 0xCC00 ctl 0xC082 bmdma 0xB880 irq 169
[17179586.276000] ata2: SATA max UDMA/133 cmd 0xC000 ctl 0xBC02 bmdma 0xB888 irq 169
[17179586.480000] ata1: SATA link down (SStatus 0)
[17179586.480000] scsi0 : sata_uli
[17179586.688000] ata2: SATA link down (SStatus 0)
[17179586.688000] scsi1 : sata_uli
[17179586.760000] usbcore: registered new driver usbfs
[17179586.760000] usbcore: registered new driver hub
[17179586.764000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179586.764000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179586.764000] ohci_hcd 0000:00:0f.0: OHCI Host Controller
[17179586.764000] ohci_hcd 0000:00:0f.0: new USB bus registered, assigned bus number 1
[17179587.224000] ohci_hcd 0000:00:0f.0: irq 177, io mem 0xf9ff3000
[17179587.284000] usb usb1: configuration #1 chosen from 1 choice
[17179587.284000] hub 1-0:1.0: USB hub found
[17179587.284000] hub 1-0:1.0: 3 ports detected
[17179587.388000] ACPI: PCI Interrupt 0000:00:0f.1[B] -> GSI 21 (level, low) -> IRQ 185
[17179587.388000] ohci_hcd 0000:00:0f.1: OHCI Host Controller
[17179587.388000] ohci_hcd 0000:00:0f.1: new USB bus registered, assigned bus number 2
[17179587.404000] ohci_hcd 0000:00:0f.1: irq 185, io mem 0xf9ffc000
[17179587.464000] usb usb2: configuration #1 chosen from 1 choice
[17179587.464000] hub 2-0:1.0: USB hub found
[17179587.464000] hub 2-0:1.0: 3 ports detected
[17179587.568000] ACPI: PCI Interrupt 0000:00:0f.2[C] -> GSI 22 (level, low) -> IRQ 193
[17179587.568000] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[17179587.568000] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 3
[17179587.584000] ohci_hcd 0000:00:0f.2: irq 193, io mem 0xf9ffd000
[17179587.644000] usb usb3: configuration #1 chosen from 1 choice
[17179587.644000] hub 3-0:1.0: USB hub found
[17179587.644000] hub 3-0:1.0: 3 ports detected
[17179587.692000] usb 1-3: new full speed USB device using ohci_hcd and address 2
[17179587.748000] ACPI: PCI Interrupt 0000:00:0f.3[D] -> GSI 23 (level, low) -> IRQ 201
[17179587.748000] ehci_hcd 0000:00:0f.3: EHCI Host Controller
[17179587.748000] ehci_hcd 0000:00:0f.3: new USB bus registered, assigned bus number 4
[17179587.748000] ehci_hcd 0000:00:0f.3: debug port 1
[17179587.772000] ehci_hcd 0000:00:0f.3: irq 201, io mem 0xf9ffe800
[17179587.772000] ehci_hcd 0000:00:0f.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179587.772000] usb usb4: configuration #1 chosen from 1 choice
[17179587.772000] hub 4-0:1.0: USB hub found
[17179587.772000] hub 4-0:1.0: 8 ports detected
[17179587.992000] Attempting manual resume
[17179588.000000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179588.000000] EXT3-fs: write access will be enabled during recovery.
[17179588.424000] kjournald starting.  Commit interval 5 seconds
[17179588.424000] EXT3-fs: recovery complete.
[17179588.424000] EXT3-fs: mounted filesystem with ordered data mode.
[17179588.448000] usb 1-3: new full speed USB device using ohci_hcd and address 3
[17179588.692000] usb 1-3: configuration #1 chosen from 1 choice
[17179594.868000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179594.872000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179594.884000] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
[17179594.884000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 209
[17179594.904000] eth0: ULi M5263 at pci0000:00:0d.0, 00:15:f2:c1:87:4f, irq 209.
[17179594.932000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.932000] agpgart: Detected AGP bridge 0
[17179594.932000] Setting up ULi AGP.
[17179594.940000] agpgart: AGP aperture is 256M @ 0xd0000000
[17179595.004000] parport: PnPBIOS parport detected.
[17179595.004000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179595.056000] input: PC Speaker as /class/input/input1
[17179595.516000] ali15x3_smbus 0000:00:03.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[17179595.516000] ali15x3_smbus 0000:00:03.1: ALI15X3 not detected, module not inserted.
[17179595.524000] ali1535_smbus 0000:00:03.1: ALI1535_smb region uninitialized - upgrade BIOS?
[17179595.524000] ali1535_smbus 0000:00:03.1: ALI1535 not detected, module not inserted.
[17179595.592000] ali1563: SMBus control = 0403
[17179595.592000] ali1563_probe: Returning 0
[17179595.992000] Linux Tulip driver version 1.1.14 (May 6, 2006)
[17179595.992000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 17 (level, low) -> IRQ 209
[17179595.992000] tulip0:  MII transceiver #1 config 3100 status 7849 advertising 05e1.
[17179595.992000] tulip0:  MII transceiver #2 config 1000 status 7849 advertising 05e1.
[17179595.992000] tulip0:  MII transceiver #3 config 1000 status 7849 advertising 05e1.
[17179595.996000] tulip0:  MII transceiver #4 config 1000 status 7849 advertising 05e1.
[17179595.996000] eth1: ADMtek Comet rev 17 at Port 0xe800, 00:50:BF:FE:D1:F9, IRQ 209.
[17179596.044000] Floppy drive(s): fd0 is 1.44M
[17179596.072000] FDC 0 is a post-1991 82077
[17179596.180000] ath_hal: module license 'Proprietary' taints kernel.
[17179596.180000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179596.196000] wlan: 0.8.4.2 (svn r1982)
[17179596.208000] ath_pci: 0.9.4.5 (svn r1982)
[17179596.208000] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179596.764000] usbcore: registered new driver libusual
[17179596.844000] Initializing USB Mass Storage driver...
[17179596.844000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179596.908000] usbcore: registered new driver usb-storage
[17179596.908000] USB Mass Storage support registered.
[17179596.908000] usb-storage: device found at 3
[17179596.908000] usb-storage: waiting for device to settle before scanning
[17179596.992000] ath_rate_sample: 1.2 (svn r1982)
[17179597.028000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179597.032000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179597.032000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179597.032000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17179597.032000] wifi0: mac 7.9 phy 4.5 radio 5.6
[17179597.032000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17179597.032000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17179597.032000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17179597.032000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17179597.032000] wifi0: Use hw queue 8 for CAB traffic
[17179597.032000] wifi0: Use hw queue 9 for beacons
[17179597.040000] wifi0: Atheros 5212: mem=0xfbfe0000, irq=177
[17179597.040000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 18 (level, low) -> IRQ 217
[17179597.148000] AC'97 0 analog subsections not ready
[17179597.216000] intel8x0_measure_ac97_clock: measured 58634 usecs
[17179597.216000] intel8x0: clocking to 48000
[17179597.344000] lp0: using parport0 (interrupt-driven).
[17179597.368000] ppa: Version 2.07 (for Linux 2.4.x)
[17179597.520000] Adding 2096472k swap on /dev/disk/by-uuid/2981783e-5585-4e9f-912f-1ddb0a29d82c.  Priority:-1 extents:1 across:2096472k
[17179597.544000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179597.576000] ts: Compaq touchscreen protocol output
[17179597.732000] EXT3 FS on hda4, internal journal
[17179598.096000] kjournald starting.  Commit interval 5 seconds
[17179598.104000] EXT3 FS on hda1, internal journal
[17179598.104000] EXT3-fs: mounted filesystem with ordered data mode.
[17179598.108000] kjournald starting.  Commit interval 5 seconds
[17179598.116000] EXT3 FS on hda3, internal journal
[17179598.116000] EXT3-fs: mounted filesystem with ordered data mode.
[17179598.196000] NET: Registered protocol family 17
[17179601.912000] usb-storage: device scan complete
[17179601.924000]   Vendor: IOMEGA    Model: ZIP 250           Rev: 79.U
[17179601.924000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179601.996000] sda: Spinning up disk...<6>ACPI: Power Button (FF) [PWRF]
[17179602.484000] ACPI: Power Button (CM) [PWRB]
[17179602.616000] ibm_acpi: ec object not found
[17179602.652000] pcc_acpi: loading...
[17179603.004000] powernow-k8: Power state transitions not supported
[17179603.004000] .<5>sd 2:0:0:0: Attached scsi removable disk sda
[17179603.060000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17179604.348000] NET: Registered protocol family 10
[17179604.348000] lo: Disabled Privacy Extensions
[17179604.348000] IPv6 over IPv4 tunneling driver
[17179605.272000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179605.272000] apm: overridden by ACPI.
[17179609.956000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[17179610.052000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179610.056000] NFSD: starting 90-second grace period
[17179610.888000] Bluetooth: Core ver 2.8
[17179610.888000] NET: Registered protocol family 31
[17179610.888000] Bluetooth: HCI device and connection manager initialized
[17179610.888000] Bluetooth: HCI socket layer initialized
[17179610.908000] Bluetooth: L2CAP ver 2.8
[17179610.908000] Bluetooth: L2CAP socket layer initialized
[17179610.940000] Bluetooth: RFCOMM socket layer initialized
[17179610.940000] Bluetooth: RFCOMM TTY layer initialized
[17179610.940000] Bluetooth: RFCOMM ver 1.7
[17179615.276000] ath0: no IPv6 routers present

```

---

