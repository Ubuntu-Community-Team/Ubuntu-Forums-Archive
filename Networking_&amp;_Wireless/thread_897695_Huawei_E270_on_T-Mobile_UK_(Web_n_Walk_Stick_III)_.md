---
title: "Huawei E270 on T-Mobile UK (Web n Walk Stick III) -- Can't Connect"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by padark on 2008-08-22
Dear Everyone:

I picked up this HSDPA modem on T-Mobile UK back in April, when I was running Gutsy, and managed to get it to work eventually: how, I cannot for the life of me remember!

When I installed Hardy, it stopped working. Completely. DESPITE the promise of "under this kernel, it just works". So I have downgraded to Gutsy, and I STILL can't get it to work. The LED double-flashes green (ie, it's powered up but doesn't detect a network) -- in fact, no matter how long I wait, it never detects a network.

I am now at my wits' (and budget's) end: I'm not techy enough to figure out what's wrong, and I'd very much appreciate a simple, step-by-step, totalidiot's guide to making this work -- as I know it does! Please DON'T tell me to go read another thread: I have 56 tabs open in Firefox, at least 50 of which are "Get a Huawei modem working under Linux". None of them have been helpful. (It'd also be nice if you'd explain to me what the various steps are doing, why you're asking for information, what the relevant code means, etc, so I understand how to do this myself next time)

I am currently running Ubuntu Gutsy (7.10), kernel 2.6.22-15-generic. I'd vastly *prefer* to be running Hardy, so if that would be easier, please say so.

The relevant outputs:

