---
title: "High CPU usage, nothing running."
date: 2010-08-21
forum: New to Ubuntu
---

### Post by jotto! on 2010-08-21
I thought this was just a MS problem but its becoming a real pain. 
With nothing running ( that Im aware of ) the system just seems slow. I have a constant CPU usage of around 70% and have no idea why.
[IMG]http://i617.photobucket.com/albums/tt252/my79vette/Screenshot-1.png[/IMG]

Everything is up to date but I am at a loss as to where to start looking.
When I check the running processes, I see sytem monitor at about 25% Firefox-bin similar and plugin-container also about 25-30%.

Has a recent update caused any issues with firefox or is something weird just going on with my system?
TIA.

---

### Post by phillw on 2010-08-21
If you will post the details of your computer, that will help.

I.E. processor, amount of RAM etc. Can you post the output of the following ```
cat /proc/cpuinfo
cat /proc/meminfo
free
dmesg
lspci
```
please use code tags around the dmesg output :-)

Regards,

Phill.

---

### Post by LightningCrash on 2010-08-21
get a few lines of vmstat 5

might give you an idea on where the waiting is taking place... kernel can take up a lot and not show anything in processes

---

### Post by jotto! on 2010-08-21
Ok, Im running a fairly old system, AMD 64bit 3200 cpu, 1.5 GB ram. All was fine and dandy until fairly recently.

cat /proc/cpuinfo

```
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 12
model name    : AMD Athlon(tm) 64 Processor 3200+
stepping    : 0
cpu MHz        : 1000.000
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up
bogomips    : 2042.80
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

```

cat /proc/meminfo

```
MemTotal:        1544084 kB
MemFree:          718640 kB
Buffers:           66428 kB
Cached:           407332 kB
SwapCached:            0 kB
Active:           425524 kB
Inactive:         335864 kB
Active(anon):     292544 kB
Inactive(anon):       32 kB
Active(file):     132980 kB
Inactive(file):   335832 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        663496 kB
HighFree:          67580 kB
LowTotal:         880588 kB
LowFree:          651060 kB
SwapTotal:       3018744 kB
SwapFree:        3018744 kB
Dirty:               120 kB
Writeback:             0 kB
AnonPages:        287676 kB
Mapped:            83364 kB
Shmem:              4952 kB
Slab:              34104 kB
SReclaimable:      24320 kB
SUnreclaim:         9784 kB
KernelStack:        2120 kB
PageTables:         6496 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3790784 kB
Committed_AS:    1162012 kB
VmallocTotal:     122880 kB
VmallocUsed:       48516 kB
VmallocChunk:      63996 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       28664 kB
DirectMap4M:      880640 kB

```

free

```
             total       used       free     shared    buffers     cached
Mem:       1544084     825444     718640          0      66448     407328
-/+ buffers/cache:     351668    1192416
Swap:      3018744          0    3018744
```

dmesg

