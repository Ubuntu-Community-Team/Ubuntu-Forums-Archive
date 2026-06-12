---
title: "Ubuntu 9.10 Karmic Koala - Very Slow (7.5 minutes) Boot up and Very Slow Shutdown Iss"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-02-25
Ubuntu 9.10 Karmic Koala - Very Slow (7.5 minutes) Boot up and Very Slow Shutdown Issue

Hi guys. I hope someone here can help me out. I'm having a major boot and shutdown issue with Ubuntu 9.10 Karmic Koala. I am running it on an Acer Extensa 4420 Laptop with AMD 64, 3 GB RAM.

I am a novice with Linux and have been using Ubuntu instead of Windows Vista for just over 2 months now, and am a very average computer user so please forgive me if I sound ignorant or I ask any stupid follow-up questions. I have gone through most of the forum posts online that talk about Ubuntu boot or shut down issues, tried a bunch of the solutions offered there, but nothing seems to be working.

Ubuntu takes nearly 7.5 minutes to fully boot. Grub loads up fine, then I select my option to boot (I have a Windows Vista boot option as well, which I rarely use nowadays). Once I select, it stalls on the Ubuntu Logo for a while. Then the splash screen shows up, and then the login screen. When I select the user account, it stalls for a while, then allows me to enter the password. After I do, it just waits, and waits, and waits, and by the time Ubuntu is fully loaded, its been nearly 7.5 mins. Until last night, I was able to boot from scratch within 30 seconds.

Shutdown used to happen within 15 seconds before, But takes longer now.

Please help me someone! I got sick of windows, explored Ubuntu, fell in love with it. Now I really need this problem fixed. I would hate to reinstall it and lose my stuff. Is there a way to just reinstall Ubuntu without deleting any of my installed programs and files? Can it be repaired, say like a windows reinstall, where when you have an issue, you can always try popping the CD in a reinstalling and repairing in the process?

I'd appreciate any help you can offer.

Thanks.

---

### Post by seventhsamurai on 2010-02-25
And here's proof of what's happening. If you're bored and want to get even more bored and actually watch my whole boot up process, here you go: [http://www.youtube.com/watch?v=CwLeqXxqxP0](http://www.youtube.com/watch?v=CwLeqXxqxP0)

---

### Post by quinnten83 on 2010-02-25
Hey,
In order to solve the slow bootup and shutdown problem, we should have a look into your log files. Right now I'm not sure which files those are. But I am sure someone will tell you which ones you need.You can try right now with

```
dmesg >boot.txt
```

