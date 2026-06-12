---
title: "D-Link DWL-122 - Odd Configuration Problem"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by SoxFan33 on 2007-10-17
Let me start off by saying that I've been using Ubuntu on and off since 6.10.  Although I've really started enjoying it lately with the beta release of 6.10.

Anyways, I have two computers running Gutsy.  Mine, which dual boots Vista and Gutsy and uses a D-Link DWL-G120 using ndiswrapper.  It works great.  At the moment, I'm trying to get an older computer in my basement running correctly with a D-Link DWL-122 Revision A1 USB adaptor.  It uses the Prism 2.5 chipset, and I've currently got the linux-wlan-ng 0.2.8 driver installed.  This is where things get tricky.

The adaptor is detected and works.  However, I have to manually input the SSID and WEP code every time I start the computer though the Network Manger applet in the task bar.  When I start the computer, it appears that its actually being indentified by the system as an ethenet card, but it still partially works as wireless.  I get this:
[img]http://img134.imageshack.us/img134/6346/networkadmincf3.png[/img]
[img]http://img134.imageshack.us/img134/5421/networktaskbarjf6.png[/img]

I've been working at this for 2 weeks now, and have talked to Ashex (he's a user here).  He was confused, and I haven't found any solution that works yet.  I also threw in a few terminal commands too.

