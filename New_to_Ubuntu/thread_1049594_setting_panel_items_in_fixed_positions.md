---
title: "setting panel items in fixed positions"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by manuleka on 2009-01-24
sometimes my top and bottom panels on ubuntu (gnome) loads up on different positions... for example i usaully get this

[http://www.manuleka.com/imgs/screenshot1.jpg](http://www.manuleka.com/imgs/screenshot1.jpg)

but sometime when i boot up Ubuntu it loads up on  different positions like this

[http://www.manuleka.com/imgs/screenshot2.jpg](http://www.manuleka.com/imgs/screenshot2.jpg)

my question is: how can i set it so each panel module or item gets a set position... like the shut down options should always stay on the right end of the top panel and the rubbish bin should always stay right of the desktop items

---

### Post by RichardLinx on 2009-01-24
Right click on the icon>lock to panel.

---

### Post by manuleka on 2009-01-24
all modules/items locked... i think it's more todo with the loading of eachh modules... some expert on this might know how to set them so each loads up into their fixed positions

i expected them to load to their fixed position since they are all locked.... but unfortunately for some reason they don't :(

---

### Post by theinnercityhippy on 2009-01-24
> **manuleka said:**
> all modules/items locked... i think it's more todo with the loading of eachh modules... some expert on this might know how to set them so each loads up into their fixed positions

i expected them to load to their fixed position since they are all locked.... but unfortunately for some reason they don't :(

In short, they should do. can you post the output of

```
dmesg
```

shortly after rebooting

-JimDog-

---

### Post by manuleka on 2009-01-24
you mean dmesg after a reboot with icons/modules on wrong positions? this doesn't happen alot when rebooting but i've recognized it happening aa few times... maybe 1 in every 6 reboots or so...

---

### Post by manuleka on 2009-01-26
here's dmesg straight after i logged on where the menus/icons on panels sit on different locations than normal

```

[    0.837588] PCI: bridge 0000:00:1c.1 32bit mmio: [dfc00000, dfcfffff]
[    0.837653] pci 0000:00:1e.0: transparent bridge
[    0.837684] bus 00 -> node 0
[    0.837699] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.838276] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.838550] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.865770] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.865770] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.865770] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.865770] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.868180] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.868515] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.868849] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.869178] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.869331] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.869331] pnp: PnP ACPI init
[    0.869331] ACPI: bus type pnp registered
[    0.929070] pnp: PnP ACPI: found 11 devices
[    0.929077] ACPI: ACPI bus type pnp unregistered
[    0.929086] PnPBIOS: Disabled by ACPI PNP
[    0.929129] PCI: Using ACPI for IRQ routing
[    0.936056] NET: Registered protocol family 8
[    0.936062] NET: Registered protocol family 20
[    0.936101] NetLabel: Initializing
[    0.936101] NetLabel:  domain hash size = 128
[    0.936101] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.936107] NetLabel:  unlabeled traffic allowed by default
[    0.936262] hpet clockevent registered
[    0.936270] hpet0: at MMIO 0xfed03000, IRQs 2, 8, 0
[    0.936281] hpet0: 3 64-bit timers, 14318180 Hz
[    0.938491] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.938496]    actual entries 65620
[    0.938665] AppArmor: AppArmor Filesystem Enabled
[    0.938701] ACPI: RTC can wake from S4
[    0.944092] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.944100] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.944108] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.944115] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.944136] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.944154] system 00:09: ioport range 0x400-0x47f has been reserved
[    0.944161] system 00:09: ioport range 0x1180-0x119f has been reserved
[    0.944168] system 00:09: ioport range 0x500-0x53f has been reserved
[    0.944175] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.944182] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.944190] system 00:09: iomem range 0xfed20000-0xfed23fff has been reserved
[    0.944197] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.944204] system 00:09: iomem range 0xfc800400-0xfc800fff has been reserved
[    0.980328] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.980337] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.980348] pci 0000:00:1c.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.980356] pci 0000:00:1c.0:   PREFETCH window: 0x000000ffd00000-0x000000ffdfffff
[    0.980369] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.980374] pci 0000:00:1c.1:   IO window: disabled
[    0.980384] pci 0000:00:1c.1:   MEM window: 0xdfc00000-0xdfcfffff
[    0.980393] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.980403] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.980408] pci 0000:00:1e.0:   IO window: disabled
[    0.980416] pci 0000:00:1e.0:   MEM window: disabled
[    0.980423] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.980454] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.980463] pci 0000:00:1c.0: setting latency timer to 64
[    0.980478] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.980486] pci 0000:00:1c.1: setting latency timer to 64
[    0.980497] pci 0000:00:1e.0: setting latency timer to 64
[    0.980505] bus: 00 index 0 io port: [0, ffff]
[    0.980510] bus: 00 index 1 mmio: [0, ffffffff]
[    0.980515] bus: 01 index 0 io port: [d000, dfff]
[    0.980520] bus: 01 index 1 mmio: [dfd00000, dfdfffff]
[    0.980525] bus: 01 index 2 mmio: [ffd00000, ffdfffff]
[    0.980530] bus: 01 index 3 mmio: [0, 0]
[    0.980535] bus: 02 index 0 mmio: [0, 0]
[    0.980539] bus: 02 index 1 mmio: [dfc00000, dfcfffff]
[    0.980544] bus: 02 index 2 mmio: [0, 0]
[    0.980548] bus: 02 index 3 mmio: [0, 0]
[    0.980553] bus: 03 index 0 mmio: [0, 0]
[    0.980557] bus: 03 index 1 mmio: [0, 0]
[    0.980561] bus: 03 index 2 mmio: [0, 0]
[    0.980566] bus: 03 index 3 io port: [0, ffff]
[    0.980570] bus: 03 index 4 mmio: [0, ffffffff]
[    0.980592] NET: Registered protocol family 2
[    0.996160] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.996764] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.997607] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.998060] TCP: Hash tables configured (established 131072 bind 65536)
[    0.998067] TCP reno registered
[    1.004221] NET: Registered protocol family 1
[    1.004462] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[    1.440062] Switched to high resolution mode on CPU 0
[    1.525527]  it is
[    2.109876] Freeing initrd memory: 8003k freed
[    2.112764] audit: initializing netlink socket (disabled)
[    2.112802] type=2000 audit(1233001757.112:1): initialized
[    2.122947] highmem bounce pool size: 64 pages
[    2.122963] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.129638] VFS: Disk quotas dquot_6.5.1
[    2.129864] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.130126] msgmni has been set to 1762
[    2.130437] io scheduler noop registered
[    2.130444] io scheduler anticipatory registered
[    2.130449] io scheduler deadline registered
[    2.130482] io scheduler cfq registered (default)
[    2.130510] pci 0000:00:02.0: Boot video device
[    2.130963] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.131008] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.131058] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.131169] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.131311] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.131503] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.131546] pcieport-driver 0000:00:1c.1: found MSI capability
[    2.131590] pci_express 0000:00:1c.1:pcie00: allocate port service
[    2.131698] pci_express 0000:00:1c.1:pcie02: allocate port service
[    2.131814] pci_express 0000:00:1c.1:pcie03: allocate port service
[    2.132671] isapnp: Scanning for PnP cards...
[    2.485811] isapnp: No Plug & Play device found
[    2.593327] hpet_resources: 0xfed03000 is busy
[    2.593484] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.599691] brd: module loaded
[    2.599876] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.600182] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.618691] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.618706] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.619535] mice: PS/2 mouse device common for all mice
[    2.619958] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.620000] rtc0: alarms up to one year, y3k, hpet irqs
[    2.620387] EISA: Probing bus 0 at eisa.0
[    2.620437] EISA: Detected 0 cards.
[    2.620444] cpuidle: using governor ladder
[    2.620449] cpuidle: using governor menu
[    2.621679] TCP cubic registered
[    2.621740] Using IPI No-Shortcut mode
[    2.622351] registered taskstats version 1
[    2.622575]   Magic number: 9:969:498
[    2.622748] rtc_cmos 00:04: setting system clock to 2009-01-26 20:29:18 UTC (1233001758)
[    2.622756] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.622761] EDD information not available.
[    2.623162] Freeing unused kernel memory: 424k freed
[    2.623308] Write protecting the kernel text: 2576k
[    2.623410] Write protecting the kernel read-only data: 936k
[    2.634252] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.980153] fuse init (API version 7.9)
[    3.101074] ACPI: SSDT 3F5E8C90, 0253 (r2  PmRef  Cpu0Ist     3000 INTL 20051117)
[    3.101931] ACPI: SSDT 3F5E7690, 0653 (r2  PmRef  Cpu0Cst     3001 INTL 20051117)
[    3.108301] Monitor-Mwait will be used to enter C-1 state
[    3.108310] Monitor-Mwait will be used to enter C-2 state
[    3.108317] Monitor-Mwait will be used to enter C-3 state
[    3.128071] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.132078] processor ACPI0007:00: registered as cooling_device0
[    3.132091] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.132963] ACPI: SSDT 3F5E8F10, 00D0 (r2  PmRef  Cpu1Ist     3000 INTL 20051117)
[    3.133760] ACPI: SSDT 3F611B10, 0083 (r2  PmRef  Cpu1Cst     3000 INTL 20051117)
[    3.136012] Marking TSC unstable due to TSC halts in idle
[    3.221870] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.222039] processor ACPI0007:01: registered as cooling_device1
[    3.222056] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.285075] thermal LNXTHERM:01: registered as thermal_zone0
[    3.396497] ACPI: Thermal Zone [THRM] (63 C)
[    3.440039] Clocksource tsc unstable (delta = -147034608 ns)
[    3.894017] usbcore: registered new interface driver usbfs
[    3.894087] usbcore: registered new interface driver hub
[    3.932663] usbcore: registered new device driver usb
[    3.962108] USB Universal Host Controller Interface driver v3.0
[    3.962207] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.962226] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.962236] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.962360] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.962414] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e080
[    3.962771] usb usb1: configuration #1 chosen from 1 choice
[    3.962859] hub 1-0:1.0: USB hub found
[    3.962882] hub 1-0:1.0: 2 ports detected
[    4.068643] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.068664] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.068675] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.068758] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.068816] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e060
[    4.069132] usb usb2: configuration #1 chosen from 1 choice
[    4.069233] hub 2-0:1.0: USB hub found
[    4.069256] hub 2-0:1.0: 2 ports detected
[    4.176671] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.176692] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.176703] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.176785] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.176845] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e040
[    4.177230] usb usb3: configuration #1 chosen from 1 choice
[    4.177328] hub 3-0:1.0: USB hub found
[    4.177353] hub 3-0:1.0: 2 ports detected
[    4.284557] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    4.284578] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.284588] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.284664] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.284722] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e020
[    4.285028] usb usb4: configuration #1 chosen from 1 choice
[    4.285121] hub 4-0:1.0: USB hub found
[    4.285155] hub 4-0:1.0: 2 ports detected
[    4.398575] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.398614] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.398645] r8169 0000:01:00.0: setting latency timer to 64
[    4.398669] r8169 0000:01:00.0: unknown MAC (37a00000)
[    4.399522] eth0: RTL8169 at 0xf883a000, 00:21:85:53:45:ed, XID 34a00000 IRQ 221
[    4.670495] No dock devices found.
[    4.761489] SCSI subsystem initialized
[    4.768975] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.769002] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.769012] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.769105] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.773060] ehci_hcd 0000:00:1d.7: debug port 1
[    4.773075] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.773097] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdff40000
[    4.792056] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.792413] usb usb5: configuration #1 chosen from 1 choice
[    4.792505] hub 5-0:1.0: USB hub found
[    4.792528] hub 5-0:1.0: 8 ports detected
[    4.868023] libata version 3.00 loaded.
[    5.014929] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.015003] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    5.015035] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    5.031645] ata_piix 0000:00:1f.2: version 2.12
[    5.031671] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.031682] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    5.185081] ata_piix 0000:00:1f.2: setting latency timer to 64
[    5.185284] scsi0 : ata_piix
[    5.185590] scsi1 : ata_piix
[    5.185714] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe0a0 irq 14
[    5.185724] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xe0a8 irq 15
[    5.369164] usb 5-5: new high speed USB device using ehci_hcd and address 2
[    5.403641] ata1.00: ATA-8: WDC WD1200BEVT-22ZCT0, 11.01A11, max UDMA/133
[    5.403654] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.421024] ata1.00: configured for UDMA/133
[    5.577406] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVT-2 11.0 PQ: 0 ANSI: 5
[    5.681163] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.718268] Driver 'sd' needs updating - please use bus_type methods
[    5.718542] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.718610] sd 0:0:0:0: [sda] Write Protect is off
[    5.718619] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.718728] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.718938] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.718998] sd 0:0:0:0: [sda] Write Protect is off
[    5.719007] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.719112] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.719126]  sda: sda1 sda2 sda3
[    5.737379] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.764469] usb 5-5: configuration #1 chosen from 1 choice
[    5.912087] usb 5-6: new high speed USB device using ehci_hcd and address 3
[    6.055686] usb 5-6: configuration #1 chosen from 1 choice
[    6.172872] usbcore: registered new interface driver libusual
[    6.192648] Initializing USB Mass Storage driver...
[    6.193665] scsi2 : SCSI emulation for USB Mass Storage devices
[    6.195221] usbcore: registered new interface driver usb-storage
[    6.195235] USB Mass Storage support registered.
[    6.196239] usb-storage: device found at 3
[    6.196248] usb-storage: waiting for device to settle before scanning
[    6.310304] PM: Starting manual resume from disk
[    6.310314] PM: Resume from partition 8:2
[    6.310318] PM: Checking hibernation image.
[    6.310642] PM: Resume from disk failed.
[    6.388016] kjournald starting.  Commit interval 5 seconds
[    6.388076] EXT3-fs: mounted filesystem with ordered data mode.
[    6.592094] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    6.818214] usb 4-1: configuration #1 chosen from 1 choice
[   11.192559] usb-storage: device scan complete
[   11.199149] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   11.202452] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   11.202742] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   12.136613] udevd version 124 started
[   14.053885] Linux agpgart interface v0.103
[   14.177426] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[   14.177653] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   14.218825] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.431792] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   14.432255] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.877383] iTCO_vendor_support: vendor-support=0
[   14.965752] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.967049] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0460)
[   14.968846] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.972118] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   15.415347] intel_rng: FWH not detected
[   15.532618] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   15.548680] ACPI: Power Button (FF) [PWRF]
[   15.549025] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C0D:00/input/input4
[   15.605204] ACPI: Lid Switch [LID0]
[   15.605507] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   15.629049] ACPI: Power Button (CM) [PWRB]
[   15.629392] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   15.653049] ACPI: Sleep Button (CM) [SLPB]
[   17.829841] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[   17.829853] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   17.833729] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   17.833739] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   17.848364] acpi device:1c: registered as cooling_device2
[   17.848818] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1a/input/input7
[   17.860047] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[   18.379510] rt2860 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.380061] 
[   18.380064] 
[   18.380066] === pAd = f8b81000, size = 580788 ===
[   18.380070] 
[   18.380076] <-- RTMPAllocAdapterBlock, Status=0
[   18.380125] rt2860 0000:02:00.0: setting latency timer to 64
[   19.177299] ACPI: AC Adapter [ADP1] (on-line)
[   19.313131] Bluetooth: Core ver 2.13
[   19.333476] NET: Registered protocol family 31
[   19.333484] Bluetooth: HCI device and connection manager initialized
[   19.333494] Bluetooth: HCI socket layer initialized
[   19.351690] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.351739] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.382074] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   19.419112] Linux video capture interface: v2.00
[   19.436226] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   19.437607] usbcore: registered new interface driver btusb
[   19.469049] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0203)
[   19.470155] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/input/input8
[   19.625433] usbcore: registered new interface driver uvcvideo
[   19.625490] USB Video Class driver (v0.1.0)
[   19.675524] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input9
[   20.204386] ACPI: Battery Slot [BAT1] (battery present)
[   20.204930] ACPI: WMI: Mapper loaded
[   23.262760] lp: driver loaded but no devices found
[   23.770747] Adding 1116508k swap on /dev/sda2.  Priority:-1 extents:1 across:1116508k
[   24.528542] EXT3 FS on sda1, internal journal
[   25.936978] type=1505 audit(1233001782.001:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4109
[   26.357258] type=1505 audit(1233001782.421:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4114
[   26.357720] type=1505 audit(1233001782.421:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4114
[   26.464450] type=1505 audit(1233001782.529:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4118
[   26.697196] ip_tables: (C) 2000-2006 Netfilter Core Team
[   29.535976] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   31.858922] apm: BIOS not found.
[   32.285370] ppdev: user-space parallel port driver
[   35.976572] uvcvideo: UVC non compliance - GET_MIN/MAX(PROBE) incorrectly supported. Enabling workaround.
[   36.698537] Bluetooth: L2CAP ver 2.11
[   36.698549] Bluetooth: L2CAP socket layer initialized
[   36.773488] Bluetooth: SCO (Voice Link) ver 0.6
[   36.773506] Bluetooth: SCO socket layer initialized
[   36.804007] Bluetooth: RFCOMM socket layer initialized
[   36.806249] Bluetooth: RFCOMM TTY layer initialized
[   36.806267] Bluetooth: RFCOMM ver 1.10
[   36.885368] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.885388] Bluetooth: BNEP filters: protocol multicast
[   36.976174] Bridge firewalling registered
[   36.980089] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   40.145567] NET: Registered protocol family 10
[   40.149267] lo: Disabled Privacy Extensions
[   40.784464] [drm] Initialized drm 1.1.0 20060810
[   40.797086] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   40.797106] pci 0000:00:02.0: setting latency timer to 64
[   40.797492] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.062272] r8169: eth0: link down
[   41.062834] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   41.086621] RX DESC f0d72000  size = 2048
[   41.087159] <-- RTMPAllocTxRxRingMemory, Status=0
[   41.092227] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   41.092248] 1. Phy Mode = 0
[   41.092253] 2. Phy Mode = 0
[   41.121615] 3. Phy Mode = 0
[   41.126337] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   41.126345] MCS Set = 00 00 00 00 00
[   41.127981] <==== RTMPInitialize, Status=0
[   41.128057] 0x1300 = 00073200
[   41.234181] NET: Registered protocol family 17
[   41.902554] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   41.902591] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   41.906197] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   41.906234] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   41.953444] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[   41.953482] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   41.956988] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   41.957022] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   42.499001] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   42.499039] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   42.503019] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   42.503056] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   51.292117] ra0: no IPv6 routers present
[   66.277201] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[   96.284185] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  136.288183] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  186.296194] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  246.304177] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  306.313175] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  366.321176] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  426.329203] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  486.337203] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  546.345203] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  588.180689] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[  588.180716] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  588.184494] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[  588.184509] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  588.895392] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[  588.895418] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  588.899107] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[  588.899118] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  606.353140] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  614.340345] ACPI: EC: non-query interrupt received, switching to interrupt mode
[  615.355476] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[  615.355502] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  615.359484] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[  615.359504] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  615.415420] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[  615.415446] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  615.419474] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[  615.419494] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  615.484289] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[  615.484315] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  615.488068] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[  615.488088] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  615.544171] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[  615.544198] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  615.548205] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[  615.548224] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  616.365126] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  616.366042] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[  619.357439] ACPI: EC: non-query interrupt received, switching to interrupt mode
[  619.876384] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[  619.876423] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  619.879939] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[  619.879946] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  619.996271] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[  619.996299] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  619.999991] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[  619.999999] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  620.067417] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[  620.067456] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  620.070965] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[  620.071005] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  620.176130] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[  620.176153] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  620.179817] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[  620.179838] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  665.400179] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121
[  714.321856] __set_isoc_interface: hci0 setting interface failed (71)
[  714.408173] usb 4-1: USB disconnect, address 2
[  714.408741] btusb_intr_complete: hci0 urb f79d4c00 failed to resubmit (19)
[  714.408777] btusb_bulk_complete: hci0 urb ee38ca00 failed to resubmit (19)
[  714.409739] btusb_bulk_complete: hci0 urb ee38c480 failed to resubmit (19)
[  714.422922] btusb_send_frame: hci0 urb f7916500 submission failed
[  714.422993] __set_isoc_interface: hci0 setting interface failed (19)
[  715.392207] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  715.601578] usb 4-1: configuration #1 chosen from 1 choice
[  725.405177] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 121

```

---

