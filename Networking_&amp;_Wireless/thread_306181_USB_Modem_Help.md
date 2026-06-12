---
title: "USB Modem Help"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by kitpierce on 2006-11-24
I have just done a fresh install of Xubuntu for a friend on an old IBM laptop (Celeron 366, 64 MB Memory, 5 Gig HD.)  The laptop doesn't have a ethernet port, so I am trying to set up internet using the USB port so I can download the latest updates and a couple extra programs.  I have a cable modem with USB and I know it works because I use it with my own computers all the time.  But for some reason I can't get the laptop to access it.  During the install process, I skipped DHCP setup because the laptop wasn't plugged in at the time.  Would doing setup again help any?  If so, how would I got about doing this?  When I run dmesg I get the following output:

[INDENT]hector@xubuntu:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000003ff0000 (usable)
[17179569.184000]  BIOS-e820: 0000000003ff0000 - 0000000003ff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000003ff8000 - 0000000004000000 (ACPI NVS)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 63MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 16368
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 12272 pages, LIFO batch:1
[17179569.184000] DMI not present or invalid.
[17179569.184000] ACPI: RSDP (v000 IBM                                   ) @ 0x000fe030
[17179569.184000] ACPI: RSDT (v001 IBM    Hammer   0x00000001 IBM  0x00000000) @ 0x03ff0000
[17179569.184000] ACPI: FADT (v001 IBM    Hammer   0x00000001 IBM  0x00000000) @ 0x03ff0054
[17179569.184000] ACPI: BOOT (v001 IBM    Hammer   0x00000001 IBM  0x00000000) @ 0x03ff002c
[17179569.184000] ACPI: DSDT (v001   Acer   AN510  0x00001000 MSFT 0x0100000a) @ 0x00000000
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 04000000:fc000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01089000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 256 (order: 8, 1024 bytes)
[    0.000000] Detected 365.955 MHz processor.
[   17.390885] Using tsc for high-res timesource
[   17.392958] Console: colour VGA+ 80x25
[   17.393408] Dentry cache hash table entries: 8192 (order: 3, 32768 bytes)
[   17.393650] Inode-cache hash table entries: 4096 (order: 2, 16384 bytes)
[   17.408381] Memory: 55400k/65472k available (1910k kernel code, 9664k reserved, 1070k data, 308k init, 0k highmem)
[   17.408406] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.486645] Calibrating delay using timer specific routine.. 733.01 BogoMIPS (lpj=1466025)
[   17.486863] Security Framework v1.0.0 initialized
[   17.486909] SELinux:  Disabled at boot.
[   17.486995] Mount-cache hash table entries: 512
[   17.487728] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   17.487777] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   17.487830] CPU: L1 I cache: 16K, L1 D cache: 16K
[   17.487845] CPU: L2 cache: 128K
[   17.487862] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   17.487973] Checking 'hlt' instruction... OK.
[   17.502783] SMP alternatives: switching to UP code
[   17.503844] Freeing SMP alternatives: 16k freed
[   17.504859] checking if image is initramfs... it is
[   20.217200] Freeing initrd memory: 5318k freed
[   20.217262] CPU0: Intel Celeron (Mendocino) stepping 0a
[   20.217302] SMP motherboard not detected.
[   20.217318] Local APIC not detected. Using dummy APIC emulation.
[   20.218004] Brought up 1 CPUs
[   20.218165] migration_cost=0
[   20.220317] NET: Registered protocol family 16
[   20.220559] EISA bus registered
[   20.238066] PCI: PCI BIOS revision 2.10 entry at 0xf0200, last bus=1
[   20.238099] PCI: Using configuration type 1
[   20.238110] Setting up standard PCI resources
[   20.240212] ACPI: Interpreter disabled.
[   20.240243] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.240321] pnp: PnP ACPI: disabled
[   20.240337] PnPBIOS: Scanning system for PnP BIOS support...
[   20.240488] PnPBIOS: Found PnP BIOS installation structure at 0xc00f62d0
[   20.240508] PnPBIOS: PnP BIOS version 1.0, entry 0xfa000:0x0, dseg 0xf0000
[   20.250566] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   20.250948] PCI: Probing PCI hardware
[   20.250969] PCI: Probing PCI hardware (bus 00)
[   20.251903] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.0
[   20.252011] PCI quirk: region 6c20-6c3f claimed by ali7101 SMB
[   20.252612] Boot video device is 0000:01:00.0
[   20.278084] pnp: 00:08: ioport range 0x1060-0x106f has been reserved
[   20.278114] pnp: 00:08: ioport range 0xf100-0xf13f has been reserved
[   20.278131] pnp: 00:08: ioport range 0xf140-0xf15f has been reserved
[   20.279694] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[   20.279718] PCI: Bridge: 0000:00:01.0
[   20.279727]   IO window: disabled.
[   20.279745]   MEM window: 80500000-80cfffff
[   20.279762]   PREFETCH window: 80d00000-820fffff
[   20.279781] PCI: Bus 2, cardbus bridge: 0000:00:13.0
[   20.279794]   IO window: 00001400-000014ff
[   20.279809]   IO window: 00001800-000018ff
[   20.279825]   PREFETCH window: 10000000-11ffffff
[   20.279841]   MEM window: 12000000-13ffffff
[   20.279855] PCI: Bus 6, cardbus bridge: 0000:00:13.1
[   20.279868]   IO window: 00001c00-00001cff
[   20.279882]   IO window: 00002000-000020ff
[   20.279897]   PREFETCH window: 14000000-15ffffff
[   20.279913]   MEM window: 16000000-17ffffff
[   20.279952] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.279994] PCI: Guessed IRQ 9 for device 0000:00:13.0
[   20.280028] PCI: Sharing IRQ 9 with 0000:00:13.1
[   20.280065] PCI: Guessed IRQ 9 for device 0000:00:13.1
[   20.280094] PCI: Sharing IRQ 9 with 0000:00:13.0
[   20.280284] NET: Registered protocol family 2
[   20.317988] IP route cache hash table entries: 512 (order: -1, 2048 bytes)
[   20.318640] TCP established hash table entries: 2048 (order: 2, 16384 bytes)
[   20.318797] TCP bind hash table entries: 1024 (order: 1, 8192 bytes)
[   20.318874] TCP: Hash tables configured (established 2048 bind 1024)
[   20.318890] TCP reno registered
[   20.320182] Simple Boot Flag at 0x6e set to 0x1
[   20.323989] audit: initializing netlink socket (disabled)
[   20.324079] audit(1164397364.108:1): initialized
[   20.325046] VFS: Disk quotas dquot_6.5.1
[   20.325168] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.325600] Initializing Cryptographic API
[   20.325634] io scheduler noop registered
[   20.325674] io scheduler anticipatory registered
[   20.325721] io scheduler deadline registered
[   20.325793] io scheduler cfq registered (default)
[   20.325836] Activating ISA DMA hang workarounds.
[   20.327454] isapnp: Scanning for PnP cards...
[   20.691524] isapnp: No Plug & Play device found
[   20.991947] Real Time Clock Driver v1.12ac
[   20.992374] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.992904] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.999235] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.001146] mice: PS/2 mouse device common for all mice
[   21.005828] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.006741] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.006774] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.007957] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   21.010344] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.010530] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.011842] EISA: Probing bus 0 at eisa.0
[   21.011888] Cannot allocate resource for EISA slot 1
[   21.011903] Cannot allocate resource for EISA slot 2
[   21.011948] Cannot allocate resource for EISA slot 6
[   21.011960] Cannot allocate resource for EISA slot 7
[   21.011985] EISA: Detected 0 cards.
[   21.012525] TCP bic registered
[   21.012571] NET: Registered protocol family 1
[   21.012607] NET: Registered protocol family 8
[   21.012620] NET: Registered protocol family 20
[   21.012748] Using IPI No-Shortcut mode
[   21.016721] Freeing unused kernel memory: 308k freed
[   21.047624] input: AT Translated Set 2 keyboard as /class/input/input0
[   21.432269] Capability LSM initialized
[   25.068835] ALI15X3: IDE controller at PCI slot 0000:00:0f.0
[   25.068933] ALI15X3: chipset revision 32
[   25.068946] ALI15X3: not 100% native mode: will probe irqs later
[   25.069017]     ide0: BM-DMA at 0x78c0-0x78c7, BIOS settings: hda:DMA, hdb:pio
[   25.069088]     ide1: BM-DMA at 0x78c8-0x78cf, BIOS settings: hdc:DMA, hdd:pio
[   25.069134] Probing IDE interface ide0...
[   25.355628] hda: IBM-DBCA-204860, ATA DISK drive
[   26.027662] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   26.029007] Probing IDE interface ide1...
[   26.763047] hdc: CRN-8241B, ATAPI CD/DVD-ROM drive
[   27.098858] ide1 at 0x170-0x177,0x376 on irq 15
[   27.170659] hda: max request size: 128KiB
[   27.224549] hda: 9514260 sectors (4871 MB) w/420KiB Cache, CHS=10068/15/63, (U)DMA
[   27.224590] hda: cache flushes not supported
[   27.224830]  hda: hda1 hda2 < hda5 >
[   27.341057] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[   27.341102] Uniform CD-ROM driver Revision: 3.20
[   28.137483] usbcore: registered new driver usbfs
[   28.137656] usbcore: registered new driver hub
[   28.145111] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   28.145317] ohci_hcd 0000:00:14.0: OHCI Host Controller
[   28.145912] ohci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[   28.146003] ohci_hcd 0000:00:14.0: irq 10, io mem 0x82100000
[   28.253171] usb usb1: configuration #1 chosen from 1 choice
[   28.254353] hub 1-0:1.0: USB hub found
[   28.254462] hub 1-0:1.0: 2 ports detected
[   28.546050] Attempting manual resume
[   28.670205] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   28.690290] kjournald starting.  Commit interval 5 seconds
[   28.690384] EXT3-fs: mounted filesystem with ordered data mode.
[   28.885683] usb 1-1: configuration #1 chosen from 1 choice
[   57.518873] PCI: Guessed IRQ 9 for device 0000:00:13.0
[   57.518927] PCI: Sharing IRQ 9 with 0000:00:13.1
[   57.518978] Yenta: CardBus bridge found at 0000:00:13.0 [1025:1002]
[   57.519015] Yenta O2: res at 0x94/0xD4: ea/00
[   57.519027] Yenta O2: old bridge, disabling read prefetch/write burst
[   57.548215] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   57.655977] Linux agpgart interface v0.101 (c) Dave Jones
[   57.658518] Yenta: ISA IRQ mask 0x08b8, PCI irq 9
[   57.658538] Socket status: 30000411
[   57.723684] PCI: Guessed IRQ 9 for device 0000:00:13.1
[   57.723731] PCI: Sharing IRQ 9 with 0000:00:13.0
[   57.723802] Yenta: CardBus bridge found at 0000:00:13.1 [1025:1002]
[   57.851417] Yenta: ISA IRQ mask 0x08b8, PCI irq 9
[   57.851437] Socket status: 30000007
[   57.922421] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   57.924846] agpgart: Detected ALi M???? chipset
[   57.933365] agpgart: AGP aperture is 64M @ 0xe0000000
[   57.936047] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   57.936171] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[   57.997910] ali1535_smbus 0000:00:11.0: SMB device not enabled - upgrade BIOS?
[   57.998018] ali1535_smbus 0000:00:11.0: ALI1535 not detected, module not inserted.
[   58.917905] pccard: PCMCIA card inserted into slot 0
[   60.108861] input: PC Speaker as /class/input/input1
[   60.874937] Floppy drive(s): fd0 is 1.44M
[   60.891521] FDC 0 is a National Semiconductor PC87306
[   61.831877] parport: PnPBIOS parport detected.
[   61.831988] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   62.338824] IBM TrackPoint firmware: 0x0b, buttons: 3/3
[   62.355418] input: TPPS/2 IBM TrackPoint as /class/input/input2
[   63.592138] eth0: register 'cdc_ether' at usb-0000:00:14.0-1, CDC Ethernet Device, 00:16:cf:22:e8:6f
[   63.592212] usbcore: registered new driver cdc_ether
[   63.853661] cs: IO port probe 0x100-0x3af: clean.
[   63.857767] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   63.859372] cs: IO port probe 0x820-0x8ff: clean.
[   63.860898] cs: IO port probe 0xc00-0xcf7: clean.
[   63.862978] cs: IO port probe 0xa00-0xaff: clean.
[   64.069366] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   64.091298] pcmcia: registering new device pcmcia0.0
[   64.094715] cs: IO port probe 0x100-0x3af: clean.
[   64.099020] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   64.100705] cs: IO port probe 0x820-0x8ff: clean.
[   64.102171] cs: IO port probe 0xc00-0xcf7: clean.
[   64.104370] cs: IO port probe 0xa00-0xaff: clean.
[   64.190406] ts: Compaq touchscreen protocol output
[   64.365140] PCI: Guessed IRQ 5 for device 0000:00:08.0
[   64.384029] gameport: ES1938 is pci0000:00:08.0/gameport0, io 0x78a4, speed 1065kHz
[   65.790860]   ASIC rev 1,<6>eth0: Megahertz 574B at io 0x300, irq 3, hw_addr 00:00:86:5B:B0:C8.
[   65.802037]  64K FIFO split 1:1 Rx:Tx, autoselect MII interface.
[   66.315139] lp0: using parport0 (interrupt-driven).
[   66.514017] Adding 176672k swap on /dev/disk/by-uuid/3e26af92-29c3-48fd-b148-b1d91cdf72bf.  Priority:-1 extents:1 across:176672k
[   66.716942] EXT3 FS on hda1, internal journal
[   86.477502] apm: BIOS version 1.2 Flags 0x0f (Driver version 1.16ac)
[  170.351273] NET: Registered protocol family 10
[  170.351896] lo: Disabled Privacy Extensions
[  170.352385] IPv6 over IPv4 tunneling driver
[  315.569905] usb 1-1: USB disconnect, address 2
[  315.570090] eth1: unregister 'cdc_ether' usb-0000:00:14.0-1, CDC Ethernet Device
[  656.825361] ohci_hcd 0000:00:14.0: wakeup
[  657.219090] usb 1-1: new full speed USB device using ohci_hcd and address 3
[  657.435469] usb 1-1: configuration #1 chosen from 1 choice
[  657.447758] eth1: register 'cdc_ether' at usb-0000:00:14.0-1, CDC Ethernet Device, 00:16:cf:22:e8:6f
[  657.659196] usb 1-1: USB disconnect, address 3
[  657.659401] eth1: unregister 'cdc_ether' usb-0000:00:14.0-1, CDC Ethernet Device
[  668.039388] ohci_hcd 0000:00:14.0: wakeup
[  668.422771] usb 1-1: new full speed USB device using ohci_hcd and address 4
[  669.042673] usb 1-1: configuration #1 chosen from 1 choice
[  669.064777] eth1: register 'cdc_ether' at usb-0000:00:14.0-1, CDC Ethernet Device, 00:16:cf:22:e8:6f
[/INDENT]

I am comfortable with the terminal, so any help would be most appreciated.  Thanks!

---

### Post by kitpierce on 2006-11-24
...anybody...?

---

### Post by marianlibrarian on 2006-11-27
I also tried and failed at setting up a usb connection to a netopia dsl modem on an old desktop. I am going today to get an ethernet card and go that route. There is alot more help on ethernet than usb. I don't know what to tell you regarding a laptop.

---

### Post by kitpierce on 2006-11-27
That's kind of the feeling I was getting as I searched the forums and google.  The laptop is due back later today, so looks like the time has passed, but thanks for dropping a note.  :D

---

### Post by marianlibrarian on 2006-12-03
USB Modems are pretty much impossible with Ubuntu. So I went to Walmart and bought a cheap Linksys ethernet network card for 14 dollars. I basically plugged it in and turned on the machine and that was it. I highly recommend going with ethernet and not USB.

---

### Post by steven8 on 2006-12-08
They are not useless at all in Dapper, gNewSense and Freespire.  My Toshiba PCX 2600 USB Cable modem worked ootb with these three distros, but not with Edgy, Feisty Fawn Herd 1 or any other distros I've tried.  I do not know what has been changed in Ubuntu with Edgy and Feisty, but it worked in Dapper.

---

