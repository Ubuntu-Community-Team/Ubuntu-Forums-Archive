---
title: "My comp STILL CRASHING"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by smileyacid on 2010-05-22
My computer crashed many times before after installing new Ubu 10.4 (lucid) it would show RED + BLUE blocks whilst booting + crashing so every one thought it video related i took some ones advice by running a few checks ect + thought the problem was fixed but it still keeps on reacuring !

PLEASE HELP !!!

-smiley

---

### Post by smileyacid on 2010-05-22
If it helps the computer crashes whilst on + quite often during use of Ffox
it is a Dell Optiplex GX260, the graphics card is a built in:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
jamie@jamie-desktop:~$

processor: intel pentium4 1.8 GHz
Memory (RAM): 2 GiB

Hope this helps a little if not would it be usefull to post log in VAR folder? 

-smiley

---

### Post by ubudog on 2010-05-22
Did you use update manager to upgrade or did you do a clean install?

---

### Post by gandaran on 2010-05-22
>  it would show RED + BLUE blocks whilst booting 
install startup manager then use it to change boot resolution, about the crashes sorry cannot help.

---

### Post by smileyacid on 2010-05-22
It is a fresh install (NO upgrade)

-smiley

im a win PC and i stole that idea

---

### Post by ubudog on 2010-05-22
> **smileyacid said:**
> It is a fresh install (NO upgrade)

-smiley

im a win PC and i stole that idea

Hmm.  Open a terminal and type the following.  Post the results here.  ```
dmesg
```

---

