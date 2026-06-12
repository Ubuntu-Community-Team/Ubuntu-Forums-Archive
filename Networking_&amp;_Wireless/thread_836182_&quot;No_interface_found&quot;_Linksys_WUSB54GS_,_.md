---
title: "&quot;No interface found&quot; Linksys WUSB54GS , Ubuntu 8"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by Bradwerkz on 2008-06-21
Hey guys,

  Need some help with my wireless USB adapter.

  OS : Ubuntu 8 Hardy
  Wifi : USB Linksys WUSB54GS with SpeedBooster

Somehow, with god's help, I managed to install the driver with ndiswrapper 1.53.
 
1)  When I do a ndiswrapper -l ; it shows the driver is   installed and present.
2)  It also does manage to scan my router and others in the Network.
3)  It seems to be connected to my router but I cant get online.
4)  When I go to Network Tools, and click "Configure" , it says " Interface does not exist". 
5)  It seems like in the Network Tools, by defauly it doesnt show
my wireless, it shows "LO" or something like that. When I select my wireless (wlan0;avahi) or something like that, it shows all the correct info, such as speed and so on.

Thanks in advanced for your help. Really appreciate it.

Regards,
Brad

---

### Post by javaJake on 2008-06-21
Hmmm, this sounds suspiciously like you goofed up your system. Let's see what's going on...

I'll need the following files, or at least the last 50 lines in them:
```
/etc/network/interfaces
*(after connecting your device and waiting 5-10 seconds)*/var/log/syslog
```

At this point it would be best to leave NetworkManager (the little icon in the upper-right corner) out of this and just use the System -> Administration -> Networking utility until we figure this all out.

---

### Post by Bradwerkz on 2008-06-22
> **javaJake said:**
> Hmmm, this sounds suspiciously like you goofed up your system. Let's see what's going on...

I'll need the following files, or at least the last 50 lines in them:
```
/etc/network/interfaces
*(after connecting your device and waiting 5-10 seconds)*/var/log/syslog
```

At this point it would be best to leave NetworkManager (the little icon in the upper-right corner) out of this and just use the System -> Administration -> Networking utility until we figure this all out.


