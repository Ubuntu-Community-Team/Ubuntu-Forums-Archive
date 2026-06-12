---
title: "driver for mecury TV BOX"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by akg_nitt on 2010-06-27
purchased merucury USB TV Box..not able to find a suitable driver for it in ubuntu..it comes up with drivers for windows XP/VISTA with trident analog video driver.is this the driver needed for ubuntu too.system is not recognising the hardware too.somebody please throw some light on it.quite strucked after purchasing it...missing World Cup....

---

### Post by akg_nitt on 2010-06-27
it doesnt seem my OS is recognising d card..here is my dmesg output
13 (0x1000-0x107f), disabling
[    0.329526] pnp 00:0a: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.329530] pnp 00:0a: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.329534] pnp 00:0a: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.329538] pnp 00:0a: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.353783] pnp: PnP ACPI: found 12 devices
[    0.353786] ACPI: ACPI bus type pnp unregistered
[    0.353791] PnPBIOS: Disabled by ACPI PNP
[    0.353805] system 00:05: ioport range 0xc80-0xcff could not be reserved
[    0.353814] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.353822] system 00:09: ioport range 0x900-0x97f has been reserved
[    0.353826] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.353833] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[    0.353837] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[    0.353841] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[    0.353844] system 00:0a: ioport range 0x809-0x809 has been reserved
[    0.353852] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[    0.353856] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[    0.353860] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.353864] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.353868] system 00:0b: iomem range 0x100000-0x3fe923ff could not be reserved
[    0.353871] system 00:0b: iomem range 0x3fe92400-0x3fefffff has been reserved
[    0.353875] system 00:0b: iomem range 0x3ff00000-0x3fffffff has been reserved
[    0.353879] system 00:0b: iomem range 0x3ff00000-0x406fffff could not be reserved
[    0.353883] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    0.353887] system 00:0b: iomem range 0xffa00000-0xffafffff has been reserved
[    0.353891] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.353895] system 00:0b: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.353898] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.353902] system 00:0b: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.353906] system 00:0b: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.353910] system 00:0b: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.353914] system 00:0b: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.353917] system 00:0b: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.353921] system 00:0b: iomem range 0xf4000000-0xf7ffffff has been reserved
[    0.388632] AppArmor: AppArmor Filesystem Enabled
[    0.388710] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.388715] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.388720] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfeafffff
[    0.388725] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.388731] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.388734] pci 0000:00:1c.0:   IO window: disabled
[    0.388741] pci 0000:00:1c.0:   MEM window: disabled
[    0.388746] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.388752] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:0c
[    0.388755] pci 0000:00:1c.2:   IO window: disabled
[    0.388762] pci 0000:00:1c.2:   MEM window: 0xf9f00000-0xf9ffffff
[    0.388768] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.388774] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.388779] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff
[    0.388786] pci 0000:00:1c.3:   MEM window: 0xf9c00000-0xf9efffff
[    0.388793] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.388803] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.388805] pci 0000:00:1e.0:   IO window: disabled
[    0.388813] pci 0000:00:1e.0:   MEM window: 0xf9b00000-0xf9bfffff
[    0.388818] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.388831]   alloc irq_desc for 16 on node -1
[    0.388834]   alloc kstat_irqs on node -1
[    0.388840] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.388845] pci 0000:00:01.0: setting latency timer to 64
[    0.388856] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.388862] pci 0000:00:1c.0: setting latency timer to 64
[    0.388872]   alloc irq_desc for 18 on node -1
[    0.388874]   alloc kstat_irqs on node -1
[    0.388878] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.388884] pci 0000:00:1c.2: setting latency timer to 64
[    0.388894]   alloc irq_desc for 19 on node -1
[    0.388897]   alloc kstat_irqs on node -1
[    0.388901] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.388907] pci 0000:00:1c.3: setting latency timer to 64
[    0.388917] pci 0000:00:1e.0: setting latency timer to 64
[    0.388923] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.388926] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.388929] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.388932] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfeafffff]
[    0.388936] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.388939] pci_bus 0000:0c: resource 1 mem: [0xf9f00000-0xf9ffffff]
[    0.388942] pci_bus 0000:0d: resource 0 io:  [0xc000-0xcfff]
[    0.388946] pci_bus 0000:0d: resource 1 mem: [0xf9c00000-0xf9efffff]
[    0.388949] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.388952] pci_bus 0000:03: resource 1 mem: [0xf9b00000-0xf9bfffff]
[    0.388955] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.388959] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.388998] NET: Registered protocol family 2
[    0.389112] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.389493] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.390019] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.390286] TCP: Hash tables configured (established 131072 bind 65536)
[    0.390289] TCP reno registered
[    0.390372] NET: Registered protocol family 1
[    0.390440] Trying to unpack rootfs image as initramfs...
[    0.501619] Switched to high resolution mode on CPU 1
[    0.503996] Switched to high resolution mode on CPU 0
[    0.623008] Freeing initrd memory: 7472k freed
[    0.626954] Simple Boot Flag at 0x79 set to 0x1
[    0.627178] cpufreq-nforce2: No nForce2 chipset.
[    0.627212] Scanning for low memory corruption every 60 seconds
[    0.627337] audit: initializing netlink socket (disabled)
[    0.627359] type=2000 audit(1277647744.624:1): initialized
[    0.637999] highmem bounce pool size: 64 pages
[    0.638005] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.639875] VFS: Disk quotas dquot_6.5.2
[    0.639954] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.640629] fuse init (API version 7.12)
[    0.640737] msgmni has been set to 1731
[    0.640993] alg: No test for stdrng (krng)
[    0.641010] io scheduler noop registered
[    0.641013] io scheduler anticipatory registered
[    0.641015] io scheduler deadline registered
[    0.641068] io scheduler cfq registered (default)
[    0.641249] pci 0000:01:00.0: Boot video device
[    0.641415]   alloc irq_desc for 24 on node -1
[    0.641418]   alloc kstat_irqs on node -1
[    0.641428] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.641436] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.641596]   alloc irq_desc for 25 on node -1
[    0.641599]   alloc kstat_irqs on node -1
[    0.641610] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.641623] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.641804]   alloc irq_desc for 26 on node -1
[    0.641806]   alloc kstat_irqs on node -1
[    0.641817] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.641829] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.642009]   alloc irq_desc for 27 on node -1
[    0.642011]   alloc kstat_irqs on node -1
[    0.642021] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.642034] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.642165] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.642316] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.642501] ACPI: AC Adapter [AC] (on-line)
[    0.642591] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.643073] ACPI: Lid Switch [LID]
[    0.643133] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.643141] ACPI: Power Button [PBTN]
[    0.643193] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.643196] ACPI: Sleep Button [SBTN]
[    0.643964] ACPI: SSDT 3fe93134 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.644536] ACPI: SSDT 3fe92bf9 004B6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.644982] Monitor-Mwait will be used to enter C-1 state
[    0.645012] Monitor-Mwait will be used to enter C-2 state
[    0.645039] Monitor-Mwait will be used to enter C-3 state
[    0.645049] Marking TSC unstable due to TSC halts in idle
[    0.645070] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.645103] processor LNXCPU:00: registered as cooling_device0
[    0.645107] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.645500] ACPI: SSDT 3fe93378 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.645893] ACPI: SSDT 3fe930af 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.646471] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.646505] processor LNXCPU:01: registered as cooling_device1
[    0.646510] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.654405] thermal LNXTHERM:01: registered as thermal_zone0
[    0.654416] ACPI: Thermal Zone [THM] (40 C)
[    0.654497] isapnp: Scanning for PnP cards...
[    0.733661] ACPI: Battery Slot [BAT0] (battery present)
[    1.011225] isapnp: No Plug & Play device found
[    1.012603] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.014257] brd: module loaded
[    1.014817] loop: module loaded
[    1.014900] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.015031] ata_piix 0000:00:1f.1: version 2.13
[    1.015044] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.015088] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.015180] scsi0 : ata_piix
[    1.015274] scsi1 : ata_piix
[    1.015986] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    1.015990] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    1.016015]   alloc irq_desc for 17 on node -1
[    1.016017]   alloc kstat_irqs on node -1
[    1.016023] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.016030] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.016212] ata2: port disabled. ignoring.
[    1.172058] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.172265] scsi2 : ata_piix
[    1.172338] scsi3 : ata_piix
[    1.172775] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    1.172783] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    1.173938] Fixed MDIO Bus: probed
[    1.173986] PPP generic driver version 2.4.2
[    1.174086] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.174106]   alloc irq_desc for 22 on node -1
[    1.174109]   alloc kstat_irqs on node -1
[    1.174114] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.174127] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.174131] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.174184] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.178098] ehci_hcd 0000:00:1a.7: debug port 1
[    1.178106] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.178122] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    1.193015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.193096] usb usb1: configuration #1 chosen from 1 choice
[    1.193132] hub 1-0:1.0: USB hub found
[    1.193140] hub 1-0:1.0: 4 ports detected
[    1.193210]   alloc irq_desc for 20 on node -1
[    1.193213]   alloc kstat_irqs on node -1
[    1.193218] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.193230] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.193234] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.193270] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.196548] ata1.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE04, max UDMA/33
[    1.197173] ehci_hcd 0000:00:1d.7: debug port 1
[    1.197181] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.197197] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    1.212025] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.212097] usb usb2: configuration #1 chosen from 1 choice
[    1.212132] hub 2-0:1.0: USB hub found
[    1.212140] hub 2-0:1.0: 6 ports detected
[    1.212216] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.212237] uhci_hcd: USB Universal Host Controller Interface driver
[    1.212263] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.212271] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.212275] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.212320] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.212350] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    1.212444] usb usb3: configuration #1 chosen from 1 choice
[    1.212476] hub 3-0:1.0: USB hub found
[    1.212484] hub 3-0:1.0: 2 ports detected
[    1.212541]   alloc irq_desc for 21 on node -1
[    1.212544]   alloc kstat_irqs on node -1
[    1.212549] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.212557] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.212561] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.212597] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.212635] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    1.212730] usb usb4: configuration #1 chosen from 1 choice
[    1.212762] hub 4-0:1.0: USB hub found
[    1.212770] hub 4-0:1.0: 2 ports detected
[    1.212828] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.212836] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.212840] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.212876] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.212905] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    1.213011] usb usb5: configuration #1 chosen from 1 choice
[    1.213044] hub 5-0:1.0: USB hub found
[    1.213051] hub 5-0:1.0: 2 ports detected
[    1.213109] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.213117] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.213121] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.213158] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.213189] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    1.213286] usb usb6: configuration #1 chosen from 1 choice
[    1.213318] hub 6-0:1.0: USB hub found
[    1.213325] hub 6-0:1.0: 2 ports detected
[    1.213385] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.213393] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.213397] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.213443] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.213472] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.213565] usb usb7: configuration #1 chosen from 1 choice
[    1.213597] hub 7-0:1.0: USB hub found
[    1.213604] hub 7-0:1.0: 2 ports detected
[    1.213732] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.231936] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.231943] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.232030] mice: PS/2 mouse device common for all mice
[    1.232166] rtc_cmos 00:03: RTC can wake from S4
[    1.232202] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.232236] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.232356] device-mapper: uevent: version 1.0.3
[    1.232669] ata1.00: configured for UDMA/33
[    1.232854] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.232929] device-mapper: multipath: version 1.1.0 loaded
[    1.232932] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.233184] EISA: Probing bus 0 at eisa.0
[    1.233265] EISA: Mainboard @G_FFFF detected.
[    1.233283] Cannot allocate resource for EISA slot 1
[    1.233322] EISA: Detected 0 cards.
[    1.233502] cpuidle: using governor ladder
[    1.233675] cpuidle: using governor menu
[    1.234288] TCP cubic registered
[    1.234477] NET: Registered protocol family 10
[    1.235044] lo: Disabled Privacy Extensions
[    1.235219] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.235473] NET: Registered protocol family 17
[    1.235493] Bluetooth: L2CAP ver 2.13
[    1.235495] Bluetooth: L2CAP socket layer initialized
[    1.235499] Bluetooth: SCO (Voice Link) ver 0.6
[    1.235501] Bluetooth: SCO socket layer initialized
[    1.235676] Bluetooth: RFCOMM TTY layer initialized
[    1.235680] Bluetooth: RFCOMM socket layer initialized
[    1.235682] Bluetooth: RFCOMM ver 1.11
[    1.236316] Using IPI No-Shortcut mode
[    1.236361] scsi 0:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE04 PQ: 0 ANSI: 5
[    1.236389] PM: Resume from disk failed.
[    1.236403] registered taskstats version 1
[    1.236559]   Magic number: 14:130:183
[    1.236596] acpi device:42: hash matches
[    1.236654] rtc_cmos 00:03: setting system clock to 2010-06-27 14:09:05 UTC (1277647745)
[    1.236657] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.236660] EDD information not available.
[    1.241233] sr0: scsi3-mmc drive: 16x/16x writer cd/rw xa/form2 cdda tray
[    1.241238] Uniform CD-ROM driver Revision: 3.20
[    1.241332] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.241386] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.500230] Clocksource tsc unstable (delta = -250779698 ns)
[    1.524228] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.665613] usb 2-1: configuration #1 chosen from 1 choice
[    1.820292] ata4.00: SATA link down (SStatus 0 SControl 300)
[    1.820318] ata4.01: SATA link down (SStatus 0 SControl 0)
[    1.820425] ata3.00: SATA link down (SStatus 0 SControl 300)
[    1.820448] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.820543] Freeing unused kernel memory: 540k freed
[    1.820921] Write protecting the kernel text: 4568k
[    1.820994] Write protecting the kernel read-only data: 1836k
[    1.833076] usb 2-4: new high speed USB device using ehci_hcd and address 4
[    1.954424] Linux agpgart interface v0.103
[    1.972063] usb 2-4: configuration #1 chosen from 1 choice
[    2.052086] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.078919] acpi device:32: registered as cooling_device2
[    2.080088] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/input/input5
[    2.080129] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    2.093006] Initializing USB Mass Storage driver...
[    2.093497] scsi4 : SCSI emulation for USB Mass Storage devices
[    2.093641] usbcore: registered new interface driver usb-storage
[    2.093645] usb-storage: device found at 4
[    2.093647] usb-storage: waiting for device to settle before scanning
[    2.093652] USB Mass Storage support registered.
[    2.120141] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.120179] b44.c:v2.0
[    2.120224] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.140934] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:82:e9:9b
[    2.178124] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f9bfd800-f9bfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.216066] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    2.398086] usb 5-2: configuration #1 chosen from 1 choice
[    2.409105] usbcore: registered new interface driver hiddev
[    2.422256] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input6
[    2.422349] generic-usb 0003:1C4F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1d.0-2/input0
[    2.422365] usbcore: registered new interface driver usbhid
[    2.422369] usbhid: v2.6:USB HID core driver
[    3.456583] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[444fc0002e9e5838]
[    7.092409] usb-storage: device scan complete
[    7.093025] scsi 4:0:0:0: Direct-Access     Seagate  FreeAgent Go     0148 PQ: 0 ANSI: 4
[    7.093777] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    7.095077] sd 4:0:0:0: [sda] 976773167 512-byte logical blocks: (500 GB/465 GiB)
[    7.095601] sd 4:0:0:0: [sda] Write Protect is off
[    7.095606] sd 4:0:0:0: [sda] Mode Sense: 1c 00 00 00
[    7.095610] sd 4:0:0:0: [sda] Assuming drive cache: write through
[    7.096833] sd 4:0:0:0: [sda] Assuming drive cache: write through
[    7.096838]  sda: sda1 sda2 sda3
[    7.164763] sd 4:0:0:0: [sda] Assuming drive cache: write through
[    7.164767] sd 4:0:0:0: [sda] Attached SCSI disk
[    7.567021] PM: Starting manual resume from disk
[    7.567025] PM: Resume from partition 8:1
[    7.567028] PM: Checking hibernation image.
[    7.567598] PM: Resume from disk failed.
[    7.611049] kjournald starting.  Commit interval 5 seconds
[    7.611060] EXT3-fs: mounted filesystem with writeback data mode.
[    8.371857] type=1505 audit(1277647752.632:2): operation="profile_load" pid=505 name=/usr/share/gdm/guest-session/Xsession
[    8.384337] type=1505 audit(1277647752.647:3): operation="profile_load" pid=506 name=/sbin/dhclient3
[    8.385191] type=1505 audit(1277647752.647:4): operation="profile_load" pid=506 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.385641] type=1505 audit(1277647752.647:5): operation="profile_load" pid=506 name=/usr/lib/connman/scripts/dhclient-script
[    8.419758] type=1505 audit(1277647752.679:6): operation="profile_load" pid=507 name=/usr/bin/evince
[    8.432708] type=1505 audit(1277647752.692:7): operation="profile_load" pid=507 name=/usr/bin/evince-previewer
[    8.440250] type=1505 audit(1277647752.703:8): operation="profile_load" pid=507 name=/usr/bin/evince-thumbnailer
[    8.455267] type=1505 audit(1277647752.715:9): operation="profile_load" pid=509 name=/usr/lib/cups/backend/cups-pdf
[    8.456238] type=1505 audit(1277647752.719:10): operation="profile_load" pid=509 name=/usr/sbin/cupsd
[    8.472759] type=1505 audit(1277647752.735:11): operation="profile_load" pid=510 name=/usr/sbin/tcpdump
[    9.663900] Adding 497972k swap on /dev/sda1.  Priority:-1 extents:1 across:497972k 
[   10.028578] EXT3 FS on sda2, internal journal
[   10.433025] udev: starting version 147
[   11.761234] lp: driver loaded but no devices found
[   12.124050] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.874112] nvidia: module license 'NVIDIA' taints kernel.
[   13.874117] Disabling lock debugging due to kernel taint
[   13.879891] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   14.128032] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.128045] nvidia 0000:01:00.0: setting latency timer to 64
[   14.128192] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009
[   14.418982] ricoh-mmc: Ricoh MMC Controller disabling driver
[   14.418986] ricoh-mmc: Copyright(c) Philip Langdale
[   14.419023] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   14.419045] ricoh-mmc: Controller is now disabled.
[   14.476115] cfg80211: Calling CRDA to update world regulatory domain
[   14.820696] sdhci: Secure Digital Host Controller Interface driver
[   14.820700] sdhci: Copyright(c) Pierre Ossman
[   15.264768] cfg80211: World regulatory domain updated:
[   15.264772]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.264776]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.264779]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.264782]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.264785]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.264787]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.293521] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.294999] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   15.295020] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   15.297099] Registered led device: mmc0::
[   15.298132] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   15.543357] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   15.543362] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   15.543453] iwl3945 0000:0c:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.543468] iwl3945 0000:0c:00.0: setting latency timer to 64
[   15.616406] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.616411] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   15.616529]   alloc irq_desc for 28 on node -1
[   15.616532]   alloc kstat_irqs on node -1
[   15.616571] iwl3945 0000:0c:00.0: irq 28 for MSI/MSI-X
[   18.075796] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.621555] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   19.694364] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   19.756642] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   19.756795] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
[   19.816294] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
[   20.168955] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.168981] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.279422] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   20.333390] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.333481] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   21.454558] type=1505 audit(1277647765.716:12): operation="profile_replace" pid=1125 name=/usr/share/gdm/guest-session/Xsession
[   21.456636] type=1505 audit(1277647765.716:13): operation="profile_replace" pid=1126 name=/sbin/dhclient3
[   21.457551] type=1505 audit(1277647765.720:14): operation="profile_replace" pid=1126 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   21.457999] type=1505 audit(1277647765.720:15): operation="profile_replace" pid=1126 name=/usr/lib/connman/scripts/dhclient-script
[   21.462312] type=1505 audit(1277647765.724:16): operation="profile_replace" pid=1127 name=/usr/bin/evince
[   21.475270] type=1505 audit(1277647765.736:17): operation="profile_replace" pid=1127 name=/usr/bin/evince-previewer
[   21.482961] type=1505 audit(1277647765.744:18): operation="profile_replace" pid=1127 name=/usr/bin/evince-thumbnailer
[   21.493543] type=1505 audit(1277647765.756:19): operation="profile_replace" pid=1129 name=/usr/lib/cups/backend/cups-pdf
[   21.494497] type=1505 audit(1277647765.756:20): operation="profile_replace" pid=1129 name=/usr/sbin/cupsd
[   21.497291] type=1505 audit(1277647765.760:21): operation="profile_replace" pid=1130 name=/usr/sbin/tcpdump
[   21.820219] b44: eth0: Link is up at 100 Mbps, full duplex.
[   21.820223] b44: eth0: Flow control is off for TX and off for RX.
[   21.820752] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.169152] usb 5-2: USB disconnect, address 2
[   30.229054] usb 5-2: new low speed USB device using uhci_hcd and address 3
[   30.403051] usb 5-2: configuration #1 chosen from 1 choice
[   30.421235] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input11
[   30.421330] generic-usb 0003:1C4F:0003.0002: input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1d.0-2/input0
[   30.660216] usb 5-2: USB disconnect, address 3
[   31.641055] usb 5-2: new low speed USB device using uhci_hcd and address 4
[   31.828522] usb 5-2: configuration #1 chosen from 1 choice
[   31.844693] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input12
[   31.844817] generic-usb 0003:1C4F:0003.0003: input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1d.0-2/input0
[   32.652058] eth0: no IPv6 routers present
[   32.995825] ppdev: user-space parallel port driver
[   82.816714] UDF-fs: No VRS found
[   82.816720] UDF-fs: No partition found (1)
[   82.889060] ISO 9660 Extensions: Microsoft Joliet Level 3
[   82.924041] ISOFS: changing to secondary root
[  893.815245] CE: hpet increasing min_delta_ns to 15000 nsec
[  947.836338] CE: hpet increasing min_delta_ns to 22500 nsec
[ 1006.823012] CE: hpet increasing min_delta_ns to 33750 nsec

no idea whats going on..somebody please show ur face....

---

