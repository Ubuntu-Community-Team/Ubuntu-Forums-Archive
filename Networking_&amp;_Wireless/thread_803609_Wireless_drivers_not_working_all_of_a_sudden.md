---
title: "Wireless drivers not working all of a sudden"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by leperisland on 2008-05-22
Hello, I'm a total newbie by the way:

i have a lenovo x60s & with Handy Heron 8.04 - fresh install.

I was happily using the wireless connection on a train today when all of a sudden the connection dropped. I rebooted and i noticed that neither the ethernet or wireless card were showing up in network connections. The ethernet port is now working (I am using it now) but the wireless is not.

I followed a few solutions blindly EG installing linux-restricted-modules but nothings working.

```
eth0      Link encap:Ethernet  HWaddr 00:16:d3:b8:03:ec  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:feb8:3ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3962861 (3.7 MB)  TX bytes:529332 (516.9 KB)
          Base address:0x2000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83400 (81.4 KB)  TX bytes:83400 (81.4 KB)

```[   12.740189] CPU1: Intel(R) Core(TM) Duo CPU      L2400  @ ```
1.66GHz stepping 0c
[   12.740222] Total of 2 processors activated (6654.63 BogoMIPS).
[   12.740425] ENABLING IO-APIC IRQs
[   12.740643] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.887252] checking TSC synchronization [CPU#0 -> CPU#1]:
[   12.907237] Measured 526800 cycles TSC warp between CPUs, turning off TSC clock.
[   12.907241] Marking TSC unstable due to: check_tsc_sync_source failed.
[   12.907260] Brought up 2 CPUs
[   12.907296] CPU0 attaching sched-domain:
[   12.907300]  domain 0: span 03
[   12.907304]   groups: 01 02
[   12.907309] CPU1 attaching sched-domain:
[   12.907312]  domain 0: span 03
[   12.907315]   groups: 02 01
[   12.908010] net_namespace: 64 bytes
[   12.908020] Booting paravirtualized kernel on bare hardware
[   12.908823] Time: 16:26:14  Date: 05/22/08
[   12.908866] NET: Registered protocol family 16
[   12.909201] EISA bus registered
[   12.909208] ACPI: bus type pci registered
[   12.909492] PCI: PCI BIOS revision 2.10 entry at 0xfd82b, last bus=24
[   12.909497] PCI: Using configuration type 1
[   12.909500] Setting up standard PCI resources
[   12.915676] ACPI: EC: EC description table is found, configuring boot EC
[   12.925478] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   12.930422] ACPI: Interpreter enabled
[   12.930427] ACPI: (supports S0 S3 S4 S5)
[   12.930451] ACPI: Using IOAPIC for interrupt routing
[   12.943374] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   12.943379] ACPI: EC: driver started in poll mode
[   12.943711] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.944749] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   12.944756] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   12.946328] PCI: Transparent bridge - 0000:00:1e.0
[   12.946463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.946784] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   12.947022] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   12.947254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[   12.947489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[   12.947724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   12.953160] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[   12.953545] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[   12.953926] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[   12.954307] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[   12.954687] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)


[   12.955074] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[   12.955456] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[   12.955837] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[   12.956114] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   12.956253] ACPI: Power Resource [PUBS] (on)
[   12.956364] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.956417] pnp: PnP ACPI init
[   12.956429] ACPI: bus type pnp registered
[   12.958700] pnpacpi: exceeded the max number of mem resources: 12
[   12.962803] pnp: PnP ACPI: found 11 devices
[   12.962807] ACPI: ACPI bus type pnp unregistered
[   12.962813] PnPBIOS: Disabled by ACPI PNP
[   12.963267] PCI: Using ACPI for IRQ routing
[   12.963272] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.062830] NET: Registered protocol family 8
[   13.062833] NET: Registered protocol family 20
[   13.062889] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   13.062897] hpet0: 3 64-bit timers, 14318180 Hz
[   13.063951] AppArmor: AppArmor Filesystem Enabled
[   13.066814] Time: hpet clocksource has been installed.
[   13.066837] Switched to high resolution mode on CPU 0
[   13.067326] Switched to high resolution mode on CPU 1
[   13.083125] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   13.083131] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[   13.083136] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[   13.083141] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[   13.083146] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[   13.083152] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[   13.083157] system 00:00: iomem range 0x0-0x0 could not be reserved
[   13.083162] system 00:00: iomem range 0x0-0x0 could not be reserved
[   13.083167] system 00:00: iomem range 0xdc000-0xdffff has been reserved
[   13.083172] system 00:00: iomem range 0xe0000-0xe3fff has been reserved
[   13.083177] system 00:00: iomem range 0xe4000-0xe7fff has been reserved
[   13.083187] system 00:00: iomem range 0xe8000-0xebfff has been reserved
[   13.083199] system 00:02: ioport range 0x164e-0x164f has been reserved
[   13.083204] system 00:02: ioport range 0x1000-0x107f has been reserved
[   13.083209] system 00:02: ioport range 0x1180-0x11bf has been reserved
[   13.083214] system 00:02: ioport range 0x800-0x80f has been reserved
[   13.083219] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[   13.083224] system 00:02: ioport range 0x1600-0x165f could not be reserved
[   13.083230] system 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   13.083236] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   13.083242] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   13.083247] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   13.083253] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[   13.083258] system 00:02: iomem range 0xfed40000-0xfed40fff could not be reserved
[   13.113958] PCI: Bridge: 0000:00:1c.0
[   13.113963]   IO window: 2000-2fff
[   13.113971]   MEM window: ee000000-ee0fffff
[   13.113978]   PREFETCH window: disabled.
[   13.113985] PCI: Bridge: 0000:00:1c.1
[   13.113990]   IO window: 3000-4fff
[   13.113998]   MEM window: ec000000-edffffff
[   13.114004]   PREFETCH window: e4000000-e40fffff
[   13.114012] PCI: Bridge: 0000:00:1c.2
[   13.114017]   IO window: 5000-6fff
[   13.114024]   MEM window: e8000000-e9ffffff
[   13.114031]   PREFETCH window: e4100000-e41fffff
[   13.114039] PCI: Bridge: 0000:00:1c.3
[   13.114043]   IO window: 7000-8fff
[   13.114051]   MEM window: ea000000-ebffffff
[   13.114057]   PREFETCH window: e4200000-e42fffff
[   13.114070] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[   13.114074]   IO window: 00009000-000090ff
[   13.114081]   IO window: 00009400-000094ff
[   13.114089]   PREFETCH window: e0000000-e3ffffff
[   13.114096]   MEM window: 88000000-8bffffff




[   13.114103] PCI: Bridge: 0000:00:1e.0
[   13.114108]   IO window: 9000-cfff
[   13.114115]   MEM window: e4300000-e7ffffff
[   13.114122]   PREFETCH window: e0000000-e3ffffff
[   13.114160] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 16
[   13.114171] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.114201] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 17
[   13.114209] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.114239] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 18
[   13.114248] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   13.114277] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 19
[   13.114286] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   13.114301] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[   13.114310] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.114333] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   13.114342] PCI: Setting latency timer of device 0000:15:00.0 to 64
[   13.114361] NET: Registered protocol family 2
[   13.160022] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.160379] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.161601] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.162211] TCP: Hash tables configured (established 131072 bind 65536)
[   13.162216] TCP reno registered
[   13.172126] checking if image is initramfs... it is
[   14.430769] Freeing initrd memory: 7703k freed
[   14.430975] Simple Boot Flag at 0x35 set to 0x1
[   14.432079] audit: initializing netlink socket (disabled)
[   14.432096] audit(1211473574.409:1): initialized
[   14.432116] highmem bounce pool size: 64 pages
[   14.435520] VFS: Disk quotas dquot_6.5.1
[   14.435644] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.435861] io scheduler noop registered
[   14.435865] io scheduler anticipatory registered
[   14.435868] io scheduler deadline registered
[   14.435887] io scheduler cfq registered (default)
[   14.435902] Boot video device is 0000:00:02.0
[   14.436184] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.436252] assign_interrupt_mode Found MSI capability
[   14.436311] Allocate Port Service[0000:00:1c.0:pcie00]
[   14.436371] Allocate Port Service[0000:00:1c.0:pcie02]
[   14.436512] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.436580] assign_interrupt_mode Found MSI capability
[   14.436644] Allocate Port Service[0000:00:1c.1:pcie00]
[   14.436707] Allocate Port Service[0000:00:1c.1:pcie02]
[   14.436841] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.436909] assign_interrupt_mode Found MSI capability
[   14.436964] Allocate Port Service[0000:00:1c.2:pcie00]
[   14.437021] Allocate Port Service[0000:00:1c.2:pcie02]
[   14.437164] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   14.437231] assign_interrupt_mode Found MSI capability
[   14.437286] Allocate Port Service[0000:00:1c.3:pcie00]
[   14.437341] Allocate Port Service[0000:00:1c.3:pcie02]
[   14.437758] isapnp: Scanning for PnP cards...
[   14.792207] isapnp: No Plug & Play device found
[   14.839805] Real Time Clock Driver v1.12ac
[   14.839963] hpet_resources: 0xfed00000 is busy
[   14.840025] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.842129] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.842241] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   14.842409] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   14.852168] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.852176] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.872381] mice: PS/2 mouse device common for all mice
[   14.872565] EISA: Probing bus 0 at eisa.0
[   14.872575] Cannot allocate resource for EISA slot 1
[   14.872580] Cannot allocate resource for EISA slot 2
[   14.872584] Cannot allocate resource for EISA slot 3
[   14.872588] Cannot allocate resource for EISA slot 4
[   14.872592] Cannot allocate resource for EISA slot 5
[   14.872596] Cannot allocate resource for EISA slot 6
[   14.872599] Cannot allocate resource for EISA slot 7
[   14.872603] Cannot allocate resource for EISA slot 8
[   14.872607] EISA: Detected 0 cards.
[   14.872611] cpuidle: using governor ladder
[   14.872615] cpuidle: using governor menu
[   14.872746] NET: Registered protocol family 1
[   14.872788] Using IPI No-Shortcut mode
[   14.872829] registered taskstats version 1
[   14.872997]   Magic number: 8:717:439
[   14.873095]   hash matches device 0000:00:1c.0
[   14.873109] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.873112] EDD information not available.
[   14.873343] Freeing unused kernel memory: 364k freed
[   14.876330] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.252906] fuse init (API version 7.9)
[   16.288538] ACPI: SSDT 7F6F1D26, 0240 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[   16.289086] ACPI: SSDT 7F6F1FEB, 065A (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[   16.294166] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.294175] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.294590] ACPI: SSDT 7F6F1C5E, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[   16.295095] ACPI: SSDT 7F6F1F66, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[   16.298440] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   16.298450] ACPI: Processor [CPU1] (supports 8 throttling states)
[   16.301639] ACPI: Thermal Zone [THM0] (45 C)
[   16.304145] ACPI: Thermal Zone [THM1] (44 C)
[   16.878114] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   16.878120] Copyright (c) 1999-2006 Intel Corporation.
[   16.878270] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   16.878290] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   16.942507] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:16:d3:b8:03:ec
[   16.980944] usbcore: registered new interface driver usbfs
[   16.980982] usbcore: registered new interface driver hub
[   16.981627] usbcore: registered new device driver usb
[   16.985876] USB Universal Host Controller Interface driver v3.0
[   17.002727] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   17.003422] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 21
[   17.003442] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   17.003448] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   17.003725] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   17.007634] ehci_hcd 0000:00:1d.7: debug port 1
[   17.007644] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   17.007659] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xee444000
[   17.021844] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.022050] usb usb1: configuration #1 chosen from 1 choice
[   17.022090] hub 1-0:1.0: USB hub found
[   17.022100] hub 1-0:1.0: 8 ports detected
[   17.125847] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 20
[   17.125864] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.125871] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.125911] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   17.125952] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   17.126131] usb usb2: configuration #1 chosen from 1 choice
[   17.126172] hub 2-0:1.0: USB hub found
[   17.126181] hub 2-0:1.0: 2 ports detected
[   17.184175] SCSI subsystem initialized
[   17.201955] libata version 3.00 loaded.
[   17.229665] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 22
[   17.229682] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.229689] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.229730] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   17.229771] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00001840
[   17.229950] usb usb3: configuration #1 chosen from 1 choice
[   17.229989] hub 3-0:1.0: USB hub found
[   17.229998] hub 3-0:1.0: 2 ports detected
[   17.333513] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 23
[   17.333529] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   17.333536] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   17.333574] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   17.333616] uhci_hcd 0000:00:1d.2: irq 23, io base 0x00001860
[   17.333798] usb usb4: configuration #1 chosen from 1 choice
[   17.333844] hub 4-0:1.0: USB hub found
[   17.333852] hub 4-0:1.0: 2 ports detected
[   17.437359] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 21
[   17.437377] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   17.437384] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   17.437421] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   17.437455] uhci_hcd 0000:00:1d.3: irq 21, io base 0x00001880
[   17.437639] usb usb5: configuration #1 chosen from 1 choice
[   17.437679] hub 5-0:1.0: USB hub found
[   17.437687] hub 5-0:1.0: 2 ports detected
[   17.540899] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 22
[   17.540912] PCI: Setting latency timer of device 0000:15:00.1 to 64
[   17.593678] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[e4301000-e43017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   17.606092] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 20
[   17.606142] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   17.606161] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   17.612491] ata_piix 0000:00:1f.2: version 2.12
[   17.612500] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   17.768680] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 20
[   17.768732] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   17.768847] scsi0 : ata_piix
[   17.768941] scsi1 : ata_piix
[   17.770679] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[   17.770684] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[   17.943636] ata1.00: ATA-7: HITACHI HTS541660J9SA00, SBBIC7JP, max UDMA/100
[   17.943645] ata1.00: 117210240 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   17.959523] ata1.00: configured for UDMA/100
[   18.126689] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS54166 SBBI PQ: 0 ANSI: 5
[   18.137779] Driver 'sd' needs updating - please use bus_type methods
[   18.137886] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   18.137907] sd 0:0:0:0: [sda] Write Protect is off
[   18.137912] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.137941] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.138023] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   18.138042] sd 0:0:0:0: [sda] Write Protect is off
[   18.138046] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.138075] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.138081]  sda: sda1 sda2 < sda5 >
[   18.564301] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.573314] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.857091] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae4070023200c]
[   18.905795] Attempting manual resume
[   18.905801] swsusp: Resume From Partition 8:5
[   18.905804] PM: Checking swsusp image.
[   18.906066] PM: Resume from disk failed.
[   18.973704] kjournald starting.  Commit interval 5 seconds
[   18.973409] EXT3-fs: mounted filesystem with ordered data mode.
[   27.696375] Linux agpgart interface v0.102
[   27.761946] agpgart: Detected an Intel 945GM Chipset.
[   27.763711] agpgart: Detected 7932K stolen memory.
[   27.817783] agpgart: AGP aperture is 256M @ 0xd0000000
[   28.151983] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.208069] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.769684] input: Power Button (FF) as /devices/virtual/input/input2
[   28.778852] ACPI: Power Button (FF) [PWRF]
[   28.778977] input: Lid Switch as /devices/virtual/input/input3
[   28.780385] ACPI: Lid Switch [LID]
[   28.780498] input: Sleep Button (CM) as /devices/virtual/input/input4
[   28.794827] ACPI: Sleep Button (CM) [SLPB]
[   29.459146] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   29.459153] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   29.459319] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
[   29.459338] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   29.459368] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   29.627334] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   29.658772] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   29.661367] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/LNXVIDEO:01/input/input6
[   29.682733] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   30.485716] ACPI: AC Adapter [AC] (off-line)
[   30.779740] iTCO_vendor_support: vendor-support=0
[   30.851622] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.851812] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   30.851887] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.934713] ACPI: Battery Slot [BAT0] (battery present)
[   30.994989] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   31.099210] intel_rng: FWH not detected
[   31.374875] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 22
[   31.374885] hda_intel: probe_mask set to 0x1 for device 17aa:2010
[   31.374914] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   31.444349] sdhci: Secure Digital Host Controller Interface driver
[   31.444354] sdhci: Copyright(c) Pierre Ossman
[   31.597449] irda_init()
[   31.597473] NET: Registered protocol family 23
[   31.653257] Non-volatile memory driver v1.2
[   31.920408] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   31.936972] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input8
[   31.986929] nsc-ircc 00:0a: activated
[   31.986937] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   31.986967] nsc-ircc, chip->init
[   31.986983] nsc-ircc, Found chip at base=0x164e
[   31.987345] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   31.987032] nsc-ircc, driver loaded (Dag Brattli)
[   31.987354] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   31.987358] thinkpad_acpi: ThinkPad BIOS 7BETD0WW (2.11 ), EC 7BHT40WW-1.13
[   31.987362] thinkpad_acpi: Lenovo ThinkPad X60s
[   31.987484] IrDA: Registered device irda0
[   31.987489] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   31.987876] thinkpad_acpi: radio switch found; radios are disabled
[   31.993293] thinkpad_acpi: acpi_bus_get_device(bay) failed: -19
[   31.993299] thinkpad_acpi: disabling subdriver bay
[   31.995452] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   31.995847] input: ThinkPad Extra Buttons as /devices/virtual/input/input9
[   32.570754] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:201c]
[   32.639601] iwl3945: Radio Frequency Kill Switch is On:
[   32.639606] Kill switch must be turned off for wireless networking to work.
[   32.644716] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   32.654772] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   32.674747] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   32.702284] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   32.723135] Yenta: ISA IRQ mask 0x0cb0, PCI irq 20
[   32.723140] Socket status: 30000006
[   32.723146] pcmcia: parent PCI bridge I/O window: 0x9000 - 0xcfff
[   32.723151] cs: IO port probe 0x9000-0xcfff: clean.
[   32.725012] pcmcia: parent PCI bridge Memory window: 0xe4300000 - 0xe7ffffff
[   32.725017] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe3ffffff
[   32.725126] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   32.740580] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 18)
[   32.740609] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 23
[   32.740633] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   32.740643] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   32.740702] mmc0: SDHCI at 0xe4301800 irq 23 DMA
[   33.207861] Clocksource tsc unstable (delta = -200111794 ns)
[   33.310745] cs: IO port probe 0x100-0x3af: clean.
[   33.313222] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   33.314258] cs: IO port probe 0x820-0x8ff: clean.
[   33.315114] cs: IO port probe 0xc00-0xcf7: clean.
[   33.316250] cs: IO port probe 0xa00-0xaff: clean.
[   33.470547] lp: driver loaded but no devices found
[   33.647937] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k
[   33.689477] EXT3 FS on sda1, internal journal
[   34.569847] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.143028] ACPI: ACPI Dock Station Driver 
[   35.263712] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   35.263724] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   35.263782] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   35.263813] ACPI: \_SB_.PCI0.SATA.SCND.MSTR: found ejectable bay
[   35.263822] ACPI: \_SB_.PCI0.SATA.SCND.MSTR: Adding notify handler
[   35.263854] ACPI: Error installing bay notify handler
[   35.263862] ACPI: \_SB_.PCI0.SATA.SCND.MSTR: Is dependent on dock
[   35.263865] 
[   35.263868] ACPI: Bay [\_SB_.PCI0.SATA.SCND.MSTR] Added
[   36.630850] apm: BIOS not found.
[   36.775845] ppdev: user-space parallel port driver
[   36.865733] audit(1211473597.598:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4964 profile="/usr/sbin/cupsd" namespace="default"
[   37.030516] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input10
[   38.112247] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   38.112257] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   38.210850] Bluetooth: Core ver 2.11
[   38.211584] NET: Registered protocol family 31
[   38.211590] Bluetooth: HCI device and connection manager initialized
[   38.211596] Bluetooth: HCI socket layer initialized
[   38.231001] Bluetooth: L2CAP ver 2.9
[   38.231008] Bluetooth: L2CAP socket layer initialized
[   38.296025] Bluetooth: RFCOMM socket layer initialized
[   38.296045] Bluetooth: RFCOMM TTY layer initialized
[   38.296048] Bluetooth: RFCOMM ver 1.8
[   41.425462] NET: Registered protocol family 17
[   41.473963] [drm] Initialized drm 1.1.0 20060810
[   41.476519] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   41.476528] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   41.476591] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   43.235943] NET: Registered protocol family 10
[   43.236325] lo: Disabled Privacy Extensions
[   50.340764] eth0: no IPv6 routers present
[   62.692434] CPU0 attaching NULL sched-domain.
[   62.692443] CPU1 attaching NULL sched-domain.
[   62.713660] CPU0 attaching sched-domain:
[   62.713670]  domain 0: span 03
[   62.713673]   groups: 01 02
[   62.713679]   domain 1: span 03
[   62.713682]    groups: 03
[   62.713687] CPU1 attaching sched-domain:
[   62.713692]  domain 0: span 03
[   62.713695]   groups: 02 01
[   62.713699]   domain 1: span 03
[   62.713702]    groups: 03
[   72.853102] e1000: eth0: e1000_watchdog: NIC Link is Down
[   77.552749] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   77.552758] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   77.556869] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   83.658553] eth0: no IPv6 routers present

```

Thanks :)

---

### Post by chili555 on 2008-05-22
> iwl3945: Radio Frequency Kill Switch is On:
[   32.639606] Kill switch must be turned off for wireless networking to work.Flip the switch and you will be all set. [http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_3945ABG_Mini-PCI_Express_Adapter](http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_3945ABG_Mini-PCI_Express_Adapter)

---

### Post by leperisland on 2008-05-22
LOL can't believe it!! Must have knocked it with my knee or something what a tool :D

Thanks,

Caroline

---