Jun 22 15:34:48 doinkz-desktop kernel: [   38.131797] AppArmor: AppArmor Filesystem Enabled
Jun 22 15:34:48 doinkz-desktop kernel: [   38.135650] Time: tsc clocksource has been installed.
Jun 22 15:34:48 doinkz-desktop kernel: [   38.143692] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jun 22 15:34:48 doinkz-desktop kernel: [   38.143696] system 00:02: ioport range 0x290-0x29f has been reserved
Jun 22 15:34:48 doinkz-desktop kernel: [   38.143698] system 00:02: ioport range 0x800-0x805 has been reserved
Jun 22 15:34:48 doinkz-desktop kernel: [   38.174192] PCI: Bridge: 0000:00:01.0
Jun 22 15:34:48 doinkz-desktop kernel: [   38.174195]   IO window: disabled.
Jun 22 15:34:48 doinkz-desktop kernel: [   38.174203]   MEM window: e4000000-e6ffffff
Jun 22 15:34:48 doinkz-desktop kernel: [   38.174210]   PREFETCH window: d0000000-dfffffff
Jun 22 15:34:48 doinkz-desktop kernel: [   38.174240] NET: Registered protocol family 2
Jun 22 15:34:48 doinkz-desktop kernel: [   38.211645] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 22 15:34:48 doinkz-desktop kernel: [   38.212060] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 22 15:34:48 doinkz-desktop kernel: [   38.212932] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 22 15:34:48 doinkz-desktop kernel: [   38.213714] TCP: Hash tables configured (established 131072 bind 65536)
Jun 22 15:34:48 doinkz-desktop kernel: [   38.213719] TCP reno registered
Jun 22 15:34:48 doinkz-desktop kernel: [   38.223758] checking if image is initramfs... it is
Jun 22 15:34:48 doinkz-desktop kernel: [   38.674910] Switched to high resolution mode on CPU 0
Jun 22 15:34:48 doinkz-desktop kernel: [   38.942058] Freeing initrd memory: 7702k freed
Jun 22 15:34:48 doinkz-desktop kernel: [   38.942786] audit: initializing netlink socket (disabled)
Jun 22 15:34:48 doinkz-desktop kernel: [   38.942804] audit(1214148851.396:1): initialized
Jun 22 15:34:48 doinkz-desktop kernel: [   38.943021] highmem bounce pool size: 64 pages
Jun 22 15:34:48 doinkz-desktop kernel: [   38.945288] VFS: Disk quotas dquot_6.5.1
Jun 22 15:34:48 doinkz-desktop kernel: [   38.945385] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 22 15:34:48 doinkz-desktop kernel: [   38.945552] io scheduler noop registered
Jun 22 15:34:48 doinkz-desktop kernel: [   38.945555] io scheduler anticipatory registered
Jun 22 15:34:48 doinkz-desktop kernel: [   38.945557] io scheduler deadline registered
Jun 22 15:34:48 doinkz-desktop kernel: [   38.945572] io scheduler cfq registered (default)
Jun 22 15:34:48 doinkz-desktop kernel: [   39.026332] Boot video device is 0000:01:00.0
Jun 22 15:34:48 doinkz-desktop kernel: [   39.026662] isapnp: Scanning for PnP cards...
Jun 22 15:34:48 doinkz-desktop kernel: [   39.380062] isapnp: No Plug & Play device found
Jun 22 15:34:48 doinkz-desktop kernel: [   39.415559] Real Time Clock Driver v1.12ac
Jun 22 15:34:48 doinkz-desktop kernel: [   39.415678] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 22 15:34:48 doinkz-desktop kernel: [   39.415811] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 22 15:34:48 doinkz-desktop kernel: [   39.415975] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun 22 15:34:48 doinkz-desktop kernel: [   39.416773] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 22 15:34:48 doinkz-desktop kernel: [   39.417160] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun 22 15:34:48 doinkz-desktop kernel: [   39.418392] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 22 15:34:48 doinkz-desktop kernel: [   39.418483] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 22 15:34:48 doinkz-desktop kernel: [   39.418670] PNP: No PS/2 controller found. Probing ports directly.
Jun 22 15:34:48 doinkz-desktop kernel: [   39.418969] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 22 15:34:48 doinkz-desktop kernel: [   39.418975] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 22 15:34:48 doinkz-desktop kernel: [   39.429813] mice: PS/2 mouse device common for all mice
Jun 22 15:34:48 doinkz-desktop kernel: [   39.429958] EISA: Probing bus 0 at eisa.0
Jun 22 15:34:48 doinkz-desktop kernel: [   39.429966] Cannot allocate resource for EISA slot 1
Jun 22 15:34:48 doinkz-desktop kernel: [   39.429995] EISA: Detected 0 cards.
Jun 22 15:34:48 doinkz-desktop kernel: [   39.429999] cpuidle: using governor ladder
Jun 22 15:34:48 doinkz-desktop kernel: [   39.430001] cpuidle: using governor menu
Jun 22 15:34:48 doinkz-desktop kernel: [   39.430111] NET: Registered protocol family 1
Jun 22 15:34:48 doinkz-desktop kernel: [   39.430147] Using IPI No-Shortcut mode
Jun 22 15:34:48 doinkz-desktop kernel: [   39.430184] registered taskstats version 1
Jun 22 15:34:48 doinkz-desktop kernel: [   39.430278]   Magic number: 12:273:589
Jun 22 15:34:48 doinkz-desktop kernel: [   39.430335]   hash matches device ptyc7
Jun 22 15:34:48 doinkz-desktop kernel: [   39.430407] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 22 15:34:48 doinkz-desktop kernel: [   39.430409] EDD information not available.
Jun 22 15:34:48 doinkz-desktop kernel: [   39.430849] Freeing unused kernel memory: 364k freed
Jun 22 15:34:48 doinkz-desktop kernel: [   40.708892] fuse init (API version 7.9)
Jun 22 15:34:48 doinkz-desktop kernel: [   40.733198] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 22 15:34:48 doinkz-desktop kernel: [   41.393383] SCSI subsystem initialized
Jun 22 15:34:48 doinkz-desktop kernel: [   41.475511] usbcore: registered new interface driver usbfs
Jun 22 15:34:48 doinkz-desktop kernel: [   41.475541] usbcore: registered new interface driver hub
Jun 22 15:34:48 doinkz-desktop kernel: [   41.495204] libata version 3.00 loaded.
Jun 22 15:34:48 doinkz-desktop kernel: [   41.506046] usbcore: registered new device driver usb
Jun 22 15:34:48 doinkz-desktop kernel: [   41.510671] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Jun 22 15:34:48 doinkz-desktop kernel: [   41.510754] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 22 15:34:48 doinkz-desktop kernel: [   41.518376] eth0: VIA Rhine III at 0xe8005000, 00:0e:2e:0a:c5:c9, IRQ 16.
Jun 22 15:34:48 doinkz-desktop kernel: [   41.519102] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
Jun 22 15:34:48 doinkz-desktop kernel: [   41.526638] pata_sis 0000:00:02.5: version 0.5.2
Jun 22 15:34:48 doinkz-desktop kernel: [   41.530301] scsi0 : pata_sis
Jun 22 15:34:48 doinkz-desktop kernel: [   41.536412] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 22 15:34:48 doinkz-desktop kernel: [   41.546647] scsi1 : pata_sis
Jun 22 15:34:48 doinkz-desktop kernel: [   41.547341] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jun 22 15:34:48 doinkz-desktop kernel: [   41.547344] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jun 22 15:34:48 doinkz-desktop kernel: [   41.616144] Floppy drive(s): fd0 is 1.44M
Jun 22 15:34:48 doinkz-desktop kernel: [   41.638156] FDC 0 is a post-1991 82077
Jun 22 15:34:48 doinkz-desktop kernel: [   41.730641] ata1.01: ATA-6: WDC WD800JB-00FMA0, 13.03G13, max UDMA/100
Jun 22 15:34:48 doinkz-desktop kernel: [   41.730647] ata1.01: 156301488 sectors, multi 16: LBA 
Jun 22 15:34:48 doinkz-desktop kernel: [   41.746686] ata1.01: configured for UDMA/100
Jun 22 15:34:48 doinkz-desktop kernel: [   42.085980] ata2.00: ATAPI: ASUS    DVD-E616P2, 1.03, max UDMA/100
Jun 22 15:34:48 doinkz-desktop kernel: [   42.085998] ata2.00: limited to UDMA/33 due to 40-wire cable
Jun 22 15:34:48 doinkz-desktop kernel: [   42.257730] ata2.00: configured for UDMA/33
Jun 22 15:34:48 doinkz-desktop kernel: [   42.257884] scsi 0:0:1:0: Direct-Access     ATA      WDC WD800JB-00FM 13.0 PQ: 0 ANSI: 5
Jun 22 15:34:48 doinkz-desktop kernel: [   42.264910] scsi 1:0:0:0: CD-ROM            ASUS     DVD-E616P2       1.03 PQ: 0 ANSI: 5
Jun 22 15:34:48 doinkz-desktop kernel: [   42.268379] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 17
Jun 22 15:34:48 doinkz-desktop kernel: [   42.268397] ohci_hcd 0000:00:03.0: OHCI Host Controller
Jun 22 15:34:48 doinkz-desktop kernel: [   42.268742] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Jun 22 15:34:48 doinkz-desktop kernel: [   42.268764] ohci_hcd 0000:00:03.0: irq 17, io mem 0xe8001000
Jun 22 15:34:48 doinkz-desktop kernel: [   42.323565] usb usb1: configuration #1 chosen from 1 choice
Jun 22 15:34:48 doinkz-desktop kernel: [   42.323599] hub 1-0:1.0: USB hub found
Jun 22 15:34:48 doinkz-desktop kernel: [   42.323609] hub 1-0:1.0: 2 ports detected
Jun 22 15:34:48 doinkz-desktop kernel: [   42.425349] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 18
Jun 22 15:34:48 doinkz-desktop kernel: [   42.425369] ohci_hcd 0000:00:03.1: OHCI Host Controller
Jun 22 15:34:48 doinkz-desktop kernel: [   42.425398] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Jun 22 15:34:48 doinkz-desktop kernel: [   42.425415] ohci_hcd 0000:00:03.1: irq 18, io mem 0xe8002000
Jun 22 15:34:48 doinkz-desktop kernel: [   42.483242] usb usb2: configuration #1 chosen from 1 choice
Jun 22 15:34:48 doinkz-desktop kernel: [   42.483272] hub 2-0:1.0: USB hub found
Jun 22 15:34:48 doinkz-desktop kernel: [   42.483281] hub 2-0:1.0: 2 ports detected
Jun 22 15:34:48 doinkz-desktop kernel: [   42.585094] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 19
Jun 22 15:34:48 doinkz-desktop kernel: [   42.585114] ohci_hcd 0000:00:03.2: OHCI Host Controller
Jun 22 15:34:48 doinkz-desktop kernel: [   42.585143] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Jun 22 15:34:48 doinkz-desktop kernel: [   42.585160] ohci_hcd 0000:00:03.2: irq 19, io mem 0xe8003000
Jun 22 15:34:48 doinkz-desktop kernel: [   42.643024] usb usb3: configuration #1 chosen from 1 choice
Jun 22 15:34:48 doinkz-desktop kernel: [   42.643055] hub 3-0:1.0: USB hub found
Jun 22 15:34:48 doinkz-desktop kernel: [   42.643065] hub 3-0:1.0: 2 ports detected
Jun 22 15:34:48 doinkz-desktop kernel: [   42.728767] usb 1-1: new full speed USB device using ohci_hcd and address 2
Jun 22 15:34:48 doinkz-desktop kernel: [   42.745251] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 20
Jun 22 15:34:48 doinkz-desktop kernel: [   42.745271] ehci_hcd 0000:00:03.3: EHCI Host Controller
Jun 22 15:34:48 doinkz-desktop kernel: [   42.745311] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
Jun 22 15:34:48 doinkz-desktop kernel: [   42.745354] PCI: cache line size of 128 is not supported by device 0000:00:03.3
Jun 22 15:34:48 doinkz-desktop kernel: [   42.745364] ehci_hcd 0000:00:03.3: irq 20, io mem 0xe8004000
Jun 22 15:34:48 doinkz-desktop kernel: [   42.916477] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 22 15:34:48 doinkz-desktop kernel: [   42.916628] usb usb4: configuration #1 chosen from 1 choice
Jun 22 15:34:48 doinkz-desktop kernel: [   42.916659] hub 4-0:1.0: USB hub found
Jun 22 15:34:48 doinkz-desktop kernel: [   42.916667] hub 4-0:1.0: 6 ports detected
Jun 22 15:34:48 doinkz-desktop kernel: [   43.039127] Driver 'sd' needs updating - please use bus_type methods
Jun 22 15:34:48 doinkz-desktop kernel: [   43.039242] sd 0:0:1:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jun 22 15:34:48 doinkz-desktop kernel: [   43.039259] sd 0:0:1:0: [sda] Write Protect is off
Jun 22 15:34:48 doinkz-desktop kernel: [   43.039263] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
Jun 22 15:34:48 doinkz-desktop kernel: [   43.039286] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 22 15:34:48 doinkz-desktop kernel: [   43.039349] sd 0:0:1:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jun 22 15:34:48 doinkz-desktop kernel: [   43.039363] sd 0:0:1:0: [sda] Write Protect is off
Jun 22 15:34:48 doinkz-desktop kernel: [   43.039366] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
Jun 22 15:34:48 doinkz-desktop kernel: [   43.039389] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 22 15:34:48 doinkz-desktop kernel: [   43.039393]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jun 22 15:34:48 doinkz-desktop kernel: [   43.056624]  sda1 sda2 < sda5 >
Jun 22 15:34:48 doinkz-desktop kernel: [   43.070178] sd 0:0:1:0: [sda] Attached SCSI disk
Jun 22 15:34:48 doinkz-desktop kernel: [   43.076771] sr0: scsi3-mmc drive: 5x/10x cd/rw xa/form2 cdda tray
Jun 22 15:34:48 doinkz-desktop kernel: [   43.076778] Uniform CD-ROM driver Revision: 3.20
Jun 22 15:34:48 doinkz-desktop kernel: [   43.076840] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun 22 15:34:48 doinkz-desktop kernel: [   43.077719] sd 0:0:1:0: Attached scsi generic sg0 type 0
Jun 22 15:34:48 doinkz-desktop kernel: [   43.077743] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jun 22 15:34:48 doinkz-desktop kernel: [   43.311928] usb 1-1: device not accepting address 2, error -62
Jun 22 15:34:48 doinkz-desktop kernel: [   43.724947] loop: module loaded
Jun 22 15:34:48 doinkz-desktop kernel: [   43.756334] kjournald starting.  Commit interval 5 seconds
Jun 22 15:34:48 doinkz-desktop kernel: [   43.756356] EXT3-fs: mounted filesystem with ordered data mode.
Jun 22 15:34:48 doinkz-desktop kernel: [   44.414239] usb 4-5: new high speed USB device using ehci_hcd and address 4
Jun 22 15:34:48 doinkz-desktop kernel: [   44.547099] usb 4-5: configuration #1 chosen from 1 choice
Jun 22 15:34:48 doinkz-desktop kernel: [   44.849586] usb 1-1: new full speed USB device using ohci_hcd and address 4
Jun 22 15:34:48 doinkz-desktop kernel: [   45.061520] usb 1-1: configuration #1 chosen from 1 choice
Jun 22 15:34:48 doinkz-desktop kernel: [   45.064429] hub 1-1:1.0: USB hub found
Jun 22 15:34:48 doinkz-desktop kernel: [   45.067382] hub 1-1:1.0: 4 ports detected
Jun 22 15:34:48 doinkz-desktop kernel: [   45.492634] usb 3-1: new low speed USB device using ohci_hcd and address 2
Jun 22 15:34:48 doinkz-desktop kernel: [   45.827372] usb 3-1: configuration #1 chosen from 1 choice
Jun 22 15:34:48 doinkz-desktop kernel: [   46.044957] usb 1-1.1: new low speed USB device using ohci_hcd and address 5
Jun 22 15:34:48 doinkz-desktop kernel: [   46.157925] usb 1-1.1: configuration #1 chosen from 1 choice
Jun 22 15:34:48 doinkz-desktop kernel: [   46.376466] usb 1-1.4: new full speed USB device using ohci_hcd and address 6
Jun 22 15:34:48 doinkz-desktop kernel: [   46.496438] usb 1-1.4: configuration #1 chosen from 1 choice
Jun 22 15:34:48 doinkz-desktop kernel: [   50.911563] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 22 15:34:48 doinkz-desktop kernel: [   50.953781] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 22 15:34:48 doinkz-desktop kernel: [   51.004405] Linux agpgart interface v0.102
Jun 22 15:34:48 doinkz-desktop kernel: [   51.048378] agpgart: Detected SiS chipset - id:1608
Jun 22 15:34:48 doinkz-desktop kernel: [   51.053631] agpgart: AGP aperture is 64M @ 0xe0000000
Jun 22 15:34:48 doinkz-desktop kernel: [   51.148799] gameport: EMU10K1 is pci0000:00:0d.1/gameport0, io 0xe000, speed 1147kHz
Jun 22 15:34:48 doinkz-desktop kernel: [   51.192192] input: PC Speaker as /devices/platform/pcspkr/input/input1
Jun 22 15:34:48 doinkz-desktop kernel: [   51.264834] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1400
Jun 22 15:34:48 doinkz-desktop kernel: [   51.510812] input: Power Button (FF) as /devices/virtual/input/input2
Jun 22 15:34:48 doinkz-desktop kernel: [   51.527557] ACPI: Power Button (FF) [PWRF]
Jun 22 15:34:48 doinkz-desktop kernel: [   51.527857] input: Power Button (CM) as /devices/virtual/input/input3
Jun 22 15:34:48 doinkz-desktop kernel: [   51.539546] ACPI: Power Button (CM) [PWRB]
Jun 22 15:34:48 doinkz-desktop kernel: [   51.539703] input: Sleep Button (CM) as /devices/virtual/input/input4
Jun 22 15:34:48 doinkz-desktop kernel: [   51.555529] ACPI: Sleep Button (CM) [FUTS]
Jun 22 15:34:48 doinkz-desktop kernel: [   52.420411] parport_pc 00:0a: reported by Plug and Play ACPI
Jun 22 15:34:48 doinkz-desktop kernel: [   52.420460] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 22 15:34:48 doinkz-desktop kernel: [   53.669987] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 21
Jun 22 15:34:48 doinkz-desktop kernel: [   53.923998] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Jun 22 15:34:48 doinkz-desktop kernel: [   54.331372] usb 4-5: reset high speed USB device using ehci_hcd and address 4
Jun 22 15:34:48 doinkz-desktop kernel: [   54.487475] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded
Jun 22 15:34:48 doinkz-desktop kernel: [   54.712777] wlan0: ethernet device 00:12:17:a0:a6:10 using NDIS driver: wusb54gs, version: 0x33c0d03, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:000E.F.conf
Jun 22 15:34:48 doinkz-desktop kernel: [   54.746750] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Jun 22 15:34:48 doinkz-desktop kernel: [   54.754786] usbcore: registered new interface driver ndiswrapper
Jun 22 15:34:48 doinkz-desktop kernel: [   54.755003] usbcore: registered new interface driver hiddev
Jun 22 15:34:48 doinkz-desktop kernel: [   54.761398] input: Razer Razer 1600dpi 3 button optical mouse as /devices/pci0000:00/0000:00:03.2/usb3/3-1/3-1:1.0/input/input5
Jun 22 15:34:48 doinkz-desktop kernel: [   54.790860] input,hidraw0: USB HID v1.10 Mouse [Razer Razer 1600dpi 3 button optical mouse] on usb-0000:00:03.2-1
Jun 22 15:34:48 doinkz-desktop kernel: [   54.796492] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:03.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input6
Jun 22 15:34:48 doinkz-desktop kernel: [   54.822734] input,hidraw1: USB HID v1.10 Keyboard [Logitech Logitech Gaming Keyboard] on usb-0000:00:03.0-1.1
Jun 22 15:34:48 doinkz-desktop kernel: [   54.835110] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:03.0/usb1/1-1/1-1.1/1-1.1:1.1/input/input7
Jun 22 15:34:48 doinkz-desktop kernel: [   54.862704] input,hiddev96,hidraw2: USB HID v1.10 Device [Logitech Logitech Gaming Keyboard] on usb-0000:00:03.0-1.1
Jun 22 15:34:48 doinkz-desktop kernel: [   54.872083] input: G15 Keyboard G15 Keyboard as /devices/pci0000:00/0000:00:03.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input8
Jun 22 15:34:48 doinkz-desktop kernel: [   54.902634] input,hiddev97,hidraw3: USB HID v1.11 Keypad [G15 Keyboard G15 Keyboard] on usb-0000:00:03.0-1.4
Jun 22 15:34:48 doinkz-desktop kernel: [   54.902660] usbcore: registered new interface driver usbhid
Jun 22 15:34:48 doinkz-desktop kernel: [   54.902665] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jun 22 15:34:48 doinkz-desktop kernel: [   56.481428] lp0: using parport0 (interrupt-driven).
Jun 22 15:34:48 doinkz-desktop kernel: [   57.120749] EXT3 FS on loop0, internal journal
Jun 22 15:34:48 doinkz-desktop kernel: [   57.330787] NET: Registered protocol family 17
Jun 22 15:34:48 doinkz-desktop kernel: [   72.685972] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:2 across:36231456k
Jun 22 15:34:48 doinkz-desktop kernel: [   73.106402] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 22 15:34:48 doinkz-desktop kernel: [   73.629570] No dock devices found.
Jun 22 15:34:48 doinkz-desktop NetworkManager: <info>  starting... 
Jun 22 15:34:48 doinkz-desktop avahi-daemon[4882]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jun 22 15:34:48 doinkz-desktop avahi-daemon[4882]: Successfully dropped root privileges.
Jun 22 15:34:48 doinkz-desktop avahi-daemon[4882]: avahi-daemon 0.6.22 starting up.
Jun 22 15:34:48 doinkz-desktop avahi-daemon[4882]: Successfully called chroot().
Jun 22 15:34:48 doinkz-desktop avahi-daemon[4882]: Successfully dropped remaining capabilities.
Jun 22 15:34:48 doinkz-desktop avahi-daemon[4882]: No service file found in /etc/avahi/services.
Jun 22 15:34:48 doinkz-desktop avahi-daemon[4882]: Network interface enumeration completed.
Jun 22 15:34:48 doinkz-desktop avahi-daemon[4882]: Registering HINFO record with values 'I686'/'LINUX'.
Jun 22 15:34:48 doinkz-desktop avahi-daemon[4882]: Server startup complete. Host name is doinkz-desktop.local. Local service cookie is 2279523459.
Jun 22 15:34:48 doinkz-desktop kernel: [   74.726134] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jun 22 15:34:48 doinkz-desktop kernel: [   74.726140] apm: overridden by ACPI.
Jun 22 15:34:48 doinkz-desktop kernel: [   74.861746] ppdev: user-space parallel port driver
Jun 22 15:34:48 doinkz-desktop kernel: [   74.986245] audit(1214120088.615:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4922 profile="/usr/sbin/cupsd" namespace="default"
Jun 22 15:34:48 doinkz-desktop dhcdbd: Started up.
Jun 22 15:34:51 doinkz-desktop hcid[5153]: Bluetooth HCI daemon
Jun 22 15:34:51 doinkz-desktop kernel: [   77.725599] eth0: link down
Jun 22 15:34:51 doinkz-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'via-rhine'. 
Jun 22 15:34:51 doinkz-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jun 22 15:34:51 doinkz-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jun 22 15:34:51 doinkz-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jun 22 15:34:51 doinkz-desktop NetworkManager: <info>  Deactivating device eth0. 
Jun 22 15:34:51 doinkz-desktop kernel: [   77.780065] Bluetooth: Core ver 2.11
Jun 22 15:34:51 doinkz-desktop kernel: [   77.783605] NET: Registered protocol family 31
Jun 22 15:34:51 doinkz-desktop kernel: [   77.783611] Bluetooth: HCI device and connection manager initialized
Jun 22 15:34:51 doinkz-desktop kernel: [   77.783616] Bluetooth: HCI socket layer initialized
Jun 22 15:34:51 doinkz-desktop hcid[5153]: Starting SDP server
Jun 22 15:34:51 doinkz-desktop kernel: [   77.812314] Bluetooth: L2CAP ver 2.9
Jun 22 15:34:51 doinkz-desktop kernel: [   77.812320] Bluetooth: L2CAP socket layer initialized
Jun 22 15:34:51 doinkz-desktop hcid[5153]: Created local server at unix:abstract=/var/run/dbus-RV9w6NXBwA,guid=3999f628c2a6cf88532a957c485e009b
Jun 22 15:34:51 doinkz-desktop input[5181]: Bluetooth Input daemon
Jun 22 15:34:51 doinkz-desktop input[5181]: Registered input manager path:/org/bluez/input
Jun 22 15:34:51 doinkz-desktop audio[5187]: Bluetooth Audio daemon
Jun 22 15:34:51 doinkz-desktop audio[5187]: Unix socket created: 5
Jun 22 15:34:51 doinkz-desktop audio[5187]: audio.conf: Key file does not have key 'Enable'
Jun 22 15:34:51 doinkz-desktop audio[5187]: audio.conf: Key file does not have key 'Disable'
Jun 22 15:34:51 doinkz-desktop NetworkManager: <debug> [1214120091.530724] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jun 22 15:34:51 doinkz-desktop kernel: [   77.896786] Bluetooth: RFCOMM socket layer initialized
Jun 22 15:34:51 doinkz-desktop kernel: [   77.896807] Bluetooth: RFCOMM TTY layer initialized
Jun 22 15:34:51 doinkz-desktop kernel: [   77.896810] Bluetooth: RFCOMM ver 1.8
Jun 22 15:34:51 doinkz-desktop audio[5187]: add_service_record: got record id 0x10000
Jun 22 15:34:51 doinkz-desktop audio[5187]: audio.conf: Key file does not have key 'Disable'
Jun 22 15:34:51 doinkz-desktop audio[5187]: audio.conf: Key file does not have group 'A2DP'
Jun 22 15:34:51 doinkz-desktop last message repeated 3 times
Jun 22 15:34:51 doinkz-desktop audio[5187]: SEP 0x806d308 registered: type:0 codec:0 seid:1
Jun 22 15:34:51 doinkz-desktop audio[5187]: add_service_record: got record id 0x10001
Jun 22 15:34:51 doinkz-desktop audio[5187]: add_service_record: got record id 0x10002
Jun 22 15:34:51 doinkz-desktop audio[5187]: add_service_record: got record id 0x10003
Jun 22 15:34:51 doinkz-desktop audio[5187]: Registered manager path:/org/bluez/audio
Jun 22 15:34:53 doinkz-desktop anacron[5269]: Anacron 2.3 started on 2008-06-22
Jun 22 15:34:53 doinkz-desktop anacron[5269]: Normal exit (0 jobs run)
Jun 22 15:34:53 doinkz-desktop /usr/sbin/cron[5298]: (CRON) INFO (pidfile fd = 3)
Jun 22 15:34:53 doinkz-desktop /usr/sbin/cron[5299]: (CRON) STARTUP (fork ok)
Jun 22 15:34:53 doinkz-desktop /usr/sbin/cron[5299]: (CRON) INFO (Running @reboot jobs)
Jun 22 15:34:57 doinkz-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jun 22 15:35:03 doinkz-desktop dhclient: No DHCPOFFERS received.
Jun 22 15:35:03 doinkz-desktop dhclient: No working leases in persistent database - sleeping.
Jun 22 15:35:03 doinkz-desktop avahi-autoipd(wlan0)[5461]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jun 22 15:35:03 doinkz-desktop avahi-autoipd(wlan0)[5461]: Successfully called chroot().
Jun 22 15:35:03 doinkz-desktop avahi-autoipd(wlan0)[5461]: Successfully dropped root privileges.
Jun 22 15:35:03 doinkz-desktop avahi-autoipd(wlan0)[5461]: Starting with address 169.254.5.9
Jun 22 15:35:03 doinkz-desktop kernel: [   90.014997] NET: Registered protocol family 10
Jun 22 15:35:03 doinkz-desktop kernel: [   90.016031] lo: Disabled Privacy Extensions
Jun 22 15:35:03 doinkz-desktop kernel: [   90.017167] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 22 15:35:03 doinkz-desktop kernel: [   90.018173] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 22 15:35:06 doinkz-desktop hcid[5153]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Jun 22 15:35:06 doinkz-desktop hcid[5153]: Default authorization agent (:1.18, /org/bluez/auth) registered
Jun 22 15:35:08 doinkz-desktop avahi-autoipd(wlan0)[5461]: Callout BIND, address 169.254.5.9 on interface wlan0
Jun 22 15:35:08 doinkz-desktop avahi-daemon[4882]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.9.
Jun 22 15:35:08 doinkz-desktop avahi-daemon[4882]: New relevant interface wlan0.IPv4 for mDNS.
Jun 22 15:35:08 doinkz-desktop avahi-daemon[4882]: Registering new address record for 169.254.5.9 on wlan0.IPv4.
Jun 22 15:35:10 doinkz-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Jun 22 15:35:10 doinkz-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun 22 15:35:12 doinkz-desktop avahi-autoipd(wlan0)[5461]: Successfully claimed IP address 169.254.5.9
Jun 22 15:35:12 doinkz-desktop kernel: [   98.960803] UDF-fs: No VRS found
Jun 22 15:35:12 doinkz-desktop kernel: [   98.969997] ISO 9660 Extensions: Microsoft Joliet Level 3
Jun 22 15:35:12 doinkz-desktop kernel: [   99.023320] ISO 9660 Extensions: RRIP_1991A
Jun 22 15:36:09 doinkz-desktop ntpdate[5612]: can't find host ntp.ubuntu.com 
Jun 22 15:36:09 doinkz-desktop ntpdate[5612]: no servers can be used, exiting
doinkz@doinkz-desktop:~$

---

### Post by pokipoki08 on 2008-06-22
Check for ndiswrapper availability
```
dmesg | grep ndiswrapper
```

Check for wifi interface
```
dmesg | grep wlan
```

Displays your interface config
```
cat /etc/network/interfaces
```

Activate your wifi interface (replace X with your interface integer)
```
sudo ifconfig wlanX up
```

Scan available wireless networks
```
iwlist wlanX scan
```

Sometimes, you need to plugin the USB wifi card AFTER you login, in order for it to be detected.

Check status of all network interfaces
```
ifconfig
```

If your wifi interface does not have an IP address, request for one with this command
```
sudo dhclient wlanX
```

Are you trying to connect to an open/restricted network? Is it WEP/WPA?

---

### Post by Bradwerkz on 2008-06-22
> **pokipoki08 said:**
> Check for ndiswrapper availability
```
dmesg | grep ndiswrapper
```

Check for wifi interface
```
dmesg | grep wlan
```

Displays your interface config
```
cat /etc/network/interfaces
```

Activate your wifi interface (replace X with your interface integer)
```
sudo ifconfig wlanX up
```

Scan available wireless networks
```
iwlist wlanX scan
```

Sometimes, you need to plugin the USB wifi card AFTER you login, in order for it to be detected.

Check status of all network interfaces
```
ifconfig
```

If your wifi interface does not have an IP address, request for one with this command
```
sudo dhclient wlanX
```

Are you trying to connect to an open/restricted network? Is it WEP/WPA?

Cool, learned a few more commands. Im kinda new. :) Ran those commands, this is what i got.

