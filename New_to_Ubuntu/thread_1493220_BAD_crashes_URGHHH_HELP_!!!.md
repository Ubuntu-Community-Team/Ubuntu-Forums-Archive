---
title: "BAD crashes URGHHH HELP !!!"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by smileyacid on 2010-05-25
**BAD** *crashes* **URGHHH** **HELP** !!!

I have been having problems with Ubu 10.4 (FRESH install) crashing it just sends the screen black with no response at all + a need to shut done people have suggested it may be video related but I saw in log file viewer in syslog (im not an expert like just guessing) something suspicious namely ' AptDaemon: INFO: Shutdown was requested ' so I looked it up on google + found a Ubu forum page similar: Unwanted shutdowns - caused by AptDaemon?

I'm still not sure what's going on can anyone help me please?

I dont want to go back to Windows

-smiley

---

### Post by SRST Technologies on 2010-05-25
Come again?

I have no idea what you're trying to say.

I get the suspicion that you're actually typing multiple sentences but can't be sure, and without that knowledge I'm not sure exactly what that long string of text means.

---

### Post by smileyacid on 2010-05-25
SORRY in a bit of a frustrated mood !

I have been having problems with Ubuntu crashing 

The screen goes black + I need to restart 

I have discussed it in a previous thread + people thought it was a video related error but after trying several things I still have the same problem


Whilst looking through my log files with System-Administration-log file viewer - syslog. I found something suspicious looking

I.e. May 25 20:16:51 Jamie-desktop Apt Daemon: INFO: Quitting due to inactivity

May 25 20:16:51 Jamie-desktop Apt Daemon: INFO: Shut-down was requested

I searched it in google + found a similar problem titled Unwanted shut-downs - caused by Apt Daemon?

does any one have any ideas ?

please help 

-smiley

---

### Post by SRST Technologies on 2010-05-25
That's strange, the only thing google returns for Unwanted shut-downs - caused by Apt Daemon is... this thread.  It doesn't exist.  You're making things up.

So what are your qualifications for calling this Apt Daemon event suspicious?  Do you have ANY clue what this daemon is or what it does or what it's supposed to do?

After trying several things to solve your video problem and none of them worked, and you're still having the same problem, why do you think the problem is being caused by something different?

How about this, instead of being the expert, why don't you be the patient?

---

### Post by smileyacid on 2010-05-25
Yeh of course 

listen if you dont know how or dont want to help

DONT