```
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:9ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390015
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=b41b6873-3c2a-48e2-a217-b0323e474f31 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7863680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005fff0)
[    0.000000] Memory: 1534628k/1572800k available (4679k kernel code, 36728k reserved, 2124k data, 660k init, 663496k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1021.400 MHz processor.
[    0.008008] Calibrating delay loop (skipped), value calculated using timer frequency.. 2042.80 BogoMIPS (lpj=4085600)
[    0.008044] Security Framework initialized
[    0.008094] AppArmor: AppArmor initialized
[    0.008108] Mount-cache hash table entries: 512
[    0.008324] Initializing cgroup subsys ns
[    0.008331] Initializing cgroup subsys cpuacct
[    0.008339] Initializing cgroup subsys memory
[    0.008353] Initializing cgroup subsys devices
[    0.008359] Initializing cgroup subsys freezer
[    0.008363] Initializing cgroup subsys net_cls
[    0.008396] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008402] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008409] mce: CPU supports 5 MCE banks
[    0.008439] Performance Events: AMD PMU driver.
[    0.008452] ... version:                0
[    0.008456] ... bit width:              48
[    0.008460] ... generic registers:      4
[    0.008464] ... value mask:             0000ffffffffffff
[    0.008468] ... max period:             00007fffffffffff
[    0.008472] ... fixed-purpose events:   0
[    0.008476] ... event mask:             000000000000000f
[    0.008484] Checking 'hlt' instruction... OK.
[    0.025336] SMP alternatives: switching to UP code
[    0.036964] Freeing SMP alternatives: 19k freed
[    0.036997] ACPI: Core revision 20090903
[    0.048047] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.048061] ftrace: allocating 21780 entries in 43 pages
[    0.052148] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056184] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.095874] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[    0.096001] Brought up 1 CPUs
[    0.096001] Total of 1 processors activated (2042.80 BogoMIPS).
[    0.096001] CPU0 attaching NULL sched-domain.
[    0.096001] devtmpfs: initialized
[    0.096001] regulator: core version 0.5
[    0.096001] Time:  0:45:22  Date: 08/22/10
[    0.096001] NET: Registered protocol family 16
[    0.096001] EISA bus registered
[    0.096001] ACPI: bus type pci registered
[    0.099298] PCI: PCI BIOS revision 2.10 entry at 0xfbac0, last bus=1
[    0.099302] PCI: Using configuration type 1 for base access
[    0.100947] bio: create slab <bio-0> at 0
[    0.101927] ACPI: EC: Look up EC in DSDT
[    0.106515] ACPI Warning: Package List length (0x5) larger than NumElements count (0x4), truncated
[    0.106525]  (20090903/dsobject-515)
[    0.112090] ACPI: Interpreter enabled
[    0.112106] ACPI: (supports S0 S1 S4 S5)
[    0.112156] ACPI: Using IOAPIC for interrupt routing
[    0.119817] ACPI: No dock devices found.
[    0.119982] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.120064] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xa0000000-0xbfffffff]
[    0.120168] pci 0000:00:01.0: supports D1
[    0.120220] pci 0000:00:0e.0: reg 10 32bit mmio: [0xd3000000-0xd3003fff]
[    0.120230] pci 0000:00:0e.0: reg 14 io port: [0x9000-0x90ff]
[    0.120272] pci 0000:00:0e.0: supports D1 D2
[    0.120277] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.120284] pci 0000:00:0e.0: PME# disabled
[    0.120320] pci 0000:00:0f.0: reg 10 io port: [0x9400-0x9407]
[    0.120329] pci 0000:00:0f.0: reg 14 io port: [0x9800-0x9803]
[    0.120338] pci 0000:00:0f.0: reg 18 io port: [0x9c00-0x9c07]
[    0.120347] pci 0000:00:0f.0: reg 1c io port: [0xa000-0xa003]
[    0.120357] pci 0000:00:0f.0: reg 20 io port: [0xa400-0xa40f]
[    0.120366] pci 0000:00:0f.0: reg 24 io port: [0xa800-0xa8ff]
[    0.120436] pci 0000:00:0f.1: reg 20 io port: [0xac00-0xac0f]
[    0.120515] pci 0000:00:10.0: reg 20 io port: [0xb000-0xb01f]
[    0.120541] pci 0000:00:10.0: supports D1 D2
[    0.120546] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.120552] pci 0000:00:10.0: PME# disabled
[    0.120602] pci 0000:00:10.1: reg 20 io port: [0xb400-0xb41f]
[    0.120628] pci 0000:00:10.1: supports D1 D2
[    0.120633] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.120639] pci 0000:00:10.1: PME# disabled
[    0.120686] pci 0000:00:10.2: reg 20 io port: [0xb800-0xb81f]
[    0.120713] pci 0000:00:10.2: supports D1 D2
[    0.120717] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.120723] pci 0000:00:10.2: PME# disabled
[    0.120771] pci 0000:00:10.3: reg 20 io port: [0xbc00-0xbc1f]
[    0.120797] pci 0000:00:10.3: supports D1 D2
[    0.120801] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.120808] pci 0000:00:10.3: PME# disabled
[    0.120841] pci 0000:00:10.4: reg 10 32bit mmio: [0xd3004000-0xd30040ff]
[    0.120882] pci 0000:00:10.4: supports D1 D2
[    0.120886] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.120892] pci 0000:00:10.4: PME# disabled
[    0.120953] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.121007] pci 0000:00:11.5: reg 10 io port: [0xc000-0xc0ff]
[    0.121051] pci 0000:00:11.5: supports D1 D2
[    0.121195] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd0ffffff]
[    0.121204] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.121212] pci 0000:01:00.0: reg 18 32bit mmio: [0xd1000000-0xd1ffffff]
[    0.121227] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.121274] pci 0000:00:01.0: bridge 32bit mmio: [0xd0000000-0xd2ffffff]
[    0.121282] pci 0000:00:01.0: bridge 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.121292] pci_bus 0000:00: on NUMA node 0
[    0.121301] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.173895] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
[    0.174182] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.174474] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 *7 10 11 12)
[    0.174730] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.174977] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.175217] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.175477] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 *10 11 12)
[    0.175709] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.175976] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.176256] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.176565] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.176835] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[    0.177039] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.177044] vgaarb: loaded
[    0.177249] SCSI subsystem initialized
[    0.177371] libata version 3.00 loaded.
[    0.177494] usbcore: registered new interface driver usbfs
[    0.177517] usbcore: registered new interface driver hub
[    0.177562] usbcore: registered new device driver usb
[    0.177784] ACPI: WMI: Mapper loaded
[    0.177788] PCI: Using ACPI for IRQ routing
[    0.177994] NetLabel: Initializing
[    0.177997] NetLabel:  domain hash size = 128
[    0.178000] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.178024] NetLabel:  unlabeled traffic allowed by default
[    0.178110] Switching to clocksource tsc
[    0.180001] AppArmor: AppArmor Filesystem Enabled
[    0.180001] pnp: PnP ACPI init
[    0.180001] ACPI: bus type pnp registered
[    0.183807] pnp: PnP ACPI: found 11 devices
[    0.183812] ACPI: ACPI bus type pnp unregistered
[    0.183819] PnPBIOS: Disabled by ACPI PNP
[    0.183841] system 00:00: iomem range 0xd4c00-0xd7fff has been reserved
[    0.183848] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.183854] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.183861] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.183868] system 00:00: iomem range 0x5fff0000-0x5fffffff could not be reserved
[    0.183875] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.183882] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.183888] system 00:00: iomem range 0x100000-0x5ffeffff could not be reserved
[    0.183895] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.183902] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.183908] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.183921] system 00:02: ioport range 0x400-0x47f has been reserved
[    0.183927] system 00:02: ioport range 0x500-0x50f has been reserved
[    0.183938] system 00:03: ioport range 0xb78-0xb7b has been reserved
[    0.183944] system 00:03: ioport range 0xf78-0xf7b has been reserved
[    0.183951] system 00:03: ioport range 0xa78-0xa7b has been reserved
[    0.183957] system 00:03: ioport range 0xe78-0xe7b has been reserved
[    0.183963] system 00:03: ioport range 0xbbc-0xbbf has been reserved
[    0.183969] system 00:03: ioport range 0xfbc-0xfbf has been reserved
[    0.183975] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.218821] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.218826] pci 0000:00:01.0:   IO window: disabled
[    0.218834] pci 0000:00:01.0:   MEM window: 0xd0000000-0xd2ffffff
[    0.218842] pci 0000:00:01.0:   PREFETCH window: 0xc0000000-0xcfffffff
[    0.218861] pci 0000:00:01.0: setting latency timer to 64
[    0.218870] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.218876] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.218882] pci_bus 0000:01: resource 1 mem: [0xd0000000-0xd2ffffff]
[    0.218888] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.218954] NET: Registered protocol family 2
[    0.219126] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.219810] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.221256] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.222081] TCP: Hash tables configured (established 131072 bind 65536)
[    0.222086] TCP reno registered
[    0.222241] NET: Registered protocol family 1
[    0.222270] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.222383] pci 0000:01:00.0: Boot video device
[    0.222511] Simple Boot Flag value 0x30 read from CMOS RAM was invalid
[    0.222516] Simple Boot Flag at 0x37 set to 0x1
[    0.222719] cpufreq-nforce2: No nForce2 chipset.
[    0.222765] Scanning for low memory corruption every 60 seconds
[    0.222950] audit: initializing netlink socket (disabled)
[    0.222977] type=2000 audit(1282437922.221:1): initialized
[    0.242767] Trying to unpack rootfs image as initramfs...
[    0.266085] highmem bounce pool size: 64 pages
[    0.266098] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.268916] VFS: Disk quotas dquot_6.5.2
[    0.269025] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.270119] fuse init (API version 7.13)
[    0.270280] msgmni has been set to 1703
[    0.274514] alg: No test for stdrng (krng)
[    0.274636] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.274641] io scheduler noop registered
[    0.274645] io scheduler anticipatory registered
[    0.274649] io scheduler deadline registered
[    0.274730] io scheduler cfq registered (default)
[    0.274920] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.274960] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.275121] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.275128] ACPI: Power Button [PWRB]
[    0.275229] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.275234] ACPI: Power Button [PWRF]
[    0.275775] processor LNXCPU:00: registered as cooling_device0
[    0.287339] thermal LNXTHERM:01: registered as thermal_zone0
[    0.287355] ACPI: Thermal Zone [THRM] (20 C)
[    0.292074] isapnp: Scanning for PnP cards...
[    0.302699] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.304911] brd: module loaded
[    0.305787] loop: module loaded
[    0.305966] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.306688] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.306693] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.306703]   alloc irq_desc for 20 on node -1
[    0.306707]   alloc kstat_irqs on node -1
[    0.306721] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.306808] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    0.307350] Fixed MDIO Bus: probed
[    0.307411] PPP generic driver version 2.4.2
[    0.307473] tun: Universal TUN/TAP device driver, 1.6
[    0.307477] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.307605] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.307631]   alloc irq_desc for 21 on node -1
[    0.307635]   alloc kstat_irqs on node -1
[    0.307642] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.307673] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.307735] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.307823] ehci_hcd 0000:00:10.4: irq 21, io mem 0xd3004000
[    0.354440] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.354620] usb usb1: configuration #1 chosen from 1 choice
[    0.354673] hub 1-0:1.0: USB hub found
[    0.354691] hub 1-0:1.0: 8 ports detected
[    0.354791] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.354817] uhci_hcd: USB Universal Host Controller Interface driver
[    0.354892] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.354903] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.354969] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.354998] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b000
[    0.355153] usb usb2: configuration #1 chosen from 1 choice
[    0.355199] hub 2-0:1.0: USB hub found
[    0.355212] hub 2-0:1.0: 2 ports detected
[    0.355288] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.355296] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.355349] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.355374] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b400
[    0.355528] usb usb3: configuration #1 chosen from 1 choice
[    0.355574] hub 3-0:1.0: USB hub found
[    0.355586] hub 3-0:1.0: 2 ports detected
[    0.355667] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.355676] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.355730] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.355754] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b800
[    0.355918] usb usb4: configuration #1 chosen from 1 choice
[    0.355964] hub 4-0:1.0: USB hub found
[    0.355976] hub 4-0:1.0: 2 ports detected
[    0.356048] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.356058] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.356118] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.356143] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000bc00
[    0.356303] usb usb5: configuration #1 chosen from 1 choice
[    0.356355] hub 5-0:1.0: USB hub found
[    0.356368] hub 5-0:1.0: 2 ports detected
[    0.356517] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.362740] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.362758] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.363000] mice: PS/2 mouse device common for all mice
[    0.363191] rtc_cmos 00:05: RTC can wake from S4
[    0.363269] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.363318] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.363546] device-mapper: uevent: version 1.0.3
[    0.365621] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.366525] device-mapper: multipath: version 1.1.0 loaded
[    0.366531] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.368068] EISA: Probing bus 0 at eisa.0
[    0.368112] EISA: Detected 0 cards.
[    0.370416] cpuidle: using governor ladder
[    0.370420] cpuidle: using governor menu
[    0.371236] TCP cubic registered
[    0.371524] NET: Registered protocol family 10
[    0.372324] lo: Disabled Privacy Extensions
[    0.372920] NET: Registered protocol family 17
[    0.372973] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[    0.373056] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x2
[    0.373061] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x6
[    0.373066] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[    0.373072] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    0.373124] Marking TSC unstable due to cpufreq changes
[    0.378934] Switching to clocksource acpi_pm
[    0.383326] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.383491] Using IPI No-Shortcut mode
[    0.383575] PM: Resume from disk failed.
[    0.383593] registered taskstats version 1
[    0.383817]   Magic number: 6:896:759
[    0.383916] rtc_cmos 00:05: setting system clock to 2010-08-22 00:45:23 UTC (1282437923)
[    0.383919] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.383921] EDD information not available.
[    0.715558] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    0.741476] Freeing initrd memory: 7780k freed
[    0.882840] isapnp: No Plug & Play device found
[    0.882872] Freeing unused kernel memory: 660k freed
[    0.884060] Write protecting the kernel text: 4680k
[    0.884090] Write protecting the kernel read-only data: 1844k
[    0.905003] udev: starting version 151
[    0.906336] usb 1-3: configuration #1 chosen from 1 choice
[    1.101475] sata_via 0000:00:0f.0: version 2.4
[    1.101502] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.101554] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.103569] Floppy drive(s): fd0 is 1.44M
[    1.107884] scsi0 : sata_via
[    1.112141] scsi1 : sata_via
[    1.112238] ata1: SATA max UDMA/133 cmd 0x9400 ctl 0x9800 bmdma 0xa400 irq 20
[    1.112241] ata2: SATA max UDMA/133 cmd 0x9c00 ctl 0xa000 bmdma 0xa408 irq 20
[    1.112301] pata_via 0000:00:0f.1: version 0.3.4
[    1.112320] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.114651] scsi2 : pata_via
[    1.114834] scsi3 : pata_via
[    1.116054] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xac00 irq 14
[    1.116057] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xac08 irq 15
[    1.116128]   alloc irq_desc for 22 on node -1
[    1.116131]   alloc kstat_irqs on node -1
[    1.116140] skge 0000:00:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.116150] skge 0000:00:0e.0: PCI: Disallowing DAC for device
[    1.116184] skge 1.13 addr 0xd3000000 irq 22 chip Yukon rev 1
[    1.116786] skge eth0: addr 00:50:8d:5c:c3:eb
[    1.120850] FDC 0 is a post-1991 82077
[    1.288358] ata3.01: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A105, max UDMA/33
[    1.304240] ata3.01: configured for UDMA/33
[    1.316015] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.481156] ata1.00: ATA-7: Maxtor 6L300S0, BACE1G20, max UDMA/133
[    1.481159] ata1.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.497162] ata1.00: configured for UDMA/133
[    1.497289] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L300S0   BACE PQ: 0 ANSI: 5
[    1.497466] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.497713] sd 0:0:0:0: [sda] 586114704 512-byte logical blocks: (300 GB/279 GiB)
[    1.497755] sd 0:0:0:0: [sda] Write Protect is off
[    1.497758] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.497779] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.497904]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.559237] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.700014] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.920545] ata2.00: ATA-6: ST3160023AS, 3.05, max UDMA/133
[    1.920548] ata2.00: 312581808 sectors, multi 16: LBA48 
[    1.936431] ata2.00: configured for UDMA/133
[    1.936511] scsi 1:0:0:0: Direct-Access     ATA      ST3160023AS      3.05 PQ: 0 ANSI: 5
[    1.936640] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.936881] sd 1:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.936918] sd 1:0:0:0: [sdb] Write Protect is off
[    1.936921] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.936940] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.937053]  sdb:
[    1.940819] scsi 2:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A105 PQ: 0 ANSI: 5
[    1.953397] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.953400] Uniform CD-ROM driver Revision: 3.20
[    1.953488] sr 2:0:1:0: Attached scsi CD-ROM sr0
[    1.953545] sr 2:0:1:0: Attached scsi generic sg2 type 5
[    1.953879]  sdb1
[    1.954188] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.549774] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   15.886468] Adding 3018744k swap on /dev/sda6.  Priority:-1 extents:1 across:3018744k 
[   15.924996] udev: starting version 151
[   16.226768] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.274982] ACPI: resource vt596_smbus [0x500-0x507] conflicts with ACPI region SM06 [0x506-0x506]
[   16.274987] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.347952] type=1505 audit(1282434339.460:2):  operation="profile_load" pid=458 name="/sbin/dhclient3"
[   16.348397] type=1505 audit(1282434339.464:3):  operation="profile_load" pid=458 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.348543] type=1505 audit(1282434339.464:4):  operation="profile_load" pid=458 name="/usr/lib/connman/scripts/dhclient-script"
[   16.399296] vga16fb: initializing
[   16.399303] vga16fb: mapped to 0xc00a0000
[   16.399402] fb0: VGA16 VGA frame buffer device
[   16.424765] Linux agpgart interface v0.103
[   16.445701] psmouse serio1: ID: 10 00 64
[   16.497685] lp: driver loaded but no devices found
[   16.498720] logips2pp: Detected unknown logitech mouse model 127
[   16.986077] nvidia: module license 'NVIDIA' taints kernel.
[   16.986084] Disabling lock debugging due to kernel taint
[   17.370161] agpgart-amd64 0000:00:00.0: AGP bridge [1106/3188]
[   17.658707] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   17.821386] agpgart-amd64 0000:00:00.0: AGP aperture is 512M @ 0xa0000000
[   17.918627] Console: switching to colour frame buffer device 80x30
[   17.933754]   alloc irq_desc for 16 on node -1
[   17.933760]   alloc kstat_irqs on node -1
[   17.933769] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.935050] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
[   18.485686] type=1505 audit(1282434341.600:5):  operation="profile_load" pid=696 name="/usr/share/gdm/guest-session/Xsession"
[   18.505284] type=1505 audit(1282434341.620:6):  operation="profile_replace" pid=697 name="/sbin/dhclient3"
[   18.505573] type=1505 audit(1282434341.620:7):  operation="profile_replace" pid=697 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.505731] type=1505 audit(1282434341.620:8):  operation="profile_replace" pid=697 name="/usr/lib/connman/scripts/dhclient-script"
[   18.544936] type=1505 audit(1282434341.660:9):  operation="profile_load" pid=699 name="/usr/bin/evince"
[   18.565534] skge eth0: enabling interface
[   18.577157] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   18.577293] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   18.578338] type=1505 audit(1282434341.692:10):  operation="profile_load" pid=699 name="/usr/bin/evince-previewer"
[   18.591359] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.594068] type=1505 audit(1282434341.708:11):  operation="profile_load" pid=699 name="/usr/bin/evince-thumbnailer"
[   19.277151] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   19.277159] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   19.277160] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   19.277162] vboxdrv: the usage of hardware performance counters by
[   19.277163] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   19.277167] vboxdrv: Found 1 processor cores.
[   19.278959] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   19.278963] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   19.427976] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   19.427990] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   19.428073] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   20.289085] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   20.308268] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.587253] ppdev: user-space parallel port driver
[   30.808029] eth0: no IPv6 routers present

```

