---
title: "Boot up message ? / system runs slow.. why?"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by bruce leroy on 2009-10-05
I'm getting this message upon booting:
 
Starting up ...
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
-missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/612c6d7e-82ee-4cd7-a505-206d7a585b28 does not exist. Dropping to a shell!

What does this mean?
When I type "exit", it boots up fine. but I notice that the system runs really slow. 20kb/s.. now that is slow. Then, audio sounds choppy.  is this the result of this error?
I updated my driver to NVIDIA 180 as recommended by the system.  Still the same results. slow, slow, slow.
 
system specs:
AMD Athlon 64, 3.2 ghz. 1.5 gig ram.
NVIDIA GeForce GPU.

---

### Post by sandyd on 2009-10-05
seems like hard disk faliure to me.

try running a livecd and see if you get the same results.

---

### Post by bruce leroy on 2009-10-05
This was from a live cd for Ubuntu Studio that i got fomr Linux Format magazine.

---

### Post by baltadt on 2009-10-05
if your running it from a live cd then it will be slow...it will only run as fast as your cd reader will let it.

---

### Post by lavinog on 2009-10-05
It could be that your live cd is corrupt. try using the check disk for defects option.

---

### Post by bruce leroy on 2009-10-05
I don't understan how running a live CD will slow down my pc speed.  Please elaborate.  I've already updated my NVIDIA driver and completed all system update.  Still slow.
This is the only OS running for this pc.

---

### Post by bruce leroy on 2009-10-05
just to add.  ubuntu studio doesn't come as a live cd.  it's a full install.

---

### Post by lavinog on 2009-10-05
> **bruce leroy said:**
> I don't understan how running a live CD will slow down my pc speed.  Please elaborate.  I've already updated my NVIDIA driver and completed all system update.  Still slow.
This is the only OS running for this pc.

Live cds can be run from cd instead of the hd.  Since cd's are slower than harddrives, the system will be slower.

for your problem:
can you post dmesg
open a terminal and type:
```
dmesg
```
and post the output here (using the code formatting please)

also you may want to post the output of fstab
```
cat /etc/fstab
```

---

