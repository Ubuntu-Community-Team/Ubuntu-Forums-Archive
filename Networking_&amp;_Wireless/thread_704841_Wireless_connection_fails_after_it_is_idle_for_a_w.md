---
title: "Wireless connection fails after it is idle for a while"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by chrisinspace on 2008-02-22
I installed Mythbuntu (basically Xubuntu with MythTV rolled into it) on a Dell machine a while ago.  I put an MSI wireless card into the box before install, and it worked from day one.  It still works fine most of the time, but if I leave the computer idle for an extended amount of time, the connection dies.  If I reboot, it works again.  I have listened to music off of my network for hours before and never had it die while in use.  It only seems to happen if the connection is not in use.  After it dies, these 4 lines repeat over and over again in my syslog until I reboot (addresses changed for security reasons).

```
Feb 22 16:17:33 mythbuntu kernel: [333323.001908] wlan0: No STA entry for own AP 00:24:11:28:25:c9

Feb 22 16:17:39 mythbuntu ntpd[4706]: bind() fd 21, family 10, port 123, scope 4, addr fe90::311:9ef:fe27:43fe, in6_is_addr_multicast=0 flags=17 fails: Cannot assign requested address

Feb 22 16:17:39 mythbuntu ntpd[4706]: unable to create socket on wlan0 (1117) for fe90::311:9ef:fe27:43fe#123

Feb 22 16:17:39 mythbuntu ntpd[4706]: failed to initialize interface for address fe90::311:9ef:fe27:43fe

```

Does anyone have any idea what's happening here?  I've searched through the forums and googled the erros, but didn't really come up with much.

---

### Post by chrisinspace on 2008-02-22
Actually, I took a closer look at the syslog and the line about 'No STA entry' appears a lot...sometimes 8 or 9 times in a row.

---

### Post by chrisinspace on 2008-02-24
I've dug up some more info and I really hope someone can use it to give me a hand with this problem.

The chipset on my card is RaLink RT2500 802.11g Cardbus/mini-PCI.

The driver is rt2500pci.

Here's my dmesg when the adapter is up:

```
chris@mythbuntu:~$ sudo dmesg
[sudo] password for chris:
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff77000 (usable)
[    0.000000]  BIOS-e820: 000000001ff77000 - 000000001ff96000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff96000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130935) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130935
[    0.000000]   HighMem    130935 ->   130935
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130935
[    0.000000] On node 0 totalpages: 130935
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125849 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FD6D0 checksum 0
[    0.000000] ACPI: RSDP 000FD6D0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD6E4, 0030 (r1 DELL    WS 330         5 ASL        61)
[    0.000000] ACPI: FACP 000FD718, 0074 (r1 DELL    WS 330         5 ASL        61)
[    0.000000] ACPI: DSDT FFFE5022, 2474 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FF96000, 0040
[    0.000000] ACPI: SSDT FFFE75D3, 00BA (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: BOOT 000FD7E8, 0028 (r1 DELL    WS330          5 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 129913
[    0.000000] Kernel command line: root=UUID=16b1b5f3-06a1-4fcc-be0c-3a3025c845c3 ro quiet splash
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1296.097 MHz processor.
[   32.606521] Console: colour VGA+ 80x25
[   32.606856] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   32.607282] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.628954] Memory: 507532k/523740k available (2015k kernel code, 15584k reserved, 915k data, 364k init, 0k highmem)
[   32.628972] virtual kernel memory layout:
[   32.628974]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   32.628976]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   32.628979]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   32.628981]     lowmem  : 0xc0000000 - 0xdff77000   ( 511 MB)
[   32.628983]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   32.628985]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   32.628987]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   32.628994] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   32.629063] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   32.709091] Calibrating delay using timer specific routine.. 2595.48 BogoMIPS (lpj=5190974)
[   32.709135] Security Framework v1.0.0 initialized
[   32.709148] SELinux:  Disabled at boot.
[   32.709173] Mount-cache hash table entries: 512
[   32.709431] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   32.709457] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   32.709464] CPU: L2 cache: 256K
[   32.709469] CPU: Hyper-Threading is disabled
[   32.709473] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   32.709497] Compat vDSO mapped to ffffe000.
[   32.709522] Checking 'hlt' instruction... OK.
[   32.725386] SMP alternatives: switching to UP code
[   32.725816] Freeing SMP alternatives: 11k freed
[   32.726459] Early unpacking initramfs... done
[   33.387114] ACPI: Core revision 20070126
[   33.400467] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   33.426384] ACPI: setting ELCR to 0200 (from 0e00)
[   33.426842] CPU0: Intel(R) Pentium(R) 4 CPU 1300MHz stepping 07
[   33.426852] SMP motherboard not detected.
[   33.430882] Uhhuh. NMI received for unknown reason 21 on CPU 0.
[   33.430941] Do you have a strange power saving mode enabled?
[   33.430994] Dazed and confused, but trying to continue
[   33.533139] Brought up 1 CPUs
[   33.533366] Booting paravirtualized kernel on bare hardware
[   33.533471] Time: 14:23:04  Date: 01/23/108
[   33.533514] NET: Registered protocol family 16
[   33.533714] EISA bus registered
[   33.533737] ACPI: bus type pci registered
[   33.560937] PCI: PCI BIOS revision 2.10 entry at 0xfc03e, last bus=2
[   33.560942] PCI: Using configuration type 1
[   33.560945] Setting up standard PCI resources
[   33.575688] ACPI: EC: Look up EC in DSDT
[   33.599312] ACPI: Interpreter enabled
[   33.599321] ACPI: (supports S0 S1 S3 S4 S5)
[   33.599362] ACPI: Using PIC for interrupt routing
[   33.624589] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   33.624624] PCI: Probing PCI hardware (bus 00)
[   33.624961] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   33.624968] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   33.626143] PCI: Transparent bridge - 0000:00:1e.0
[   33.626190] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   33.627264] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   33.648243] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   33.648662] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   33.649091] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   33.649505] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   33.649913] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   33.650323] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   33.650733] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   33.651152] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   33.651409] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.651440] pnp: PnP ACPI init
[   33.651462] ACPI: bus type pnp registered
[   33.676876] pnp: PnP ACPI: found 11 devices
[   33.676883] ACPI: ACPI bus type pnp unregistered
[   33.676892] PnPBIOS: Disabled by ACPI PNP
[   33.677010] PCI: Using ACPI for IRQ routing
[   33.677016] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   33.677025] PCI: Cannot allocate resource region 8 of bridge 0000:00:01.0
[   33.677140] PCI: Cannot allocate resource region 0 of device 0000:01:00.0
[   33.688859] NET: Registered protocol family 8
[   33.688864] NET: Registered protocol family 20
[   33.689020] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   33.689027] pnp: 00:00: iomem range 0x100000-0xffffff could not be reserved
[   33.689033] pnp: 00:00: iomem range 0x1000000-0x1ff76fff could not be reserved
[   33.689039] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   33.689061] Time: tsc clocksource has been installed.
[   33.689082] pnp: 00:0a: ioport range 0x800-0x85f has been reserved
[   33.689088] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[   33.689094] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[   33.719866] PCI: Bridge: 0000:00:01.0
[   33.719871]   IO window: disabled.
[   33.719879]   MEM window: 30000000-317fffff
[   33.719886]   PREFETCH window: f0000000-f7ffffff
[   33.719896] PCI: Bridge: 0000:00:1e.0
[   33.719901]   IO window: e000-efff
[   33.719910]   MEM window: ff100000-ff2fffff
[   33.719918]   PREFETCH window: f8000000-f80fffff
[   33.719944] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   33.719971] NET: Registered protocol family 2
[   33.757126] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   33.757204] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   33.757391] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   33.757549] TCP: Hash tables configured (established 16384 bind 16384)
[   33.757557] TCP reno registered
[   33.769348] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   34.389672]  it is
[   35.065479] Freeing initrd memory: 7205k freed
[   35.065644] Simple Boot Flag at 0x7d set to 0x1
[   35.066075] audit: initializing netlink socket (disabled)
[   35.066096] audit(1203776584.956:1): initialized
[   35.070796] VFS: Disk quotas dquot_6.5.1
[   35.070919] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   35.071129] io scheduler noop registered
[   35.071135] io scheduler anticipatory registered
[   35.071138] io scheduler deadline registered
[   35.071182] io scheduler cfq registered (default)
[   35.071246] Boot video device is 0000:01:00.0
[   35.071588] isapnp: Scanning for PnP cards...
[   35.426213] isapnp: No Plug & Play device found
[   35.524145] Real Time Clock Driver v1.12ac
[   35.524310] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.524439] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.524984] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   35.526726] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.527429] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   35.529280] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.529725] input: Macintosh mouse button emulation as /class/input/input0
[   35.530008] PNP: No PS/2 controller found. Probing ports directly.
[   35.781050] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.781417] mice: PS/2 mouse device common for all mice
[   35.781684] EISA: Probing bus 0 at eisa.0
[   35.781735] EISA: Detected 0 cards.
[   35.781913] TCP cubic registered
[   35.781941] NET: Registered protocol family 1
[   35.782067] Testing NMI watchdog ... CPU#0: NMI appears to be stuck (2->2)!
[   35.861553] Using IPI No-Shortcut mode
[   35.861873]   Magic number: 12:11:385
[   35.862673] Freeing unused kernel memory: 364k freed
[   37.335652] AppArmor: AppArmor initialized<5>audit(1203776587.456:2):  type=1505 info="AppArmor initialized" pid=1101
[   37.353700] fuse init (API version 7.8)
[   37.366255] Failure registering capabilities with primary security module.
[   38.659028] SCSI subsystem initialized
[   38.671378] libata version 2.21 loaded.
[   38.680103] ata_piix 0000:00:1f.1: version 2.11
[   38.680184] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   38.680327] scsi0 : ata_piix
[   38.680453] scsi1 : ata_piix
[   38.680509] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   38.680516] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   38.718024] usbcore: registered new interface driver usbfs
[   38.718073] usbcore: registered new interface driver hub
[   38.718124] usbcore: registered new device driver usb
[   38.720207] USB Universal Host Controller Interface driver v3.0
[   38.844822] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41KW0, max UDMA/133
[   38.844831] ata1.00: 160086528 sectors, multi 8: LBA 
[   38.860764] ata1.00: configured for UDMA/100
[   39.028178] Floppy drive(s): fd0 is 1.44M
[   39.105389] FDC 0 is a National Semiconductor PC87306
[   39.180672] ata2.00: ATAPI: _NEC DVD+RW ND-1100A, 10FD, max UDMA/33
[   39.352927] ata2.00: configured for UDMA/33
[   39.353152] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[   39.356133] scsi 1:0:0:0: CD-ROM            _NEC     DVD+RW ND-1100A  10FD PQ: 0 ANSI: 5
[   39.357126] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   39.357134] PCI: setting IRQ 11 as level-triggered
[   39.357141] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   39.357161] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   39.357167] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   39.357428] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   39.357468] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ff80
[   39.357727] usb usb1: configuration #1 chosen from 1 choice
[   39.357784] hub 1-0:1.0: USB hub found
[   39.357801] hub 1-0:1.0: 2 ports detected
[   39.392219] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[   39.392312] sd 0:0:0:0: [sda] Write Protect is off
[   39.392318] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   39.392357] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.392479] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[   39.392501] sd 0:0:0:0: [sda] Write Protect is off
[   39.392506] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   39.392542] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.392551]  sda: sda1 sda2 < sda5 >
[   39.429354] sd 0:0:0:0: [sda] Attached SCSI disk
[   39.438478] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   39.438852] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   39.461126] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[   39.461135] PCI: setting IRQ 9 as level-triggered
[   39.461141] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[   39.461162] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   39.461168] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   39.461236] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   39.461273] uhci_hcd 0000:00:1f.4: irq 9, io base 0x0000ff60
[   39.461473] usb usb2: configuration #1 chosen from 1 choice
[   39.461528] hub 2-0:1.0: USB hub found
[   39.461544] hub 2-0:1.0: 2 ports detected
[   39.470406] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   39.470416] Uniform CD-ROM driver Revision: 3.20
[   39.470865] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   39.565280] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   39.565289] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   39.565303] 3c59x: Donald Becker and others.
[   39.565312] 0000:02:0c.0: 3Com PCI 3c905C Tornado at e0814c00.
[   39.700230] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   39.815253] Attempting manual resume
[   39.815261] swsusp: Resume From Partition 8:5
[   39.815265] PM: Checking swsusp image.
[   39.815618] PM: Resume from disk failed.
[   39.850130] EXT3-fs: INFO: recovery required on readonly filesystem.
[   39.850138] EXT3-fs: write access will be enabled during recovery.
[   39.880568] usb 1-1: configuration #1 chosen from 1 choice
[   40.120172] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   40.299453] usb 1-2: configuration #1 chosen from 1 choice
[   40.540133] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   40.722213] usb 2-2: configuration #1 chosen from 1 choice
[   40.728018] usbcore: registered new interface driver hiddev
[   40.747285] input: Logitech Logitech(R) Precision(TM) Gamepad as /class/input/input1
[   40.747301] input: USB HID v1.10 Joystick [Logitech Logitech(R) Precision(TM) Gamepad] on usb-0000:00:1f.2-1
[   40.766279] input: Logitech Logitech(R) Precision(TM) Gamepad as /class/input/input2
[   40.766296] input: USB HID v1.10 Joystick [Logitech Logitech(R) Precision(TM) Gamepad] on usb-0000:00:1f.2-2
[   40.766328] usbcore: registered new interface driver usbhid
[   40.766336] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   43.342960] kjournald starting.  Commit interval 5 seconds
[   43.342989] EXT3-fs: recovery complete.
[   43.360568] EXT3-fs: mounted filesystem with ordered data mode.
[   53.816370] iTCO_vendor_support: vendor-support=0
[   53.818423] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   53.818567] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0x0860)
[   53.818650] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   53.850776] Intel 82802 RNG detected
[   54.095538] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   54.099124] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   54.122846] Linux agpgart interface v0.102 (c) Dave Jones
[   54.132936] agpgart: Detected an Intel i850 Chipset.
[   54.141386] agpgart: AGP aperture is 128M @ 0xe8000000
[   55.509288] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   55.509297] PCI: setting IRQ 10 as level-triggered
[   55.509304] ACPI: PCI Interrupt 0000:02:08.1[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   55.770037] Linux video capture interface: v2.00
[   55.882318] bttv: driver version 0.9.17 loaded
[   55.882325] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   55.882438] bttv: Bt8xx card found (0).
[   55.882475] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   55.882496] bttv0: Bt878 (rev 17) at 0000:02:08.0, irq: 10, latency: 64, mmio: 0xf8001000
[   55.882515] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   55.882521] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   55.882559] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init]
[   55.885051] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   55.917177] tveeprom 0-0050: Hauppauge model 38061, rev B410, serial# 4084416
[   55.917184] tveeprom 0-0050: tuner model is Philips FI1236 MK2 (idx 10, type 2)
[   55.917190] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   55.917195] tveeprom 0-0050: audio processor is None (idx 0)
[   55.917199] tveeprom 0-0050: has radio
[   55.917204] bttv0: Hauppauge eeprom indicates model#38061
[   55.917208] bttv0: using tuner=2
[   55.917252] bttv0: i2c: checking for MSP34xx @ 0x80... <6>input: PC Speaker as /class/input/input3
[   56.071902] parport_pc 00:09: reported by Plug and Play ACPI
[   56.072024] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[   56.157836] usbcore: registered new interface driver xpad
[   56.157846] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   56.317928] not found
[   56.317939] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>Bluetooth: Core ver 2.11
[   56.445751] NET: Registered protocol family 31
[   56.445757] Bluetooth: HCI device and connection manager initialized
[   56.445764] Bluetooth: HCI socket layer initialized
[   56.504598] Bluetooth: HCI USB driver ver 2.9
[   56.514503] usbcore: registered new interface driver hci_usb
[   56.622806] not found
[   56.622817] bttv0: i2c: checking for TDA7432 @ 0x8a... <4>nvidia: module license 'NVIDIA' taints kernel.
[   57.191126] not found
[   57.264334] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   57.297384] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   57.297439] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   57.297446] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   57.306908] bttv0: registered device video0
[   57.306984] bttv0: registered device vbi0
[   57.307049] bttv0: registered device radio0
[   57.307080] bttv0: PLL: 28636363 => 35468950 .. ok
[   57.355341] gameport: EMU10K1 is pci0000:02:09.1/gameport0, io 0xecd8, speed 877kHz
[   57.355747] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   57.388514] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   57.388524] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   57.403226] bt878: AUDIO driver version 0.0.0 loaded
[   57.556713] ieee80211_init: failed to initialize WME (err=-17)
[   57.571535] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   57.571657] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   57.571760] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   57.571913] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   57.586594] wmaster0: Selected rate control algorithm 'simple'
[   57.707375] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   57.707739] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   57.709269] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   57.709301] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   58.325669] intel8x0_measure_ac97_clock: measured 52162 usecs
[   58.325677] intel8x0: clocking to 41158
[   58.625710] wlan0: Initial auth_alg=0
[   58.625719] wlan0: authenticate with AP 00:24:11:28:25:c9
[   58.627283] wlan0: RX authentication from 00:24:11:28:25:c9 (alg=0 transaction=2 status=0)
[   58.627288] wlan0: authenticated
[   58.627293] wlan0: associate with AP 00:24:11:28:25:c9
[   58.629448] wlan0: RX AssocResp from 00:24:11:28:25:c9 (capab=0x411 status=0 aid=3)
[   58.629453] wlan0: associated
[   58.920334] lp0: using parport0 (interrupt-driven).
[   59.205113] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   59.722268] NET: Registered protocol family 10
[   59.722446] lo: Disabled Privacy Extensions
[   60.297492] EXT3 FS on sda1, internal journal
[   60.556381] wlan0: duplicate address detected!
[   62.238034] No dock devices found.
[   62.408864] input: Power Button (FF) as /class/input/input4
[   62.416397] ACPI: Power Button (FF) [PWRF]
[   62.477115] input: Power Button (CM) as /class/input/input5
[   62.477571] ACPI: Power Button (CM) [VBTN]
[   65.858671] eth0:  setting half-duplex.
[   65.859415] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   74.729331] Bluetooth: L2CAP ver 2.8
[   74.729340] Bluetooth: L2CAP socket layer initialized
[   74.782554] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   74.983207] Bluetooth: RFCOMM socket layer initialized
[   74.983435] Bluetooth: RFCOMM TTY layer initialized
[   74.983442] Bluetooth: RFCOMM ver 1.8
[   75.070329] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[   75.070339] Bluetooth: BNEP filters: protocol multicast
[   75.130940] Bridge firewalling registered
[   76.686127] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   76.686155] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   76.686185] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  139.224168] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input6

```