lspci

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0e.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 Ultra] (rev a1)

```

Not sure what any of that means! lol.

---

### Post by earthpigg on 2010-08-21
> High CPU usage, nothing running.

based on your screenshot, this is not true.

it is ironic, but the graphical system monitor you are using? it itself uses a ***huge*** amount of CPU power to run. you can see this in the system monitor itself. go to processes and sort by CPU%.

take it off your panel & dont run it.

i suggest that you install & use htop instead.

once that is done, we can look at what else we need to do using htop as our tool instead of gnome system monitor. 

sort by CPU, see what is towards the top.

---

### Post by jotto! on 2010-08-21
vmstat 5

```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  0      0 674888  66668 407316    0    0   323    77  516 1748 37  8 53  2
 2  0      0 674896  66676 407340    0    0     0    14  596 1746 65  9 25  1
 0  0      0 677484  66684 407340    0    0     0    29  464 1208 63  7 29  0
 0  0      0 676872  66692 407340    0    0     0    22  351 1087 63  8 28  0
 2  0      0 674284  66692 407340    0    0     0     0  526 1993 65 11 24  0
 1  0      0 674284  66700 407340    0    0     0     3  644 2281 76 10 15  0
 2  0      0 674268  66700 407340    0    0     0     0  676 2574 78 11 11  0
 3  0      0 675024  66700 407340    0    0     0     0  615 2307 78 11 11  0
 1  0      0 671376  66700 407336    0    0     0     0  496 1610 75 14 10  0
 0  0      0 673980  66700 407336    0    0     0     1  425 1357 72 13 14  0
 1  1      0 668244  66736 408416    0    0   179  3122  730 3110 79 17  4  0
 6  1      0 629764  66784 410028    0    0   358    39  755 2053 86 12  0  2
 3  0      0 610224  66792 427204    0    0  3414    43  741 2348 87 13  0  0
 3  0      0 601528  66800 436216    0    0  1775    10  698 2142 90 10  0  0
 3  1      0 588756  66808 440080    0    0   754     3  736 2895 89 11  0  0
 5  0      0 587396  66816 443852    0    0   698     3  734 1467 90 10  0  0
 3  0      0 601788  66824 445436    0    0   270     3  539 1283 91  9  0  0


