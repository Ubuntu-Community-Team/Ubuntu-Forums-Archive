---
title: "webcam problems"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by dovael on 2009-11-02
I have OMS-19 GPT web camera with VFW interface. It came with disk of drivers only for XP and Vista. How do I install it in Ubuntu 9.10 and also make it work with Skype

---

### Post by alanrr_sr on 2009-11-02
Is that a USB webcam?
Did u try just plug in it on your computer? 
Did you try programas like cheese?
What is the output of the command lsusb and ls /dev/video* ?
Have you read [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) ?

---

### Post by dovael on 2009-11-02
Replying to your queries.
It is USB webcam. I did plug it in & set up cheese and got green screen. Output of lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:612a Microdia PC Camera (SN9C325)
Bus 001 Device 003: ID 03f0:4f11 Hewlett-Packard OfficeJet 5600 (USBHUB)
Bus 001 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dov@dov-desktop:~$ 
Output of ls /dev/video* is
/dev/video0
I did look into Ubuntu help on webcam as you suggested but it left me more confused than ever.
Appreciate any help.

---

### Post by alanrr_sr on 2009-11-03
New request :(

What is the output of dmesg when you connect the camera?

Edit 1:
(I am not an expert, just theorizing: I think that your camera has support for v4l , but not for v4l2, and this is not nice at the moment)

Edit 2:
it has a v4l2 driver..it should work, at least with cheese:
[http://moinejf.free.fr/webcam.html](http://moinejf.free.fr/webcam.html)

---

### Post by dovael on 2009-11-03
output of dmesg when I connect the camera


[    0.156418] PCI: Using configuration type 1 for base access
[    0.157369] bio: create slab <bio-0> at 0
[    0.160158] ACPI: EC: Look up EC in DSDT
[    0.167435] ACPI: Interpreter enabled
[    0.167446] ACPI: (supports S0 S1 S3 S4 S5)
[    0.167467] ACPI: Using IOAPIC for interrupt routing
[    0.167510] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.171233] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.171235] PCI: Using MMCONFIG for extended config space
[    0.178072] ACPI Warning: Incorrect checksum in table [OEMB] - 3C, should be 35 20090521 tbutils-246
[    0.178870] ACPI: No dock devices found.
[    0.179153] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.179243] pci 0000:00:02.0: reg 10 32bit mmio: [0xfea80000-0xfeafffff]
[    0.179248] pci 0000:00:02.0: reg 14 io port: [0xdc00-0xdc07]
[    0.179253] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.179258] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.179336] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfea78000-0xfea7bfff]
[    0.179379] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.179382] pci 0000:00:1b.0: PME# disabled
[    0.179441] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.179444] pci 0000:00:1c.0: PME# disabled
[    0.179504] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.179508] pci 0000:00:1c.1: PME# disabled
[    0.179558] pci 0000:00:1d.0: reg 20 io port: [0xd880-0xd89f]
[    0.179606] pci 0000:00:1d.1: reg 20 io port: [0xd800-0xd81f]
[    0.179654] pci 0000:00:1d.2: reg 20 io port: [0xd480-0xd49f]
[    0.179701] pci 0000:00:1d.3: reg 20 io port: [0xd400-0xd41f]
[    0.179755] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfea77c00-0xfea77fff]
[    0.179806] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.179810] pci 0000:00:1d.7: PME# disabled
[    0.179931] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.179936] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.179940] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.179943] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.179947] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0a00 (mask 0017)
[    0.179951] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 00ff)
[    0.179992] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.180006] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.180013] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.180019] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.180026] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.180068] pci 0000:00:1f.2: reg 10 io port: [0xd080-0xd087]
[    0.180074] pci 0000:00:1f.2: reg 14 io port: [0xd000-0xd003]
[    0.180080] pci 0000:00:1f.2: reg 18 io port: [0xcc00-0xcc07]
[    0.180086] pci 0000:00:1f.2: reg 1c io port: [0xc880-0xc883]
[    0.180091] pci 0000:00:1f.2: reg 20 io port: [0xc800-0xc80f]
[    0.180115] pci 0000:00:1f.2: PME# supported from D3hot
[    0.180119] pci 0000:00:1f.2: PME# disabled
[    0.180163] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.180276] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.180297] pci 0000:02:00.0: reg 18 64bit mmio: [0xfdfff000-0xfdffffff]
[    0.180311] pci 0000:02:00.0: reg 20 64bit mmio: [0xfdfe0000-0xfdfeffff]
[    0.180319] pci 0000:02:00.0: reg 30 32bit mmio: [0xfebf0000-0xfebfffff]
[    0.180359] pci 0000:02:00.0: supports D1 D2
[    0.180361] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.180366] pci 0000:02:00.0: PME# disabled
[    0.180424] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
[    0.180428] pci 0000:00:1c.1: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.180434] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.180482] pci 0000:00:1e.0: transparent bridge
[    0.180504] pci_bus 0000:00: on NUMA node 0
[    0.180508] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180658] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.180773] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.180830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.183494] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.183598] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.183698] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.183798] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.183897] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.184012] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.184114] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.184215] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.184388] SCSI subsystem initialized
[    0.184415] libata version 3.00 loaded.
[    0.184415] usbcore: registered new interface driver usbfs
[    0.184415] usbcore: registered new interface driver hub
[    0.184415] usbcore: registered new device driver usb
[    0.184415] ACPI: WMI: Mapper loaded
[    0.184415] PCI: Using ACPI for IRQ routing
[    0.196012] Bluetooth: Core ver 2.15
[    0.196035] NET: Registered protocol family 31
[    0.196035] Bluetooth: HCI device and connection manager initialized
[    0.196035] Bluetooth: HCI socket layer initialized
[    0.196035] NetLabel: Initializing
[    0.196035] NetLabel:  domain hash size = 128
[    0.196035] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.196054] NetLabel:  unlabeled traffic allowed by default
[    0.196208] hpet clockevent registered
[    0.196210] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.196215] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.196220] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.212060] pnp: PnP ACPI init
[    0.212086] ACPI: bus type pnp registered
[    0.216275] pnp: PnP ACPI: found 18 devices
[    0.216278] ACPI: ACPI bus type pnp unregistered
[    0.216282] PnPBIOS: Disabled by ACPI PNP
[    0.216293] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.216302] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.216305] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.216307] system 00:07: ioport range 0x480-0x4bf has been reserved
[    0.216310] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.216313] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.216316] system 00:07: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.216322] system 00:09: iomem range 0xffc00000-0xfff7ffff has been reserved
[    0.216327] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.216329] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.216336] system 00:0d: ioport range 0xa00-0xadf has been reserved
[    0.216338] system 00:0d: ioport range 0xae0-0xaef has been reserved
[    0.216347] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[    0.216353] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.216356] system 00:11: iomem range 0xc0000-0xcffff could not be reserved
[    0.216358] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[    0.216361] system 00:11: iomem range 0x100000-0x3f6fffff could not be reserved
[    0.251008] AppArmor: AppArmor Filesystem Enabled
[    0.251044] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.251046] pci 0000:00:1c.0:   IO window: disabled
[    0.251051] pci 0000:00:1c.0:   MEM window: disabled
[    0.251054] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.251058] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.251062] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    0.251067] pci 0000:00:1c.1:   MEM window: 0xfeb00000-0xfebfffff
[    0.251071] pci 0000:00:1c.1:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.251077] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.251078] pci 0000:00:1e.0:   IO window: disabled
[    0.251083] pci 0000:00:1e.0:   MEM window: disabled
[    0.251086] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.251098]   alloc irq_desc for 16 on node -1
[    0.251100]   alloc kstat_irqs on node -1
[    0.251105] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.251110] pci 0000:00:1c.0: setting latency timer to 64
[    0.251117]   alloc irq_desc for 17 on node -1
[    0.251118]   alloc kstat_irqs on node -1
[    0.251122] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.251125] pci 0000:00:1c.1: setting latency timer to 64
[    0.251131] pci 0000:00:1e.0: setting latency timer to 64
[    0.251136] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.251138] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.251141] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.251143] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.251145] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.251148] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.251150] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.251185] NET: Registered protocol family 2
[    0.251277] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.251569] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.252006] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.252402] TCP: Hash tables configured (established 131072 bind 65536)
[    0.252406] TCP reno registered
[    0.252518] NET: Registered protocol family 1
[    0.252589] Trying to unpack rootfs image as initramfs...
[    0.426784] Freeing initrd memory: 7703k freed
[    0.430988] cpufreq-nforce2: No nForce2 chipset.
[    0.431016] Scanning for low memory corruption every 60 seconds
[    0.431113] audit: initializing netlink socket (disabled)
[    0.431130] type=2000 audit(1257258859.428:1): initialized
[    0.438814] highmem bounce pool size: 64 pages
[    0.438819] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.440165] VFS: Disk quotas dquot_6.5.2
[    0.440220] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.440716] fuse init (API version 7.12)
[    0.440796] msgmni has been set to 1731
[    0.440984] alg: No test for stdrng (krng)
[    0.440997] io scheduler noop registered
[    0.440999] io scheduler anticipatory registered
[    0.441000] io scheduler deadline registered
[    0.441038] io scheduler cfq registered (default)
[    0.441050] pci 0000:00:02.0: Boot video device
[    0.441227]   alloc irq_desc for 24 on node -1
[    0.441229]   alloc kstat_irqs on node -1
[    0.441239] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.441248] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.441360]   alloc irq_desc for 25 on node -1
[    0.441362]   alloc kstat_irqs on node -1
[    0.441369] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.441376] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.441456] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.441471] Firmware did not grant requested _OSC control
[    0.441486] Firmware did not grant requested _OSC control
[    0.441512] Firmware did not grant requested _OSC control
[    0.441523] Firmware did not grant requested _OSC control
[    0.441535] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.441659] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.441663] ACPI: Power Button [PWRF]
[    0.441719] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.441721] ACPI: Power Button [PWRB]
[    0.441977] processor LNXCPU:00: registered as cooling_device0
[    0.442009] processor LNXCPU:01: registered as cooling_device1
[    0.444144] isapnp: Scanning for PnP cards...
[    0.697550] Switched to high resolution mode on CPU 1
[    0.700125] Switched to high resolution mode on CPU 0
[    0.797017] isapnp: No Plug & Play device found
[    0.797979] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.798072] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.798159] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.798437] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.798681] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.799623] brd: module loaded
[    0.800057] loop: module loaded
[    0.800123] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.800219] ata_piix 0000:00:1f.1: version 2.13
[    0.800232]   alloc irq_desc for 18 on node -1
[    0.800235]   alloc kstat_irqs on node -1
[    0.800242] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.800277] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.800350] scsi0 : ata_piix
[    0.800425] scsi1 : ata_piix
[    0.801720] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.801723] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.801745]   alloc irq_desc for 19 on node -1
[    0.801747]   alloc kstat_irqs on node -1
[    0.801753] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.801759] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.801798] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.801839] scsi2 : ata_piix
[    0.801969] scsi3 : ata_piix
[    0.803125] ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
[    0.803128] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
[    0.803897] Fixed MDIO Bus: probed
[    0.803929] PPP generic driver version 2.4.2
[    0.804032] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.804050]   alloc irq_desc for 23 on node -1
[    0.804052]   alloc kstat_irqs on node -1
[    0.804058] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.804072] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.804075] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.804120] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.808030] ehci_hcd 0000:00:1d.7: debug port 1
[    0.808036] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.808048] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfea77c00
[    0.820033] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.820157] usb usb1: configuration #1 chosen from 1 choice
[    0.820200] hub 1-0:1.0: USB hub found
[    0.820206] hub 1-0:1.0: 8 ports detected
[    0.820267] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.820284] uhci_hcd: USB Universal Host Controller Interface driver
[    0.820314] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.820320] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.820323] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.820357] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.820379] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    0.820450] usb usb2: configuration #1 chosen from 1 choice
[    0.820475] hub 2-0:1.0: USB hub found
[    0.820480] hub 2-0:1.0: 2 ports detected
[    0.820524] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.820531] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.820534] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.820560] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.820581] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.820646] usb usb3: configuration #1 chosen from 1 choice
[    0.820669] hub 3-0:1.0: USB hub found
[    0.820674] hub 3-0:1.0: 2 ports detected
[    0.820715] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.820721] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.820724] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.820750] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.820780] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    0.820844] usb usb4: configuration #1 chosen from 1 choice
[    0.820869] hub 4-0:1.0: USB hub found
[    0.820875] hub 4-0:1.0: 2 ports detected
[    0.820914] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.820920] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.820923] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.820950] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.820977] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
[    0.821043] usb usb5: configuration #1 chosen from 1 choice
[    0.821068] hub 5-0:1.0: USB hub found
[    0.821074] hub 5-0:1.0: 2 ports detected
[    0.821167] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.823125] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.823130] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.823188] mice: PS/2 mouse device common for all mice
[    0.823278] rtc_cmos 00:03: RTC can wake from S4
[    0.823312] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.823335] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.823431] device-mapper: uevent: version 1.0.3
[    0.823542] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.823599] device-mapper: multipath: version 1.1.0 loaded
[    0.823602] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.823705] EISA: Probing bus 0 at eisa.0
[    0.823730] EISA: Detected 0 cards.
[    0.823799] cpuidle: using governor ladder
[    0.823801] cpuidle: using governor menu
[    0.824262] TCP cubic registered
[    0.824403] NET: Registered protocol family 10
[    0.824828] lo: Disabled Privacy Extensions
[    0.825135] NET: Registered protocol family 17
[    0.825152] Bluetooth: L2CAP ver 2.13
[    0.825154] Bluetooth: L2CAP socket layer initialized
[    0.825156] Bluetooth: SCO (Voice Link) ver 0.6
[    0.825158] Bluetooth: SCO socket layer initialized
[    0.825184] Bluetooth: RFCOMM TTY layer initialized
[    0.825187] Bluetooth: RFCOMM socket layer initialized
[    0.825188] Bluetooth: RFCOMM ver 1.11
[    0.825226] Using IPI No-Shortcut mode
[    0.825287] PM: Resume from disk failed.
[    0.825299] registered taskstats version 1
[    0.825400]   Magic number: 1:768:585
[    0.825466] rtc_cmos 00:03: setting system clock to 2009-11-03 14:34:20 UTC (1257258860)
[    0.825469] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.825471] EDD information not available.
[    0.849573] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.978243] ata3.00: ATA-8: WDC WD1600AAJS-00B4A0, 01.03A01, max UDMA/133
[    0.978249] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.985247] ata3.00: configured for UDMA/133
[    0.985262] ata1.00: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
[    0.985267] ata1.00: 78165360 sectors, multi 16: LBA 
[    0.985327] ata1.01: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A101, max UDMA/33
[    0.985363] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.001142] ata1.00: configured for UDMA/33
[    1.016214] ata1.01: configured for UDMA/33
[    1.018677] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
[    1.018795] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.020923] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.022695] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A101 PQ: 0 ANSI: 5
[    1.022718] sd 0:0:0:0: [sda] Write Protect is off
[    1.022720] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.022742] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.034270] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.034275] Uniform CD-ROM driver Revision: 3.20
[    1.034406] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.034444] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.034496]  sda:
[    1.034530] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-0 01.0 PQ: 0 ANSI: 5
[    1.034621] sd 2:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.034629] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.034660] sd 2:0:0:0: [sdb] Write Protect is off
[    1.034663] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.034684] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.034786]  sdb: sdb1 sdb2 < sda1 sda2 < > sda3
[    1.076040] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.081230]  sdb5 >
[    1.081509] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.081526] Freeing unused kernel memory: 540k freed
[    1.081805] Write protecting the kernel text: 4568k
[    1.081845] Write protecting the kernel read-only data: 1836k
[    1.136546] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    1.187563] Linux agpgart interface v0.103
[    1.190176] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    1.190513] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[    1.193678] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.223522] [drm] Initialized drm 1.1.0 20060810
[    1.260381] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.260387] i915 0000:00:02.0: setting latency timer to 64
[    1.262617]   alloc irq_desc for 26 on node -1
[    1.262622]   alloc kstat_irqs on node -1
[    1.262632] i915 0000:00:02.0: irq 26 for MSI/MSI-X
[    1.267384] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.267403] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.267440] r8169 0000:02:00.0: setting latency timer to 64
[    1.267483]   alloc irq_desc for 27 on node -1
[    1.267485]   alloc kstat_irqs on node -1
[    1.267499] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    1.268087] eth0: RTL8168c/8111c at 0xf853c000, 00:21:85:69:71:58, XID 3c4000c0 IRQ 27
[    1.383369] usb 1-3: configuration #1 chosen from 1 choice
[    1.384697] hub 1-3:1.0: USB hub found
[    1.385830] hub 1-3:1.0: 4 ports detected
[    1.399467] [drm] fb0: inteldrmfb frame buffer device
[    1.399522] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.465987] [drm] DAC-6: set mode 1920x1080 14
[    1.493394] Console: switching to colour frame buffer device 240x67
[    1.672086] usb 1-3.4: new full speed USB device using ehci_hcd and address 3
[    1.765580] usb 1-3.4: configuration #1 chosen from 1 choice
[    1.951821] xor: automatically using best checksumming function: pIII_sse
[    1.968504]    pIII_sse  :  8149.000 MB/sec
[    1.968506] xor: using function: pIII_sse (8149.000 MB/sec)
[    1.970772] device-mapper: dm-raid45: initialized v0.2594b
[    2.212300] PM: Starting manual resume from disk
[    2.212304] PM: Resume from partition 8:21
[    2.212306] PM: Checking hibernation image.
[    2.212488] PM: Resume from disk failed.
[    2.243280] kjournald starting.  Commit interval 5 seconds
[    2.243290] EXT3-fs: mounted filesystem with writeback data mode.
[    3.098391] type=1505 audit(1257258862.770:2): operation="profile_load" pid=451 name=/usr/share/gdm/guest-session/Xsession
[    3.101812] type=1505 audit(1257258862.774:3): operation="profile_load" pid=452 name=/sbin/dhclient3
[    3.102528] type=1505 audit(1257258862.774:4): operation="profile_load" pid=452 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.102887] type=1505 audit(1257258862.774:5): operation="profile_load" pid=452 name=/usr/lib/connman/scripts/dhclient-script
[    3.123210] type=1505 audit(1257258862.794:6): operation="profile_load" pid=453 name=/usr/bin/evince
[    3.133580] type=1505 audit(1257258862.806:7): operation="profile_load" pid=453 name=/usr/bin/evince-previewer
[    3.140050] type=1505 audit(1257258862.814:8): operation="profile_load" pid=453 name=/usr/bin/evince-thumbnailer
[    3.257750] type=1505 audit(1257258862.931:9): operation="profile_load" pid=455 name=/usr/bin/freshclam
[    3.267388] type=1505 audit(1257258862.939:10): operation="profile_load" pid=456 name=/usr/sbin/clamd
[    4.800803] Adding 3004112k swap on /dev/sdb5.  Priority:-1 extents:1 across:3004112k 
[    5.195808] EXT3 FS on sdb1, internal journal
[    6.593537] udev: starting version 147
[    9.254592] Linux video capture interface: v2.00
[    9.266746] gspca: main v2.6.0 registered
[    9.268282] gspca: probing 0c45:612a
[    9.268988] sonixj: Sonix chip id: 12
[    9.269444] gspca: probe ok
[    9.269462] usbcore: registered new interface driver sonixj
[    9.269465] sonixj: registered
[    9.328958] psmouse serio1: ID: 10 00 64
[    9.383167] intel_rng: FWH not detected
[    9.392672] lp: driver loaded but no devices found
[    9.442231] parport_pc 00:0f: reported by Plug and Play ACPI
[    9.442339] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    9.475373] ppdev: user-space parallel port driver
[    9.510543] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.540785] lp0: using parport0 (interrupt-driven).
[    9.828772] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   10.022819] nf_conntrack version 0.5.0 (16234 buckets, 64936 max)
[   10.023028] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   10.023031] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   10.023033] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   10.071179] __ratelimit: 12 callbacks suppressed
[   10.071183] type=1505 audit(1257258869.742:15): operation="profile_replace" pid=992 name=/usr/share/gdm/guest-session/Xsession
[   10.072929] type=1505 audit(1257258869.746:16): operation="profile_replace" pid=993 name=/sbin/dhclient3
[   10.073594] type=1505 audit(1257258869.746:17): operation="profile_replace" pid=993 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.073956] type=1505 audit(1257258869.746:18): operation="profile_replace" pid=993 name=/usr/lib/connman/scripts/dhclient-script
[   10.079272] type=1505 audit(1257258869.750:19): operation="profile_replace" pid=994 name=/usr/bin/evince
[   10.089901] type=1505 audit(1257258869.762:20): operation="profile_replace" pid=994 name=/usr/bin/evince-previewer
[   10.096202] type=1505 audit(1257258869.770:21): operation="profile_replace" pid=994 name=/usr/bin/evince-thumbnailer
[   10.187549] type=1505 audit(1257258869.858:22): operation="profile_replace" pid=999 name=/usr/bin/freshclam
[   10.189568] type=1505 audit(1257258869.862:23): operation="profile_replace" pid=1000 name=/usr/sbin/clamd
[   10.191509] type=1505 audit(1257258869.862:24): operation="profile_replace" pid=1001 name=/usr/lib/cups/backend/cups-pdf
[   10.228302] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.228325] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.409903] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   10.410085] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   21.370851] r8169: eth0: link up
[   21.370856] r8169: eth0: link up
[   31.796520] eth0: no IPv6 routers present
[   33.716793] CPU0 attaching NULL sched-domain.
[   33.716799] CPU1 attaching NULL sched-domain.
[   33.728595] CPU0 attaching sched-domain:
[   33.728599]  domain 0: span 0-1 level MC
[   33.728602]   groups: 0 1
[   33.728606]   domain 1: span 0-1 level CPU
[   33.728608]    groups: 0-1 (__cpu_power = 2048)
[   33.728614] CPU1 attaching sched-domain:
[   33.728616]  domain 0: span 0-1 level MC
[   33.728618]   groups: 1 0
[   33.728621]   domain 1: span 0-1 level CPU
[   33.728624]    groups: 0-1 (__cpu_power = 2048)
[   34.905776] CPU0 attaching NULL sched-domain.
[   34.905782] CPU1 attaching NULL sched-domain.
[   34.920134] CPU0 attaching sched-domain:
[   34.920141]  domain 0: span 0-1 level MC
[   34.920146]   groups: 0 1
[   34.920155] CPU1 attaching sched-domain:
[   34.920158]  domain 0: span 0-1 level MC
[   34.920162]   groups: 1 0
[   55.085058] [drm] DAC-6: set mode  15
[14173.165635] usb 1-3.4: USB disconnect, address 3
[14173.165835] gspca: disconnect complete
[14237.988037] usb 2-1: new full speed USB device using uhci_hcd and address 2
[14238.141229] usb 2-1: configuration #1 chosen from 1 choice
[14238.144189] gspca: probing 0c45:612a
[14238.149101] sonixj: Sonix chip id: 12
[14238.151165] gspca: probe ok
dov@dov-desktop:~$

---

