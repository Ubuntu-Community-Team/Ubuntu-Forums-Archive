---
title: "[SOLVED] Huawei E172 - Vodafone USB Modem Stick"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by mundo on 2008-07-24
I have tried various things but I cannot get this to work on Ubuntu.  I believe that this can be done but can anyone give me step by step instructions.

---

### Post by mundo on 2008-07-24
I have found this on the betavine website but when I tried to run it, it said that I didn't have permissions even though I right clicked on the file and checked run as executable.

[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

vodafone-mobile-connect-card-driver-for-linux-2.0.beta3-ALL-i386-installer.run

---

### Post by cpetercarter on 2008-07-24
Hav a look at [this]("http://ubuntuforums.org/showthread.php?t=843973"). It contains instructions for the E220 modem - it would be interesting if you could report whether they also work for the E172.

---

### Post by mundo on 2008-07-24
Thanks, I hadn't found that one, I'll give it a try tonight and report back.

---

### Post by wheezy-weasel on 2008-07-28
It didn't work for me :(
Have posted same issue [here]("http://ubuntuforums.org/showthread.php?p=5476343#post5476343").

---

### Post by mundo on 2008-08-03
Didn't work for me either :(

I have downloaded and installed "Vodafone Mobile Connect Card" software from Betavine.  I originally tried 2.0.beta3 ( vodafone-mobile-connect-card-driver-for-linux-2.0.beta3-ALL-i386-installer.run) but a number of people on other forums advised that they had problems with this and I couldn't get it to work so now I have installed 1.99.17 (vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb) but I can't get that to work either.

[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

Here is my dmesg output

```
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 387827
[    0.000000] Kernel command line: root=UUID=4b3c75e3-f58b-449c-a1d2-abb305b80e92 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1395.516 MHz processor.
[    3.837003] Console: colour VGA+ 80x25
[    3.837009] console [tty0] enabled
[    3.837380] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    3.837886] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    3.924792] Memory: 1537716k/1563520k available (2177k kernel code, 24492k reserved, 1006k data, 368k init, 646016k highmem)
[    3.924804] virtual kernel memory layout:
[    3.924805]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    3.924807]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    3.924809]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    3.924810]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    3.924812]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    3.924813]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[    3.924815]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[    3.924820] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    3.924891] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    4.004834] Calibrating delay using timer specific routine.. 2793.01 BogoMIPS (lpj=5586022)
[    4.004877] Security Framework initialized
[    4.004889] SELinux:  Disabled at boot.
[    4.004912] AppArmor: AppArmor initialized
[    4.004917] Failure registering capabilities with primary security module.
[    4.004928] Mount-cache hash table entries: 512
[    4.005119] Initializing cgroup subsys ns
[    4.005128] Initializing cgroup subsys cpuacct
[    4.005144] CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[    4.005158] CPU: L1 I cache: 32K, L1 D cache: 32K
[    4.005161] CPU: L2 cache: 2048K
[    4.005165] CPU: After all inits, caps: afe9fbbf 00000000 00000000 00002040 00000180 00000000 00000000 00000000
[    4.005178] Compat vDSO mapped to ffffe000.
[    4.005196] Checking 'hlt' instruction... OK.
[    4.021276] SMP alternatives: switching to UP code
[    4.023514] Freeing SMP alternatives: 11k freed
[    4.023658] Early unpacking initramfs... done
[    4.461598] ACPI: Core revision 20070126
[    4.461747] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    4.478120] CPU0: Intel(R) Pentium(R) M processor 1.40GHz stepping 06
[    4.478147] Total of 1 processors activated (2793.01 BogoMIPS).
[    4.478279] ENABLING IO-APIC IRQs
[    4.478449] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    4.624248] Brought up 1 CPUs
[    4.624273] CPU0 attaching sched-domain:
[    4.624276]  domain 0: span 01
[    4.624278]   groups: 01
[    4.624466] net_namespace: 64 bytes
[    4.624474] Booting paravirtualized kernel on bare hardware
[    4.624999] Time: 15:39:04  Date: 08/03/08
[    4.625027] NET: Registered protocol family 16
[    4.625247] EISA bus registered
[    4.625267] ACPI: bus type pci registered
[    4.625512] PCI: PCI BIOS revision 2.10 entry at 0xfd8c8, last bus=5
[    4.625515] PCI: Using configuration type 1
[    4.625523] Setting up standard PCI resources
[    4.628388] ACPI: EC: EC description table is found, configuring boot EC
[    4.635188] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    4.756499] ACPI: Interpreter enabled
[    4.756502] ACPI: (supports S0 S3 S4 S5)
[    4.756518] ACPI: Using IOAPIC for interrupt routing
[    4.765483] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    4.765487] ACPI: EC: driver started in poll mode
[    4.765668] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    4.766141] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    4.766145] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    4.766557] PCI: Transparent bridge - 0000:00:1e.0
[    4.766621] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    4.766804] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    4.769705] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    4.769949] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    4.770189] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    4.770428] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    4.770668] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    4.770907] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    4.771127] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    4.771368] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    4.771535] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    4.771642] ACPI: Power Resource [PUBS] (on)
[    4.771692] Linux Plug and Play Support v0.97 (c) Adam Belay
[    4.771729] pnp: PnP ACPI init
[    4.771736] ACPI: bus type pnp registered
[    4.773089] pnpacpi: exceeded the max number of mem resources: 12
[    4.776967] pnp: PnP ACPI: found 10 devices
[    4.776970] ACPI: ACPI bus type pnp unregistered
[    4.776973] PnPBIOS: Disabled by ACPI PNP
[    4.777257] PCI: Using ACPI for IRQ routing
[    4.777260] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    4.800025] NET: Registered protocol family 8
[    4.800027] NET: Registered protocol family 20
[    4.800095] AppArmor: AppArmor Filesystem Enabled
[    4.804012] Time: tsc clocksource has been installed.
[    4.812045] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    4.812049] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    4.812052] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    4.812056] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[    4.812060] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    4.812063] system 00:00: iomem range 0x0-0x0 could not be reserved
[    4.812066] system 00:00: iomem range 0x0-0x0 could not be reserved
[    4.812070] system 00:00: iomem range 0x0-0x0 could not be reserved
[    4.812073] system 00:00: iomem range 0xdc000-0xdffff has been reserved
[    4.812077] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    4.812081] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    4.812084] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    4.812091] system 00:02: ioport range 0x1000-0x107f has been reserved
[    4.812095] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    4.812098] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    4.812102] system 00:02: ioport range 0x1600-0x167f has been reserved
[    4.812105] system 00:02: ioport range 0x1680-0x169f has been reserved
[    4.842539] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[    4.842542]   IO window: 00003000-000030ff
[    4.842546]   IO window: 00003400-000034ff
[    4.842551]   PREFETCH window: f0000000-f3ffffff
[    4.842555]   MEM window: d4000000-d7ffffff
[    4.842558] PCI: Bridge: 0000:00:1e.0
[    4.842561]   IO window: 3000-7fff
[    4.842567]   MEM window: d0200000-dfffffff
[    4.842571]   PREFETCH window: f0000000-f7ffffff
[    4.842583] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    4.842599] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.842613] NET: Registered protocol family 2
[    4.880003] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    4.880264] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    4.881226] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    4.881804] TCP: Hash tables configured (established 131072 bind 65536)
[    4.881809] TCP reno registered
[    4.892109] checking if image is initramfs... it is
[    5.343455] Switched to high resolution mode on CPU 0
[    5.748014] Freeing initrd memory: 7316k freed
[    5.748268] Simple Boot Flag at 0x35 set to 0x1
[    5.748753] audit: initializing netlink socket (disabled)
[    5.748773] audit(1217777944.712:1): initialized
[    5.748996] highmem bounce pool size: 64 pages
[    5.751281] VFS: Disk quotas dquot_6.5.1
[    5.751374] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.751535] io scheduler noop registered
[    5.751538] io scheduler anticipatory registered
[    5.751540] io scheduler deadline registered
[    5.751553] io scheduler cfq registered (default)
[    5.751570] Boot video device is 0000:00:02.0
[    5.751952] isapnp: Scanning for PnP cards...
[    6.104453] isapnp: No Plug & Play device found
[    6.136331] Real Time Clock Driver v1.12ac
[    6.136451] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    6.137123] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17
[    6.137133] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    6.137851] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    6.137936] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    6.138048] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    6.144466] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.144471] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.150621] mice: PS/2 mouse device common for all mice
[    6.150748] EISA: Probing bus 0 at eisa.0
[    6.150754] Cannot allocate resource for EISA slot 1
[    6.150757] Cannot allocate resource for EISA slot 2
[    6.150760] Cannot allocate resource for EISA slot 3
[    6.150762] Cannot allocate resource for EISA slot 4
[    6.150765] Cannot allocate resource for EISA slot 5
[    6.150768] Cannot allocate resource for EISA slot 6
[    6.150770] Cannot allocate resource for EISA slot 7
[    6.150775] EISA: Detected 0 cards.
[    6.150779] cpuidle: using governor ladder
[    6.150781] cpuidle: using governor menu
[    6.150891] NET: Registered protocol family 1
[    6.150922] Using IPI No-Shortcut mode
[    6.150958] registered taskstats version 1
[    6.151081]   Magic number: 4:958:688
[    6.151186] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.151189] EDD information not available.
[    6.151429] Freeing unused kernel memory: 368k freed
[    6.154868] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    7.407931] fuse init (API version 7.9)
[    7.434353] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    7.434360] ACPI: Processor [CPU] (supports 8 throttling states)
[    7.436782] ACPI: Thermal Zone [THM0] (57 C)
[    8.185339] usbcore: registered new interface driver usbfs
[    8.185370] usbcore: registered new interface driver hub
[    8.201888] usbcore: registered new device driver usb
[    8.216200] USB Universal Host Controller Interface driver v3.0
[    8.216267] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    8.216280] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    8.216285] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    8.216687] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    8.216716] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001820
[    8.216872] usb usb1: configuration #1 chosen from 1 choice
[    8.216899] hub 1-0:1.0: USB hub found
[    8.216906] hub 1-0:1.0: 2 ports detected
[    8.288370] SCSI subsystem initialized
[    8.320189] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[    8.320203] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    8.320209] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    8.320238] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    8.320265] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001840
[    8.320402] usb usb2: configuration #1 chosen from 1 choice
[    8.320429] hub 2-0:1.0: USB hub found
[    8.320436] hub 2-0:1.0: 2 ports detected
[    8.361703] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    8.361707] Copyright (c) 1999-2006 Intel Corporation.
[    8.376011] libata version 3.00 loaded.
[    8.424072] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[    8.424088] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    8.424093] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    8.424120] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    8.424147] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001860
[    8.424277] usb usb3: configuration #1 chosen from 1 choice
[    8.424307] hub 3-0:1.0: USB hub found
[    8.424315] hub 3-0:1.0: 2 ports detected
[    8.528897] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[    8.528914] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    8.528918] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    8.528948] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    8.532867] ehci_hcd 0000:00:1d.7: debug port 1
[    8.532873] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    8.532885] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0100000
[    8.547812] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    8.547940] usb usb4: configuration #1 chosen from 1 choice
[    8.547968] hub 4-0:1.0: USB hub found
[    8.547975] hub 4-0:1.0: 6 ports detected
[    8.651913] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 20 (level, low) -> IRQ 21
[    8.920896] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0a:e4:2e:e5:43
[    9.113414] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    9.113545] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    9.113554] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[    9.113592] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    9.113606] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[    9.123176] ata_piix 0000:00:1f.1: version 2.12
[    9.123193] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[    9.123226] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    9.123841] scsi0 : ata_piix
[    9.124408] scsi1 : ata_piix
[    9.125395] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    9.125399] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    9.287359] ata1.00: ATA-5: HITACHI_DK13FA-40B, 00MCA0B4, max UDMA/100
[    9.287364] ata1.00: 78140160 sectors, multi 16: LBA 
[    9.295287] ata1.00: configured for UDMA/100
[    9.382887] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    9.450987] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK13FA-4 00MC PQ: 0 ANSI: 5
[    9.458828] Driver 'sd' needs updating - please use bus_type methods
[    9.458903] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    9.458918] sd 0:0:0:0: [sda] Write Protect is off
[    9.458922] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.458940] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.458992] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    9.459003] sd 0:0:0:0: [sda] Write Protect is off
[    9.459006] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.459024] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.459028]  sda:<6>usb 2-1: configuration #1 chosen from 1 choice
[    9.559622]  sda1 sda2 sda3 < sda5 sda6 >
[    9.603450] sd 0:0:0:0: [sda] Attached SCSI disk
[    9.614683] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    9.630637] usbcore: registered new interface driver libusual
[    9.638010] Initializing USB Mass Storage driver...
[    9.642106] scsi2 : SCSI emulation for USB Mass Storage devices
[    9.642712] usbcore: registered new interface driver usb-storage
[    9.642716] USB Mass Storage support registered.
[    9.642795] usb-storage: device found at 2
[    9.642797] usb-storage: waiting for device to settle before scanning
[   10.169931] Attempting manual resume
[   10.169936] swsusp: Resume From Partition 8:6
[   10.169938] PM: Checking swsusp image.
[   10.170131] PM: Resume from disk failed.
[   10.219898] kjournald starting.  Commit interval 5 seconds
[   10.219910] EXT3-fs: mounted filesystem with ordered data mode.
[   14.638378] usb-storage: device scan complete
[   14.641371] scsi 2:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   14.644360] scsi 2:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[   14.644677] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[   14.649380] sd 2:0:0:1: [sdb] Attached SCSI removable disk
[   14.649414] sd 2:0:0:1: Attached scsi generic sg2 type 0
[   25.013543] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   25.828507] Linux agpgart interface v0.102
[   25.948345] intel_rng: FWH not detected
[   25.992328] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.056314] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.186567] agpgart: Detected an Intel 855GM Chipset.
[   26.187115] agpgart: Detected 8060K stolen memory.
[   26.208079] agpgart: AGP aperture is 128M @ 0xe0000000
[   26.435807] iTCO_vendor_support: vendor-support=0
[   26.495744] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   26.495836] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   26.495870] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   26.806690] input: Power Button (FF) as /devices/virtual/input/input3
[   26.815377] ACPI: Power Button (FF) [PWRF]
[   26.815456] input: Lid Switch as /devices/virtual/input/input4
[   26.815672] ACPI: Lid Switch [LID]
[   26.815727] input: Sleep Button (CM) as /devices/virtual/input/input5
[   26.831357] ACPI: Sleep Button (CM) [SLPB]
[   27.686905] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   27.698376] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   28.545449] ieee80211_crypt: registered algorithm 'NULL'
[   28.580075] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   28.580080] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   28.784377] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0555]
[   28.846063] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   28.846067] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   28.890037] sdhci: Secure Digital Host Controller Interface driver
[   28.890041] sdhci: Copyright(c) Pierre Ossman
[   28.909799] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   28.909803] Socket status: 30000006
[   28.909807] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   28.909811] cs: IO port probe 0x3000-0x7fff: clean.
[   28.911239] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xdfffffff
[   28.911243] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[   28.953180] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 22
[   28.993870] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   29.065017] Non-volatile memory driver v1.2
[   29.192782] irda_init()
[   29.192800] NET: Registered protocol family 23
[   29.431424] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   29.446302] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input7
[   29.475740] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   29.475744] thinkpad_acpi: http://ibm-acpi.sf.net/
[   29.475746] thinkpad_acpi: ThinkPad BIOS 1UETD3WW (2.08 ), EC 1UHTB2WW-1.62
[   29.475749] thinkpad_acpi: IBM ThinkPad X40
[   29.479524] nsc-ircc 00:09: activated
[   29.479529] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   29.479544] nsc-ircc, chip->init
[   29.479553] nsc-ircc, Found chip at base=0x164e
[   29.479576] nsc-ircc, driver loaded (Dag Brattli)
[   29.480101] thinkpad_acpi: acpi_bus_get_device(bay) failed: -19
[   29.480105] thinkpad_acpi: disabling subdriver bay
[   29.481879] thinkpad_acpi: CMOS NVRAM (6) and EC (0) do not agree on display brightness level
[   29.482121] input: ThinkPad Extra Buttons as /devices/virtual/input/input8
[   29.849351] ACPI: AC Adapter [AC] (on-line)
[   29.868079] ACPI: Battery Slot [BAT0] (battery present)
[   29.912232] usbcore: registered new interface driver usbserial
[   29.912252] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   29.912292] usbcore: registered new interface driver usbserial_generic
[   29.912295] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   29.924432] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[   29.924458] option 2-1:1.0: GSM modem (1-port) converter detected
[   29.924642] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[   29.924653] option 2-1:1.1: GSM modem (1-port) converter detected
[   29.924731] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[   29.924741] option 2-1:1.2: GSM modem (1-port) converter detected
[   29.924816] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
[   29.924826] usbcore: registered new interface driver option
[   29.924829] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[   30.103017] Driver 'sr' needs updating - please use bus_type methods
[   30.135805] sr0: scsi-1 drive
[   30.135809] Uniform CD-ROM driver Revision: 3.20
[   30.135868] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   31.599386] IrDA: Registered device irda0
[   31.599391] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   31.608105] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   31.608136] sdhci: SDHCI controller found at 0000:02:00.1 [1180:0822] (rev 13)
[   31.608155] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 17 (level, low) -> IRQ 17
[   31.609166] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   31.611204] mmc0: SDHCI at 0xd0221000 irq 17 DMA
[   31.611247] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[   31.611263] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   31.807476] cs: IO port probe 0x100-0x3af: clean.
[   31.808449] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   31.808874] cs: IO port probe 0x820-0x8ff: clean.
[   31.809229] cs: IO port probe 0xc00-0xcf7: clean.
[   31.809738] cs: IO port probe 0xa00-0xaff: clean.
[   32.532967] intel8x0_measure_ac97_clock: measured 55490 usecs
[   32.532972] intel8x0: clocking to 48000
[   33.715140] lp: driver loaded but no devices found
[   33.953267] Adding 811240k swap on /dev/sda6.  Priority:-1 extents:1 across:811240k
[   34.603971] EXT3 FS on sda5, internal journal
[   36.049926] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.593838] ACPI: ACPI Dock Station Driver 
[   36.710923] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: found ejectable bay
[   36.710931] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: Adding notify handler
[   36.710975] ACPI: Bay [\_SB_.PCI0.IDE0.SCND.MSTR] Added
[   36.710984] ACPI: \_SB_.PCI0.IDE0.SCDM.MSTR: found ejectable bay
[   36.710989] ACPI: \_SB_.PCI0.IDE0.SCDM.MSTR: Adding notify handler
[   36.711010] ACPI: Error installing bay notify handler
[   36.711014] ACPI: Bay [\_SB_.PCI0.IDE0.SCDM.MSTR] Added
[   38.378386] IBM machine detected. Enabling interrupts during APM calls.
[   38.378393] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   38.378395] apm: overridden by ACPI.
[   38.532152] ppdev: user-space parallel port driver
[   38.782213] audit(1217777978.338:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4912 profile="/usr/sbin/cupsd" namespace="default"
[   38.989175] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input9
[   91.941958] Marking TSC unstable due to: cpufreq changes.
[   91.971724] Time: acpi_pm clocksource has been installed.
[   92.394901] Clocksource tsc unstable (delta = -258859367 ns)
[   95.915123] Bluetooth: Core ver 2.11
[   95.916102] NET: Registered protocol family 31
[   95.916111] Bluetooth: HCI device and connection manager initialized
[   95.916120] Bluetooth: HCI socket layer initialized
[   95.968353] Bluetooth: L2CAP ver 2.9
[   95.968363] Bluetooth: L2CAP socket layer initialized
[   96.095263] Bluetooth: RFCOMM socket layer initialized
[   96.095289] Bluetooth: RFCOMM TTY layer initialized
[   96.095295] Bluetooth: RFCOMM ver 1.8
[   43.379025] [drm] Initialized drm 1.1.0 20060810
[   43.382390] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.382398] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   43.382467] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   43.382480] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   43.382533] [drm] Initialized i915 1.6.0 20060119 on minor 1
[  177.213538] NET: Registered protocol family 10
[  177.214559] lo: Disabled Privacy Extensions
[  177.216255] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  177.217179] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  153.489429] NET: Registered protocol family 17
[   88.211138] UDF-fs: No VRS found
[  702.438798] usb 2-1: USB disconnect, address 2
[  702.441330] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  702.441376] option 2-1:1.0: device disconnected
[  702.441959] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  702.441995] option 2-1:1.1: device disconnected
[  702.442567] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  702.442604] option 2-1:1.2: device disconnected
[  705.688786] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  705.853062] usb 2-1: configuration #1 chosen from 1 choice
[  705.858235] option 2-1:1.0: GSM modem (1-port) converter detected
[  705.858514] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[  705.865038] option 2-1:1.1: GSM modem (1-port) converter detected
[  705.865216] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[  705.868963] option 2-1:1.2: GSM modem (1-port) converter detected
[  705.869134] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
[  705.908820] scsi3 : SCSI emulation for USB Mass Storage devices
[  705.911592] usb-storage: device found at 3
[  705.911601] usb-storage: waiting for device to settle before scanning
[  712.327668] usb-storage: device scan complete
[  712.330685] scsi 3:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  712.333670] scsi 3:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  712.374609] sr1: scsi-1 drive
[  712.374731] sr 3:0:0:0: Attached scsi CD-ROM sr1
[  712.374831] sr 3:0:0:0: Attached scsi generic sg1 type 5
[  712.380721] sd 3:0:0:1: [sdb] Attached SCSI removable disk
[  712.380815] sd 3:0:0:1: Attached scsi generic sg2 type 0
[ 1238.879245] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1240.757492] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1241.008100] ieee80211_crypt: registered algorithm 'TKIP'
[ 1258.403950] eth1: no IPv6 routers present

```

and here is my wvdial.conf:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Username = web
Password = web
Carrier Check = no
```

and here is sudo wvdial:

```

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Aug  3 17:07:08 2008
--> Pid of pppd: 8039
--> Disconnecting at Sun Aug  3 17:07:09 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

```

---

### Post by wheezy-weasel on 2008-08-03
Hi

The issues with the vmcc seem to be caused by a driver conflict. Have you tried black listing the airprime module?
```

sudo echo "blacklist airprime" > /etc/modprobe.d/blacklist-airprime
```
roboot
Delete the ~/.vmc2 directory and try again.

For ref. my thread at [betavine]("http://betavine.net/bvportal/forums/index.html?threadId=ff8080811b2fbbfd011b63d3ccd6245f&postPage=1").

---

### Post by mundo on 2008-08-03
I've managed to get this working now by using Network Manager 0.7

[http://ubuntuforums.org/showthread.php?t=797059]("http://ubuntuforums.org/showthread.php?t=797059")

---

