---
title: "How to set Hardy to auto detect when you switch on the light same as blue tooth?"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Suky on 2008-05-08
Hi,

I'm using Hardy and successfully setup wireless for Broadcom 43xx Ver 0.2. 

1.) I would like to ask for when I turn on my laptop with wireless switch off, I can't use the wireless. How to set Hardy to auto detect when switch wireless on same as blue tooth. 

For now, when I want to use wireless connection, I must be reboot with turn the wireless switch on!!!!

2.) I can't connect to my wireless network after I connect to wire network and get connect back to wireless. It's connect to a different wireless network that can detected and connected. 

I'm not quite sure these are the limitation on Hardy or not? compare with wireless function on windows XP.

Thanks in advance for any suggestion

---

### Post by luisromangz on 2008-05-08
I'm using a bcm4318 integrated wireless adapter in my laptop, with the new b43 drivers, and NetworkManager, and it detects automatically when the wireless network becames active. Are you using NetworkManager or other method to connect?

---

### Post by Suky on 2008-05-08
Hi, I'm using HP Compaq 6515b. 
How to check the version of b43, I installed by following the instructions from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851) ,my driver is sp37950 download from HP.

I use Network Manager 0.6.6, checked by right-click --> about 

> My H/W 

lspci -nn = 10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)

---

### Post by luisromangz on 2008-05-09
Which version of Ubuntu are you using? Gusty, Hardy? It seems from the tutorial that you are using ndiswrapper... what are the output of dmesg and the ndiswrapper commands?

---

### Post by Suky on 2008-05-11
I'm using Hardy and ndiswrapper for wireless

> ndiswrapper -l
bcmwl5 : driver installed


I don't know what you want to see in the log, So this is output from 'dmesg' 

