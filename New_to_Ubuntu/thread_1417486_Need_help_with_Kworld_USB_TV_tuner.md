---
title: "Need help with Kworld USB TV tuner"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by frontline2010 on 2010-02-27
[IMG]http://i192.photobucket.com/albums/z231/frontline2010/IMGA0957.jpg[/IMG]It&#8217;s Saturday and I&#8217;m bored out of my skull so I think i will mess around with Ubuntu and what more can it do.:)
 
 
[LEFT]About a year ago I saw this USB analog TV tuner at Aldi for cheap so I bought it when I got home I called tech support to find the latest drivers. The support guy said that the card was really made by Kworld and told me the real name of the device and what site to download the newest drivers...But time has passed and I forgot the real model name of the USB adapter ..I tried to call them today but they are closed so I tried do download their drivers from the Aldi&#8217;s support site to see what the name came up as and it said PV-TV303URF is there any drivers for Ubuntu for this TV Card? [/LEFT]
 
[LEFT]THERE ARE SOME PICS OF THE TUNER[/LEFT]

---

### Post by Jose Catre-Vandis on 2010-02-27
Stick the stick into your PC with Ubuntu loaded up, open a terminal and check the following (post the out put back here)

```
lsusb
```
```
dmesg
```

This should show us whether the kernel is p[icking up your card and loadinig the modules.

You will then need to install tvtime to tune channels

---

### Post by frontline2010 on 2010-02-27
> **Jose Catre-Vandis said:**
> Stick the stick into your PC with Ubuntu loaded up, open a terminal and check the following (post the out put back here)

```
lsusb
``````
dmesg
```This should show us whether the kernel is p[icking up your card and loadinig the modules.

You will then need to install tvtime to tune channels

Well here  it is.......

[    0.096830] pci 0000:02:01.1: reg 10 32bit mmio: [0xfeafe000-0xfeafefff]
[    0.096876] pci 0000:02:01.1: supports D1 D2
[    0.096879] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.096884] pci 0000:02:01.1: PME# disabled
[    0.096920] pci 0000:02:01.2: reg 10 32bit mmio: [0xfeaffc00-0xfeaffcff]
[    0.096966] pci 0000:02:01.2: supports D1 D2
[    0.096969] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.096974] pci 0000:02:01.2: PME# disabled
[    0.097026] pci 0000:02:0a.0: reg 10 io port: [0xdf80-0xdf9f]
[    0.097072] pci 0000:02:0a.0: supports D1 D2
[    0.097107] pci 0000:02:0a.1: reg 10 io port: [0xdff0-0xdff7]
[    0.097153] pci 0000:02:0a.1: supports D1 D2
[    0.097212] pci 0000:02:0b.0: reg 10 32bit mmio: [0xfeac0000-0xfeadffff]
[    0.097221] pci 0000:02:0b.0: reg 14 32bit mmio: [0xfeaa0000-0xfeabffff]
[    0.097229] pci 0000:02:0b.0: reg 18 io port: [0xdf00-0xdf3f]
[    0.097251] pci 0000:02:0b.0: reg 30 32bit mmio: [0xfea80000-0xfea9ffff]
[    0.097279] pci 0000:02:0b.0: PME# supported from D0 D3hot D3cold
[    0.097285] pci 0000:02:0b.0: PME# disabled
[    0.097372] pci 0000:02:0d.0: supports D1 D2
[    0.097375] pci 0000:02:0d.0: PME# supported from D0 D1 D2 D3hot
[    0.097380] pci 0000:02:0d.0: PME# disabled
[    0.097414] pci 0000:00:1e.0: transparent bridge
[    0.097420] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.097426] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe900000-0xfeafffff]
[    0.097432] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xf4500000-0xf46fffff]
[    0.097489] pci 0000:03:08.0: reg 10 32bit mmio: [0xfe9fd000-0xfe9fdfff]
[    0.097551] pci 0000:03:08.0: supports D1 D2
[    0.097554] pci 0000:03:08.0: PME# supported from D0 D1 D2 D3hot
[    0.097559] pci 0000:03:08.0: PME# disabled
[    0.097605] pci 0000:03:08.1: reg 10 32bit mmio: [0xfe9fe000-0xfe9fefff]
[    0.097666] pci 0000:03:08.1: supports D1 D2
[    0.097669] pci 0000:03:08.1: PME# supported from D0 D1 D2 D3hot
[    0.097675] pci 0000:03:08.1: PME# disabled
[    0.097721] pci 0000:03:08.2: reg 10 32bit mmio: [0xfe9ffc00-0xfe9ffcff]
[    0.097782] pci 0000:03:08.2: supports D1 D2
[    0.097785] pci 0000:03:08.2: PME# supported from D0 D1 D2 D3hot
[    0.097791] pci 0000:03:08.2: PME# disabled
[    0.097850] pci 0000:03:0c.0: reg 10 32bit mmio: [0xfe9ff000-0xfe9ff7ff]
[    0.097860] pci 0000:03:0c.0: reg 14 32bit mmio: [0xfe9f8000-0xfe9fbfff]
[    0.097915] pci 0000:03:0c.0: supports D1 D2
[    0.097918] pci 0000:03:0c.0: PME# supported from D0 D1 D2 D3hot
[    0.097923] pci 0000:03:0c.0: PME# disabled
[    0.097971] pci 0000:02:0d.0: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.097979] pci 0000:02:0d.0: bridge 64bit mmio pref: [0xf4500000-0xf45fffff]
[    0.097998] pci_bus 0000:00: on NUMA node 0
[    0.098004] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.098091] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.107817] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.107940] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[    0.108073] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.108192] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.108311] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.108432] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.108553] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.108672] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.108943] SCSI subsystem initialized
[    0.109033] libata version 3.00 loaded.
[    0.109135] usbcore: registered new interface driver usbfs
[    0.109158] usbcore: registered new interface driver hub
[    0.109190] usbcore: registered new device driver usb
[    0.109365] ACPI: WMI: Mapper loaded
[    0.109369] PCI: Using ACPI for IRQ routing
[    0.109571] Bluetooth: Core ver 2.15
[    0.109614] NET: Registered protocol family 31
[    0.109617] Bluetooth: HCI device and connection manager initialized
[    0.109620] Bluetooth: HCI socket layer initialized
[    0.109623] NetLabel: Initializing
[    0.109626] NetLabel:  domain hash size = 128
[    0.109628] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.109646] NetLabel:  unlabeled traffic allowed by default
[    0.112115] pnp: PnP ACPI init
[    0.112148] ACPI: bus type pnp registered
[    0.115580] pnp: PnP ACPI: found 12 devices
[    0.115584] ACPI: ACPI bus type pnp unregistered
[    0.115590] PnPBIOS: Disabled by ACPI PNP
[    0.115609] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.115615] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.115619] system 00:0b: iomem range 0x100000-0x1fffffff could not be reserved
[    0.115623] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.115627] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.150352] AppArmor: AppArmor Filesystem Enabled
[    0.150371] pci 0000:02:0b.0: BAR 6: address space collision on of device [0xfea80000-0xfea9ffff]
[    0.150398] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.150401] pci 0000:00:01.0:   IO window: disabled
[    0.150406] pci 0000:00:01.0:   MEM window: 0xfc800000-0xfe8fffff
[    0.150411] pci 0000:00:01.0:   PREFETCH window: 0xe4400000-0xf44fffff
[    0.150420] pci 0000:02:0d.0: PCI bridge, secondary bus 0000:03
[    0.150423] pci 0000:02:0d.0:   IO window: disabled
[    0.150431] pci 0000:02:0d.0:   MEM window: 0xfe900000-0xfe9fffff
[    0.150436] pci 0000:02:0d.0:   PREFETCH window: 0x000000f4500000-0x000000f45fffff
[    0.150444] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.150448] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.150456] pci 0000:00:1e.0:   MEM window: 0xfe900000-0xfeafffff
[    0.150462] pci 0000:00:1e.0:   PREFETCH window: 0xf4500000-0xf46fffff
[    0.150480] pci 0000:00:1e.0: setting latency timer to 64
[    0.150495] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.150499] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.150503] pci_bus 0000:01: resource 1 mem: [0xfc800000-0xfe8fffff]
[    0.150506] pci_bus 0000:01: resource 2 pref mem [0xe4400000-0xf44fffff]
[    0.150510] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.150513] pci_bus 0000:02: resource 1 mem: [0xfe900000-0xfeafffff]
[    0.150517] pci_bus 0000:02: resource 2 pref mem [0xf4500000-0xf46fffff]
[    0.150520] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.150524] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.150527] pci_bus 0000:03: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.150531] pci_bus 0000:03: resource 2 pref mem [0xf4500000-0xf45fffff]
[    0.150582] NET: Registered protocol family 2
[    0.150717] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.151068] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.151162] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.151250] TCP: Hash tables configured (established 16384 bind 16384)
[    0.151253] TCP reno registered
[    0.151350] NET: Registered protocol family 1
[    0.151436] Trying to unpack rootfs image as initramfs...
[    0.532528] Freeing initrd memory: 11309k freed
[    0.548111] cpufreq-nforce2: No nForce2 chipset.
[    0.548150] Scanning for low memory corruption every 60 seconds
[    0.548293] audit: initializing netlink socket (disabled)
[    0.548314] type=2000 audit(1267226512.547:1): initialized
[    0.557064] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.558969] VFS: Disk quotas dquot_6.5.2
[    0.559044] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.559785] fuse init (API version 7.12)
[    0.559898] msgmni has been set to 993
[    0.560185] alg: No test for stdrng (krng)
[    0.560203] io scheduler noop registered
[    0.560206] io scheduler anticipatory registered
[    0.560208] io scheduler deadline registered
[    0.560280] io scheduler cfq registered (default)
[    0.560331] pci 0000:01:00.0: Boot video device
[    0.592155] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.592188] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.592346] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.592351] ACPI: Power Button [PWRF]
[    0.592417] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.592424] ACPI: Power Button [PBTN]
[    0.592656] processor LNXCPU:00: registered as cooling_device0
[    0.595607] isapnp: Scanning for PnP cards...
[    0.651972] Switched to high resolution mode on CPU 0
[    0.949513] isapnp: No Plug & Play device found
[    0.950954] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.951075] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.951173] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.951533] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.951670] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.952951] brd: module loaded
[    0.953522] loop: module loaded
[    0.953638] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.953779] ata_piix 0000:00:1f.1: version 2.13
[    0.953857] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.953979] scsi0 : ata_piix
[    0.954106] scsi1 : ata_piix
[    0.955693] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.955697] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.956929] Fixed MDIO Bus: probed
[    0.956979] PPP generic driver version 2.4.2
[    0.957119] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.957153]   alloc irq_desc for 23 on node -1
[    0.957157]   alloc kstat_irqs on node -1
[    0.957166] ehci_hcd 0000:02:01.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    0.957188] ehci_hcd 0000:02:01.2: EHCI Host Controller
[    0.957254] ehci_hcd 0000:02:01.2: new USB bus registered, assigned bus number 1
[    0.980042] ehci_hcd 0000:02:01.2: irq 23, io mem 0xfeaffc00
[    0.992010] ehci_hcd 0000:02:01.2: USB 2.0 started, EHCI 0.95
[    0.992120] usb usb1: configuration #1 chosen from 1 choice
[    0.992164] hub 1-0:1.0: USB hub found
[    0.992177] hub 1-0:1.0: 5 ports detected
[    0.992256] ehci_hcd 0000:03:08.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    0.992273] ehci_hcd 0000:03:08.2: EHCI Host Controller
[    0.992327] ehci_hcd 0000:03:08.2: new USB bus registered, assigned bus number 2
[    1.016028] ehci_hcd 0000:03:08.2: irq 23, io mem 0xfe9ffc00
[    1.028009] ehci_hcd 0000:03:08.2: USB 2.0 started, EHCI 0.95
[    1.028096] usb usb2: configuration #1 chosen from 1 choice
[    1.028134] hub 2-0:1.0: USB hub found
[    1.028144] hub 2-0:1.0: 5 ports detected
[    1.028223] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.028253]   alloc irq_desc for 19 on node -1
[    1.028257]   alloc kstat_irqs on node -1
[    1.028266] ohci_hcd 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.028278] ohci_hcd 0000:02:01.0: OHCI Host Controller
[    1.028328] ohci_hcd 0000:02:01.0: new USB bus registered, assigned bus number 3
[    1.028357] ohci_hcd 0000:02:01.0: irq 19, io mem 0xfeafd000
[    1.084100] usb usb3: configuration #1 chosen from 1 choice
[    1.084138] hub 3-0:1.0: USB hub found
[    1.084152] hub 3-0:1.0: 3 ports detected
[    1.084218]   alloc irq_desc for 18 on node -1
[    1.084222]   alloc kstat_irqs on node -1
[    1.084228] ohci_hcd 0000:02:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.084240] ohci_hcd 0000:02:01.1: OHCI Host Controller
[    1.084283] ohci_hcd 0000:02:01.1: new USB bus registered, assigned bus number 4
[    1.084307] ohci_hcd 0000:02:01.1: irq 18, io mem 0xfeafe000
[    1.116547] ata2.00: ATAPI: ATAPI   iHAP322   8, UL14, max UDMA/66
[    1.116938] ata1.00: ATA-6: ST320014A, 3.07, max UDMA/100
[    1.116942] ata1.00: 39102336 sectors, multi 16: LBA 
[    1.132302] ata2.00: configured for UDMA/66
[    1.140109] usb usb4: configuration #1 chosen from 1 choice
[    1.140150] hub 4-0:1.0: USB hub found
[    1.140162] hub 4-0:1.0: 2 ports detected
[    1.140236]   alloc irq_desc for 21 on node -1
[    1.140239]   alloc kstat_irqs on node -1
[    1.140247] ohci_hcd 0000:03:08.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.140262] ohci_hcd 0000:03:08.0: OHCI Host Controller
[    1.140310] ohci_hcd 0000:03:08.0: new USB bus registered, assigned bus number 5
[    1.140338] ohci_hcd 0000:03:08.0: irq 21, io mem 0xfe9fd000
[    1.164380] ata1.00: configured for UDMA/100
[    1.164523] scsi 0:0:0:0: Direct-Access     ATA      ST320014A        3.07 PQ: 0 ANSI: 5
[    1.164697] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.164750] sd 0:0:0:0: [sda] 39102336 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    1.164816] sd 0:0:0:0: [sda] Write Protect is off
[    1.164820] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.164853] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.165027]  sda:
[    1.166351] scsi 1:0:0:0: CD-ROM            ATAPI    iHAP322   8      UL14 PQ: 0 ANSI: 5
[    1.171276]  sda1 sda2 <sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.172318] Uniform CD-ROM driver Revision: 3.20
[    1.172442] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.172515] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.702005]  sda5 >
[    1.702350] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.702465] usb usb5: configuration #1 chosen from 1 choice
[    1.702508] hub 5-0:1.0: USB hub found
[    1.702522] hub 5-0:1.0: 3 ports detected
[    1.702609]   alloc irq_desc for 22 on node -1
[    1.702613]   alloc kstat_irqs on node -1
[    1.702623] ohci_hcd 0000:03:08.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.702644] ohci_hcd 0000:03:08.1: OHCI Host Controller
[    1.702696] ohci_hcd 0000:03:08.1: new USB bus registered, assigned bus number 6
[    1.702729] ohci_hcd 0000:03:08.1: irq 22, io mem 0xfe9fe000
[    2.262117] usb usb6: configuration #1 chosen from 1 choice
[    2.262162] hub 6-0:1.0: USB hub found
[    2.262175] hub 6-0:1.0: 2 ports detected
[    2.262242] uhci_hcd: USB Universal Host Controller Interface driver
[    2.262315] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.262325] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    2.262329] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    2.262379] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 7
[    2.262405] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000ef80
[    2.262508] usb usb7: configuration #1 chosen from 1 choice
[    2.262545] hub 7-0:1.0: USB hub found
[    2.262555] hub 7-0:1.0: 2 ports detected
[    2.262683] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.265607] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.265616] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.265701] mice: PS/2 mouse device common for all mice
[    2.265824] rtc_cmos 00:02: RTC can wake from S4
[    2.265871] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.265894] rtc0: alarms up to one month, 114 bytes nvram
[    2.266044] device-mapper: uevent: version 1.0.3
[    2.266171] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.266271] device-mapper: multipath: version 1.1.0 loaded
[    2.266275] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.266439] EISA: Probing bus 0 at eisa.0
[    2.266477] EISA: Detected 0 cards.
[    2.266534] cpuidle: using governor ladder
[    2.266537] cpuidle: using governor menu
[    2.267241] TCP cubic registered
[    2.267415] NET: Registered protocol family 10
[    2.267995] lo: Disabled Privacy Extensions
[    2.268417] NET: Registered protocol family 17
[    2.268445] Bluetooth: L2CAP ver 2.13
[    2.268447] Bluetooth: L2CAP socket layer initialized
[    2.268451] Bluetooth: SCO (Voice Link) ver 0.6
[    2.268452] Bluetooth: SCO socket layer initialized
[    2.268512] Bluetooth: RFCOMM TTY layer initialized
[    2.268516] Bluetooth: RFCOMM socket layer initialized
[    2.268519] Bluetooth: RFCOMM ver 1.11
[    2.268563] Using IPI No-Shortcut mode
[    2.268665] PM: Resume from disk failed.
[    2.268682] registered taskstats version 1
[    2.268839]   Magic number: 14:193:404
[    2.268940] rtc_cmos 00:02: setting system clock to 2010-02-26 23:21:54 UTC (1267226514)
[    2.268944] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.268946] EDD information not available.
[    2.269022] Freeing unused kernel memory: 540k freed
[    2.269749] Write protecting the kernel text: 4568k
[    2.269788] Write protecting the kernel read-only data: 1836k
[    2.300222] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.440539] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    2.442494] ramzswap: disk size set to 127268 kB
[    2.539097] Linux agpgart interface v0.103
[    2.543498] agpgart-intel 0000:00:00.0: Intel i850 Chipset
[    2.593189] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    2.593574] usb 2-2: configuration #1 chosen from 1 choice
[    2.597829] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    2.597835] Copyright (c) 1999-2006 Intel Corporation.
[    2.597900] e1000 0000:02:0b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.858921] e1000: 0000:02:0b.0: e1000_probe: (PCI:33MHz:32-bit) 00:07:e9:0b:63:f1
[    2.919363] Adding 127264k swap on /dev/ramzswap0.  Priority:100 extents:1 across:127264k SSD
[    2.990987] ohci1394 0000:03:0c.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.018083] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.044057] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fe9ff000-fe9ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.952380] xor: automatically using best checksumming function: pIII_sse
[    3.972007]    pIII_sse  :  3201.000 MB/sec
[    3.972011] xor: using function: pIII_sse (3201.000 MB/sec)
[    3.976485] device-mapper: dm-raid45: initialized v0.2594b
[    4.316199] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[640050c5c00048ff]
[    4.874221] PM: Starting manual resume from disk
[    4.874228] PM: Resume from partition 8:5
[    4.874230] PM: Checking hibernation image.
[    4.874475] PM: Resume from disk failed.
[    4.938917] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    4.938925] EXT4-fs (sda1): write access will be enabled during recovery
[    4.943258] EXT4-fs (sda1): barriers enabled
[    6.164558] kjournald2 starting: pid 391, dev sda1:8, commit interval 5 seconds
[    6.164586] EXT4-fs (sda1): delayed allocation enabled
[    6.164591] EXT4-fs: file extents enabled
[    6.165977] EXT4-fs: mballoc enabled
[    6.165998] EXT4-fs (sda1): orphan cleanup on readonly fs
[    6.166008] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 523284
[    6.166054] EXT4-fs (sda1): 1 orphan inode deleted
[    6.166059] EXT4-fs (sda1): recovery complete
[    6.225225] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   22.849917] Adding 859436k swap on /dev/sda5.  Priority:-1 extents:1 across:859436k 
[   23.195450] udev: starting version 147
[   23.434552] EXT4-fs (sda1): internal journal on sda1:8
[   23.789403] lp: driver loaded but no devices found
[   23.804590] parport_pc 00:09: reported by Plug and Play ACPI
[   23.804618] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   23.900975] ppdev: user-space parallel port driver
[   23.904281] lp0: using parport0 (interrupt-driven).
[   23.917962] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.019180] intel_rng: Firmware space is locked read-only. If you can't or
[   24.019182] intel_rng: don't want to disable this in firmware setup, and if
[   24.019184] intel_rng: you are certain that your system has a functional
[   24.019186] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   24.154985] psmouse serio1: ID: 10 00 64
[   24.638389] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   24.876946] nvidia: module license 'NVIDIA' taints kernel.
[   24.876953] Disabling lock debugging due to kernel taint
[   25.170375] gameport: EMU10K1 is pci0000:02:0a.1/gameport0, io 0xdff0, speed 1065kHz
[   25.171572] cfg80211: Calling CRDA to update world regulatory domain
[   25.190268]   alloc irq_desc for 16 on node -1
[   25.190274]   alloc kstat_irqs on node -1
[   25.190286] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.190640] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu Jun 25 18:42:21 PDT 2009
[   25.638807] cfg80211: World regulatory domain updated:
[   25.638813]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.638817]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.638821]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.638825]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.638828]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.638832]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.676031] usb 2-2: reset high speed USB device using ehci_hcd and address 2
[   25.840113] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.638198] phy0: Selected rate control algorithm 'minstrel'
[   26.639072] zd1211rw 2-2:1.0: phy0
[   26.639105] usbcore: registered new interface driver zd1211rw
[   26.894147] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.899105] usb 2-2: firmware: requesting zd1211/zd1211b_ub
[   27.341153] usb 2-2: firmware: requesting zd1211/zd1211b_uphr
[   27.495887] zd1211rw 2-2:1.0: firmware version 4725
[   27.543610] zd1211rw 2-2:1.0: zd1211b chip 083a:4505 v4810 high 00-22-2d AL2230_RF pa0 g--NS
[   27.546741] cfg80211: Calling CRDA for country: US
[   27.550098] cfg80211: Regulatory domain changed to country: US
[   27.550104]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.550109]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   27.550113]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   27.550116]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.550120]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.550124]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   27.573099] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.604164] EMU10K1_Audigy 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   30.108181] type=1505 audit(1267244542.339:2): operation="profile_load" pid=1060 name=/usr/share/gdm/guest-session/Xsession
[   30.122820] type=1505 audit(1267244542.351:3): operation="profile_load" pid=1064 name=/sbin/dhclient3
[   30.123480] type=1505 audit(1267244542.351:4): operation="profile_load" pid=1064 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   30.123840] type=1505 audit(1267244542.351:5): operation="profile_load" pid=1064 name=/usr/lib/connman/scripts/dhclient-script
[   30.158639] type=1505 audit(1267244542.387:6): operation="profile_load" pid=1065 name=/usr/bin/evince
[   30.184740] type=1505 audit(1267244542.415:7): operation="profile_load" pid=1065 name=/usr/bin/evince-previewer
[   30.203354] type=1505 audit(1267244542.431:8): operation="profile_load" pid=1065 name=/usr/bin/evince-thumbnailer
[   30.227938] type=1505 audit(1267244542.455:9): operation="profile_load" pid=1067 name=/usr/bin/freshclam
[   30.238404] type=1505 audit(1267244542.467:10): operation="profile_load" pid=1068 name=/usr/lib/cups/backend/cups-pdf
[   30.239191] type=1505 audit(1267244542.467:11): operation="profile_load" pid=1068 name=/usr/sbin/cupsd
[   33.383325] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   33.383343] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   33.383365] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   44.504049] wlan0: authenticate with AP 00:24:2c:6d:8e:52
[   44.506188] wlan0: authenticated
[   44.506195] wlan0: associate with AP 00:24:2c:6d:8e:52
[   44.508307] wlan0: RX AssocResp from 00:24:2c:6d:8e:52 (capab=0x401 status=0 aid=2)
[   44.508314] wlan0: associated
[   44.520558] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   55.176020] wlan0: no IPv6 routers present
[37349.136035] usb 2-4: new high speed USB device using ehci_hcd and address 3
[37349.271734] usb 2-4: configuration #1 chosen from 1 choice
[37349.616271] Linux video capture interface: v2.00
[37349.792146] em28xx: New device USB 2863 Device @ 480 Mbps (eb1a:e303, interface 0, class 0)
[37349.792259] em28xx #0: chip ID is em2860
[37350.138234] em28xx #0: i2c eeprom 00: 1a eb 67 95 1a eb 03 e3 d0 00 5c 03 6a 22 00 00
[37350.138251] em28xx #0: i2c eeprom 10: 00 00 04 57 4e 03 01 00 00 00 00 00 00 00 00 00
[37350.138265] em28xx #0: i2c eeprom 20: 06 00 01 00 f0 10 01 00 00 00 00 00 5b 00 00 00
[37350.138278] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 00 00 00 00
[37350.138291] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[37350.138305] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[37350.138318] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 22 03 55 00 53 00
[37350.138331] em28xx #0: i2c eeprom 70: 42 00 20 00 32 00 38 00 36 00 33 00 20 00 44 00
[37350.138345] em28xx #0: i2c eeprom 80: 65 00 76 00 69 00 63 00 65 00 00 00 00 00 00 00
[37350.138358] em28xx #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[37350.138371] em28xx #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[37350.138384] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[37350.138397] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[37350.138411] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[37350.138424] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[37350.138437] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[37350.138452] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x9dca1441
[37350.138455] em28xx #0: EEPROM info:
[37350.138458] em28xx #0:    AC97 audio (5 sample rates)
[37350.138460] em28xx #0:    500mA max power
[37350.138464] em28xx #0:    Table at 0x04, strings=0x226a, 0x0000, 0x0000
[37350.139232] em28xx #0: Identified as Kaiomy TVnPC U2 (card=63)
[37350.169438] tvp5150 3-005c: chip found @ 0xb8 (em28xx #0)
[37350.221643] tuner 3-0000: chip found @ 0x0 (em28xx #0)
[37350.228067] tuner 3-0061: chip found @ 0xc2 (em28xx #0)
[37350.402031] tuner-simple 3-0000: unable to probe Alps TSBE1, proceeding anyway.
[37350.402038] tuner-simple 3-0000: creating new instance
[37350.402043] tuner-simple 3-0000: type set to 10 (Alps TSBE1)
[37350.468283] xc2028 3-0061: creating new instance
[37350.468289] xc2028 3-0061: type set to XCeive xc2028/xc3028 tuner
[37350.480064] usb 2-4: firmware: requesting xc3028-v27.fw
[37350.528703] xc2028 3-0061: Error: firmware xc3028-v27.fw not found.
[37350.528803] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1e.0/0000:02:0d.0/0000:03:08.2/usb2/2-4/input/input5
[37350.531689] em28xx #0: Config register raw data: 0xd0
[37350.556197] em28xx #0: AC97 vendor ID = 0xffffffff
[37350.568191] em28xx #0: AC97 features = 0x6a90
[37350.568194] em28xx #0: Empia 202 AC97 audio processor detected
[37351.096484] tvp5150 3-005c: tvp5150am1 detected.
[37353.312035] em28xx #0: v4l2 driver version 0.1.2
[37354.220222] em28xx #0: Registered radio device as /dev/radio0
[37354.220227] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[37354.248080] usbcore: registered new interface driver em28xx
[37354.248087] em28xx driver loaded
[37354.298896] em28xx-audio.c: probing for em28x1 non standard usbaudio
[37354.298900] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[37354.299361] Em28xx: Initialized (Em28xx Audio Extension) extension
[37354.604481] tvp5150 3-005c: tvp5150am1 detected.
[37357.260563] tvp5150 3-005c: tvp5150am1 detected.
[37360.304493] tvp5150 3-005c: tvp5150am1 detected.
corey@corey-desktop:~$

---

### Post by frontline2010 on 2010-02-27
I did further looking in the drivers on windows and found out that it is an eMPIA Technology 2863 device ...if that helps

---

### Post by tomba1977 on 2010-02-27
Can I get some help on this one too please?

My DVB-T USB stick - a Peak - comes up with the same info as frontline's in that it is an eMPIA device but mine also says:  Hauppauge WinTV PVR-150.

Will this work in ubuntu 9.10?

---

### Post by frontline2010 on 2010-02-27
I tested it by running tvtime but it says (NO SIGNAL) but the funny thing is that the S-Video and the Composite video when selected work perfect. I got cable “Comcast” running in to it and the setting should be right as with US standards.

---

### Post by Jose Catre-Vandis on 2010-02-28
> **tomba1977 said:**
> Can I get some help on this one too please?

My DVB-T USB stick - a Peak - comes up with the same info as frontline's in that it is an eMPIA device but mine also says:  Hauppauge WinTV PVR-150.

Will this work in ubuntu 9.10?

You need to install dvb-apps from the repos, and run the scan utility to grab a channels.conf for your receiver. Your local transmitter can be found in the dvb-t section. (Check where files are installed)

Place the channels .conf in your ~/.mplayer directory and then play tv with this command:```
mplayer dvb://
```

---

### Post by Jose Catre-Vandis on 2010-02-28
> **frontline2010 said:**
> I tested it by running tvtime but it says (NO SIGNAL) but the funny thing is that the S-Video and the Composite video when selected work perfect. I got cable “Comcast” running in to it and the setting should be right as with US standards.

Check out the tvtime site for any specific information regarding your locale and type of receiver. (also confirm it is an analog tv card and not dvb?)

---

### Post by tomba1977 on 2010-02-28
> **Jose Catre-Vandis said:**
> You need to install dvb-apps from the repos, and run the scan utility to grab a channels.conf for your receiver. Your local transmitter can be found in the dvb-t section. (Check where files are installed)

Place the channels .conf in your ~/.mplayer directory and then play tv with this command:```
mplayer dvb://
```


This is where I give up until I know much more about how to use the command line.

I'm no good with these tar.gz files. They simply confuse me. I downloaded it but have no idea how to make it spark into life.

Thanks for the help. I'll keep a note of it.

---

### Post by Jose Catre-Vandis on 2010-02-28
mplayer is in the repos

```
sudo apt-get install mplayer
```

or install via synaptic

---

