---
title: "Compiz crashes Ubuntu"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-29
Hi Everyone,

I just upgraded to Ubuntu 9.10 and I have the GM965 chipset.

I was in Compiz-Config Settings manager in one of my standard user accounts. I enabled the "Reflection" effect. Now everytime compiz is loaded by that account on login, it locks up the entire OS. I can only type this to you from the root account. 

How can I "uncheck" the user-made reflection setting in CCSM from the root account? Is this possible? Is my home user account now trashed? 

My touchpad also no longer works. I tried:
```
sudo /etc/init.d/hal restart
```

but Ubuntu claims it no longer knows what "hal" is. What controls removable devices in Ubuntu 9.10? How do I restart that process?

Thanks!:p

---

### Post by asuastrophysics on 2009-10-29
c'mon, no one has any ideas? I've used ubuntu for a year now and it's just this most recent upgrade that's caught me offguard. 

My laptop is almost completely unusable right now. Does anyone know how to restart new the hardware layer abstraction service in Karmic? I heard they no longer use "hal". I was told it's "depreciated" in Karmic. Does anyone know???

---

### Post by lavinog on 2009-10-29
> **asuastrophysics said:**
> 
but Ubuntu claims it no longer knows what "hal" is. What controls removable devices in Ubuntu 9.10? How do I restart that process?


from [http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)
> Ubuntu 9.10 RC's underlying technology for power management, laptop hotkeys, and handling of storage devices and cameras maps has moved from "hal" (which is in the process of being deprecated) to "DeviceKit-power", "DeviceKit-disks" and "udev".

for your compiz issue, you might want to rm your user settings for compiz:
```

rm -r /home/username/.compiz

```

or if you don't want to remove, just rename:
```

mv /home/username/.compiz /home/username/.compiz_backup

```

---

### Post by asuastrophysics on 2009-10-29
thanks that fixed my compiz issue!!!! :D
:popcorn:

---

### Post by lavinog on 2009-10-29
what is not working with your touchpad.

Is it disabled completely or are you not able to use the buttons?
can you post your dmesg?

---

### Post by asuastrophysics on 2009-10-29
> **lavinog said:**
> what is not working with your touchpad.

Is it disabled completely or are you not able to use the buttons?
can you post your dmesg?

It wasn't working at all at first. I had to use a USB mouse for a while.
A few restarts remedied that problem, but my two-finger scrolling feature is still disabled, as well as the center 4-direction button between the left and right mouse buttons. (I press up/down on this to scroll vertically, and left/right to scroll horizontally. 

The output of "dmesg" was so large that I couldn't even find the start point where I issued the command. Is there a certain place within "dmesg" I should post to save you time, so you don't have to look through the whole thing? :) 

Thanks a lot for your help! :D :popcorn:

---

### Post by lavinog on 2009-10-29
```
dmesg>dmesg.txt
```
you can then attache dmesg.txt
It looks like you figured out as much as I will be able to figure out though.

---

### Post by asuastrophysics on 2009-10-29
> **lavinog said:**
> ```
dmesg>dmesg.txt
```
you can then attache dmesg.txt
It looks like you figured out as much as I will be able to figure out though.

