---
title: "netgear wireless USB card not working"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by jord1242 on 2008-02-10
I am trying to use a netgear usb 2.0 adapter, WG111v2 and configure it with ndiswrapper.

I read on the forum where someone was able to use the Win98 driver, so I downloaded the appropriate net111v2.inf driver and did the following:

```
# sudo ndiswrapper -i /home/{account}/net111v2.inf
# sudo depmod -a
# sudo modprobe ndiswrapper
# sudo ndiswrapper -m
```rebooted the machine 

I confirmed it was installed with 
```

# sudo ndiswrapper -l
```It can see my netgear access point, but when I try and connect it says "unable to connect to netgear".

If anyone has any ideas, I would like to hear them. Thanks.

Here is my iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:47:96:E4
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
```Here is my iwlist scan on wlan0:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:47:96:E4
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```Here is my dmesg:


```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fffdc00 (usable)
[    0.000000]  BIOS-e820: 000000000fffdc00 - 000000000ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65533) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65533
[    0.000000]   HighMem     65533 ->    65533
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65533
[    0.000000] On node 0 totalpages: 65533
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60958 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6A80 checksum 0
[    0.000000] ACPI: RSDP 000F6A80, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0FFFDE96, 0028 (r1 PTLTD    RSDT          1 PTL   1000000)
[    0.000000] ACPI: FACP 0FFFFB8C, 0074 (r1 GATEWA TABOR II 19991104 PTL     F4240)
[    0.000000] ACPI: DSDT 0FFFDEBE, 1CCE (r1 GATEWA TABOR II        1 MSFT  1000004)
[    0.000000] ACPI: FACS 0FFFFFC0, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effe7000)
[    0.000000] Built 1 zonelists.  Total pages: 65022
[    0.000000] Kernel command line: root=UUID=f4b99621-5055-414f-8ac8-68fa545a48c1 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0120c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 497.448 MHz processor.
[   86.886718] Console: colour VGA+ 80x25
[   86.887315] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   86.887878] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   86.923587] Memory: 248076k/262132k available (2015k kernel code, 13528k reserved, 916k data, 364k init, 0k highmem)
[   86.923629] virtual kernel memory layout:
[   86.923634]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   86.923640]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   86.923646]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   86.923652]     lowmem  : 0xc0000000 - 0xcfffd000   ( 255 MB)
[   86.923658]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   86.923664]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   86.923670]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   86.923684] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   86.923820] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   87.003843] Calibrating delay using timer specific routine.. 995.99 BogoMIPS (lpj=1991984)
[   87.003944] Security Framework v1.0.0 initialized
[   87.003972] SELinux:  Disabled at boot.
[   87.004036] Mount-cache hash table entries: 512
[   87.004495] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   87.004538] CPU: L1 I cache: 16K, L1 D cache: 16K
[   87.004549] CPU: L2 cache: 512K
[   87.004560] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   87.004600] Compat vDSO mapped to ffffe000.
[   87.004648] Checking 'hlt' instruction... OK.
[   87.020168] SMP alternatives: switching to UP code
[   87.020744] Freeing SMP alternatives: 11k freed
[   87.021726] Early unpacking initramfs... done
[   88.375433] ACPI: Core revision 20070126
[   88.375689] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   88.378368] ACPI: setting ELCR to 0200 (from 0e20)
[   88.379846] CPU0: Intel Pentium III (Katmai) stepping 03
[   88.379868] SMP motherboard not detected.
[   88.379878] Local APIC not detected. Using dummy APIC emulation.
[   88.380045] Brought up 1 CPUs
[   88.380498] Booting paravirtualized kernel on bare hardware
[   88.380668] Time: 19:12:21  Date: 01/10/108
[   88.380767] NET: Registered protocol family 16
[   88.381146] EISA bus registered
[   88.381180] ACPI: bus type pci registered
[   88.381919] PCI: PCI BIOS revision 2.10 entry at 0xfd983, last bus=1
[   88.381929] PCI: Using configuration type 1
[   88.381937] Setting up standard PCI resources
[   88.389197] ACPI: EC: Look up EC in DSDT
[   88.395777] ACPI: Interpreter enabled
[   88.395791] ACPI: (supports S0 S1 S5)
[   88.395848] ACPI: Using PIC for interrupt routing
[   88.409383] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   88.409414] PCI: Probing PCI hardware (bus 00)
[   88.409907] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   88.409915] * this clock source is slow. Consider trying other clock sources
[   88.409982] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   88.409994] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[   88.410663] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   88.414857] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12)
[   88.415210] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[   88.415634] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12)
[   88.415990] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[   88.416397] ACPI: Power Resource [PFAN] (on)
[   88.416455] Linux Plug and Play Support v0.97 (c) Adam Belay
[   88.416519] pnp: PnP ACPI init
[   88.416555] ACPI: bus type pnp registered
[   88.431233] pnp: PnP ACPI: found 12 devices
[   88.431244] ACPI: ACPI bus type pnp unregistered
[   88.431258] PnPBIOS: Disabled by ACPI PNP
[   88.431485] PCI: Using ACPI for IRQ routing
[   88.431499] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   88.433978] NET: Registered protocol family 8
[   88.433989] NET: Registered protocol family 20
[   88.434243] pnp: 00:01: ioport range 0x7000-0x700f has been reserved
[   88.434258] pnp: 00:01: ioport range 0x8000-0x803f has been reserved
[   88.434274] pnp: 00:01: iomem range 0xfff80000-0xffffffff could not be reserved
[   88.435531] Time: tsc clocksource has been installed.
[   88.465930] PCI: Bridge: 0000:00:01.0
[   88.465939]   IO window: disabled.
[   88.465953]   MEM window: f1000000-f1ffffff
[   88.465965]   PREFETCH window: f8000000-fc0fffff
[   88.466022] NET: Registered protocol family 2
[   88.503698] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   88.503861] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[   88.504256] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   88.504518] TCP: Hash tables configured (established 8192 bind 8192)
[   88.504529] TCP reno registered
[   88.515999] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   89.707688]  it is
[   91.110145] Freeing initrd memory: 7396k freed
[   91.111425] audit: initializing netlink socket (disabled)
[   91.111472] audit(1202670743.016:1): initialized
[   91.122970] VFS: Disk quotas dquot_6.5.1
[   91.123271] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   91.123710] io scheduler noop registered
[   91.123721] io scheduler anticipatory registered
[   91.123730] io scheduler deadline registered
[   91.123836] io scheduler cfq registered (default)
[   91.123872] Limiting direct PCI/PCI transfers.
[   91.123939] Boot video device is 0000:01:00.0
[   91.124585] isapnp: Scanning for PnP cards...
[   91.479019] isapnp: No Plug & Play device found
[   91.628480] Real Time Clock Driver v1.12ac
[   91.628890] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   91.629083] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   91.630399] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[   91.631961] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   91.636375] pnp: Device 00:0b activated.
[   91.636765] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   91.640314] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   91.640897] input: Macintosh mouse button emulation as /class/input/input0
[   91.641288] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MICE] at 0x60,0x64 irq 1,12
[   91.643886] serio: i8042 KBD port at 0x60,0x64 irq 1
[   91.643907] serio: i8042 AUX port at 0x60,0x64 irq 12
[   91.644739] mice: PS/2 mouse device common for all mice
[   91.645278] EISA: Probing bus 0 at eisa.0
[   91.645303] Cannot allocate resource for EISA slot 1
[   91.645345] Cannot allocate resource for EISA slot 7
[   91.645355] Cannot allocate resource for EISA slot 8
[   91.645364] EISA: Detected 0 cards.
[   91.645718] TCP cubic registered
[   91.645784] NET: Registered protocol family 1
[   91.645886] Using IPI No-Shortcut mode
[   91.646417]   Magic number: 12:907:242
[   91.646549]   hash matches device ttysf
[   91.648112] Freeing unused kernel memory: 364k freed
[   91.706657] input: AT Translated Set 2 keyboard as /class/input/input1
[   93.513441] AppArmor: AppArmor initialized<5>audit(1202670745.516:2):  type=1505 info="AppArmor initialized" pid=1156
[   93.554055] fuse init (API version 7.8)
[   93.576876] Failure registering capabilities with primary security module.
[   93.610329] ACPI: Fan [FAN1] (on)
[   93.639273] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   95.821442] SCSI subsystem initialized
[   95.871532] libata version 2.21 loaded.
[   95.897830] ata_piix 0000:00:07.1: version 2.11
[   95.898391] scsi0 : ata_piix
[   95.898575] scsi1 : ata_piix
[   95.898705] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011000 irq 14
[   95.898722] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011008 irq 15
[   96.011931] usbcore: registered new interface driver usbfs
[   96.012048] usbcore: registered new interface driver hub
[   96.012161] usbcore: registered new device driver usb
[   96.018831] USB Universal Host Controller Interface driver v3.0
[   96.061649] ata1.00: ATA-7: Maxtor 6Y080P0, YAR41BW0, max UDMA/133
[   96.061667] ata1.00: 160086528 sectors, multi 16: LBA
[   96.077608] ata1.00: configured for UDMA/33
[   96.168808] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[   96.188910] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   96.659974] Floppy drive(s): fd0 is 1.44M
[   96.721360] ata2.00: ATAPI: CRD-8400B, 1.04, max UDMA/33
[   96.721383] ata2.01: ATAPI: LITE-ON LTR-40125S, ZS0J, max UDMA/33
[   96.721408] ata2.00: device is on DMA blacklist, disabling DMA
[   96.748736] FDC 0 is a post-1991 82077
[   96.877361] ata2.00: configured for PIO4
[   10.096000] Marking TSC unstable due to: possible TSC halt in C2.
[   10.100000] Time: acpi_pm clocksource has been installed.
[   10.132000] ata2.01: configured for UDMA/33
[   10.132000] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080P0   YAR4 PQ: 0 ANSI: 5
[   10.132000] scsi 1:0:0:0: CD-ROM            LG       CD-ROM CRD-8400B 1.04 PQ: 0 ANSI: 5
[   10.136000] scsi 1:0:1:0: CD-ROM            LITE-ON  LTR-40125S       ZS0J PQ: 0 ANSI: 5
[   10.136000] PCI: Enabling device 0000:00:0d.0 (0104 -> 0107)
[   10.136000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   10.136000] PCI: setting IRQ 10 as level-triggered
[   10.136000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   10.160000] eth0: Davicom DM9102 at pci0000:00:0d.0, 00:08:a1:17:68:ac, irq 10.
[   10.160000] PCI: Enabling device 0000:00:0f.0 (0114 -> 0116)
[   10.160000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   10.160000] PCI: setting IRQ 5 as level-triggered
[   10.160000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   10.160000] ohci_hcd 0000:00:0f.0: OHCI Host Controller
[   10.160000] ohci_hcd 0000:00:0f.0: new USB bus registered, assigned bus number 1
[   10.160000] ohci_hcd 0000:00:0f.0: irq 5, io mem 0xf0001000
[   10.244000] usb usb1: configuration #1 chosen from 1 choice
[   10.244000] hub 1-0:1.0: USB hub found
[   10.244000] hub 1-0:1.0: 2 ports detected
[   10.264000] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[   10.264000] sd 0:0:0:0: [sda] Write Protect is off
[   10.264000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.264000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.264000] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[   10.264000] sd 0:0:0:0: [sda] Write Protect is off
[   10.264000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.264000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.264000]  sda: sda1 sda2 < sda5 >
[   10.312000] sd 0:0:0:0: [sda] Attached SCSI disk
[   10.336000] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[   10.336000] Uniform CD-ROM driver Revision: 3.20
[   10.336000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   10.336000] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   10.336000] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   10.340000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   10.340000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   10.340000] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   10.348000] PCI: Enabling device 0000:00:0f.1 (0114 -> 0116)
[   10.348000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   10.348000] PCI: setting IRQ 9 as level-triggered
[   10.348000] ACPI: PCI Interrupt 0000:00:0f.1[b] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   10.348000] ohci_hcd 0000:00:0f.1: OHCI Host Controller
[   10.348000] ohci_hcd 0000:00:0f.1: new USB bus registered, assigned bus number 2
[   10.348000] ohci_hcd 0000:00:0f.1: irq 9, io mem 0xf0002000
[   10.432000] usb usb2: configuration #1 chosen from 1 choice
[   10.432000] hub 2-0:1.0: USB hub found
[   10.432000] hub 2-0:1.0: 1 port detected
[   10.536000] PCI: Enabling device 0000:00:0f.2 (0114 -> 0116)
[   10.536000] ACPI: PCI Interrupt 0000:00:0f.2[C] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   10.536000] ehci_hcd 0000:00:0f.2: EHCI Host Controller
[   10.536000] ehci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 3
[   10.560000] ehci_hcd 0000:00:0f.2: irq 10, io mem 0xf0000400
[   10.560000] ehci_hcd 0000:00:0f.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   10.560000] usb usb3: configuration #1 chosen from 1 choice
[   10.560000] hub 3-0:1.0: USB hub found
[   10.560000] hub 3-0:1.0: 3 ports detected
[   10.664000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   10.664000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   10.664000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 4
[   10.664000] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001020
[   10.664000] usb usb4: configuration #1 chosen from 1 choice
[   10.664000] hub 4-0:1.0: USB hub found
[   10.664000] hub 4-0:1.0: 2 ports detected
[   11.008000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   11.140000] Attempting manual resume
[   11.140000] swsusp: Resume From Partition 8:5
[   11.140000] PM: Checking swsusp image.
[   11.140000] PM: Resume from disk failed.
[   11.188000] usb 4-2: configuration #1 chosen from 1 choice
[   11.324000] kjournald starting.  Commit interval 5 seconds
[   11.324000] EXT3-fs: mounted filesystem with ordered data mode.
[   26.320000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.344000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.372000] Linux agpgart interface v0.102 (c) Dave Jones
[   26.444000] agpgart: Detected an Intel 440BX Chipset.
[   26.452000] agpgart: AGP aperture is 64M @ 0xf4000000
[   26.540000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   27.436000] input: PC Speaker as /class/input/input2
[   27.836000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   29.928000] parport_pc 00:0a: reported by Plug and Play ACPI
[   29.928000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   31.732000] PCI: Enabling device 0000:00:0e.0 (0104 -> 0105)
[   31.732000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   31.732000] PCI: setting IRQ 11 as level-triggered
[   31.732000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   33.220000] lp0: using parport0 (interrupt-driven).
[   33.340000] Adding 738948k swap on /dev/sda5.  Priority:-1 extents:1 across:738948k
[   33.704000] EXT3 FS on sda1, internal journal
[   34.016000] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   37.224000] No dock devices found.
[   37.568000] input: Power Button (FF) as /class/input/input4
[   37.568000] ACPI: Power Button (FF) [PWRF]
[   42.588000] ppdev: user-space parallel port driver
[   43.052000] audit(1202670782.658:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4618 profile="/usr/sbin/cupsd"
[   43.384000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   43.384000] apm: overridden by ACPI.
[   46.344000] Failure registering capabilities with primary security module.
[   46.760000] Bluetooth: Core ver 2.11
[   46.760000] NET: Registered protocol family 31
[   46.760000] Bluetooth: HCI device and connection manager initialized
[   46.760000] Bluetooth: HCI socket layer initialized
[   46.820000] Bluetooth: L2CAP ver 2.8
[   46.820000] Bluetooth: L2CAP socket layer initialized
[   46.972000] Bluetooth: RFCOMM socket layer initialized
[   46.972000] Bluetooth: RFCOMM TTY layer initialized
[   46.972000] Bluetooth: RFCOMM ver 1.8
[  271.584000] ndiswrapper version 1.45 loaded (smp=yes)
[  271.772000] usb 4-2: reset full speed USB device using uhci_hcd and address 2
[  272.020000] ndiswrapper: driver net111v2 (NETGEAR Inc.,3/16/2006,5.1213.06.0316) loaded
[  279.628000] wlan0: ethernet device 00:14:6c:6c:7b:f0 using NDIS driver: net111v2, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:6A00.F.conf
[  279.628000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  279.628000] usbcore: registered new interface driver ndiswrapper
[  291.420000] NET: Registered protocol family 17
[  337.912000] NET: Registered protocol family 10
[  337.912000] lo: Disabled Privacy Extensions
[  337.912000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  348.136000] wlan0: no IPv6 routers present
[  352.832000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  365.632000] wlan0: no IPv6 routers present
[  444.784000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  676.832000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  687.320000] wlan0: no IPv6 routers present
[  857.144000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  867.804000] wlan0: no IPv6 routers present
[  918.532000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  975.536000] wlan0: no IPv6 routers present
```