And here it is when the connection is down:

```
chris@mythbuntu:~$ sudo dmesg
[sudo] password for chris:
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff77000 (usable)
[    0.000000]  BIOS-e820: 000000001ff77000 - 000000001ff96000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff96000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130935) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130935
[    0.000000]   HighMem    130935 ->   130935
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130935
[    0.000000] On node 0 totalpages: 130935
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125849 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FD6D0 checksum 0
[    0.000000] ACPI: RSDP 000FD6D0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD6E4, 0030 (r1 DELL    WS 330         5 ASL        61)
[    0.000000] ACPI: FACP 000FD718, 0074 (r1 DELL    WS 330         5 ASL        61)
[    0.000000] ACPI: DSDT FFFE5022, 2474 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FF96000, 0040
[    0.000000] ACPI: SSDT FFFE75D3, 00BA (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: BOOT 000FD7E8, 0028 (r1 DELL    WS330          5 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 129913
[    0.000000] Kernel command line: root=UUID=16b1b5f3-06a1-4fcc-be0c-3a3025c845c3 ro quiet splash
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1296.100 MHz processor.
[   32.762713] Console: colour VGA+ 80x25
[   32.763052] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   32.763471] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.785147] Memory: 507532k/523740k available (2015k kernel code, 15584k reserved, 915k data, 364k init, 0k highmem)
[   32.785167] virtual kernel memory layout:
[   32.785169]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   32.785172]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   32.785174]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   32.785176]     lowmem  : 0xc0000000 - 0xdff77000   ( 511 MB)
[   32.785178]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   32.785180]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   32.785182]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   32.785189] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   32.785258] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   32.865285] Calibrating delay using timer specific routine.. 2595.50 BogoMIPS (lpj=5191015)
[   32.865329] Security Framework v1.0.0 initialized
[   32.865342] SELinux:  Disabled at boot.
[   32.865367] Mount-cache hash table entries: 512
[   32.865626] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   32.865652] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   32.865658] CPU: L2 cache: 256K
[   32.865663] CPU: Hyper-Threading is disabled
[   32.865668] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   32.865691] Compat vDSO mapped to ffffe000.
[   32.865716] Checking 'hlt' instruction... OK.
[   32.881580] SMP alternatives: switching to UP code
[   32.882010] Freeing SMP alternatives: 11k freed
[   32.882653] Early unpacking initramfs... done
[   33.542732] ACPI: Core revision 20070126
[   33.556085] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   33.582026] ACPI: setting ELCR to 0200 (from 0e00)
[   33.582483] CPU0: Intel(R) Pentium(R) 4 CPU 1300MHz stepping 07
[   33.582494] SMP motherboard not detected.
[   33.586523] Uhhuh. NMI received for unknown reason 31 on CPU 0.
[   33.586583] Do you have a strange power saving mode enabled?
[   33.586636] Dazed and confused, but trying to continue
[   33.689333] Brought up 1 CPUs
[   33.689560] Booting paravirtualized kernel on bare hardware
[   33.689665] Time: 21:22:20  Date: 01/22/108
[   33.689708] NET: Registered protocol family 16
[   33.689911] EISA bus registered
[   33.689934] ACPI: bus type pci registered
[   33.717135] PCI: PCI BIOS revision 2.10 entry at 0xfc03e, last bus=2
[   33.717140] PCI: Using configuration type 1
[   33.717144] Setting up standard PCI resources
[   33.731897] ACPI: EC: Look up EC in DSDT
[   33.755514] ACPI: Interpreter enabled
[   33.755523] ACPI: (supports S0 S1 S3 S4 S5)
[   33.755564] ACPI: Using PIC for interrupt routing
[   33.780737] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   33.780773] PCI: Probing PCI hardware (bus 00)
[   33.781110] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   33.781117] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   33.782291] PCI: Transparent bridge - 0000:00:1e.0
[   33.782340] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   33.783416] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   33.804389] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   33.804808] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   33.805221] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   33.805650] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   33.806059] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   33.806471] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   33.806880] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   33.807298] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   33.807553] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.807585] pnp: PnP ACPI init
[   33.807607] ACPI: bus type pnp registered
[   33.833016] pnp: PnP ACPI: found 11 devices
[   33.833023] ACPI: ACPI bus type pnp unregistered
[   33.833032] PnPBIOS: Disabled by ACPI PNP
[   33.833150] PCI: Using ACPI for IRQ routing
[   33.833157] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   33.833166] PCI: Cannot allocate resource region 8 of bridge 0000:00:01.0
[   33.833281] PCI: Cannot allocate resource region 0 of device 0000:01:00.0
[   33.845000] NET: Registered protocol family 8
[   33.845004] NET: Registered protocol family 20
[   33.845160] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   33.845168] pnp: 00:00: iomem range 0x100000-0xffffff could not be reserved
[   33.845174] pnp: 00:00: iomem range 0x1000000-0x1ff76fff could not be reserved
[   33.845180] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   33.845204] pnp: 00:0a: ioport range 0x800-0x85f has been reserved
[   33.845209] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[   33.845215] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[   33.845255] Time: tsc clocksource has been installed.
[   33.876012] PCI: Bridge: 0000:00:01.0
[   33.876017]   IO window: disabled.
[   33.876025]   MEM window: 30000000-317fffff
[   33.876032]   PREFETCH window: f0000000-f7ffffff
[   33.876042] PCI: Bridge: 0000:00:1e.0
[   33.876047]   IO window: e000-efff
[   33.876056]   MEM window: ff100000-ff2fffff
[   33.876064]   PREFETCH window: f8000000-f80fffff
[   33.876090] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   33.876116] NET: Registered protocol family 2
[   33.913319] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   33.913397] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   33.913585] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   33.913739] TCP: Hash tables configured (established 16384 bind 16384)
[   33.913746] TCP reno registered
[   33.925538] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   34.549994]  it is
[   35.228645] Freeing initrd memory: 7205k freed
[   35.228810] Simple Boot Flag at 0x7d set to 0x1
[   35.229269] audit: initializing netlink socket (disabled)
[   35.229290] audit(1203715340.956:1): initialized
[   35.233983] VFS: Disk quotas dquot_6.5.1
[   35.234106] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   35.234315] io scheduler noop registered
[   35.234320] io scheduler anticipatory registered
[   35.234324] io scheduler deadline registered
[   35.234368] io scheduler cfq registered (default)
[   35.234433] Boot video device is 0000:01:00.0
[   35.234777] isapnp: Scanning for PnP cards...
[   35.589384] isapnp: No Plug & Play device found
[   35.678405] Real Time Clock Driver v1.12ac
[   35.678570] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.678695] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.679158] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   35.680825] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.681626] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   35.683396] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.683846] input: Macintosh mouse button emulation as /class/input/input0
[   35.684127] PNP: No PS/2 controller found. Probing ports directly.
[   35.937244] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.937594] mice: PS/2 mouse device common for all mice
[   35.937854] EISA: Probing bus 0 at eisa.0
[   35.937906] EISA: Detected 0 cards.
[   35.938084] TCP cubic registered
[   35.938112] NET: Registered protocol family 1
[   35.938238] Testing NMI watchdog ... CPU#0: NMI appears to be stuck (2->2)!
[   36.017720] Using IPI No-Shortcut mode
[   36.018041]   Magic number: 12:678:399
[   36.018838] Freeing unused kernel memory: 364k freed
[   37.444049] AppArmor: AppArmor initialized<5>audit(1203715343.456:2):  type=1505 info="AppArmor initialized" pid=1101
[   37.461978] fuse init (API version 7.8)
[   37.474680] Failure registering capabilities with primary security module.
[   38.853570] SCSI subsystem initialized
[   38.866835] libata version 2.21 loaded.
[   38.875499] ata_piix 0000:00:1f.1: version 2.11
[   38.875579] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   38.875722] scsi0 : ata_piix
[   38.875823] scsi1 : ata_piix
[   38.875880] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   38.875887] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   38.966199] usbcore: registered new interface driver usbfs
[   38.966249] usbcore: registered new interface driver hub
[   38.966300] usbcore: registered new device driver usb
[   38.968250] USB Universal Host Controller Interface driver v3.0
[   39.036972] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41KW0, max UDMA/133
[   39.036981] ata1.00: 160086528 sectors, multi 8: LBA 
[   39.053007] ata1.00: configured for UDMA/100
[   39.237174] Floppy drive(s): fd0 is 1.44M
[   39.254377] FDC 0 is a National Semiconductor PC87306
[   39.372863] ata2.00: ATAPI: _NEC DVD+RW ND-1100A, 10FD, max UDMA/33
[   39.544794] ata2.00: configured for UDMA/33
[   39.545015] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[   39.547382] scsi 1:0:0:0: CD-ROM            _NEC     DVD+RW ND-1100A  10FD PQ: 0 ANSI: 5
[   39.548682] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   39.548691] PCI: setting IRQ 11 as level-triggered
[   39.548697] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   39.548718] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   39.548725] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   39.548975] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   39.549015] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ff80
[   39.549274] usb usb1: configuration #1 chosen from 1 choice
[   39.549330] hub 1-0:1.0: USB hub found
[   39.549348] hub 1-0:1.0: 2 ports detected
[   39.583409] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[   39.583458] sd 0:0:0:0: [sda] Write Protect is off
[   39.583464] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   39.583502] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.583625] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[   39.583647] sd 0:0:0:0: [sda] Write Protect is off
[   39.583653] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   39.583688] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.583697]  sda: sda1 sda2 < sda5 >
[   39.618850] sd 0:0:0:0: [sda] Attached SCSI disk
[   39.628133] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   39.628529] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   39.653347] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[   39.653356] PCI: setting IRQ 9 as level-triggered
[   39.653361] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[   39.653381] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   39.653388] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   39.653449] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   39.653486] uhci_hcd 0000:00:1f.4: irq 9, io base 0x0000ff60
[   39.653695] usb usb2: configuration #1 chosen from 1 choice
[   39.653759] hub 2-0:1.0: USB hub found
[   39.653772] hub 2-0:1.0: 2 ports detected
[   39.667620] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   39.667630] Uniform CD-ROM driver Revision: 3.20
[   39.668125] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   39.757510] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   39.757519] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   39.757534] 3c59x: Donald Becker and others.
[   39.757542] 0000:02:0c.0: 3Com PCI 3c905C Tornado at e0814c00.
[   39.892447] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   40.004581] Attempting manual resume
[   40.004589] swsusp: Resume From Partition 8:5
[   40.004592] PM: Checking swsusp image.
[   40.004928] PM: Resume from disk failed.
[   40.068059] kjournald starting.  Commit interval 5 seconds
[   40.068083] EXT3-fs: mounted filesystem with ordered data mode.
[   40.075130] usb 1-1: configuration #1 chosen from 1 choice
[   40.316372] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   40.495981] usb 1-2: configuration #1 chosen from 1 choice
[   40.736336] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   40.922403] usb 2-2: configuration #1 chosen from 1 choice
[   40.925665] usbcore: registered new interface driver hiddev
[   40.944819] input: Logitech Logitech(R) Precision(TM) Gamepad as /class/input/input1
[   40.944834] input: USB HID v1.10 Joystick [Logitech Logitech(R) Precision(TM) Gamepad] on usb-0000:00:1f.2-1
[   40.963802] input: Logitech Logitech(R) Precision(TM) Gamepad as /class/input/input2
[   40.963818] input: USB HID v1.10 Joystick [Logitech Logitech(R) Precision(TM) Gamepad] on usb-0000:00:1f.2-2
[   40.963850] usbcore: registered new interface driver usbhid
[   40.963857] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   48.018480] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.029827] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.245845] Linux agpgart interface v0.102 (c) Dave Jones
[   48.272012] iTCO_vendor_support: vendor-support=0
[   48.289417] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   48.289557] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0x0860)
[   48.289637] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   48.323004] Intel 82802 RNG detected
[   48.778992] agpgart: Detected an Intel i850 Chipset.
[   48.787505] agpgart: AGP aperture is 128M @ 0xe8000000
[   49.917412] gameport: EMU10K1 is pci0000:02:09.1/gameport0, io 0xecd8, speed 877kHz
[   50.005446] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   50.005455] PCI: setting IRQ 10 as level-triggered
[   50.005462] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   50.005488] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   50.018439] Linux video capture interface: v2.00
[   50.080191] input: PC Speaker as /class/input/input3
[   50.219842] nvidia: module license 'NVIDIA' taints kernel.
[   50.810512] parport_pc 00:09: reported by Plug and Play ACPI
[   50.810634] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[   50.838950] intel8x0_measure_ac97_clock: measured 53637 usecs
[   50.838958] intel8x0: clocking to 41138
[   50.850116] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   50.850126] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   50.850471] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   50.992676] Bluetooth: Core ver 2.11
[   50.992767] NET: Registered protocol family 31
[   50.992772] Bluetooth: HCI device and connection manager initialized
[   50.992778] Bluetooth: HCI socket layer initialized
[   51.024945] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   51.042615] usbcore: registered new interface driver xpad
[   51.042629] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   51.072792] Bluetooth: HCI USB driver ver 2.9
[   51.075953] usbcore: registered new interface driver hci_usb
[   51.114334] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   51.312032] bttv: driver version 0.9.17 loaded
[   51.312041] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   51.579797] ieee80211_init: failed to initialize WME (err=-17)
[   51.596601] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   51.596725] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   51.596828] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   51.596987] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   51.609461] wmaster0: Selected rate control algorithm 'simple'
[   51.912373] bttv: Bt8xx card found (0).
[   51.912415] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   51.912437] bttv0: Bt878 (rev 17) at 0000:02:08.0, irq: 10, latency: 64, mmio: 0xf8001000
[   51.912465] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   51.912472] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   51.912511] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init]
[   51.915004] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   51.947302] tveeprom 0-0050: Hauppauge model 38061, rev B410, serial# 4084416
[   51.947309] tveeprom 0-0050: tuner model is Philips FI1236 MK2 (idx 10, type 2)
[   51.947315] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   51.947320] tveeprom 0-0050: audio processor is None (idx 0)
[   51.947325] tveeprom 0-0050: has radio
[   51.947329] bttv0: Hauppauge eeprom indicates model#38061
[   51.947334] bttv0: using tuner=2
[   51.948045] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   52.010162] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   52.022191] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   52.063805] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   52.127986] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   52.128043] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   52.128050] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   52.142642] bttv0: registered device video0
[   52.142715] bttv0: registered device vbi0
[   52.142809] bttv0: registered device radio0
[   52.142840] bttv0: PLL: 28636363 => 35468950 .. ok
[   52.175696] ACPI: PCI Interrupt 0000:02:08.1[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   52.245840] bt878: AUDIO driver version 0.0.0 loaded
[   52.878795] wlan0: Initial auth_alg=0
[   52.878805] wlan0: authenticate with AP 00:13:10:18:22:c7
[   52.882150] wlan0: RX authentication from 00:13:10:18:22:c7 (alg=0 transaction=2 status=0)
[   52.882159] wlan0: authenticated
[   52.882164] wlan0: associate with AP 00:13:10:18:22:c7
[   52.885302] wlan0: authentication frame received from 00:13:10:18:22:c7, but not in authenticate state - ignored
[   52.886405] wlan0: RX AssocResp from 00:13:10:18:22:c7 (capab=0x411 status=0 aid=3)
[   52.886411] wlan0: associated
[   53.109614] lp0: using parport0 (interrupt-driven).
[   53.377694] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   54.350861] NET: Registered protocol family 10
[   54.351053] lo: Disabled Privacy Extensions
[   54.492585] wlan0: duplicate address detected!
[   54.520063] EXT3 FS on sda1, internal journal
[   57.019291] No dock devices found.
[   57.181809] input: Power Button (FF) as /class/input/input4
[   57.189336] ACPI: Power Button (FF) [PWRF]
[   57.260622] input: Power Button (CM) as /class/input/input5
[   57.268087] ACPI: Power Button (CM) [VBTN]
[   60.492812] eth0:  setting half-duplex.
[   60.493577] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   69.409879] Bluetooth: L2CAP ver 2.8
[   69.409888] Bluetooth: L2CAP socket layer initialized
[   69.421658] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   69.669742] Bluetooth: RFCOMM socket layer initialized
[   69.669951] Bluetooth: RFCOMM TTY layer initialized
[   69.669957] Bluetooth: RFCOMM ver 1.8
[   69.722869] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[   69.722879] Bluetooth: BNEP filters: protocol multicast
[   69.809384] Bridge firewalling registered
[   71.359011] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   71.359038] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   71.359068] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  127.673390] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input6
[ 1196.757035] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input7
[ 1494.109895] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input8
[ 1762.020440] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input9
[ 1905.646568] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input10
[ 3660.371861] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3660.399958] eth0:  setting half-duplex.
[ 3660.400702] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3660.419079] wlan0: Initial auth_alg=0
[ 3660.419090] wlan0: authenticate with AP 00:24:11:28:25:c9
[ 3660.431518] wlan0: RX authentication from 00:24:11:28:25:c9 (alg=0 transaction=2 status=0)
[ 3660.431529] wlan0: authenticated
[ 3660.431535] wlan0: associate with AP 00:24:11:28:25:c9
[ 3660.435196] wlan0: RX AssocResp from 00:24:11:28:25:c9 (capab=0x411 status=0 aid=3)
[ 3660.435206] wlan0: associated
[ 3660.435940] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3660.516294] eth0:  setting half-duplex.
[ 3660.517040] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3671.049465] wlan0: no IPv6 routers present
[ 3683.103942]  CIFS VFS: server not responding
[ 3683.103956]  CIFS VFS: No response for cmd 114 mid 13
[ 3686.912720] eth0:  setting half-duplex.
[ 3686.913465] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4278.850061] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input11
[ 5608.225849] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input12
[ 9492.884515] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input13
[11665.848796] UDF-fs: Partition marked readonly; forcing readonly mount
[11665.848819] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'THE_LAST_MIMZY_WS', timestamp 2007/05/22 14:30 (1ed4)
[12863.011645] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input14
[13402.114069] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input15
[17776.999415] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input16
[59428.144587] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input17
[59451.675081] input: Wireless Engineering Inc. Bluetooth Keyboard as /class/input/input18
[59697.141983] NVRM: Xid (0001:00): 16, Head 00000000 Count 00687984
[59705.141191] NVRM: Xid (0001:00): 16, Head 00000000 Count 00687985
[59713.140411] NVRM: Xid (0001:00): 16, Head 00000000 Count 00687986
[59721.139619] NVRM: Xid (0001:00): 16, Head 00000000 Count 00687987
[59729.138840] NVRM: Xid (0001:00): 16, Head 00000000 Count 00687988
[59737.138008] NVRM: Xid (0001:00): 16, Head 00000000 Count 00687989
[59745.137212] NVRM: Xid (0001:00): 16, Head 00000000 Count 0068798a
[59753.136415] NVRM: Xid (0001:00): 16, Head 00000000 Count 0068798b

```

I noticed in both instances there is an error that says 'duplicate address detected!'.  Is this IP address (I tried changing that), IRQ address, DMA address?

---

### Post by chrisinspace on 2008-02-28
I'm gonna bump this one last time in hopes of getting some help with this issue.  Does anyone have any idea what's going on here?

---

### Post by chrisinspace on 2008-03-07
Nobody has a single suggestion or response?  Ok...I give up.

---