That command will create a file that you can then attach here for others to have a look at.
As for re-installation, You can backup your home-drive (including your hidden folders) to an external hard-drive, reinstall, and copy your home-drive back to your computer. You should still maintain all your data.
Even better will be (if you're going to be reinstalling anyway) to create a separate home-partition. You can then reinstall as many times as necessary and it should not affect your data. However, always make sure you have a backup. There are many guides on how to set this up, you can try googling it.

---

### Post by NightwishFan on 2010-02-25
I am guessing you are a Kikuchiyo fan?

I believe you, problems happen. When booting, hold in shift and you will see a menu. Choose "Recovery Mode". If the boot process is slow, it will have text messages about what is going on.

---

### Post by quinnten83 on 2010-02-25
Have you tried selecting one of the previous kernels to see if that boots up quicker?

---

### Post by seventhsamurai on 2010-02-25
Hi Guys. Thanks for trying to help. I tried selecting a previous kernel and it too takes equally long to boot. I'm attempting the recovery mode and log file creation now. Will post results in a bit.

I don't mind just backing up and reinstalling. Just trying to understand why this is happening. It was working fine last evening, and I did not do any updates or change anything or install any new programs even. i had left the computer on, it randomly shut off on its own, and then its been doing this since.

---

### Post by NightwishFan on 2010-02-25
The logs should crack it. Hopefully you will be back up and running soon. :popcorn:

---

### Post by seventhsamurai on 2010-02-25
Ok so did the whole log files/boot.txt thing and this is what came out of it:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-19-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 (Ubuntu 2.6.31-19.56-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=4536203d-801a-48e3-82de-5e61f0b82d4d ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afe80000 (usable)
[    0.000000]  BIOS-e820: 00000000afe80000 - 00000000afe92000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afe92000 - 00000000afe94000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afe94000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xafe80 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000afe80000 (usable)
[    0.000000]  modified: 00000000afe80000 - 00000000afe92000 (ACPI data)
[    0.000000]  modified: 00000000afe92000 - 00000000afe94000 (ACPI NVS)
[    0.000000]  modified: 00000000afe94000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000afe80000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00afe80000 page 4k
[    0.000000] kernel direct mapping tables up to afe80000 @ 10000-15000
[    0.000000] RAMDISK: 3786d000 - 37fef054
[    0.000000] ACPI: RSDP 00000000000f83c0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000afe87bbf 0005C (v01 ACRSYS ACRPRDCT 06040000 INNA 00000000)
[    0.000000] ACPI: FACP 00000000afe919af 000F4 (v03 ATI    Herring  06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 00000000afe87c1b 09D94 (v01    ATI    SB600 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 00000000afe93fc0 00040
[    0.000000] ACPI: SLIC 00000000afe91b17 00176 (v01 ACRSYS ACRPRDCT 06040000 ANNI 00000001)
[    0.000000] ACPI: SSDT 00000000afe91c8d 00248 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: ASF! 00000000afe91ed5 00063 (v32    DMA AMDTBL   06040000 PTL  00000001)
[    0.000000] ACPI: APIC 00000000afe91f38 00054 (v01 PTLTD       APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 00000000afe91f8c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 00000000afe91fc8 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000afe80000
[    0.000000] Bootmem setup node 0 0000000000000000-00000000afe80000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000002dfcf] pages 16
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00afe80000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [003786d000 - 0037fef054]          RAMDISK ==> [003786d000 - 0037fef054]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e5204]              BRK ==> [00019e5000 - 00019e5204]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000f83f0] f83f0
[    0.000000]  [ffffea0000000000-ffffea00027fffff] PMD -> [ffff880001e00000-ffff8800045fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000afe80
[    0.000000] On node 0 totalpages: 720397
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 104 pages reserved
[    0.000000]   DMA zone: 3821 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9795 pages used for memmap
[    0.000000]   DMA32 zone: 706621 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880001a02000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 710442
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=4536203d-801a-48e3-82de-5e61f0b82d4d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 4480000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 2822352k/2882048k available (5315k kernel code, 460k absent, 59236k reserved, 3017k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2194.412 MHz processor.
[    0.000014] spurious 8259A interrupt: IRQ7.
[    0.000767] Console: colour VGA+ 80x25
[    0.000770] console [tty0] enabled
[    0.010000] allocated 28835840 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 4388.82 BogoMIPS (lpj=21944120)
[    0.010042] Security Framework initialized
[    0.010066] AppArmor: AppArmor initialized
[    0.010396] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.014038] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.015793] Mount-cache hash table entries: 256
[    0.015969] Initializing cgroup subsys ns
[    0.015974] Initializing cgroup subsys cpuacct
[    0.015978] Initializing cgroup subsys memory
[    0.015988] Initializing cgroup subsys freezer
[    0.015990] Initializing cgroup subsys net_cls
[    0.016004] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.016006] CPU: L2 Cache: 512K (64 bytes/line)
[    0.016009] CPU 0/0x0 -> Node 0
[    0.016011] tseg: 00aff00000
[    0.016013] CPU: Physical Processor ID: 0
[    0.016015] CPU: Processor Core ID: 0
[    0.016018] mce: CPU supports 5 MCE banks
[    0.016029] using C1E aware idle routine
[    0.016031] Performance Counters: AMD PMU driver.
[    0.016036] ... version:                 0
[    0.016037] ... bit width:               48
[    0.016039] ... generic counters:        4
[    0.016040] ... value mask:              0000ffffffffffff
[    0.016042] ... max period:              00007fffffffffff
[    0.016044] ... fixed-purpose counters:  0
[    0.016045] ... counter mask:            000000000000000f
[    0.017631] ACPI: Core revision 20090521
[    0.030077] Setting APIC routing to flat
[    0.030396] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.040000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.040000] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.040000] ..... (found apic 0 pin 0) ...
[    0.148396] ....... works.
[    0.148397] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-64 stepping 02
[    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 4389.01 BogoMIPS (lpj=21945067)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 5 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.300454] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-64 stepping 02
[    0.300471] Brought up 2 CPUs
[    0.300473] Total of 2 processors activated (8777.83 BogoMIPS).
[    0.300470] System has AMD C1E enabled
[    0.300470] Switch to broadcast mode on CPU1
[    0.300522] CPU0 attaching sched-domain:
[    0.300525]  domain 0: span 0-1 level MC
[    0.300528]   groups: 0 1
[    0.300533] CPU1 attaching sched-domain:
[    0.300535]  domain 0: span 0-1 level MC
[    0.300537]   groups: 1 0
[    0.300611] Switch to broadcast mode on CPU0
[    0.300611] Booting paravirtualized kernel on bare hardware
[    0.300611] regulator: core version 0.5
[    0.300611] Time: 17:10:06  Date: 02/25/10
[    0.300611] NET: Registered protocol family 16
[    0.300611] node 0 link 0: io port [1000, fffff]
[    0.300611] TOM: 00000000c0000000 aka 3072M
[    0.300611] node 0 link 0: mmio [f0100000, ffffffff]
[    0.300611] node 0 link 0: mmio [f0000000, f00fffff]
[    0.300611] node 0 link 0: mmio [e0000000, dfffffff]
[    0.300611] node 0 link 0: mmio [d0000000, dfffffff]
[    0.300611] node 0 link 0: mmio [a0000, bffff]
[    0.300611] node 0 link 0: mmio [f0000000, efffffff]
[    0.300611] node 0 link 0: mmio [e0000000, efffffff]
[    0.300611] node 0 link 0: mmio [c0000000, cfffffff]
[    0.300611] bus: [00,ff] on node 0 link 0
[    0.300611] bus: 00 index 0 io port: [0, ffff]
[    0.300611] bus: 00 index 1 mmio: [e0000000, fcffffffff]
[    0.300611] bus: 00 index 2 mmio: [c0000000, dfffffff]
[    0.300611] bus: 00 index 3 mmio: [a0000, bffff]
[    0.300611] ACPI: bus type pci registered
[    0.300611] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 13
[    0.300611] PCI: MCFG area at e0000000 reserved in E820
[    0.300702] PCI: Using MMCONFIG at e0000000 - e0dfffff
[    0.300705] PCI: Using configuration type 1 for base access
[    0.301474] bio: create slab <bio-0> at 0
[    0.301474] ACPI: EC: Look up EC in DSDT
[    0.304516] ACPI: BIOS _OSI(Linux) query ignored
[    0.301474] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.350064] ACPI: Interpreter enabled
[    0.350068] ACPI: (supports S0 S3 S4 S5)
[    0.350092] ACPI: Using IOAPIC for interrupt routing
[    0.361018] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.361021] ACPI: EC: driver started in interrupt mode
[    0.361275] ACPI: No dock devices found.
[    0.362693] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.362800] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.362803] pci 0000:00:04.0: PME# disabled
[    0.362819] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.362819] pci 0000:00:05.0: PME# disabled
[    0.362819] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.362819] pci 0000:00:06.0: PME# disabled
[    0.362819] pci 0000:00:12.0: reg 10 io port: [0x8440-0x8447]
[    0.362819] pci 0000:00:12.0: reg 14 io port: [0x8434-0x8437]
[    0.362819] pci 0000:00:12.0: reg 18 io port: [0x8438-0x843f]
[    0.362819] pci 0000:00:12.0: reg 1c io port: [0x8430-0x8433]
[    0.362819] pci 0000:00:12.0: reg 20 io port: [0x8400-0x840f]
[    0.362819] pci 0000:00:12.0: reg 24 32bit mmio: [0xf0709000-0xf07093ff]
[    0.362819] pci 0000:00:12.0: set SATA to AHCI mode
[    0.362819] pci 0000:00:13.0: reg 10 32bit mmio: [0xf0704000-0xf0704fff]
[    0.362819] pci 0000:00:13.1: reg 10 32bit mmio: [0xf0705000-0xf0705fff]
[    0.362819] pci 0000:00:13.2: reg 10 32bit mmio: [0xf0706000-0xf0706fff]
[    0.362819] pci 0000:00:13.3: reg 10 32bit mmio: [0xf0707000-0xf0707fff]
[    0.362819] pci 0000:00:13.4: reg 10 32bit mmio: [0xf0708000-0xf0708fff]
[    0.362819] pci 0000:00:13.5: reg 10 32bit mmio: [0xf0709400-0xf07094ff]
[    0.362819] pci 0000:00:13.5: supports D1 D2
[    0.362819] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.362819] pci 0000:00:13.5: PME# disabled
[    0.362819] pci 0000:00:14.0: reg 10 io port: [0x8410-0x841f]
[    0.362819] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.362819] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.362819] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.362819] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.362819] pci 0000:00:14.1: reg 20 io port: [0x8420-0x842f]
[    0.362819] pci 0000:00:14.2: reg 10 64bit mmio: [0xf0700000-0xf0703fff]
[    0.362819] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.362819] pci 0000:00:14.2: PME# disabled
[    0.362819] pci 0000:01:05.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.362819] pci 0000:01:05.0: reg 18 64bit mmio: [0xf0100000-0xf010ffff]
[    0.362819] pci 0000:01:05.0: reg 20 io port: [0x9000-0x90ff]
[    0.362819] pci 0000:01:05.0: reg 24 32bit mmio: [0xf0000000-0xf00fffff]
[    0.362819] pci 0000:01:05.0: supports D1 D2
[    0.362819] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.362819] pci 0000:00:01.0: bridge 32bit mmio: [0xf0000000-0xf01fffff]
[    0.362819] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.362819] pci 0000:02:00.0: reg 10 64bit mmio: [0xf0200000-0xf0203fff]
[    0.362819] pci 0000:02:00.0: reg 18 io port: [0xa000-0xa0ff]
[    0.362819] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.362819] pci 0000:02:00.0: supports D1 D2
[    0.362819] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.362819] pci 0000:02:00.0: PME# disabled
[    0.362819] pci 0000:00:04.0: bridge io port: [0xa000-0xafff]
[    0.362819] pci 0000:00:04.0: bridge 32bit mmio: [0xf0200000-0xf02fffff]
[    0.362819] pci 0000:05:00.0: reg 10 64bit mmio: [0xf0300000-0xf0303fff]
[    0.362819] pci 0000:05:00.0: supports D1 D2
[    0.362819] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.362819] pci 0000:05:00.0: PME# disabled
[    0.362819] pci 0000:00:05.0: bridge 32bit mmio: [0xf0300000-0xf03fffff]
[    0.362819] pci 0000:00:06.0: bridge io port: [0x00-0xfff]
[    0.362819] pci 0000:00:06.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.362819] pci 0000:0b:06.0: reg 10 32bit mmio: [0xf0400000-0xf0400fff]
[    0.362819] pci 0000:0b:06.0: supports D1 D2
[    0.362819] pci 0000:0b:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.362819] pci 0000:0b:06.0: PME# disabled
[    0.362819] pci 0000:0b:06.2: reg 10 32bit mmio: [0xf0403800-0xf04038ff]
[    0.362819] pci 0000:0b:06.2: supports D1 D2
[    0.362819] pci 0000:0b:06.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.362819] pci 0000:0b:06.2: PME# disabled
[    0.362819] pci 0000:0b:06.3: reg 10 32bit mmio: [0xf0401000-0xf0401fff]
[    0.362819] pci 0000:0b:06.3: supports D1 D2
[    0.362819] pci 0000:0b:06.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.362819] pci 0000:0b:06.3: PME# disabled
[    0.362819] pci 0000:0b:06.4: reg 10 32bit mmio: [0xf0402000-0xf0402fff]
[    0.362819] pci 0000:0b:06.4: reg 14 32bit mmio: [0xf0403000-0xf04037ff]
[    0.362819] pci 0000:0b:06.4: supports D1 D2
[    0.362819] pci 0000:0b:06.4: PME# supported from D0 D1 D2 D3hot
[    0.362819] pci 0000:0b:06.4: PME# disabled
[    0.362819] pci 0000:00:14.4: transparent bridge
[    0.362819] pci 0000:00:14.4: bridge 32bit mmio: [0xf0400000-0xf04fffff]
[    0.362819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.362819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.362819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.362819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.362819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.362819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.365660] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.365783] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.365895] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.366007] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.366119] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.366231] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.366342] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.366455] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.366658] SCSI subsystem initialized
[    0.370023] libata version 3.00 loaded.
[    0.370053] usbcore: registered new interface driver usbfs
[    0.370053] usbcore: registered new interface driver hub
[    0.370053] usbcore: registered new device driver usb
[    0.370092] ACPI: WMI: Mapper loaded
[    0.370094] PCI: Using ACPI for IRQ routing
[    0.370102] pci 0000:00:06.0: BAR 13: can't allocate resource
[    0.370104] pci 0000:00:06.0: BAR 14: can't allocate resource
[    0.400007] Bluetooth: Core ver 2.15
[    0.410015] NET: Registered protocol family 31
[    0.410017] Bluetooth: HCI device and connection manager initialized
[    0.410021] Bluetooth: HCI socket layer initialized
[    0.410023] NetLabel: Initializing
[    0.410024] NetLabel:  domain hash size = 128
[    0.410026] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.410040] NetLabel:  unlabeled traffic allowed by default
[    0.410243] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.410248] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.450019] Switched to high resolution mode on CPU 0
[    0.450035] Switched to high resolution mode on CPU 1
[    0.462533] pnp: PnP ACPI init
[    0.462554] ACPI: bus type pnp registered
[    0.469623] pnp: PnP ACPI: found 12 devices
[    0.469626] ACPI: ACPI bus type pnp unregistered
[    0.469637] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.469640] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.469647] system 00:06: ioport range 0x1080-0x1080 has been reserved
[    0.469650] system 00:06: ioport range 0x220-0x22f has been reserved
[    0.469653] system 00:06: ioport range 0x40b-0x40b has been reserved
[    0.469656] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.469659] system 00:06: ioport range 0x4d6-0x4d6 has been reserved
[    0.469662] system 00:06: ioport range 0x530-0x537 has been reserved
[    0.469664] system 00:06: ioport range 0xc00-0xc01 has been reserved
[    0.469667] system 00:06: ioport range 0xc14-0xc14 has been reserved
[    0.469671] system 00:06: ioport range 0xc50-0xc52 has been reserved
[    0.469673] system 00:06: ioport range 0xc6c-0xc6c has been reserved
[    0.469676] system 00:06: ioport range 0xc6f-0xc6f has been reserved
[    0.469679] system 00:06: ioport range 0xcd0-0xcd1 has been reserved
[    0.469682] system 00:06: ioport range 0xcd2-0xcd3 has been reserved
[    0.469685] system 00:06: ioport range 0xcd4-0xcd5 has been reserved
[    0.469687] system 00:06: ioport range 0xcd6-0xcd7 has been reserved
[    0.469690] system 00:06: ioport range 0xcd8-0xcdf has been reserved
[    0.469693] system 00:06: ioport range 0x8000-0x805f has been reserved
[    0.469696] system 00:06: ioport range 0xf40-0xf47 has been reserved
[    0.469699] system 00:06: ioport range 0x87f-0x87f has been reserved
[    0.469702] system 00:06: iomem range 0xff800000-0xffefffff has been reserved
[    0.469707] system 00:07: iomem range 0xe0000-0xfffff could not be reserved
[    0.469710] system 00:07: iomem range 0xfff00000-0xffffffff has been reserved
[    0.474430] AppArmor: AppArmor Filesystem Enabled
[    0.474488] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.474491] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.474494] pci 0000:00:01.0:   MEM window: 0xf0000000-0xf01fffff
[    0.474498] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.474503] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.474506] pci 0000:00:04.0:   IO window: 0xa000-0xafff
[    0.474509] pci 0000:00:04.0:   MEM window: 0xf0200000-0xf02fffff
[    0.474512] pci 0000:00:04.0:   PREFETCH window: 0xc4000000-0xc40fffff
[    0.474516] pci 0000:00:05.0: PCI bridge, secondary bus 0000:05
[    0.474518] pci 0000:00:05.0:   IO window: disabled
[    0.474521] pci 0000:00:05.0:   MEM window: 0xf0300000-0xf03fffff
[    0.474524] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.474527] pci 0000:00:06.0: PCI bridge, secondary bus 0000:08
[    0.474529] pci 0000:00:06.0:   IO window: disabled
[    0.474532] pci 0000:00:06.0:   MEM window: disabled
[    0.474535] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.474540] pci 0000:0b:06.0: CardBus bridge, secondary bus 0000:0c
[    0.474543] pci 0000:0b:06.0:   IO window: 0x002000-0x0020ff
[    0.474551] pci 0000:0b:06.0:   IO window: 0x002400-0x0024ff
[    0.474557] pci 0000:0b:06.0:   PREFETCH window: 0xc0000000-0xc3ffffff
[    0.474562] pci 0000:0b:06.0:   MEM window: 0xc8000000-0xcbffffff
[    0.474568] pci 0000:00:14.4: PCI bridge, secondary bus 0000:0b
[    0.474571] pci 0000:00:14.4:   IO window: 0x2000-0x2fff
[    0.474577] pci 0000:00:14.4:   MEM window: 0xf0400000-0xf04fffff
[    0.474582] pci 0000:00:14.4:   PREFETCH window: 0xc0000000-0xc3ffffff
[    0.474594] pci 0000:00:04.0: setting latency timer to 64
[    0.474599] pci 0000:00:05.0: setting latency timer to 64
[    0.474604] pci 0000:00:06.0: setting latency timer to 64
[    0.474619]   alloc irq_desc for 20 on node 0
[    0.474621]   alloc kstat_irqs on node 0
[    0.474626] pci 0000:0b:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.474634] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.474637] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.474640] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.474642] pci_bus 0000:01: resource 1 mem: [0xf0000000-0xf01fffff]
[    0.474645] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.474648] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.474650] pci_bus 0000:02: resource 1 mem: [0xf0200000-0xf02fffff]
[    0.474653] pci_bus 0000:02: resource 2 pref mem [0xc4000000-0xc40fffff]
[    0.474656] pci_bus 0000:05: resource 1 mem: [0xf0300000-0xf03fffff]
[    0.474658] pci_bus 0000:08: resource 0 mem: [0x0-0xfff]
[    0.474661] pci_bus 0000:08: resource 1 mem: [0x0-0xfffff]
[    0.474664] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
[    0.474667] pci_bus 0000:0b: resource 1 mem: [0xf0400000-0xf04fffff]
[    0.474669] pci_bus 0000:0b: resource 2 pref mem [0xc0000000-0xc3ffffff]
[    0.474672] pci_bus 0000:0b: resource 3 io:  [0x00-0xffff]
[    0.474674] pci_bus 0000:0b: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.474677] pci_bus 0000:0c: resource 0 io:  [0x2000-0x20ff]
[    0.474680] pci_bus 0000:0c: resource 1 io:  [0x2400-0x24ff]
[    0.474682] pci_bus 0000:0c: resource 2 pref mem [0xc0000000-0xc3ffffff]
[    0.474685] pci_bus 0000:0c: resource 3 mem: [0xc8000000-0xcbffffff]
[    0.474729] NET: Registered protocol family 2
[    0.474901] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.476708] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.483555] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.484381] TCP: Hash tables configured (established 524288 bind 65536)
[    0.484385] TCP reno registered
[    0.484501] NET: Registered protocol family 1
[    0.484571] Trying to unpack rootfs image as initramfs...
[    0.672257] Freeing initrd memory: 7688k freed
[    0.678202] Scanning for low memory corruption every 60 seconds
[    0.678358] audit: initializing netlink socket (disabled)
[    0.678376] type=2000 audit(1267117805.672:1): initialized
[    0.687141] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.688592] VFS: Disk quotas dquot_6.5.2
[    0.688645] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.689288] fuse init (API version 7.12)
[    0.689368] msgmni has been set to 5527
[    0.689663] alg: No test for stdrng (krng)
[    0.689677] io scheduler noop registered
[    0.689680] io scheduler anticipatory registered
[    0.689682] io scheduler deadline registered
[    0.689721] io scheduler cfq registered (default)
[    0.689822] pci 0000:01:05.0: Boot video device
[    0.690047]   alloc irq_desc for 24 on node 0
[    0.690050]   alloc kstat_irqs on node 0
[    0.690058] pcieport-driver 0000:00:04.0: irq 24 for MSI/MSI-X
[    0.690064] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    0.690210]   alloc irq_desc for 25 on node 0
[    0.690212]   alloc kstat_irqs on node 0
[    0.690217] pcieport-driver 0000:00:05.0: irq 25 for MSI/MSI-X
[    0.690221] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    0.690350]   alloc irq_desc for 26 on node 0
[    0.690352]   alloc kstat_irqs on node 0
[    0.690358] pcieport-driver 0000:00:06.0: irq 26 for MSI/MSI-X
[    0.690362] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    0.690452] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.690469] Firmware did not grant requested _OSC control
[    0.690500] Firmware did not grant requested _OSC control
[    0.690513] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.692777] ACPI: AC Adapter [ADP1] (on-line)
[    0.692846] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.692850] ACPI: Power Button [PWRF]
[    0.692904] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.692907] ACPI: Power Button [PWRB]
[    0.692947] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.694487] ACPI: Lid Switch [LID0]
[    0.694534] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    0.694542] ACPI: Sleep Button [SLPB]
[    0.694747] ACPI: processor limited to max C-state 1
[    0.694782] processor LNXCPU:00: registered as cooling_device0
[    0.694817] processor LNXCPU:01: registered as cooling_device1
[    0.714557] thermal LNXTHERM:01: registered as thermal_zone0
[    0.714564] ACPI: Thermal Zone [TZS0] (67 C)
[    0.722358] thermal LNXTHERM:02: registered as thermal_zone1
[    0.722365] ACPI: Thermal Zone [TZS1] (71 C)
[    0.723684] Linux agpgart interface v0.103
[    0.723723] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.724896] brd: module loaded
[    0.725322] loop: module loaded
[    0.725422] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.725758] ahci 0000:00:12.0: version 3.0
[    0.725773]   alloc irq_desc for 22 on node 0
[    0.725775]   alloc kstat_irqs on node 0
[    0.725781] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.725812] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    0.725932] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.725936] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    0.726489] scsi0 : ahci
[    0.726642] scsi1 : ahci
[    0.726699] scsi2 : ahci
[    0.726760] scsi3 : ahci
[    0.727019] ata1: SATA max UDMA/133 abar m1024@0xf0709000 port 0xf0709100 irq 22
[    0.727023] ata2: SATA max UDMA/133 abar m1024@0xf0709000 port 0xf0709180 irq 22
[    0.727027] ata3: SATA max UDMA/133 abar m1024@0xf0709000 port 0xf0709200 irq 22
[    0.727031] ata4: SATA max UDMA/133 abar m1024@0xf0709000 port 0xf0709280 irq 22
[    0.727408]   alloc irq_desc for 16 on node 0
[    0.727410]   alloc kstat_irqs on node 0
[    0.727417] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.727468] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    0.727545] scsi4 : pata_atiixp
[    0.727604] scsi5 : pata_atiixp
[    0.728341] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    0.728344] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    0.729049] Fixed MDIO Bus: probed
[    0.729081] PPP generic driver version 2.4.2
[    0.729172] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.729241]   alloc irq_desc for 19 on node 0
[    0.729244]   alloc kstat_irqs on node 0
[    0.729248] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.729272] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.729363] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.729413] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.729432] ehci_hcd 0000:00:13.5: debug port 1
[    0.729453] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf0709400
[    0.740084] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.740159] usb usb1: configuration #1 chosen from 1 choice
[    0.740188] hub 1-0:1.0: USB hub found
[    0.740198] hub 1-0:1.0: 10 ports detected
[    0.740291] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.740359] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.740377] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.740413] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.740442] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf0704000
[    0.800089] usb usb2: configuration #1 chosen from 1 choice
[    0.800117] hub 2-0:1.0: USB hub found
[    0.800131] hub 2-0:1.0: 2 ports detected
[    0.800253]   alloc irq_desc for 17 on node 0
[    0.800255]   alloc kstat_irqs on node 0
[    0.800261] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.800276] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.800312] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.800340] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf0705000
[    0.860089] usb usb3: configuration #1 chosen from 1 choice
[    0.860121] hub 3-0:1.0: USB hub found
[    0.860134] hub 3-0:1.0: 2 ports detected
[    0.860228]   alloc irq_desc for 18 on node 0
[    0.860230]   alloc kstat_irqs on node 0
[    0.860233] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.860246] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.860283] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.860309] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf0706000
[    0.865625] ACPI: Battery Slot [BAT0] (battery present)
[    0.900768] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T40N, JP01, max UDMA/33
[    0.920100] usb usb4: configuration #1 chosen from 1 choice
[    0.920124] hub 4-0:1.0: USB hub found
[    0.920137] hub 4-0:1.0: 2 ports detected
[    0.920389] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.920402] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.920439] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.920462] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf0707000
[    0.940721] ata5.00: configured for UDMA/33
[    0.980091] usb usb5: configuration #1 chosen from 1 choice
[    0.980119] hub 5-0:1.0: USB hub found
[    0.980133] hub 5-0:1.0: 2 ports detected
[    0.980225] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.980236] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    0.980273] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    0.980292] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf0708000
[    1.040128] usb usb6: configuration #1 chosen from 1 choice
[    1.040154] hub 6-0:1.0: USB hub found
[    1.040167] hub 6-0:1.0: 2 ports detected
[    1.040231] uhci_hcd: USB Universal Host Controller Interface driver
[    1.040354] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.049919] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.056995] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.057002] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.057005] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.057008] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.057011] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.057101] mice: PS/2 mouse device common for all mice
[    1.057232] rtc_cmos 00:04: RTC can wake from S4
[    1.057278] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.057309] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.057434] device-mapper: uevent: version 1.0.3
[    1.057533] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.057647] device-mapper: multipath: version 1.1.0 loaded
[    1.057650] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.057882] cpuidle: using governor ladder
[    1.057884] cpuidle: using governor menu
[    1.058311] TCP cubic registered
[    1.058441] NET: Registered protocol family 10
[    1.058893] lo: Disabled Privacy Extensions
[    1.059174] NET: Registered protocol family 17
[    1.059195] Bluetooth: L2CAP ver 2.13
[    1.059197] Bluetooth: L2CAP socket layer initialized
[    1.059200] Bluetooth: SCO (Voice Link) ver 0.6
[    1.059202] Bluetooth: SCO socket layer initialized
[    1.059250] Bluetooth: RFCOMM TTY layer initialized
[    1.059257] Bluetooth: RFCOMM socket layer initialized
[    1.059259] Bluetooth: RFCOMM ver 1.11
[    1.059283] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-64 processors (2 cpu cores) (version 2.20.00)
[    1.059332] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x11
[    1.059334] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x12
[    1.059336] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x13
[    1.059338] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0x14
[    1.059340] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x1e
[    1.059488] PM: Resume from disk failed.
[    1.059503] registered taskstats version 1
[    1.059676]   Magic number: 14:273:189
[    1.059752] acpi device:1b: hash matches
[    1.059802] rtc_cmos 00:04: setting system clock to 2010-02-25 17:10:07 UTC (1267117807)
[    1.059806] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.059807] EDD information not available.
[    1.060048] usb 1-7: new high speed USB device using ehci_hcd and address 2
[    1.070079] ata2: SATA link down (SStatus 0 SControl 300)
[    1.070110] ata3: SATA link down (SStatus 0 SControl 300)
[    1.070139] ata4: SATA link down (SStatus 0 SControl 300)
[    1.079444] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.250033] ata1: softreset failed (device not ready)
[    1.250037] ata1: applying SB600 PMP SRST workaround and retrying
[    1.280484] usb 1-7: configuration #1 chosen from 1 choice
[    1.430043] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.430990] ata1.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC31P, max UDMA/133
[    1.430993] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.431013] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.432149] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.432153] ata1.00: configured for UDMA/133
[    1.450152] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[    1.450294] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.450319] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.450371] sd 0:0:0:0: [sda] Write Protect is off
[    1.450374] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.450395] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.450530]  sda:
[    1.453924] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40N  JP01 PQ: 0 ANSI: 5
[    1.465124] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.465127] Uniform CD-ROM driver Revision: 3.20
[    1.465211] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.465257] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.467094]  sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.521529] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.620115] Freeing unused kernel memory: 660k freed
[    1.620486] Write protecting the kernel read-only data: 7584k
[    1.855731] [drm] Initialized drm 1.1.0 20060810
[    1.880062] [drm] radeon default to kernel modesetting DISABLED.
[    1.880523] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.880688] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[    1.886369] sky2 driver version 1.23
[    1.886497] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.886515] sky2 0000:02:00.0: setting latency timer to 64
[    1.886563] sky2 0000:02:00.0: Yukon-2 Extreme chip revision 2
[    1.886641]   alloc irq_desc for 27 on node 0
[    1.886644]   alloc kstat_irqs on node 0
[    1.886657] sky2 0000:02:00.0: irq 27 for MSI/MSI-X
[    1.887547] sky2 eth0: addr 00:1d:72:c8:7d:53
[    1.899959] ohci1394 0000:0b:06.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.917120] acpi device:21: registered as cooling_device2
[    1.917393] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e/device:1f/input/input6
[    1.917433] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    1.961083] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f0402000-f04027ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    3.131815] PM: Starting manual resume from disk
[    3.131821] PM: Resume from partition 8:7
[    3.131822] PM: Checking hibernation image.
[    3.132042] PM: Resume from disk failed.
[    3.163158] EXT4-fs (sda6): barriers enabled
[    3.184682] kjournald2 starting: pid 434, dev sda6:8, commit interval 5 seconds
[    3.184694] EXT4-fs (sda6): delayed allocation enabled
[    3.184697] EXT4-fs: file extents enabled
[    3.184832] EXT4-fs: mballoc enabled
[    3.184850] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    3.292778] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001d72ffffc87d53]
[    3.906096] type=1505 audit(1267117810.342:2): operation="profile_load" pid=457 name=/usr/share/gdm/guest-session/Xsession
[    3.908778] type=1505 audit(1267117810.342:3): operation="profile_load" pid=458 name=/sbin/dhclient3
[    3.909056] type=1505 audit(1267117810.342:4): operation="profile_load" pid=458 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.909211] type=1505 audit(1267117810.342:5): operation="profile_load" pid=458 name=/usr/lib/connman/scripts/dhclient-script
[    3.966449] type=1505 audit(1267117810.402:6): operation="profile_load" pid=459 name=/usr/bin/evince
[    3.971194] type=1505 audit(1267117810.402:7): operation="profile_load" pid=459 name=/usr/bin/evince-previewer
[    3.974041] type=1505 audit(1267117810.412:8): operation="profile_load" pid=459 name=/usr/bin/evince-thumbnailer
[    4.010034] type=1505 audit(1267117810.442:9): operation="profile_load" pid=461 name=/usr/lib/cups/backend/cups-pdf
[   18.226872] udev: starting version 147
[   18.251144] Adding 1108444k swap on /dev/sda7.  Priority:-1 extents:1 across:1108444k 
[   18.272123] lp: driver loaded but no devices found
[   18.279722] irda_init()
[   18.279745] NET: Registered protocol family 23
[   18.297771] nsc-ircc 00:0a: activated
[   18.297778] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   18.297838] nsc-ircc, chip->init
[   18.297851] nsc-ircc, Found chip at base=0x02e
[   18.297886] nsc-ircc, driver loaded (Dag Brattli)
[   18.298551] IrDA: Registered device irda0
[   18.298620] nsc-ircc, Found dongle: Supports SIR Mode only
[   18.298681] nsc-ircc, chip->init
[   18.298694] nsc-ircc, Found chip at base=0x02e
[   18.298729] nsc-ircc, driver loaded (Dag Brattli)
[   18.298734] nsc_ircc_open(), can't get iobase of 0x2f8
[   18.327376] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   18.333819] EDAC MC: Ver: 2.1.0 Jan 28 2010
[   18.336296] EDAC amd64_edac:  Ver: 3.2.0 Jan 28 2010
[   18.337745] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   18.368016] lib80211: common routines for IEEE802.11 drivers
[   18.368020] lib80211_crypt: registered algorithm 'NULL'
[   18.372795] wl: module license 'MIXED/Proprietary' taints kernel.
[   18.372799] Disabling lock debugging due to kernel taint
[   18.375045] yenta_cardbus 0000:0b:06.0: CardBus bridge found [1025:0123]
[   18.375079] yenta_cardbus 0000:0b:06.0: O2: res at 0x94/0xD4: 00/ea
[   18.375081] yenta_cardbus 0000:0b:06.0: O2: enabling read prefetch/write burst
[   18.378227] sdhci: Secure Digital Host Controller Interface driver
[   18.378230] sdhci: Copyright(c) Pierre Ossman
[   18.404749] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   18.404754] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   18.404757] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   18.404759]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   18.404760]     Might be a BIOS bug, if BIOS says ECC is enabled
[   18.404761]     Use of the override can cause unknown side effects.
[   18.404810] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   18.430707] wl 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.430716] wl 0000:05:00.0: setting latency timer to 64
[   18.518231] EXT4-fs (sda6): internal journal on sda6:8
[   18.536712] yenta_cardbus 0000:0b:06.0: ISA IRQ mask 0x0cb0, PCI irq 20
[   18.536718] yenta_cardbus 0000:0b:06.0: Socket status: 30000006
[   18.536726] yenta_cardbus 0000:0b:06.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   18.536730] yenta_cardbus 0000:0b:06.0: pcmcia: parent PCI bridge Memory window: 0xf0400000 - 0xf04fffff
[   18.536733] yenta_cardbus 0000:0b:06.0: pcmcia: parent PCI bridge Memory window: 0xc0000000 - 0xc3ffffff
[   18.539636] sdhci-pci 0000:0b:06.2: SDHCI controller found [1217:7120] (rev 2)
[   18.539658] sdhci-pci 0000:0b:06.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.539715] mmc0: Unknown controller version (2). You may experience problems.
[   18.539791] Registered led device: mmc0::
[   18.539844] mmc0: SDHCI controller on PCI [0000:0b:06.2] using DMA
[   18.540171] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.545386] Linux video capture interface: v2.00
[   18.548558] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (064e:a103)
[   18.549701] lib80211_crypt: registered algorithm 'TKIP'
[   18.554286] acer-wmi: Acer Laptop ACPI-WMI Extras
[   18.554408] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   18.558751] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.570656] acer-wmi: Brightness must be controlled by generic video driver
[   18.571328] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:13.5/usb1/1-7/1-7:1.0/input/input7
[   18.571386] usbcore: registered new interface driver uvcvideo
[   18.571393] USB Video Class driver (v0.1.0)
[   18.585244] udev: renamed network interface eth1 to eth2
[   18.634624] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   18.634641] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.788107] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   18.788216] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input8
[   19.237516] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa04000
[   19.288664] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[   23.094590] ata1.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x0
[   23.094595] ata1.00: irq_stat 0x40000008
[   23.094604] ata1.00: cmd 60/08:18:0e:09:c1/00:00:1b:00:00/40 tag 3 ncq 4096 in
[   23.094605]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   23.094609] ata1.00: status: { DRDY ERR }
[   23.094611] ata1.00: error: { UNC }
[   23.095816] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   23.097259] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   23.097263] ata1.00: configured for UDMA/133
[   23.097280] ata1: EH complete
[   23.114452] sky2 eth0: enabling interface
[   23.115076] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.257600] __ratelimit: 6 callbacks suppressed
[   23.257604] type=1505 audit(1267098029.692:12): operation="profile_replace" pid=979 name=/usr/share/gdm/guest-session/Xsession
[   23.259656] type=1505 audit(1267098029.692:13): operation="profile_replace" pid=980 name=/sbin/dhclient3
[   23.259932] type=1505 audit(1267098029.692:14): operation="profile_replace" pid=980 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   23.260096] type=1505 audit(1267098029.692:15): operation="profile_replace" pid=980 name=/usr/lib/connman/scripts/dhclient-script
[   23.265234] type=1505 audit(1267098029.702:16): operation="profile_replace" pid=981 name=/usr/bin/evince
[   23.269983] type=1505 audit(1267098029.702:17): operation="profile_replace" pid=981 name=/usr/bin/evince-previewer
[   23.272849] type=1505 audit(1267098029.712:18): operation="profile_replace" pid=981 name=/usr/bin/evince-thumbnailer
[   23.278924] type=1505 audit(1267098029.712:19): operation="profile_replace" pid=983 name=/usr/lib/cups/backend/cups-pdf
[   23.279270] type=1505 audit(1267098029.712:20): operation="profile_replace" pid=983 name=/usr/sbin/cupsd
[   23.281644] type=1505 audit(1267098029.712:21): operation="profile_replace" pid=984 name=/usr/sbin/tcpdump
[   27.383458] ata1.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x0
[   27.383463] ata1.00: irq_stat 0x40000008
[   27.383471] ata1.00: cmd 60/08:10:0e:09:c1/00:00:1b:00:00/40 tag 2 ncq 4096 in
[   27.383472]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   27.383476] ata1.00: status: { DRDY ERR }
[   27.383478] ata1.00: error: { UNC }
[   27.384678] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   27.386119] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   27.386122] ata1.00: configured for UDMA/133
[   27.386140] ata1: EH complete
[   31.650096] ata1.00: exception Emask 0x0 SAct 0x2f SErr 0x0 action 0x0
[   31.650101] ata1.00: irq_stat 0x40000008
[   31.650110] ata1.00: cmd 60/08:18:0e:09:c1/00:00:1b:00:00/40 tag 3 ncq 4096 in
[   31.650111]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   31.650114] ata1.00: status: { DRDY ERR }
[   31.650117] ata1.00: error: { UNC }
[   31.651313] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   31.653354] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   31.653357] ata1.00: configured for UDMA/133
[   31.653375] ata1: EH complete
[   34.140024] eth2: no IPv6 routers present
[   35.927834] ata1.00: exception Emask 0x0 SAct 0x1e SErr 0x0 action 0x0
[   35.927838] ata1.00: irq_stat 0x40000008
[   35.927846] ata1.00: cmd 60/08:08:0e:09:c1/00:00:1b:00:00/40 tag 1 ncq 4096 in
[   35.927847]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   35.927850] ata1.00: status: { DRDY ERR }
[   35.927852] ata1.00: error: { UNC }
[   35.929062] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   35.930508] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   35.930511] ata1.00: configured for UDMA/133
[   35.930525] ata1: EH complete
[   40.205585] ata1.00: exception Emask 0x0 SAct 0x1b SErr 0x0 action 0x0
[   40.205590] ata1.00: irq_stat 0x40000008
[   40.205598] ata1.00: cmd 60/08:18:0e:09:c1/00:00:1b:00:00/40 tag 3 ncq 4096 in
[   40.205599]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   40.205603] ata1.00: status: { DRDY ERR }
[   40.205605] ata1.00: error: { UNC }
[   40.206805] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   40.208251] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   40.208254] ata1.00: configured for UDMA/133
[   40.208271] ata1: EH complete
[   44.483342] ata1.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x0
[   44.483346] ata1.00: irq_stat 0x40000008
[   44.483355] ata1.00: cmd 60/08:08:0e:09:c1/00:00:1b:00:00/40 tag 1 ncq 4096 in
[   44.483356]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   44.483359] ata1.00: status: { DRDY ERR }
[   44.483361] ata1.00: error: { UNC }
[   44.484585] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   44.486020] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   44.486023] ata1.00: configured for UDMA/133
[   44.486045] sd 0:0:0:0: [sda] Unhandled sense code
[   44.486047] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   44.486051] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   44.486056] Descriptor sense data with sense descriptors (in hex):
[   44.486057]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   44.486065]         1b c1 09 0e 
[   44.486068] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   44.486073] end_request: I/O error, dev sda, sector 465635598
[   44.486092] ata1: EH complete
[   48.796186] ata1.00: exception Emask 0x0 SAct 0xb SErr 0x0 action 0x0
[   48.796192] ata1.00: irq_stat 0x40000008
[   48.796200] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[   48.796201]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   48.796204] ata1.00: status: { DRDY ERR }
[   48.796206] ata1.00: error: { UNC }
[   48.797414] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   48.798848] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   48.798851] ata1.00: configured for UDMA/133
[   48.798866] ata1: EH complete
[   53.061047] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[   53.061049] ata1.00: irq_stat 0x40000008
[   53.061056] ata1.00: cmd 60/08:10:0e:09:c1/00:00:1b:00:00/40 tag 2 ncq 4096 in
[   53.061057]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   53.061060] ata1.00: status: { DRDY ERR }
[   53.061062] ata1.00: error: { UNC }
[   53.062261] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   53.063747] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   53.063749] ata1.00: configured for UDMA/133
[   53.063758] ata1: EH complete
[   57.316570] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[   57.316573] ata1.00: irq_stat 0x40000008
[   57.316579] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[   57.316580]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   57.316583] ata1.00: status: { DRDY ERR }
[   57.316585] ata1.00: error: { UNC }
[   57.317787] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   57.319221] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   57.319223] ata1.00: configured for UDMA/133
[   57.319231] ata1: EH complete
[   61.605473] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[   61.605476] ata1.00: irq_stat 0x40000008
[   61.605483] ata1.00: cmd 60/08:10:0e:09:c1/00:00:1b:00:00/40 tag 2 ncq 4096 in
[   61.605484]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   61.605487] ata1.00: status: { DRDY ERR }
[   61.605489] ata1.00: error: { UNC }
[   61.606674] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   61.608119] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   61.608122] ata1.00: configured for UDMA/133
[   61.608128] ata1: EH complete
[   65.861005] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[   65.861007] ata1.00: irq_stat 0x40000008
[   65.861013] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[   65.861014]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   65.861017] ata1.00: status: { DRDY ERR }
[   65.861019] ata1.00: error: { UNC }
[   65.862201] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   65.863654] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   65.863657] ata1.00: configured for UDMA/133
[   65.863664] ata1: EH complete
[   70.149842] ata1.00: exception Emask 0x0 SAct 0x4 SErr 0x0 action 0x0
[   70.149847] ata1.00: irq_stat 0x40000008
[   70.149854] ata1.00: cmd 60/08:10:0e:09:c1/00:00:1b:00:00/40 tag 2 ncq 4096 in
[   70.149855]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   70.149858] ata1.00: status: { DRDY ERR }
[   70.149860] ata1.00: error: { UNC }
[   70.151070] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   70.152534] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   70.152537] ata1.00: configured for UDMA/133
[   70.152547] sd 0:0:0:0: [sda] Unhandled sense code
[   70.152549] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   70.152553] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   70.152557] Descriptor sense data with sense descriptors (in hex):
[   70.152559]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   70.152567]         1b c1 09 0e 
[   70.152571] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   70.152576] end_request: I/O error, dev sda, sector 465635598
[   70.152587] ata1: EH complete
[   70.909092] usplash:397 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
[   72.580975] [drm] Setting GART location based on new memory map
[   72.582142] [drm] Loading RS690/RS740 Microcode
[   72.582163] [drm] Num pipes: 1
[   72.582170] [drm] writeback test succeeded in 1 usecs
[   78.538708] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[   78.538713] ata1.00: irq_stat 0x40000008
[   78.538722] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[   78.538723]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   78.538726] ata1.00: status: { DRDY ERR }
[   78.538728] ata1.00: error: { UNC }
[   78.554489] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   78.555948] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   78.555951] ata1.00: configured for UDMA/133
[   78.555966] ata1: EH complete
[   82.827569] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[   82.827574] ata1.00: irq_stat 0x40000008
[   82.827582] ata1.00: cmd 60/08:08:0e:09:c1/00:00:1b:00:00/40 tag 1 ncq 4096 in
[   82.827584]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   82.827587] ata1.00: status: { DRDY ERR }
[   82.827589] ata1.00: error: { UNC }
[   82.828795] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   82.830239] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   82.830242] ata1.00: configured for UDMA/133
[   82.830250] ata1: EH complete
[   87.083139] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   87.083143] ata1.00: irq_stat 0x40000008
[   87.083150] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[   87.083152]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   87.083155] ata1.00: status: { DRDY ERR }
[   87.083157] ata1.00: error: { UNC }
[   87.084356] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   87.085777] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   87.085780] ata1.00: configured for UDMA/133
[   87.085787] ata1: EH complete
[   91.327572] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   91.327575] ata1.00: irq_stat 0x40000008
[   91.327581] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[   91.327583]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   91.327585] ata1.00: status: { DRDY ERR }
[   91.327588] ata1.00: error: { UNC }
[   91.328783] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   91.330213] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   91.330215] ata1.00: configured for UDMA/133
[   91.330221] ata1: EH complete
[   95.571973] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   95.571976] ata1.00: irq_stat 0x40000008
[   95.571982] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[   95.571984]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   95.571986] ata1.00: status: { DRDY ERR }
[   95.571988] ata1.00: error: { UNC }
[   95.573258] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   95.574707] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   95.574710] ata1.00: configured for UDMA/133
[   95.574716] ata1: EH complete
[   99.827528] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   99.827530] ata1.00: irq_stat 0x40000008
[   99.827536] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[   99.827538]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[   99.827540] ata1.00: status: { DRDY ERR }
[   99.827542] ata1.00: error: { UNC }
[   99.828741] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   99.830175] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   99.830178] ata1.00: configured for UDMA/133
[   99.830186] sd 0:0:0:0: [sda] Unhandled sense code
[   99.830188] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   99.830192] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   99.830197] Descriptor sense data with sense descriptors (in hex):
[   99.830199]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   99.830207]         1b c1 09 0e 
[   99.830211] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   99.830216] end_request: I/O error, dev sda, sector 465635598
[   99.830229] ata1: EH complete
[  104.131709] ata1.00: exception Emask 0x0 SAct 0x10 SErr 0x0 action 0x0
[  104.131714] ata1.00: irq_stat 0x40000008
[  104.131722] ata1.00: cmd 60/08:20:0e:09:c1/00:00:1b:00:00/40 tag 4 ncq 4096 in
[  104.131723]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  104.131726] ata1.00: status: { DRDY ERR }
[  104.131729] ata1.00: error: { UNC }
[  104.133280] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  104.134736] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  104.134739] ata1.00: configured for UDMA/133
[  104.134747] ata1: EH complete
[  108.394225] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  108.394228] ata1.00: irq_stat 0x40000008
[  108.394234] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  108.394235]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  108.394238] ata1.00: status: { DRDY ERR }
[  108.394240] ata1.00: error: { UNC }
[  108.395438] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  108.396883] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  108.396886] ata1.00: configured for UDMA/133
[  108.396892] ata1: EH complete
[  112.649842] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  112.649845] ata1.00: irq_stat 0x40000008
[  112.649851] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  112.649852]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  112.649855] ata1.00: status: { DRDY ERR }
[  112.649857] ata1.00: error: { UNC }
[  112.651034] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  112.652483] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  112.652485] ata1.00: configured for UDMA/133
[  112.652492] ata1: EH complete
[  116.905436] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  116.905441] ata1.00: irq_stat 0x40000008
[  116.905448] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  116.905449]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  116.905452] ata1.00: status: { DRDY ERR }
[  116.905454] ata1.00: error: { UNC }
[  116.906652] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  116.908085] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  116.908088] ata1.00: configured for UDMA/133
[  116.908096] ata1: EH complete
[  121.149866] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  121.149870] ata1.00: irq_stat 0x40000008
[  121.149878] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  121.149879]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  121.149882] ata1.00: status: { DRDY ERR }
[  121.149884] ata1.00: error: { UNC }
[  121.151092] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  121.152559] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  121.152566] ata1.00: configured for UDMA/133
[  121.152581] ata1: EH complete
[  125.405478] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  125.405481] ata1.00: irq_stat 0x40000008
[  125.405488] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  125.405489]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  125.405492] ata1.00: status: { DRDY ERR }
[  125.405493] ata1.00: error: { UNC }
[  125.406687] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  125.408117] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  125.408120] ata1.00: configured for UDMA/133
[  125.408131] sd 0:0:0:0: [sda] Unhandled sense code
[  125.408133] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  125.408137] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  125.408141] Descriptor sense data with sense descriptors (in hex):
[  125.408143]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  125.408151]         1b c1 09 0e 
[  125.408155] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  125.408160] end_request: I/O error, dev sda, sector 465635598
[  125.408177] ata1: EH complete
[  129.705476] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  129.705481] ata1.00: irq_stat 0x40000008
[  129.705489] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  129.705491]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  129.705494] ata1.00: status: { DRDY ERR }
[  129.705496] ata1.00: error: { UNC }
[  129.706700] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  129.708145] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  129.708148] ata1.00: configured for UDMA/133
[  129.708156] ata1: EH complete
[  133.949949] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  133.949954] ata1.00: irq_stat 0x40000008
[  133.949961] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  133.949963]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  133.949966] ata1.00: status: { DRDY ERR }
[  133.949968] ata1.00: error: { UNC }
[  133.951173] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  133.953148] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  133.953151] ata1.00: configured for UDMA/133
[  133.953159] ata1: EH complete
[  138.194449] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  138.194452] ata1.00: irq_stat 0x40000008
[  138.194458] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  138.194459]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  138.194462] ata1.00: status: { DRDY ERR }
[  138.194464] ata1.00: error: { UNC }
[  138.195644] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  138.197091] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  138.197094] ata1.00: configured for UDMA/133
[  138.197100] ata1: EH complete
[  142.450019] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  142.450022] ata1.00: irq_stat 0x40000008
[  142.450028] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  142.450030]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  142.450032] ata1.00: status: { DRDY ERR }
[  142.450035] ata1.00: error: { UNC }
[  142.451215] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  142.453138] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  142.453140] ata1.00: configured for UDMA/133
[  142.453146] ata1: EH complete
[  146.683381] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  146.683384] ata1.00: irq_stat 0x40000008
[  146.683390] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  146.683391]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  146.683394] ata1.00: status: { DRDY ERR }
[  146.683396] ata1.00: error: { UNC }
[  146.684577] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  146.686024] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  146.686026] ata1.00: configured for UDMA/133
[  146.686032] ata1: EH complete
[  150.938911] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  150.938914] ata1.00: irq_stat 0x40000008
[  150.938920] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  150.938921]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  150.938924] ata1.00: status: { DRDY ERR }
[  150.938926] ata1.00: error: { UNC }
[  150.940127] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  150.941560] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  150.941563] ata1.00: configured for UDMA/133
[  150.941571] sd 0:0:0:0: [sda] Unhandled sense code
[  150.941573] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  150.941577] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  150.941582] Descriptor sense data with sense descriptors (in hex):
[  150.941584]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  150.941592]         1b c1 09 0e 
[  150.941596] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  150.941601] end_request: I/O error, dev sda, sector 465635598
[  150.941615] ata1: EH complete
[  155.305129] ata1.00: exception Emask 0x0 SAct 0x20 SErr 0x0 action 0x0
[  155.305133] ata1.00: irq_stat 0x40000008
[  155.305141] ata1.00: cmd 60/08:28:0e:09:c1/00:00:1b:00:00/40 tag 5 ncq 4096 in
[  155.305142]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  155.305145] ata1.00: status: { DRDY ERR }
[  155.305147] ata1.00: error: { UNC }
[  155.306351] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  155.307803] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  155.307806] ata1.00: configured for UDMA/133
[  155.307813] ata1: EH complete
[  159.561214] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  159.561217] ata1.00: irq_stat 0x40000008
[  159.561223] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  159.561224]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  159.561227] ata1.00: status: { DRDY ERR }
[  159.561229] ata1.00: error: { UNC }
[  159.562414] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  159.564327] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  159.564330] ata1.00: configured for UDMA/133
[  159.564336] ata1: EH complete
[  163.816798] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  163.816802] ata1.00: irq_stat 0x40000008
[  163.816811] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  163.816812]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  163.816815] ata1.00: status: { DRDY ERR }
[  163.816817] ata1.00: error: { UNC }
[  163.818019] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  163.819466] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  163.819470] ata1.00: configured for UDMA/133
[  163.819482] ata1: EH complete
[  168.061211] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  168.061215] ata1.00: irq_stat 0x40000008
[  168.061222] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  168.061223]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  168.061226] ata1.00: status: { DRDY ERR }
[  168.061228] ata1.00: error: { UNC }
[  168.062425] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  168.064319] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  168.064321] ata1.00: configured for UDMA/133
[  168.064329] ata1: EH complete
[  172.316815] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  172.316819] ata1.00: irq_stat 0x40000008
[  172.316826] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  172.316827]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  172.316830] ata1.00: status: { DRDY ERR }
[  172.316832] ata1.00: error: { UNC }
[  172.318025] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  172.319474] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  172.319477] ata1.00: configured for UDMA/133
[  172.319484] ata1: EH complete
[  176.539049] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  176.539052] ata1.00: irq_stat 0x40000008
[  176.539058] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  176.539060]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  176.539062] ata1.00: status: { DRDY ERR }
[  176.539064] ata1.00: error: { UNC }
[  176.540245] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  176.541691] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  176.541694] ata1.00: configured for UDMA/133
[  176.541702] sd 0:0:0:0: [sda] Unhandled sense code
[  176.541704] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  176.541708] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  176.541713] Descriptor sense data with sense descriptors (in hex):
[  176.541715]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  176.541723]         1b c1 09 0e 
[  176.541726] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  176.541732] end_request: I/O error, dev sda, sector 465635598
[  176.541746] ata1: EH complete
[  183.739172] ata1.00: exception Emask 0x0 SAct 0x1f SErr 0x0 action 0x0
[  183.739177] ata1.00: irq_stat 0x40000008
[  183.739186] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  183.739187]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  183.739190] ata1.00: status: { DRDY ERR }
[  183.739192] ata1.00: error: { UNC }
[  183.740386] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  183.741828] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  183.741831] ata1.00: configured for UDMA/133
[  183.741850] ata1: EH complete
[  188.017979] ata1.00: exception Emask 0x0 SAct 0x10 SErr 0x0 action 0x0
[  188.017983] ata1.00: irq_stat 0x40000008
[  188.017991] ata1.00: cmd 60/08:20:0e:09:c1/00:00:1b:00:00/40 tag 4 ncq 4096 in
[  188.017992]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  188.017995] ata1.00: status: { DRDY ERR }
[  188.017997] ata1.00: error: { UNC }
[  188.019201] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  188.020649] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  188.020652] ata1.00: configured for UDMA/133
[  188.020660] ata1: EH complete
[  192.272447] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  192.272452] ata1.00: irq_stat 0x40000008
[  192.272460] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  192.272461]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  192.272464] ata1.00: status: { DRDY ERR }
[  192.272466] ata1.00: error: { UNC }
[  192.273674] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  192.275140] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  192.275143] ata1.00: configured for UDMA/133
[  192.275157] ata1: EH complete
[  196.516893] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  196.516897] ata1.00: irq_stat 0x40000008
[  196.516905] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  196.516906]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  196.516909] ata1.00: status: { DRDY ERR }
[  196.516911] ata1.00: error: { UNC }
[  196.518108] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  196.519552] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  196.519555] ata1.00: configured for UDMA/133
[  196.519562] ata1: EH complete
[  200.761345] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  200.761349] ata1.00: irq_stat 0x40000008
[  200.761356] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  200.761357]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  200.761360] ata1.00: status: { DRDY ERR }
[  200.761362] ata1.00: error: { UNC }
[  200.763054] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  200.764506] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  200.764508] ata1.00: configured for UDMA/133
[  200.764516] ata1: EH complete
[  205.016867] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  205.016871] ata1.00: irq_stat 0x40000008
[  205.016878] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  205.016880]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  205.016883] ata1.00: status: { DRDY ERR }
[  205.016885] ata1.00: error: { UNC }
[  205.018091] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  205.019549] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  205.019552] ata1.00: configured for UDMA/133
[  205.019562] sd 0:0:0:0: [sda] Unhandled sense code
[  205.019564] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  205.019567] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  205.019572] Descriptor sense data with sense descriptors (in hex):
[  205.019574]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  205.019582]         1b c1 09 0e 
[  205.019586] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  205.019591] end_request: I/O error, dev sda, sector 465635598
[  205.019596] Buffer I/O error on device sda6, logical block 3553320
[  205.019613] ata1: EH complete
[  276.983553] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  276.983558] ata1.00: irq_stat 0x40000008
[  276.983566] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  276.983568]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  276.983571] ata1.00: status: { DRDY ERR }
[  276.983573] ata1.00: error: { UNC }
[  276.984779] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  276.986222] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  276.986225] ata1.00: configured for UDMA/133
[  276.986236] ata1: EH complete
[  281.239104] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  281.239108] ata1.00: irq_stat 0x40000008
[  281.239115] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  281.239116]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  281.239119] ata1.00: status: { DRDY ERR }
[  281.239122] ata1.00: error: { UNC }
[  281.240330] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  281.241772] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  281.241775] ata1.00: configured for UDMA/133
[  281.241788] ata1: EH complete
[  285.494650] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  285.494655] ata1.00: irq_stat 0x40000008
[  285.494663] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  285.494664]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  285.494667] ata1.00: status: { DRDY ERR }
[  285.494669] ata1.00: error: { UNC }
[  285.495873] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  285.497315] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  285.497318] ata1.00: configured for UDMA/133
[  285.497327] ata1: EH complete
[  289.750210] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  289.750214] ata1.00: irq_stat 0x40000008
[  289.750221] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  289.750222]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  289.750225] ata1.00: status: { DRDY ERR }
[  289.750227] ata1.00: error: { UNC }
[  289.751439] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  289.753345] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  289.753348] ata1.00: configured for UDMA/133
[  289.753357] ata1: EH complete
[  293.994641] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  293.994644] ata1.00: irq_stat 0x40000008
[  293.994651] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  293.994652]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  293.994655] ata1.00: status: { DRDY ERR }
[  293.994657] ata1.00: error: { UNC }
[  293.995857] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  293.997317] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  293.997320] ata1.00: configured for UDMA/133
[  293.997327] ata1: EH complete
[  298.250245] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  298.250249] ata1.00: irq_stat 0x40000008
[  298.250256] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  298.250257]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  298.250260] ata1.00: status: { DRDY ERR }
[  298.250262] ata1.00: error: { UNC }
[  298.251461] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  298.253346] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  298.253349] ata1.00: configured for UDMA/133
[  298.253360] sd 0:0:0:0: [sda] Unhandled sense code
[  298.253362] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  298.253366] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  298.253370] Descriptor sense data with sense descriptors (in hex):
[  298.253372]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  298.253380]         1b c1 09 0e 
[  298.253384] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  298.253390] end_request: I/O error, dev sda, sector 465635598
[  298.253407] ata1: EH complete
[  302.574259] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  302.574264] ata1.00: irq_stat 0x40000008
[  302.574272] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  302.574274]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  302.574277] ata1.00: status: { DRDY ERR }
[  302.574279] ata1.00: error: { UNC }
[  302.575484] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  302.576943] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  302.576947] ata1.00: configured for UDMA/133
[  302.576956] ata1: EH complete
[  306.839082] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  306.839086] ata1.00: irq_stat 0x40000008
[  306.839094] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  306.839095]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  306.839098] ata1.00: status: { DRDY ERR }
[  306.839100] ata1.00: error: { UNC }
[  306.840294] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  306.841740] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  306.841743] ata1.00: configured for UDMA/133
[  306.841751] ata1: EH complete
[  311.083528] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  311.083533] ata1.00: irq_stat 0x40000008
[  311.083540] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  311.083542]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  311.083545] ata1.00: status: { DRDY ERR }
[  311.083547] ata1.00: error: { UNC }
[  311.084749] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  311.086191] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  311.086194] ata1.00: configured for UDMA/133
[  311.086207] ata1: EH complete
[  315.339136] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  315.339140] ata1.00: irq_stat 0x40000008
[  315.339147] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  315.339148]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  315.339151] ata1.00: status: { DRDY ERR }
[  315.339153] ata1.00: error: { UNC }
[  315.340356] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  315.341802] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  315.341805] ata1.00: configured for UDMA/133
[  315.341812] ata1: EH complete
[  319.594605] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  319.594608] ata1.00: irq_stat 0x40000008
[  319.594615] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  319.594617]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  319.594619] ata1.00: status: { DRDY ERR }
[  319.594622] ata1.00: error: { UNC }
[  319.595820] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  319.597254] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  319.597256] ata1.00: configured for UDMA/133
[  319.597264] ata1: EH complete
[  323.850204] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  323.850207] ata1.00: irq_stat 0x40000008
[  323.850214] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  323.850215]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  323.850218] ata1.00: status: { DRDY ERR }
[  323.850220] ata1.00: error: { UNC }
[  323.851415] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  323.853351] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  323.853354] ata1.00: configured for UDMA/133
[  323.853363] sd 0:0:0:0: [sda] Unhandled sense code
[  323.853365] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  323.853369] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  323.853374] Descriptor sense data with sense descriptors (in hex):
[  323.853376]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  323.853384]         1b c1 09 0e 
[  323.853388] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  323.853393] end_request: I/O error, dev sda, sector 465635598
[  323.853408] ata1: EH complete
[  328.186622] ata1.00: exception Emask 0x0 SAct 0x40 SErr 0x0 action 0x0
[  328.186627] ata1.00: irq_stat 0x40000008
[  328.186635] ata1.00: cmd 60/08:30:0e:09:c1/00:00:1b:00:00/40 tag 6 ncq 4096 in
[  328.186637]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  328.186640] ata1.00: status: { DRDY ERR }
[  328.186642] ata1.00: error: { UNC }
[  328.187852] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  328.189296] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  328.189300] ata1.00: configured for UDMA/133
[  328.189309] ata1: EH complete
[  332.450200] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  332.450202] ata1.00: irq_stat 0x40000008
[  332.450209] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  332.450210]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  332.450213] ata1.00: status: { DRDY ERR }
[  332.450214] ata1.00: error: { UNC }
[  332.451409] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  332.453387] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  332.453389] ata1.00: configured for UDMA/133
[  332.453395] ata1: EH complete
[  336.705712] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  336.705714] ata1.00: irq_stat 0x40000008
[  336.705721] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  336.705722]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  336.705725] ata1.00: status: { DRDY ERR }
[  336.705727] ata1.00: error: { UNC }
[  336.706926] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  336.708372] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  336.708375] ata1.00: configured for UDMA/133
[  336.708381] ata1: EH complete
[  340.950171] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  340.950175] ata1.00: irq_stat 0x40000008
[  340.950182] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  340.950183]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  340.950186] ata1.00: status: { DRDY ERR }
[  340.950188] ata1.00: error: { UNC }
[  340.951394] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  340.953352] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  340.953355] ata1.00: configured for UDMA/133
[  340.953368] ata1: EH complete
[  345.205726] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  345.205730] ata1.00: irq_stat 0x40000008
[  345.205738] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  345.205739]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  345.205742] ata1.00: status: { DRDY ERR }
[  345.205744] ata1.00: error: { UNC }
[  345.206948] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  345.208390] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  345.208393] ata1.00: configured for UDMA/133
[  345.208404] ata1: EH complete
[  349.450205] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  349.450210] ata1.00: irq_stat 0x40000008
[  349.450217] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  349.450219]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  349.450222] ata1.00: status: { DRDY ERR }
[  349.450224] ata1.00: error: { UNC }
[  349.451421] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  349.453354] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  349.453357] ata1.00: configured for UDMA/133
[  349.453368] sd 0:0:0:0: [sda] Unhandled sense code
[  349.453370] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  349.453374] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  349.453380] Descriptor sense data with sense descriptors (in hex):
[  349.453382]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  349.453390]         1b c1 09 0e 
[  349.453394] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  349.453399] end_request: I/O error, dev sda, sector 465635598
[  349.453416] ata1: EH complete
[  353.765813] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  353.765817] ata1.00: irq_stat 0x40000008
[  353.765826] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  353.765827]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  353.765830] ata1.00: status: { DRDY ERR }
[  353.765832] ata1.00: error: { UNC }
[  353.767035] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  353.768451] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  353.768454] ata1.00: configured for UDMA/133
[  353.768461] ata1: EH complete
[  358.027962] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  358.027966] ata1.00: irq_stat 0x40000008
[  358.027973] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  358.027974]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  358.027977] ata1.00: status: { DRDY ERR }
[  358.027979] ata1.00: error: { UNC }
[  358.029172] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  358.030598] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  358.030601] ata1.00: configured for UDMA/133
[  358.030609] ata1: EH complete
[  362.283471] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  362.283474] ata1.00: irq_stat 0x40000008
[  362.283481] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  362.283482]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  362.283485] ata1.00: status: { DRDY ERR }
[  362.283487] ata1.00: error: { UNC }
[  362.284685] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  362.286136] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  362.286138] ata1.00: configured for UDMA/133
[  362.286144] ata1: EH complete
[  366.527911] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  366.527914] ata1.00: irq_stat 0x40000008
[  366.527921] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  366.527922]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  366.527925] ata1.00: status: { DRDY ERR }
[  366.527927] ata1.00: error: { UNC }
[  366.529125] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  366.530567] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  366.530570] ata1.00: configured for UDMA/133
[  366.530575] ata1: EH complete
[  370.783534] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  370.783539] ata1.00: irq_stat 0x40000008
[  370.783547] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  370.783548]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  370.783552] ata1.00: status: { DRDY ERR }
[  370.783554] ata1.00: error: { UNC }
[  370.784765] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  370.786211] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  370.786214] ata1.00: configured for UDMA/133
[  370.786228] ata1: EH complete
[  375.039061] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  375.039064] ata1.00: irq_stat 0x40000008
[  375.039070] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  375.039072]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  375.039074] ata1.00: status: { DRDY ERR }
[  375.039076] ata1.00: error: { UNC }
[  375.040300] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  375.041761] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  375.041764] ata1.00: configured for UDMA/133
[  375.041772] sd 0:0:0:0: [sda] Unhandled sense code
[  375.041774] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  375.041777] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  375.041782] Descriptor sense data with sense descriptors (in hex):
[  375.041784]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  375.041792]         1b c1 09 0e 
[  375.041796] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  375.041801] end_request: I/O error, dev sda, sector 465635598
[  375.041816] ata1: EH complete
[  379.339029] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  379.339034] ata1.00: irq_stat 0x40000008
[  379.339042] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  379.339043]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  379.339046] ata1.00: status: { DRDY ERR }
[  379.339049] ata1.00: error: { UNC }
[  379.340252] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  379.341698] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  379.341701] ata1.00: configured for UDMA/133
[  379.341710] ata1: EH complete
[  383.594608] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  383.594611] ata1.00: irq_stat 0x40000008
[  383.594618] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  383.594619]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  383.594622] ata1.00: status: { DRDY ERR }
[  383.594624] ata1.00: error: { UNC }
[  383.595805] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  383.597253] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  383.597256] ata1.00: configured for UDMA/133
[  383.597262] ata1: EH complete
[  387.850164] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  387.850167] ata1.00: irq_stat 0x40000008
[  387.850174] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  387.850175]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  387.850178] ata1.00: status: { DRDY ERR }
[  387.850180] ata1.00: error: { UNC }
[  387.851357] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  387.853349] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  387.853352] ata1.00: configured for UDMA/133
[  387.853357] ata1: EH complete
[  392.105672] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  392.105675] ata1.00: irq_stat 0x40000008
[  392.105681] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  392.105683]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  392.105685] ata1.00: status: { DRDY ERR }
[  392.105687] ata1.00: error: { UNC }
[  392.106885] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  392.108317] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  392.108320] ata1.00: configured for UDMA/133
[  392.108325] ata1: EH complete
[  396.361230] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  396.361233] ata1.00: irq_stat 0x40000008
[  396.361239] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  396.361240]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  396.361243] ata1.00: status: { DRDY ERR }
[  396.361245] ata1.00: error: { UNC }
[  396.362447] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  396.364342] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  396.364344] ata1.00: configured for UDMA/133
[  396.364350] ata1: EH complete
[  400.605712] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  400.605716] ata1.00: irq_stat 0x40000008
[  400.605723] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  400.605724]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  400.605727] ata1.00: status: { DRDY ERR }
[  400.605729] ata1.00: error: { UNC }
[  400.606923] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  400.608350] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  400.608353] ata1.00: configured for UDMA/133
[  400.608363] sd 0:0:0:0: [sda] Unhandled sense code
[  400.608365] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  400.608369] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  400.608374] Descriptor sense data with sense descriptors (in hex):
[  400.608376]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  400.608384]         1b c1 09 0e 
[  400.608388] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  400.608393] end_request: I/O error, dev sda, sector 465635598
[  400.608413] ata1: EH complete
[  404.861244] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  404.861249] ata1.00: irq_stat 0x40000008
[  404.861257] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  404.861258]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  404.861261] ata1.00: status: { DRDY ERR }
[  404.861263] ata1.00: error: { UNC }
[  404.862466] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  404.864320] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  404.864323] ata1.00: configured for UDMA/133
[  404.864333] ata1: EH complete
[  409.105677] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  409.105680] ata1.00: irq_stat 0x40000008
[  409.105688] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  409.105689]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  409.105692] ata1.00: status: { DRDY ERR }
[  409.105694] ata1.00: error: { UNC }
[  409.106905] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  409.108350] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  409.108353] ata1.00: configured for UDMA/133
[  409.108361] ata1: EH complete
[  413.350108] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  413.350111] ata1.00: irq_stat 0x40000008
[  413.350118] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  413.350119]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  413.350122] ata1.00: status: { DRDY ERR }
[  413.350124] ata1.00: error: { UNC }
[  413.351324] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  413.353351] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  413.353353] ata1.00: configured for UDMA/133
[  413.353360] ata1: EH complete
[  417.605656] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  417.605660] ata1.00: irq_stat 0x40000008
[  417.605668] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  417.605669]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  417.605672] ata1.00: status: { DRDY ERR }
[  417.605675] ata1.00: error: { UNC }
[  417.606880] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  417.608341] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  417.608344] ata1.00: configured for UDMA/133
[  417.608351] ata1: EH complete
[  421.872331] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  421.872336] ata1.00: irq_stat 0x40000008
[  421.872344] ata1.00: cmd 60/08:08:0e:09:c1/00:00:1b:00:00/40 tag 1 ncq 4096 in
[  421.872345]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  421.872348] ata1.00: status: { DRDY ERR }
[  421.872350] ata1.00: error: { UNC }
[  421.873563] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  421.875001] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  421.875004] ata1.00: configured for UDMA/133
[  421.875015] ata1: EH complete
[  426.132601] ata1.00: exception Emask 0x0 SAct 0x6 SErr 0x0 action 0x0
[  426.132604] ata1.00: irq_stat 0x40000008
[  426.132610] ata1.00: cmd 60/08:08:0e:09:c1/00:00:1b:00:00/40 tag 1 ncq 4096 in
[  426.132612]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  426.132614] ata1.00: status: { DRDY ERR }
[  426.132616] ata1.00: error: { UNC }
[  426.133818] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  426.135245] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  426.135247] ata1.00: configured for UDMA/133
[  426.135255] sd 0:0:0:0: [sda] Unhandled sense code
[  426.135257] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  426.135261] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  426.135266] Descriptor sense data with sense descriptors (in hex):
[  426.135268]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  426.135276]         1b c1 09 0e 
[  426.135280] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  426.135285] end_request: I/O error, dev sda, sector 465635598
[  426.135295] ata1: EH complete
[  430.416813] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  430.416818] ata1.00: irq_stat 0x40000008
[  430.416827] ata1.00: cmd 60/08:08:0e:09:c1/00:00:1b:00:00/40 tag 1 ncq 4096 in
[  430.416828]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  430.416831] ata1.00: status: { DRDY ERR }
[  430.416833] ata1.00: error: { UNC }
[  430.418030] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  430.419469] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  430.419472] ata1.00: configured for UDMA/133
[  430.419482] ata1: EH complete
[  434.672333] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  434.672338] ata1.00: irq_stat 0x40000008
[  434.672345] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  434.672346]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  434.672349] ata1.00: status: { DRDY ERR }
[  434.672351] ata1.00: error: { UNC }
[  434.673563] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  434.675000] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  434.675003] ata1.00: configured for UDMA/133
[  434.675013] ata1: EH complete
[  438.950135] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[  438.950137] ata1.00: irq_stat 0x40000008
[  438.950144] ata1.00: cmd 60/08:08:0e:09:c1/00:00:1b:00:00/40 tag 1 ncq 4096 in
[  438.950145]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  438.950148] ata1.00: status: { DRDY ERR }
[  438.950150] ata1.00: error: { UNC }
[  438.951330] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  438.953346] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  438.953348] ata1.00: configured for UDMA/133
[  438.953355] ata1: EH complete
[  443.205651] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  443.205654] ata1.00: irq_stat 0x40000008
[  443.205660] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  443.205661]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  443.205664] ata1.00: status: { DRDY ERR }
[  443.205666] ata1.00: error: { UNC }
[  443.206868] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  443.208330] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  443.208332] ata1.00: configured for UDMA/133
[  443.208339] ata1: EH complete
[  447.461237] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  447.461240] ata1.00: irq_stat 0x40000008
[  447.461246] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  447.461247]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  447.461250] ata1.00: status: { DRDY ERR }
[  447.461252] ata1.00: error: { UNC }
[  447.462432] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  447.464321] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  447.464324] ata1.00: configured for UDMA/133
[  447.464330] ata1: EH complete
[  451.716787] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  451.716790] ata1.00: irq_stat 0x40000008
[  451.716796] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  451.716797]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  451.716800] ata1.00: status: { DRDY ERR }
[  451.716802] ata1.00: error: { UNC }
[  451.717982] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  451.719430] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  451.719432] ata1.00: configured for UDMA/133
[  451.719440] sd 0:0:0:0: [sda] Unhandled sense code
[  451.719442] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  451.719446] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  451.719451] Descriptor sense data with sense descriptors (in hex):
[  451.719453]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  451.719461]         1b c1 09 0e 
[  451.719464] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  451.719470] end_request: I/O error, dev sda, sector 465635598
[  451.719482] ata1: EH complete
[  456.077612] ata1.00: exception Emask 0x0 SAct 0x10000 SErr 0x0 action 0x0
[  456.077615] ata1.00: irq_stat 0x40000008
[  456.077622] ata1.00: cmd 60/08:80:0e:09:c1/00:00:1b:00:00/40 tag 16 ncq 4096 in
[  456.077624]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  456.077626] ata1.00: status: { DRDY ERR }
[  456.077629] ata1.00: error: { UNC }
[  456.078832] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  456.080265] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  456.080267] ata1.00: configured for UDMA/133
[  456.080273] ata1: EH complete
[  460.327853] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  460.327856] ata1.00: irq_stat 0x40000008
[  460.327862] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  460.327864]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  460.327866] ata1.00: status: { DRDY ERR }
[  460.327868] ata1.00: error: { UNC }
[  460.329065] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  460.330513] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  460.330516] ata1.00: configured for UDMA/133
[  460.330521] ata1: EH complete
[  464.583416] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  464.583421] ata1.00: irq_stat 0x40000008
[  464.583429] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  464.583430]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  464.583433] ata1.00: status: { DRDY ERR }
[  464.583435] ata1.00: error: { UNC }
[  464.584640] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  464.586081] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  464.586084] ata1.00: configured for UDMA/133
[  464.586094] ata1: EH complete
[  468.839005] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  468.839009] ata1.00: irq_stat 0x40000008
[  468.839017] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  468.839018]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  468.839021] ata1.00: status: { DRDY ERR }
[  468.839023] ata1.00: error: { UNC }
[  468.840219] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  468.841654] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  468.841657] ata1.00: configured for UDMA/133
[  468.841665] ata1: EH complete
[  473.094515] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  473.094519] ata1.00: irq_stat 0x40000008
[  473.094525] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  473.094526]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  473.094529] ata1.00: status: { DRDY ERR }
[  473.094531] ata1.00: error: { UNC }
[  473.095733] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  473.097188] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  473.097191] ata1.00: configured for UDMA/133
[  473.097197] ata1: EH complete
[  477.338953] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  477.338956] ata1.00: irq_stat 0x40000008
[  477.338962] ata1.00: cmd 60/08:00:0e:09:c1/00:00:1b:00:00/40 tag 0 ncq 4096 in
[  477.338964]          res 51/40:08:0e:09:c1/ff:00:1b:00:00/40 Emask 0x409 (media error) <F>
[  477.338966] ata1.00: status: { DRDY ERR }
[  477.338968] ata1.00: error: { UNC }
[  477.340167] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  477.341631] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  477.341634] ata1.00: configured for UDMA/133
[  477.341643] sd 0:0:0:0: [sda] Unhandled sense code
[  477.341645] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  477.341649] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  477.341653] Descriptor sense data with sense descriptors (in hex):
[  477.341655]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  477.341663]         1b c1 09 0e 
[  477.341667] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  477.341672] end_request: I/O error, dev sda, sector 465635598
[  477.341687] ata1: EH complete
```

I have no idea what to make of what I'm seeing. Someone please help!

---

### Post by rustutzman on 2010-02-25
Hmmm... looks to me like you have a failing hard drive. That would explain the slowness as the drive has to keep re-reading the same sectors to load the data. 

You might want to boot to a live cd and fsck your laptop drive and see what it comes up with.

Russ

---

### Post by seventhsamurai on 2010-02-25
Hi Russ

Thanks for the idea. I'll give it a shot. But once Ubuntu has finished booting, it works flawlessly and I don't experience any difference in speed except when I shut down. When I suspend the system, it goes into suspension without issues and bounces back from suspension equally fast. I even booted my Windows Vista partition and that boots and runs just fine (or at least how it's supposed to). Wouldn't a failing hard drive affect performance of either OS after booting as well?

Let me try the fsck option and get back to you.

Thanks again.

---

### Post by seventhsamurai on 2010-02-25
I tried with a live CD. Used G-Part. Basically I booted off the disc, selected the partition on which Ubuntu is installed, and selected "check" and then "apply". It finished the process within 10 seconds. Fishy.

Then when I tried to reboot, it was hanging on some error, and shut down. Boot speed has not improved. Im on the verge of formatting the partition and re-installing. any other ideas?

---

### Post by rustutzman on 2010-02-25
You might have some bad sectors that you're current install is on causing the lag. At any rate as long as you don't have any data to lose a re-install might the quickest solution. 

Russ

---

### Post by NightwishFan on 2010-02-25
Make sure you check the CD for errors. Also the Disk Utility in System -> Administration can check hard disk status.

---

### Post by shadowlands on 2010-02-25
> **seventhsamurai said:**
> Ubuntu 9.10 Karmic Koala - Very Slow (7.5 minutes) Boot up and Very Slow Shutdown Issue

Hi guys. I hope someone here can help me out. I'm having a major boot and shutdown issue with Ubuntu 9.10 Karmic Koala. I am running it on an Acer Extensa 4420 Laptop with AMD 64, 3 GB RAM.

I am a novice with Linux and have been using Ubuntu instead of Windows Vista for just over 2 months now, and am a very average computer user so please forgive me if I sound ignorant or I ask any stupid follow-up questions. I have gone through most of the forum posts online that talk about Ubuntu boot or shut down issues, tried a bunch of the solutions offered there, but nothing seems to be working.

Ubuntu takes nearly 7.5 minutes to fully boot. Grub loads up fine, then I select my option to boot (I have a Windows Vista boot option as well, which I rarely use nowadays). Once I select, it stalls on the Ubuntu Logo for a while. Then the splash screen shows up, and then the login screen. When I select the user account, it stalls for a while, then allows me to enter the password. After I do, it just waits, and waits, and waits, and by the time Ubuntu is fully loaded, its been nearly 7.5 mins. Until last night, I was able to boot from scratch within 30 seconds.

Shutdown used to happen within 15 seconds before, But takes longer now.

Please help me someone! I got sick of windows, explored Ubuntu, fell in love with it. Now I really need this problem fixed. I would hate to reinstall it and lose my stuff. Is there a way to just reinstall Ubuntu without deleting any of my installed programs and files? Can it be repaired, say like a windows reinstall, where when you have an issue, you can always try popping the CD in a reinstalling and repairing in the process?

I'd appreciate any help you can offer.

Thanks.

I think you woul ddbe much happer with 09.4. After much crying and frustration I went back to 09.4 and I am so happy now.

---

### Post by NightwishFan on 2010-02-25
Depends on the hardware. Some users may actually be better off with a newer kernel.

---

### Post by seventhsamurai on 2010-02-26
I just popped in a live cd and reformatted the partition and reinstalled ubuntu. A hassle but at least its working fine now.

---

### Post by VAkaras on 2010-09-18
Hi, all. I seem to have similar problem and I have no idea how to solve it.

After some system updates or after new program install, Ubuntu doesn't restart normally. (It seems that this happens, when kernel is somehow touched.) It loads until login screen normally, then asks for password, and when I enter it, login dialog box disappears and nothing happens. When I try to switch to TTY1, I see these messages showed:

```