```
~$ lsusb
Bus 001 Device 002: ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b
Bus 001 Device 001: ID 0000:0000  
```

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.
```

```
~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```

```
~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017eae000 (usable)
[    0.000000]  BIOS-e820: 0000000017eae000 - 0000000017f00000 (reserved)
[    0.000000]  BIOS-e820: 0000000017f02000 - 0000000018002000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 382MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 97966) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    97966
[    0.000000]   HighMem     97966 ->    97966
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    97966
[    0.000000] On node 0 totalpages: 97966
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 733 pages used for memmap
[    0.000000]   Normal zone: 93137 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FD790 checksum 0
[    0.000000] ACPI: RSDP 000FD790, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD7A4, 0028 (r1 DELL    GX110          7 ASL        61)
[    0.000000] ACPI: FACP 000FD7CC, 0074 (r1 DELL    GX110          7 ASL        61)
[    0.000000] ACPI: DSDT FFFE5000, 181D (r1   DELL    dt_ex     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 17EAE000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18002000:e7afe000)
[    0.000000] Built 1 zonelists.  Total pages: 97201
[    0.000000] Kernel command line: root=UUID=f9943045-492d-438b-ba7b-1e67fa9232a4 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0130d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 864.616 MHz processor.
[   35.772915] Console: colour VGA+ 80x25
[   35.774150] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   35.775627] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   35.816743] Memory: 376844k/391864k available (2015k kernel code, 14408k reserved, 916k data, 364k init, 0k highmem)
[   35.816770] virtual kernel memory layout:
[   35.816773]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   35.816776]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   35.816780]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   35.816783]     lowmem  : 0xc0000000 - 0xd7eae000   ( 382 MB)
[   35.816786]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   35.816790]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   35.816793]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   35.816803] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   35.816894] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   35.896904] Calibrating delay using timer specific routine.. 1730.61 BogoMIPS (lpj=3461228)
[   35.896973] Security Framework v1.0.0 initialized
[   35.896992] SELinux:  Disabled at boot.
[   35.897030] Mount-cache hash table entries: 512
[   35.897335] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   35.897363] CPU: L1 I cache: 16K, L1 D cache: 16K
[   35.897369] CPU: L2 cache: 256K
[   35.897380] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   35.897403] Compat vDSO mapped to ffffe000.
[   35.897443] Checking 'hlt' instruction... OK.
[   35.913142] SMP alternatives: switching to UP code
[   35.913543] Freeing SMP alternatives: 11k freed
[   35.914244] Early unpacking initramfs... done
[   36.703501] ACPI: Core revision 20070126
[   36.711331] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   36.726671] ACPI: setting ELCR to 0200 (from 0e20)
[   36.727086] CPU0: Intel Pentium III (Coppermine) stepping 06
[   36.727101] SMP motherboard not detected.
[   36.727108] Local APIC not detected. Using dummy APIC emulation.
[   36.727221] Brought up 1 CPUs
[   36.727605] Booting paravirtualized kernel on bare hardware
[   36.727744] Time: 19:07:29  Date: 09/15/107
[   36.727828] NET: Registered protocol family 16
[   36.728149] EISA bus registered
[   36.728177] ACPI: bus type pci registered
[   36.753625] PCI: PCI BIOS revision 2.10 entry at 0xfc0ce, last bus=1
[   36.753632] PCI: Using configuration type 1
[   36.753637] Setting up standard PCI resources
[   36.757200] ACPI: EC: Look up EC in DSDT
[   36.763092] ACPI: Interpreter enabled
[   36.763102] ACPI: (supports S0 S1 S4 S5)
[   36.763140] ACPI: Using PIC for interrupt routing
[   36.771201] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   36.771244] PCI: Probing PCI hardware (bus 00)
[   36.771574] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   36.771582] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   36.772146] PCI: Transparent bridge - 0000:00:1e.0
[   36.772186] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   36.772748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   36.776770] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   36.777173] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   36.777564] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   36.777956] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   36.778217] Linux Plug and Play Support v0.97 (c) Adam Belay
[   36.778247] pnp: PnP ACPI init
[   36.778277] ACPI: bus type pnp registered
[   36.793041] pnp: PnP ACPI: found 14 devices
[   36.793050] ACPI: ACPI bus type pnp unregistered
[   36.793062] PnPBIOS: Disabled by ACPI PNP
[   36.793205] PCI: Using ACPI for IRQ routing
[   36.793213] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   36.797671] NET: Registered protocol family 8
[   36.797677] NET: Registered protocol family 20
[   36.797882] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   36.797891] pnp: 00:00: iomem range 0x100000-0xffffff could not be reserved
[   36.797899] pnp: 00:00: iomem range 0x1000000-0x17eadfff could not be reserved
[   36.797907] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   36.797936] pnp: 00:0d: ioport range 0x800-0x85f has been reserved
[   36.797943] pnp: 00:0d: ioport range 0xc00-0xc7f has been reserved
[   36.797950] pnp: 00:0d: ioport range 0x860-0x8ff could not be reserved
[   36.800635] Time: tsc clocksource has been installed.
[   36.828691] PCI: Bridge: 0000:00:1e.0
[   36.828698]   IO window: e000-efff
[   36.828710]   MEM window: fd000000-feffffff
[   36.828718]   PREFETCH window: f9000000-f9ffffff
[   36.828740] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   36.828775] NET: Registered protocol family 2
[   36.868753] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   36.868904] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   36.869617] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   36.870295] TCP: Hash tables configured (established 16384 bind 16384)
[   36.870305] TCP reno registered
[   36.881081] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   37.532758]  it is
[   38.361783] Freeing initrd memory: 7051k freed
[   38.362663] audit: initializing netlink socket (disabled)
[   38.362701] audit(1192475250.488:1): initialized
[   38.368480] VFS: Disk quotas dquot_6.5.1
[   38.368688] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   38.369013] io scheduler noop registered
[   38.369021] io scheduler anticipatory registered
[   38.369027] io scheduler deadline registered
[   38.369089] io scheduler cfq registered (default)
[   38.369130] Boot video device is 0000:00:01.0
[   38.369568] isapnp: Scanning for PnP cards...
[   38.723487] isapnp: No Plug & Play device found
[   38.805435] Real Time Clock Driver v1.12ac
[   38.805657] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.805796] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.806239] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.807799] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.808579] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.810423] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.811050] input: Macintosh mouse button emulation as /class/input/input0
[   38.811281] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   38.813501] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.813516] serio: i8042 AUX port at 0x60,0x64 irq 12
[   38.813947] mice: PS/2 mouse device common for all mice
[   38.814227] EISA: Probing bus 0 at eisa.0
[   38.814281] EISA: Detected 0 cards.
[   38.814540] TCP cubic registered
[   38.814585] NET: Registered protocol family 1
[   38.814654] Using IPI No-Shortcut mode
[   38.815062]   Magic number: 11:232:142
[   38.816799] Freeing unused kernel memory: 364k freed
[   38.884074] input: AT Translated Set 2 keyboard as /class/input/input1
[   40.377417] AppArmor: AppArmor initialized<5>audit(1192475252.488:2):  type=1505 info="AppArmor initialized" pid=1155
[   40.402204] fuse init (API version 7.8)
[   40.419888] Failure registering capabilities with primary security module.
[   40.464746] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   42.134335] SCSI subsystem initialized
[   42.156877] libata version 2.21 loaded.
[   42.171413] ata_piix 0000:00:1f.1: version 2.11
[   42.171556] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   42.171836] scsi0 : ata_piix
[   42.171974] scsi1 : ata_piix
[   42.172030] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   42.172039] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   42.335179] ata1.00: ATA-4: Maxtor 90432D3, WAS82739, max UDMA/33
[   42.335194] ata1.00: 8440992 sectors, multi 8: LBA 
[   42.351171] ata1.00: configured for UDMA/33
[   42.472254] usbcore: registered new interface driver usbfs
[   42.472333] usbcore: registered new interface driver hub
[   42.472392] usbcore: registered new device driver usb
[   42.622759] USB Universal Host Controller Interface driver v3.0
[   42.728027] Floppy drive(s): fd0 is 1.44M
[   42.794135] FDC 0 is a National Semiconductor PC87306
[   42.834895] ata2.00: ATAPI: LG CD-RW CED-8080B, 1.04, max MWDMA2
[   42.834918] ata2.01: ATAPI: IOMEGA  ZIP 250       ATAPI       Floppy, 51.G, max MWDMA0, CDB intr
[   43.006726] ata2.00: configured for MWDMA2
[   43.178651] ata2.01: configured for PIO3
[   43.178991] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 90432D3   WAS8 PQ: 0 ANSI: 5
[   43.179829] scsi 1:0:0:0: CD-ROM            LG       CD-RW CED-8080B  1.04 PQ: 0 ANSI: 5
[   43.184466] scsi 1:0:1:0: Direct-Access     IOMEGA   ZIP 250          51.G PQ: 0 ANSI: 5
[   43.185655] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   43.185666] PCI: setting IRQ 11 as level-triggered
[   43.185672] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   43.247000] sd 0:0:0:0: [sda] 8440992 512-byte hardware sectors (4322 MB)
[   43.249297] sd 0:0:0:0: [sda] Write Protect is off
[   43.249310] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   43.249387] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.249535] sd 0:0:0:0: [sda] 8440992 512-byte hardware sectors (4322 MB)
[   43.249559] sd 0:0:0:0: [sda] Write Protect is off
[   43.249566] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   43.249604] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.249618]  sda: sda1 sda2 < sda5 >
[   43.296134] sd 0:0:0:0: [sda] Attached SCSI disk
[   43.301591] sd 1:0:1:0: [sdb] Attached SCSI removable disk
[   43.316309] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   43.316752] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   43.317124] sd 1:0:1:0: Attached scsi generic sg2 type 0
[   43.345315] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   43.345335] Uniform CD-ROM driver Revision: 3.20
[   43.346501] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   43.993822] Attempting manual resume
[   43.993833] swsusp: Resume From Partition 8:5
[   43.993838] PM: Checking swsusp image.
[   44.020209] PM: Resume from disk failed.
[   44.126709] kjournald starting.  Commit interval 5 seconds
[   44.126746] EXT3-fs: mounted filesystem with ordered data mode.
[   58.193365] scsi2 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   58.193373]         <Adaptec 2902/04/10/15/20C/30C SCSI adapter>
[   58.193377]         aic7850: Ultra Single Channel A, SCSI Id=7, 3/253 SCBs
[   58.193381] 
[   58.195585] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   58.195600] PCI: setting IRQ 5 as level-triggered
[   58.195607] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   58.195627] 3c59x: Donald Becker and others.
[   58.195642] 0000:01:0c.0: 3Com PCI 3c905C Tornado at d8814c00.
[   58.217609] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   58.217635] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   58.217643] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   58.218293] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   58.218343] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ff80
[   58.218692] usb usb1: configuration #1 chosen from 1 choice
[   58.218762] hub 1-0:1.0: USB hub found
[   58.218788] hub 1-0:1.0: 2 ports detected
[   58.561260] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   58.729350] usb 1-1: configuration #1 chosen from 1 choice
[   63.833475] iTCO_vendor_support: vendor-support=0
[   63.837306] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   63.837490] iTCO_wdt: Found a ICH TCO device (Version=1, TCOBASE=0x0860)
[   63.837570] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   63.923966] Linux agpgart interface v0.102 (c) Dave Jones
[   63.966322] agpgart: Detected an Intel i810 Chipset.
[   63.971861] agpgart: detected 4MB dedicated video ram.
[   63.978203] agpgart: AGP aperture is 64M @ 0xf4000000
[   64.044392] Intel 82802 RNG detected
[   64.095497] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   64.106428] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   64.420685] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[   66.080489] gameport: EMU10K1 is pci0000:01:0b.1/gameport0, io 0xecf0, speed 1125kHz
[   66.343390] input: PC Speaker as /class/input/input2
[   67.032137] prism2usb_init: prism2_usb.o: 0.2.8 Loaded
[   67.032147] prism2usb_init: dev_info is: prism2_usb
[   67.032678] usbcore: registered new interface driver prism2_usb
[   67.808875] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   67.812940] parport_pc 00:0c: reported by Plug and Play ACPI
[   67.813061] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[   68.091428] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[   68.091443] PCI: setting IRQ 9 as level-triggered
[   68.091450] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[   68.886855] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[   68.886875] prism2sta_getcardinfo: Failed to retrieve NICIDENTITY
[   68.886883] prism2sta_getcardinfo: Failed, result=-5
[   68.886889] prism2sta_ifstate: prism2sta_getcardinfo() failed,result=-5
[   69.886306] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[   70.640194] lp0: using parport0 (interrupt-driven).
[   70.755438] Adding 240932k swap on /dev/sda5.  Priority:-1 extents:1 across:240932k
[   71.235784] EXT3 FS on sda1, internal journal
[   73.615989] input: Power Button (FF) as /class/input/input4
[   73.616671] ACPI: Power Button (FF) [PWRF]
[   73.670441] No dock devices found.
[   77.716418] eth0:  setting half-duplex.
[   77.860077] ppdev: user-space parallel port driver
[   78.362335] audit(1192475290.919:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4515 profile="/usr/sbin/cupsd"
[   78.463239] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   78.463255] apm: overridden by ACPI.
[   78.872942] Failure registering capabilities with primary security module.
[   79.286501] Bluetooth: Core ver 2.11
[   79.286804] NET: Registered protocol family 31
[   79.286810] Bluetooth: HCI device and connection manager initialized
[   79.286819] Bluetooth: HCI socket layer initialized
[   79.341086] Bluetooth: L2CAP ver 2.8
[   79.341099] Bluetooth: L2CAP socket layer initialized
[   79.416250] Bluetooth: RFCOMM socket layer initialized
[   79.416472] Bluetooth: RFCOMM TTY layer initialized
[   79.416479] Bluetooth: RFCOMM ver 1.8
[  615.170803] NET: Registered protocol family 10
[  615.171331] lo: Disabled Privacy Extensions
[  615.171613] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

