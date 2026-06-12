---
title: "ubuntu tv card question"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by Trinity33 on 2010-03-05
hi im new to ubuntu use karmic with 2.6.31.14 generic kernel. to be honest i really like it everything is working perfect till now. what i want to do is remove win7 from my laptop so to do that i need to make my tv card working in karmic with mythtv or any other player. i got hauppauge wintv nova-s usb2. and its working perfect in win7 can watch satellite tv channels without any problem. cos i use karmic almost in 99% of the time so difficult is to when u want to watch tv change to windows and then boot up karmic again. 

first thing i did was to ask about my card on mythtv-user and linuxtv irc channel and so i got the answer trin your card will work with v4l-dvb. so i was happy  for a sec. downloaded the last driver using git. then wanted to install it and the truble started there is still a bug firedtv so i had to dissable it no problem. to get that driver installed i needed 3 days. doesnt, matter its installed now. today i wanted to test my card if its working so i conneted nova-s usb2 and dmseg out put was : 

[    0.972603] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.972814] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.973112] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.028155] ACPI: AC Adapter [ACAD] (on-line)
[    1.028312] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.028321] ACPI: Power Button [PWRF]
[    1.028443] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.028533] ACPI: Lid Switch [LID]
[    1.028654] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.028662] ACPI: Sleep Button [SLPB]
[    1.028773] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.028780] ACPI: Power Button [PWRB]
[    1.030279] ACPI: SSDT 7f685eda 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    1.031436] ACPI: SSDT 7f685993 004C2 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    1.037049] Marking TSC unstable due to TSC halts in idle
[    1.037091] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.037155] processor LNXCPU:00: registered as cooling_device0
[    1.037166] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.037995] ACPI: SSDT 7f686112 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    1.038864] ACPI: SSDT 7f685e55 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    1.040663] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.040725] processor LNXCPU:01: registered as cooling_device1
[    1.040735] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.228135] thermal LNXTHERM:01: registered as thermal_zone0
[    1.228157] ACPI: Thermal Zone [TZ00] (30 C)
[    1.340134] thermal LNXTHERM:02: registered as thermal_zone1
[    1.340155] ACPI: Thermal Zone [TZ01] (30 C)
[    1.340306] isapnp: Scanning for PnP cards...
[    1.694755] isapnp: No Plug & Play device found
[    2.596215] ACPI: Battery Slot [BAT1] (battery present)
[    2.596502] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.599830] brd: module loaded
[    2.601043] loop: module loaded
[    2.601239] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.601523] ata_piix 0000:00:1f.2: version 2.13
[    2.601555] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.601567] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.756045] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.756200] scsi0 : ata_piix
[    2.756407] scsi1 : ata_piix
[    2.758661] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x5440 irq 14
[    2.758670] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x5448 irq 15
[    2.761037] Fixed MDIO Bus: probed
[    2.761127] PPP generic driver version 2.4.2
[    2.761357] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.761401]   alloc irq_desc for 23 on node -1
[    2.761407]   alloc kstat_irqs on node -1
[    2.761421] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.761447] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.761456] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.761565] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.765506] ehci_hcd 0000:00:1d.7: debug port 1
[    2.765519] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.765549] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0444000
[    2.780042] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.780216] usb usb1: configuration #1 chosen from 1 choice
[    2.780290] hub 1-0:1.0: USB hub found
[    2.780307] hub 1-0:1.0: 8 ports detected
[    2.780461] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.780504] uhci_hcd: USB Universal Host Controller Interface driver
[    2.780566] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.780581] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.780590] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.780671] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.780713] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000050a0
[    2.780897] usb usb2: configuration #1 chosen from 1 choice
[    2.780967] hub 2-0:1.0: USB hub found
[    2.780982] hub 2-0:1.0: 2 ports detected
[    2.781109] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.781123] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.781131] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.781221] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.781281] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000050c0
[    2.781465] usb usb3: configuration #1 chosen from 1 choice
[    2.781534] hub 3-0:1.0: USB hub found
[    2.781550] hub 3-0:1.0: 2 ports detected
[    2.781660] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.781674] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.781682] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.781759] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.781811] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000050e0
[    2.781997] usb usb4: configuration #1 chosen from 1 choice
[    2.782065] hub 4-0:1.0: USB hub found
[    2.782080] hub 4-0:1.0: 2 ports detected
[    2.782188] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.782202] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.782210] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.782284] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.782337] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00005400
[    2.782520] usb usb5: configuration #1 chosen from 1 choice
[    2.782589] hub 5-0:1.0: USB hub found
[    2.782605] hub 5-0:1.0: 2 ports detected
[    2.782843] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    2.783281] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.783388] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.783402] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.783410] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.783419] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.783427] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.783599] mice: PS/2 mouse device common for all mice
[    2.783938] rtc_cmos 00:07: RTC can wake from S4
[    2.784047] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.784097] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.784392] device-mapper: uevent: version 1.0.3
[    2.784626] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.784776] device-mapper: multipath: version 1.1.0 loaded
[    2.784782] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.785082] EISA: Probing bus 0 at eisa.0
[    2.785094] Cannot allocate resource for EISA slot 1
[    2.785100] Cannot allocate resource for EISA slot 2
[    2.785117] Cannot allocate resource for EISA slot 5
[    2.785140] EISA: Detected 0 cards.
[    2.785558] cpuidle: using governor ladder
[    2.785878] cpuidle: using governor menu
[    2.786539] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.787228] TCP cubic registered
[    2.787641] NET: Registered protocol family 10
[    2.788794] lo: Disabled Privacy Extensions
[    2.789662] NET: Registered protocol family 17
[    2.789703] Bluetooth: L2CAP ver 2.13
[    2.789708] Bluetooth: L2CAP socket layer initialized
[    2.789716] Bluetooth: SCO (Voice Link) ver 0.6
[    2.789720] Bluetooth: SCO socket layer initialized
[    2.789817] Bluetooth: RFCOMM TTY layer initialized
[    2.789825] Bluetooth: RFCOMM socket layer initialized
[    2.789831] Bluetooth: RFCOMM ver 1.11
[    2.790675] Using IPI No-Shortcut mode
[    2.790772] PM: Resume from disk failed.
[    2.790789] registered taskstats version 1
[    2.790943]   Magic number: 2:436:141
[    2.790947]   hash matches /build/buildd/linux-2.6.31/drivers/base/power/main.c:382
[    2.790970] block ram6: hash matches
[    2.791020] acpi device:12: hash matches
[    2.791080] rtc_cmos 00:07: setting system clock to 2010-03-05 19:08:13 UTC (1267816093)
[    2.791085] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.791087] EDD information not available.
[    2.920487] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PP02, max UDMA/33
[    2.932646] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
[    2.932650] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.936530] ata2.00: configured for UDMA/33
[    2.944708] ata1.00: configured for UDMA/100
[    2.944855] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[    2.945021] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.945075] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.945138] sd 0:0:0:0: [sda] Write Protect is off
[    2.945142] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.945174] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.945340]  sda:
[    2.949434] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PP02 PQ: 0 ANSI: 5
[    2.961121] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.961125] Uniform CD-ROM driver Revision: 3.20
[    2.961234] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.961289] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.967137]  sda1 sda2 < sda5
[    3.000053] Clocksource tsc unstable (delta = -91200064 ns)
[    3.005162]  sda6 >
[    3.005524] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.168313] Freeing unused kernel memory: 540k freed
[    3.168741] Write protecting the kernel text: 4568k
[    3.168813] Write protecting the kernel read-only data: 1836k
[    3.327000] Linux agpgart interface v0.103
[    3.331362] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    3.331770] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    3.335120] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    3.336274] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/input/input6
[    3.336323] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.455434] [drm] Initialized drm 1.1.0 20060810
[    3.462275] b43-pci-bridge 0000:06:02.0: enabling device (0000 -> 0002)
[    3.462291]   alloc irq_desc for 22 on node -1
[    3.462294]   alloc kstat_irqs on node -1
[    3.462307] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.462323] b43-pci-bridge 0000:06:02.0: setting latency timer to 64
[    3.480344] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.480353] i915 0000:00:02.0: setting latency timer to 64
[    3.528088] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[    3.532395]   alloc irq_desc for 21 on node -1
[    3.532399]   alloc kstat_irqs on node -1
[    3.532408] b44 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.532421] b44 0000:06:01.0: setting latency timer to 64
[    3.600157] ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
[    3.600191] b44.c:v2.0
[    3.620965] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:16:d4:a8:86:91
[    4.009554] [drm] TV-14: set mode NTSC 480i 0
[    4.136587] [drm] fb0: inteldrmfb frame buffer device
[    4.136599] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.206685] [drm] LVDS-8: set mode 1280x800 17
[    4.431574] Console: switching to colour frame buffer device 160x50
[    4.770765] PM: Starting manual resume from disk
[    4.770771] PM: Resume from partition 8:6
[    4.770774] PM: Checking hibernation image.
[    4.771001] PM: Resume from disk failed.
[    4.775694] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    4.775701] EXT4-fs (sda5): write access will be enabled during recovery
[    4.794278] EXT4-fs (sda5): barriers enabled
[    7.439170] kjournald2 starting: pid 382, dev sda5:8, commit interval 5 seconds
[    7.439199] EXT4-fs (sda5): delayed allocation enabled
[    7.439205] EXT4-fs: file extents enabled
[    7.443097] EXT4-fs: mballoc enabled
[    7.443117] EXT4-fs (sda5): orphan cleanup on readonly fs
[    7.443127] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 8153
[    7.443169] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 8128
[    7.443223] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 8075
[    7.443251] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 8054
[    7.443264] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5891
[    7.443285] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1677
[    7.443308] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 248449
[    7.443360] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 135910
[    7.443382] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 336
[    7.443395] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 107
[    7.443407] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 106
[    7.443418] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 105
[    7.443429] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 79
[    7.443441] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 72
[    7.443451] EXT4-fs (sda5): 14 orphan inodes deleted
[    7.443455] EXT4-fs (sda5): recovery complete
[    7.749311] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    8.453507] type=1505 audit(1267816099.161:2): operation="profile_load" pid=405 name=/usr/share/gdm/guest-session/Xsession
[    8.457215] type=1505 audit(1267816099.164:3): operation="profile_load" pid=406 name=/sbin/dhclient3
[    8.458037] type=1505 audit(1267816099.164:4): operation="profile_load" pid=406 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.458487] type=1505 audit(1267816099.164:5): operation="profile_load" pid=406 name=/usr/lib/connman/scripts/dhclient-script
[    8.518639] type=1505 audit(1267816099.224:6): operation="profile_load" pid=407 name=/usr/bin/evince
[    8.531469] type=1505 audit(1267816099.236:7): operation="profile_load" pid=407 name=/usr/bin/evince-previewer
[    8.539073] type=1505 audit(1267816099.244:8): operation="profile_load" pid=407 name=/usr/bin/evince-thumbnailer
[    8.567485] type=1505 audit(1267816099.272:9): operation="profile_load" pid=409 name=/usr/lib/cups/backend/cups-pdf
[    8.568473] type=1505 audit(1267816099.276:10): operation="profile_load" pid=409 name=/usr/sbin/cupsd
[    8.577641] type=1505 audit(1267816099.284:11): operation="profile_load" pid=410 name=/usr/sbin/mysqld
[    9.643382] udev: starting version 147
[    9.645547] Adding 1341388k swap on /dev/sda6.  Priority:-1 extents:1 across:1341388k 
[    9.976377] EXT4-fs (sda5): internal journal on sda5:8
[   12.818390] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.675274] intel_rng: FWH not detected
[   13.795254] sdhci: Secure Digital Host Controller Interface driver
[   13.795259] sdhci: Copyright(c) Pierre Ossman
[   13.797611] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[   13.797630] sdhci-pci 0000:06:04.2: enabling device (0000 -> 0002)
[   13.797643] sdhci-pci 0000:06:04.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.797732] Registered led device: mmc0::
[   13.797783] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
[   13.797799] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[   13.797813] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)
[   13.797819] sdhci-pci 0000:06:04.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.797873] Registered led device: mmc1::
[   13.797910] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
[   14.263630] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   14.294167] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   14.595397] acer-wmi: Acer Laptop ACPI-WMI Extras
[   14.632134] cfg80211: Calling CRDA to update world regulatory domain
[   14.704263] Registered led device: acer-wmi::mail
[   14.730302] lp: driver loaded but no devices found
[   14.916373] yenta_cardbus 0000:06:04.0: CardBus bridge found [1025:0090]
[   14.916402] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
[   14.916405] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
[   14.916413] yenta_cardbus 0000:06:04.0: TI: mfunc 0x90501212, devctl 0x44
[   15.148821] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   15.148827] yenta_cardbus 0000:06:04.0: Socket status: 30000006
[   15.148833] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   15.148845] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   15.148850] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   15.149117] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
[   15.149121] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   15.214104] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   15.517218] phy0: Selected rate control algorithm 'minstrel'
[   15.518183] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   16.021216] cfg80211: World regulatory domain updated:
[   16.021221]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.021226]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.021230]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.021234]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.021237]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.021241]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.044336] __ratelimit: 6 callbacks suppressed
[   16.044341] type=1505 audit(1267816106.752:14): operation="profile_replace" pid=891 name=/usr/share/gdm/guest-session/Xsession
[   16.046623] type=1505 audit(1267816106.752:15): operation="profile_replace" pid=892 name=/sbin/dhclient3
[   16.047450] type=1505 audit(1267816106.752:16): operation="profile_replace" pid=892 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   16.047908] type=1505 audit(1267816106.752:17): operation="profile_replace" pid=892 name=/usr/lib/connman/scripts/dhclient-script
[   16.048600] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   16.050824] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   16.051780] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   16.052716] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   16.053451] type=1505 audit(1267816106.760:18): operation="profile_replace" pid=893 name=/usr/bin/evince
[   16.053509]  clean.
[   16.053774] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   16.066766] type=1505 audit(1267816106.772:19): operation="profile_replace" pid=893 name=/usr/bin/evince-previewer
[   16.074425] type=1505 audit(1267816106.780:20): operation="profile_replace" pid=893 name=/usr/bin/evince-thumbnailer
[   16.085341] type=1505 audit(1267816106.792:21): operation="profile_replace" pid=895 name=/usr/lib/cups/backend/cups-pdf
[   16.086322] type=1505 audit(1267816106.792:22): operation="profile_replace" pid=895 name=/usr/sbin/cupsd
[   16.089521] type=1505 audit(1267816106.796:23): operation="profile_replace" pid=896 name=/usr/sbin/mysqld
[   16.532098] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.532154] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.872873] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   22.028468] __ratelimit: 12 callbacks suppressed
[   22.028473] type=1503 audit(1267816112.736:28): operation="open" pid=1267 parent=1266 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   23.048944] type=1503 audit(1267816113.756:29): operation="open" pid=1295 parent=1292 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   23.075167] type=1503 audit(1267816113.780:30): operation="open" pid=1305 parent=1177 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   24.067091] type=1503 audit(1267816114.773:31): operation="open" pid=1316 parent=1315 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   25.083426] type=1503 audit(1267816115.788:32): operation="open" pid=1326 parent=1325 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   26.105272] type=1503 audit(1267816116.812:33): operation="open" pid=1338 parent=1337 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   27.470428] type=1503 audit(1267816118.176:34): operation="open" pid=1355 parent=1354 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   27.669205] type=1503 audit(1267816118.376:35): operation="open" pid=1367 parent=1366 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   29.670873] [drm] TV-14: set mode NTSC 480i 0
[   29.811448] [drm] TV-14: set mode NTSC 480i 0
[   30.267720] [drm] TV-14: set mode NTSC 480i 0
[   30.408428] [drm] TV-14: set mode NTSC 480i 0
[   33.983044] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.743801] ppdev: user-space parallel port driver
[   41.689364] [drm] TV-14: set mode NTSC 480i 0
[   41.830298] [drm] TV-14: set mode NTSC 480i 0
[   42.116768] [drm] TV-14: set mode NTSC 480i 0
[   42.258172] [drm] TV-14: set mode NTSC 480i 0
[   42.553157] [drm] TV-14: set mode NTSC 480i 0
[   42.693258] [drm] TV-14: set mode NTSC 480i 0
[   44.808475] [drm] TV-14: set mode NTSC 480i 0
[   44.948732] [drm] TV-14: set mode NTSC 480i 0
[   75.072088] usb 1-5: new high speed USB device using ehci_hcd and address 2
[   75.205498] usb 1-5: configuration #1 chosen from 1 choice
[   75.207211] hub 1-5:1.0: USB hub found
[   75.209176] hub 1-5:1.0: 4 ports detected
[   75.480385] usb 1-5.4: new high speed USB device using ehci_hcd and address 3
[   75.572994] usb 1-5.4: configuration #1 chosen from 1 choice
[   75.676374] usb 1-5.4: reset high speed USB device using ehci_hcd and address 3
[   75.769406] phy1: Selected rate control algorithm 'minstrel'
[   75.770416] zd1211rw 1-5.4:1.0: phy1
[   75.770444] usbcore: registered new interface driver zd1211rw
[   75.851973] udev: renamed network interface wlan1 to wlan2
[   78.841106] usb 1-7: new high speed USB device using ehci_hcd and address 4
[   79.236635] usb 1-7: configuration #1 chosen from 1 choice
[   88.823025] usb 1-5.4: firmware: requesting zd1211/zd1211b_ub
[   88.842124] usb 1-5.4: firmware: requesting zd1211/zd1211b_uphr
[   88.897692] zd1211rw 1-5.4:1.0: firmware version 4725
[   88.937692] zd1211rw 1-5.4:1.0: zd1211b chip 0ace:1215 v4810 high 00-0e-3b AL2230_RF pa0 --6-S
[   89.009305] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   89.016237] cfg80211: Calling CRDA for country: US
[   89.019299] cfg80211: Regulatory domain changed to country: US
[   89.019303]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   89.019308]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   89.019311]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   89.019315]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   89.019319]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   89.019323]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  117.580506] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  117.784257] wlan2: direct probe to AP 00:1b:2f:62:7e:2a try 1
[  117.784285] wlan2: privacy configuration mismatch and mixed-cell disabled - disassociate
[  117.863252] wlan2: authenticate with AP 00:1b:2f:62:7e:2a
[  117.866624] wlan2: authenticated
[  117.866628] wlan2: associate with AP 00:1b:2f:62:7e:2a
[  117.871673] wlan2: RX AssocResp from 00:1b:2f:62:7e:2a (capab=0x431 status=0 aid=4)
[  117.871680] wlan2: associated
[  117.996381] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  128.212056] wlan2: no IPv6 routers present
[  157.856056] wlan2: no probe response from AP 00:1b:2f:62:7e:2a - disassociating
[  175.023878] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  175.255881] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  176.040373] wlan2: authenticate with AP 00:1f:9f:47:ef:f1
[  176.042476] wlan2: authenticated
[  176.042479] wlan2: associate with AP 00:1f:9f:47:ef:f1
[  176.045280] wlan2: RX AssocResp from 00:1f:9f:47:ef:f1 (capab=0x411 status=0 aid=1)
[  176.045287] wlan2: associated
[  176.046169] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  186.156040] wlan2: no IPv6 routers present
[  238.728133] wlan2: deauthenticating by local choice (reason=3)
[  238.760122] wlan2: deauthenticating by local choice (reason=3)
[  246.536304] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  247.365216] wlan2: direct probe to AP 00:22:3f:ce:79:20 try 1
[  247.365512] wlan2: privacy configuration mismatch and mixed-cell disabled - disassociate
[  247.564062] wlan2: privacy configuration mismatch and mixed-cell disabled - disassociate
[  247.572804] wlan2: deauthenticated (Reason: 6)
[  250.527089] wlan2: authenticate with AP 00:22:3f:ce:79:20
[  250.531704] wlan2: authenticated
[  250.531714] wlan2: associate with AP 00:22:3f:ce:79:20
[  250.533823] wlan2: RX AssocResp from 00:22:3f:ce:79:20 (capab=0x411 status=0 aid=1)
[  250.533831] wlan2: associated
[  250.535495] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  261.200052] wlan2: no IPv6 routers present
[  316.317884] usb 1-7: USB disconnect, address 4
[  316.588078] usb 1-7: new high speed USB device using ehci_hcd and address 5
[  316.984741] usb 1-7: configuration #1 chosen from 1 choice
[  317.662170] usb 1-7: USB disconnect, address 5
[  318.140058] usb 5-1: new full speed USB device using uhci_hcd and address 2
[  318.360064] usb 5-1: device descriptor read/64, error -32
[  318.700062] usb 5-1: not running at top speed; connect to a high speed hub
[  318.903256] usb 5-1: configuration #1 chosen from 1 choice
[  320.089097] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[  320.089111] usb 5-1: USB disconnect, address 2
[  320.332074] usb 5-1: new full speed USB device using uhci_hcd and address 3
[  320.568003] usb 5-1: not running at top speed; connect to a high speed hub
[  320.771194] usb 5-1: configuration #1 chosen from 1 choice
[  320.835660] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[  320.835675] usb 5-1: USB disconnect, address 3
[  321.076058] usb 5-1: new full speed USB device using uhci_hcd and address 4
[  321.520088] usb 5-1: device descriptor read/64, error -32
[  321.859960] usb 5-1: not running at top speed; connect to a high speed hub
[  322.063156] usb 5-1: configuration #1 chosen from 1 choice
[  324.056110] usb 5-1: USB disconnect, address 4
[  324.540059] usb 1-7: new high speed USB device using ehci_hcd and address 7
[  324.936854] usb 1-7: configuration #1 chosen from 1 choice
[  326.506593] usb 1-7: USB disconnect, address 7
[  327.152106] usb 1-7: new high speed USB device using ehci_hcd and address 8
[  327.548910] usb 1-7: configuration #1 chosen from 1 choice
[  346.768484] usb 1-7: USB disconnect, address 8
[  347.040074] usb 1-7: new high speed USB device using ehci_hcd and address 9
[  347.436885] usb 1-7: configuration #1 chosen from 1 choice
[ 1378.301058] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1609.571470] xchat-gnome[4122]: segfault at 4 ip 00283808 sp bf993560 error 4 in libgobject-2.0.so.0.2200.2[27b000+3c000]

so i cant see if my card is working or not then i downloaded mythtv to see if its working. the setup is not that difficult what i found is that mythtv doesnt see my card.  and i didnt know why cos people from linuxtv irc channel toled me 4 days ago that this card should work with v4l-dvb so i asked today again on linuxtv irc channel about my card and  got new answer that my card is not supported im little angry cos first i got the info about my card being supported and there is not much info about mythtv and nova-s usb2 so i had problem nstalling v4l-dvb. now i got it and the new info from linuxtv channel that my card is not supported. 

i want to ask maybe someone know anything how to get hauppauge nova-s usb2 model 4700 chipset cx24123 work in karmic is there any chance to get it work ? if so whatd river shoudl i get or how to get it to work? if that card wouldnt work in karmic then what card is the best to use in karmic if i want to watch satellite channels and use usb not pci?

---

### Post by laceration on 2010-03-05
as per
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-S-USB2](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-S-USB2)

Not Supported! 

Sorry, a lot are devices are supported by Linux, though.

[http://www.linuxtv.org/wiki/index.php](http://www.linuxtv.org/wiki/index.php) is a good place to find out what is supported + how to install.

A good approach is to shop for a device, find one at a good price and then check if it is supported.

---

