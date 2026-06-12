---
title: "Disable a specific device in my laptop"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Kosimo on 2009-04-26
Hello guys.

I would like to find the way to disable my Bluetooth card as I'm not using it at all. Powertop says that is waking up my system 100% of the time and I can't physically remove it. In windows I can disable the device on device manager. There is something similar I can do here in Jaunty?


Thank you!

---

### Post by 3rdalbum on 2009-04-26
Find out the name of your Bluetooth device's driver (usually the boot log in the "dmesg" command helps). Let's say it's "bcm203x":

```
sudo modprobe -r bcm203x
```

You can find a list of Bluetooth driver modules that are currently available by typing this command:

```
sudo modprobe -l | grep "bluetooth"
```

The actual filenames (not the whole paths, just the names), minus the ".ko" at the end, is the name of the module.

Note that the device might continue to draw as much power even when it's not associated with a driver... you'd have to try it and see.

---

### Post by Kosimo on 2009-04-26
> **3rdalbum said:**
> Find out the name of your Bluetooth device's driver (usually the boot log in the "dmesg" command helps). Let's say it's "bcm203x":

```
sudo modprobe -r bcm203x
```

You can find a list of Bluetooth driver modules that are currently available by typing this command:

```
sudo modprobe -l | grep "bluetooth"
```

The actual filenames (not the whole paths, just the names), minus the ".ko" at the end, is the name of the module.

Note that the device might continue to draw as much power even when it's not associated with a driver... you'd have to try it and see.


Hey, thank you for your answer but I'm a bit lost.

I tried the codes but: dmesg gives me an endless list


