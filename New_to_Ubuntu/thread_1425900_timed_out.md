---
title: "timed out ?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by sergiocntr on 2010-03-09
Dear all
this is my first post and first I want to say one big thanks at all for the precious information that I founded looking inside the forum .

I have ubuntu 9.10 on my pc and it works without monitor only for 10 minutes.After this time it stops.Literally the ssh connection dead after this time and I need to reboot the system with the main switch.
I tried several ways ,also with 9.10 server, but still the same problem.
I really don't understand why with the monitor plugged it works great and without it works only for ten minutes : please could someone explain me why? Is it one way to avoid this problem? 
PS
I've removed the xorg daemon end modified the grub cfg file removing the "splash" word leaving only "quiet" : this is the only way I've founded for to let the pc work without monitor,otherwise it hangs at boot.
Thanks
Sergio

---

### Post by ubudog on 2010-03-09
In a command line, type ```
dmesg
``` Then paste the output here.

---

### Post by sergiocntr on 2010-03-09
Thanks for your help Ubudog 

```


[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fe40
[    0.000000] On node 0 totalpages: 261583
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 269 pages used for memmap
[    0.000000]   HighMem zone: 34101 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3ff00000 (gap: 3ff00000:bfcc0000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1805000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259538
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=f05fe6c7-aca9-47db-9c9f-3728e84221a9 ro quiet
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5233600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003fe40)
[    0.000000] Memory: 1016300k/1046784k available (4565k kernel code, 29576k reserved, 2143k data, 540k init, 137480k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1999.006 MHz processor.
[    0.001958] Console: colour VGA+ 80x25
[    0.001967] console [tty0] enabled
[    0.002048] Calibrating delay loop (skipped), value calculated using timer frequency.. 3998.01 BogoMIPS (lpj=7996024)
[    0.002103] Security Framework initialized
[    0.002158] AppArmor: AppArmor initialized
[    0.002176] Mount-cache hash table entries: 512
[    0.002495] Initializing cgroup subsys ns
[    0.002509] Initializing cgroup subsys cpuacct
[    0.002518] Initializing cgroup subsys memory
[    0.002532] Initializing cgroup subsys freezer
[    0.002538] Initializing cgroup subsys net_cls
[    0.002572] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.002580] CPU: L2 cache: 512K
[    0.002585] CPU: Hyper-Threading is disabled
[    0.002595] mce: CPU supports 4 MCE banks
[    0.002616] CPU0: Thermal monitoring enabled (TM1)
[    0.002643] Performance Counters: no PMU driver, software counters only.
[    0.002658] Checking 'hlt' instruction... OK.
[    0.017370] SMP alternatives: switching to UP code
[    0.031528] ACPI: Core revision 20090521
[    0.044283] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.083978] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 07
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (3998.01 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] Booting paravirtualized kernel on bare hardware
[    0.084001] regulator: core version 0.5
[    0.084001] Time: 23:19:54  Date: 03/09/10
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.084001] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.084001] PCI: Using configuration type 1 for base access
[    0.084001] bio: create slab <bio-0> at 0
[    0.084738] ACPI: EC: Look up EC in DSDT
[    0.094924] ACPI: Interpreter enabled
[    0.094934] ACPI: (supports S0 S1 S3 S4 S5)
[    0.094986] ACPI: Using IOAPIC for interrupt routing
[    0.103259] ACPI: No dock devices found.
[    0.103462] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.103533] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.103551] pci 0000:00:00.0: reg 10 32bit mmio: [0xfe800000-0xfebfffff]
[    0.103658] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.103670] pci 0000:00:02.0: reg 14 32bit mmio: [0xfe780000-0xfe7fffff]
[    0.103682] pci 0000:00:02.0: reg 18 io port: [0xec00-0xec07]
[    0.103760] pci 0000:00:06.0: reg 10 32bit mmio: [0xfecf0000-0xfecf0fff]
[    0.103889] pci 0000:00:1d.0: reg 20 io port: [0xdc00-0xdc1f]
[    0.103962] pci 0000:00:1d.1: reg 20 io port: [0xe000-0xe01f]
[    0.104048] pci 0000:00:1d.2: reg 20 io port: [0xe400-0xe41f]
[    0.104122] pci 0000:00:1d.3: reg 20 io port: [0xe800-0xe81f]
[    0.104203] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe77bc00-0xfe77bfff]
[    0.104276] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.104285] pci 0000:00:1d.7: PME# disabled
[    0.104404] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.104415] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.104422] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.104458] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.104470] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.104481] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.104493] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.104505] pci 0000:00:1f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.104517] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.104587] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.104672] pci 0000:01:05.0: reg 10 io port: [0xb800-0xb8ff]
[    0.104684] pci 0000:01:05.0: reg 14 32bit mmio: [0xfe5ffc00-0xfe5ffcff]
[    0.104736] pci 0000:01:05.0: supports D1 D2
[    0.104741] pci 0000:01:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.104748] pci 0000:01:05.0: PME# disabled
[    0.104796] pci 0000:00:1e.0: transparent bridge
[    0.104804] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[    0.104812] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe500000-0xfe5fffff]
[    0.104830] pci_bus 0000:00: on NUMA node 0
[    0.104838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.104980] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.108652] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.108825] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.108992] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.109159] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.109324] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.109493] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.109662] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.109829] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.110208] SCSI subsystem initialized
[    0.110358] libata version 3.00 loaded.
[    0.110505] usbcore: registered new interface driver usbfs
[    0.110539] usbcore: registered new interface driver hub
[    0.110586] usbcore: registered new device driver usb
[    0.110829] ACPI: WMI: Mapper loaded
[    0.110833] PCI: Using ACPI for IRQ routing
[    0.111083] Bluetooth: Core ver 2.15
[    0.111144] NET: Registered protocol family 31
[    0.111149] Bluetooth: HCI device and connection manager initialized
[    0.111156] Bluetooth: HCI socket layer initialized
[    0.111161] NetLabel: Initializing
[    0.111165] NetLabel:  domain hash size = 128
[    0.111168] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.111198] NetLabel:  unlabeled traffic allowed by default
[    0.111385] hpet clockevent registered
[    0.111391] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.111400] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.111413] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.119052] pnp: PnP ACPI init
[    0.119112] ACPI: bus type pnp registered
[    0.124784] pnp: PnP ACPI: found 9 devices
[    0.124789] ACPI: ACPI bus type pnp unregistered
[    0.124797] PnPBIOS: Disabled by ACPI PNP
[    0.124823] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.124830] system 00:05: ioport range 0x800-0x87f has been reserved
[    0.124837] system 00:05: ioport range 0x480-0x4bf has been reserved
[    0.124846] system 00:05: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.124853] system 00:05: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.124865] system 00:06: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.124872] system 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.124883] system 00:07: ioport range 0x680-0x6ff has been reserved
[    0.124889] system 00:07: ioport range 0x295-0x296 has been reserved
[    0.124900] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[    0.124907] system 00:08: iomem range 0xc0000-0xdffff could not be reserved
[    0.124914] system 00:08: iomem range 0xe0000-0xfffff could not be reserved
[    0.124920] system 00:08: iomem range 0x100000-0x3fefffff could not be reserved
[    0.124927] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.159766] AppArmor: AppArmor Filesystem Enabled
[    0.159808] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.159815] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.159826] pci 0000:00:1e.0:   MEM window: 0xfe500000-0xfe5fffff
[    0.159833] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.159854] pci 0000:00:1e.0: setting latency timer to 64
[    0.159865] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.159871] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.159877] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.159883] pci_bus 0000:01: resource 1 mem: [0xfe500000-0xfe5fffff]
[    0.159889] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.159894] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.159969] NET: Registered protocol family 2
[    0.160154] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.160822] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.162555] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.163650] TCP: Hash tables configured (established 131072 bind 65536)
[    0.163665] TCP reno registered
[    0.163947] NET: Registered protocol family 1
[    0.164164] Trying to unpack rootfs image as initramfs...
[    0.498473] Freeing initrd memory: 7465k freed
[    0.515462] cpufreq-nforce2: No nForce2 chipset.
[    0.515523] Scanning for low memory corruption every 60 seconds
[    0.515776] audit: initializing netlink socket (disabled)
[    0.515819] type=2000 audit(1268176794.512:1): initialized
[    0.527352] highmem bounce pool size: 64 pages
[    0.527364] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.529679] VFS: Disk quotas dquot_6.5.2
[    0.529774] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.530720] fuse init (API version 7.12)
[    0.530862] msgmni has been set to 1731
[    0.531257] alg: No test for stdrng (krng)
[    0.531281] io scheduler noop registered
[    0.531286] io scheduler anticipatory registered
[    0.531291] io scheduler deadline registered
[    0.531375] io scheduler cfq registered (default)
[    0.531407] pci 0000:00:02.0: Boot video device
[    0.531667] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.531713] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.531945] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.531954] ACPI: Power Button [PWRF]
[    0.532086] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.532092] ACPI: Power Button [PWRB]
[    0.532550] processor LNXCPU:00: registered as cooling_device0
[    0.536845] isapnp: Scanning for PnP cards...
[    0.612033] Switched to high resolution mode on CPU 0
[    0.891138] isapnp: No Plug & Play device found
[    0.893294] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.895362] brd: module loaded
[    0.896135] loop: module loaded
[    0.896287] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.896494] ata_piix 0000:00:1f.1: version 2.13
[    0.896530]   alloc irq_desc for 18 on node -1
[    0.896535]   alloc kstat_irqs on node -1
[    0.896552] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.896650] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.896839] scsi0 : ata_piix
[    0.897055] scsi1 : ata_piix
[    0.900167] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.900173] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.901647] Fixed MDIO Bus: probed
[    0.901721] PPP generic driver version 2.4.2
[    0.901928] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.901973]   alloc irq_desc for 23 on node -1
[    0.901979]   alloc kstat_irqs on node -1
[    0.901994] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.902024] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.902032] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.902141] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.906073] ehci_hcd 0000:00:1d.7: debug port 1
[    0.906084] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.906463] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe77bc00
[    0.920016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.920177] usb usb1: configuration #1 chosen from 1 choice
[    0.920232] hub 1-0:1.0: USB hub found
[    0.920250] hub 1-0:1.0: 8 ports detected
[    0.920382] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.920422] uhci_hcd: USB Universal Host Controller Interface driver
[    0.920509]   alloc irq_desc for 16 on node -1
[    0.920514]   alloc kstat_irqs on node -1
[    0.920526] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.920541] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.920548] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.920620] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.920668] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000dc00
[    0.920799] usb usb2: configuration #1 chosen from 1 choice
[    0.920851] hub 2-0:1.0: USB hub found
[    0.920865] hub 2-0:1.0: 2 ports detected
[    0.920943]   alloc irq_desc for 19 on node -1
[    0.920948]   alloc kstat_irqs on node -1
[    0.920957] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.920968] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.920974] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.921047] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.921097] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e000
[    0.921226] usb usb3: configuration #1 chosen from 1 choice
[    0.921273] hub 3-0:1.0: USB hub found
[    0.921289] hub 3-0:1.0: 2 ports detected
[    0.921367] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.921378] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.921384] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.921441] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.921483] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[    0.921640] usb usb4: configuration #1 chosen from 1 choice
[    0.921685] hub 4-0:1.0: USB hub found
[    0.921700] hub 4-0:1.0: 2 ports detected
[    0.921781] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.921791] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.921797] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.921857] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.921888] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e800
[    0.922015] usb usb5: configuration #1 chosen from 1 choice
[    0.922061] hub 5-0:1.0: USB hub found
[    0.922078] hub 5-0:1.0: 2 ports detected
[    0.922251] PNP: No PS/2 controller found. Probing ports directly.
[    0.924926] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.924939] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.925056] mice: PS/2 mouse device common for all mice
[    0.925215] rtc_cmos 00:02: RTC can wake from S4
[    0.925285] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.925318] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.925521] device-mapper: uevent: version 1.0.3
[    0.925717] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.925850] device-mapper: multipath: version 1.1.0 loaded
[    0.925856] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.926076] EISA: Probing bus 0 at eisa.0
[    0.926119] EISA: Detected 0 cards.
[    0.926204] cpuidle: using governor ladder
[    0.926209] cpuidle: using governor menu
[    0.927053] TCP cubic registered
[    0.927277] NET: Registered protocol family 10
[    0.928041] lo: Disabled Privacy Extensions
[    0.928538] NET: Registered protocol family 17
[    0.928580] Bluetooth: L2CAP ver 2.13
[    0.928584] Bluetooth: L2CAP socket layer initialized
[    0.928590] Bluetooth: SCO (Voice Link) ver 0.6
[    0.928594] Bluetooth: SCO socket layer initialized
[    0.928674] Bluetooth: RFCOMM TTY layer initialized
[    0.928679] Bluetooth: RFCOMM socket layer initialized
[    0.928684] Bluetooth: RFCOMM ver 1.11
[    0.928750] Using IPI No-Shortcut mode
[    0.928892] PM: Resume from disk failed.
[    0.928915] registered taskstats version 1
[    0.929092]   Magic number: 2:369:352
[    0.929214] rtc_cmos 00:02: setting system clock to 2010-03-09 23:19:55 UTC (1268176795)
[    0.929221] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.929225] EDD information not available.
[    1.114887] ata2.01: ATA-7: MAXTOR STM3160215A, 3.AAD, max UDMA/100
[    1.114894] ata2.01: 312581808 sectors, multi 16: LBA48 
[    1.118157] ata1.00: ATA-7: MAXTOR STM3160212A, 3.AAJ, max UDMA/100
[    1.118163] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.118220] ata1.01: ATAPI: DVD-RW IDE1108, VER B018, max UDMA/66
[    1.181477] ata2.01: configured for UDMA/100
[    1.184634] ata1.00: configured for UDMA/100
[    1.200216] ata1.01: configured for UDMA/66
[    1.201135] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM316021 3.AA PQ: 0 ANSI: 5
[    1.201368] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.201725] scsi 0:0:1:0: CD-ROM            DVDRW    IDE1108          B018 PQ: 0 ANSI: 5
[    1.202406] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.202492] sd 0:0:0:0: [sda] Write Protect is off
[    1.202498] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.202539] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.202778]  sda: sda1 sda2 < sda5 >
[    1.259087] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.260409] sr0: scsi3-mmc drive: 1x/40x writer cd/rw xa/form2 cdda tray
[    1.260416] Uniform CD-ROM driver Revision: 3.20
[    1.260569] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.260678] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.260837] scsi 1:0:1:0: Direct-Access     ATA      MAXTOR STM316021 3.AA PQ: 0 ANSI: 5
[    1.261020] sd 1:0:1:0: Attached scsi generic sg2 type 0
[    1.261081] sd 1:0:1:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.261158] sd 1:0:1:0: [sdb] Write Protect is off
[    1.261164] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.261204] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.261409]  sdb: sdb1
[    1.279665] sd 1:0:1:0: [sdb] Attached SCSI disk
[    1.279697] Freeing unused kernel memory: 540k freed
[    1.280804] Write protecting the kernel text: 4568k
[    1.280847] Write protecting the kernel read-only data: 1836k
[    1.288141] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.442949] usb 1-6: configuration #1 chosen from 1 choice
[    1.619300] Linux agpgart interface v0.103
[    1.645285] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    1.645527] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[    1.655052] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.655116] 8139cp 0000:01:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.683564] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    1.708085] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    1.776175] 8139too Fast Ethernet driver 0.9.28
[    1.776297]   alloc irq_desc for 22 on node -1
[    1.776302]   alloc kstat_irqs on node -1
[    1.776320] 8139too 0000:01:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.777797] eth0: RealTek RTL8139 at 0xb800, 00:19:66:b7:43:35, IRQ 22
[    1.867616] [drm] Initialized drm 1.1.0 20060810
[    1.891947] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.891960] i915 0000:00:02.0: setting latency timer to 64
[    1.905842] usb 3-2: configuration #1 chosen from 1 choice
[    1.936816] usbcore: registered new interface driver hiddev
[    2.054985] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3
[    2.055154] generic-usb 0003:15CA:00C3.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2/input0
[    2.055194] usbcore: registered new interface driver usbhid
[    2.055201] usbhid: v2.6:USB HID core driver
[    2.101865] [drm] fb0: inteldrmfb frame buffer device
[    2.101887] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.196913] render error detected, EIR: 0x00000010
[    2.196921] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    2.196938] render error detected, EIR: 0x00000010
[    2.208137] [drm] DAC-5: set mode 1680x1050 17
[    2.225039] Console: switching to colour frame buffer device 210x65
[    2.880356] PM: Starting manual resume from disk
[    2.880366] PM: Resume from partition 8:5
[    2.880370] PM: Checking hibernation image.
[    2.880655] PM: Resume from disk failed.
[    2.915848] EXT4-fs (sda1): barriers enabled
[    2.937451] kjournald2 starting: pid 310, dev sda1:8, commit interval 5 seconds
[    2.937483] EXT4-fs (sda1): delayed allocation enabled
[    2.937490] EXT4-fs: file extents enabled
[    2.965615] EXT4-fs: mballoc enabled
[    2.965649] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.689819] type=1505 audit(1268176798.258:2): operation="profile_load" pid=333 name=/sbin/dhclient3
[    3.690666] type=1505 audit(1268176798.258:3): operation="profile_load" pid=333 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.691136] type=1505 audit(1268176798.258:4): operation="profile_load" pid=333 name=/usr/lib/connman/scripts/dhclient-script
[    3.743283] type=1505 audit(1268176798.310:5): operation="profile_load" pid=334 name=/usr/bin/evince
[    3.758028] type=1505 audit(1268176798.326:6): operation="profile_load" pid=334 name=/usr/bin/evince-previewer
[    3.766539] type=1505 audit(1268176798.334:7): operation="profile_load" pid=334 name=/usr/bin/evince-thumbnailer
[    3.801494] type=1505 audit(1268176798.370:8): operation="profile_load" pid=336 name=/usr/sbin/mysqld
[    3.806297] type=1505 audit(1268176798.374:9): operation="profile_load" pid=337 name=/usr/sbin/ntpd
[    3.811096] type=1505 audit(1268176798.378:10): operation="profile_load" pid=338 name=/usr/sbin/tcpdump
[    4.522704] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k 
[    5.109621] EXT4-fs (sda1): internal journal on sda1:8
[    5.238254] udev: starting version 147
[    5.300600] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[    6.754190] intel_rng: FWH not detected
[    7.144368] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.239886] usb 1-6: firmware: requesting sms1xxx-hcw-55xxx-dvbt-02.fw
[    7.281445] lp: driver loaded but no devices found
[    8.082264] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.464094] smscore_set_device_mode: firmware download success: sms1xxx-hcw-55xxx-dvbt-02.fw
[    8.725499] DVB: registering new adapter (Hauppauge WinTV MiniStick)
[    8.725860] DVB: registering adapter 0 frontend 0 (Siano Mobile Digital MDTV Receiver)...
[    8.734340] usbcore: registered new interface driver smsusb
[    9.524232] type=1505 audit(1268176804.094:11): operation="profile_replace" pid=676 name=/sbin/dhclient3
[    9.526094] type=1505 audit(1268176804.094:12): operation="profile_replace" pid=676 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.526566] type=1505 audit(1268176804.094:13): operation="profile_replace" pid=676 name=/usr/lib/connman/scripts/dhclient-script
[    9.543527] type=1505 audit(1268176804.110:14): operation="profile_replace" pid=677 name=/usr/bin/evince
[    9.559673] type=1505 audit(1268176804.126:15): operation="profile_replace" pid=677 name=/usr/bin/evince-previewer
[    9.570770] type=1505 audit(1268176804.138:16): operation="profile_replace" pid=677 name=/usr/bin/evince-thumbnailer
[    9.587657] type=1505 audit(1268176804.154:17): operation="profile_replace" pid=679 name=/usr/sbin/mysqld
[    9.593655] type=1505 audit(1268176804.162:18): operation="profile_replace" pid=680 name=/usr/sbin/ntpd
[    9.599358] type=1505 audit(1268176804.166:19): operation="profile_replace" pid=681 name=/usr/sbin/tcpdump
[   13.428765] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   18.504493] type=1503 audit(1268176813.074:20): operation="open" pid=1131 parent=1130 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   19.151686] type=1503 audit(1268176813.718:21): operation="open" pid=1226 parent=1225 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   19.894309] type=1503 audit(1268176814.462:22): operation="open" pid=1356 parent=1236 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   20.367568] type=1503 audit(1268176814.934:23): operation="open" pid=1362 parent=1361 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.411293] type=1503 audit(1268176815.978:24): operation="open" pid=1376 parent=1375 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.490616] type=1503 audit(1268176817.058:25): operation="open" pid=1394 parent=1393 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.593538] type=1503 audit(1268176817.162:26): operation="open" pid=1405 parent=1404 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   24.140020] eth0: no IPv6 routers present



```As told, it is very strange (almost for me...) : with the monitor plugged it works like a charm .... without only for 10 minutes .
It seems that it is right the time before the sleep of the monitor...but  I  removed all the power saving things and leaved the pc to "never" for the monitor's stand by...but the monitor goes down however .....(This is the third time that I set up Mythbuntu ,everytime with this trouble and I'm confident with this)
I tried Fedora but I was involved with trouble in the mythtv installation-setup and I walked back to Ubuntu.
Now in Italy is quite late ,I'll read your answer tomorrow.
Thanks again.
Sergio