Here is that dmesg file:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: root=UUID=29fd35f3-2c43-4ee5-9c64-484c7d1a78d0 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6e1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6e1000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7f6d0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  modified: 000000007f6d0000 - 000000007f6e1000 (ACPI NVS)
[    0.000000]  modified: 000000007f6e1000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007f6d0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 007f600000 page 2M
[    0.000000]  007f600000 - 007f6d0000 page 4k
[    0.000000] kernel direct mapping tables up to 7f6d0000 @ 8000-c000
[    0.000000] RAMDISK: 3786f000 - 37fef091
[    0.000000] ACPI: RSDP 00000000000f7b50 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 000000007f6d3921 0007C (v01 ACRSYS ACRPRDCT 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 000000007f6ddc2a 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 000000007f6d4de1 08DD5 (v02 INTEL  CRESTLNE 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS 000000007f6e0fc0 00040
[    0.000000] ACPI: APIC 000000007f6ddd1e 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 000000007f6ddd86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 000000007f6dddbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 000000007f6dddfa 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 000000007f6dde62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 000000007f6dde8a 00176 (v01 ACRSYS ACRPRDCT 06040000 acer 00000000)
[    0.000000] ACPI: SSDT 000000007f6d4b04 002DD (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 000000007f6d3f29 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 000000007f6d3e83 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 000000007f6d399d 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007f6d0000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007f6d0000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  000000000001eedf] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007f6d0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [003786f000 - 0037fef091]          RAMDISK ==> [003786f000 - 0037fef091]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3178]              BRK ==> [00019e3000 - 00019e3178]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000f7b80] f7b80
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f6d0
[    0.000000] On node 0 totalpages: 521834
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 101 pages reserved
[    0.000000]   DMA zone: 3837 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7080 pages used for memmap
[    0.000000]   DMA32 zone: 510760 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019f4000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 514597
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=29fd35f3-2c43-4ee5-9c64-484c7d1a78d0 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2040444k/2087744k available (5313k kernel code, 408k absent, 46892k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1733.421 MHz processor.
[    0.001424] Console: colour VGA+ 80x25
[    0.001427] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3466.84 BogoMIPS (lpj=17334210)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 1024K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring handled by SMI
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.030072] Setting APIC routing to flat
[    0.030458] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.133428] CPU0: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz stepping 0d
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3466.58 BogoMIPS (lpj=17332933)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 1024K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring handled by SMI
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.291432] CPU1: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz stepping 0d
[    0.291444] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300030] Brought up 2 CPUs
[    0.300033] Total of 2 processors activated (6933.42 BogoMIPS).
[    0.300094] CPU0 attaching sched-domain:
[    0.300098]  domain 0: span 0-1 level MC
[    0.300101]   groups: 0 1
[    0.300108] CPU1 attaching sched-domain:
[    0.300110]  domain 0: span 0-1 level MC
[    0.300113]   groups: 1 0
[    0.300201] Booting paravirtualized kernel on bare hardware
[    0.300203] regulator: core version 0.5
[    0.300203] Time:  7:56:29  Date: 10/29/09
[    0.300203] NET: Registered protocol family 16
[    0.300262] ACPI: bus type pci registered
[    0.300344] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.300348] PCI: MCFG area at e0000000 reserved in E820
[    0.306183] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.306186] PCI: Using configuration type 1 for base access
[    0.307244] bio: create slab <bio-0> at 0
[    0.310593] ACPI: EC: Look up EC in DSDT
[    0.315219] ACPI: BIOS _OSI(Linux) query ignored
[    0.316551] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.850004] ACPI: EC: missing confirmations, switch off interrupt mode.
[    1.990086] ACPI: Interpreter enabled
[    1.990090] ACPI: (supports S0 S3 S4 S5)
[    1.990116] ACPI: Using IOAPIC for interrupt routing
[    1.995661] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    1.995664] ACPI: EC: driver started in poll mode
[    1.996049] ACPI: No dock devices found.
[    1.996731] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.996738] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007d32abc0), AE_NOT_FOUND
[    1.996774] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.996895] pci 0000:00:02.0: reg 10 64bit mmio: [0xf0000000-0xf00fffff]
[    1.996904] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    1.996911] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    1.996963] pci 0000:00:02.1: reg 10 64bit mmio: [0xf0100000-0xf01fffff]
[    1.997098] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    1.997174] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    1.997257] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf0704800-0xf0704bff]
[    1.997331] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.997338] pci 0000:00:1a.7: PME# disabled
[    1.997400] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf0500000-0xf0503fff]
[    1.997471] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.997477] pci 0000:00:1b.0: PME# disabled
[    1.997577] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.997582] pci 0000:00:1c.0: PME# disabled
[    1.997689] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.997694] pci 0000:00:1c.1: PME# disabled
[    1.997798] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.997803] pci 0000:00:1c.2: PME# disabled
[    1.997883] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
[    1.997959] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
[    1.998033] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
[    1.998119] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf0704c00-0xf0704fff]
[    1.998192] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.998199] pci 0000:00:1d.7: PME# disabled
[    1.998393] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    1.998398] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    1.998403] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    1.998408] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0600 (mask 003f)
[    1.998415] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0068 (mask 0007)
[    1.998476] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    1.998485] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    1.998494] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    1.998503] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    1.998512] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    1.998598] pci 0000:00:1f.2: reg 10 io port: [0x1c00-0x1c07]
[    1.998607] pci 0000:00:1f.2: reg 14 io port: [0x18d4-0x18d7]
[    1.998617] pci 0000:00:1f.2: reg 18 io port: [0x18d8-0x18df]
[    1.998625] pci 0000:00:1f.2: reg 1c io port: [0x18d0-0x18d3]
[    1.998635] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    1.998644] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf0704000-0xf07047ff]
[    1.998692] pci 0000:00:1f.2: PME# supported from D3hot
[    1.998698] pci 0000:00:1f.2: PME# disabled
[    1.998736] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    1.998765] pci 0000:00:1f.3: reg 20 io port: [0x1c20-0x1c3f]
[    1.998871] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
[    1.998877] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    1.998886] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    1.998966] pci 0000:04:00.0: reg 10 64bit mmio: [0x000000-0x00ffff]
[    1.999158] pci 0000:00:1c.1: bridge io port: [0x00-0xfff]
[    1.999163] pci 0000:00:1c.1: bridge 32bit mmio: [0x000000-0x0fffff]
[    1.999172] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    1.999406] pci 0000:05:00.0: reg 10 64bit mmio: [0x000000-0x00ffff]
[    1.999656] pci 0000:05:00.0: PME# supported from D3hot D3cold
[    1.999668] pci 0000:05:00.0: PME# disabled
[    1.999793] pci 0000:00:1c.2: bridge io port: [0x00-0xfff]
[    1.999798] pci 0000:00:1c.2: bridge 32bit mmio: [0x000000-0x0fffff]
[    1.999807] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    1.999879] pci 0000:0a:09.0: reg 10 32bit mmio: [0xf0400000-0xf04007ff]
[    1.999947] pci 0000:0a:09.0: supports D1 D2
[    1.999950] pci 0000:0a:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.999956] pci 0000:0a:09.0: PME# disabled
[    2.000025] pci 0000:0a:09.1: reg 10 32bit mmio: [0xf0400800-0xf04008ff]
[    2.000093] pci 0000:0a:09.1: supports D1 D2
[    2.000095] pci 0000:0a:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    2.000101] pci 0000:0a:09.1: PME# disabled
[    2.000151] pci 0000:0a:09.2: reg 10 32bit mmio: [0xf0400c00-0xf0400cff]
[    2.000220] pci 0000:0a:09.2: supports D1 D2
[    2.000222] pci 0000:0a:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    2.000228] pci 0000:0a:09.2: PME# disabled
[    2.000279] pci 0000:0a:09.3: reg 10 32bit mmio: [0xf0401000-0xf04010ff]
[    2.000348] pci 0000:0a:09.3: supports D1 D2
[    2.000350] pci 0000:0a:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    2.000356] pci 0000:0a:09.3: PME# disabled
[    2.000405] pci 0000:0a:09.4: reg 10 32bit mmio: [0xf0401400-0xf04014ff]
[    2.000473] pci 0000:0a:09.4: supports D1 D2
[    2.000475] pci 0000:0a:09.4: PME# supported from D0 D1 D2 D3hot D3cold
[    2.000481] pci 0000:0a:09.4: PME# disabled
[    2.000544] pci 0000:00:1e.0: transparent bridge
[    2.000553] pci 0000:00:1e.0: bridge 32bit mmio: [0xf0400000-0xf04fffff]
[    2.000594] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.000863] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    2.000956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    2.001037] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    2.001168] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    2.001282] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    2.001288] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007d32abc0), AE_NOT_FOUND
[    2.015139] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    2.015265] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    2.015389] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    2.015511] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    2.015633] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    2.015756] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    2.015877] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    2.015999] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    2.016227] SCSI subsystem initialized
[    2.016281] libata version 3.00 loaded.
[    2.016281] usbcore: registered new interface driver usbfs
[    2.016281] usbcore: registered new interface driver hub
[    2.016281] usbcore: registered new device driver usb
[    2.016281] ACPI: WMI: Mapper loaded
[    2.016281] PCI: Using ACPI for IRQ routing
[    2.016281] pci 0000:00:1c.0: BAR 13: can't allocate resource
[    2.016281] pci 0000:00:1c.0: BAR 14: can't allocate resource
[    2.016281] pci 0000:00:1c.0: BAR 15: can't allocate resource
[    2.016281] pci 0000:00:1c.1: BAR 13: can't allocate resource
[    2.016281] pci 0000:00:1c.1: BAR 14: can't allocate resource
[    2.016281] pci 0000:00:1c.1: BAR 15: can't allocate resource
[    2.016281] pci 0000:00:1c.2: BAR 13: can't allocate resource
[    2.016281] pci 0000:00:1c.2: BAR 14: can't allocate resource
[    2.016281] pci 0000:00:1c.2: BAR 15: can't allocate resource
[    2.040009] Bluetooth: Core ver 2.15
[    2.040035] NET: Registered protocol family 31
[    2.040035] Bluetooth: HCI device and connection manager initialized
[    2.040035] Bluetooth: HCI socket layer initialized
[    2.040035] NetLabel: Initializing
[    2.040035] NetLabel:  domain hash size = 128
[    2.040035] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.040043] NetLabel:  unlabeled traffic allowed by default
[    2.040111] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    2.040117] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    2.060029] Switched to high resolution mode on CPU 0
[    2.061465] Switched to high resolution mode on CPU 1
[    2.080017] pnp: PnP ACPI init
[    2.080044] ACPI: bus type pnp registered
[    2.082664] pnp: PnP ACPI: found 11 devices
[    2.082667] ACPI: ACPI bus type pnp unregistered
[    2.082680] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    2.082684] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    2.082687] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    2.082691] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    2.082694] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    2.082697] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    2.082701] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    2.082704] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    2.082712] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    2.082720] system 00:06: ioport range 0x680-0x69f has been reserved
[    2.082724] system 00:06: ioport range 0x800-0x80f has been reserved
[    2.082727] system 00:06: ioport range 0x1000-0x107f has been reserved
[    2.082731] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    2.082738] system 00:06: ioport range 0x1640-0x164f has been reserved
[    2.082742] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    2.087467] AppArmor: AppArmor Filesystem Enabled
[    2.087565] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    2.087568] pci 0000:00:1c.0:   IO window: disabled
[    2.087575] pci 0000:00:1c.0:   MEM window: disabled
[    2.087581] pci 0000:00:1c.0:   PREFETCH window: disabled
[    2.087596] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    2.087598] pci 0000:00:1c.1:   IO window: disabled
[    2.087606] pci 0000:00:1c.1:   MEM window: 0x80000000-0x800fffff
[    2.087611] pci 0000:00:1c.1:   PREFETCH window: disabled
[    2.087672] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    2.087674] pci 0000:00:1c.2:   IO window: disabled
[    2.087681] pci 0000:00:1c.2:   MEM window: 0x80100000-0x801fffff
[    2.087686] pci 0000:00:1c.2:   PREFETCH window: disabled
[    2.087693] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    2.087695] pci 0000:00:1e.0:   IO window: disabled
[    2.087702] pci 0000:00:1e.0:   MEM window: 0xf0400000-0xf04fffff
[    2.087707] pci 0000:00:1e.0:   PREFETCH window: disabled
[    2.087725]   alloc irq_desc for 17 on node 0
[    2.087727]   alloc kstat_irqs on node 0
[    2.087734] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.087742] pci 0000:00:1c.0: setting latency timer to 64
[    2.087752] pci 0000:00:1c.1: enabling device (0000 -> 0002)
[    2.087756]   alloc irq_desc for 16 on node 0
[    2.087758]   alloc kstat_irqs on node 0
[    2.087762] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    2.087769] pci 0000:00:1c.1: setting latency timer to 64
[    2.087779] pci 0000:00:1c.2: enabling device (0000 -> 0002)
[    2.087783]   alloc irq_desc for 18 on node 0
[    2.087785]   alloc kstat_irqs on node 0
[    2.087789] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.087796] pci 0000:00:1c.2: setting latency timer to 64
[    2.087806] pci 0000:00:1e.0: setting latency timer to 64
[    2.087812] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    2.087815] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    2.087818] pci_bus 0000:02: resource 0 mem: [0x0-0xfff]
[    2.087820] pci_bus 0000:02: resource 1 mem: [0x0-0xfffff]
[    2.087823] pci_bus 0000:02: resource 2 mem: [0x0-0xfffff]
[    2.087825] pci_bus 0000:04: resource 0 mem: [0x0-0xfff]
[    2.087828] pci_bus 0000:04: resource 1 mem: [0x80000000-0x800fffff]
[    2.087831] pci_bus 0000:04: resource 2 mem: [0x0-0xfffff]
[    2.087833] pci_bus 0000:05: resource 0 mem: [0x0-0xfff]
[    2.087836] pci_bus 0000:05: resource 1 mem: [0x80100000-0x801fffff]
[    2.087838] pci_bus 0000:05: resource 2 mem: [0x0-0xfffff]
[    2.087841] pci_bus 0000:0a: resource 1 mem: [0xf0400000-0xf04fffff]
[    2.087844] pci_bus 0000:0a: resource 3 io:  [0x00-0xffff]
[    2.087847] pci_bus 0000:0a: resource 4 mem: [0x000000-0xffffffffffffffff]
[    2.087890] NET: Registered protocol family 2
[    2.088058] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    2.089029] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    2.091984] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.092702] TCP: Hash tables configured (established 262144 bind 65536)
[    2.092707] TCP reno registered
[    2.092864] NET: Registered protocol family 1
[    2.092967] Trying to unpack rootfs image as initramfs...
[    2.308268] Freeing initrd memory: 7680k freed
[    2.313592] Simple Boot Flag at 0x35 set to 0x1
[    2.313828] Scanning for low memory corruption every 60 seconds
[    2.314013] audit: initializing netlink socket (disabled)
[    2.314038] type=2000 audit(1256802990.310:1): initialized
[    2.325618] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.327283] VFS: Disk quotas dquot_6.5.2
[    2.327353] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.328043] fuse init (API version 7.12)
[    2.328137] msgmni has been set to 4000
[    2.328384] alg: No test for stdrng (krng)
[    2.328401] io scheduler noop registered
[    2.328404] io scheduler anticipatory registered
[    2.328407] io scheduler deadline registered
[    2.328461] io scheduler cfq registered (default)
[    2.328477] pci 0000:00:02.0: Boot video device
[    2.328835]   alloc irq_desc for 24 on node 0
[    2.328838]   alloc kstat_irqs on node 0
[    2.328853] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    2.328866] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.329076]   alloc irq_desc for 25 on node 0
[    2.329078]   alloc kstat_irqs on node 0
[    2.329089] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    2.329101] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.329307]   alloc irq_desc for 26 on node 0
[    2.329310]   alloc kstat_irqs on node 0
[    2.329320] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    2.329333] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    2.329462] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.329538] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    2.329545] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007d32abc0), AE_NOT_FOUND
[    2.329633] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    2.329639] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007d32abc0), AE_NOT_FOUND
[    2.329715] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    2.329721] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007d32abc0), AE_NOT_FOUND
[    2.329815] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    2.329821] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007d32abc0), AE_NOT_FOUND
[    2.329895] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    2.329901] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007d32abc0), AE_NOT_FOUND
[    2.329974] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    2.329980] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007d32abc0), AE_NOT_FOUND
[    2.330047] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.470114] ACPI: AC Adapter [ACAD] (on-line)
[    2.470185] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.470189] ACPI: Power Button [PWRF]
[    2.470268] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.470340] ACPI: Lid Switch [LID]
[    2.470390] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    2.470393] ACPI: Power Button [PWRB]
[    2.470444] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    2.470447] ACPI: Sleep Button [SLPB]
[    2.471222] ACPI: SSDT 000000007f6d4804 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    2.471821] ACPI: SSDT 000000007f6d4188 005F7 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    2.474670] Monitor-Mwait will be used to enter C-1 state
[    2.474711] Monitor-Mwait will be used to enter C-2 state
[    2.474735] Monitor-Mwait will be used to enter C-3 state
[    2.474744] Marking TSC unstable due to TSC halts in idle
[    2.474767] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.474798] processor LNXCPU:00: registered as cooling_device0
[    2.474803] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.475234] ACPI: SSDT 000000007f6d4a3c 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    2.475652] ACPI: SSDT 000000007f6d477f 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    2.476841] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.476868] processor LNXCPU:01: registered as cooling_device1
[    2.476872] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.030080] thermal LNXTHERM:01: registered as thermal_zone0
[    3.030089] ACPI: Thermal Zone [THRM] (58 C)
[    3.031469] Linux agpgart interface v0.103
[    3.031483] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.032942] brd: module loaded
[    3.033449] loop: module loaded
[    3.033546] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    3.033715] ahci 0000:00:1f.2: version 3.0
[    3.033738]   alloc irq_desc for 19 on node 0
[    3.033740]   alloc kstat_irqs on node 0
[    3.033748] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.033796]   alloc irq_desc for 27 on node 0
[    3.033798]   alloc kstat_irqs on node 0
[    3.033810] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    3.033888] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    3.033892] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    3.033898] ahci 0000:00:1f.2: setting latency timer to 64
[    3.034291] ACPI: Battery Slot [BAT1] (battery absent)
[    3.034351] scsi0 : ahci
[    3.034475] scsi1 : ahci
[    3.034533] scsi2 : ahci
[    3.034659] ata1: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704100 irq 27
[    3.034664] ata2: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704180 irq 27
[    3.034668] ata3: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704200 irq 27
[    3.034802] ata_piix 0000:00:1f.1: version 2.13
[    3.034817] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.034867] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.034968] scsi3 : ata_piix
[    3.035047] scsi4 : ata_piix
[    3.035778] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.035781] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.036754] Fixed MDIO Bus: probed
[    3.036796] PPP generic driver version 2.4.2
[    3.036930] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.037130] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.037155] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.037160] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.037236] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.041147] ehci_hcd 0000:00:1a.7: debug port 1
[    3.041155] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.041176] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0704800
[    3.060021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.060105] usb usb1: configuration #1 chosen from 1 choice
[    3.060139] hub 1-0:1.0: USB hub found
[    3.060147] hub 1-0:1.0: 4 ports detected
[    3.060263]   alloc irq_desc for 23 on node 0
[    3.060265]   alloc kstat_irqs on node 0
[    3.060273] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.060287] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.060291] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.060331] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.064243] ehci_hcd 0000:00:1d.7: debug port 1
[    3.064251] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.064267] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0704c00
[    3.080015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.080083] usb usb2: configuration #1 chosen from 1 choice
[    3.080112] hub 2-0:1.0: USB hub found
[    3.080120] hub 2-0:1.0: 6 ports detected
[    3.080201] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.080228] uhci_hcd: USB Universal Host Controller Interface driver
[    3.080342] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.080351] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.080355] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.080399] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.080440] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    3.080532] usb usb3: configuration #1 chosen from 1 choice
[    3.080565] hub 3-0:1.0: USB hub found
[    3.080573] hub 3-0:1.0: 2 ports detected
[    3.080673]   alloc irq_desc for 21 on node 0
[    3.080675]   alloc kstat_irqs on node 0
[    3.080682] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.080690] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.080694] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.080745] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.080785] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    3.080879] usb usb4: configuration #1 chosen from 1 choice
[    3.080911] hub 4-0:1.0: USB hub found
[    3.080919] hub 4-0:1.0: 2 ports detected
[    3.081011] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.081019] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.081023] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.081073] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.081104] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    3.081196] usb usb5: configuration #1 chosen from 1 choice
[    3.081224] hub 5-0:1.0: USB hub found
[    3.081232] hub 5-0:1.0: 2 ports detected
[    3.081324] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.081333] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.081337] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.081376] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.081417] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    3.081510] usb usb6: configuration #1 chosen from 1 choice
[    3.081540] hub 6-0:1.0: USB hub found
[    3.081547] hub 6-0:1.0: 2 ports detected
[    3.081649] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.081658] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.081662] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.081698] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.081730] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    3.081824] usb usb7: configuration #1 chosen from 1 choice
[    3.081854] hub 7-0:1.0: USB hub found
[    3.081861] hub 7-0:1.0: 2 ports detected
[    3.081989] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.084258] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.085754] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.085760] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.085763] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.085767] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.085770] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.085851] mice: PS/2 mouse device common for all mice
[    3.086003] rtc_cmos 00:07: RTC can wake from S4
[    3.086043] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.086078] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.086203] device-mapper: uevent: version 1.0.3
[    3.086300] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    3.086372] device-mapper: multipath: version 1.1.0 loaded
[    3.086376] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.086633] cpuidle: using governor ladder
[    3.086766] cpuidle: using governor menu
[    3.087234] TCP cubic registered
[    3.087392] NET: Registered protocol family 10
[    3.087895] lo: Disabled Privacy Extensions
[    3.088227] NET: Registered protocol family 17
[    3.088251] Bluetooth: L2CAP ver 2.13
[    3.088253] Bluetooth: L2CAP socket layer initialized
[    3.088257] Bluetooth: SCO (Voice Link) ver 0.6
[    3.088260] Bluetooth: SCO socket layer initialized
[    3.088300] Bluetooth: RFCOMM TTY layer initialized
[    3.088307] Bluetooth: RFCOMM socket layer initialized
[    3.088309] Bluetooth: RFCOMM ver 1.11
[    3.089150] PM: Resume from disk failed.
[    3.089167] registered taskstats version 1
[    3.089320]   Magic number: 13:834:926
[    3.089448] rtc_cmos 00:07: setting system clock to 2009-10-29 07:56:32 UTC (1256802992)
[    3.089452] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.089454] EDD information not available.
[    3.115864] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.212388] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T40N, JP01, max UDMA/33
[    3.250331] ata4.00: configured for UDMA/33
[    3.380073] ata2: SATA link down (SStatus 0 SControl 300)
[    3.380099] ata3: SATA link down (SStatus 0 SControl 300)
[    3.380126] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.381128] ACPI Warning: \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer 20090521 nspredef-940
[    3.381137] ata1.00: _GTF unexpected object type 0x1
[    3.381309] ata1.00: ATA-8: Hitachi HTS542512K9SA00, BB2OC31P, max UDMA/133
[    3.381312] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.382495] ata1.00: _GTF unexpected object type 0x1
[    3.382681] ata1.00: configured for UDMA/133
[    3.400188] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BB2O PQ: 0 ANSI: 5
[    3.400338] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.400385] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    3.400436] sd 0:0:0:0: [sda] Write Protect is off
[    3.400439] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.400467] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.400612]  sda:
[    3.404279] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40N  JP01 PQ: 0 ANSI: 5
[    3.415553] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.415556] Uniform CD-ROM driver Revision: 3.20
[    3.415663] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.415715] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.500039] Clocksource tsc unstable (delta = -281755422 ns)
[    3.525924]  sda1 sda2 < sda5 >
[    3.571076] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.571116] Freeing unused kernel memory: 660k freed
[    3.571387] Write protecting the kernel read-only data: 7580k
[    3.699726] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    3.700179] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    3.703513] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    3.729822] [drm] Initialized drm 1.1.0 20060810
[    3.823912] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.823920] i915 0000:00:02.0: setting latency timer to 64
[    3.846595] ohci1394 0000:0a:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.847748] tg3.c:v3.99 (April 20, 2009)
[    3.847808] tg3 0000:05:00.0: enabling device (0000 -> 0002)
[    3.847818] tg3 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.847838] tg3 0000:05:00.0: setting latency timer to 64
[    3.848415]   alloc irq_desc for 28 on node 0
[    3.848419]   alloc kstat_irqs on node 0
[    3.848430] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    3.953286] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0400000-f04007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.957659] tg3 0000:05:00.0: wake-up capability disabled by ACPI
[    3.957673] tg3 0000:05:00.0: PME# disabled
[    4.110804] eth0: Tigon3 [partno(BCM95787m) rev b002] (PCI Express) MAC address 00:1e:68:3f:42:80
[    4.110809] eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    4.110813] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    4.110816] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.401930] [drm] TV-14: set mode NTSC 480i 0
[    4.528850] [drm] fb0: inteldrmfb frame buffer device
[    5.272960] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0066ecd300]
[    8.510179] acpi device:05: registered as cooling_device2
[   11.920161] acpi device:06: registered as cooling_device3
[   11.920371] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input6
[   11.920415] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.920458] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.989422] [drm] LVDS-8: set mode 1280x800 17
[   12.012991] Console: switching to colour frame buffer device 160x50
[   12.276902] PM: Starting manual resume from disk
[   12.276907] PM: Resume from partition 8:5
[   12.276909] PM: Checking hibernation image.
[   12.277084] PM: Resume from disk failed.
[   12.281497] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[   12.281502] EXT4-fs (sda1): write access will be enabled during recovery
[   12.410766] EXT4-fs (sda1): barriers enabled
[   16.173527] kjournald2 starting: pid 410, dev sda1:8, commit interval 5 seconds
[   16.173564] EXT4-fs (sda1): delayed allocation enabled
[   16.173569] EXT4-fs: file extents enabled
[   16.178100] EXT4-fs: mballoc enabled
[   16.178118] EXT4-fs (sda1): recovery complete
[   16.207397] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   19.116582] type=1505 audit(1256803008.520:2): operation="profile_load" pid=433 name=/usr/share/gdm/guest-session/Xsession
[   19.159966] type=1505 audit(1256803008.560:3): operation="profile_load" pid=434 name=/sbin/dhclient3
[   19.160832] type=1505 audit(1256803008.570:4): operation="profile_load" pid=434 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.161285] type=1505 audit(1256803008.570:5): operation="profile_load" pid=434 name=/usr/lib/connman/scripts/dhclient-script
[   19.211802] type=1505 audit(1256803008.620:6): operation="profile_load" pid=435 name=/usr/bin/evince
[   19.225077] type=1505 audit(1256803008.630:7): operation="profile_load" pid=435 name=/usr/bin/evince-previewer
[   19.232967] type=1505 audit(1256803008.640:8): operation="profile_load" pid=435 name=/usr/bin/evince-thumbnailer
[   19.307931] type=1505 audit(1256803008.710:9): operation="profile_load" pid=437 name=/usr/lib/cups/backend/cups-pdf
[   19.308923] type=1505 audit(1256803008.710:10): operation="profile_load" pid=437 name=/usr/sbin/cupsd
[   19.340024] type=1505 audit(1256803008.740:11): operation="profile_load" pid=438 name=/usr/sbin/dhcpd3
[   23.742278] Adding 4915848k swap on /dev/sda5.  Priority:-1 extents:1 across:4915848k 
[   24.433026] EXT4-fs (sda1): internal journal on sda1:8
[   26.270195] udev: starting version 147
[   29.918204] ricoh-mmc: Ricoh MMC Controller disabling driver
[   29.918208] ricoh-mmc: Copyright(c) Philip Langdale
[   29.918303] ricoh-mmc: Ricoh MMC controller found at 0000:0a:09.2 [1180:0843] (rev 12)
[   29.918325] ricoh-mmc: Controller is now disabled.
[   30.060107] cfg80211: Calling CRDA to update world regulatory domain
[   30.100308] lp: driver loaded but no devices found
[   30.449413] __ratelimit: 3 callbacks suppressed
[   30.449417] type=1505 audit(1256803019.850:13): operation="profile_replace" pid=788 name=/usr/share/gdm/guest-session/Xsession
[   30.451830] type=1505 audit(1256803019.860:14): operation="profile_replace" pid=789 name=/sbin/dhclient3
[   30.452704] type=1505 audit(1256803019.860:15): operation="profile_replace" pid=789 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   30.453160] type=1505 audit(1256803019.860:16): operation="profile_replace" pid=789 name=/usr/lib/connman/scripts/dhclient-script
[   30.457887] type=1505 audit(1256803019.860:17): operation="profile_replace" pid=790 name=/usr/bin/evince
[   30.470975] type=1505 audit(1256803019.880:18): operation="profile_replace" pid=790 name=/usr/bin/evince-previewer
[   30.478879] type=1505 audit(1256803019.880:19): operation="profile_replace" pid=790 name=/usr/bin/evince-thumbnailer
[   30.490326] type=1505 audit(1256803019.900:20): operation="profile_replace" pid=792 name=/usr/lib/cups/backend/cups-pdf
[   30.491315] type=1505 audit(1256803019.900:21): operation="profile_replace" pid=792 name=/usr/sbin/cupsd
[   30.494498] type=1505 audit(1256803019.900:22): operation="profile_replace" pid=793 name=/usr/sbin/dhcpd3
[   30.930948] input: PS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   31.040992] sdhci: Secure Digital Host Controller Interface driver
[   31.040996] sdhci: Copyright(c) Pierre Ossman
[   31.043012] sdhci-pci 0000:0a:09.1: SDHCI controller found [1180:0822] (rev 22)
[   31.043035] sdhci-pci 0000:0a:09.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   31.044079] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   31.045156] Registered led device: mmc0::
[   31.046202] mmc0: SDHCI controller on PCI [0000:0a:09.1] using DMA
[   31.240865] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.538733] acer-wmi: Acer Laptop ACPI-WMI Extras
[   32.539279] acer-wmi: Brightness must be controlled by generic video driver
[   33.787506] ath5k 0000:04:00.0: enabling device (0000 -> 0002)
[   33.787520] ath5k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   33.787537] ath5k 0000:04:00.0: setting latency timer to 64
[   33.787645] ath5k 0000:04:00.0: registered as 'phy0'
[   33.879492] ath: EEPROM regdomain: 0x65
[   33.879496] ath: EEPROM indicates we should expect a direct regpair map
[   33.879500] ath: Country alpha2 being used: 00
[   33.879502] ath: Regpair used: 0x65
[   34.355743]   alloc irq_desc for 22 on node 0
[   34.355747]   alloc kstat_irqs on node 0
[   34.355756] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   34.355811] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   34.358645] phy0: Selected rate control algorithm 'minstrel'
[   34.359432] Registered led device: ath5k-phy0::rx
[   34.359454] Registered led device: ath5k-phy0::tx
[   34.359458] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   34.621286] cfg80211: World regulatory domain updated:
[   34.621290] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   34.621294] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   34.621297] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   34.621300] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   34.621303] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   34.621306] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.554135] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   35.554240] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   48.760423] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.831557] tg3 0000:05:00.0: wake-up capability disabled by ACPI
[   48.831573] tg3 0000:05:00.0: PME# disabled
[   48.831809]   alloc irq_desc for 29 on node 0
[   48.831812]   alloc kstat_irqs on node 0
[   48.831844] tg3 0000:05:00.0: irq 29 for MSI/MSI-X
[   49.046031] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.201063] [drm] TV-14: set mode NTSC 480i 0
[   52.343757] [drm] TV-14: set mode NTSC 480i 0
[   52.741901] [drm] TV-14: set mode NTSC 480i 0
[   52.893471] [drm] TV-14: set mode NTSC 480i 0
[   67.463292] ppdev: user-space parallel port driver
[   67.734547] [drm] TV-14: set mode NTSC 480i 0
[   67.875970] [drm] TV-14: set mode NTSC 480i 0
[   68.169087] [drm] TV-14: set mode NTSC 480i 0
[   68.311347] [drm] TV-14: set mode NTSC 480i 0
[   68.704455] [drm] TV-14: set mode NTSC 480i 0
[   68.846411] [drm] TV-14: set mode NTSC 480i 0
[   95.119389] [drm] TV-14: set mode NTSC 480i 0
[   95.261180] [drm] TV-14: set mode NTSC 480i 0
[   95.557168] [drm] TV-14: set mode NTSC 480i 0
[   95.698595] [drm] TV-14: set mode NTSC 480i 0
[   95.994247] [drm] TV-14: set mode NTSC 480i 0
[   96.136298] [drm] TV-14: set mode NTSC 480i 0
[   99.614338] [drm] TV-14: set mode NTSC 480i 0
[   99.756189] [drm] TV-14: set mode NTSC 480i 0
[  109.818481] wlan0: authenticate with AP 00:1c:10:9d:1c:0c
[  109.819938] wlan0: authenticated
[  109.819944] wlan0: associate with AP 00:1c:10:9d:1c:0c
[  109.822227] wlan0: RX AssocResp from 00:1c:10:9d:1c:0c (capab=0x411 status=0 aid=4)
[  109.822231] wlan0: associated
[  109.823279] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  120.392555] wlan0: no IPv6 routers present
[ 1332.981483] [drm] TV-14: set mode NTSC 480i 0
[ 1333.125362] [drm] TV-14: set mode NTSC 480i 0
[ 1333.409630] [drm] TV-14: set mode NTSC 480i 0
[ 1333.551609] [drm] TV-14: set mode NTSC 480i 0
[ 1336.815953] [drm] TV-14: set mode NTSC 480i 0
[ 1336.957667] [drm] TV-14: set mode NTSC 480i 0
[ 1337.247879] [drm] TV-14: set mode NTSC 480i 0
[ 1337.390354] [drm] TV-14: set mode NTSC 480i 0
[ 1337.675705] [drm] TV-14: set mode NTSC 480i 0
[ 1337.817371] [drm] TV-14: set mode NTSC 480i 0
[ 1347.101333] [drm] TV-14: set mode NTSC 480i 0
[ 1347.243933] [drm] TV-14: set mode NTSC 480i 0
[ 1347.539253] [drm] TV-14: set mode NTSC 480i 0
[ 1347.681158] [drm] TV-14: set mode NTSC 480i 0
[ 1347.970194] [drm] TV-14: set mode NTSC 480i 0
[ 1348.113296] [drm] TV-14: set mode NTSC 480i 0
[ 1350.657179] [drm] TV-14: set mode NTSC 480i 0
[ 1350.798983] [drm] TV-14: set mode NTSC 480i 0
[ 2365.594112] CE: hpet increasing min_delta_ns to 15000 nsec
[ 2982.776430] __ratelimit: 3 callbacks suppressed
[ 2982.776436] npviewer.bin[4042]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ff914b9c error 14
[ 3293.657931] CE: hpet increasing min_delta_ns to 22500 nsec
[ 3937.774371] wlan0: disassociating by local choice (reason=3)
[ 3939.761352] [drm] TV-14: set mode NTSC 480i 0
[ 3939.903274] [drm] TV-14: set mode NTSC 480i 0
[ 3940.188213] [drm] TV-14: set mode NTSC 480i 0
[ 3940.329938] [drm] TV-14: set mode NTSC 480i 0
[ 3945.718174] [drm] TV-14: set mode NTSC 480i 0
[ 3945.859349] [drm] TV-14: set mode NTSC 480i 0
[ 3946.149934] [drm] TV-14: set mode NTSC 480i 0
[ 3946.291089] [drm] TV-14: set mode NTSC 480i 0
[ 3946.578167] [drm] TV-14: set mode NTSC 480i 0
[ 3946.719321] [drm] TV-14: set mode NTSC 480i 0
[ 3959.335576] [drm] TV-14: set mode NTSC 480i 0
[ 3959.499943] [drm] TV-14: set mode NTSC 480i 0
[ 3959.786903] [drm] TV-14: set mode NTSC 480i 0
[ 3959.929288] [drm] TV-14: set mode NTSC 480i 0
[ 3960.219319] [drm] TV-14: set mode NTSC 480i 0
[ 3960.360490] [drm] TV-14: set mode NTSC 480i 0
[ 3962.508566] [drm] TV-14: set mode NTSC 480i 0
[ 3962.650702] [drm] TV-14: set mode NTSC 480i 0
[ 4136.535758] wlan0: authenticate with AP 00:1c:10:9d:1c:0c
[ 4136.537222] wlan0: authenticated
[ 4136.537226] wlan0: associate with AP 00:1c:10:9d:1c:0c
[ 4136.539521] wlan0: RX AssocResp from 00:1c:10:9d:1c:0c (capab=0x411 status=0 aid=4)
[ 4136.539525] wlan0: associated
[ 7078.152787] npviewer.bin[8127]: segfault at 4 ip 00000000080515c2 sp 00000000ffc2b6e0 error 4 in npviewer.bin[8048000+23000]
[ 7122.879037] npviewer.bin[8271]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000fff254ac error 14
[ 8317.210161] wlan0: deauthenticating by local choice (reason=3)
[ 8317.710639] tg3 0000:05:00.0: PME# enabled
[ 8317.710729] tg3 0000:05:00.0: wake-up capability enabled by ACPI
[ 8317.737374] wlan0: disassociating by local choice (reason=3)
[ 8319.234938] PM: Syncing filesystems ... done.
[ 8319.249347] PM: Preparing system for mem sleep
[ 8319.249353] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 8319.250569] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 8319.250657] PM: Entering mem sleep
[ 8319.250674] Suspending console(s) (use no_console_suspend to debug)
[ 8319.320084] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 8319.320193] sd 0:0:0:0: [sda] Stopping disk
[ 8320.390796] ACPI handle has no context!
[ 8320.391877] ACPI handle has no context!
[ 8320.391884] sdhci-pci 0000:0a:09.1: PME# disabled
[ 8320.391892] sdhci-pci 0000:0a:09.1: PCI INT B disabled
[ 8320.391900] ACPI handle has no context!
[ 8320.415129] ACPI handle has no context!
[ 8320.430370] ath5k 0000:04:00.0: PCI INT A disabled
[ 8320.530150] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 8320.530162] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 8320.530172] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 8320.530180] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 8320.530188] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 8320.530223] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 8320.550067] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 8320.550075] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 8320.550084] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 8320.610138] PM: suspend devices took 1.360 seconds
[ 8320.610287] ricoh-mmc: Suspending.
[ 8320.610297] ricoh-mmc: Controller is now re-enabled.
[ 8320.610519] ehci_hcd 0000:00:1d.7: PME# disabled
[ 8320.630331] ehci_hcd 0000:00:1a.7: PME# disabled
[ 8320.650264] ACPI: Preparing to enter system sleep state S3
[ 8320.650521] Disabling non-boot CPUs ...
[ 8320.760020] CPU 1 is now offline
[ 8320.760023] SMP alternatives: switching to UP code
[ 8320.767452] CPU0 attaching NULL sched-domain.
[ 8320.767456] CPU1 attaching NULL sched-domain.
[ 8320.767468] CPU0 attaching NULL sched-domain.
[ 8320.767719] CPU1 is down
[ 8320.767771] Extended CMOS year: 2000
[ 8320.767771] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 8320.767771] Back to C!
[ 8320.767771] CPU0: Thermal monitoring handled by SMI
[ 8320.767771] Extended CMOS year: 2000
[ 8320.767771] Enabling non-boot CPUs ...
[ 8320.767771] SMP alternatives: switching to SMP code
[ 8320.775109] Booting processor 1 APIC 0x1 ip 0x6000
[ 8320.767294] Initializing CPU#1
[ 8320.767294] Calibrating delay using timer specific routine.. 3466.69 BogoMIPS (lpj=17333461)
[ 8320.767294] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 8320.767294] CPU: L2 cache: 1024K
[ 8320.767294] CPU 1/0x1 -> Node 0
[ 8320.767294] CPU: Physical Processor ID: 0
[ 8320.767294] CPU: Processor Core ID: 1
[ 8320.767294] mce: CPU supports 6 MCE banks
[ 8320.767294] CPU1: Thermal monitoring enabled (TM2)
[ 8320.767294] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[ 8320.931524] CPU1: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz stepping 0d
[ 8320.931592] CPU0 attaching NULL sched-domain.
[ 8320.932519] Switched to high resolution mode on CPU 1
[ 8320.970025] CPU0 attaching sched-domain:
[ 8320.970029]  domain 0: span 0-1 level MC
[ 8320.970032]   groups: 0 1
[ 8320.970037] CPU1 attaching sched-domain:
[ 8320.970039]  domain 0: span 0-1 level MC
[ 8320.970041]   groups: 1 0
[ 8320.972520] CPU1 is up
[ 8320.972523] ACPI: Waking up from system sleep state S3
[ 8321.870112] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 8321.870122] i915 0000:00:02.0: restoring config space at offset 0x8 (was 0x1, writing 0x1801)
[ 8321.870127] i915 0000:00:02.0: restoring config space at offset 0x6 (was 0xc, writing 0xd000000c)
[ 8321.870132] i915 0000:00:02.0: restoring config space at offset 0x4 (was 0x4, writing 0xf0000004)
[ 8321.870138] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900000, writing 0x900407)
[ 8321.870169] pci 0000:00:02.1: restoring config space at offset 0x4 (was 0x4, writing 0xf0100004)
[ 8321.870175] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[ 8321.870210] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 8321.870246] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 8321.870292] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 8321.870313] ehci_hcd 0000:00:1a.7: PME# disabled
[ 8321.870354] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 8321.870362] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 8321.870399] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
[ 8321.870413] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 8321.870419] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[ 8321.870425] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
[ 8321.870436] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 8321.870444] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100404)
[ 8321.870499] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x40200, writing 0x40205)
[ 8321.870513] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 8321.870519] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0x80008000)
[ 8321.870525] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
[ 8321.870536] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 8321.870544] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100406)
[ 8321.870598] pcieport-driver 0000:00:1c.2: restoring config space at offset 0xf (was 0x40300, writing 0x4030a)
[ 8321.870612] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 8321.870619] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x8 (was 0x0, writing 0x80108010)
[ 8321.870625] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
[ 8321.870636] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 8321.870643] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100406)
[ 8321.870708] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 8321.870744] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 8321.870779] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 8321.870824] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 8321.870844] ehci_hcd 0000:00:1d.7: PME# disabled
[ 8321.870866] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 8321.870872] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xf040f040)
[ 8321.870877] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
[ 8321.870891] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100004, writing 0x100007)
[ 8321.870960] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[ 8321.870987] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2880005)
[ 8321.871012] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 8321.871039] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 8321.871096] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0x80200000)
[ 8321.871138] ath5k 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 8321.871168] ath5k 0000:04:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x80000004)
[ 8321.871175] ath5k 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 8321.871184] ath5k 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 8321.871346] tg3 0000:05:00.0: restoring config space at offset 0xc (was 0x0, writing 0x42cc0000)
[ 8321.871394] tg3 0000:05:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x80100004)
[ 8321.871406] tg3 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 8321.871424] tg3 0000:05:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 8321.871527] ohci1394 0000:0a:09.0: restoring config space at offset 0x4 (was 0x0, writing 0xf0400000)
[ 8321.871534] ohci1394 0000:0a:09.0: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[ 8321.871542] ohci1394 0000:0a:09.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 8321.871585] sdhci-pci 0000:0a:09.1: restoring config space at offset 0x4 (was 0x0, writing 0xf0400800)
[ 8321.871591] sdhci-pci 0000:0a:09.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[ 8321.871599] sdhci-pci 0000:0a:09.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 8321.871643] ricoh-mmc 0000:0a:09.2: restoring config space at offset 0x4 (was 0x0, writing 0xf0400c00)
[ 8321.871649] ricoh-mmc 0000:0a:09.2: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[ 8321.871657] ricoh-mmc 0000:0a:09.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 8321.871670] ricoh-mmc: Resuming.
[ 8321.871681] ricoh-mmc: Controller is now disabled.
[ 8321.871714] pci 0000:0a:09.3: restoring config space at offset 0x4 (was 0x0, writing 0xf0401400)
[ 8321.871720] pci 0000:0a:09.3: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[ 8321.871728] pci 0000:0a:09.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 8322.390060] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 8324.153345] i915 0000:00:02.0: setting latency timer to 64
[ 8324.214936] [drm] LVDS-8: set mode 1280x800 17
[ 8324.235220] pci 0000:00:02.1: PME# disabled
[ 8324.235234] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 8324.235241] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 8324.235270] usb usb3: root hub lost power or was reset
[ 8324.235293] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 8324.235300] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 8324.235328] usb usb4: root hub lost power or was reset
[ 8324.235351] ehci_hcd 0000:00:1a.7: PME# disabled
[ 8324.235356] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 8324.235363] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 8324.235375] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 8324.235382] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 8324.235416] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 8324.235423] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 8324.235449] usb usb5: root hub lost power or was reset
[ 8324.235471] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 8324.235478] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 8324.235505] usb usb6: root hub lost power or was reset
[ 8324.235526] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 8324.235533] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 8324.235561] usb usb7: root hub lost power or was reset
[ 8324.235584] ehci_hcd 0000:00:1d.7: PME# disabled
[ 8324.235589] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 8324.235596] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 8324.235609] pci 0000:00:1e.0: setting latency timer to 64
[ 8324.235620] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 8324.235626] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 8324.235767] ahci 0000:00:1f.2: setting latency timer to 64
[ 8324.235815] ath5k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 8324.292084] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0400000-f04007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 8324.298175] sdhci-pci 0000:0a:09.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 8324.298179] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[ 8324.299201] pci 0000:0a:09.3: PME# disabled
[ 8324.299208] pci 0000:0a:09.4: PME# disabled
[ 8324.384458] sd 0:0:0:0: [sda] Starting disk
[ 8324.420450] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 8324.420454] ata4.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[ 8324.460345] ata4.00: configured for UDMA/33
[ 8324.580074] ata2: SATA link down (SStatus 0 SControl 300)
[ 8324.580102] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 8324.580126] ata3: SATA link down (SStatus 0 SControl 300)
[ 8324.581095] ata1.00: _GTF unexpected object type 0x1
[ 8324.773608] ata1.00: _GTF unexpected object type 0x1
[ 8324.773839] ata1.00: configured for UDMA/133
[ 8324.774112] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[ 8324.774114] ata1: irq_stat 0x00400040, connection status changed
[ 8324.774120] ata1: hard resetting link
[ 8325.520068] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 8325.521038] ata1.00: _GTF unexpected object type 0x1
[ 8325.522375] ata1.00: _GTF unexpected object type 0x1
[ 8325.522563] ata1.00: configured for UDMA/133
[ 8325.522566] ata1: EH complete
[ 8325.617134] PM: resume devices took 3.720 seconds
[ 8325.617173] PM: Finishing wakeup.
[ 8325.617176] Restarting tasks ... done.
[ 8329.056700] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8329.057957] tg3 0000:05:00.0: wake-up capability disabled by ACPI
[ 8329.057973] tg3 0000:05:00.0: PME# disabled
[ 8329.058253] tg3 0000:05:00.0: irq 29 for MSI/MSI-X
[ 8329.271313] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 8340.817030] wlan0: authenticate with AP 00:1c:10:9d:1c:0c
[ 8340.818654] wlan0: authenticated
[ 8340.818659] wlan0: associate with AP 00:1c:10:9d:1c:0c
[ 8340.821048] wlan0: RX AssocResp from 00:1c:10:9d:1c:0c (capab=0x411 status=0 aid=3)
[ 8340.821054] wlan0: associated
[ 8340.822063] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8351.130069] wlan0: no IPv6 routers present
```

---