```

---

### Post by LightningCrash on 2010-08-21
there is definitely something running in userspace doing that!

run `top` and see what is at the top of the list. (you can CTRL+C or press Q to exit)


(personally i suspect some sort of indexing critter)

---

### Post by jotto! on 2010-08-21
> **earthpigg said:**
> based on your screenshot, this is not true.

it is ironic, but the graphical system monitor you are using? it itself uses a ***huge*** amount of CPU power to run. you can see this in the system monitor itself. go to processes and sort by CPU%.

take it off your panel & dont run it.

i suggest that you install & use htop instead.

once that is done, we can look at what else we need to do using htop as our tool instead of gnome system monitor. 

sort by CPU, see what is towards the top.

The CPU usage never used to be this high, even when using the graphical interface...something has happened to cause it recently but I do not know what.

Just checked the processes again, highest CPU was 8% with sys monitor, firefox and others mentioned before were 0, Graph still showing 95%!!! and system slow.

---

### Post by jotto! on 2010-08-21
top

```
876 root      20   0  103m  57m  10m S  1.3  3.8   6:15.66 Xorg               
 1229 jotto     20   0 90216  10m 8140 S  0.3  0.7   0:01.56 gnome-settings-    
 1240 jotto     20   0 57216  37m  10m S  0.3  2.5   0:49.62 compiz             
 1587 jotto     20   0  402m  88m  27m S  0.3  5.9   2:12.27 firefox-bin        
 2085 jotto     20   0 18968 8676 6940 S  0.3  0.6   0:05.42 awn-applet         
 2352 jotto     20   0 47536  12m  10m S  0.3  0.9   0:00.68 gnome-terminal     
 2371 jotto     20   0  2548 1204  904 R  0.3  0.1   0:00.14 top                
    1 root      20   0  2804 1624 1164 S  0.0  0.1   0:00.35 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd          