dmesg:
```
[   26.057146] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.057423] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.135421] Memory: 2059280k/2088640k available (2016k kernel code, 28124k reserved, 919k data, 364k init, 1171136k highmem)
[   26.135429] virtual kernel memory layout:
[   26.135430]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   26.135431]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.135431]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   26.135432]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   26.135433]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   26.135434]       .data : 0xc02f8046 - 0xc03dde84   ( 919 kB)
[   26.135435]       .text : 0xc0100000 - 0xc02f8046   (2016 kB)
[   26.135437] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.135469] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   26.135591] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   26.135595] hpet0: 3 64-bit timers, 14318180 Hz
[   26.216565] Calibrating delay using timer specific routine.. 3993.07 BogoMIPS (lpj=7986157)
[   26.216584] Security Framework v1.0.0 initialized
[   26.216589] SELinux:  Disabled at boot.
[   26.216600] Mount-cache hash table entries: 512
[   26.216709] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   26.216715] monitor/mwait feature present.
[   26.216717] using mwait in idle threads.
[   26.216720] CPU: L1 I cache: 32K, L1 D cache: 32K
[   26.216722] CPU: L2 cache: 4096K
[   26.216725] CPU: Physical Processor ID: 0
[   26.216726] CPU: Processor Core ID: 0
[   26.216728] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   26.216735] Compat vDSO mapped to ffffe000.
[   26.216746] Checking 'hlt' instruction... OK.
[   26.232645] SMP alternatives: switching to UP code
[   26.233001] Early unpacking initramfs... done
[   26.507811] ACPI: Core revision 20070126
[   26.507854] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.522218] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   26.522232] SMP alternatives: switching to SMP code
[   26.522291] Booting processor 1/1 eip 3000
[   26.532692] Initializing CPU#1
[   26.612339] Calibrating delay using timer specific routine.. 3990.00 BogoMIPS (lpj=7980010)
[   26.612345] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   26.612349] monitor/mwait feature present.
[   26.612351] CPU: L1 I cache: 32K, L1 D cache: 32K
[   26.612353] CPU: L2 cache: 4096K
[   26.612355] CPU: Physical Processor ID: 0
[   26.612356] CPU: Processor Core ID: 1
[   26.612357] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   26.613059] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   26.613078] Total of 2 processors activated (7983.08 BogoMIPS).
[   26.613224] ENABLING IO-APIC IRQs
[   26.613400] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.780320] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   26.800322] Brought up 2 CPUs
[   27.206817] migration_cost=33
[   27.206926] Booting paravirtualized kernel on bare hardware
[   27.206993] Time: 15:24:17  Date: 07/22/108
[   27.207009] NET: Registered protocol family 16
[   27.207078] EISA bus registered
[   27.207082] ACPI: bus type pci registered
[   27.207222] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[   27.207224] PCI: Using configuration type 1
[   27.207225] Setting up standard PCI resources
[   27.216729] ACPI: EC: Look up EC in DSDT
[   27.216850] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   27.324244] ACPI: Interpreter enabled
[   27.324246] ACPI: (supports S0 S1 S3 S4 S5)
[   27.324262] ACPI: Using IOAPIC for interrupt routing
[   27.333184] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   27.333285] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.333300] PCI: Probing PCI hardware (bus 00)
[   27.335016] PCI: Transparent bridge - 0000:00:1e.0
[   27.335079] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.335211] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   27.335301] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   27.335381] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   27.335458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   27.335536] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   27.372355] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   27.372468] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   27.372578] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   27.372688] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   27.372797] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   27.372908] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   27.373017] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   27.373128] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   27.373226] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.373236] pnp: PnP ACPI init
[   27.373242] ACPI: bus type pnp registered
[   27.375782] pnp: PnP ACPI: found 13 devices
[   27.375784] ACPI: ACPI bus type pnp unregistered
[   27.375787] PnPBIOS: Disabled by ACPI PNP
[   27.375822] PCI: Using ACPI for IRQ routing
[   27.375824] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.391832] NET: Registered protocol family 8
[   27.391833] NET: Registered protocol family 20
[   27.391872] pnp: 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   27.391880] pnp: 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   27.391882] pnp: 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   27.391885] pnp: 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[   27.391887] pnp: 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[   27.391892] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   27.391894] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   27.391898] pnp: 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[   27.391901] Time: tsc clocksource has been installed.
[   27.391904] pnp: 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   27.391906] pnp: 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   27.391908] pnp: 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   27.391911] pnp: 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
[   27.391914] Switched to high resolution mode on CPU 0
[   27.391981] Switched to high resolution mode on CPU 1
[   27.422149] PCI: Bridge: 0000:00:1c.0
[   27.422152]   IO window: e000-efff
[   27.422156]   MEM window: f8000000-fbefffff
[   27.422160]   PREFETCH window: f0000000-f6ffffff
[   27.422164] PCI: Bridge: 0000:00:1c.2
[   27.422165]   IO window: disabled.
[   27.422170]   MEM window: f7f00000-f7ffffff
[   27.422173]   PREFETCH window: disabled.
[   27.422177] PCI: Bridge: 0000:00:1c.3
[   27.422180]   IO window: d000-dfff
[   27.422184]   MEM window: f7e00000-f7efffff
[   27.422187]   PREFETCH window: disabled.
[   27.422191] PCI: Bridge: 0000:00:1c.4
[   27.422194]   IO window: c000-cfff
[   27.422198]   MEM window: f7d00000-f7dfffff
[   27.422201]   PREFETCH window: disabled.
[   27.422206] PCI: Bridge: 0000:00:1e.0
[   27.422207]   IO window: disabled.
[   27.422211]   MEM window: fbf00000-fbffffff
[   27.422214]   PREFETCH window: disabled.
[   27.422236] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.422241] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.422257] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 17
[   27.422262] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   27.422279] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[   27.422283] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   27.422299] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   27.422303] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   27.422313] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   27.422321] NET: Registered protocol family 2
[   27.467817] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.467864] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   27.468378] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   27.468558] TCP: Hash tables configured (established 131072 bind 65536)
[   27.468561] TCP reno registered
[   27.483894] checking if image is initramfs... it is
[   28.026328] Freeing initrd memory: 7065k freed
[   28.026794] audit: initializing netlink socket (disabled)
[   28.026805] audit(1219418657.608:1): initialized
[   28.026878] highmem bounce pool size: 64 pages
[   28.028392] VFS: Disk quotas dquot_6.5.1
[   28.028428] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   28.028497] io scheduler noop registered
[   28.028499] io scheduler anticipatory registered
[   28.028500] io scheduler deadline registered
[   28.028511] io scheduler cfq registered (default)
[   28.028525] Boot video device is 0000:00:02.0
[   28.228484] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.228523] assign_interrupt_mode Found MSI capability
[   28.228526] Allocate Port Service[0000:00:1c.0:pcie00]
[   28.228550] Allocate Port Service[0000:00:1c.0:pcie02]
[   28.228619] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   28.228658] assign_interrupt_mode Found MSI capability
[   28.228660] Allocate Port Service[0000:00:1c.2:pcie00]
[   28.228683] Allocate Port Service[0000:00:1c.2:pcie02]
[   28.228752] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   28.228791] assign_interrupt_mode Found MSI capability
[   28.228793] Allocate Port Service[0000:00:1c.3:pcie00]
[   28.228816] Allocate Port Service[0000:00:1c.3:pcie02]
[   28.228887] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   28.228926] assign_interrupt_mode Found MSI capability
[   28.228928] Allocate Port Service[0000:00:1c.4:pcie00]
[   28.228951] Allocate Port Service[0000:00:1c.4:pcie02]
[   28.229072] isapnp: Scanning for PnP cards...
[   28.581948] isapnp: No Plug & Play device found
[   28.597853] Real Time Clock Driver v1.12ac
[   28.598000] hpet_resources: 0xfed00000 is busy
[   28.598039] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.598903] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.599001] input: Macintosh mouse button emulation as /class/input/input0
[   28.599070] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   28.601075] i8042.c: Detected active multiplexing controller, rev 1.1.
[   28.602320] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.602324] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   28.602326] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   28.602331] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   28.602332] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   28.602458] mice: PS/2 mouse device common for all mice
[   28.602612] EISA: Probing bus 0 at eisa.0
[   28.602639] EISA: Detected 0 cards.
[   28.602704] TCP cubic registered
[   28.602713] NET: Registered protocol family 1
[   28.602730] Using IPI No-Shortcut mode
[   28.602870]   Magic number: 4:630:437
[   28.603091] Freeing unused kernel memory: 364k freed
[   28.639226] input: AT Translated Set 2 keyboard as /class/input/input1
[   29.769313] AppArmor: AppArmor initialized<5>audit(1219418659.108:2):  type=1505 info="AppArmor initialized" pid=1244
[   29.775604] fuse init (API version 7.8)
[   29.779136] Failure registering capabilities with primary security module.
[   29.813228] ACPI: SSDT 7F7C00E0, 0320 (r1    AMI   CPU1PM        1 INTL 20060113)
[   29.813543] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   29.813547] ACPI: Processor [CPU1] (supports 8 throttling states)
[   29.813679] ACPI: SSDT 7F7C0400, 00E3 (r1    AMI   CPU2PM        1 INTL 20060113)
[   29.813956] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   29.813960] ACPI: Processor [CPU2] (supports 8 throttling states)
[   29.815766] ACPI: Thermal Zone [TZ00] (58 C)
[    3.548000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.552000] Time: hpet clocksource has been installed.
[    3.880000] usbcore: registered new interface driver usbfs
[    3.880000] usbcore: registered new interface driver hub
[    3.880000] usbcore: registered new device driver usb
[    3.880000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 17
[    3.880000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    3.880000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.880000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.880000] ehci_hcd 0000:00:1a.7: debug port 1
[    3.880000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    3.880000] ehci_hcd 0000:00:1a.7: irq 17, io mem 0xf7afbc00
[    3.884000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.884000] usb usb1: configuration #1 chosen from 1 choice
[    3.884000] hub 1-0:1.0: USB hub found
[    3.884000] hub 1-0:1.0: 4 ports detected
[    3.888000] USB Universal Host Controller Interface driver v3.0
[    3.972000] SCSI subsystem initialized
[    3.976000] libata version 2.21 loaded.
[    3.988000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.988000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.988000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.988000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.988000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.988000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.988000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf7afb800
[    3.992000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.992000] usb usb2: configuration #1 chosen from 1 choice
[    3.992000] hub 2-0:1.0: USB hub found
[    3.992000] hub 2-0:1.0: 6 ports detected
[    4.096000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.096000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    4.096000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.096000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.096000] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[    4.096000] usb usb3: configuration #1 chosen from 1 choice
[    4.096000] hub 3-0:1.0: USB hub found
[    4.096000] hub 3-0:1.0: 2 ports detected
[    4.200000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 20
[    4.200000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    4.200000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.200000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.200000] uhci_hcd 0000:00:1a.1: irq 20, io base 0x0000b880
[    4.200000] usb usb4: configuration #1 chosen from 1 choice
[    4.200000] hub 4-0:1.0: USB hub found
[    4.200000] hub 4-0:1.0: 2 ports detected
[    4.304000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    4.304000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.304000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.304000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    4.304000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000b080
[    4.304000] usb usb5: configuration #1 chosen from 1 choice
[    4.304000] hub 5-0:1.0: USB hub found
[    4.304000] hub 5-0:1.0: 2 ports detected
[    4.408000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[    4.408000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.408000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.408000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.408000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000b400
[    4.408000] usb usb6: configuration #1 chosen from 1 choice
[    4.408000] hub 6-0:1.0: USB hub found
[    4.408000] hub 6-0:1.0: 2 ports detected
[    4.512000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[    4.512000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.512000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.512000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.512000] uhci_hcd 0000:00:1d.2: irq 17, io base 0x0000b480
[    4.512000] usb usb7: configuration #1 chosen from 1 choice
[    4.512000] hub 7-0:1.0: USB hub found
[    4.512000] hub 7-0:1.0: 2 ports detected
[    4.616000] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.668000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[fbffe800-fbffefff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.672000] ahci 0000:00:1f.2: version 2.2
[    4.672000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 18 (level, low) -> IRQ 17
[    5.676000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    5.676000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    5.676000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.676000] scsi0 : ahci
[    5.676000] scsi1 : ahci
[    5.676000] scsi2 : ahci
[    5.676000] ata1: SATA max UDMA/133 cmd 0xf8862100 ctl 0x00000000 bmdma 0x00000000 irq 17
[    5.676000] ata2: SATA max UDMA/133 cmd 0xf8862180 ctl 0x00000000 bmdma 0x00000000 irq 17
[    5.676000] ata3: SATA max UDMA/133 cmd 0xf8862200 ctl 0x00000000 bmdma 0x00000000 irq 17
[    5.912000] usb 2-6: new high speed USB device using ehci_hcd and address 3
[    5.952000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180003a9afe1]
[    6.060000] usb 2-6: configuration #1 chosen from 1 choice
[    6.164000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.208000] ata1.00: ATA-8: WDC WD2500BEVS-22UST0, 01.01A01, max UDMA/133
[    6.208000] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.208000] ata1.00: configured for UDMA/133
[    6.300000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    6.480000] usb 3-1: configuration #1 chosen from 1 choice
[    6.524000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.728000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    6.836000] ata3: SATA link down (SStatus 0 SControl 300)
[    6.836000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-2 01.0 PQ: 0 ANSI: 5
[    6.836000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 18
[    6.888000] usb 4-2: configuration #1 chosen from 1 choice
[    7.160000] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    7.404000] usb 7-1: configuration #1 chosen from 1 choice
[    7.564000] usbcore: registered new interface driver libusual
[    7.568000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    7.568000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    7.568000] Initializing USB Mass Storage driver...
[    7.568000] scsi3 : SCSI emulation for USB Mass Storage devices
[    7.568000] usb-storage: device found at 2
[    7.568000] usb-storage: waiting for device to settle before scanning
[    7.568000] usbcore: registered new interface driver usb-storage
[    7.568000] USB Mass Storage support registered.
[    7.840000] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[    7.840000] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    7.840000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    7.840000] scsi4 : ahci
[    7.840000] ata4: SATA max UDMA/133 cmd 0xf88b8100 ctl 0x00000000 bmdma 0x00000000 irq 18
[    8.164000] ata4: SATA link down (SStatus 0 SControl 300)
[    8.164000] ata_piix 0000:00:1f.1: version 2.11
[    8.164000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 18
[    8.164000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    8.164000] scsi5 : ata_piix
[    8.164000] scsi6 : ata_piix
[    8.164000] ata5: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    8.164000] ata6: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    8.168000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    8.168000] sd 0:0:0:0: [sda] Write Protect is off
[    8.168000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.168000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.168000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    8.168000] sd 0:0:0:0: [sda] Write Protect is off
[    8.168000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.168000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.168000]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    8.244000] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.244000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.484000] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WR02, max UDMA/33
[    8.536000] Attempting manual resume
[    8.536000] swsusp: Resume From Partition 8:5
[    8.536000] PM: Checking swsusp image.
[    8.536000] PM: Resume from disk failed.
[    8.584000] kjournald starting.  Commit interval 5 seconds
[    8.584000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.656000] ata5.00: configured for UDMA/33
[    8.656000] ata6: port disabled. ignoring.
[    8.660000] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WR02 PQ: 0 ANSI: 5
[    8.660000] scsi 5:0:0:0: Attached scsi generic sg1 type 5
[   12.576000] usb-storage: device scan complete
[   12.576000] scsi 3:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   12.580000] scsi 3:0:0:0: Attached scsi generic sg2 type 5
[   15.564000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.640000] agpgart: Detected an Intel 965GM Chipset.
[   15.644000] agpgart: Detected 7676K stolen memory.
[   15.656000] agpgart: AGP aperture is 256M @ 0xd0000000
[   15.756000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.764000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.772000] input: PC Speaker as /class/input/input2
[   16.120000] ieee80211_crypt: registered algorithm 'NULL'
[   16.204000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.204000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.252000] Bluetooth: Core ver 2.11
[   16.252000] NET: Registered protocol family 31
[   16.252000] Bluetooth: HCI device and connection manager initialized
[   16.252000] Bluetooth: HCI socket layer initialized
[   16.288000] sdhci: Secure Digital Host Controller Interface driver
[   16.288000] sdhci: Copyright(c) Pierre Ossman
[   16.288000] sdhci: SDHCI controller found at 0000:06:01.1 [1180:0822] (rev 22)
[   16.288000] ACPI: PCI Interrupt 0000:06:01.1[B] -> GSI 17 (level, low) -> IRQ 20
[   16.288000] mmc0: SDHCI at 0xfbfff400 irq 20 DMA
[   16.308000] Bluetooth: HCI USB driver ver 2.9
[   16.312000] usbcore: registered new interface driver hci_usb
[   16.324000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.324000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   16.324000] sky2 0000:01:00.0: v1.18 addr 0xf7dfc000 irq 16 Yukon-EC Ultra (0xb4) rev 2
[   16.324000] sky2 eth0: addr 00:1d:60:73:a7:70
[   16.336000] usbcore: registered new interface driver usbserial
[   16.336000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   16.336000] usbcore: registered new interface driver usbserial_generic
[   16.336000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   16.344000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[   16.344000] option 4-2:1.0: GSM modem (1-port) converter detected
[   16.344000] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
[   16.344000] option 4-2:1.1: GSM modem (1-port) converter detected
[   16.344000] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1
[   16.344000] usbcore: registered new interface driver option
[   16.344000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[   16.360000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp
[   16.360000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   16.360000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 17
[   16.360000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   16.360000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.376000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   16.376000] Uniform CD-ROM driver Revision: 3.20
[   16.376000] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   16.396000] sr1: scsi-1 drive
[   16.400000] sr 3:0:0:0: Attached scsi CD-ROM sr1
[   16.464000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   16.464000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   16.620000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   16.660000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   16.708000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   17.268000] lp: driver loaded but no devices found
[   17.324000] Adding 6056464k swap on /dev/sda5.  Priority:-1 extents:1 across:6056464k
[   17.740000] EXT3 FS on sda6, internal journal
[   18.220000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   18.508000] kjournald starting.  Commit interval 5 seconds
[   18.508000] EXT3 FS on sda1, internal journal
[   18.508000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.560000] kjournald starting.  Commit interval 5 seconds
[   18.560000] EXT3 FS on sda7, internal journal
[   18.560000] EXT3-fs: mounted filesystem with ordered data mode.
[   19.156000] ACPI: Battery Slot [BAT0] (battery present)
[   19.268000] ACPI: AC Adapter [AC0] (on-line)
[   19.280000] Asus Laptop ACPI Extras version 0.30
[   19.280000]   Error calling BSTS
[   19.280000]   unsupported model Z37E, trying default values
[   19.280000]   send /proc/acpi/dsdt to the developers
[   19.320000] No dock devices found.
[   19.368000] input: Power Button (FF) as /class/input/input4
[   19.368000] ACPI: Power Button (FF) [PWRF]
[   19.368000] input: Lid Switch as /class/input/input5
[   19.368000] ACPI: Lid Switch [LID]
[   19.368000] input: Sleep Button (CM) as /class/input/input6
[   19.368000] ACPI: Sleep Button (CM) [SLPB]
[   19.368000] input: Power Button (CM) as /class/input/input7
[   19.368000] ACPI: Power Button (CM) [PWRB]
[   19.428000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.344000] Failure registering capabilities with primary security module.
[   20.552000] ppdev: user-space parallel port driver
[   20.684000] sky2 eth0: enabling interface
[   20.780000] audit(1219418676.386:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5297 profile="/usr/sbin/cupsd"
[   20.820000] apm: BIOS not found.
[   20.996000] cdrom: This disc doesn't have any tracks I recognize!
[   21.140000] Bluetooth: L2CAP ver 2.8
[   21.140000] Bluetooth: L2CAP socket layer initialized
[   21.256000] Bluetooth: RFCOMM socket layer initialized
[   21.256000] Bluetooth: RFCOMM TTY layer initialized
[   21.256000] Bluetooth: RFCOMM ver 1.8
[   25.464000] [drm] Initialized drm 1.1.0 20060810
[   25.472000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.472000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   76.192000] ISO 9660 Extensions: Microsoft Joliet Level 1
[   76.196000] ISOFS: changing to secondary root
[   87.164000] NET: Registered protocol family 17
[   90.676000] NET: Registered protocol family 10
[   90.676000] lo: Disabled Privacy Extensions
[   90.676000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  459.556000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  460.000000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  470.192000] eth1: no IPv6 routers present
[  541.996000] ieee80211_crypt: registered algorithm 'TKIP'
[  543.976000] ieee80211_crypt: registered algorithm 'WEP'
[  586.012000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  586.160000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  596.484000] eth1: no IPv6 routers present
[  619.508000] eth1: no IPv6 routers present
[ 1255.700000] usb 4-2: USB disconnect, address 2
[ 1255.700000] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 1255.700000] option 4-2:1.0: device disconnected
[ 1255.700000] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1255.700000] option 4-2:1.1: device disconnected
[ 1268.316000] usb 4-1: new full speed USB device using uhci_hcd and address 3
[ 1268.476000] usb 4-1: configuration #1 chosen from 1 choice
[ 1268.480000] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1268.480000] usb-storage: device found at 3
[ 1268.480000] usb-storage: waiting for device to settle before scanning
[ 1269.576000] usb 4-1: USB disconnect, address 3
[ 1270.824000] usb 4-1: new full speed USB device using uhci_hcd and address 4
[ 1270.984000] usb 4-1: configuration #1 chosen from 1 choice
[ 1270.988000] option 4-1:1.0: GSM modem (1-port) converter detected
[ 1270.988000] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 1270.992000] option 4-1:1.1: GSM modem (1-port) converter detected
[ 1270.992000] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 1270.992000] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1270.992000] usb-storage: device found at 4
[ 1270.992000] usb-storage: waiting for device to settle before scanning
[ 1275.992000] usb-storage: device scan complete
[ 1275.996000] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1276.028000] sr1: scsi-1 drive
[ 1276.028000] sr 8:0:0:0: Attached scsi CD-ROM sr1
[ 1276.028000] sr 8:0:0:0: Attached scsi generic sg2 type 5
[ 1282.792000] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 1282.796000] ISOFS: changing to secondary root
[ 1308.636000] usbcore: deregistering interface driver usb-storage
[ 1560.492000] end_request: I/O error, dev sr0, sector 0
[ 1560.492000] Buffer I/O error on device sr0, logical block 0
[ 1561.100000] end_request: I/O error, dev sr0, sector 0
[ 1561.100000] Buffer I/O error on device sr0, logical block 0
[ 1561.712000] end_request: I/O error, dev sr0, sector 0
[ 1561.712000] Buffer I/O error on device sr0, logical block 0
[ 1562.300000] end_request: I/O error, dev sr0, sector 0
[ 1562.300000] Buffer I/O error on device sr0, logical block 0
[ 1562.888000] end_request: I/O error, dev sr0, sector 0
[ 1562.888000] Buffer I/O error on device sr0, logical block 0
[ 1563.480000] end_request: I/O error, dev sr0, sector 0
[ 1563.480000] Buffer I/O error on device sr0, logical block 0

```