### Post by smileyacid on 2010-05-22
```
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10441940 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f771)
[    0.000000] Memory: 2043344k/2088388k available (4673k kernel code, 43448k reserved, 2121k data, 656k init, 1179084k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590653 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590653   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1793.082 MHz processor.
[    0.008011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3586.16 BogoMIPS (lpj=7172328)
[    0.008047] Security Framework initialized
[    0.008102] AppArmor: AppArmor initialized
[    0.008118] Mount-cache hash table entries: 512
[    0.008416] Initializing cgroup subsys ns
[    0.008426] Initializing cgroup subsys cpuacct
[    0.008435] Initializing cgroup subsys memory
[    0.008451] Initializing cgroup subsys devices
[    0.008457] Initializing cgroup subsys freezer
[    0.008462] Initializing cgroup subsys net_cls
[    0.008508] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.008516] CPU: L2 cache: 512K
[    0.008520] CPU: Hyper-Threading is disabled
[    0.008529] mce: CPU supports 4 MCE banks
[    0.008549] CPU0: Thermal monitoring enabled (TM1)
[    0.008573] Performance Events: no PMU driver, software events only.
[    0.008586] Checking 'hlt' instruction... OK.
[    0.025514] SMP alternatives: switching to UP code
[    0.043082] ACPI: Core revision 20090903
[    0.081879] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.081890] ftrace: allocating 21771 entries in 43 pages
[    0.084147] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.084474] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.126069] CPU0: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 04
[    0.128001] Brought up 1 CPUs
[    0.128001] Total of 1 processors activated (3586.16 BogoMIPS).
[    0.128001] CPU0 attaching NULL sched-domain.
[    0.128001] devtmpfs: initialized
[    0.128001] regulator: core version 0.5
[    0.128001] Time: 15:50:10  Date: 05/22/10
[    0.128001] NET: Registered protocol family 16
[    0.128001] EISA bus registered
[    0.128001] ACPI: bus type pci registered
[    0.145003] PCI: PCI BIOS revision 2.10 entry at 0xfbdea, last bus=1
[    0.145008] PCI: Using configuration type 1 for base access
[    0.146855] bio: create slab <bio-0> at 0
[    0.147578] ACPI: EC: Look up EC in DSDT
[    0.180762] ACPI: Interpreter enabled
[    0.180783] ACPI: (supports S0 S1 S3 S4 S5)
[    0.180827] ACPI: Using IOAPIC for interrupt routing
[    0.217013] ACPI: No dock devices found.
[    0.217881] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.217957] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.218065] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.218076] pci 0000:00:02.0: reg 14 32bit mmio: [0xff680000-0xff6fffff]
[    0.218223] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.218296] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.218369] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.218452] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa00800-0xffa00bff]
[    0.218527] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.218535] pci 0000:00:1d.7: PME# disabled
[    0.218606] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.218608] * this clock source is slow. If you are sure your timer does not have
[    0.218611] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.218668] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.218675] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.218709] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.218720] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.218731] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.218741] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.218752] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.218763] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.218834] pci 0000:00:1f.3: reg 20 io port: [0xdc80-0xdc9f]
[    0.218896] pci 0000:00:1f.5: reg 10 io port: [0xd800-0xd8ff]
[    0.218906] pci 0000:00:1f.5: reg 14 io port: [0xdc40-0xdc7f]
[    0.218917] pci 0000:00:1f.5: reg 18 32bit mmio: [0xffa00400-0xffa005ff]
[    0.218927] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xffa00000-0xffa000ff]
[    0.218969] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.218976] pci 0000:00:1f.5: PME# disabled
[    0.219068] pci 0000:01:0c.0: reg 10 32bit mmio: [0xff8e0000-0xff8fffff]
[    0.219084] pci 0000:01:0c.0: reg 18 io port: [0xecc0-0xecff]
[    0.219140] pci 0000:01:0c.0: PME# supported from D0 D3hot D3cold
[    0.219147] pci 0000:01:0c.0: PME# disabled
[    0.219191] pci 0000:00:1e.0: transparent bridge
[    0.219198] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.219206] pci 0000:00:1e.0: bridge 32bit mmio: [0xff800000-0xff9fffff]
[    0.219222] pci_bus 0000:00: on NUMA node 0
[    0.219230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.219679] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.322853] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.323228] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.323592] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.323956] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.324326] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.324688] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.325050] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.325416] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.325651] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.325664] vgaarb: loaded
[    0.325905] SCSI subsystem initialized
[    0.326034] libata version 3.00 loaded.
[    0.326172] usbcore: registered new interface driver usbfs
[    0.326203] usbcore: registered new interface driver hub
[    0.326254] usbcore: registered new device driver usb
[    0.326496] ACPI: WMI: Mapper loaded
[    0.326500] PCI: Using ACPI for IRQ routing
[    0.326725] NetLabel: Initializing
[    0.326730] NetLabel:  domain hash size = 128
[    0.326733] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.326756] NetLabel:  unlabeled traffic allowed by default
[    0.326819] Switching to clocksource tsc
[    0.328001] AppArmor: AppArmor Filesystem Enabled
[    0.328001] pnp: PnP ACPI init
[    0.328001] ACPI: bus type pnp registered
[    0.353279] pnp 00:0a: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.353288] pnp 00:0a: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.354153] pnp: PnP ACPI: found 11 devices
[    0.354158] ACPI: ACPI bus type pnp unregistered
[    0.354166] PnPBIOS: Disabled by ACPI PNP
[    0.354189] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.354197] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    0.354203] system 00:00: iomem range 0x1000000-0x7f770fff could not be reserved
[    0.354209] system 00:00: iomem range 0xc0000-0xcbfff could not be reserved
[    0.354215] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.354222] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.354227] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.354233] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.354239] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
[    0.354257] system 00:0a: ioport range 0xc00-0xc7f has been reserved
[    0.389179] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.389187] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.389197] pci 0000:00:1e.0:   MEM window: 0xff800000-0xff9fffff
[    0.389204] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.389226] pci 0000:00:1e.0: setting latency timer to 64
[    0.389236] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.389241] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.389246] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.389251] pci_bus 0000:01: resource 1 mem: [0xff800000-0xff9fffff]
[    0.389256] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.389260] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.389327] NET: Registered protocol family 2
[    0.389517] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.390186] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.391492] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.392357] TCP: Hash tables configured (established 131072 bind 65536)
[    0.392364] TCP reno registered
[    0.392631] NET: Registered protocol family 1
[    0.392678] pci 0000:00:02.0: Boot video device
[    0.392968] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    0.392972] Simple Boot Flag at 0x7a set to 0x1
[    0.393174] cpufreq-nforce2: No nForce2 chipset.
[    0.393231] Scanning for low memory corruption every 60 seconds
[    0.393448] audit: initializing netlink socket (disabled)
[    0.393471] type=2000 audit(1274543410.393:1): initialized
[    0.410745] Trying to unpack rootfs image as initramfs...
[    0.429562] highmem bounce pool size: 64 pages
[    0.429575] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.437209] VFS: Disk quotas dquot_6.5.2
[    0.437383] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.438569] fuse init (API version 7.13)
[    0.438742] msgmni has been set to 1690
[    0.445464] alg: No test for stdrng (krng)
[    0.445660] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.445667] io scheduler noop registered
[    0.445671] io scheduler anticipatory registered
[    0.445675] io scheduler deadline registered
[    0.445753] io scheduler cfq registered (default)
[    0.445937] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.445988] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.446155] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.446170] ACPI: Power Button [VBTN]
[    0.446263] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.446269] ACPI: Power Button [PWRF]
[    0.446603] processor LNXCPU:00: registered as cooling_device0
[    0.485619] isapnp: Scanning for PnP cards...
[    0.498079] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.498213] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.498816] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.500712] brd: module loaded
[    0.550250] loop: module loaded
[    0.550454] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.550657] ata_piix 0000:00:1f.1: version 2.13
[    0.550677] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.550694]   alloc irq_desc for 18 on node -1
[    0.550698]   alloc kstat_irqs on node -1
[    0.550712] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.550794] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.550971] scsi0 : ata_piix
[    0.551124] scsi1 : ata_piix
[    0.551190] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.551196] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.551858] Fixed MDIO Bus: probed
[    0.551928] PPP generic driver version 2.4.2
[    0.552026] tun: Universal TUN/TAP device driver, 1.6
[    0.552030] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.552191] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.552227]   alloc irq_desc for 23 on node -1
[    0.552232]   alloc kstat_irqs on node -1
[    0.552243] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.552270] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.552277] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.552347] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.552401] ehci_hcd 0000:00:1d.7: debug port 1
[    0.556284] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.561735] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa00800
[    0.581838] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.582100] usb usb1: configuration #1 chosen from 1 choice
[    0.582160] hub 1-0:1.0: USB hub found
[    0.582181] hub 1-0:1.0: 6 ports detected
[    0.582298] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.582330] uhci_hcd: USB Universal Host Controller Interface driver
[    0.582418]   alloc irq_desc for 16 on node -1
[    0.582423]   alloc kstat_irqs on node -1
[    0.582436] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.582453] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.582460] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.582536] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.582586] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    0.582751] usb usb2: configuration #1 chosen from 1 choice
[    0.582802] hub 2-0:1.0: USB hub found
[    0.582820] hub 2-0:1.0: 2 ports detected
[    0.582894]   alloc irq_desc for 19 on node -1
[    0.582899]   alloc kstat_irqs on node -1
[    0.582908] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.582920] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.582926] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.582989] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.583029] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    0.583182] usb usb3: configuration #1 chosen from 1 choice
[    0.583232] hub 3-0:1.0: USB hub found
[    0.583249] hub 3-0:1.0: 2 ports detected
[    0.583323] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.583334] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.583340] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.583403] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.583445] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    0.583623] usb usb4: configuration #1 chosen from 1 choice
[    0.583679] hub 4-0:1.0: USB hub found
[    0.583696] hub 4-0:1.0: 2 ports detected
[    0.583848] PNP: PS/2 Controller [PNP0f13:MOU] at 0x60,0x64 irq 12
[    0.583853] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.591474] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.591490] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.591788] mice: PS/2 mouse device common for all mice
[    0.592018] rtc_cmos 00:05: RTC can wake from S4
[    0.592093] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.592124] rtc0: alarms up to one day, 242 bytes nvram
[    0.592355] device-mapper: uevent: version 1.0.3
[    0.597854] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.597987] device-mapper: multipath: version 1.1.0 loaded
[    0.597993] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.598221] EISA: Probing bus 0 at eisa.0
[    0.598267] EISA: Detected 0 cards.
[    0.601416] cpuidle: using governor ladder
[    0.601423] cpuidle: using governor menu
[    0.602337] TCP cubic registered
[    0.602628] NET: Registered protocol family 10
[    0.603480] lo: Disabled Privacy Extensions
[    0.604046] NET: Registered protocol family 17
[    0.604149] Using IPI No-Shortcut mode
[    0.604342] PM: Resume from disk failed.
[    0.604363] registered taskstats version 1
[    0.604679]   Magic number: 10:26:842
[    0.604787] rtc_cmos 00:05: setting system clock to 2010-05-22 15:50:10 UTC (1274543410)
[    0.604794] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.604797] EDD information not available.
[    0.750181] ata2.00: ATAPI: HL-DT-STDVD-RAM GH22LP20, 1.04, max UDMA/66
[    0.750365] ata1.00: ATA-8: WDC WD1600AAJB-00J3A0, 01.03E01, max UDMA/133
[    0.750371] ata1.00: 312581808 sectors, multi 8: LBA48 
[    0.758125] ata2.00: configured for UDMA/66
[    0.766226] ata1.00: configured for UDMA/100
[    0.917163] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.125690] usb 1-1: configuration #1 chosen from 1 choice
[    1.179665] isapnp: No Plug & Play device found
[    1.179912] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AAJB-0 01.0 PQ: 0 ANSI: 5
[    1.180220] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.180514] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.180606] sd 0:0:0:0: [sda] Write Protect is off
[    1.180612] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.180660] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.181073]  sda:
[    1.182102] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22LP20 1.04 PQ: 0 ANSI: 5
[    1.188625] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.188635] Uniform CD-ROM driver Revision: 3.20
[    1.188854] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.188976] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.209325]  sda1 sda2 <
[    1.210882] Freeing initrd memory: 7774k freed
[    1.229377]  sda5 sda6 >
[    1.248300] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.248332] Freeing unused kernel memory: 656k freed
[    1.249499] Write protecting the kernel text: 4676k
[    1.249561] Write protecting the kernel read-only data: 1840k
[    1.293018] udev: starting version 151
[    1.408112] usb 1-5: new high speed USB device using ehci_hcd and address 5
[    1.542459] usb 1-5: configuration #1 chosen from 1 choice
[    1.652102] usb 1-6: new high speed USB device using ehci_hcd and address 6
[    1.689920] Initializing USB Mass Storage driver...
[    1.695517] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
[    1.695524] Copyright (c) 1999-2006 Intel Corporation.
[    1.695629] e1000 0000:01:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.699428] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.699767] usb-storage: device found at 2
[    1.699773] usb-storage: waiting for device to settle before scanning
[    1.700302] scsi5 : SCSI emulation for USB Mass Storage devices
[    1.700596] usb-storage: device found at 2
[    1.700600] usb-storage: waiting for device to settle before scanning
[    1.700644] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.701180] usbcore: registered new interface driver usb-storage
[    1.701188] USB Mass Storage support registered.
[    1.701656] usb-storage: device found at 5
[    1.701661] usb-storage: waiting for device to settle before scanning
[    1.715791] FDC 0 is a post-1991 82077
[    1.971443] e1000: 0000:01:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:08:74:18:aa:7b
[    1.993085] usb 1-6: configuration #1 chosen from 1 choice
[    2.005657] scsi7 : SCSI emulation for USB Mass Storage devices
[    2.007281] usb-storage: device found at 6
[    2.007287] usb-storage: waiting for device to settle before scanning
[    2.008518] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    2.154520] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.244037] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.420243] usb 3-1: configuration #1 chosen from 1 choice
[    2.660032] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    2.804050] usb 3-2: not running at top speed; connect to a high speed hub
[    2.832229] usb 3-2: configuration #1 chosen from 1 choice
[    2.835241] scsi8 : SCSI emulation for USB Mass Storage devices
[    2.835448] usb-storage: device found at 3
[    2.835452] usb-storage: waiting for device to settle before scanning
[    3.522352] Adding 2044920k swap on /dev/sda6.  Priority:-1 extents:1 across:2044920k 
[    4.001264] udev: starting version 151
[    5.175962] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    5.178241] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.247593] usbcore: registered new interface driver usbserial
[    5.248459] USB Serial support registered for generic
[    5.249342] usbcore: registered new interface driver usbserial_generic
[    5.249349] usbserial: USB Serial Driver core
[    5.273197] USB Serial support registered for GSM modem (1-port)
[    5.274030] option 1-1:1.0: GSM modem (1-port) converter detected
[    5.274564] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[    5.274593] option 1-1:1.1: GSM modem (1-port) converter detected
[    5.276833] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[    5.277021] usbcore: registered new interface driver option
[    5.277026] option: v0.7.2:USB Driver for GSM modems
[    5.297890] dell-wmi: No known WMI GUID found
[    5.426326] parport_pc 00:09: reported by Plug and Play ACPI
[    5.426387] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    5.464305] usbcore: registered new interface driver hiddev
[    5.481923] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    5.482398] generic-usb 0003:03F0:0024.0001: input,hidraw0: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:1d.1-1/input0
[    5.482507] usbcore: registered new interface driver usbhid
[    5.483320] usbhid: v2.6:USB HID core driver
[    5.637606] psmouse serio1: ID: 00 00 3c
[    5.693687] Linux agpgart interface v0.103
[    5.707972] ppdev: user-space parallel port driver
[    5.714555] lp0: using parport0 (interrupt-driven).
[    5.728231] logips2pp: Detected unknown logitech mouse model 8
[    5.766622] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    5.766973] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[    5.772735] intel_rng: FWH not detected
[    5.778132] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    5.989143] type=1505 audit(1274539815.883:2):  operation="profile_load" pid=407 name="/sbin/dhclient3"
[    5.990003] type=1505 audit(1274539815.883:3):  operation="profile_load" pid=407 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    5.990465] type=1505 audit(1274539815.883:4):  operation="profile_load" pid=407 name="/usr/lib/connman/scripts/dhclient-script"
[    6.285123] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input4
[    6.353766] [drm] Initialized drm 1.1.0 20060810
[    6.697730] usb-storage: device scan complete
[    6.699493] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[    6.703328] usb-storage: device scan complete
[    6.703977] usb-storage: device scan complete
[    6.704140] scsi 6:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[    6.706630] scsi 5:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[    6.716470] sr1: scsi-1 drive
[    6.716712] sr 4:0:0:0: Attached scsi CD-ROM sr1
[    6.716849] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    6.725860] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    6.728625] sd 5:0:0:0: Attached scsi generic sg4 type 0
[    6.744856] sd 6:0:0:0: [sdb] 3915776 512-byte logical blocks: (2.00 GB/1.86 GiB)
[    6.752996] sd 6:0:0:0: [sdb] Write Protect is off
[    6.753006] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    6.753012] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.759351] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.759414]  sdb: sdb1
[    6.763443] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    6.764638] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.764699] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    6.883069] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.883082] i915 0000:00:02.0: setting latency timer to 64
[    6.899521] [drm] set up 15M of stolen space
[    6.945395] [drm] initialized overlay support
[    7.100669] usb-storage: device scan complete
[    7.101241] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer Micro     8.01 PQ: 0 ANSI: 0 CCS
[    7.105235] sd 7:0:0:0: Attached scsi generic sg5 type 0
[    7.106482] sd 7:0:0:0: [sdd] 3907583 512-byte logical blocks: (2.00 GB/1.86 GiB)
[    7.106952] sd 7:0:0:0: [sdd] Write Protect is off
[    7.106959] sd 7:0:0:0: [sdd] Mode Sense: 45 00 00 08
[    7.106964] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[    7.109228] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[    7.109291]  sdd: sdd1
[    7.116353] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[    7.116429] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[    7.190902] fb0: inteldrmfb frame buffer device
[    7.190909] registered panic notifier
[    7.190924] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.449857] vga16fb: initializing
[    7.449868] vga16fb: mapped to 0xc00a0000
[    7.449878] vga16fb: not registering due to another framebuffer present
[    7.707926]   alloc irq_desc for 17 on node -1
[    7.707932]   alloc kstat_irqs on node -1
[    7.707945] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.708038] Intel ICH 0000:00:1f.5: setting latency timer to 64
[    7.834037] usb-storage: device scan complete
[    7.837015] scsi 8:0:0:0: Direct-Access     ACTIONS  HS USB FlashDisk 2.00 PQ: 0 ANSI: 0 CCS
[    7.841934] sd 8:0:0:0: Attached scsi generic sg6 type 0
[    7.848924] sd 8:0:0:0: [sde] 1971121 512-byte logical blocks: (1.00 GB/962 MiB)
[    7.853012] sd 8:0:0:0: [sde] Write Protect is off
[    7.853022] sd 8:0:0:0: [sde] Mode Sense: 00 c0 00 00
[    7.853028] sd 8:0:0:0: [sde] Assuming drive cache: write through
[    7.864977] sd 8:0:0:0: [sde] Assuming drive cache: write through
[    7.865042]  sde:
[    7.883332] sd 8:0:0:0: [sde] Assuming drive cache: write through
[    7.883392] sd 8:0:0:0: [sde] Attached SCSI removable disk
[    8.024431] Console: switching to colour frame buffer device 128x48
[    8.108031] intel8x0_measure_ac97_clock: measured 53621 usecs (2583 samples)
[    8.108038] intel8x0: clocking to 48000
[   11.015253] type=1505 audit(1274539820.907:5):  operation="profile_load" pid=736 name="/usr/share/gdm/guest-session/Xsession"
[   11.019499] type=1505 audit(1274539820.911:6):  operation="profile_replace" pid=739 name="/sbin/dhclient3"
[   11.020821] type=1505 audit(1274539820.915:7):  operation="profile_replace" pid=739 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.021313] type=1505 audit(1274539820.915:8):  operation="profile_replace" pid=739 name="/usr/lib/connman/scripts/dhclient-script"
[   11.213006] type=1505 audit(1274539821.107:9):  operation="profile_load" pid=740 name="/usr/bin/evince"
[   11.226361] type=1505 audit(1274539821.119:10):  operation="profile_load" pid=740 name="/usr/bin/evince-previewer"
[   11.235464] type=1505 audit(1274539821.127:11):  operation="profile_load" pid=740 name="/usr/bin/evince-thumbnailer"
[   11.374478] type=1505 audit(1274539821.267:12):  operation="profile_load" pid=806 name="/usr/lib/cups/backend/cups-pdf"
[   11.375509] type=1505 audit(1274539821.267:13):  operation="profile_load" pid=806 name="/usr/sbin/cupsd"
[   11.391632] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.492929] type=1505 audit(1274539821.387:14):  operation="profile_load" pid=808 name="/usr/sbin/mysqld-akonadi"
[   14.226973] PPP BSD Compression module registered
[   14.473782] PPP Deflate Compression module registered
[   42.377442] ISO 9660 Extensions: Microsoft Joliet Level 1
[   42.418851] ISOFS: changing to secondary root
jamie@jamie-desktop:~$
```

---

### Post by smileyacid on 2010-05-22
can you let me know what dmesg does ?

-smiley

---

### Post by ubudog on 2010-05-22
> **smileyacid said:**
> can you let me know what dmesg does ?

-smiley

I still have to look over it... But dmesg shows error messages on your system and you can see if everything is working properly.  Also, if something crashed, it should show up on dmesg.

---

### Post by ubudog on 2010-05-22
Couldn't find anything.  Maybe someone else on here can take a look?

---

### Post by smileyacid on 2010-05-22
ubudog Can you do me 1 last favour + tell me the difference between what dmesg does + the info that would be in the xlog file found in the VAR folder in root

-smiley

---

### Post by ubudog on 2010-05-22
The dmesg command shows you more than just X releated stuff.

---

