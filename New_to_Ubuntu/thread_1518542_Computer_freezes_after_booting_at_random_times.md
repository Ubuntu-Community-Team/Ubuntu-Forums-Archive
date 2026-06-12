---
title: "Computer freezes after booting at random times"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by agm. on 2010-06-26
Hello,

Running Jaunty 9.04.

Right before I went away for 3 weeks, I updated my computer and after an update, the computer boots, but will randomly freeze after a bit of time.  It can be doing nothing and just freeze or I can be suring the web, it does not matter and varies in the time from boot until the freeze.  When I got back today, it still does the same thing and I tried to run the update manager and see if that would fix the problem, but it froze mid-update.  Now when I try to update, it gives me an error about medibuntu repository.

How do I check the logs to see what is causing the problem?

Additionally, I tried to log into 2 different 10.04 cd that I burned and I get error messages there or it hangs at the "Ubuntu" load screen.  Is there a way to save those messages as well?

I'm trying to figure out if this is a hardware or OS problem and any help in trying to track down these problems is much appreciated!

Thanks!

---

### Post by nhasian on 2010-06-26
what error messages are you receiving?  do you know what your cpu/gpu temperatures are to see if its overheating or not?

---

### Post by agm. on 2010-06-26
That is part of my question:

What logs should I be checking when I go into system log viewer?

When I boot, right now it basically gives about 2-3 minutes (sometimes a few longer) before it locks.  So I'm trying to figure out what I need to copy/paste onto a thumb-drive so that I can put it up here so people with better knowledge can help me.

Thanks for your reply!

---

### Post by agm. on 2010-06-27
So I tried to load from CD again today using 10.04 and it hangs the system.  The attached photo shows the error messages when the system does not just hang on the Ubuntu logo with dots...

I went into the BIOS and the system says that it has a CPU temp of 41 C, with an system temp of 45... I couldn't figure out how to determine the temperature while running the OS.  

When the system froze today, it was roughly 16:24 and I looked through the entire log viewer after reboot and nothing seemed to really show anything happening at 16:24.  I turned off the computer and then copy-pasted the entire kernlog (though I am not sure that this is the one that matters)... 

Any help would on what is happening would be greatly, greatly appreciated!!!