```
[   18.242483] Console: colour VGA+ 80x25
[   18.242486] console [tty0] enabled
[   18.242541] Checking aperture...
[   18.242544] CPU 0: aperture @ 9268000000 size 32 MB
[   18.242546] Aperture too small (32 MB)
[   18.263388] No AGP bridge found
[   18.332766] Memory: 2443024k/2490048k available (2466k kernel code, 46636k reserved, 1309k data, 316k init)
[   18.332839] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   18.410831] Calibrating delay using timer specific routine.. 3201.64 BogoMIPS (lpj=6403294)
[   18.410905] Security Framework initialized
[   18.410911] SELinux:  Disabled at boot.
[   18.410963] AppArmor: AppArmor initialized
[   18.410967] Failure registering capabilities with primary security module.
[   18.411791] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   18.419208] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   18.422702] Mount-cache hash table entries: 256
[   18.423063] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.423066] CPU: L2 Cache: 512K (64 bytes/line)
[   18.423069] CPU 0/0 -> Node 0
[   18.423072] CPU: Physical Processor ID: 0
[   18.423073] CPU: Processor Core ID: 0
[   18.423137] SMP alternatives: switching to UP code
[   18.424686] Early unpacking initramfs... done
[   19.292048] ACPI: Core revision 20070126
[   19.292345] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.301331] ACPI: setting ELCR to 0200 (from 0c20)
[   19.383684] SMP motherboard not detected.
[   19.383692] Disabling APIC timer
[   19.383694] SMP disabled
[   19.383738] Brought up 1 CPUs
[   19.383781] CPU0 attaching sched-domain:
[   19.383784]  domain 0: span 01
[   19.383786]   groups: 01
[   19.383968] net_namespace: 120 bytes
[   19.384444] Time:  8:57:33  Date: 05/12/08
[   19.384475] NET: Registered protocol family 16
[   19.384668] ACPI: bus type pci registered
[   19.384747] PCI: Using configuration type 1
[   19.386416] ACPI: EC: Look up EC in DSDT
[   19.388039] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   19.637152] ACPI: Interpreter enabled
[   19.637158] ACPI: (supports S0 S3 S4 S5)
[   19.637173] ACPI: Using PIC for interrupt routing
[   19.648379] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[   19.648383] ACPI: EC: driver started in interrupt mode
[   19.648459] ACPI: PCI Root Bridge [C08B] (0000:00)
[   19.648678] pci 0000:00:12.0: set SATA to AHCI mode
[   19.649931] PCI: Transparent bridge - 0000:00:14.4
[   19.650005] ACPI: PCI Interrupt Routing Table [\_SB_.C08B._PRT]
[   19.650490] ACPI: PCI Interrupt Routing Table [\_SB_.C08B.C08C._PRT]
[   19.650651] ACPI: PCI Interrupt Routing Table [\_SB_.C08B.C0FC._PRT]
[   19.676371] ACPI: PCI Interrupt Link [C145] (IRQs *10 11)
[   19.676583] ACPI: PCI Interrupt Link [C146] (IRQs 10 11) *5
[   19.676785] ACPI: PCI Interrupt Link [C147] (IRQs 10 11) *0, disabled.
[   19.676995] ACPI: PCI Interrupt Link [C148] (IRQs 10 *11)
[   19.677196] ACPI: PCI Interrupt Link [C149] (IRQs 10 11) *0, disabled.
[   19.677399] ACPI: PCI Interrupt Link [C14A] (IRQs 9) *0, disabled.
[   19.677601] ACPI: PCI Interrupt Link [C14B] (IRQs 10 11) *0, disabled.
[   19.677822] ACPI: PCI Interrupt Link [C14C] (IRQs 10 *11)
[   19.677996] ACPI: Power Resource [C171] (off)
[   19.678241] ACPI: Power Resource [C231] (off)
[   19.678302] ACPI: Power Resource [C24D] (on)
[   19.678436] ACPI: Power Resource [C397] (off)
[   19.678554] ACPI: Power Resource [C398] (off)
[   19.678677] ACPI: Power Resource [C399] (off)
[   19.678794] ACPI: Power Resource [C39A] (off)
[   19.678853] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.678884] pnp: PnP ACPI init
[   19.678893] ACPI: bus type pnp registered
[   19.688251] pnp: PnP ACPI: found 14 devices
[   19.688255] ACPI: ACPI bus type pnp unregistered
[   19.688507] PCI: Using ACPI for IRQ routing
[   19.688510] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.688549] PCI: Cannot allocate resource region 0 of device 0000:00:14.2
[   19.697727] NET: Registered protocol family 8
[   19.697730] NET: Registered protocol family 20
[   19.697855] AppArmor: AppArmor Filesystem Enabled
[   19.709721] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   19.709724] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   19.709727] system 00:00: iomem range 0x100000-0xffffffff could not be reserved
[   19.709738] system 00:0a: ioport range 0x40b-0x40b has been reserved
[   19.709741] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   19.709744] system 00:0a: ioport range 0x4d6-0x4d6 has been reserved
[   19.709747] system 00:0a: ioport range 0x500-0x51f has been reserved
[   19.709750] system 00:0a: ioport range 0xc00-0xc01 has been reserved
[   19.709752] system 00:0a: ioport range 0xc14-0xc14 has been reserved
[   19.709755] system 00:0a: ioport range 0xc50-0xc51 has been reserved
[   19.709758] system 00:0a: ioport range 0xc52-0xc52 has been reserved
[   19.709761] system 00:0a: ioport range 0xc6c-0xc6c has been reserved
[   19.709764] system 00:0a: ioport range 0xc6f-0xc6f has been reserved
[   19.709766] system 00:0a: ioport range 0xcd0-0xcdf has been reserved
[   19.709771] system 00:0a: iomem range 0xffb00000-0xffbfffff could not be reserved
[   19.709774] system 00:0a: iomem range 0xfff00000-0xffffffff could not be reserved
[   19.709781] system 00:0c: ioport range 0x8000-0x802f has been reserved
[   19.709784] system 00:0c: ioport range 0x8100-0x811f has been reserved
[   19.709787] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   19.709790] system 00:0c: iomem range 0xfec00000-0xfec000ff could not be reserved
[   19.709793] system 00:0c: iomem range 0xfed45000-0xfed8ffff has been reserved
[   19.709800] system 00:0d: iomem range 0xcd400-0xcffff has been reserved
[   19.709803] system 00:0d: iomem range 0x0-0x7ffffff could not be reserved
[   19.709806] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   19.710242] PCI: Bridge: 0000:00:01.0
[   19.710244]   IO window: 4000-4fff
[   19.710247]   MEM window: d0400000-d05fffff
[   19.710249]   PREFETCH window: c0000000-c7ffffff
[   19.710252] PCI: Bridge: 0000:00:04.0
[   19.710254]   IO window: disabled.
[   19.710256]   MEM window: d0000000-d00fffff
[   19.710258]   PREFETCH window: disabled.
[   19.710261] PCI: Bridge: 0000:00:05.0
[   19.710263]   IO window: 2000-3fff
[   19.710265]   MEM window: cc000000-cfffffff
[   19.710267]   PREFETCH window: disabled.
[   19.710270] PCI: Bridge: 0000:00:06.0
[   19.710271]   IO window: disabled.
[   19.710274]   MEM window: c8000000-c80fffff
[   19.710276]   PREFETCH window: disabled.
[   19.710283] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   19.710285]   IO window: 00001000-000010ff
[   19.710293]   IO window: 00001400-000014ff
[   19.710298]   PREFETCH window: a8000000-abffffff
[   19.710303]   MEM window: ac000000-afffffff
[   19.710307] PCI: Bridge: 0000:00:14.4
[   19.710309]   IO window: disabled.
[   19.710314]   MEM window: d0100000-d03fffff
[   19.710317]   PREFETCH window: disabled.
[   19.710337] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   19.710344] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   19.710351] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   19.710824] ACPI: PCI Interrupt Link [C149] enabled at IRQ 11
[   19.710827] PCI: setting IRQ 11 as level-triggered
[   19.710834] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [C149] -> GSI 11 (level, low) -> IRQ 11
[   19.710901] NET: Registered protocol family 2
[   19.713681] Time: acpi_pm clocksource has been installed.
[   19.713707] Switched to high resolution mode on CPU 0
[   19.745766] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.747396] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   19.753929] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   19.754748] TCP: Hash tables configured (established 524288 bind 65536)
[   19.754752] TCP reno registered
[   19.765735] checking if image is initramfs... it is
[   20.508468] Freeing initrd memory: 7506k freed
[   20.515027] audit: initializing netlink socket (disabled)
[   20.515042] audit(1210582654.200:1): initialized
[   20.517427] VFS: Disk quotas dquot_6.5.1
[   20.517517] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   20.517662] io scheduler noop registered
[   20.517665] io scheduler anticipatory registered
[   20.517667] io scheduler deadline registered
[   20.517785] io scheduler cfq registered (default)
[   20.518830] Boot video device is 0000:01:05.0
[   20.519025] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   20.519046] assign_interrupt_mode Found MSI capability
[   20.519068] Allocate Port Service[0000:00:04.0:pcie00]
[   20.519141] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   20.519161] assign_interrupt_mode Found MSI capability
[   20.519181] Allocate Port Service[0000:00:05.0:pcie00]
[   20.519244] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   20.519264] assign_interrupt_mode Found MSI capability
[   20.519283] Allocate Port Service[0000:00:06.0:pcie00]
[   20.551978] Real Time Clock Driver v1.12ac
[   20.552098] Linux agpgart interface v0.102
[   20.552101] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.553602] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.553682] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.553790] PNP: PS/2 Controller [PNP0303:C24A,PNP0f13:C24B] at 0x60,0x64 irq 1,12
[   20.555707] i8042.c: Detected active multiplexing controller, rev 1.1.
[   20.556483] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.556488] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   20.556491] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   20.556493] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   20.556496] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   20.564900] mice: PS/2 mouse device common for all mice
[   20.564939] cpuidle: using governor ladder
[   20.564941] cpuidle: using governor menu
[   20.565098] NET: Registered protocol family 1
[   20.565122] IO APIC resources could be not be allocated.
[   20.565155] registered taskstats version 1
[   20.565303]   Magic number: 8:184:978
[   20.565318]   hash matches device ttyc5
[   20.565477] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   20.565481] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.565483] EDD information not available.
[   20.565492] Freeing unused kernel memory: 316k freed
[   20.596801] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   21.792006] fuse init (API version 7.9)
[   21.809034] ACPI: Transitioning device [C39B] to D3
[   21.809038] ACPI: Transitioning device [C39B] to D3
[   21.809043] ACPI: Fan [C39B] (off)
[   21.809270] ACPI: Transitioning device [C39C] to D3
[   21.809273] ACPI: Transitioning device [C39C] to D3
[   21.809276] ACPI: Fan [C39C] (off)
[   21.809499] ACPI: Transitioning device [C39D] to D3
[   21.809501] ACPI: Transitioning device [C39D] to D3
[   21.809505] ACPI: Fan [C39D] (off)
[   21.809728] ACPI: Transitioning device [C39E] to D3
[   21.809730] ACPI: Transitioning device [C39E] to D3
[   21.809734] ACPI: Fan [C39E] (off)
[   21.815516] ACPI: Processor [C000] (supports 8 throttling states)
[   21.815564] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.824985] ACPI: Thermal Zone [TZ1] (32 C)
[   22.640295] tg3.c:v3.86 (November 9, 2007)
[   22.640845] ACPI: PCI Interrupt Link [C145] enabled at IRQ 10
[   22.640848] PCI: setting IRQ 10 as level-triggered
[   22.640856] ACPI: PCI Interrupt 0000:10:00.0[A] -> Link [C145] -> GSI 10 (level, low) -> IRQ 10
[   22.640905] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   22.686961] SCSI subsystem initialized
[   22.757878] libata version 3.00 loaded.
[   22.774231] usbcore: registered new interface driver usbfs
[   22.774256] usbcore: registered new interface driver hub
[   22.788486] usbcore: registered new device driver usb
[   22.826641] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.466593] eth0: Tigon3 [partno(none) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:17:a4:e3:a7:93
[   23.466601] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   23.466604] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   23.466745] ahci 0000:00:12.0: version 3.0
[   23.466774] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [C145] -> GSI 10 (level, low) -> IRQ 10
[   23.466919] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   23.466926] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   23.466929] ahci 0000:00:12.0: nr_ports (4) and implemented port map (0x1) don't match, using nr_ports
[   23.466932] ahci 0000:00:12.0: forcing PORTS_IMPL to 0xf
[   24.468955] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   24.468961] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
[   24.470175] scsi0 : ahci
[   24.470532] scsi1 : ahci
[   24.470708] scsi2 : ahci
[   24.470891] scsi3 : ahci
[   24.470964] ata1: SATA max UDMA/133 abar m1024@0xd0609000 port 0xd0609100 irq 10
[   24.470968] ata2: SATA max UDMA/133 abar m1024@0xd0609000 port 0xd0609180 irq 10
[   24.470972] ata3: SATA max UDMA/133 abar m1024@0xd0609000 port 0xd0609200 irq 10
[   24.470976] ata4: SATA max UDMA/133 abar m1024@0xd0609000 port 0xd0609280 irq 10
[   24.944453] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.945240] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC7BP, max UDMA/100
[   24.945244] ata1.00: 312581808 sectors, multi 16: LBA48 
[   24.946206] ata1.00: configured for UDMA/100
[   25.256137] ata2: SATA link down (SStatus 0 SControl 0)
[   25.567818] ata3: SATA link down (SStatus 0 SControl 0)
[   25.879505] ata4: SATA link down (SStatus 0 SControl 0)
[   25.879632] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[   25.880791] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [C145] -> GSI 10 (level, low) -> IRQ 10
[   25.880845] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   25.883162] ACPI: PCI Interrupt Link [C14C] enabled at IRQ 11
[   25.883168] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [C14C] -> GSI 11 (level, low) -> IRQ 11
[   25.883258] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   25.883580] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   25.883607] ohci_hcd 0000:00:13.0: irq 11, io mem 0xd0601000
[   25.891952] Driver 'sd' needs updating - please use bus_type methods
[   25.895564] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   25.895579] sd 0:0:0:0: [sda] Write Protect is off
[   25.895582] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.895599] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.895654] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   25.895664] sd 0:0:0:0: [sda] Write Protect is off
[   25.895666] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.895682] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.895686]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
[   25.943618] hub 1-0:1.0: USB hub found
[   25.943630] hub 1-0:1.0: 2 ports detected
[   26.047909] ACPI: PCI Interrupt Link [C146] enabled at IRQ 10
[   26.047914] ACPI: PCI Interrupt 0000:00:13.1[B] -> Link [C146] -> GSI 10 (level, low) -> IRQ 10
[   26.048034] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   26.048107] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   26.048130] ohci_hcd 0000:00:13.1: irq 10, io mem 0xd0602000
[   26.107420] usb usb2: configuration #1 chosen from 1 choice
[   26.107447] hub 2-0:1.0: USB hub found
[   26.107461] hub 2-0:1.0: 2 ports detected
[   26.211283] ACPI: PCI Interrupt 0000:00:13.2[C] -> Link [C146] -> GSI 10 (level, low) -> IRQ 10
[   26.211421] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   26.211487] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   26.211511] ohci_hcd 0000:00:13.2: irq 10, io mem 0xd0603000
[   26.271248] usb usb3: configuration #1 chosen from 1 choice
[   26.271273] hub 3-0:1.0: USB hub found
[   26.271287] hub 3-0:1.0: 2 ports detected
[   26.313241]  sda1 sda2 sda3 sda4
[   26.337976] sd 0:0:0:0: [sda] Attached SCSI disk
[   26.344287] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.375115] ACPI: PCI Interrupt 0000:00:13.3[B] -> Link [C146] -> GSI 10 (level, low) -> IRQ 10
[   26.375230] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   26.375297] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   26.375321] ohci_hcd 0000:00:13.3: irq 10, io mem 0xd0604000
[   26.435085] usb usb4: configuration #1 chosen from 1 choice
[   26.435116] hub 4-0:1.0: USB hub found
[   26.435128] hub 4-0:1.0: 2 ports detected
[   26.526865] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   26.538992] ACPI: PCI Interrupt 0000:00:13.4[C] -> Link [C146] -> GSI 10 (level, low) -> IRQ 10
[   26.539149] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   26.539216] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   26.539237] ohci_hcd 0000:00:13.4: irq 10, io mem 0xd0605000
[   26.598919] usb usb5: configuration #1 chosen from 1 choice
[   26.598946] hub 5-0:1.0: USB hub found
[   26.598959] hub 5-0:1.0: 2 ports detected
[   26.703222] ACPI: PCI Interrupt 0000:00:13.5[D] -> Link [C14C] -> GSI 11 (level, low) -> IRQ 11
[   26.703339] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   26.703415] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   26.703462] ehci_hcd 0000:00:13.5: debug port 1
[   26.703474] ehci_hcd 0000:00:13.5: irq 11, io mem 0xd0606000
[   26.726681] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.726870] usb usb6: configuration #1 chosen from 1 choice
[   26.726898] hub 6-0:1.0: USB hub found
[   26.726905] hub 6-0:1.0: 10 ports detected
[   26.810366] Attempting manual resume
[   26.810370] swsusp: Resume From Partition 8:3
[   26.810372] PM: Checking swsusp image.
[   26.810593] PM: Resume from disk failed.
[   26.819180] ReiserFS: sda4: found reiserfs format "3.6" with standard journal
[   26.819196] ReiserFS: sda4: using ordered data mode
[   26.831248] ACPI: PCI Interrupt Link [C14A] enabled at IRQ 9
[   26.831253] PCI: setting IRQ 9 as level-triggered
[   26.831260] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [C14A] -> GSI 9 (level, low) -> IRQ 9
[   26.883556] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[d0101000-d01017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   26.889058] ReiserFS: sda4: journal params: device sda4, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   26.890616] ReiserFS: sda4: checking transaction log (sda4)
[   26.909468] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [C145] -> GSI 10 (level, low) -> IRQ 10
[   26.910684] scsi4 : pata_atiixp
[   26.911185] scsi5 : pata_atiixp
[   26.911721] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x5040 irq 14
[   26.911725] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x5048 irq 15
[   26.946109] ReiserFS: sda4: Using r5 hash to sort names
[   27.122253] usb 2-1: device not accepting address 2, error -62
[   27.230603] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PC05, max MWDMA2
[   27.402409] ata5.00: configured for MWDMA2
[   27.561728] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PC05 PQ: 0 ANSI: 5
[   27.561826] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   27.945442] usb 2-1: new low speed USB device using ohci_hcd and address 4
[   28.174471] usb 2-1: configuration #1 chosen from 1 choice
[   28.177293] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f992965240e]
[   37.659794] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.691829] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.963874] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   38.023373] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   38.023381] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   38.418234] input: Power Button (FF) as /devices/virtual/input/input2
[   38.429766] ACPI: Power Button (FF) [PWRF]
[   38.429929] input: Sleep Button (CM) as /devices/virtual/input/input3
[   38.442937] ACPI: Sleep Button (CM) [C28D]
[   38.443070] input: Lid Switch as /devices/virtual/input/input4
[   38.443201] ACPI: Lid Switch [C1F0]
[   38.843146] ACPI: AC Adapter [C1EB] (off-line)
[   38.925391] ACPI: Battery Slot [C1ED] (battery present)
[   38.925680] ACPI: Battery Slot [C1EC] (battery absent)
[   38.970538] ACPI: WMI-Acer: Mapper loaded
[   39.312890] Yenta: CardBus bridge found at 0000:02:04.0 [103c:30c2]
[   39.322223] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   39.438543] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   39.438548] Socket status: 30000006
[   39.438551] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   39.438558] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd03fffff
[   39.649753] [fglrx] Maximum main memory to use for locked dma buffers: 2258 MBytes.
[   39.649790] [fglrx] ASYNCIO init succeed!
[   39.649919] [fglrx] PAT is enabled successfully!
[   39.655164] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   39.863447] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   40.702718] ACPI: PCI Interrupt 0000:00:14.2[A] -> Link [C145] -> GSI 10 (level, low) -> IRQ 10
[   40.810812] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6
[   40.816576] ACPI: Video Device [C08D] (multi-head: yes  rom: no  post: no)
[   41.202728] Driver 'sr' needs updating - please use bus_type methods
[   41.222283] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   41.222290] Uniform CD-ROM driver Revision: 3.20
[   41.222388] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   41.815655] usbcore: registered new interface driver hiddev
[   41.829917] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A as /devices/pci0000:00/0000:00:13.1/usb2/2-1/2-1:1.0/input/input7
[   41.843649] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A] on usb-0000:00:13.1-1
[   41.843671] usbcore: registered new interface driver usbhid
[   41.843675] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.877327] spurious 8259A interrupt: IRQ7.
[   42.487060] tpm_inf_pnp 00:03: Found C232 with ID IFX0102
[   42.487112] tpm_inf_pnp 00:03: TPM found: config base 0x520, data base 0x530, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   42.507286] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
[   42.507294] serio: Synaptics pass-through port at isa0060/serio4/input0
[   42.547327] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   42.576687] parport_pc 00:02: activated
[   42.576692] parport_pc 00:02: reported by Plug and Play ACPI
[   42.577862] parport_pc 00:02: disabled
[   45.484003] lp: driver loaded but no devices found
[   45.619459] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   45.684677] usbcore: registered new interface driver ndiswrapper
[   45.733152] Adding 1052248k swap on /dev/sda3.  Priority:-1 extents:1 across:1052248k
[   46.495587] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.078735] No dock devices found.
[   47.402444] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-52 processors (1 cpu cores) (version 2.20.00)
[   47.402481] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
[   47.402484] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[   47.402525] powernow-k8: ph2 null fid transition 0x8
[   48.600672] ppdev: user-space parallel port driver
[   48.721650] audit(1210557483.360:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5067 profile="/usr/sbin/cupsd" namespace="default"
[   50.295454] Bluetooth: Core ver 2.11
[   50.296350] NET: Registered protocol family 31
[   50.296355] Bluetooth: HCI device and connection manager initialized
[   50.296359] Bluetooth: HCI socket layer initialized
[   50.331083] Bluetooth: L2CAP ver 2.9
[   50.331088] Bluetooth: L2CAP socket layer initialized
[   50.402916] Bluetooth: RFCOMM socket layer initialized
[   50.403498] Bluetooth: RFCOMM TTY layer initialized
[   50.403502] Bluetooth: RFCOMM ver 1.8
[   51.760949] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   51.760955] tg3: eth0: Flow control is off for TX and off for RX.
[   52.775247] ACPI: PCI Interrupt Link [C148] enabled at IRQ 11
[   52.775256] ACPI: PCI Interrupt 0000:01:05.0[B] -> Link [C148] -> GSI 11 (level, low) -> IRQ 11
[   52.882593] usbcore: deregistering interface driver ndiswrapper
[   52.906744] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   52.916465] Clocksource tsc unstable (delta = -250016915 ns)
[   52.934530] usbcore: registered new interface driver ndiswrapper
[   53.618362] NET: Registered protocol family 17
[   54.832028] [fglrx] GART Table is not in FRAME_BUFFER range 
[   54.832040] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[   54.832043] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   57.264051] NET: Registered protocol family 10
[   57.264798] lo: Disabled Privacy Extensions
[   62.640146] eth0: no IPv6 routers present
[   65.639573] hda-intel: Invalid position buffer, using LPIB read method instead.
[   79.133212] CPU0 attaching NULL sched-domain.
[   79.138462] CPU0 attaching sched-domain:
[   79.138470]  domain 0: span 01
[   79.138472]   groups: 01
[   96.435588] ISO 9660 Extensions: Microsoft Joliet Level 3
[   96.497167] ISOFS: changing to secondary root
[ 1361.363780] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1361.394614] ISOFS: changing to secondary root
[ 2531.744055] CPU0 attaching NULL sched-domain.
[ 2531.748837] CPU0 attaching sched-domain:
[ 2531.748844]  domain 0: span 01
[ 2531.748847]   groups: 01

```