```
[    0.564126] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.564133] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.564139] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.564141] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.564144] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.564146] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.564149] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.564151] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[    0.564154] system 00:06: ioport range 0xfe80-0xfeff has been reserved
[    0.598889] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.598892] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.598895] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.598899] pci 0000:00:01.0:   MEM window: 0xcc000000-0xceffffff
[    0.598903] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.598908] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.598912] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.598918] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
[    0.598923] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.598932] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.598936] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.598942] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
[    0.598947] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    0.598956] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.598960] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.598966] pci 0000:00:1c.2:   MEM window: 0xfa000000-0xfbffffff
[    0.598972] pci 0000:00:1c.2:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
[    0.598980] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:08
[    0.598983] pci 0000:00:1c.4:   IO window: 0x6000-0x6fff
[    0.598990] pci 0000:00:1c.4:   MEM window: 0xfc000000-0xfc0fffff
[    0.598995] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.599005] pci 0000:09:03.0: CardBus bridge, secondary bus 0000:0a
[    0.599007] pci 0000:09:03.0:   IO window: 0x007000-0x0070ff
[    0.599013] pci 0000:09:03.0:   IO window: 0x007400-0x0074ff
[    0.599019] pci 0000:09:03.0:   PREFETCH window: 0x88000000-0x8bffffff
[    0.599025] pci 0000:09:03.0:   MEM window: 0x90000000-0x93ffffff
[    0.599030] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.599034] pci 0000:00:1e.0:   IO window: 0x7000-0x7fff
[    0.599041] pci 0000:00:1e.0:   MEM window: 0xfc100000-0xfc1fffff
[    0.599046] pci 0000:00:1e.0:   PREFETCH window: 0x00000088000000-0x0000008bffffff
[    0.599061] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.599065] pci 0000:00:01.0: setting latency timer to 64
[    0.599075] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.599080] pci 0000:00:1c.0: setting latency timer to 64
[    0.599089] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.599094] pci 0000:00:1c.1: setting latency timer to 64
[    0.599104] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.599109] pci 0000:00:1c.2: setting latency timer to 64
[    0.599119] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.599124] pci 0000:00:1c.4: setting latency timer to 64
[    0.599133] pci 0000:00:1e.0: setting latency timer to 64
[    0.599143] pci 0000:09:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.599150] bus: 00 index 0 io port: [0x00-0xffff]
[    0.599152] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.599154] bus: 01 index 0 io port: [0x2000-0x2fff]
[    0.599156] bus: 01 index 1 mmio: [0xcc000000-0xceffffff]
[    0.599158] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.599160] bus: 01 index 3 mmio: [0x0-0x0]
[    0.599162] bus: 02 index 0 io port: [0x3000-0x3fff]
[    0.599164] bus: 02 index 1 mmio: [0xf6000000-0xf7ffffff]
[    0.599166] bus: 02 index 2 mmio: [0xf0000000-0xf1ffffff]
[    0.599168] bus: 02 index 3 mmio: [0x0-0x0]
[    0.599169] bus: 04 index 0 io port: [0x4000-0x4fff]
[    0.599171] bus: 04 index 1 mmio: [0xf8000000-0xf9ffffff]
[    0.599173] bus: 04 index 2 mmio: [0xf2000000-0xf3ffffff]
[    0.599175] bus: 04 index 3 mmio: [0x0-0x0]
[    0.599177] bus: 06 index 0 io port: [0x5000-0x5fff]
[    0.599179] bus: 06 index 1 mmio: [0xfa000000-0xfbffffff]
[    0.599181] bus: 06 index 2 mmio: [0xf4000000-0xf5ffffff]
[    0.599183] bus: 06 index 3 mmio: [0x0-0x0]
[    0.599185] bus: 08 index 0 io port: [0x6000-0x6fff]
[    0.599187] bus: 08 index 1 mmio: [0xfc000000-0xfc0fffff]
[    0.599189] bus: 08 index 2 mmio: [0x0-0x0]
[    0.599190] bus: 08 index 3 mmio: [0x0-0x0]
[    0.599192] bus: 09 index 0 io port: [0x7000-0x7fff]
[    0.599194] bus: 09 index 1 mmio: [0xfc100000-0xfc1fffff]
[    0.599196] bus: 09 index 2 mmio: [0x88000000-0x8bffffff]
[    0.599198] bus: 09 index 3 io port: [0x00-0xffff]
[    0.599200] bus: 09 index 4 mmio: [0x000000-0xffffffff]
[    0.599202] bus: 0a index 0 io port: [0x7000-0x70ff]
[    0.599204] bus: 0a index 1 io port: [0x7400-0x74ff]
[    0.599206] bus: 0a index 2 mmio: [0x88000000-0x8bffffff]
[    0.599208] bus: 0a index 3 mmio: [0x90000000-0x93ffffff]
[    0.599216] NET: Registered protocol family 2
[    0.609049] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.609288] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.609635] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.609823] TCP: Hash tables configured (established 131072 bind 65536)
[    0.609825] TCP reno registered
[    0.613070] NET: Registered protocol family 1
[    0.613189] checking if image is initramfs... it is
[    1.215289] Freeing initrd memory: 7380k freed
[    1.215330] Simple Boot Flag at 0x36 set to 0x1
[    1.215504] cpufreq: No nForce2 chipset.
[    1.215631] audit: initializing netlink socket (disabled)
[    1.215648] type=2000 audit(1240742446.212:1): initialized
[    1.222644] highmem bounce pool size: 64 pages
[    1.222650] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.223940] VFS: Disk quotas dquot_6.5.1
[    1.223998] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.224580] fuse init (API version 7.10)
[    1.224664] msgmni has been set to 1698
[    1.224834] alg: No test for stdrng (krng)
[    1.224845] io scheduler noop registered
[    1.224847] io scheduler anticipatory registered
[    1.224849] io scheduler deadline registered
[    1.224863] io scheduler cfq registered (default)
[    1.225040] pci 0000:01:00.0: Boot video device
[    1.242122] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.242162] pcieport-driver 0000:00:01.0: found MSI capability
[    1.242188] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.242198] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.242212] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.242224] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.242278] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.242330] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.242365] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.242382] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.242394] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.242406] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.242484] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.242536] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.242571] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.242588] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.242600] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.242612] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.242692] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.242745] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.242780] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    1.242797] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.242809] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.242821] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.242898] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.242950] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.242986] pcieport-driver 0000:00:1c.4: irq 2299 for MSI/MSI-X
[    1.243002] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.243016] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.243028] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.243117] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.245127] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.247496] ACPI: AC Adapter [ADP1] (on-line)
[    1.264621] ACPI: EC: GPE storm detected, transactions will use polling mode
[    1.290696] ACPI: Battery Slot [BAT0] (battery present)
[    1.290765] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.292390] ACPI: Lid Switch [LID0]
[    1.292432] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.292441] ACPI: Power Button (CM) [PWRB]
[    1.295902] ACPI: SSDT 7FED8DB7, 025F (r1   Sony     VAIO 20071221 PTL  20050624)
[    1.296314] ACPI: SSDT 7FED886E, 04B7 (r1   Sony     VAIO 20071221 PTL  20050624)
[    1.298789] Monitor-Mwait will be used to enter C-1 state
[    1.298792] Monitor-Mwait will be used to enter C-2 state
[    1.298795] Monitor-Mwait will be used to enter C-3 state
[    1.298808] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.298832] processor ACPI_CPU:00: registered as cooling_device0
[    1.298835] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.299275] ACPI: SSDT 7FED9016, 00E4 (r1   Sony     VAIO 20071221 PTL  20050624)
[    1.299642] ACPI: SSDT 7FED8D25, 0092 (r1   Sony     VAIO 20071221 PTL  20050624)
[    1.300945] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.300964] processor ACPI_CPU:01: registered as cooling_device1
[    1.300968] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.328620] thermal LNXTHERM:01: registered as thermal_zone0
[    1.332686] ACPI: Thermal Zone [TZ00] (30 C)
[    1.334524] thermal LNXTHERM:02: registered as thermal_zone1
[    1.337511] ACPI: Thermal Zone [TZ01] (30 C)
[    1.337564] isapnp: Scanning for PnP cards...
[    1.691684] isapnp: No Plug & Play device found
[    1.697226] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.698207] brd: module loaded
[    1.698499] loop: module loaded
[    1.698564] Fixed MDIO Bus: probed
[    1.698569] PPP generic driver version 2.4.2
[    1.698621] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.698648] Driver 'sd' needs updating - please use bus_type methods
[    1.698657] Driver 'sr' needs updating - please use bus_type methods
[    1.698697] ahci 0000:00:1f.2: version 3.0
[    1.698712] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.698753] ahci 0000:00:1f.2: irq 2298 for MSI/MSI-X
[    1.698815] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
[    1.698818] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    1.698824] ahci 0000:00:1f.2: setting latency timer to 64
[    1.698932] scsi0 : ahci
[    1.699008] scsi1 : ahci
[    1.699062] scsi2 : ahci
[    1.699122] ata1: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 2298
[    1.699124] ata2: DUMMY
[    1.699126] ata3: DUMMY
[    2.016021] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.016839] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 succeeded
[    2.016842] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.017178] ata1.00: ATA-8: FUJITSU MHY2200BH, 0000000B, max UDMA/100
[    2.017181] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.018073] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 succeeded
[    2.018076] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.018428] ata1.00: configured for UDMA/100
[    2.032116] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHY2200B 0000 PQ: 0 ANSI: 5
[    2.032206] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    2.032221] sd 0:0:0:0: [sda] Write Protect is off
[    2.032223] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.032248] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.032303] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    2.032317] sd 0:0:0:0: [sda] Write Protect is off
[    2.032319] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.032343] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.032346]  sda: sda1 sda2 sda3 sda4
[    2.099721] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.099767] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.099814] ata_piix 0000:00:1f.1: version 2.12
[    2.099821] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.099855] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.099926] scsi3 : ata_piix
[    2.099981] scsi4 : ata_piix
[    2.100766] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    2.100769] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    2.280440] ata4.00: ATAPI: PIONEER DVD-RW  DVRKD08, 1.00, max UDMA/33
[    2.312391] ata4.00: configured for UDMA/33
[    2.576818] scsi 3:0:0:0: CD-ROM            PIONEER  DVD-RW  DVRKD08  1.00 PQ: 0 ANSI: 5
[    2.701024] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.701027] Uniform CD-ROM driver Revision: 3.20
[    2.701112] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.701146] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.701799] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.701817] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.701831] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.701835] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.701887] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.705808] ehci_hcd 0000:00:1a.7: debug port 1
[    2.705815] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.705829] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc404800
[    2.720008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.720071] usb usb1: configuration #1 chosen from 1 choice
[    2.720097] hub 1-0:1.0: USB hub found
[    2.720104] hub 1-0:1.0: 4 ports detected
[    2.720207] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.720218] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.720221] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.720261] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.724178] ehci_hcd 0000:00:1d.7: debug port 1
[    2.724185] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.724197] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc404c00
[    2.736008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.736069] usb usb2: configuration #1 chosen from 1 choice
[    2.736093] hub 2-0:1.0: USB hub found
[    2.736099] hub 2-0:1.0: 6 ports detected
[    2.736193] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.736209] uhci_hcd: USB Universal Host Controller Interface driver
[    2.736229] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.736235] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.736239] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.736286] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.736322] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    2.736397] usb usb3: configuration #1 chosen from 1 choice
[    2.736420] hub 3-0:1.0: USB hub found
[    2.736427] hub 3-0:1.0: 2 ports detected
[    2.736508] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.736514] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.736518] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.736559] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.736597] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    2.736665] usb usb4: configuration #1 chosen from 1 choice
[    2.736689] hub 4-0:1.0: USB hub found
[    2.736695] hub 4-0:1.0: 2 ports detected
[    2.736779] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.736785] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.736789] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.736827] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.736854] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    2.736927] usb usb5: configuration #1 chosen from 1 choice
[    2.736953] hub 5-0:1.0: USB hub found
[    2.736958] hub 5-0:1.0: 2 ports detected
[    2.737043] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.737049] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.737053] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.737092] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.737127] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    2.737201] usb usb6: configuration #1 chosen from 1 choice
[    2.737224] hub 6-0:1.0: USB hub found
[    2.737230] hub 6-0:1.0: 2 ports detected
[    2.737309] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.737315] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.737319] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.737362] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.737389] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    2.737457] usb usb7: configuration #1 chosen from 1 choice
[    2.737480] hub 7-0:1.0: USB hub found
[    2.737486] hub 7-0:1.0: 2 ports detected
[    2.737610] usbcore: registered new interface driver libusual
[    2.737639] usbcore: registered new interface driver usbserial
[    2.737649] USB Serial support registered for generic
[    2.737665] usbcore: registered new interface driver usbserial_generic
[    2.737666] usbserial: USB Serial Driver core
[    2.737711] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.740771] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.744377] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.744382] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.744385] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.744387] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.744390] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.748038] mice: PS/2 mouse device common for all mice
[    2.760069] rtc_cmos 00:07: RTC can wake from S4
[    2.760101] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.760134] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.760189] device-mapper: uevent: version 1.0.3
[    2.760267] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.760335] device-mapper: multipath: version 1.0.5 loaded
[    2.760338] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.760410] EISA: Probing bus 0 at eisa.0
[    2.760416] Cannot allocate resource for EISA slot 1
[    2.760419] Cannot allocate resource for EISA slot 2
[    2.760421] Cannot allocate resource for EISA slot 3
[    2.760423] Cannot allocate resource for EISA slot 4
[    2.760425] Cannot allocate resource for EISA slot 5
[    2.760428] Cannot allocate resource for EISA slot 6
[    2.760430] Cannot allocate resource for EISA slot 7
[    2.760436] EISA: Detected 0 cards.
[    2.760544] cpuidle: using governor ladder
[    2.760658] cpuidle: using governor menu
[    2.761142] TCP cubic registered
[    2.761238] NET: Registered protocol family 10
[    2.761650] lo: Disabled Privacy Extensions
[    2.761974] NET: Registered protocol family 17
[    2.761990] Bluetooth: L2CAP ver 2.11
[    2.761992] Bluetooth: L2CAP socket layer initialized
[    2.761994] Bluetooth: SCO (Voice Link) ver 0.6
[    2.761996] Bluetooth: SCO socket layer initialized
[    2.762025] Bluetooth: RFCOMM socket layer initialized
[    2.762031] Bluetooth: RFCOMM TTY layer initialized
[    2.762032] Bluetooth: RFCOMM ver 1.10
[    2.762079] Marking TSC unstable due to TSC halts in idle
[    2.762889] Using IPI No-Shortcut mode
[    2.762955] registered taskstats version 1
[    2.763079]   Magic number: 5:134:680
[    2.763164] rtc_cmos 00:07: setting system clock to 2009-04-26 10:40:48 UTC (1240742448)
[    2.763167] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.763169] EDD information not available.
[    2.763457] Freeing unused kernel memory: 532k freed
[    2.763605] Write protecting the kernel text: 4128k
[    2.763662] Write protecting the kernel read-only data: 1532k
[    2.966355] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.045018] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.180949] usb 1-2: configuration #1 chosen from 1 choice
[    3.428082] ACPI: EC: missing confirmations, switch off interrupt mode.
[    3.470941] sky2 driver version 1.22
[    3.470992] sky2 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.471006] sky2 0000:08:00.0: setting latency timer to 64
[    3.471049] sky2 0000:08:00.0: Yukon-2 FE chip revision 1
[    3.500019] Clocksource tsc unstable (delta = -146400941 ns)
[    3.501007] ohci1394 0000:09:03.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.534814] sky2 0000:08:00.0: Marvell Yukon 88E8036 Fast Ethernet Controller
[    3.534816]  Part Number: Yukon 88E8036
[    3.534818]  Engineering Level: Rev. 1.6
[    3.534820]  Manufacturer: Marvell
[    3.534899] sky2 0000:08:00.0: irq 2297 for MSI/MSI-X
[    3.550757] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fc102000-fc1027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.593064] sky2 eth0: addr 00:1a:80:a6:45:c2
[    3.713143] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    3.888533] usb 7-1: configuration #1 chosen from 1 choice
[    3.890485] hub 7-1:1.0: USB hub found
[    3.892455] hub 7-1:1.0: 3 ports detected
[    4.137219] PM: Starting manual resume from disk
[    4.137223] PM: Resume from partition 8:4
[    4.137224] PM: Checking hibernation image.
[    4.137409] PM: Resume from disk failed.
[    4.151755] EXT4-fs: barriers enabled
[    4.168060] kjournald2 starting.  Commit interval 5 seconds
[    4.168068] EXT4-fs: delayed allocation enabled
[    4.168070] EXT4-fs: file extents enabled
[    4.168638] EXT4-fs: mballoc enabled
[    4.168641] EXT4-fs: mounted filesystem with ordered data mode.
[    4.185461] usb 7-1.1: new full speed USB device using uhci_hcd and address 3
[    4.318528] usb 7-1.1: configuration #1 chosen from 1 choice
[    4.393454] usb 7-1.2: new full speed USB device using uhci_hcd and address 4
[    4.512517] usb 7-1.2: configuration #1 chosen from 1 choice
[    4.589453] usb 7-1.3: new full speed USB device using uhci_hcd and address 5
[    4.708520] usb 7-1.3: configuration #1 chosen from 1 choice
[    4.825485] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603029f45a5]
[    9.667874] udev: starting version 141
[    9.921097] cfg80211: Using static regulatory domain info
[    9.921101] cfg80211: Regulatory domain: US
[    9.921103] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.921105] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[    9.921108] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[    9.921110] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[    9.921112] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[    9.921115] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[    9.921117] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[    9.921154] cfg80211: Calling CRDA for country: US
[    9.932414] sony-laptop: Sony Notebook Control Driver v0.6.
[    9.934630] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:29/SNY5001:00/input/input4
[    9.952286] input: Sony Vaio Jogdial as /devices/virtual/input/input5
[    9.977307] sony-laptop: detected Sony Vaio FZ Series
[   10.076003] iTCO_vendor_support: vendor-support=0
[   10.121902] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.122194] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   10.122292] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.138443] cfg80211: Regulatory domain changed to country: US
[   10.138447] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.138450] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   10.138452] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   10.138454] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.138457] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.138459] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   10.221329] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   10.221446] usbcore: registered new interface driver btusb
[   10.258177] usbcore: registered new interface driver hiddev
[   10.260801] input: HID 044e:3013 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.2/7-1.2:1.0/input/input6
[   10.264210] generic-usb 0003:044E:3013.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 044e:3013] on usb-0000:00:1d.2-1.2/input0
[   10.267824] input: HID 044e:3012 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.3/7-1.3:1.0/input/input7
[   10.270219] generic-usb 0003:044E:3012.0002: input,hidraw1: USB HID v1.11 Mouse [HID 044e:3012] on usb-0000:00:1d.2-1.3/input0
[   10.270244] usbcore: registered new interface driver usbhid
[   10.270267] usbhid: v2.6:USB HID core driver
[   10.279230] Linux agpgart interface v0.103
[   11.153194] nvidia: module license 'NVIDIA' taints kernel.
[   11.267750] yenta_cardbus 0000:09:03.0: CardBus bridge found [104d:9005]
[   11.267774] yenta_cardbus 0000:09:03.0: Enabling burst memory read transactions
[   11.267780] yenta_cardbus 0000:09:03.0: Using CSCINT to route CSC interrupts to PCI
[   11.267783] yenta_cardbus 0000:09:03.0: Routing CardBus interrupts to PCI
[   11.267789] yenta_cardbus 0000:09:03.0: TI: mfunc 0x01121b22, devctl 0x64
[   11.299782] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   11.406166] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.406177] nvidia 0000:01:00.0: setting latency timer to 64
[   11.406454] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.51  Thu Apr 16 19:02:15 PDT 2009
[   11.433852] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.439931] Linux video capture interface: v2.00
[   11.499098] yenta_cardbus 0000:09:03.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   11.499103] yenta_cardbus 0000:09:03.0: Socket status: 30000006
[   11.499107] pci_bus 0000:09: Raising subordinate bus# of parent bus (#09) from #0a to #0d
[   11.499114] yenta_cardbus 0000:09:03.0: pcmcia: parent PCI bridge I/O window: 0x7000 - 0x7fff
[   11.499117] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: clean.
[   11.499371] yenta_cardbus 0000:09:03.0: pcmcia: parent PCI bridge Memory window: 0xfc100000 - 0xfc1fffff
[   11.499374] yenta_cardbus 0000:09:03.0: pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   11.502054] tifm_7xx1 0000:09:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   11.573105] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   11.573109] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   11.573262] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.573291] iwlagn 0000:06:00.0: setting latency timer to 64
[   11.573403] iwlagn 0000:06:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   11.590730] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183b)
[   11.591125] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   11.591381] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   11.591384] uvcvideo: Failed to initialize the device (-5).
[   11.591421] usbcore: registered new interface driver uvcvideo
[   11.591424] USB Video Class driver (v0.1.0)
[   11.616109] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   11.616197] iwlagn 0000:06:00.0: irq 2296 for MSI/MSI-X
[   11.617514] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.845277] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.845376] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.930192] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   11.932334] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   11.933251] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   11.933989] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   11.934920] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.018684] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input9
[   12.044711] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input10
[   12.079564] lp: driver loaded but no devices found
[   12.177635] Adding 682752k swap on /dev/sda4.  Priority:-1 extents:1 across:682752k
[   12.712965] EXT4 FS on sda3, internal journal on sda3:8
[   13.806890] type=1505 audit(1240738859.540:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2209
[   13.851253] type=1505 audit(1240738859.585:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2213
[   13.851357] type=1505 audit(1240738859.585:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2213
[   13.851398] type=1505 audit(1240738859.585:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2213
[   13.851434] type=1505 audit(1240738859.585:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2213
[   13.975460] type=1505 audit(1240738859.709:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2218
[   13.975634] type=1505 audit(1240738859.709:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2218
[   14.002205] type=1505 audit(1240738859.737:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2222
[   21.265588] sky2 eth0: enabling interface
[   21.265791] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.266416] iwlagn 0000:06:00.0: firmware: requesting lbm-iwlwifi-4965-2.ucode
[   21.357693] iwlagn 0000:06:00.0: loaded firmware version 228.57.2.23
[   21.558154] Registered led device: iwl-phy0::radio
[   21.558176] Registered led device: iwl-phy0::assoc
[   21.558192] Registered led device: iwl-phy0::RX
[   21.558208] Registered led device: iwl-phy0::TX
[   21.588489] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.476775] wlan0: authenticate with AP f63616b8
[   33.478580] wlan0: authenticated
[   33.478582] wlan0: associate with AP f63616b8
[   33.482393] wlan0: RX AssocResp from f4a8804e (capab=0x431 status=0 aid=2)
[   33.482395] wlan0: associated
[   33.504632] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.558841] cfg80211: Calling CRDA for country: US
[   33.561300] cfg80211: Current regulatory domain updated by AP to: US
[   33.561303] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   33.561306] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   43.708050] wlan0: no IPv6 routers present
[   46.409414] wlan0: beacon loss from AP f63616b8 - sending probe request
[   86.653647] wlan0: beacon loss from AP f63616b8 - sending probe request
[  146.458891] wlan0: beacon loss from AP f63616b8 - sending probe request
[  446.311004] wlan0: beacon loss from AP f63616b8 - sending probe request
[  566.434297] wlan0: beacon loss from AP f63616b8 - sending probe request
[  686.456901] wlan0: beacon loss from AP f63616b8 - sending probe request
[  806.068155] wlan0: beacon loss from AP f63616b8 - sending probe request
[ 4166.159949] wlan0: beacon loss from AP f63616b8 - sending probe request
[ 4286.284909] wlan0: beacon loss from AP f63616b8 - sending probe request
[ 4350.088085] CE: hpet increasing min_delta_ns to 15000 nsec
[ 4526.327744] wlan0: beacon loss from AP f63616b8 - sending probe request
[ 4646.143816] wlan0: beacon loss from AP f63616b8 - sending probe request
[ 4766.473640] wlan0: beacon loss from AP f63616b8 - sending probe request

```