lsusb: 
```
Bus 004 Device 006: ID 12d1:1003  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 147e:2016  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 05e3:0503 Genesys Logic, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

(under Hardy, this is correctly identified as a Huawei modem, albeit as an E220)

ls -la /dev/ttyUSB*:
```
crw-rw---- 1 root dialout 188, 0 2008-08-22 17:24 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2008-08-22 17:27 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2008-08-22 17:24 /dev/ttyUSB2

```

(That is the first time all day I've got three entries for ttyUSB*!)

wvdial.conf:
```
[Dialer Defaults]
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99***1#
Modem = /dev/ttyUSB0
Username = user
Dial Command = ATDT
Password = pass
Baud = 460800
Init3 = AT+CGDCONT=1,"IP","general.t-mobile.uk"
Stupid Mode=1
```

wvdial:
```
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT+CGDCONT=1,"IP","general.t-mobile.uk"
WvDial Modem<*1>: AT+CGDCONT=1,"IP","general.t-mobile.uk"
WvDial Modem<*1>: ERROR
WvDial<Err>: Bad init string.
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT+CGDCONT=1,"IP","general.t-mobile.uk"
WvDial Modem<*1>: AT+CGDCONT=1,"IP","general.t-mobile.uk"
WvDial Modem<*1>: ERROR
WvDial<Err>: Bad init string.