Please let me know if you need more.
Thanks a lot.

---

### Post by mplexus on 2008-05-14
I'm using Hardy as well (64bit) on "acer aspire 1524 wlmi", and ndiswrapper + neti2220x64 for my INPROCOMM card. I also have to boot with the wireless card switched on in order for wireless networking to work, otherwise the wireless button does not activate the wireless card.

It is not an issue of ndiswrapper which is loaded and uses the correct driver, it is just that I am unable to activate the wireless card if I don't activate it at the beginning of the boot. Once I activate the card at the beginning of the boot then wireless networking works fine, yet again, I cannot disable the wireless card unless I reboot.

It is like the wireless button stops responding after the kernel is loaded, cause the functionality of the wireless button stops seconds after selecting ubuntu from grub.

This did not occur in former ubuntu versions.

------Last Edit
I found the solution: i blacklisted module acer-acpi. now the wireless button works fine. I do have to enable it first (now it lights up as expected) and then modprobe ndiswrapper to get wi-fi, and this is the functionality i want, not having the wireless card "on" all the time.

---

### Post by Suky on 2008-05-20
Hi mplexus,

Could you explain more how to blacklist module "acer-acpi"? And, I'm using HP notebook not Acer.

my blacklist 
```
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

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

#blacklist bcm43xx
blacklist bcm43xx

```Thanks,

---

### Post by mplexus on 2008-05-22
Unfortunately I don't know if blacklisting the acer-acpi module applies to other than acer laptops..

In my case,in the end of the file you posted I added the line
blacklist acer-acpi

I just aimed to give a hint: maybe some module takes control of the wireless button but may be not giving the right functionality. That was my case anyway (I think!).

---

### Post by Suky on 2008-05-22
Thanks mplexus, I understand your point.

---