The line that I think is most concerning (but I don't know much about this sort of thing) is the line:

> 
Jun 27 16:36:57 tony-desktop kernel: [   86.036018] Clocksource tsc unstable (delta = -91342407 ns)


But here is the log from basically right before the freeze until about 10 seconds before the next freeze (with about 10 minutes of time turned off between boot-ups).

```

Jun 27 16:18:45 tony-desktop kernel: [  486.013191] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 289
Jun 27 16:20:45 tony-desktop kernel: [  606.012073] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 289
Jun 27 16:22:45 tony-desktop kernel: [  726.013361] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 289
Jun 27 16:37:20 tony-desktop syslogd 1.5.0#5ubuntu3: restart.
Jun 27 16:37:20 tony-desktop kernel: Inspecting /boot/System.map-2.6.28-19-generic
Jun 27 16:37:20 tony-desktop kernel: Cannot find map file.
Jun 27 16:37:20 tony-desktop kernel: Loaded 74765 symbols from 48 modules.
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Linux version 2.6.28-19-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #61-Ubuntu SMP Wed May 26 23:35:15 UTC 2010 (Ubuntu 2.6.28-19.61-generic)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] KERNEL supported cpus:
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   Intel GenuineIntel
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   NSC Geode by NSC
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  BIOS-e820: 00000000a0000000 - 00000000b0000000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] DMI 2.2 present.
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] modified physical RAM map:
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000003fff0000 (usable)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  modified: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  modified: 000000003fff3000 - 0000000040000000 (ACPI data)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  modified: 00000000a0000000 - 00000000b0000000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] RAMDISK: 378bc000 - 37fef63a
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Allocated new RAMDISK: 0087d000 - 00fb063a
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Move RAMDISK from 00000000378bc000 - 0000000037fef639 to 0087d000 - 00fb0639
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: RSDP 000F7B80, 0014 (r0 XPC   )
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: RSDT 3FFF3040, 0034 (r1 XPC    AWRDACPI 42302E31 AWRD        0)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: FACP 3FFF30C0, 0074 (r1 XPC    AWRDACPI 42302E31 AWRD        0)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: DSDT 3FFF3180, 497D (r1 XPC     SN25V10     1000 MSFT  100000E)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: FACS 3FFF0000, 0040
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: SSDT 3FFF7C00, 01CA (r1 PTLTD  POWERNOW        1  LTP        1)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: MCFG 3FFF7E40, 003C (r1 XPC    AWRDACPI 42302E31 AWRD        0)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: APIC 3FFF7B40, 0072 (r1 XPC    AWRDACPI 42302E31 AWRD        0)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] 139MB HIGHMEM available.
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] 883MB LOWMEM available.
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   mapped low ram: 0 - 373fe000
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   low ram: 00000000 - 373fe000
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   bootmap 00012000 - 00018e80
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   #7 [000087d000 - 0000fb063a]      NEW RAMDISK ==> [000087d000 - 0000fb063a]
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] found SMP MP-table at [c00f3920] 000f3920
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Zone PFN ranges:
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]   HighMem  0x000373fe -> 0x0003fff0
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jun 27 16:37:20 tony-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0003fff0
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Allocating PCI resources starting at 48000000 (gap: 40000000:60000000)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259967
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Kernel command line: root=UUID=d8aee13a-9612-4f52-b0e0-532be520d594 ro quiet splash 
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Initializing CPU#0
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jun 27 16:37:20 tony-desktop kernel: [    0.000000] Detected 2210.195 MHz processor.
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] console [tty0] enabled
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] allocated 5242240 bytes of page_cgroup
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] Memory: 1018392k/1048512k available (4116k kernel code, 29284k reserved, 2199k data, 532k init, 143304k highmem)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] virtual kernel memory layout:
Jun 27 16:37:20 tony-desktop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000]       .data : 0xc0505131 - 0xc072ae60   (2199 kB)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000]       .text : 0xc0100000 - 0xc0505131   (4116 kB)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jun 27 16:37:20 tony-desktop kernel: [    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4420.39 BogoMIPS (lpj=8840780)
Jun 27 16:37:20 tony-desktop kernel: [    0.004025] Security Framework initialized
Jun 27 16:37:20 tony-desktop kernel: [    0.004031] SELinux:  Disabled at boot.
Jun 27 16:37:20 tony-desktop kernel: [    0.004053] AppArmor: AppArmor initialized
Jun 27 16:37:20 tony-desktop kernel: [    0.004060] Mount-cache hash table entries: 512
Jun 27 16:37:20 tony-desktop kernel: [    0.004185] Initializing cgroup subsys ns
Jun 27 16:37:20 tony-desktop kernel: [    0.004188] Initializing cgroup subsys cpuacct
Jun 27 16:37:20 tony-desktop kernel: [    0.004190] Initializing cgroup subsys memory
Jun 27 16:37:20 tony-desktop kernel: [    0.004194] Initializing cgroup subsys freezer
Jun 27 16:37:20 tony-desktop kernel: [    0.004205] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 27 16:37:20 tony-desktop kernel: [    0.004207] CPU: L2 Cache: 1024K (64 bytes/line)
Jun 27 16:37:20 tony-desktop kernel: [    0.004209] CPU: Physical Processor ID: 0
Jun 27 16:37:20 tony-desktop kernel: [    0.004210] CPU: Processor Core ID: 0
Jun 27 16:37:20 tony-desktop kernel: [    0.004222] Checking 'hlt' instruction... OK.
Jun 27 16:37:20 tony-desktop kernel: [    0.021845] ACPI: Core revision 20080926
Jun 27 16:37:20 tony-desktop kernel: [    0.023308] ACPI: Checking initramfs for custom DSDT
Jun 27 16:37:20 tony-desktop kernel: [    0.280395] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Jun 27 16:37:20 tony-desktop kernel: [    0.321124] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 02
Jun 27 16:37:20 tony-desktop kernel: [    0.324001] Booting processor 1 APIC 0x1 ip 0x6000
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] Initializing CPU#1
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 4420.66 BogoMIPS (lpj=8841325)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Jun 27 16:37:20 tony-desktop kernel: [    0.004000] CPU: Processor Core ID: 1
Jun 27 16:37:20 tony-desktop kernel: [    0.408202] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 02
Jun 27 16:37:20 tony-desktop kernel: [    0.408251] Brought up 2 CPUs
Jun 27 16:37:20 tony-desktop kernel: [    0.408253] Total of 2 processors activated (8841.05 BogoMIPS).
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] net_namespace: 776 bytes
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] Booting paravirtualized kernel on bare hardware
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] Time: 16:37:00  Date: 06/27/10
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] regulator: core version 0.5
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] NET: Registered protocol family 16
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] EISA bus registered
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] ACPI: bus type pci registered
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] PCI: MCFG area at e0000000 reserved in E820
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] PCI: Using MMCONFIG for extended config space
Jun 27 16:37:20 tony-desktop kernel: [    0.408374] PCI: Using configuration type 1 for base access
Jun 27 16:37:20 tony-desktop kernel: [    0.417397] ACPI: Interpreter enabled
Jun 27 16:37:20 tony-desktop kernel: [    0.417400] ACPI: (supports S0 S1 S4 S5)
Jun 27 16:37:20 tony-desktop kernel: [    0.417418] ACPI: Using IOAPIC for interrupt routing
Jun 27 16:37:20 tony-desktop kernel: [    0.424306] ACPI: No dock devices found.
Jun 27 16:37:20 tony-desktop kernel: [    0.424317] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 27 16:37:20 tony-desktop kernel: [    0.424399] HPET not enabled in BIOS. You might try hpet=force boot option
Jun 27 16:37:20 tony-desktop kernel: [    0.424430] pci 0000:00:01.1: PME# supported from D3hot D3cold
Jun 27 16:37:20 tony-desktop kernel: [    0.424433] pci 0000:00:01.1: PME# disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.424465] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 27 16:37:20 tony-desktop kernel: [    0.424468] pci 0000:00:02.0: PME# disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.424500] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Jun 27 16:37:20 tony-desktop kernel: [    0.424503] pci 0000:00:02.1: PME# disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.424640] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 27 16:37:20 tony-desktop kernel: [    0.424643] pci 0000:00:0a.0: PME# disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.424662] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 27 16:37:20 tony-desktop kernel: [    0.424664] pci 0000:00:0b.0: PME# disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.424684] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 27 16:37:20 tony-desktop kernel: [    0.424687] pci 0000:00:0c.0: PME# disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.424706] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 27 16:37:20 tony-desktop kernel: [    0.424708] pci 0000:00:0d.0: PME# disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.424728] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 27 16:37:20 tony-desktop kernel: [    0.424730] pci 0000:00:0e.0: PME# disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.424885] pci 0000:05:07.0: PME# supported from D2 D3hot D3cold
Jun 27 16:37:20 tony-desktop kernel: [    0.424888] pci 0000:05:07.0: PME# disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.424909] pci 0000:00:09.0: transparent bridge
Jun 27 16:37:20 tony-desktop kernel: [    0.478937] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.479087] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.479237] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 10 11 *12 14 15)
Jun 27 16:37:20 tony-desktop kernel: [    0.479387] ACPI: PCI Interrupt Link [LNK4] (IRQs *3 4 5 7 9 10 11 12 14 15)
Jun 27 16:37:20 tony-desktop kernel: [    0.479535] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.479686] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jun 27 16:37:20 tony-desktop kernel: [    0.479834] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.479984] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Jun 27 16:37:20 tony-desktop kernel: [    0.480141] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.480291] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.480441] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 11 *12 14 15)
Jun 27 16:37:20 tony-desktop kernel: [    0.480591] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jun 27 16:37:20 tony-desktop kernel: [    0.480740] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.480901] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jun 27 16:37:20 tony-desktop kernel: [    0.481059] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jun 27 16:37:20 tony-desktop kernel: [    0.481216] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.481384] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.481548] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.481718] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Jun 27 16:37:20 tony-desktop kernel: [    0.481880] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
Jun 27 16:37:20 tony-desktop kernel: [    0.481986] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.482155] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Jun 27 16:37:20 tony-desktop kernel: [    0.482324] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.482494] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Jun 27 16:37:20 tony-desktop kernel: [    0.482663] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.482832] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.483002] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Jun 27 16:37:20 tony-desktop kernel: [    0.483171] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Jun 27 16:37:20 tony-desktop kernel: [    0.483340] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.483517] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Jun 27 16:37:20 tony-desktop kernel: [    0.483694] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Jun 27 16:37:20 tony-desktop kernel: [    0.483870] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
Jun 27 16:37:20 tony-desktop kernel: [    0.483984] ACPI: WMI: Mapper loaded
Jun 27 16:37:20 tony-desktop kernel: [    0.484102] SCSI subsystem initialized
Jun 27 16:37:20 tony-desktop kernel: [    0.484115] usbcore: registered new interface driver usbfs
Jun 27 16:37:20 tony-desktop kernel: [    0.484115] usbcore: registered new interface driver hub
Jun 27 16:37:20 tony-desktop kernel: [    0.484115] usbcore: registered new device driver usb
Jun 27 16:37:20 tony-desktop kernel: [    0.484115] PCI: Using ACPI for IRQ routing
Jun 27 16:37:20 tony-desktop kernel: [    0.492008] Bluetooth: Core ver 2.13
Jun 27 16:37:20 tony-desktop kernel: [    0.492022] NET: Registered protocol family 31
Jun 27 16:37:20 tony-desktop kernel: [    0.492022] Bluetooth: HCI device and connection manager initialized
Jun 27 16:37:20 tony-desktop kernel: [    0.492022] Bluetooth: HCI socket layer initialized
Jun 27 16:37:20 tony-desktop kernel: [    0.492022] NET: Registered protocol family 8
Jun 27 16:37:20 tony-desktop kernel: [    0.492022] NET: Registered protocol family 20
Jun 27 16:37:20 tony-desktop kernel: [    0.492030] NetLabel: Initializing
Jun 27 16:37:20 tony-desktop kernel: [    0.492031] NetLabel:  domain hash size = 128
Jun 27 16:37:20 tony-desktop kernel: [    0.492033] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 27 16:37:20 tony-desktop kernel: [    0.492045] NetLabel:  unlabeled traffic allowed by default
Jun 27 16:37:20 tony-desktop kernel: [    0.492111] AppArmor: AppArmor Filesystem Enabled
Jun 27 16:37:20 tony-desktop kernel: [    0.496007] pnp: PnP ACPI init
Jun 27 16:37:20 tony-desktop kernel: [    0.496014] ACPI: bus type pnp registered
Jun 27 16:37:20 tony-desktop kernel: [    0.500199] pnp: PnP ACPI: found 12 devices
Jun 27 16:37:20 tony-desktop kernel: [    0.500201] ACPI: ACPI bus type pnp unregistered
Jun 27 16:37:20 tony-desktop kernel: [    0.500204] PnPBIOS: Disabled by ACPI PNP
Jun 27 16:37:20 tony-desktop kernel: [    0.500211] system 00:01: ioport range 0x1000-0x107f has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500213] system 00:01: ioport range 0x1080-0x10ff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500216] system 00:01: ioport range 0x1400-0x147f has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500218] system 00:01: ioport range 0x1480-0x14ff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500220] system 00:01: ioport range 0x1800-0x187f has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500223] system 00:01: ioport range 0x1880-0x18ff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500226] system 00:01: iomem range 0xa0000000-0xafffffff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500231] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500234] system 00:02: ioport range 0x800-0x805 has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500236] system 00:02: ioport range 0x290-0x30f has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500239] system 00:02: ioport range 0x290-0x297 has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500245] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500250] system 00:0b: iomem range 0xd0000-0xd3fff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500253] system 00:0b: iomem range 0xd5800-0xd7fff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500255] system 00:0b: iomem range 0xf0000-0xfbfff could not be reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500258] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500260] system 00:0b: iomem range 0x3fff0000-0x3fffffff could not be reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500263] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500265] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500268] system 00:0b: iomem range 0x100000-0x3ffeffff could not be reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500270] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500273] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500275] system 00:0b: iomem range 0xfefff000-0xfeffffff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500278] system 00:0b: iomem range 0xfff80000-0xfff80fff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500280] system 00:0b: iomem range 0xfff90000-0xfffbffff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.500283] system 00:0b: iomem range 0xfffed000-0xfffeffff has been reserved
Jun 27 16:37:20 tony-desktop kernel: [    0.534962] pci 0000:00:09.0: PCI bridge, secondary bus 0000:05
Jun 27 16:37:20 tony-desktop kernel: [    0.534965] pci 0000:00:09.0:   IO window: 0xa000-0xafff
Jun 27 16:37:20 tony-desktop kernel: [    0.534968] pci 0000:00:09.0:   MEM window: 0xd0000000-0xd00fffff
Jun 27 16:37:20 tony-desktop kernel: [    0.534970] pci 0000:00:09.0:   PREFETCH window: disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.534974] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:04
Jun 27 16:37:20 tony-desktop kernel: [    0.534975] pci 0000:00:0b.0:   IO window: disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.534978] pci 0000:00:0b.0:   MEM window: disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.534980] pci 0000:00:0b.0:   PREFETCH window: disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.534983] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
Jun 27 16:37:20 tony-desktop kernel: [    0.534984] pci 0000:00:0c.0:   IO window: disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.534987] pci 0000:00:0c.0:   MEM window: disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.534989] pci 0000:00:0c.0:   PREFETCH window: disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.534992] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:02
Jun 27 16:37:20 tony-desktop kernel: [    0.534994] pci 0000:00:0d.0:   IO window: disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.534996] pci 0000:00:0d.0:   MEM window: disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.534998] pci 0000:00:0d.0:   PREFETCH window: disabled
Jun 27 16:37:20 tony-desktop kernel: [    0.535002] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:01
Jun 27 16:37:20 tony-desktop kernel: [    0.535004] pci 0000:00:0e.0:   IO window: 0x9000-0x9fff
Jun 27 16:37:20 tony-desktop kernel: [    0.535007] pci 0000:00:0e.0:   MEM window: 0xb0000000-0xcfffffff
Jun 27 16:37:20 tony-desktop kernel: [    0.535010] pci 0000:00:0e.0:   PREFETCH window: 0x00000048000000-0x000000480fffff
Jun 27 16:37:20 tony-desktop kernel: [    0.535036] bus: 00 index 0 io port: [0x00-0xffff]
Jun 27 16:37:20 tony-desktop kernel: [    0.535038] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Jun 27 16:37:20 tony-desktop kernel: [    0.535040] bus: 05 index 0 io port: [0xa000-0xafff]
Jun 27 16:37:20 tony-desktop kernel: [    0.535041] bus: 05 index 1 mmio: [0xd0000000-0xd00fffff]
Jun 27 16:37:20 tony-desktop kernel: [    0.535043] bus: 05 index 2 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535045] bus: 05 index 3 io port: [0x00-0xffff]
Jun 27 16:37:20 tony-desktop kernel: [    0.535047] bus: 05 index 4 mmio: [0x000000-0xffffffff]
Jun 27 16:37:20 tony-desktop kernel: [    0.535049] bus: 04 index 0 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535050] bus: 04 index 1 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535052] bus: 04 index 2 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535053] bus: 04 index 3 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535055] bus: 03 index 0 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535056] bus: 03 index 1 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535058] bus: 03 index 2 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535060] bus: 03 index 3 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535061] bus: 02 index 0 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535063] bus: 02 index 1 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535064] bus: 02 index 2 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535066] bus: 02 index 3 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535068] bus: 01 index 0 io port: [0x9000-0x9fff]
Jun 27 16:37:20 tony-desktop kernel: [    0.535070] bus: 01 index 1 mmio: [0xb0000000-0xcfffffff]
Jun 27 16:37:20 tony-desktop kernel: [    0.535072] bus: 01 index 2 mmio: [0x48000000-0x480fffff]
Jun 27 16:37:20 tony-desktop kernel: [    0.535073] bus: 01 index 3 mmio: [0x0-0x0]
Jun 27 16:37:20 tony-desktop kernel: [    0.535081] NET: Registered protocol family 2
Jun 27 16:37:20 tony-desktop kernel: [    0.548060] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 27 16:37:20 tony-desktop kernel: [    0.548335] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 27 16:37:20 tony-desktop kernel: [    0.548994] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 27 16:37:20 tony-desktop kernel: [    0.549323] TCP: Hash tables configured (established 131072 bind 65536)
Jun 27 16:37:20 tony-desktop kernel: [    0.549326] TCP reno registered
Jun 27 16:37:20 tony-desktop kernel: [    0.556089] NET: Registered protocol family 1
Jun 27 16:37:20 tony-desktop kernel: [    0.556206] checking if image is initramfs... it is
Jun 27 16:37:20 tony-desktop kernel: [    1.081601] Freeing initrd memory: 7373k freed
Jun 27 16:37:20 tony-desktop kernel: [    1.081811] cpufreq: No nForce2 chipset.
Jun 27 16:37:20 tony-desktop kernel: [    1.081927] audit: initializing netlink socket (disabled)
Jun 27 16:37:20 tony-desktop kernel: [    1.081945] type=2000 audit(1277656621.080:1): initialized
Jun 27 16:37:20 tony-desktop kernel: [    1.089168] highmem bounce pool size: 64 pages
Jun 27 16:37:20 tony-desktop kernel: [    1.089173] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jun 27 16:37:20 tony-desktop kernel: [    1.090632] VFS: Disk quotas dquot_6.5.1
Jun 27 16:37:20 tony-desktop kernel: [    1.090681] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 27 16:37:20 tony-desktop kernel: [    1.091231] fuse init (API version 7.10)
Jun 27 16:37:20 tony-desktop kernel: [    1.091316] msgmni has been set to 1724
Jun 27 16:37:20 tony-desktop kernel: [    1.091531] alg: No test for stdrng (krng)
Jun 27 16:37:20 tony-desktop kernel: [    1.091546] io scheduler noop registered
Jun 27 16:37:20 tony-desktop kernel: [    1.091548] io scheduler anticipatory registered
Jun 27 16:37:20 tony-desktop kernel: [    1.091549] io scheduler deadline registered
Jun 27 16:37:20 tony-desktop kernel: [    1.091569] io scheduler cfq registered (default)
Jun 27 16:37:20 tony-desktop kernel: [    1.091587] pci 0000:00:00.0: Enabling HT MSI Mapping
Jun 27 16:37:20 tony-desktop kernel: [    9.104020] pci 0000:00:02.1: EHCI: BIOS handoff failed (BIOS bug?) 01010001
Jun 27 16:37:20 tony-desktop kernel: [    9.104058] pci 0000:00:0b.0: Enabling HT MSI Mapping
Jun 27 16:37:20 tony-desktop kernel: [    9.104065] pci 0000:00:0b.0: Found enabled HT MSI Mapping
Jun 27 16:37:20 tony-desktop kernel: [    9.104069] pci 0000:00:0b.0: Linking AER extended capability
Jun 27 16:37:20 tony-desktop kernel: [    9.104078] pci 0000:00:0c.0: Enabling HT MSI Mapping
Jun 27 16:37:20 tony-desktop kernel: [    9.104084] pci 0000:00:0c.0: Found enabled HT MSI Mapping
Jun 27 16:37:20 tony-desktop kernel: [    9.104087] pci 0000:00:0c.0: Linking AER extended capability
Jun 27 16:37:20 tony-desktop kernel: [    9.104095] pci 0000:00:0d.0: Enabling HT MSI Mapping
Jun 27 16:37:20 tony-desktop kernel: [    9.104101] pci 0000:00:0d.0: Found enabled HT MSI Mapping
Jun 27 16:37:20 tony-desktop kernel: [    9.104104] pci 0000:00:0d.0: Linking AER extended capability
Jun 27 16:37:20 tony-desktop kernel: [    9.104112] pci 0000:00:0e.0: Enabling HT MSI Mapping
Jun 27 16:37:20 tony-desktop kernel: [    9.104118] pci 0000:00:0e.0: Found enabled HT MSI Mapping
Jun 27 16:37:20 tony-desktop kernel: [    9.104121] pci 0000:00:0e.0: Linking AER extended capability
Jun 27 16:37:20 tony-desktop kernel: [    9.109550] pcieport-driver 0000:00:0b.0: found MSI capability
Jun 27 16:37:20 tony-desktop kernel: [    9.109629] pcieport-driver 0000:00:0c.0: found MSI capability
Jun 27 16:37:20 tony-desktop kernel: [    9.109702] pcieport-driver 0000:00:0d.0: found MSI capability
Jun 27 16:37:20 tony-desktop kernel: [    9.109775] pcieport-driver 0000:00:0e.0: found MSI capability
Jun 27 16:37:20 tony-desktop kernel: [    9.109843] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 27 16:37:20 tony-desktop kernel: [    9.109851] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 27 16:37:20 tony-desktop kernel: [    9.109974] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Jun 27 16:37:20 tony-desktop kernel: [    9.109976] ACPI: Power Button (FF) [PWRF]
Jun 27 16:37:20 tony-desktop kernel: [    9.110014] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Jun 27 16:37:20 tony-desktop kernel: [    9.110017] ACPI: Power Button (CM) [PWRB]
Jun 27 16:37:20 tony-desktop kernel: [    9.110064] fan PNP0C0B:00: registered as cooling_device0
Jun 27 16:37:20 tony-desktop kernel: [    9.110069] ACPI: Fan [FAN] (on)
Jun 27 16:37:20 tony-desktop kernel: [    9.110503] processor ACPI_CPU:00: registered as cooling_device1
Jun 27 16:37:20 tony-desktop kernel: [    9.110530] processor ACPI_CPU:01: registered as cooling_device2
Jun 27 16:37:20 tony-desktop kernel: [    9.114249] thermal LNXTHERM:01: registered as thermal_zone0
Jun 27 16:37:20 tony-desktop kernel: [    9.114552] ACPI: Thermal Zone [THRM] (40 C)
Jun 27 16:37:20 tony-desktop kernel: [    9.114593] isapnp: Scanning for PnP cards...
Jun 27 16:37:20 tony-desktop kernel: [    9.467066] isapnp: No Plug & Play device found
Jun 27 16:37:20 tony-desktop kernel: [    9.473122] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jun 27 16:37:20 tony-desktop kernel: [    9.473200] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 27 16:37:20 tony-desktop kernel: [    9.473463] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 27 16:37:20 tony-desktop kernel: [    9.474100] brd: module loaded
Jun 27 16:37:20 tony-desktop kernel: [    9.474376] loop: module loaded
Jun 27 16:37:20 tony-desktop kernel: [    9.474430] Fixed MDIO Bus: probed
Jun 27 16:37:20 tony-desktop kernel: [    9.474435] PPP generic driver version 2.4.2
Jun 27 16:37:20 tony-desktop kernel: [    9.474483] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jun 27 16:37:20 tony-desktop kernel: [    9.474506] Driver 'sd' needs updating - please use bus_type methods
Jun 27 16:37:20 tony-desktop kernel: [    9.474517] Driver 'sr' needs updating - please use bus_type methods
Jun 27 16:37:20 tony-desktop kernel: [    9.475003] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Jun 27 16:37:20 tony-desktop kernel: [    9.475011] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Jun 27 16:37:20 tony-desktop kernel: [    9.475112] scsi0 : sata_nv
Jun 27 16:37:20 tony-desktop kernel: [    9.475231] scsi1 : sata_nv
Jun 27 16:37:20 tony-desktop kernel: [    9.475362] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
Jun 27 16:37:20 tony-desktop kernel: [    9.475364] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
Jun 27 16:37:20 tony-desktop kernel: [   10.196023] ata1: SATA link down (SStatus 0 SControl 300)
Jun 27 16:37:20 tony-desktop kernel: [   11.076029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 27 16:37:20 tony-desktop kernel: [   11.084789] ata2.00: ATA-7: WDC WD1500ADFD-00NLR1, 20.07P20, max UDMA/133
Jun 27 16:37:20 tony-desktop kernel: [   11.084792] ata2.00: 293046768 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 27 16:37:20 tony-desktop kernel: [   11.100794] ata2.00: configured for UDMA/133
Jun 27 16:37:20 tony-desktop kernel: [   11.100891] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1500ADFD-0 20.0 PQ: 0 ANSI: 5
Jun 27 16:37:20 tony-desktop kernel: [   11.100963] sd 1:0:0:0: [sda] 293046768 512-byte hardware sectors: (150 GB/139 GiB)
Jun 27 16:37:20 tony-desktop kernel: [   11.100977] sd 1:0:0:0: [sda] Write Protect is off
Jun 27 16:37:20 tony-desktop kernel: [   11.101000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 27 16:37:20 tony-desktop kernel: [   11.101065] sd 1:0:0:0: [sda] 293046768 512-byte hardware sectors: (150 GB/139 GiB)
Jun 27 16:37:20 tony-desktop kernel: [   11.101077] sd 1:0:0:0: [sda] Write Protect is off
Jun 27 16:37:20 tony-desktop kernel: [   11.101098] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 27 16:37:20 tony-desktop kernel: [   11.101101]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
Jun 27 16:37:20 tony-desktop kernel: [   11.135752] sd 1:0:0:0: [sda] Attached SCSI disk
Jun 27 16:37:20 tony-desktop kernel: [   11.135784] sd 1:0:0:0: Attached scsi generic sg0 type 0
Jun 27 16:37:20 tony-desktop kernel: [   11.136103] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
Jun 27 16:37:20 tony-desktop kernel: [   11.136108] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
Jun 27 16:37:20 tony-desktop kernel: [   11.136199] scsi2 : sata_nv
Jun 27 16:37:20 tony-desktop kernel: [   11.136260] scsi3 : sata_nv
Jun 27 16:37:20 tony-desktop kernel: [   11.136388] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 22
Jun 27 16:37:20 tony-desktop kernel: [   11.136391] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 22
Jun 27 16:37:20 tony-desktop kernel: [   11.860022] ata3: SATA link down (SStatus 0 SControl 300)
Jun 27 16:37:20 tony-desktop kernel: [   12.584021] ata4: SATA link down (SStatus 0 SControl 300)
Jun 27 16:37:20 tony-desktop kernel: [   12.584219] scsi4 : pata_amd
Jun 27 16:37:20 tony-desktop kernel: [   12.584295] scsi5 : pata_amd
Jun 27 16:37:20 tony-desktop kernel: [   12.584821] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jun 27 16:37:20 tony-desktop kernel: [   12.584823] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jun 27 16:37:20 tony-desktop kernel: [   12.748248] ata5.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB02, max UDMA/33
Jun 27 16:37:20 tony-desktop kernel: [   12.764198] ata5.00: configured for UDMA/33
Jun 27 16:37:20 tony-desktop kernel: [   12.765356] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB02 PQ: 0 ANSI: 5
Jun 27 16:37:20 tony-desktop kernel: [   12.772194] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 27 16:37:20 tony-desktop kernel: [   12.772197] Uniform CD-ROM driver Revision: 3.20
Jun 27 16:37:20 tony-desktop kernel: [   12.772302] sr 4:0:0:0: Attached scsi generic sg1 type 5
Jun 27 16:37:20 tony-desktop kernel: [   12.772737] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 27 16:37:20 tony-desktop kernel: [   12.772995] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Jun 27 16:37:20 tony-desktop kernel: [   12.773011] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
Jun 27 16:37:20 tony-desktop kernel: [   12.773023] ehci_hcd 0000:00:02.1: EHCI Host Controller
Jun 27 16:37:20 tony-desktop kernel: [   12.773073] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Jun 27 16:37:20 tony-desktop kernel: [   12.773094] ehci_hcd 0000:00:02.1: debug port 1
Jun 27 16:37:20 tony-desktop kernel: [   12.773108] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfeb00000
Jun 27 16:37:20 tony-desktop kernel: [   12.784022] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Jun 27 16:37:20 tony-desktop kernel: [   12.784083] usb usb1: configuration #1 chosen from 1 choice
Jun 27 16:37:20 tony-desktop kernel: [   12.784108] hub 1-0:1.0: USB hub found
Jun 27 16:37:20 tony-desktop kernel: [   12.784116] hub 1-0:1.0: 10 ports detected
Jun 27 16:37:20 tony-desktop kernel: [   12.784210] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 27 16:37:20 tony-desktop kernel: [   12.784461] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
Jun 27 16:37:20 tony-desktop kernel: [   12.784466] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
Jun 27 16:37:20 tony-desktop kernel: [   12.784477] ohci_hcd 0000:00:02.0: OHCI Host Controller
Jun 27 16:37:20 tony-desktop kernel: [   12.784513] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Jun 27 16:37:20 tony-desktop kernel: [   12.784529] ohci_hcd 0000:00:02.0: irq 20, io mem 0xd0103000
Jun 27 16:37:20 tony-desktop kernel: [   12.842047] usb usb2: configuration #1 chosen from 1 choice
Jun 27 16:37:20 tony-desktop kernel: [   12.842070] hub 2-0:1.0: USB hub found
Jun 27 16:37:20 tony-desktop kernel: [   12.842077] hub 2-0:1.0: 10 ports detected
Jun 27 16:37:20 tony-desktop kernel: [   12.842157] uhci_hcd: USB Universal Host Controller Interface driver
Jun 27 16:37:20 tony-desktop kernel: [   12.842218] PNP: No PS/2 controller found. Probing ports directly.
Jun 27 16:37:20 tony-desktop kernel: [   13.092401] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 27 16:37:20 tony-desktop kernel: [   13.092494] mice: PS/2 mouse device common for all mice
Jun 27 16:37:20 tony-desktop kernel: [   13.092645] rtc_cmos 00:04: RTC can wake from S4
Jun 27 16:37:20 tony-desktop kernel: [   13.092676] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Jun 27 16:37:20 tony-desktop kernel: [   13.092698] rtc0: alarms up to one year, y3k, 242 bytes nvram
Jun 27 16:37:20 tony-desktop kernel: [   13.092747] device-mapper: uevent: version 1.0.3
Jun 27 16:37:20 tony-desktop kernel: [   13.092850] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Jun 27 16:37:20 tony-desktop kernel: [   13.092984] device-mapper: multipath: version 1.0.5 loaded
Jun 27 16:37:20 tony-desktop kernel: [   13.092986] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 27 16:37:20 tony-desktop kernel: [   13.093074] EISA: Probing bus 0 at eisa.0
Jun 27 16:37:20 tony-desktop kernel: [   13.093080] Cannot allocate resource for EISA slot 1
Jun 27 16:37:20 tony-desktop kernel: [   13.093097] EISA: Detected 0 cards.
Jun 27 16:37:20 tony-desktop kernel: [   13.093162] cpuidle: using governor ladder
Jun 27 16:37:20 tony-desktop kernel: [   13.093164] cpuidle: using governor menu
Jun 27 16:37:20 tony-desktop kernel: [   13.093607] TCP cubic registered
Jun 27 16:37:20 tony-desktop kernel: [   13.093694] NET: Registered protocol family 10
Jun 27 16:37:20 tony-desktop kernel: [   13.094052] lo: Disabled Privacy Extensions
Jun 27 16:37:20 tony-desktop kernel: [   13.094329] NET: Registered protocol family 17
Jun 27 16:37:20 tony-desktop kernel: [   13.094343] Bluetooth: L2CAP ver 2.11
Jun 27 16:37:20 tony-desktop kernel: [   13.094344] Bluetooth: L2CAP socket layer initialized
Jun 27 16:37:20 tony-desktop kernel: [   13.094347] Bluetooth: SCO (Voice Link) ver 0.6
Jun 27 16:37:20 tony-desktop kernel: [   13.094349] Bluetooth: SCO socket layer initialized
Jun 27 16:37:20 tony-desktop kernel: [   13.094383] Bluetooth: RFCOMM socket layer initialized
Jun 27 16:37:20 tony-desktop kernel: [   13.094390] Bluetooth: RFCOMM TTY layer initialized
Jun 27 16:37:20 tony-desktop kernel: [   13.094392] Bluetooth: RFCOMM ver 1.10
Jun 27 16:37:20 tony-desktop kernel: [   13.094443] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (2 cpu cores) (version 2.20.00)
Jun 27 16:37:20 tony-desktop kernel: [   13.094500] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
Jun 27 16:37:20 tony-desktop kernel: [   13.094503] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
Jun 27 16:37:20 tony-desktop kernel: [   13.094505] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
Jun 27 16:37:20 tony-desktop kernel: [   13.094507] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Jun 27 16:37:20 tony-desktop kernel: [   13.094552] Using IPI No-Shortcut mode
Jun 27 16:37:20 tony-desktop kernel: [   13.094640] registered taskstats version 1
Jun 27 16:37:20 tony-desktop kernel: [   13.094772]   Magic number: 14:307:642
Jun 27 16:37:20 tony-desktop kernel: [   13.094888] rtc_cmos 00:04: setting system clock to 2010-06-27 16:37:13 UTC (1277656633)
Jun 27 16:37:20 tony-desktop kernel: [   13.094892] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 27 16:37:20 tony-desktop kernel: [   13.094893] EDD information not available.
Jun 27 16:37:20 tony-desktop kernel: [   13.095314] Freeing unused kernel memory: 532k freed
Jun 27 16:37:20 tony-desktop kernel: [   13.095450] Write protecting the kernel text: 4120k
Jun 27 16:37:20 tony-desktop kernel: [   13.095498] Write protecting the kernel read-only data: 1524k
Jun 27 16:37:20 tony-desktop kernel: [   13.153035] usb 1-2: new high speed USB device using ehci_hcd and address 3
Jun 27 16:37:20 tony-desktop kernel: [   13.279145] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Jun 27 16:37:20 tony-desktop kernel: [   13.279461] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Jun 27 16:37:20 tony-desktop kernel: [   13.279466] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jun 27 16:37:20 tony-desktop kernel: [   13.294763] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Jun 27 16:37:20 tony-desktop kernel: [   13.294774] ohci1394 0000:05:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
Jun 27 16:37:20 tony-desktop kernel: [   13.347505] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[d0000000-d00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun 27 16:37:20 tony-desktop kernel: [   13.352938] usb 1-2: configuration #1 chosen from 1 choice
Jun 27 16:37:20 tony-desktop kernel: [   13.353037] hub 1-2:1.0: USB hub found
Jun 27 16:37:20 tony-desktop kernel: [   13.353126] hub 1-2:1.0: 4 ports detected
Jun 27 16:37:20 tony-desktop kernel: [   13.385016] FDC 0 is a post-1991 82077
Jun 27 16:37:20 tony-desktop kernel: [   13.577161] usb 1-6: new high speed USB device using ehci_hcd and address 5
Jun 27 16:37:20 tony-desktop kernel: [   13.712456] usb 1-6: configuration #1 chosen from 1 choice
Jun 27 16:37:20 tony-desktop kernel: [   13.730980] Initializing USB Mass Storage driver...
Jun 27 16:37:20 tony-desktop kernel: [   13.731639] scsi6 : SCSI emulation for USB Mass Storage devices
Jun 27 16:37:20 tony-desktop kernel: [   13.731791] usbcore: registered new interface driver usb-storage
Jun 27 16:37:20 tony-desktop kernel: [   13.731794] USB Mass Storage support registered.
Jun 27 16:37:20 tony-desktop kernel: [   13.796715] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:30:1b:bb:8f:4d
Jun 27 16:37:20 tony-desktop kernel: [   13.796719] forcedeth 0000:00:0a.0: highdma csum timirq gbit lnktim desc-v3
Jun 27 16:37:20 tony-desktop kernel: [   13.825667] PM: Starting manual resume from disk
Jun 27 16:37:20 tony-desktop kernel: [   13.845736] kjournald starting.  Commit interval 5 seconds
Jun 27 16:37:20 tony-desktop kernel: [   13.845753] EXT3-fs: mounted filesystem with ordered data mode.
Jun 27 16:37:20 tony-desktop kernel: [   14.013021] usb 2-1: new low speed USB device using ohci_hcd and address 2
Jun 27 16:37:20 tony-desktop kernel: [   14.239103] usb 2-1: configuration #1 chosen from 1 choice
Jun 27 16:37:20 tony-desktop kernel: [   14.545023] usb 2-4: new full speed USB device using ohci_hcd and address 3
Jun 27 16:37:20 tony-desktop kernel: [   14.770110] usb 2-4: configuration #1 chosen from 1 choice
Jun 27 16:37:20 tony-desktop kernel: [   14.845261] usb 1-2.1: new high speed USB device using ehci_hcd and address 6
Jun 27 16:37:20 tony-desktop kernel: [   14.970424] usb 1-2.1: configuration #1 chosen from 1 choice
Jun 27 16:37:20 tony-desktop kernel: [   17.026747] udev: starting version 141
Jun 27 16:37:20 tony-desktop kernel: [   17.139920] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Jun 27 16:37:20 tony-desktop kernel: [   17.139959] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
Jun 27 16:37:20 tony-desktop kernel: [   17.162108] Linux agpgart interface v0.103
Jun 27 16:37:20 tony-desktop kernel: [   17.187733] rtusb init --->
Jun 27 16:37:20 tony-desktop kernel: [   17.188076] 
Jun 27 16:37:20 tony-desktop kernel: [   17.188077] 
Jun 27 16:37:20 tony-desktop kernel: [   17.188078] === pAd = f7e82000, size = 566744 ===
Jun 27 16:37:20 tony-desktop kernel: [   17.188079] 
Jun 27 16:37:20 tony-desktop kernel: [   17.188080] <-- RTMPAllocAdapterBlock, Status=0
Jun 27 16:37:20 tony-desktop kernel: [   17.188708] usbcore: registered new interface driver rt2870
Jun 27 16:37:20 tony-desktop kernel: [   17.326632] usbcore: registered new interface driver hiddev


Jun 27 16:37:20 tony-desktop kernel: [   17.351562] input: Dell Dell Smart Card Reader Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input4
Jun 27 16:37:20 tony-desktop kernel: [   17.356875] generic-usb 0003:413C:2101.0002: input,hidraw1: USB HID v1.11 Keyboard [Dell Dell Smart Card Reader Keyboard] on usb-0000:00:02.0-4/input0
Jun 27 16:37:20 tony-desktop kernel: [   17.356900] usbcore: registered new interface driver usbhid
Jun 27 16:37:20 tony-desktop kernel: [   17.356921] usbhid: v2.6:USB HID core driver
Jun 27 16:37:20 tony-desktop kernel: [   17.454757] nvidia: module license 'NVIDIA' taints kernel.
Jun 27 16:37:20 tony-desktop kernel: [   17.468441] parport_pc 00:09: reported by Plug and Play ACPI
Jun 27 16:37:20 tony-desktop kernel: [   17.468482] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 27 16:37:20 tony-desktop kernel: [   17.493637] ppdev: user-space parallel port driver
Jun 27 16:37:20 tony-desktop kernel: [   17.509680] input: PC Speaker as /devices/platform/pcspkr/input/input5
Jun 27 16:37:20 tony-desktop kernel: [   17.710159] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Jun 27 16:37:20 tony-desktop kernel: [   17.710170] nvidia 0000:01:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Jun 27 16:37:20 tony-desktop kernel: [   17.710619] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Jun 27 16:37:20 tony-desktop kernel: [   17.805250] ICE1724 0000:05:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Jun 27 16:37:20 tony-desktop kernel: [   17.934220] lp0: using parport0 (interrupt-driven).
Jun 27 16:37:20 tony-desktop kernel: [   17.995618] Adding 3004112k swap on /dev/sda8.  Priority:-1 extents:1 across:3004112k
Jun 27 16:37:20 tony-desktop kernel: [   18.527209] EXT3 FS on sda7, internal journal
Jun 27 16:37:20 tony-desktop kernel: [   18.730413] scsi 6:0:0:0: Direct-Access     Generic  CF Reader        1.01 PQ: 0 ANSI: 0
Jun 27 16:37:20 tony-desktop kernel: [   18.730901] scsi 6:0:0:1: Direct-Access     Generic  SM/SD/MS Reader  1.00 PQ: 0 ANSI: 0
Jun 27 16:37:20 tony-desktop kernel: [   18.731849] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Jun 27 16:37:20 tony-desktop kernel: [   18.731911] sd 6:0:0:0: Attached scsi generic sg2 type 0
Jun 27 16:37:20 tony-desktop kernel: [   18.732700] sd 6:0:0:1: [sdc] Attached SCSI removable disk
Jun 27 16:37:20 tony-desktop kernel: [   18.732737] sd 6:0:0:1: Attached scsi generic sg3 type 0
Jun 27 16:37:20 tony-desktop kernel: [   19.447555] type=1505 audit(1277671039.849:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2086
Jun 27 16:37:20 tony-desktop kernel: [   19.494026] type=1505 audit(1277671039.897:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2090
Jun 27 16:37:20 tony-desktop kernel: [   19.494159] type=1505 audit(1277671039.897:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2090
Jun 27 16:37:20 tony-desktop kernel: [   19.494203] type=1505 audit(1277671039.897:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2090
Jun 27 16:37:20 tony-desktop kernel: [   19.494247] type=1505 audit(1277671039.897:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2090
Jun 27 16:37:20 tony-desktop kernel: [   19.627671] type=1505 audit(1277671040.029:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2095
Jun 27 16:37:20 tony-desktop kernel: [   19.627865] type=1505 audit(1277671040.029:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2095
Jun 27 16:37:20 tony-desktop kernel: [   19.654160] type=1505 audit(1277671040.057:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2099
Jun 27 16:37:22 tony-desktop kernel: [   21.618505] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 27 16:37:22 tony-desktop kernel: [   21.618509] Bluetooth: BNEP filters: protocol multicast
Jun 27 16:37:22 tony-desktop kernel: [   21.627799] Bridge firewalling registered
Jun 27 16:37:27 tony-desktop kernel: [   26.595047] eth0: no link during initialization.
Jun 27 16:37:27 tony-desktop kernel: [   26.595475] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 27 16:37:27 tony-desktop kernel: [   26.858129] <-- RTMPAllocTxRxRingMemory, Status=0
Jun 27 16:37:27 tony-desktop kernel: [   26.859758] -->RTUSBVenderReset
Jun 27 16:37:27 tony-desktop kernel: [   26.859883] <--RTUSBVenderReset
Jun 27 16:37:27 tony-desktop kernel: [   27.139160] --> Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
Jun 27 16:37:27 tony-desktop kernel: [   27.139164] 1. Phy Mode = 0
Jun 27 16:37:27 tony-desktop kernel: [   27.139166] 2. Phy Mode = 0
Jun 27 16:37:27 tony-desktop kernel: [   27.168271] RTMPSetPhyMode: channel is out of range, use first channel=1 
Jun 27 16:37:27 tony-desktop kernel: [   27.178265] 3. Phy Mode = 0
Jun 27 16:37:27 tony-desktop kernel: [   27.182640] MCS Set = 00 00 00 00 00
Jun 27 16:37:27 tony-desktop kernel: [   27.192393] <==== RTMPInitialize, Status=0
Jun 27 16:37:27 tony-desktop kernel: [   27.193898] 0x1300 = 00073200
Jun 27 16:37:32 tony-desktop kernel: [   32.210716] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 289
Jun 27 16:37:32 tony-desktop pulseaudio[3263]: alsa-util.c: Device front:0 doesn't support sample format s16le, changed to s32le.
Jun 27 16:37:32 tony-desktop pulseaudio[3263]: alsa-util.c: Device front:0 doesn't support sample format s16le, changed to s32le.
Jun 27 16:37:43 tony-desktop kernel: [   42.996060] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 289
Jun 27 16:37:43 tony-desktop kernel: [   42.996260] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Jun 27 16:37:43 tony-desktop kernel: [   43.058408] DRS: unkown mode,default use 11N 2S AP 
Jun 27 16:37:43 tony-desktop kernel: [   43.058413] DRS: unkown mode (SupRateLen=0, ExtRateLen=0, MCSSet[0]=0x0, MCSSet[1]=0x0)
Jun 27 16:36:57 tony-desktop kernel: [   86.036018] Clocksource tsc unstable (delta = -91342407 ns)
Jun 27 16:37:08 tony-desktop kernel: [   96.437793] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 162
Jun 27 16:38:08 tony-desktop kernel: [  156.434668] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 289
Jun 27 16:39:28 tony-desktop kernel: [  236.436066] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 162
Jun 27 16:41:08 tony-desktop kernel: [  336.436073] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 162

```

---

### Post by RJARRRPCGP on 2010-06-28
You may have bad caps: Especially if your motherboard was made before 2005.

[http://badcaps.net](http://badcaps.net)

---

### Post by Putnam11 on 2010-06-28
If you have any hardware acceleration, you should try to turn that off.  I had it freeze up a lot before, then I turned off my CPU and GPU hardware acceleration.

---

### Post by mörgæs on 2010-06-28
The photo shows a kernel panic. 

How does the machine work, if you go 'and now till something completely different': A live Puppy Linux, for example?

If you get some operative system to run, try a full memory test.

---

### Post by agm. on 2010-06-28
This problem is quite quite confusing and tricky!  Yesterday, I tried to boot into the windows partition and after about 20-30 minutes, it froze as well.  This made me think that it was a significant hardware problem.

After cleaning the case with compressed air and leaving the cover off, I tried to boot into 9.04 again and it froze in about 7-8 minutes, but longer than it had allowed prior to the cleaning, but it still locked up.

Today, I booted into Windows to try SpeedFan because it was a quick utility that could log the entire CPU temperature data (and I hadn't found something similar in Linux yet). 

Well, it has been running Windows for over 2 hours without locking up.  I have had the SpeedFan running and the GPU is at 60C and the CPU is at about 50C, but it stays constantly around those temperatures.

So I of course, shut down windows and rebooted into Linux and it locked the system in about 3 minutes.  I was trying to install lm-sensors to see if I could get that to do similar things to SpeedFan and it locked right after downloading them.

So this is making me wonder whether it is software or hardware related.  If it is hardware related, I definitely think at this point that it is either CPU/motherboard issues, but it is unclear why windows will run for so long while Linux will lock up.

In regards to hardware acceleration, how do I know if I have any of it turned on?  I have compiz fusion turned on... is that hardware acceleration?  (Sorry for the ignorance)

Thanks for the help and hopefully I can figure this problem out with all of your help!

---

### Post by mörgæs on 2010-06-29
It is very likely hardware related, but CPU and motherboard hardly ever fails given the temperatures you mention (50-60 °C). However, memory errors are common and can give a lot of strange symptoms, among others freezing and kernel panic.

Again, best is to run a memory test and / or try to switch memory with another machine, if you have access to one.

---

### Post by agm. on 2010-06-29
Ran a memory test using memtest86 (tested it twice) and it passed.

Additionally, is there a big difference between hardware interface between windows and linux?  The reason I ask is that currently, I have had windows running for upwards of 5-6 hours without it locking, but I cannot get linux to last more than 10 minutes!

Seems strange.  Any other suggestions are greatly appreciated.

I will try to burn a copy of Puppy Linux later today at work and bring it home and try to see if that will boot from a LiveCD.

Thanks for the help

---

### Post by nhasian on 2010-06-29
I just want to clarify, you said that windows ALSO locks up after 5-6 hours?  Neither Windows nor Ubuntu should lock up.  if both operating systems are locking up (regardless of the duration of time between lockups) then you definitely have a hardware problem with your computer.

> **agm. said:**
> ... I have had windows running for upwards of 5-6 hours without it locking, but I cannot get linux to last more than 10 minutes!

---

### Post by agm. on 2010-06-29
> I just want to clarify, you said that windows ALSO locks up after 5-6 hours? Neither Windows nor Ubuntu should lock up. if both operating systems are locking up (regardless of the duration of time between lockups) then you definitely have a hardware problem with your computer.

No, as of right now, I am running Windows on this computer and it has been running for approximately 7 hours and has yet to lock up. I'm keeping it on over night to see if it will stay stable.  If it does, then I definitely think it is something Linux related.  I am going to try and burn two new LiveCD's tomorrow.  One of puppy Linux because it is supposed to be smaller and another of 10.04.  I want to see if I burn new Live CD's (and different distro's) whether I get the same errors as the first two live CD's.

It is very strange though.  I originally thought that it was hardware related because I was trying to do lots of tasks to see if I could get windows to freeze similarly to Linux and I think it just sort of "slowed down" really badly and I took it as the same thing.  Since that one time, I have had windows running for 3 hours, 5 hours, and 7 hours with no problems.  I then reboot the computer and log into the 9.04 partition and it only lasts 5-7 minutes.  

But I can't find anything in the logs that can help me identify the problem (though I am not 100% what would identify the problem).

Thanks for your help!

---

### Post by agm. on 2010-07-01
As an update... At this point, I am almost 100% sure it is hardware related.  Regardless of which partition it boots into, the computer will freeze.  Ubuntu 9.04 only lasts about 4-8 minutes before a freeze, while Windows XP can last upwards of 10 hours (but it will freeze).  

I have been using Windows XP more so than Ubuntu recently to try and diagnose the problems.  The GPU temp stays at roughly 55-60C and the CPU stays at 45-50C.  I have been using SpeedFan to see if right before a crash there is a major spike in CPU/GPU temperature, and there is not one.  Would this mean that it is most likely a RAM related problem?

Additionally, I downloaded a Puppy Linux Live CD and booted into it.  While the system would boot into Puppy Linux, it would still freeze in this system as well.  From my understanding, when you boot into a Live CD, that means that you are running on RAM, which would further lead to a RAM problem... thoughts?

My question is that I have done a Memtest86 and Memtest86+ and it has passed each test.  Do I run this for a set number of iterations?  Also if the RAM passes the test the first time, can it fail it on subsequent passes?  

Any further comments on this problem would be greatly appreciated!

---

### Post by nhasian on 2010-07-01
Booting from the liveCD just takes the hard disk or hard disk controller out of the equation. Yes ubuntu is running from ram, and the cd drive instead of the hard disk and ram... so on 2nd thought it really doesnt take the controller out of the equation, only the hard disk :D

so anyways, if you can replace the cpu, ram, video adaptor, motherboard one at a time you can isolate the problematic part.  someone mentioned earlier that for a few years ago a lot of motherboards had defective capacitors.  I would check that first.

from [http://www.nytimes.com/2010/06/29/technology/29dell.html](http://www.nytimes.com/2010/06/29/technology/29dell.html)

> The problems affecting the Dell computers stemmed from an industrywide encounter with bad capacitors produced by Asian PC component suppliers. Capacitors are found on computer motherboards, playing a crucial role in the flow of current across the hardware. They are not meant to pop and leak fluid, but that is exactly what was happening earlier this decade, causing computers made by Dell, Hewlett-Packard, Apple and others to break. 

> **agm. said:**
> From my understanding, when you boot into a Live CD, that means that you are running on RAM, which would further lead to a RAM problem... thoughts?

---

### Post by agm. on 2010-07-10
Well, I "think" I have figured out the problem at this point and it is an extremely simple solution, but totally overlooked!

I took the computer into a local repair shop this week and they had the computer all week and couldn't replicate the same issue with the computer freezing.  They looked in the log file and found "usb device errors" and had me bring in all my USB peripherals but they could not replicate the problem!

The only thing that I did not bring in was my monitor which can create 4 additional USB ports through a usb (computer) to monitor connection.  After playing around with it in the store for about 10-15 minutes and the system not breaking, I took it home.  When I took it home and attached it to my monitor, I only attached DVI and the system continued to work well.

I shut down and added in the monitor 4 port hub and immediately the system locked!  After removing it and restarting, I've been running the OS for about 4 hours and not having any issues.

So my advice if anyone ever sees this thread trying to trouble shoot is that don't forget to do the extremely simple "checks" of removing all USB devices, and adding them back in 1 at a time to try and fix the problem!  It sometimes can be the most basic thing (and I guess the hub has gone bad? I don't care and won't be using it anymore now that I have a stable system again)!

Thanks for the help and the recommendations during the whole process!

---

### Post by mörgæs on 2010-07-11
Thanks for sharing. I didn't suspect the USB units, but I will remember this.

---