### Post by bruce leroy on 2009-10-06
[    7.624398] pci 0000:00:10.1: PME# disabled
[    7.624670] PCI: 0000:00:14.0 reg 10 32bit mmio: [feadc000, feadcfff]
[    7.624780] PCI: 0000:00:14.0 reg 14 io port: [cc00, cc07]
[    7.625095] pci 0000:00:14.0: supports D1
[    7.625155] pci 0000:00:14.0: supports D2
[    7.625225] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    7.625319] pci 0000:00:14.0: PME# disabled
[    7.627918] PCI: 0000:04:07.0 reg 10 32bit mmio: [febf0000, febfffff]
[    7.628076] PCI: 0000:04:07.0 reg 14 io port: [ec00, ec07]
[    7.628406] pci 0000:04:07.0: PME# supported from D3hot D3cold
[    7.628494] pci 0000:04:07.0: PME# disabled
[    7.628742] pci 0000:00:10.0: transparent bridge
[    7.628824] PCI: bridge 0000:00:10.0 io port: [e000, efff]
[    7.628913] PCI: bridge 0000:00:10.0 32bit mmio: [feb00000, febfffff]
[    7.629109] bus 00 -> node 0
[    7.629210] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    7.639374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    7.643903] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    7.648471] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[    7.653450] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    8.129683] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    8.139443] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *5
[    8.149232] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    8.159003] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    8.168809] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    8.178575] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    8.188706] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *10
[    8.198473] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    8.208296] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    8.218075] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *5
[    8.227955] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    8.237766] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *5
[    8.247552] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    8.257687] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    8.267477] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
[    8.277299] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *5
[    8.287088] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[    8.296923] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[    8.308594] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    8.312474] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - A6, should be A2 [20080609]
[    8.312666] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.313304] pnp: PnP ACPI init
[    8.313473] ACPI: bus type pnp registered
[    8.515534] pnp: PnP ACPI: found 12 devices
[    8.515596] ACPI: ACPI bus type pnp unregistered
[    8.515666] PnPBIOS: Disabled by ACPI PNP
[    8.521260] PCI: Using ACPI for IRQ routing
[    8.523454] NET: Registered protocol family 8
[    8.524064] NET: Registered protocol family 20
[    8.524650] NetLabel: Initializing
[    8.524707] NetLabel:  domain hash size = 128
[    8.524769] NetLabel:  protocols = UNLABELED CIPSOv4
[    8.525027] NetLabel:  unlabeled traffic allowed by default
[    8.541872] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    8.541955]    actual entries 65620
[    8.542948] AppArmor: AppArmor Filesystem Enabled
[    8.543111] ACPI: RTC can wake from S4
[    8.543223] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    8.543223] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    8.544078] system 00:07: ioport range 0x800-0x80f has been reserved
[    8.544178] system 00:07: ioport range 0x4000-0x407f has been reserved
[    8.544280] system 00:07: ioport range 0x4080-0x40ff has been reserved
[    8.544382] system 00:07: ioport range 0x4400-0x447f has been reserved
[    8.544487] system 00:07: ioport range 0x4480-0x44ff has been reserved
[    8.544589] system 00:07: ioport range 0x4800-0x487f has been reserved
[    8.544692] system 00:07: ioport range 0x4880-0x48ff has been reserved
[    8.544795] system 00:07: ioport range 0x2000-0x207f has been reserved
[    8.544897] system 00:07: ioport range 0x2080-0x20ff has been reserved
[    8.545004] system 00:07: iomem range 0xfea80000-0xfeabffff has been reserved
[    8.545111] system 00:07: iomem range 0xfee01000-0xfeefffff could not be reserved
[    8.545295] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    8.545405] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[    8.545516] system 00:08: iomem range 0xff380000-0xff3fffff has been reserved
[    8.545696] system 00:09: ioport range 0xa00-0xa0f has been reserved
[    8.545793] system 00:09: ioport range 0xa10-0xa1f has been reserved
[    8.545967] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    8.546155] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    8.546256] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    8.546359] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    8.546462] system 00:0b: iomem range 0x100000-0x5fffffff could not be reserved
[    8.546575] system 00:0b: iomem range 0xff780000-0xffffffff could not be reserved
[    8.591283] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    8.591360] pci 0000:00:02.0:   IO window: disabled
[    8.591445] pci 0000:00:02.0:   MEM window: disabled
[    8.591525] pci 0000:00:02.0:   PREFETCH window: disabled
[    8.591625] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    8.591702] pci 0000:00:03.0:   IO window: disabled
[    8.591786] pci 0000:00:03.0:   MEM window: disabled
[    8.591866] pci 0000:00:03.0:   PREFETCH window: disabled
[    8.591965] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
[    8.592111] Switched to high resolution mode on CPU 0
[    8.592188] pci 0000:00:04.0:   IO window: disabled
[    8.592272] pci 0000:00:04.0:   MEM window: disabled
[    8.592352] pci 0000:00:04.0:   PREFETCH window: disabled
[    8.592453] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    8.592541] pci 0000:00:10.0:   IO window: 0xe000-0xefff
[    8.592635] pci 0000:00:10.0:   MEM window: 0xfeb00000-0xfebfffff
[    8.592725] pci 0000:00:10.0:   PREFETCH window: disabled
[    8.592872] pci 0000:00:02.0: setting latency timer to 64
[    8.592995] pci 0000:00:03.0: setting latency timer to 64
[    8.593119] pci 0000:00:04.0: setting latency timer to 64
[    8.593233] pci 0000:00:10.0: setting latency timer to 64
[    8.593318] bus: 00 index 0 io port: [0, ffff]
[    8.593389] bus: 00 index 1 mmio: [0, ffffffff]
[    8.593464] bus: 01 index 0 mmio: [0, 0]
[    8.593529] bus: 01 index 1 mmio: [0, 0]
[    8.593594] bus: 01 index 2 mmio: [0, 0]
[    8.593659] bus: 01 index 3 mmio: [0, 0]
[    8.593726] bus: 02 index 0 mmio: [0, 0]
[    8.593791] bus: 02 index 1 mmio: [0, 0]
[    8.593856] bus: 02 index 2 mmio: [0, 0]
[    8.593924] bus: 02 index 3 mmio: [0, 0]
[    8.593990] bus: 03 index 0 mmio: [0, 0]
[    8.594055] bus: 03 index 1 mmio: [0, 0]
[    8.594120] bus: 03 index 2 mmio: [0, 0]
[    8.594185] bus: 03 index 3 mmio: [0, 0]
[    8.594254] bus: 04 index 0 io port: [e000, efff]
[    8.594328] bus: 04 index 1 mmio: [feb00000, febfffff]
[    8.594402] bus: 04 index 2 mmio: [0, 0]
[    8.594472] bus: 04 index 3 io port: [0, ffff]
[    8.594542] bus: 04 index 4 mmio: [0, ffffffff]
[    8.594685] NET: Registered protocol family 2
[    8.597825] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.604817] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.623536] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.630704] TCP: Hash tables configured (established 131072 bind 65536)
[    8.630785] TCP reno registered
[    8.632386] NET: Registered protocol family 1
[    8.634315] checking if image is initramfs... it is
[   22.017937] Freeing initrd memory: 8114k freed
[   22.028273] audit: initializing netlink socket (disabled)
[   22.028401] type=2000 audit(1254750713.028:1): initialized
[   22.224176] highmem bounce pool size: 64 pages
[   22.224302] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[   22.283853] VFS: Disk quotas dquot_6.5.1
[   22.286247] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.288302] msgmni has been set to 1754
[   22.291237] io scheduler noop registered
[   22.291301] io scheduler anticipatory registered
[   22.291376] io scheduler deadline registered
[   22.291782] io scheduler cfq registered (default)
[   22.291995] pci 0000:00:00.0: Enabling HT MSI Mapping
[   22.292862] pci 0000:00:02.0: Enabling HT MSI Mapping
[   22.293083] pci 0000:00:03.0: Enabling HT MSI Mapping
[   22.293303] pci 0000:00:04.0: Enabling HT MSI Mapping
[   22.293516] pci 0000:00:05.0: Boot video device
[   22.293698] pci 0000:00:09.0: Enabling HT MSI Mapping
[   22.732503] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   22.732695] pci 0000:00:10.0: Enabling HT MSI Mapping
[   22.732903] pci 0000:00:10.1: Enabling HT MSI Mapping
[   22.735429] pcieport-driver 0000:00:02.0: setting latency timer to 64
[   22.735814] pcieport-driver 0000:00:02.0: found MSI capability
[   22.736180] pci_express 0000:00:02.0:pcie00: allocate port service
[   22.736851] pci_express 0000:00:02.0:pcie03: allocate port service
[   22.737962] pcieport-driver 0000:00:03.0: setting latency timer to 64
[   22.738346] pcieport-driver 0000:00:03.0: found MSI capability
[   22.738648] pci_express 0000:00:03.0:pcie00: allocate port service
[   22.739316] pci_express 0000:00:03.0:pcie03: allocate port service
[   22.740501] pcieport-driver 0000:00:04.0: setting latency timer to 64
[   22.740885] pcieport-driver 0000:00:04.0: found MSI capability
[   22.741190] pci_express 0000:00:04.0:pcie00: allocate port service
[   22.741864] pci_express 0000:00:04.0:pcie03: allocate port service
[   22.747059] isapnp: Scanning for PnP cards...
[   23.103021] isapnp: No Plug & Play device found
[   23.862348] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[   23.903014] brd: module loaded
[   23.904651] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.907483] PNP: No PS/2 controller found. Probing ports directly.
[   23.911880] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.911977] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.917500] mice: PS/2 mouse device common for all mice
[   23.919784] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[   23.919950] rtc0: alarms up to one year, y3k
[   23.922151] EISA: Probing bus 0 at eisa.0
[   23.922259] Cannot allocate resource for EISA slot 2
[   23.922365] Cannot allocate resource for EISA slot 4
[   23.922446] Cannot allocate resource for EISA slot 5
[   23.922525] Cannot allocate resource for EISA slot 6
[   23.922659] EISA: Detected 0 cards.
[   23.922718] cpuidle: using governor ladder
[   23.922782] cpuidle: using governor menu
[   23.939395] TCP cubic registered
[   23.939785] Using IPI No-Shortcut mode
[   23.943130] registered taskstats version 1
[   23.946122]   Magic number: 13:117:887
[   23.946624] tty ptyue: hash matches
[   23.947122] rtc_cmos 00:02: setting system clock to 2009-10-05 13:51:57 UTC (1254750717)
[   23.947223] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.947297] EDD information not available.
[   23.949549] Freeing unused kernel memory: 428k freed
[   23.952149] Write protecting the kernel text: 2588k
[   23.953494] Write protecting the kernel read-only data: 940k
[   28.054056] fuse init (API version 7.9)
[   28.944285] processor ACPI0007:00: registered as cooling_device0
[   60.387322] usbcore: registered new interface driver usbfs
[   60.387692] usbcore: registered new interface driver hub
[   60.400412] usbcore: registered new device driver usb
[   60.712578] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   60.725213] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[   60.725324] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[   60.725438] forcedeth 0000:00:14.0: setting latency timer to 64
[   60.748116] nv_probe: set workaround bit for reversed mac addr
[   60.985223] No dock devices found.
[   61.169266] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   61.924847] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:17:1e:4c:3f
[   61.924964] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[   61.938199] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[   61.938312] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[   61.938451] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[   61.938534] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   61.939369] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   61.939717] ehci_hcd 0000:00:0b.1: debug port 1
[   61.939807] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[   61.940005] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xfeadfc00
[   61.952141] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   61.953984] usb usb1: configuration #1 chosen from 1 choice
[   61.954666] hub 1-0:1.0: USB hub found
[   61.954787] hub 1-0:1.0: 8 ports detected
[   62.121382] SCSI subsystem initialized
[   62.176357] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[   62.176470] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
[   62.176608] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[   62.176691] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   62.177202] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   62.177434] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xfeade000
[   62.275532] usb usb2: configuration #1 chosen from 1 choice
[   62.276434] hub 2-0:1.0: USB hub found
[   62.276554] hub 2-0:1.0: 8 ports detected
[   63.144483] libata version 3.00 loaded.
[   63.540157] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   63.649968] pata_acpi 0000:00:0d.0: setting latency timer to 64
[   63.663027] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
[   63.663137] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[   63.688342] pata_acpi 0000:00:0e.0: setting latency timer to 64
[   63.688544] pata_acpi 0000:00:0e.0: PCI INT A disabled
[   63.754400] usb 2-1: configuration #1 chosen from 1 choice
[   64.269646] sata_nv 0000:00:0e.0: version 3.5
[   64.269775] sata_nv 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[   64.269875] sata_nv 0000:00:0e.0: Using SWNCQ mode
[   64.270218] sata_nv 0000:00:0e.0: setting latency timer to 64
[   64.279989] scsi0 : sata_nv
[   64.281585] scsi1 : sata_nv
[   64.287073] ata1: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 20
[   64.287168] ata2: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 20
[   64.324165] usb 2-2: new full speed USB device using ohci_hcd and address 3
[   64.526299] usb 2-2: configuration #1 chosen from 1 choice
[   64.528647] hub 2-2:1.0: USB hub found
[   64.536169] hub 2-2:1.0: 4 ports detected
[   65.032488] ata1: SATA link down (SStatus 0 SControl 300)
[   65.089353] usb 2-7: new full speed USB device using ohci_hcd and address 4
[   65.322640] usb 2-7: configuration #1 chosen from 1 choice
[   65.412156] usb 2-2.1: new low speed USB device using ohci_hcd and address 5
[   65.552441] usb 2-2.1: configuration #1 chosen from 1 choice
[   65.652155] usb 2-2.2: new low speed USB device using ohci_hcd and address 6
[   65.772599] ata2: SATA link down (SStatus 0 SControl 300)
[   65.777385] pata_amd 0000:00:0d.0: version 0.3.10
[   65.777712] pata_amd 0000:00:0d.0: setting latency timer to 64
[   65.784281] scsi2 : pata_amd
[   65.785503] scsi3 : pata_amd
[   65.835553] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   65.835644] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   65.846427] usb 2-2.2: configuration #1 chosen from 1 choice
[   65.926554] usb 2-2.3: new low speed USB device using ohci_hcd and address 7
[   66.002750] ata3.00: ATA-6: WDC WD1600BB-22GUC0, 08.02D08, max UDMA/100
[   66.002844] ata3.00: 312581808 sectors, multi 16: LBA48 
[   66.003170] ata3: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc600c500) ACPI=0x3f01f (20:900:0x11)
[   66.020337] ata3.00: configured for UDMA/100
[   66.057802] usb 2-2.3: configuration #1 chosen from 1 choice
[   66.200725] ata4.00: ATAPI: LITE-ON DVDRW SHW-1635S, YGS4, max UDMA/66
[   66.201055] ata4: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc600c500) ACPI=0x1f01f (30:900:0x11)
[   66.232850] ata4.00: configured for UDMA/66
[   66.233765] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BB-22G 08.0 PQ: 0 ANSI: 5
[   66.236915] scsi 3:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-1635S  YGS4 PQ: 0 ANSI: 5
[   74.718700] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[   74.719627] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   75.773858] usbcore: registered new interface driver libusual
[   76.125202] Initializing USB Mass Storage driver...
[   76.306453] scsi4 : SCSI emulation for USB Mass Storage devices
[   76.317841] usbcore: registered new interface driver usb-storage
[   76.317943] USB Mass Storage support registered.
[   76.318031] usb-storage: device found at 4
[   76.318094] usb-storage: waiting for device to settle before scanning
[   76.598507] usbcore: registered new interface driver hiddev
[   76.686006] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input1
[   76.700878] input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.0-2.1
[   76.722457] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.2/2-2.2:1.0/input/input2
[   76.883090] input,hidraw1: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-2.2
[   76.897592] input: No brand SP02-A1 as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input3
[   76.921831] input,hidraw2: USB HID v1.10 Keyboard [No brand SP02-A1] on usb-0000:00:0b.0-2.3
[   76.926105] Driver 'sd' needs updating - please use bus_type methods
[   76.927332] /build/buildd/linux-2.6.27/drivers/hid/usbhid/hid-core.c: couldn't find an input interrupt endpoint
[   76.928130] usbcore: registered new interface driver usbhid
[   76.928226] usbhid: v2.6:USB HID core driver
[   76.928817] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   76.929100] sd 2:0:0:0: [sda] Write Protect is off
[   76.929176] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   76.929630] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   76.930664] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   76.930948] sd 2:0:0:0: [sda] Write Protect is off
[   76.931024] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   76.931482] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   76.931591]  sda: sda1 sda2 < sda5 >
[   77.077992] sd 2:0:0:0: [sda] Attached SCSI disk
[   77.132152] Driver 'sr' needs updating - please use bus_type methods
[   77.138934] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   77.139018] Uniform CD-ROM driver Revision: 3.20
[   77.140728] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   81.318068] usb-storage: device scan complete
[   81.325045] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   81.332154] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   81.339097] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   81.346101] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   81.370529] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   81.371869] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   81.384533] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   81.385868] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   81.398570] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   81.399844] sd 4:0:0:2: Attached scsi generic sg4 type 0
[   81.412766] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   81.414046] sd 4:0:0:3: Attached scsi generic sg5 type 0
[  111.906068] PM: Starting manual resume from disk
[  111.906137] PM: Resume from partition 8:5
[  111.906196] PM: Checking hibernation image.
[  111.906645] PM: Resume from disk failed.
[  112.662179] kjournald starting.  Commit interval 5 seconds
[  112.662325] EXT3-fs: mounted filesystem with ordered data mode.
[  124.711479] udevd version 124 started
[  160.701724] Linux agpgart interface v0.103
[  162.529669] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  163.902025] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  166.600139] nvidia: module license 'NVIDIA' taints kernel.
[  174.549169] ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 19
[  174.549279] nvidia 0000:00:05.0: PCI INT A -> Link[LNEC] -> GSI 19 (level, low) -> IRQ 19
[  174.549395] nvidia 0000:00:05.0: setting latency timer to 64
[  174.803214] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008
[  180.348423] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[  180.364121] ACPI: Power Button (FF) [PWRF]
[  180.366018] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[  180.376120] ACPI: Power Button (CM) [PWRB]
[  209.386882] parport_pc 00:05: reported by Plug and Play ACPI
[  209.387021] parport0: PC-style at 0x378, irq 7 [PCSPP]
[  239.754054]  : Error requesting region 5000 .. 503F for SMB1
[  239.754292] nForce2_smbus 0000:00:0a.1: Error probing SMB1.
[  239.755182] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x6000
[  255.824244] input: PC Speaker as /devices/platform/pcspkr/input/input6
[  295.703912] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x7D04
[  295.704465] usbcore: registered new interface driver usblp
[  330.696195] loop: module loaded
[  333.288825] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[  333.288923] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[  333.289198] HDA Intel 0000:00:10.1: setting latency timer to 64
[  333.434726] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[  338.798463] lp0: using parport0 (interrupt-driven).
[  341.237247] Adding 4168828k swap on /dev/sda5.  Priority:-1 extents:1 across:4168828k
[  342.945169] EXT3 FS on sda1, internal journal
[  346.729306] type=1505 audit(1254751040.075:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4451
[  352.707627] type=1505 audit(1254751046.051:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4456
[  352.711013] type=1505 audit(1254751046.055:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4456
[  354.178092] ip_tables: (C) 2000-2006 Netfilter Core Team
[  357.634726] NET: Registered protocol family 17
[  365.064774] NET: Registered protocol family 10
[  365.140185] lo: Disabled Privacy Extensions
[  371.396482] ACPI: WMI: Mapper loaded
[  375.592071] eth0: no IPv6 routers present
[  378.156610] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[  378.162626] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[  388.712135] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  389.673372] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  389.673468] apm: overridden by ACPI.
[  390.958819] ppdev: user-space parallel port driver
[  411.975377] Bluetooth: Core ver 2.13
[  411.988667] NET: Registered protocol family 31
[  411.988751] Bluetooth: HCI device and connection manager initialized
[  411.988835] Bluetooth: HCI socket layer initialized
[  414.227270] Bluetooth: L2CAP ver 2.11
[  414.227345] Bluetooth: L2CAP socket layer initialized
[  414.960229] Bluetooth: RFCOMM socket layer initialized
[  414.963767] Bluetooth: RFCOMM TTY layer initialized
[  414.963851] Bluetooth: RFCOMM ver 1.10
[  416.629404] Bluetooth: SCO (Voice Link) ver 0.6
[  416.629485] Bluetooth: SCO socket layer initialized
[  419.448511] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  419.448597] Bluetooth: BNEP filters: protocol multicast
[  423.438093] Bridge firewalling registered
[  666.796147] ppdev0: registered pardevice
[  666.853188] ppdev0: unregistered pardevice
[  674.152595] ppdev0: registered pardevice
[  674.208579] ppdev0: unregistered pardevice
[  674.571369] ppdev0: registered pardevice
[  674.624153] ppdev0: unregistered pardevice
[ 1675.549500] ppdev0: registered pardevice
[ 1675.607294] ppdev0: unregistered pardevice
[ 1690.811630] ppdev0: registered pardevice
[ 1690.882583] ppdev0: unregistered pardevice
[ 1691.633091] ppdev0: registered pardevice
[ 1691.680153] ppdev0: unregistered pardevice
[14811.488193] usb 2-2: USB disconnect, address 3
[14811.488285] usb 2-2.1: USB disconnect, address 5
[14811.611420] usb 2-2.2: USB disconnect, address 6
[14811.691685] usb 2-2.3: USB disconnect, address 7
[15345.984184] usb 2-2: new full speed USB device using ohci_hcd and address 8
[15346.244232] usb 2-2: configuration #1 chosen from 1 choice
[15346.271695] hub 2-2:1.0: USB hub found
[15346.275773] hub 2-2:1.0: 4 ports detected
[15346.638030] usb 2-2.1: new low speed USB device using ohci_hcd and address 9
[15346.801947] usb 2-2.1: configuration #1 chosen from 1 choice
[15346.856399] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input7
[15346.913763] input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.0-2.1
[15346.998043] usb 2-2.2: new low speed USB device using ohci_hcd and address 10
[15347.132173] usb 2-2.2: configuration #1 chosen from 1 choice
[15347.162228] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.2/2-2.2:1.0/input/input8
[15347.211508] input,hidraw1: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-2.2
[15347.298032] usb 2-2.3: new low speed USB device using ohci_hcd and address 11
[15347.444175] usb 2-2.3: configuration #1 chosen from 1 choice
[15347.472248] input: No brand SP02-A1 as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input9
[15347.498030] input,hidraw2: USB HID v1.10 Keyboard [No brand SP02-A1] on usb-0000:00:0b.0-2.3
[15347.514707] /build/buildd/linux-2.6.27/drivers/hid/usbhid/hid-core.c: couldn't find an input interrupt endpoint
[16545.243833] usblp0: removed
[16575.102326] type=1503 audit(1254767265.670:5): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=7150 profile="/usr/sbin/cupsd"
[17516.624225] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[18567.165716] UDF-fs: Partition marked readonly; forcing readonly mount
[18567.213237] UDF-fs INFO UDF: Mounting volume 'STYLE_WARS_DISC_1', timestamp 2003/02/14 02:35 (1e5c)
[40627.786298] usb 2-2: USB disconnect, address 8
[40627.786388] usb 2-2.1: USB disconnect, address 9
[40627.998099] usb 2-2.2: USB disconnect, address 10
[40628.068326] usb 2-2.3: USB disconnect, address 11
[41974.168218] usb 2-2: new full speed USB device using ohci_hcd and address 12
[41974.440165] usb 2-2: configuration #1 chosen from 1 choice
[41974.468163] hub 2-2:1.0: USB hub found
[41974.471284] hub 2-2:1.0: 4 ports detected
[41974.821851] usb 2-2.1: new low speed USB device using ohci_hcd and address 13
[41974.982737] usb 2-2.1: configuration #1 chosen from 1 choice
[41975.037492] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input10
[41975.101856] input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.0-2.1
[41975.194910] usb 2-2.2: new low speed USB device using ohci_hcd and address 14
[41975.328178] usb 2-2.2: configuration #1 chosen from 1 choice
[41975.371832] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.2/2-2.2:1.0/input/input11
[41975.423472] input,hidraw1: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-2.2
[41975.509851] usb 2-2.3: new low speed USB device using ohci_hcd and address 15
[41975.648180] usb 2-2.3: configuration #1 chosen from 1 choice
[41975.678970] input: No brand SP02-A1 as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input12
[41975.738106] input,hidraw2: USB HID v1.10 Keyboard [No brand SP02-A1] on usb-0000:00:0b.0-2.3
[41975.755240] /build/buildd/linux-2.6.27/drivers/hid/usbhid/hid-core.c: couldn't find an input interrupt endpoint


from fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ad39be8a-618c-463c-9508-69f9ffd4ba96 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d8c95192-c6fa-45dc-9baf-8868cafc85ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by lavinog on 2009-10-06
Is there something attached to your parallel port?

can you post /boot/grub/menu.lst

---

### Post by wdzieczny on 2009-10-06
Check the MD5 Sum before you install that. I honestly believe that is a corrupt copy. Just download a new one and burn it (as slow as possible) it won't kill you I promise.

---

### Post by lavinog on 2009-10-06
I agree with starcannons reply in your other thread:[http://ubuntuforums.org/showpost.php?p=8044558&postcount=8](http://ubuntuforums.org/showpost.php?p=8044558&postcount=8)

What feature do you want from ubuntustudio?

If you have no need for the low latency kernel, don't use it.  Your system might not be enough to support it.

Use the regular Ubuntu live cd and install with it.  Let us know if that fixed your speed issue.

---

### Post by bruce leroy on 2009-10-14
I've loaded Ubuntu 9.04 although I'm not getting the errors anymore, my system is still slow and the sound is choppy.
AMD64 2.2 Ghz, 1.5 ram, NVIDIA Geforce 6100 gpu.  I know my pc isn't the best, but I don't think it should be running slow and should not have any sound issues.

---

### Post by lavinog on 2009-10-14
what kind of sound card do you have?
How are you determining that your system is slow?
Do you have desktop effects on?
Are you using the restricted nvidia driver?

Since 9.10 is due out in 12 days, you could give that a try.

---

### Post by bruce leroy on 2009-10-14
When I open and close apps there is a lag.  Dragging the page there is also a lag.  I'm using nvidia 173.  I don't have any effects on my desktop.

---