[http://ubuntuforums.org/showthread.php?t=1491072](http://ubuntuforums.org/showthread.php?t=1491072)

was the problem for any one realy wanting to help

---

### Post by 2hot6ft2 on 2010-05-25
> **smileyacid said:**
> Yeh of course 

listen if you dont know how or dont want to help

DONT

[http://ubuntuforums.org/showthread.php?t=1491072](http://ubuntuforums.org/showthread.php?t=1491072)

was the problem for any one realy wanting to help
In the thread you linked to it looks to me like AptDaemon just shut down due to inactivity like Update Manager shutting down after not finding any updates. I don't believe that it's your issue either since you made no mention of an error. Only that it shut down the AptDaemon which is not like shutting the system down.
ACPI seems to have had an error though.
And I have responded there to that issue since you have said nothing about having the same error they did.
:popcorn:

---

### Post by durand on 2010-05-25
> **SRST Technologies said:**
> That's strange, the only thing google returns for Unwanted shut-downs - caused by Apt Daemon is... this thread.  It doesn't exist.  You're making things up.

...

Could you please be more polite? If you don't have anything constructive to say, don't say anything. You're not being too helpful.

Do you get the same problems from running it off the CD? See if you can post the output of "dmesg" here. Open a terminal (Application > Accessories > Terminal), type dmesg > output.txt and press enter. Then attach the output.txt file that will be in your home directory here.

---

### Post by libssd on 2010-05-25
Try an earlier release (9.04 = Jaunty, or 9.10 (Karmic). Looking at install surveys, they have fewer problems than 10.4, and are more likely to work out of the box.

---

### Post by smileyacid on 2010-05-25
I have invested time in this distro + have many apps installed  ect if i post some info of some sort can someone please  help me through this 

Is there any thing of particular use i can post  apart from dmesg

If it helps the computer crashes whilst on + quite often during use of Ffox
it is a Dell Optiplex GX260, the graphics card is a built in:

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
jamie@jamie-desktop:~$

processor: intel pentium4 1.8 GHz
Memory (RAM): 2 GiB

dmesg: [    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1078000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292468 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7f800000 (gap: 7f800000:7f400000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36024 r0 d21320 u1048576
[    0.000000] pcpu-alloc: s36024 r0 d21320 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517918
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=752220dd-64af-4f27-a265-f2e7ed5a8029 ro vga=792 quiet quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10441940 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f771)
[    0.000000] Memory: 2043344k/2088388k available (4673k kernel code, 43452k reserved, 2121k data, 656k init, 1179084k highmem)
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
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1793.026 MHz processor.
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3586.05 BogoMIPS (lpj=7172104)
[    0.004050] Security Framework initialized
[    0.004104] AppArmor: AppArmor initialized
[    0.004121] Mount-cache hash table entries: 512
[    0.004422] Initializing cgroup subsys ns
[    0.004432] Initializing cgroup subsys cpuacct
[    0.004441] Initializing cgroup subsys memory
[    0.004456] Initializing cgroup subsys devices
[    0.004462] Initializing cgroup subsys freezer
[    0.004467] Initializing cgroup subsys net_cls
[    0.004514] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004521] CPU: L2 cache: 512K
[    0.004526] CPU: Hyper-Threading is disabled
[    0.004534] mce: CPU supports 4 MCE banks
[    0.004555] CPU0: Thermal monitoring enabled (TM1)
[    0.004579] Performance Events: no PMU driver, software events only.
[    0.004593] Checking 'hlt' instruction... OK.
[    0.021514] SMP alternatives: switching to UP code
[    0.039049] ACPI: Core revision 20090903
[    0.077673] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.077684] ftrace: allocating 21771 entries in 43 pages
[    0.080153] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.080479] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.121813] CPU0: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 04
[    0.124001] Brought up 1 CPUs
[    0.124001] Total of 1 processors activated (3586.05 BogoMIPS).
[    0.124001] CPU0 attaching NULL sched-domain.
[    0.124001] devtmpfs: initialized
[    0.124001] regulator: core version 0.5
[    0.124001] Time: 23:46:47  Date: 05/25/10
[    0.124001] NET: Registered protocol family 16
[    0.124001] EISA bus registered
[    0.124001] ACPI: bus type pci registered
[    0.141033] PCI: PCI BIOS revision 2.10 entry at 0xfbdea, last bus=1
[    0.141038] PCI: Using configuration type 1 for base access
[    0.142897] bio: create slab <bio-0> at 0
[    0.143620] ACPI: EC: Look up EC in DSDT
[    0.176773] ACPI: Interpreter enabled
[    0.176794] ACPI: (supports S0 S1 S3 S4 S5)
[    0.176837] ACPI: Using IOAPIC for interrupt routing
[    0.213158] ACPI: No dock devices found.
[    0.214025] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.214101] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.214209] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.214220] pci 0000:00:02.0: reg 14 32bit mmio: [0xff680000-0xff6fffff]
[    0.214367] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.214442] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.214515] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.214597] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa00800-0xffa00bff]
[    0.214673] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.214681] pci 0000:00:1d.7: PME# disabled
[    0.214751] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.214754] * this clock source is slow. If you are sure your timer does not have
[    0.214756] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.214814] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.214821] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.214855] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.214866] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.214877] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.214887] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.214898] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.214909] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.214980] pci 0000:00:1f.3: reg 20 io port: [0xdc80-0xdc9f]
[    0.215043] pci 0000:00:1f.5: reg 10 io port: [0xd800-0xd8ff]
[    0.215053] pci 0000:00:1f.5: reg 14 io port: [0xdc40-0xdc7f]
[    0.215064] pci 0000:00:1f.5: reg 18 32bit mmio: [0xffa00400-0xffa005ff]
[    0.215075] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xffa00000-0xffa000ff]
[    0.215116] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.215123] pci 0000:00:1f.5: PME# disabled
[    0.215216] pci 0000:01:0c.0: reg 10 32bit mmio: [0xff8e0000-0xff8fffff]
[    0.215233] pci 0000:01:0c.0: reg 18 io port: [0xecc0-0xecff]
[    0.215289] pci 0000:01:0c.0: PME# supported from D0 D3hot D3cold
[    0.215296] pci 0000:01:0c.0: PME# disabled
[    0.215339] pci 0000:00:1e.0: transparent bridge
[    0.215347] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.215354] pci 0000:00:1e.0: bridge 32bit mmio: [0xff800000-0xff9fffff]
[    0.215371] pci_bus 0000:00: on NUMA node 0
[    0.215379] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.215829] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.318894] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.319271] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.319634] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.319997] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.320364] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.320727] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.321088] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.321454] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.321693] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.321707] vgaarb: loaded
[    0.321947] SCSI subsystem initialized
[    0.322080] libata version 3.00 loaded.
[    0.322219] usbcore: registered new interface driver usbfs
[    0.322248] usbcore: registered new interface driver hub
[    0.322299] usbcore: registered new device driver usb
[    0.322543] ACPI: WMI: Mapper loaded
[    0.322547] PCI: Using ACPI for IRQ routing
[    0.322775] NetLabel: Initializing
[    0.322780] NetLabel:  domain hash size = 128
[    0.322782] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.322806] NetLabel:  unlabeled traffic allowed by default
[    0.322868] Switching to clocksource tsc
[    0.324001] AppArmor: AppArmor Filesystem Enabled
[    0.324001] pnp: PnP ACPI init
[    0.324001] ACPI: bus type pnp registered
[    0.349328] pnp 00:0a: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.349337] pnp 00:0a: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.350202] pnp: PnP ACPI: found 11 devices
[    0.350206] ACPI: ACPI bus type pnp unregistered
[    0.350215] PnPBIOS: Disabled by ACPI PNP
[    0.350238] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.350246] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    0.350253] system 00:00: iomem range 0x1000000-0x7f770fff could not be reserved
[    0.350259] system 00:00: iomem range 0xc0000-0xcbfff could not be reserved
[    0.350264] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.350271] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.350276] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.350282] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.350288] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
[    0.350305] system 00:0a: ioport range 0xc00-0xc7f has been reserved
[    0.385237] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.385244] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.385254] pci 0000:00:1e.0:   MEM window: 0xff800000-0xff9fffff
[    0.385262] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.385284] pci 0000:00:1e.0: setting latency timer to 64
[    0.385294] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.385299] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.385304] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.385309] pci_bus 0000:01: resource 1 mem: [0xff800000-0xff9fffff]
[    0.385314] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.385318] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.385388] NET: Registered protocol family 2
[    0.385584] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.386277] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.387702] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.388622] TCP: Hash tables configured (established 131072 bind 65536)
[    0.388630] TCP reno registered
[    0.388908] NET: Registered protocol family 1
[    0.388956] pci 0000:00:02.0: Boot video device
[    0.389296] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    0.389301] Simple Boot Flag at 0x7a set to 0x1
[    0.389461] cpufreq-nforce2: No nForce2 chipset.
[    0.389520] Scanning for low memory corruption every 60 seconds
[    0.389739] audit: initializing netlink socket (disabled)
[    0.389762] type=2000 audit(1274831206.389:1): initialized
[    0.407535] Trying to unpack rootfs image as initramfs...
[    0.425864] highmem bounce pool size: 64 pages
[    0.425876] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.432575] VFS: Disk quotas dquot_6.5.2
[    0.432709] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.433890] fuse init (API version 7.13)
[    0.434058] msgmni has been set to 1690
[    0.437624] alg: No test for stdrng (krng)
[    0.437788] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.437795] io scheduler noop registered
[    0.437799] io scheduler anticipatory registered
[    0.437803] io scheduler deadline registered
[    0.437882] io scheduler cfq registered (default)
[    0.438069] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.438120] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.438291] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.438307] ACPI: Power Button [VBTN]
[    0.438400] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.438406] ACPI: Power Button [PWRF]
[    0.438743] processor LNXCPU:00: registered as cooling_device0
[    0.489308] isapnp: Scanning for PnP cards...
[    0.495280] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.495410] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.496016] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.497978] brd: module loaded
[    0.498858] loop: module loaded
[    0.499045] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.499246] ata_piix 0000:00:1f.1: version 2.13
[    0.499266] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.499283]   alloc irq_desc for 18 on node -1
[    0.499288]   alloc kstat_irqs on node -1
[    0.499301] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.499390] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.545261] scsi0 : ata_piix
[    0.549772] scsi1 : ata_piix
[    0.549844] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.549850] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.550563] Fixed MDIO Bus: probed
[    0.550637] PPP generic driver version 2.4.2
[    0.550756] tun: Universal TUN/TAP device driver, 1.6
[    0.550761] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.550927] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.550970]   alloc irq_desc for 23 on node -1
[    0.550976]   alloc kstat_irqs on node -1
[    0.550990] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.551019] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.551026] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.551104] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.551161] ehci_hcd 0000:00:1d.7: debug port 1
[    0.555059] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.557633] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa00800
[    0.577634] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.577892] usb usb1: configuration #1 chosen from 1 choice
[    0.577951] hub 1-0:1.0: USB hub found
[    0.577972] hub 1-0:1.0: 6 ports detected
[    0.578084] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.578116] uhci_hcd: USB Universal Host Controller Interface driver
[    0.578206]   alloc irq_desc for 16 on node -1
[    0.578212]   alloc kstat_irqs on node -1
[    0.578226] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.578244] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.578250] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.578325] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.578374] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    0.578542] usb usb2: configuration #1 chosen from 1 choice
[    0.578592] hub 2-0:1.0: USB hub found
[    0.578610] hub 2-0:1.0: 2 ports detected
[    0.578684]   alloc irq_desc for 19 on node -1
[    0.578689]   alloc kstat_irqs on node -1
[    0.578698] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.578710] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.578715] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.578780] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.578819] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    0.578970] usb usb3: configuration #1 chosen from 1 choice
[    0.579019] hub 3-0:1.0: USB hub found
[    0.579035] hub 3-0:1.0: 2 ports detected
[    0.579108] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.579119] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.579125] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.579189] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.579231] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    0.579409] usb usb4: configuration #1 chosen from 1 choice
[    0.579463] hub 4-0:1.0: USB hub found
[    0.579481] hub 4-0:1.0: 2 ports detected
[    0.579635] PNP: PS/2 Controller [PNP0f13:MOU] at 0x60,0x64 irq 12
[    0.579641] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.586648] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.586672] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.586977] mice: PS/2 mouse device common for all mice
[    0.587208] rtc_cmos 00:05: RTC can wake from S4
[    0.587284] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.587314] rtc0: alarms up to one day, 242 bytes nvram
[    0.587546] device-mapper: uevent: version 1.0.3
[    0.587783] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.593362] device-mapper: multipath: version 1.1.0 loaded
[    0.593371] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.593663] EISA: Probing bus 0 at eisa.0
[    0.593708] EISA: Detected 0 cards.
[    0.593794] cpuidle: using governor ladder
[    0.593799] cpuidle: using governor menu
[    0.594628] TCP cubic registered
[    0.594881] NET: Registered protocol family 10
[    0.595782] lo: Disabled Privacy Extensions
[    0.596355] NET: Registered protocol family 17
[    0.596457] Using IPI No-Shortcut mode
[    0.596640] PM: Resume from disk failed.
[    0.596664] registered taskstats version 1
[    0.596985]   Magic number: 10:549:808
[    0.597099] rtc_cmos 00:05: setting system clock to 2010-05-25 23:46:47 UTC (1274831207)
[    0.597107] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.597110] EDD information not available.
[    0.750192] ata2.00: ATAPI: HL-DT-STDVD-RAM GH22LP20, 1.04, max UDMA/66
[    0.762649] ata1.00: ATA-8: WDC WD1600AAJB-00J3A0, 01.03E01, max UDMA/133
[    0.762657] ata1.00: 312581808 sectors, multi 8: LBA48 
[    0.765911] ata2.00: configured for UDMA/66
[    0.774528] ata1.00: configured for UDMA/100
[    1.179674] isapnp: No Plug & Play device found
[    1.179719] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.179969] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AAJB-0 01.0 PQ: 0 ANSI: 5
[    1.180298] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.180582] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.180675] sd 0:0:0:0: [sda] Write Protect is off
[    1.180681] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.180728] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.181162]  sda:
[    1.182011] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22LP20 1.04 PQ: 0 ANSI: 5
[    1.188702] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.188713] Uniform CD-ROM driver Revision: 3.20
[    1.188943] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.189062] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.191366]  sda1 sda2 <
[    1.208065] Freeing initrd memory: 7778k freed
[    1.222252]  sda5 sda6 >
[    1.238743] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.238775] Freeing unused kernel memory: 656k freed
[    1.240035] Write protecting the kernel text: 4676k
[    1.240097] Write protecting the kernel read-only data: 1840k
[    1.318013] udev: starting version 151
[    1.356672] usb 2-1: configuration #1 chosen from 1 choice
[    1.732299] usbcore: registered new interface driver hiddev
[    1.749312] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[    1.749490] generic-usb 0003:03F0:0024.0001: input,hidraw0: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:1d.0-1/input0
[    1.749540] usbcore: registered new interface driver usbhid
[    1.749545] usbhid: v2.6:USB HID core driver
[    1.750534] FDC 0 is a post-1991 82077
[    1.754759] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
[    1.754768] Copyright (c) 1999-2006 Intel Corporation.
[    1.754840] e1000 0000:01:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.027392] e1000: 0000:01:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:08:74:18:aa:7b
[    2.062877] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    2.214628] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    2.214638] EXT4-fs (sda5): write access will be enabled during recovery
[    2.590250] EXT4-fs (sda5): recovery complete
[    2.593618] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    6.524049] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    6.667500] usb 1-3: configuration #1 chosen from 1 choice
[   14.747911] Adding 2044920k swap on /dev/sda6.  Priority:-1 extents:1 across:2044920k 
[   14.818389] udev: starting version 151
[   15.103306] lp: driver loaded but no devices found
[   15.257338] Linux agpgart interface v0.103
[   15.269679] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.317295] intel_rng: FWH not detected
[   15.582804] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   15.583073] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   15.650504] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   15.663328] psmouse serio1: ID: 00 00 3c
[   15.734532] logips2pp: Detected unknown logitech mouse model 8
[   15.752496] Initializing USB Mass Storage driver...
[   15.836131] parport_pc 00:09: reported by Plug and Play ACPI
[   15.836193] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   15.856113] scsi4 : SCSI emulation for USB Mass Storage devices
[   15.867208] usb-storage: device found at 3
[   15.867215] usb-storage: waiting for device to settle before scanning
[   15.875802] scsi5 : SCSI emulation for USB Mass Storage devices
[   15.885456] usbcore: registered new interface driver usb-storage
[   15.885464] USB Mass Storage support registered.
[   15.886131] usb-storage: device found at 3
[   15.886137] usb-storage: waiting for device to settle before scanning
[   15.928368] lp0: using parport0 (interrupt-driven).
[   16.081983] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.087631] [drm] Initialized drm 1.1.0 20060810
[   16.132527] type=1505 audit(1274827623.034:2):  operation="profile_load" pid=523 name="/sbin/dhclient3"
[   16.133394] type=1505 audit(1274827623.034:3):  operation="profile_load" pid=523 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.133857] type=1505 audit(1274827623.034:4):  operation="profile_load" pid=523 name="/usr/lib/connman/scripts/dhclient-script"
[   16.193978] dell-wmi: No known WMI GUID found
[   16.210220] usbcore: registered new interface driver usbserial
[   16.210617] ppdev: user-space parallel port driver
[   16.210715] USB Serial support registered for generic
[   16.211203] usbcore: registered new interface driver usbserial_generic
[   16.211209] usbserial: USB Serial Driver core
[   16.262496] USB Serial support registered for GSM modem (1-port)
[   16.263083] option 1-3:1.0: GSM modem (1-port) converter detected
[   16.263568] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[   16.263598] option 1-3:1.1: GSM modem (1-port) converter detected
[   16.264180] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[   16.264313] usbcore: registered new interface driver option
[   16.264319] option: v0.7.2:USB Driver for GSM modems
[   16.298419] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input4
[   16.533191] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.533204] i915 0000:00:02.0: setting latency timer to 64
[   16.596392] [drm] set up 15M of stolen space
[   16.739053] [drm] initialized overlay support
[   17.052958] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.069762] type=1505 audit(1274827623.970:5):  operation="profile_load" pid=637 name="/usr/share/gdm/guest-session/Xsession"
[   17.088471] type=1505 audit(1274827623.990:6):  operation="profile_replace" pid=639 name="/sbin/dhclient3"
[   17.089368] type=1505 audit(1274827623.990:7):  operation="profile_replace" pid=639 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.089856] type=1505 audit(1274827623.990:8):  operation="profile_replace" pid=639 name="/usr/lib/connman/scripts/dhclient-script"
[   17.139813] type=1505 audit(1274827624.038:9):  operation="profile_load" pid=642 name="/usr/bin/evince"
[   17.179252] type=1505 audit(1274827624.078:10):  operation="profile_load" pid=642 name="/usr/bin/evince-previewer"
[   17.215990] type=1505 audit(1274827624.114:11):  operation="profile_load" pid=642 name="/usr/bin/evince-thumbnailer"
[   17.283854] fb0: inteldrmfb frame buffer device
[   17.283860] registered panic notifier
[   17.283879] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.283967]   alloc irq_desc for 17 on node -1
[   17.283972]   alloc kstat_irqs on node -1
[   17.283985] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   17.284088] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   17.303792] vga16fb: initializing
[   17.303803] vga16fb: mapped to 0xc00a0000
[   17.303811] vga16fb: not registering due to another framebuffer present
[   17.386353] Console: switching to colour frame buffer device 128x48
[   17.692106] intel8x0_measure_ac97_clock: measured 53673 usecs (2586 samples)
[   17.692112] intel8x0: clocking to 48000
[   19.334022] PPP BSD Compression module registered
[   19.482008] PPP Deflate Compression module registered
[   25.151159] usb-storage: device scan complete
[   25.152527] usb-storage: device scan complete
[   25.154151] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   25.158623] scsi 5:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[   28.176258] option: option_instat_callback: error -108
[   28.176641] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[   28.176671] option 1-3:1.0: device disconnected
[   35.150461] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[   35.150492] option 1-3:1.1: device disconnected
[   35.260089] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[   35.424183] option 1-3:1.1: GSM modem (1-port) converter detected
[   35.424394] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[   35.438104] option 1-3:1.0: GSM modem (1-port) converter detected
[   35.438371] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[   35.463688] sr1: scsi-1 drive
[   35.463967] sr 4:0:0:0: Attached scsi CD-ROM sr1
[   35.464167] sr 4:0:0:0: Attached scsi generic sg2 type 5
[   35.466817] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   35.501618] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   38.706611] ISO 9660 Extensions: Microsoft Joliet Level 1
[   38.790988] ISOFS: changing to secondary root
jamie@jamie-desktop:~$
``` 


-smiley

---

### Post by durand on 2010-05-25
Does it crash much if you don't use firefox? It could be a flash bug? The dmesg doesn't show any serious problems occuring. What about if you play a video? Have you tried installing the video driver?

---

### Post by kansasnoob on 2010-05-25
Please post the output of:

```
lspci | grep VGA
```

---

### Post by smileyacid on 2010-05-25
It seems to play videos fine + no i have not installed a video driver do you recomend that ? any one in particular ?

would there be a generic one for intel video

-smiley

---

### Post by smileyacid on 2010-05-25
lspci | grep VGA :
hope this helps

jamie@jamie-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
jamie@jamie-desktop:~$ 


-smiley

---

### Post by kansasnoob on 2010-05-25
Just needed the specific graphics card info. You're not alone:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

There are a number of possible work-arounds there.

---

### Post by theozzlives on 2010-05-25
> **libssd said:**
> Try an earlier release (9.04 = Jaunty, or 9.10 (Karmic). Looking at install surveys, they have fewer problems than 10.4, and are more likely to work out of the box.

Karmic is crap! Lucid Alpha1 was better than Karmic final.

---

### Post by kansasnoob on 2010-05-25
BTW always check the release notes:

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes](http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes)

---

### Post by kansasnoob on 2010-05-25
> **theozzlives said:**
> Karmic is crap! Lucid Alpha1 was better than Karmic final.

Karmic works great on my Intel machine, but it's unusable on my VIA hardware :(

---

### Post by smileyacid on 2010-05-25
If it helps i installed from a USB it worked fine but this was because my cd caused similar problems at boot 
live CD would boot black with red + blue squares then just black

-smiley

---

### Post by kansasnoob on 2010-05-25
> **smileyacid said:**
> If it helps i installed from a USB it worked fine but this was because my cd caused similar problems at boot 
live CD would boot black with red + blue squares then just black

-smiley

Did you not see the link I posted:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

You have an Intel i845 graphics chip so you'll have to try one or more of those workarounds.

---

### Post by smileyacid on 2010-05-25
Sorry no I was busy ill have a look + try something out cheers kansasnoob
thanks for all your help + everyone else I hope something works 

thanks for now -smiley

---