---

### Post by sergiocntr on 2010-03-10
Please help!

---

### Post by halitech on 2010-03-10
have you checked in the BIOS to make sure power saver is disabled there?

---

### Post by sergiocntr on 2010-03-10
Yes : suspend to ram  - Disabled.
It is the only choice inside the bios involved.

---

### Post by sergiocntr on 2010-03-10
Seems hard to fix.
The same operating system in one other machine works well,also without monitor.
I really don-t understand why this hardware configuration is so unlucky....
Please could someone send me one updated gude /or link for how to remove the monitor login,leaving the PC with only ssh control?
Someone told me that  could be the monitor itself that shutdown automatically ,what this can be so dangerous for the operating system is myterious....
Sergio

---

### Post by anewguy on 2010-03-10
I'd like to see a solution here as well, as I had an Ubuntu server with a very similar problem.  In my case, I had no monitor or keyboard attached and used ssh to connect.  The server was wireless.  The 2 PC's that were accessing the server could see the server and as long as 1 was transferring something the server connection would stay up - if not, then after about 10 minutes (hence why I suspect it might have been something similar) I could no longer access the server and had to reboot it.  With that experience (I didn't get a solution from the forum either though a lot of people really tried to help), I quit using a server and sold it.  I would like to have a server again.  I was using either 8.10 or 9.04 server edition at the time.

dave

---

### Post by ubudog on 2010-03-10
What type of computer is it?

---

### Post by sergiocntr on 2010-03-11
It is a normal pc with celeron processor @2600 Ghz 
This is the MB [http://www.asrock.com/mb/overview.asp?Model=P4i65GV](http://www.asrock.com/mb/overview.asp?Model=P4i65GV)

Thanks
Sergio

---