```

I have also loaded version 1.0 of the vodafone software, and tried loading various beta versions with Hardy. All of them have the same result: the program starts, then hangs on the "authenticating" step.

One final thing: I'm aware of the various shell scripts, kernel mods, etc, connected with the Huawei, but I don't know the difference between them, what they do, or even if they're necessary any more, so I haven't loaded any of them. If I need to be using one, please explain which, and how to load it.

Thanks very much indeed! P

---

### Post by GeorgeVita on 2008-08-23
Hi, I have a Huawei E170, running on Ubundu 8.04 with just editing the wvdial.conf. As I saw on your post you have a good wvdial.conf file but the "ERROR" comes on the: Init3 = AT+CGDCONT=1,"IP","general.t-mobile.uk"

At first rename the above line to Init4 because you have another Init3 line (which now not executed as replaced by the last one).

Are you sure for the APN name "general.t-mobile.uk" ?

AND ALSO what about SIM-PIN check? Have you release this check from the SIM?

The AT+CGDCONT... command responds with ERROR when you have not given PIN if must given!

---

### Post by GeorgeVita on 2008-08-23
Additionally I would like to propose the following **wvdial.conf** for **Ubuntu 8.04** (default setup & updates).

From a terminal window you have to: **sudo gedit /etc/wvdial.conf**
Edit it or copy the following lines and SAVE. Change the PIN# if you are using the SIM-PIN check.

[B][Dialer Defaults]
New PPPD = yes
Dial Command = ATDT
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0

[Dialer hspa]
Phone = *99***1#
Stupid Mode = 1
Init3 = AT+CGDCONT=1,"IP","general.t-mobile.uk"

[Dialer myPIN]
Init4 = AT+CPIN=1234
[/B]
Reboot without modem, insert modem on USB port, from a terminal window lsusb and when you see "Huawei..." you can dial. If you have a PIN check first dial: **sudo wvdial myPIN** (you have to replace the 1234 to your PIN#).
Then dial with: **sudo wvdial hspa**
Disconnect by pressing: **CTRL-C** at the same terminal window.

In any error post me a copy of the terminal messages.

Regards
George

---

### Post by TDFlanders on 2008-08-24
Hi there,

I had a similar problem. None of the scripts ever worked for me. Try NetworkManager 0.7.0 . It is standard in Intrepid. You can find a how to here:

[http://ubuntuforums.org/showthread.php?t=848135](http://ubuntuforums.org/showthread.php?t=848135)

and here:

[https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

After that it should just work. I also tried two other packages that are only available through intrepid.

USBprog

[http://developer.berlios.de/projects/usbprog/](http://developer.berlios.de/projects/usbprog/)

and also:

D-Feet D-Bus Debugger

[http://hosted.fedoraproject.org/projects/d-feet](http://hosted.fedoraproject.org/projects/d-feet)

If you install USBprog and click on cache and download all, then a whole bunch of firmware should be downloaded. After I did this I clicked on auto GSM in network-manager 0.7.0 and it worked without ever having to configure anything.

The D-Feet Debugger I never used.

Also take a look at:

[http://www.huawei.com/mobileweb/en/doc/list.do?type=-1&id=736](http://www.huawei.com/mobileweb/en/doc/list.do?type=-1&id=736)

You can download the latest drivers and run them under Windows Wireless Drivers. It could be that your flash and play modem will work that way if you open the popup stuff with wine or wine programs bootloader.

Cheers,

Thomas

---

### Post by mcdee on 2008-08-28
> **TDFlanders said:**
> Hi there,

I had a similar problem. None of the scripts ever worked for me. Try NetworkManager 0.7.0 . It is standard in Intrepid. You can find a how to here:

[http://ubuntuforums.org/showthread.php?t=848135](http://ubuntuforums.org/showthread.php?t=848135)

and here:

[https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

After that it should just work.



Ah, the good old "should just work" :mad:

Anyway, after installing NetworkManager 0.7.0 as per above it didn't just work for me.  So here is a step-by-step guide.

[LIST=1]
[*]After installing the new NetworkManager as above, reboot
[*]After logging in, right-click on the network manager applet in the system tray
[*]Select 'Edit Connections..."
[*]Select the 'Mobile Broadband' tab
[*]Hit the 'Add' button
[*]Select 'Create a GSM connection' and hit 'OK'
[*]Change the 'Connection name' field to 'T-Mobile' (without the quotes)
[*]Change the 'Username' field to 'user' (again without the quotes)
[*]Change the 'Password' field to 'pass' (again without the quotes)
[*]Change the 'APN' field to 'general.t-mobile.uk' (again without the quotes)
[*]Hit 'OK'
[*]Plug in your modem
[*]Left-click on the network manager applet in the system tray, select the 'T-Mobile' option
[*]That's it!
[/LIST]

At least, that worked for me.

Cheers,
Jim.

---

### Post by luc514 on 2008-10-21
Hey everyone,

One quick note, I called T-Mobile when the stick started to give me this hassle, and they suggested pulling the SIM and re-inserting it.  It worked after that.

Might be worth a try.

-Luc

---

