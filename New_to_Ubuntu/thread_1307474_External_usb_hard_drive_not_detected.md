---
title: "External usb hard drive not detected"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by FredOdman on 2009-10-31
I have looked for the answer to this for some time now without much luck so I am hoping that someone here is willing to help a poor beginner. I have installed the server version 8.04 on an old tablet pc at home. I wanted to add some more space so I bought a WD 1TB NTFS drive and tried to connect it via usb. The problem I have is that I don't know if it is even detected at all and I certanly don't know what letters it might be assigned if it is there at all. When I run fdisk -l I only get three partitions, none of them showing  NTFS. When I run lsusb I get  "Bus 001 Device 001: ID 0000:0000" 

If someone would be kind enough to tell me if the drive is detected, what it is called, and how to mount it, I would be very grateful.


Here is what I get from dmesg

[   13.542169] io scheduler noop registered
[   13.542173] io scheduler anticipatory registered
[   13.542176] io scheduler deadline registered (default)
[   13.542189] io scheduler cfq registered
[   13.542237] Boot video device is 0000:01:00.0
[   13.542685] isapnp: Scanning for PnP cards...
[   13.899176] isapnp: No Plug & Play device found
[   13.939542] Real Time Clock Driver v1.12ac
[   13.939707] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.940788] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   13.940794] PCI: setting IRQ 11 as level-triggered
[   13.940799] ACPI: PCI Interrupt 0000:00:02.6[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.940813] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   13.941830] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.941947] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   13.942081] PNP: PS/2 Controller [PNP0303:KBC,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[   13.946513] i8042.c: Detected active multiplexing controller, rev 1.1.
[   13.950518] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.950526] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   13.950529] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   13.950532] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   13.950535] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   13.978047] mice: PS/2 mouse device common for all mice
[   13.978228] EISA: Probing bus 0 at eisa.0
[   13.978243] Cannot allocate resource for EISA slot 1
[   13.978278] EISA: Detected 0 cards.
[   13.978283] cpuidle: using governor ladder
[   13.978286] cpuidle: using governor menu
[   13.978512] NET: Registered protocol family 1
[   13.978561] Using IPI No-Shortcut mode
[   13.978636] registered taskstats version 1
[   13.978774]   Magic number: 13:156:200
[   13.978911]   hash matches device ttypf
[   13.979143] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   13.980255] Freeing unused kernel memory: 384k freed
[   13.984593] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   14.213239] fuse init (API version 7.9)
[   14.239972] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   14.242494] Marking TSC unstable due to: TSC halts in idle.
[   14.243859] ACPI: Thermal Zone [THZN] (64 C)
[   14.247785] Time: acpi_pm clocksource has been installed.
[   14.265515] device-mapper: uevent: version 1.0.3
[   14.265600] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   15.077875] SCSI subsystem initialized
[   15.171257] libata version 3.00 loaded.
[   15.184851] usbcore: registered new interface driver usbfs
[   15.184895] usbcore: registered new interface driver hub
[   15.217344] usbcore: registered new device driver usb
[   15.227337] sis900.c: v1.08.10 Apr. 2 2006
[   15.227472] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[   15.229478] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 2.
[   15.241900] 0000:00:04.0: Using transceiver found at address 2 as default
[   15.243079] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 7, 00:40:ca:ce:07:60
[   15.269602] pata_sis 0000:00:02.5: version 0.5.2
[   15.293264] scsi0 : pata_sis
[   15.306856] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   15.311322] scsi1 : pata_sis
[   15.312199] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[   15.312204] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[   15.647485] ata1.00: ATAPI: Slimtype COMBO SOSC-2483K, KKF1, max UDMA/33
[   15.827499] ata1.00: configured for UDMA/33
[   16.007378] ata2.00: ATA-6: IC25N060ATMR04-0, MO3OAD4A, max UDMA/100
[   16.007386] ata2.00: 117210240 sectors, multi 16: LBA48
[   16.007402] ata2.00: limited to UDMA/33 due to 40-wire cable
[   16.047329] ata2.00: configured for UDMA/33
[   16.048173] scsi 0:0:0:0: CD-ROM            Slimtype COMBO SOSC-2483K KKF1 PQ: 0 ANSI: 5
[   16.048358] scsi 1:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[   16.052263] PCI: Enabling device 0000:00:03.0 (0000 -> 0002)
[   16.052595] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   16.052600] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   16.052626] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   16.052632] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   16.053132] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   16.053157] ohci_hcd 0000:00:03.0: irq 11, io mem 0x28020000
[   16.106739] ohci_hcd 0000:00:03.0: USB HC reset timed out!
[   16.106790] ohci_hcd 0000:00:03.0: can't start
[   16.106844] ohci_hcd 0000:00:03.0: startup error -1
[   16.106888] ohci_hcd 0000:00:03.0: USB bus 1 deregistered
[   16.107004] ACPI: PCI interrupt for device 0000:00:03.0 disabled
[   16.107008] ohci_hcd 0000:00:03.0: init 0000:00:03.0 fail, -1
[   16.107057] ohci_hcd: probe of 0000:00:03.0 failed with error -1
[   16.107087] PCI: Enabling device 0000:00:03.1 (0000 -> 0002)
[   16.107405] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[   16.107410] ACPI: PCI Interrupt 0000:00:03.1[B] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[   16.107432] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   16.107437] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   16.107927] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 1
[   16.107948] ohci_hcd 0000:00:03.1: irq 11, io mem 0x28021000
[   16.166700] ohci_hcd 0000:00:03.1: USB HC reset timed out!
[   16.166745] ohci_hcd 0000:00:03.1: can't start
[   16.166792] ohci_hcd 0000:00:03.1: startup error -1
[   16.166833] ohci_hcd 0000:00:03.1: USB bus 1 deregistered
[   16.166900] ACPI: PCI interrupt for device 0000:00:03.1 disabled
[   16.166903] ohci_hcd 0000:00:03.1: init 0000:00:03.1 fail, -1
[   16.166950] ohci_hcd: probe of 0000:00:03.1 failed with error -1
[   16.167182] PCI: Enabling device 0000:00:03.2 (0000 -> 0002)
[   16.167437] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   16.167441] ACPI: PCI Interrupt 0000:00:03.2[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   16.167456] ehci_hcd 0000:00:03.2: EHCI Host Controller
[   16.167845] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 1
[   16.167902] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[   16.167914] ehci_hcd 0000:00:03.2: irq 11, io mem 0x28022000
[   16.186683] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1e.cc, driver 10 Dec 2004
[   16.186923] usb usb1: configuration #1 chosen from 1 choice
[   16.186962] hub 1-0:1.0: USB hub found
[   16.186974] hub 1-0:1.0: 0 ports detected
[   16.312116] Driver 'sd' needs updating - please use bus_type methods
[   16.314168] sd 1:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   16.314191] sd 1:0:0:0: [sda] Write Protect is off
[   16.314194] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.314222] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.314304] sd 1:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   16.314318] sd 1:0:0:0: [sda] Write Protect is off
[   16.314321] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.314341] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.314346]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   16.319635] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[   16.319648] Uniform CD-ROM driver Revision: 3.20
[   16.319743] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   16.334817]  sda1 sda2 < sda5 >
[   16.340460] sd 1:0:0:0: [sda] Attached SCSI disk
[   16.350827] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   16.350864] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   36.013207] padlock: VIA PadLock Hash Engine not detected.
[   39.993744] Attempting manual resume
[   39.993752] swsusp: Resume From Partition 254:2
[   39.993754] PM: Checking swsusp image.
[   39.994196] PM: Resume from disk failed.
[   40.071862] EXT3-fs: INFO: recovery required on readonly filesystem.
[   40.071874] EXT3-fs: write access will be enabled during recovery.
[   45.874552] kjournald starting.  Commit interval 5 seconds
[   45.874594] EXT3-fs: dm-1: orphan cleanup on readonly fs
[   45.874608] ext3_orphan_cleanup: deleting unreferenced inode 163857
[   45.893436] EXT3-fs: dm-1: 1 orphan inode deleted
[   45.893439] EXT3-fs: recovery complete.
[   45.958003] EXT3-fs: mounted filesystem with ordered data mode.
[   52.493860] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   53.493135] Linux agpgart interface v0.102
[   53.823015] Yenta: CardBus bridge found at 0000:00:0c.0 [1524:1410]
[   53.823047] Yenta: Enabling burst memory read transactions
[   53.823053] Yenta: Using CSCINT to route CSC interrupts to PCI
[   53.823056] Yenta: Routing CardBus interrupts to PCI
[   53.823061] Yenta TI: socket 0000:00:0c.0, mfunc 0x01021002, devctl 0x44
[   53.932799] Yenta TI: socket 0000:00:0c.0 probing PCI interrupt failed, trying to fix
[   53.999974] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   54.042705] Yenta TI: socket 0000:00:0c.0 no PCI interrupts. Fish. Please report.
[   54.042720] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[   54.042722] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   54.183287] Yenta: ISA IRQ mask 0x0000, PCI irq 0
[   54.183295] Socket status: 16cca3b2
[   54.232936] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   54.422611] agpgart: Detected SiS chipset - id:1857
[   54.426314] agpgart: AGP aperture is 32M @ 0xf0000000
[   54.477419] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1400
[   54.512718] input: Power Button (FF) as /devices/virtual/input/input3
[   54.592536] ACPI: Power Button (FF) [PWRF]
[   54.592646] input: Power Button (CM) as /devices/virtual/input/input4
[   54.672430] ACPI: Power Button (CM) [PBTN]
[   54.672543] input: Lid Switch as /devices/virtual/input/input5
[   54.714262] ACPI: Lid Switch [LID]
[   54.714397] input: Sleep Button (CM) as /devices/virtual/input/input6
[   54.792342] ACPI: Sleep Button (CM) [SLPB]
[   54.799011] ACPI: AC Adapter [AC] (on-line)
[   54.851820] ACPI: Battery Slot [BAT2] (battery present)
[   55.012287] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   55.861558] intel8x0_measure_ac97_clock: measured 59256 usecs
[   55.861569] intel8x0: clocking to 48000
[   55.862080] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   55.933937] phy0: Selected rate control algorithm 'simple'
[   56.057365] NET: Registered protocol family 10
[   56.125913] input: PS/2 Mouse as /devices/virtual/input/input7
[   56.181606] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio3/input/input8
[   56.492367] eth0: Media Link On 100mbps full-duplex
[   56.725407] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input9
[   56.791254] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   56.963984] lo: Disabled Privacy Extensions
[   58.894888] cs: IO port probe 0x100-0x3af: clean.
[   58.896844] cs: IO port probe 0x3e0-0x4ff: clean.
[   58.897657] cs: IO port probe 0x820-0x8ff: clean.
[   58.898370] cs: IO port probe 0xc00-0xcf7: clean.
[   58.899306] cs: IO port probe 0xa00-0xaff: clean.
[   60.012136] loop: module loaded
[   60.125825] lp: driver loaded but no devices found
[   60.702283] Adding 1449976k swap on /dev/mapper/Home-swap_1.  Priority:-1 extents:1 across:1449976k
[   61.548218] EXT3 FS on dm-1, internal journal
[   62.767032] kjournald starting.  Commit interval 5 seconds
[   62.776558] EXT3 FS on sda1, internal journal
[   62.776566] EXT3-fs: mounted filesystem with ordered data mode.
[   64.280354] ip_tables: (C) 2000-2006 Netfilter Core Team
[   67.424240] eth0: no IPv6 routers present
[94890.265168] usbcore: registered new interface driver libusual
[94890.277624] Initializing USB Mass Storage driver...
[94890.277694] usbcore: registered new interface driver usb-storage
[94890.277699] USB Mass Storage support registered.

---

### Post by humphreybc on 2009-10-31
Have you installed gparted?

```

sudo aptitude install gparted

```

Check if it shows up mounted or unmounted in Partition Editor (the combo box to the top right of the window). If it does, then that's great, if not, then we have a bit more of a problem.

Is it empty, or do you have files on there? Have you considered backing up any data, then formatting it to fat32? This plays nicer with linux than ntfs, and is still compatible with Windows, unlike ext.

Cheers

---

### Post by FredOdman on 2009-10-31
Thanks for the reply buddy. Close to three am here now so I will take a look at it tomorrow. I have no gui installed so could I run this one anyway. Is there a smaller gui than Gnome that I could install to make things simpler for me? Anyway, thanks again I'll let you know how things went at a later time. By the way, I flew the Viggen in the Swedish Air force for thirteen years so I really like your picture.

Fred

---