```
~$ sudo lshw -C network
[sudo] password for basement:
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:47:54:bd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.8 link=no multicast=yes

```

Finally, I've tried configuring the card manually with iwconfig.  I have a 128-bit ASCII WEP code.  I'm not completely sure I did it right though.  If anyone could give me a little help, I would be very thankful  :)

---

### Post by tormod on 2007-10-19
This is the problem:
[   68.886855] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[   68.886875] prism2sta_getcardinfo: Failed to retrieve NICIDENTITY
[   68.886883] prism2sta_getcardinfo: Failed, result=-5
[   68.886889] prism2sta_ifstate: prism2sta_getcardinfo() failed,result=-5
[   69.886306] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)

You might have to unplug and replug the device a couple of times before it will work. Run **tail -f /var/log/syslog** while you plug it, so you can see the messages. My card always work at reboot, but if I plug it in after boot, I usually have to unplug/replug a magic 5 times.


Other than that it should work fine with network-admin or network-manager.

---

### Post by SoxFan33 on 2007-10-24
Sorry I didn't repond for a few days.  Gutsy final was released, so I installed that, and I was really busy.  I just got a chance to try fixing it today.  I used tail **-f /var/log/syslog** but all I saw was what was coming up in dmesg.  It still wasn't working right after 7 plugins/unplugs.  Is there a way to manualy set up up?