```

lost some of the others but these were at the top and had big numbers next to them.

What are all these read outs telling you? would be nice to know what Im looking at.

---

### Post by jotto! on 2010-08-21
Ok, Xorg is the main kernel? the operating system itself?

Sys monitor was CPU hungry...around 20% Xorg is between 5 and 20%. When sys monitor was reporting 95% usage, top was showing a peak of about 45%!

Maybe im just being paranoid. :lolflag:

Just restarted firefox and i have several pages set as my homepage as it were. Some have animations and flash on them. firefox-bin and plugin- container are both around 20-25% each.
Perhaps I will try a different browser and see what happens.

---

### Post by earthpigg on 2010-08-21
Xorg is what gives us a graphical display, something different than the kernel itself. Xorg talks to the kernel (linux itself is just the kernel, strictly speaking), and the kernel gives Xorg the resources it needs.

flash animations will always be CPU intensive. unfortunately.

---

### Post by jotto! on 2010-08-21
Thanks for that.
Have had my home pages set since I first installed ubuntu so am still unsure why this is happening now.

Just tried chromium and sett same pages and cpu usage is down.

Something is going on with firefox.

---

### Post by walt.smith1960 on 2010-08-21
I'm seeing something similar when viewing flash videos.  I think it was Carlee that observed Flash in Linux sucks. It looks like that to me.  My desktop is a single AMD athlon 2600+ and it'll run 95%+ CPU usage continuously when streaming  flash videos from some sites but not all.  Close Firefox and after a few seconds CPU drops to maybe 7%.  Chromium seems to be a *little* better.

---

### Post by earthpigg on 2010-08-21
> **jotto! said:**
> Something is going on with firefox.

good, now we have the problem isolated.

it could have been an addon update.

want to try disabling them all and compare CPU usage?

if that's it, then we can narrow down which addon it is by disabling/enabling them a few at a time and observing results.

---

### Post by jotto! on 2010-08-21
> **earthpigg said:**
> good, now we have the problem isolated.

it could have been an addon update.

want to try disabling them all and compare CPU usage?

if that's it, then we can narrow down which addon it is by disabling/enabling them a few at a time and observing results.

Disabled all add ons, firefox running at about 20-25%. plugin container nowhere to be seen. 
Strangely, enabling them all again has had little difference.

2.03am here..time to get some shut eye. Will start working on it again in a few hours! Thanks for all the replies so far, appreciate it.

---

### Post by lovinglinux on 2010-08-22
> **jotto! said:**
> Just tried chromium and sett same pages and cpu usage is down.

Something is going on with firefox.

Probably not Firefox. Chrome comes with a bundled flash version and does not use the one from your system. So probably you have a bad plugin installed that is being used by Firefox.

Install and run [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/") to make sure you have the proper flash plugin installed.

> **jotto! said:**
> When I check the running processes, I see sytem monitor at about 25% Firefox-bin similar and plugin-container also about 25-30%.

Has a recent update caused any issues with firefox or is something weird just going on with my system?
TIA.

Since Firefox 3.6.4, the flash runs isolated inside a process called **plugin-container**. This is done to avoid crashing the browser if the plugin crashes.

To reduce CPU usage, install [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") and only allow pages were you need to view flash content.

[Ablock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") might help as well.

> **jotto! said:**
> Just restarted firefox and i have several pages set as my homepage as it were. Some have animations and flash on them. firefox-bin and plugin- container are both around 20-25% each.

Use [BarTab]("https://addons.mozilla.org/en-US/firefox/addon/67651/") extension. It prevents pages from being loaded until they are needed. So when you start your browser with several pages set as home-page, they don't suck your CPU and memory.

To improve flash performance see [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

---

### Post by jotto! on 2010-08-23
> **lovinglinux said:**
> Probably not Firefox. Chrome comes with a bundled flash version and does not use the one from your system. So probably you have a bad plugin installed that is being used by Firefox.

Install and run [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/") to make sure you have the proper flash plugin installed.



Since Firefox 3.6.4, the flash runs isolated inside a process called **plugin-container**. This is done to avoid crashing the browser if the plugin crashes.

To reduce CPU usage, install [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") and only allow pages were you need to view flash content.

[Ablock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") might help as well.



Use [BarTab]("https://addons.mozilla.org/en-US/firefox/addon/67651/") extension. It prevents pages from being loaded until they are needed. So when you start your browser with several pages set as home-page, they don't suck your CPU and memory.

To improve flash performance see [Flash Optimization]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html").


Thanks for that, will check out the links and install some of the items you mentioned.
It is indeed a flash problem.
Has adobe recently updated their product? I know on windows my son had a new version installed recently. This would possibly be around the same sort of time that I noticed this system running slow or is it just a coincidence?
As I said before, system was fine as it was and watching flash videos etc all seemed to be OK. Now, it just seems to hog the CPU.

---

### Post by kennedyvelez on 2010-09-22
When you're done with this, you will say that your cpu usage is just 3-4%. I just removed gnome system monitor and replaced it with htop... My friends here are challenging me to put my drive to maximum use. That would be a challenge... And your htop will respond with just around 50%... 
Anyway, thank you guys for providing this support...

---

