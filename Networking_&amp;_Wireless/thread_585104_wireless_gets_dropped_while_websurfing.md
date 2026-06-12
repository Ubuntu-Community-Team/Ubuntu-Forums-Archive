---
title: "wireless gets dropped while websurfing"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by okst666 on 2007-10-21
every time I am going to surf on that website ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) my wireless drops

I not even need to reboot to get it back on working,I have to shut the computer down or at least unplug that usb-thingy and plug it in again...
If I forget to unplug it or just reboot, this usb-thingy gets EXTREMLY hot.

thats the lsusb-output
```

Bus 005 Device 004: ID 148f:2573 Ralink Technology, Corp. 

```

and here comes demesg...

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
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
[    0.000000] ACPI: RSDP signature @ 0xC00FEB90 checksum 0
[    0.000000] ACPI: RSDP 000FEB90, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD1C9, 0034 (r1 DELL    8300           6 ASL        61)
[    0.000000] ACPI: FACP 000FD1FD, 0074 (r1 DELL    8300           6 ASL        61)
[    0.000000] ACPI: DSDT FFFC614C, 2426 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 3FF74000, 0040
[    0.000000] ACPI: SSDT FFFC8572, 00A7 (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FD271, 006C (r1 DELL    8300           6 ASL        61)
[    0.000000] ACPI: BOOT 000FD2DD, 0028 (r1 DELL    8300           6 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Built 1 zonelists.  Total pages: 259958
[    0.000000] Kernel command line: root=UUID=7de7ba65-4f41-4adc-8796-3d33defbc06a ro quiet splash locale=de_DE
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2593.753 MHz processor.
[    9.954503] Console: colour VGA+ 80x25
[    9.955110] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.955693] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.985583] Memory: 1027148k/1048016k available (2015k kernel code, 20216k reserved, 916k data, 364k init, 130512k highmem)
[    9.985595] virtual kernel memory layout:
[    9.985596]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    9.985597]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.985598]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    9.985599]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    9.985600]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    9.985601]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    9.985602]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    9.985605] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.985653] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.065515] Calibrating delay using timer specific routine.. 5191.37 BogoMIPS (lpj=10382757)
[   10.065550] Security Framework v1.0.0 initialized
[   10.065560] SELinux:  Disabled at boot.
[   10.065574] Mount-cache hash table entries: 512
[   10.065760] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   10.065774] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   10.065777] CPU: L2 cache: 512K
[   10.065779] CPU: Hyper-Threading is disabled
[   10.065782] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   10.065795] Compat vDSO mapped to ffffe000.
[   10.065811] Checking 'hlt' instruction... OK.
[   10.081621] SMP alternatives: switching to UP code
[   10.081887] Freeing SMP alternatives: 11k freed
[   10.082178] Early unpacking initramfs... done
[   10.400515] ACPI: Core revision 20070126
[   10.412250] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.435334] CPU0: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09
[   10.435376] Total of 1 processors activated (5191.37 BogoMIPS).
[   10.435505] ENABLING IO-APIC IRQs
[   10.435692] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.580514] Brought up 1 CPUs
[   10.580641] Booting paravirtualized kernel on bare hardware
[   10.580710] Time: 15:09:42  Date: 09/21/107
[   10.580734] NET: Registered protocol family 16
[   10.580830] EISA bus registered
[   10.580845] ACPI: bus type pci registered
[   10.581662] PCI: PCI BIOS revision 2.10 entry at 0xfbb38, last bus=2
[   10.581664] PCI: Using configuration type 1
[   10.581666] Setting up standard PCI resources
[   10.588819] ACPI: EC: Look up EC in DSDT
[   10.615274] ACPI: Interpreter enabled
[   10.615278] ACPI: (supports S0 S1 S3 S4 S5)
[   10.615303] ACPI: Using IOAPIC for interrupt routing
[   10.637821] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.637839] PCI: Probing PCI hardware (bus 00)
[   10.638294] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   10.638298] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   10.638737] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   10.638801] PCI: Transparent bridge - 0000:00:1e.0
[   10.638828] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.639259] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   10.746149] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   10.746460] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   10.746767] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   10.747075] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   10.747382] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[   10.747687] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   10.747993] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   10.748307] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 15)
[   10.748441] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.748458] pnp: PnP ACPI init
[   10.748467] ACPI: bus type pnp registered
[   10.764154] pnp: PnP ACPI: found 8 devices
[   10.764157] ACPI: ACPI bus type pnp unregistered
[   10.764162] PnPBIOS: Disabled by ACPI PNP
[   10.764217] PCI: Using ACPI for IRQ routing
[   10.764220] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.771441] NET: Registered protocol family 8
[   10.771443] NET: Registered protocol family 20
[   10.771514] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   10.771517] pnp: 00:00: iomem range 0x100000-0xffffff could not be reserved
[   10.771520] pnp: 00:00: iomem range 0x1000000-0x3ff73fff could not be reserved
[   10.771523] pnp: 00:00: iomem range 0xc0000-0xfffff could not be reserved
[   10.771533] pnp: 00:07: ioport range 0x800-0x85f has been reserved
[   10.771536] pnp: 00:07: ioport range 0xc00-0xc7f has been reserved
[   10.771539] pnp: 00:07: ioport range 0x860-0x8ff could not be reserved
[   10.772082] Time: tsc clocksource has been installed.
[   10.801818] PCI: Bridge: 0000:00:01.0
[   10.801821]   IO window: d000-dfff
[   10.801827]   MEM window: fe900000-feafffff
[   10.801831]   PREFETCH window: e8000000-f7ffffff
[   10.801835] PCI: Bridge: 0000:00:1e.0
[   10.801838]   IO window: c000-cfff
[   10.801844]   MEM window: fe800000-fe8fffff
[   10.801847]   PREFETCH window: disabled.
[   10.801864] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.801877] NET: Registered protocol family 2
[   10.839990] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.840147] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   10.841560] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.842095] TCP: Hash tables configured (established 131072 bind 65536)
[   10.842102] TCP reno registered
[   10.852108] checking if image is initramfs... it is
[   11.303011] Switched to high resolution mode on CPU 0
[   11.477115] Freeing initrd memory: 7347k freed
[   11.477256] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   11.477259] Simple Boot Flag at 0x7a set to 0x1
[   11.477517] audit: initializing netlink socket (disabled)
[   11.477534] audit(1192979382.184:1): initialized
[   11.477626] highmem bounce pool size: 64 pages
[   11.479777] VFS: Disk quotas dquot_6.5.1
[   11.479839] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.479940] io scheduler noop registered
[   11.479943] io scheduler anticipatory registered
[   11.479945] io scheduler deadline registered
[   11.479962] io scheduler cfq registered (default)
[   11.480044] Boot video device is 0000:01:00.0
[   11.480218] isapnp: Scanning for PnP cards...
[   11.833454] isapnp: No Plug & Play device found
[   11.863184] Real Time Clock Driver v1.12ac
[   11.863269] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.864580] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.864803] input: Macintosh mouse button emulation as /class/input/input0
[   11.864886] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
[   11.864889] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   11.868420] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.868427] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.868641] mice: PS/2 mouse device common for all mice
[   11.868764] EISA: Probing bus 0 at eisa.0
[   11.868803] EISA: Detected 0 cards.
[   11.868912] TCP cubic registered
[   11.868925] NET: Registered protocol family 1
[   11.868949] Using IPI No-Shortcut mode
[   11.869127]   Magic number: 11:808:184
[   11.869704] Freeing unused kernel memory: 364k freed
[   11.913778] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.100744] AppArmor: AppArmor initialized<5>audit(1192979383.684:2):  type=1505 info="AppArmor initialized" pid=1158
[   13.108142] fuse init (API version 7.8)
[   13.113611] Failure registering capabilities with primary security module.
[   13.133393] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   13.749944] usbcore: registered new interface driver usbfs
[   13.749975] usbcore: registered new interface driver hub
[   13.749999] usbcore: registered new device driver usb
[   13.750949] USB Universal Host Controller Interface driver v3.0
[   13.751022] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.751035] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.751039] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.751203] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.751231] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[   13.751369] usb usb1: configuration #1 chosen from 1 choice
[   13.751398] hub 1-0:1.0: USB hub found
[   13.751405] hub 1-0:1.0: 2 ports detected
[   13.853851] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   13.853866] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.853870] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.853895] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.853922] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[   13.854026] usb usb2: configuration #1 chosen from 1 choice
[   13.854054] hub 2-0:1.0: USB hub found
[   13.854062] hub 2-0:1.0: 2 ports detected
[   13.862109] SCSI subsystem initialized
[   13.867773] libata version 2.21 loaded.
[   13.893509] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   13.893513] e100: Copyright(c) 1999-2006 Intel Corporation
[   13.957632] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   13.957646] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.957650] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.957681] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.957709] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[   13.957817] usb usb3: configuration #1 chosen from 1 choice
[   13.957848] hub 3-0:1.0: USB hub found
[   13.957857] hub 3-0:1.0: 2 ports detected
[   14.061378] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   14.061391] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   14.061395] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   14.061422] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   14.061446] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[   14.061555] usb usb4: configuration #1 chosen from 1 choice
[   14.061589] hub 4-0:1.0: USB hub found
[   14.061598] hub 4-0:1.0: 2 ports detected
[   14.093195] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   14.167164] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   14.167183] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   14.167188] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.167231] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   14.167269] ehci_hcd 0000:00:1d.7: debug port 1
[   14.167276] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   14.167287] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80800
[   14.208998] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.209142] usb usb5: configuration #1 chosen from 1 choice
[   14.209173] hub 5-0:1.0: USB hub found
[   14.209184] hub 5-0:1.0: 8 ports detected
[   14.312857] ata_piix 0000:00:1f.1: version 2.11
[   14.312878] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   14.312921] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   14.313020] scsi0 : ata_piix
[   14.313457] scsi1 : ata_piix
[   14.313499] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   14.313503] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   14.476768] ata1.00: ATA-4: ST320413A, 3.39, max UDMA/100
[   14.476772] ata1.00: 39102336 sectors, multi 8: LBA 
[   14.492716] ata1.00: configured for UDMA/100
[   14.616103] usb 1-1: device not accepting address 2, error -71
[   14.967682] ata2.00: ATAPI: SAMSUNG DVD-ROM SD-616T, F310, max UDMA/33
[   14.967689] ata2.01: ATAPI: HL-DT-ST GCE-8481B, C102, max UDMA/33
[   15.131343] ata2.00: configured for UDMA/33
[   15.295199] ata2.01: configured for UDMA/33
[   15.295333] scsi 0:0:0:0: Direct-Access     ATA      ST320413A        3.39 PQ: 0 ANSI: 5
[   15.296143] scsi 1:0:0:0: CD-ROM            SAMSUNG  DVD-ROM SD-616T  F310 PQ: 0 ANSI: 5
[   15.296711] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8481B  C102 PQ: 0 ANSI: 5
[   15.297015] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   15.297034] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   15.297077] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   15.297125] scsi2 : ata_piix
[   15.297325] scsi3 : ata_piix
[   15.297482] ata3: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fe12 bmdma 0x0001fea0 irq 18
[   15.297486] ata4: SATA max UDMA/133 cmd 0x0001fe20 ctl 0x0001fe32 bmdma 0x0001fea8 irq 18
[   15.350596] usb 5-2: new high speed USB device using ehci_hcd and address 3
[   15.487041] usb 5-2: configuration #1 chosen from 1 choice
[   15.514622] ata3.00: ATA-6: ST3120023AS, 3.01, max UDMA/133
[   15.514626] ata3.00: 234441648 sectors, multi 8: LBA 
[   15.514629] ata3.00: applying bridge limits
[   15.530571] ata3.00: configured for UDMA/100
[   15.686047] scsi 2:0:0:0: Direct-Access     ATA      ST3120023AS      3.01 PQ: 0 ANSI: 5
[   15.690929] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 20
[   15.740945] usb 5-7: new high speed USB device using ehci_hcd and address 4
[   15.743067] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fe8fe000-fe8fe7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   15.753205] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   15.776625] e100: eth0: e100_probe: addr 0xfe8ff000, irq 21, MAC addr 00:07:E9:6E:A8:94
[   15.797712] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[   15.798941] sd 0:0:0:0: [sda] Write Protect is off
[   15.798945] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.805507] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.805611] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[   15.805625] sd 0:0:0:0: [sda] Write Protect is off
[   15.805628] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.805659] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.805664]  sda: sda1 sda2 < sda5 >
[   15.852876] sd 0:0:0:0: [sda] Attached SCSI disk
[   15.853635] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   15.853650] sd 2:0:0:0: [sdb] Write Protect is off
[   15.853653] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   15.853672] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.853825] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   15.853837] sd 2:0:0:0: [sdb] Write Protect is off
[   15.853840] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   15.853858] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.853862]  sdb:sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   15.855861] Uniform CD-ROM driver Revision: 3.20
[   15.855900] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   15.858675] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   15.858725] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   15.877227]  sdb1 sdb2
[   15.877297] sd 2:0:0:0: [sdb] Attached SCSI disk
[   15.881541] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   15.881565] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   15.881586] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   15.881610] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   16.028567] usb 5-7: configuration #1 chosen from 1 choice
[   16.264697] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   16.280446] Attempting manual resume
[   16.280451] swsusp: Resume From Partition 8:5
[   16.280453] PM: Checking swsusp image.
[   16.308686] PM: Resume from disk failed.
[   16.365320] kjournald starting.  Commit interval 5 seconds
[   16.365335] EXT3-fs: mounted filesystem with ordered data mode.
[   16.441234] usb 1-1: configuration #1 chosen from 1 choice
[   17.019238] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00601d0000004786]
[   25.539159] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.709473] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.724897] Linux agpgart interface v0.102 (c) Dave Jones
[   25.761073] agpgart: Detected an Intel i875 Chipset.
[   25.766026] agpgart: AGP aperture is 128M @ 0xe0000000
[   25.779052] EDAC MC: Ver: 2.0.1 Oct 14 2007
[   25.790291] EDAC i82875p: i82875p init one
[   25.798626] PCI: Unable to reserve mem region #1:1000@fecf0000 for device 0000:00:06.0
[   25.798757] EDAC MC0: Giving out device to i82875p_edac i82875p: DEV 0000:00:00.0
[   25.902119] iTCO_vendor_support: vendor-support=0
[   25.903536] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   25.903615] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   25.903658] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   26.052583] input: PC Speaker as /class/input/input2
[   26.239118] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   26.239121]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   26.239122]  you are certain that your <4>intel_rng: system has a functional
[   26.239124]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   26.550074] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0820
[   26.550098] usbcore: registered new interface driver usblp
[   26.550101] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   26.581768] usbcore: registered new interface driver hiddev
[   26.594279] input: Microsoft Basic Optical Mouse as /class/input/input3
[   26.594352] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.0-1
[   26.594368] usbcore: registered new interface driver usbhid
[   26.594372] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   27.096622] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   27.096646] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   27.164701] ieee80211_init: failed to initialize WME (err=-17)
[   27.175439] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   27.175485] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   27.175523] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   27.175584] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   27.198436] wmaster0: Selected rate control algorithm 'simple'
[   27.287436] usbcore: registered new interface driver rt73usb
[   27.295164] usbcore: registered new interface driver rt2500usb
[   27.517347] intel8x0_measure_ac97_clock: measured 52343 usecs
[   27.517351] intel8x0: clocking to 48000
[   28.412409] lp: driver loaded but no devices found
[   28.498024] Adding 859436k swap on /dev/sda5.  Priority:-1 extents:1 across:859436k
[   29.000253] EXT3 FS on sda1, internal journal
[   29.750606] kjournald starting.  Commit interval 5 seconds
[   29.756868] EXT3 FS on sdb2, internal journal
[   29.756873] EXT3-fs: mounted filesystem with ordered data mode.
[   30.616090] input: Power Button (FF) as /class/input/input4
[   30.620900] ACPI: Power Button (FF) [PWRF]
[   30.654923] input: Power Button (CM) as /class/input/input5
[   30.659731] ACPI: Power Button (CM) [VBTN]
[   30.710798] No dock devices found.
[   32.653506] ppdev: user-space parallel port driver
[   32.987170] NET: Registered protocol family 10
[   32.987366] lo: Disabled Privacy Extensions
[   32.987514] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.987669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.209186] audit(1192979404.464:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4719 profile="/usr/sbin/cupsd"
[   33.343198] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.343204] apm: overridden by ACPI.
[   33.705417] Failure registering capabilities with primary security module.
[   37.678018] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   37.684069] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   37.684894] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   37.908918] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   42.900392] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   42.900400] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   42.900404] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[   42.901364] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   42.901664] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   42.901894] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   42.902112] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   42.911351] [fglrx] total      GART = 134217728
[   42.911361] [fglrx] free       GART = 118222848
[   42.911363] [fglrx] max single GART = 118222848
[   42.911365] [fglrx] total      LFB  = 134217728
[   42.911367] [fglrx] free       LFB  = 116387840
[   42.911369] [fglrx] max single LFB  = 116387840
[   42.911371] [fglrx] total      Inv  = 0
[   42.911372] [fglrx] free       Inv  = 0
[   42.911374] [fglrx] max single Inv  = 0
[   42.911376] [fglrx] total      TIM  = 0
[   69.252537] NET: Registered protocol family 17
[   70.283885] wlan0: Initial auth_alg=0
[   70.283893] wlan0: authenticate with AP 00:12:bf:49:71:2a
[   70.285286] wlan0: RX authentication from 00:12:bf:49:71:2a (alg=0 transaction=2 status=0)
[   70.285292] wlan0: authenticated
[   70.285295] wlan0: associate with AP 00:12:bf:49:71:2a
[   70.290137] wlan0: RX AssocResp from 00:12:bf:49:71:2a (capab=0x71 status=0 aid=2)
[   70.290142] wlan0: associated
[   70.292783] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   70.390314] wlan0: CTS protection enabled (BSSID=00:12:bf:49:71:2a)
[   70.633391] wlan0: duplicate address detected!
[   79.762946] wlan0: duplicate address detected!
[ 1082.326699] [fglrx] Internal AGP support requested, but kernel AGP support active.
[ 1082.326707] [fglrx] Have to use kernel AGP support to avoid conflicts.
[ 1082.326711] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[ 1082.327672] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 1082.327947] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 1082.328172] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 1082.328384] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[ 1082.338372] [fglrx] total      GART = 134217728
[ 1082.338381] [fglrx] free       GART = 118222848
[ 1082.338384] [fglrx] max single GART = 118222848
[ 1082.338386] [fglrx] total      LFB  = 134217728
[ 1082.338388] [fglrx] free       LFB  = 100659200
[ 1082.338390] [fglrx] max single LFB  = 100659200
[ 1082.338392] [fglrx] total      Inv  = 0
[ 1082.338393] [fglrx] free       Inv  = 0
[ 1082.338395] [fglrx] max single Inv  = 0
[ 1082.338397] [fglrx] total      TIM  = 0
[ 1121.426584] [fglrx] Internal AGP support requested, but kernel AGP support active.
[ 1121.426604] [fglrx] Have to use kernel AGP support to avoid conflicts.
[ 1121.426609] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[ 1121.427534] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 1121.427805] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 1121.428029] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 1121.428239] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[ 1121.438356] [fglrx] total      GART = 134217728
[ 1121.438364] [fglrx] free       GART = 118222848
[ 1121.438367] [fglrx] max single GART = 118222848
[ 1121.438369] [fglrx] total      LFB  = 134217728
[ 1121.438371] [fglrx] free       LFB  = 100659200
[ 1121.438373] [fglrx] max single LFB  = 100659200
[ 1121.438374] [fglrx] total      Inv  = 0
[ 1121.438376] [fglrx] free       Inv  = 0
[ 1121.438378] [fglrx] max single Inv  = 0
[ 1121.438380] [fglrx] total      TIM  = 0
[ 1164.731943] [fglrx] Internal AGP support requested, but kernel AGP support active.
[ 1164.731951] [fglrx] Have to use kernel AGP support to avoid conflicts.
[ 1164.731955] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[ 1164.732928] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 1164.733205] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 1164.733428] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 1164.733640] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[ 1164.743810] [fglrx] total      GART = 134217728
[ 1164.743819] [fglrx] free       GART = 118222848
[ 1164.743822] [fglrx] max single GART = 118222848
[ 1164.743824] [fglrx] total      LFB  = 134217728
[ 1164.743826] [fglrx] free       LFB  = 116387840
[ 1164.743828] [fglrx] max single LFB  = 116387840
[ 1164.743830] [fglrx] total      Inv  = 0
[ 1164.743831] [fglrx] free       Inv  = 0
[ 1164.743833] [fglrx] max single Inv  = 0
[ 1164.743835] [fglrx] total      TIM  = 0
[ 2496.841429] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2496.941331] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 2497.041096] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2497.140867] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2497.240641] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 2498.338388] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2498.438163] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 2498.537933] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2498.637707] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[ 2498.737603] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2498.837377] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 2499.934991] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2500.034894] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 2500.134667] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2500.234439] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
[ 2500.334211] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2500.433985] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 2501.232295] wlan0: No ProbeResp from current AP 00:12:bf:49:71:2a - assume out of range
[ 2501.463882] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2501.563656] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2501.663428] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2501.763193] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2501.863091] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2501.962867] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2502.062633] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2502.062741] phy0 -> rt73usb_bbp_read: Error - PHY_CSR3 register busy. Read failed.
[ 2502.162415] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2502.262188] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 2502.362084] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2502.461857] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3090 with error -110.
[ 2502.561624] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2502.661393] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2502.761169] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2502.860937] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2502.960841] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2502.960950] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2503.060615] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2503.160386] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2503.260158] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2503.359930] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2503.459703] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2503.459811] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2503.559477] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2503.659374] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2503.759138] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2503.858908] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2503.958691] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2503.958799] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2504.058455] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2504.158365] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2504.258125] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2504.357907] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2504.457677] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2504.457785] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2504.557444] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2504.657214] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2504.756985] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2504.856881] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2504.956657] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2504.956766] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2505.056430] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2505.156199] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2505.255971] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2505.355876] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2505.455654] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2505.455761] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2505.555422] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2505.655190] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2505.754957] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2505.854732] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2505.954503] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2505.954611] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2506.054400] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2506.154172] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2506.253945] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2506.353716] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2506.453496] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2506.453604] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2506.553393] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2506.653158] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2506.752932] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2506.852702] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2506.952482] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2506.952591] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2507.052249] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2507.152019] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2507.251915] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2507.351689] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2507.451461] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2507.451569] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2507.551239] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2507.651005] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2507.750778] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2507.850675] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2507.950447] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2507.950555] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2508.058201] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[ 2508.157980] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[ 2508.257751] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[ 2508.357517] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[ 2508.457416] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2508.557188] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2508.656960] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[ 2508.756739] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[ 2508.856510] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[ 2508.956287] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[ 2509.056173] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2509.155951] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2509.311594] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2509.411362] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2509.511136] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2509.611038] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2509.710809] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2509.810584] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2509.910354] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2509.910462] phy0 -> rt73usb_bbp_read: Error - PHY_CSR3 register busy. Read failed.
[ 2510.010129] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2510.109898] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 2510.209790] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2510.309569] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3090 with error -110.
[ 2510.409338] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2510.509112] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2510.608880] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2510.708652] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2510.808554] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2510.808663] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2510.908329] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2511.008113] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2511.107873] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2511.207643] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2511.307411] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2511.307519] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2511.407308] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2511.507080] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2511.606853] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2511.706624] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2511.806400] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2511.806509] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2511.906170] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2512.006066] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2512.105839] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2512.205611] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2512.305383] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2512.305491] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2512.405154] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2512.504928] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2512.604825] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2512.704597] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2512.804372] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2512.804481] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2512.904141] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2513.003913] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2513.103687] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2513.203591] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2513.303360] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2513.303468] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2513.403127] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2513.502899] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2513.602672] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2513.702444] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2513.802344] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2513.802453] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2513.902123] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.001890] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.101657] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.201430] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.301203] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.301311] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2514.401099] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.500872] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.600668] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.700424] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.800318] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.800426] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2514.899967] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2514.999862] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2515.099636] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2515.199410] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2515.299181] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2515.299290] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2515.398957] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2515.498726] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2515.598617] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2515.698394] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2515.798166] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2515.798274] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2515.905916] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[ 2516.005687] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[ 2516.105466] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[ 2516.205364] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[ 2516.305132] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2516.404907] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2516.504678] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[ 2516.604452] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[ 2516.704219] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[ 2516.804121] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[ 2516.903887] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2517.003671] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2517.159304] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2517.259078] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2517.358853] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2517.458753] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2517.558519] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2517.658292] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2517.758064] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2517.758172] phy0 -> rt73usb_bbp_read: Error - PHY_CSR3 register busy. Read failed.
[ 2517.857836] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 2517.957608] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 2518.057505] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2518.157278] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3090 with error -110.
[ 2518.257048] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2518.356824] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2518.456595] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2518.556365] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2518.656264] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2518.656373] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2518.756037] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2518.855809] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2518.955582] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2519.055356] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2519.155125] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2519.155233] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2519.255023] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2519.354794] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2519.454573] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2519.554338] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2519.654112] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2519.654221] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2519.754009] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2519.853784] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2519.953555] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2520.053325] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2520.153096] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2520.153206] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2520.252873] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2520.352643] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2520.452546] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2520.552312] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2520.652091] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2520.652200] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2520.751856] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2520.851628] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2520.951403] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2521.051298] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2521.151074] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2521.151182] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2521.250845] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2521.350621] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2521.450387] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2521.550159] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2521.650059] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2521.650167] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2521.749827] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2521.849601] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2521.949378] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2522.049146] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2522.148919] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2522.149027] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2522.248820] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2522.348585] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2522.448359] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2522.548131] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2522.647901] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2522.648010] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2522.747676] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2522.847573] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2522.947346] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2523.047123] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2523.146890] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2523.146998] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2523.246660] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2523.346439] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2523.402431] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3010 with error -110.
[ 2523.405233] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2523.446332] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2523.546103] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2523.645885] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[ 2523.645992] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 2523.753630] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[ 2523.853404] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[ 2523.953175] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[ 2524.053069] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[ 2524.152844] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2524.252614] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2524.352387] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[ 2524.452161] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[ 2524.551933] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[ 2524.651830] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[ 2524.751603] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2524.851374] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2524.967814] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2525.066891] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2525.166912] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -110.
[ 2525.266559] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -110.
[ 2525.366457] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[ 2525.466478] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -110.
[ 2525.677620] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[ 2525.777385] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[ 2525.901228] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[ 2526.001000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[ 2526.100772] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[ 2526.200545] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 2526.300442] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 2526.400215] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[ 2526.499987] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[ 2526.599758] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[ 2526.699531] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[ 2526.799302] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[ 2526.899076] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 2526.998977] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[ 2527.098745] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 2527.217483] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 2527.334208] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 2527.455316] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 2527.573784] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 2527.589607] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
```

I think the last lines are the interesting.
How can I prevent it from happening ?

---

### Post by gb5uqx on 2007-10-22
Just try this and see what happens...

> sudo /etc/init.d/networking restart

Works for me. I have a similar problem and it's drivin me nutz

---

### Post by okst666 on 2007-10-22
thanks, but it does not work for me...
dmesg-dumps still full and no network after I tried...
Still complete reboot and unplug neccessary.

C'mon..I can believe that 7.10 is that bad...

---

### Post by Tobu on 2007-10-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/133486](https://bugs.launchpad.net/ubuntu/+bug/133486) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is a bug with rt73usb. When doing a log of reassociations (while downloading, with poor radio...), the driver goes nuts.

More info here (no fix in Gutsy yet): [https://bugs.launchpad.net/ubuntu/+bug/133486](https://bugs.launchpad.net/ubuntu/+bug/133486)

---

### Post by okst666 on 2007-11-07
The problem occures more often now...(dont know why) and the wlan-stick get so hot when the connection drops that you can allready smell the melting plastic.

BTW: Who can I sue, when my house burns down by fire from my wlan-adapter ?

edit: I can make fingerprints in the case of that stick

---

### Post by gvigorus on 2007-11-23
Hi. I've got the same issue using RT73 Ralink USB dongle. Maybe ndiswrapper is a better solution at this time since linux driver is still so unstable?

---

### Post by okst666 on 2007-11-29
strange...
yesterday night, I surfed with firefox on a friends computer (xammp) for some files.
Everytime Firefox started a download of a file, and later even calling the website caused the driver to crash and makes the usbstick cooking.

I tried Opera then, and it worked perfectly and had no crashs at all.
Now I realize that those crashes allways only happen, when I use firefox.
The crashs never occur doing something else.

So - is it the driver, or firefox causing this misbehaviour ?

---