doinkz@doinkz-desktop:~$ dmesg | grep ndiswrapper
[   48.810809] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   49.311842] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded
[   49.577089] usbcore: registered new interface driver ndiswrapper


doinkz@doinkz-desktop:~$ dmesg | grep wlan
[   49.535110] wlan0: ethernet device 00:12:17:a0:a6:10 using NDIS driver: wusb54gs, version: 0x33c0d03, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:000E.F.conf
[   49.569057] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   87.483253] ADDRCONF(NETDEV_UP): wlan0: link is not ready


doinkz@doinkz-desktop:~$ sudo ifconfig wlan0 up
doinkz@doinkz-desktop:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:E9:9C:A3
                    ESSID:"RazerPc2"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:30:0A:0E:93:AB
                    ESSID:"aztech"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1B:5B:21:27:89
                    ESSID:"kintaro"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:1A:C4:F1:84:59
                    ESSID:"2WIRE512"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:1B:5B:DE:FA:31
                    ESSID:"2WIRE732"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

doinkz@doinkz-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:2e:0a:c5:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:142192 (138.8 KB)  TX bytes:142192 (138.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:a0:a6:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:12:17:a0:a6:10  
          inet addr:169.254.5.9  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

doinkz@doinkz-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:12:17:a0:a6:10
Sending on   LPF/wlan0/00:12:17:a0:a6:10
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
doinkz@doinkz-desktop:~$

---

### Post by Bradwerkz on 2008-06-22
oh, by the way, it is WEP 128bit protected.

---

### Post by pokipoki08 on 2008-06-22
When posting, wrap your terminal output like below, [COLOR="Red"]but without the double quotes[/COLOR]

[[COLOR="Red"]"[/COLOR]code[COLOR="Red"]"[/COLOR]]
your terminal output here
[[COLOR="Red"]"[/COLOR]/code[COLOR="Red"]"[/COLOR]]

Network Manager is interfering with manual wifi connection (what we're doing here), it must be uninstalled.

```
sudo apt-get remove network-manager
```

Go to Ubuntu menu,
System -> Administration -> Network
select 'Wireless Connection' & click Properties
uncheck 'Enable this connection'

Run these commands at the terminal, one at a time
[COLOR="RoyalBlue"](change these values accordingly)[/COLOR]

```
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 essid '[COLOR="RoyalBlue"]your essid[/COLOR]'
sudo iwconfig wlan0 key s:[COLOR="RoyalBlue"]password[/COLOR] restricted
```

Post the terminal output of the commands below,

```
iwconfig wlan0
```
```
sudo dhclient wlan0
```

---

### Post by Bradwerkz on 2008-06-23
Sorry for being messy.

So i have remove the network manager and disable the network connection from the System -> Administration -> Network.

New problem arises now; dont seem to be able to scan anymore access point.

```

sudo iwconfig wlan0 key s:904EE2E5E0C9B115036BDD2E2E restricted

```

Output : Error for wireless request "Set Encode" (8B2A) :
         SET failed on device wlan0 ; Invalid argument.


```

iwconfig wlan0

```

Output : 

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  noise 
    level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Code :
```

 sudo dhclient wlan0

```

Output :

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:12:17:a0:a6:10
Sending on   LPF/wlan0/00:12:17:a0:a6:10
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I have checked the driver using ndiswrapper -l and it shows it is installed and present. 
I have tried scanning and return 0 results.

---

### Post by pokipoki08 on 2008-06-23
I believe your card is working but the [COLOR="Red"]hex password[/COLOR] you input is incorrect. Input the [COLOR="Blue"]ASCII (normal text) password[/COLOR] instead.

```
sudo iwconfig wlan0 key s:[COLOR="Red"]904EE2E5E0C9B115036BDD2E2E[/COLOR] restricted
```

```
sudo iwconfig wlan0 key s:[COLOR="Blue"]password[/COLOR] restricted
```

You are not far away from a successful connection.

Check for errors as you try these commands. Please post them here.

```
dmesg | grep ndiswrapper
```
```
dmesg | grep wlan0
```
```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
iwlist wlan0 scan
```
```

sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 essid [COLOR="Blue"]'your essid'[/COLOR]
sudo iwconfig wlan0 key s:[COLOR="Blue"]password[/COLOR] restricted
```
```
**[COLOR="Magenta"]iwconfig wlan0[/COLOR]**
```

Once you can see **[COLOR="Magenta"]iwconfig wlan0[/COLOR]** giving you the correct ESSID (the wireless network you are trying to connect to), you are ready to request for an IP address.

To request for an IP address
```
sudo dhclient wlan0
```

---