---

### Post by tormod on 2007-10-24
I am afraid this is a race condition / timing issue. Can you try to make the computer very busy (compile some stuff, or watch a movie, or do a software upgrade etc) and plug in the card at the same time?

I haven't find a way to work around it other than unplug/replug. Please try more than 7 times if only to verify you see the same as I do. Now that I know more than me are seeing this, I will report it upstream when I find some time.

---

### Post by SoxFan33 on 2007-10-24
Ok.  Will do tomorrow after school. I'll report then

---

### Post by tormod on 2007-10-29
> **SoxFan33 said:**
> The adaptor is detected and works.  However, I have to manually input the SSID and WEP code every time I start the computer though the Network Manger applet in the task bar. Do you happen to have a hidden essid? It's a know issue with the prism2_usb driver that it won't report hidden networks to the network-manager, so that you will not get automatically reconnected to them. "Manual configuration..." / network-admin should work fine anyway.

BTW, I reported the hfa384x_usbctlx_complete_sync error messages upstream, but at the same time I am not sure they make any problems other than being irritating.

---

### Post by SoxFan33 on 2007-10-29
No I don't have a hidden SSID.  Its out in the open for all to see :P.

Anways, I guess I forgot to post the other day.  I logged on, inteded to post what I tried, and guess I never did :/