[   19.082236] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   19.082245] ata1.00: irq_stat 0x40000008
[   19.082252] ata1.00: failed command: READ FPDMA QUEUED
[   19.082263] ata1.00: cmd 60/00:00:40:e1:b8/02:00:1a:00:00/40 tag 0 ncq 262144 in
[   19.082266]          res 41/40:00:75:e1:b8/00:00:1a:00:00/40 Emask 0x409 (media error) <F>
[   19.082272] ata1.00: status: { DRDY ERR }
[   19.082276] ata1.00: error: { UNC }
[   19.102260] ata1.00: configured for UDMA/133
[   19.102278] ata1: EH complete
[   23.302115] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[   23.302123] ata1.00: irq_stat 0x40000008
[   23.302130] ata1.00: failed command: READ FPDMA QUEUED
[   23.302141] ata1.00: cmd 60/00:00:40:e8:b8/01:00:1a:00:00/40 tag 0 ncq 131072 in
[   23.302144]          res 41/40:00:f4:e8:b8/00:00:1a:00:00/40 Emask 0x409 (media error) <F>
[   23.302150] ata1.00: status: { DRDY ERR }
[   23.302154] ata1.00: error: { UNC }
[   23.322152] ata1.00: configured for UDMA/133
[   23.322174] ata1: EH complete
[   25.623071] ata1.00: exception Emask 0x0 SAct 0x4 SErr 0x0 action 0x0
[   25.623074] ata1.00: irq_stat 0x40000008
[   25.623077] ata1.00: failed command: READ FPDMA QUEUED
[   25.623084] ata1.00: cmd 60/00:10:40:e8:b8/01:00:1a:00:00/40 tag 2 ncq 131072 in
[   25.623085]          res 41/40:00:f4:e8:b8/00:00:1a:00:00/40 Emask 0x409 (media error) <F>
[   25.623089] ata1.00: status: { DRDY ERR }
[   25.623091] ata1.00: error: { UNC }
[   25.643017] ata1.00: configured for UDMA/133
[   25.643032] ata1: EH complete
[   27.721946] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   27.721952] ata1.00: irq_stat 0x40000008
[   27.721957] ata1.00: failed command: READ FPDMA QUEUED
[   27.721968] ata1.00: cmd 60/00:00:40:e8:b8/01:00:1a:00:00/40 tag 0 ncq 131072 in
[   27.721970]          res 41/40:00:f4:e8:b8/00:00:1a:00:00/40 Emask 0x409 (media error) <F>
[   27.721976] ata1.00: status: { DRDY ERR }
[   27.721980] ata1.00: error: { UNC }
[   27.741953] ata1.00: configured for UDMA/133
[   27.741968] ata1: EH complete
[   29.776376] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   29.776381] ata1.00: irq_stat 0x40000008
[   29.776386] ata1.00: failed command: READ FPDMA QUEUED
[   29.776397] ata1.00: cmd 60/00:00:40:e8:b8/01:00:1a:00:00/40 tag 0 ncq 131072 in
[   29.776400]          res 41/40:00:f4:e8:b8/00:00:1a:00:00/40 Emask 0x409 (media error) <F>
[   29.776405] ata1.00: status: { DRDY ERR }


```

Then I reboot computer with Sys Rq. When Ubuntu is booting it starts file system check, which founds errors on my home partition, fixes it and system starts normally. After logging in I almost always have to restore some programs configuration (for example compiz and firefox) from backup.

Could someone tell me where I should look for the reasons and possible solution of this problem?

P.S. I am using Samsung NP-R528-DT01EE laptop with Ubuntu lucid 64-bit. /, /boot and /home partitions are formated as ext4.
P.P.S. Sorry for my English.

---