---

### Post by jord1242 on 2008-02-11
Just wondering if anyone had any ideas to try? I have seen people successfully get this adapter to work, and it is recognizing the WAP (which is also netgear) but is not connecting for some reason.

Thanks for any help you can provide!

JJ

---

### Post by sennep on 2008-02-11
You've balcklisted the rtl8187 right?

What is the output of ```
lsusb
```

---

### Post by jord1242 on 2008-02-11
Yes, I blacklisted a bunch of different drivers from a post of a guy on here that got it working. I'll post my blacklist file and also the output from the command you gave tonight from home.

Thanks for the reply.

JJ

---

### Post by jord1242 on 2008-02-11
Here is the output of what I blacklisted.

```
desktop:~$ cat /etc/modprobe.d/blacklist
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

# wg111v2 conflicting drivers
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b
```

Here is the output of lsusb:

```
desktop:~$ sudo lsusb
Bus 004 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

Thanks again for the help!

JJ

---

### Post by sennep on 2008-02-12
I have the exact same version (0846:6a00) of this adapter, and the driver on my CD didn't work.Try [this driver]("http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html") with ndiswrapper and see if it makes a difference. I think you have to uninstall the old driver first though, the command is "ndiswrapper -r filename" or something like that.

---

### Post by jord1242 on 2008-02-12
Sweet. Thanks. I am to keep the same blacklists?

JJ

---

### Post by sennep on 2008-02-12
yeah just keep that blacklist, it shouldn't do any harm.

---

### Post by jord1242 on 2008-02-16
Installed the driver (after removing the old) and this time used ndisgtk to install it. it installed fine, but it still won't connect to my wireless (but does see it).

```
-desktop:~$ ndiswrapper -l
netrtuw : driver installed
        device (0846:6A00) present (alternate driver: rtl8187)
```


Any other ideas what to do? Anyway to debug why it is not connecting?

Thanks,
JJ

---

### Post by Hightide on 2008-02-16
HI Jord1242

I had a similar problem with my Netgear USB and only after a Gutsy reinstall did I get it working with WPA PSK security.

But have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=590942#6") first


regards

:)

---

### Post by jord1242 on 2008-02-16
> **Hightide said:**
> HI Jord1242

I had a similar problem with my Netgear USB and only after a Gutsy reinstall did I get it working with WPA PSK security.

But have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=590942#6") first


regards

:)

Thanks. I'll check that thread and re-try it again. 

JJ

---