None of your suggestions seemed to work.  Unplugging and Plugging back in just didn't want to work.  However, I'm now working more on getting a manual configuration working.  When I do put in a manual configuration, It is detected as a wireless device at boot, but still won't connect to the network.  Maybe i'll experiment with KNetworkManager some more.

And I must say, I did some work on my Gutsy install on my computer, and I'm loving it.  I'm considering a switch from Vista, but still dualbooting both.  The only real problem I have is Adobe CS3 (I use Photoshop, Illustrator, and sometimes Dreamweaver).  I don't really like gimp.

---

### Post by tormod on 2007-10-30
When you say manual configuration, do you mean editing /etc/network/interfaces?

I'd suggest you file a bug on linux-wlan-ng and attach that file, dmesg output and /var/log/syslog

---

### Post by SoxFan33 on 2007-10-30
> **tormod said:**
> When you say manual configuration, do you mean editing /etc/network/interfaces?

I'd suggest you file a bug on linux-wlan-ng and attach that file, dmesg output and /var/log/syslog

Well, either configuring it through network manager or the /etc/network/interfaces file (although NM edits that).  I'm also going to do some experimenting with KNetworkManager which I've heard is better with wireless.

---

### Post by tormod on 2007-10-30
> **SoxFan33 said:**
> Well, either configuring it through network manager or the /etc/network/interfaces file (although NM edits that).  I'm also going to do some experimenting with KNetworkManager which I've heard is better with wireless.

Network-manager does not edit the interfaces file, but when you choose "Manual configuration..." it starts network-admin (same as in System->Administration) which does.

network-admin should be the fool-proof way of configuring it. If it doesn't work then, it can be a driver or hardware issue. But to be sure, I have to see the log files.

---