I can't find anything else. Powertop keeps saying that bluetooth is still waking up my system 100% of the time.  I think something went wrong.

---

### Post by Spiritous on 2009-04-26
> **Kosimo said:**
> Hello guys.

I would like to find the way to disable my Bluetooth card as I'm not using it at all. Powertop says that is waking up my system 100% of the time and I can't physically remove it. In windows I can disable the device on device manager. There is something similar I can do here in Jaunty?


Thank you!

AGH! I know how to do this in windows but ubuntu... Hmm i'll search a bit

---

### Post by Kosimo on 2009-04-26
and this is the output of the other command:

```
sudo modprobe -l | grep "bluetooth"
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/drivers/bluetooth/bcm203x.ko
kernel/drivers/bluetooth/bpa10x.ko
kernel/drivers/bluetooth/bfusb.ko
kernel/drivers/bluetooth/dtl1_cs.ko
kernel/drivers/bluetooth/bt3c_cs.ko
kernel/drivers/bluetooth/bluecard_cs.ko
kernel/drivers/bluetooth/btuart_cs.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/bluetooth/btsdio.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/net/bluetooth/hidp/hidp.ko

```

---

### Post by Didius Falco on 2009-04-26
Go into System/Administration/Services. You'll have to enter your pass word to unlock it. Then uncheck the "Bluetooth Management" box and reboot.

That should fix it.

---

### Post by Kosimo on 2009-04-26
> **Spiritous said:**
> AGH! I know how to do this in windows but ubuntu... Hmm i'll search a bit

Hey! Thanks for answering ;)  I am trying to do it as well :)

---

### Post by Kosimo on 2009-04-26
> **Didius Falco said:**
> Go into System/Administration/Services. You'll have to enter your pass word to unlock it. Then uncheck the "Bluetooth Management" box and reboot.

That should fix it.

Hello, 
This disables the service but not the device itself.

---

### Post by Spiritous on 2009-04-26
> **Kosimo said:**
> Hello, 
This disables the service but not the device itself.

FOUND IT :D [http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html](http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html)

Hope this helps :D

---

### Post by Kosimo on 2009-04-26
> **Spiritous said:**
> FOUND IT :D [http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html](http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html)

Hope this helps :D

Gonna give a try right now!

Thanks!

---

