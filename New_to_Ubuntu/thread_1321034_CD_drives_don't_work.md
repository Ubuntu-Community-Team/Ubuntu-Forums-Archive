---
title: "CD drives don't work"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by abooks on 2009-11-09
Since upgrading to 9.04, then 9.10 neither of my disc drives work. When I put in audio, I can find it on Amarok, but it has no name and no files, so won't play. I tried putting in a photo CD, opened Gwen and saw its name, but when I clicked on it the machine froze and I hard to hard boot to get out at all.

---

### Post by abooks on 2009-11-09
I don't know the diagnostics, but borrowing from other forums I tried a few things that indicate Ubuntu can see them:

$ ls /dev/s*
/dev/scd0  /dev/sda1  /dev/sequencer   /dev/sg1       /dev/sndstat  /dev/stderr
/dev/scd1  /dev/sda2  /dev/sequencer2  /dev/sg2       /dev/sr0      /dev/stdin
/dev/sda   /dev/sda5  /dev/sg0         /dev/snapshot  /dev/sr1      /dev/stdout

/dev/shm:
pulse-shm-4277770060

/dev/snd:
by-path    controlC1  hwC1D0    pcmC0D0c  pcmC1D0c  pcmC1D1p  pcmC1D2p  timer
controlC0  hwC0D2     midiC1D0  pcmC0D0p  pcmC1D0p  pcmC1D2c  seq

with a cd in the driver:

$ mount                                                       
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)                    
proc on /proc type proc (rw)                                                
none on /sys type sysfs (rw,noexec,nosuid,nodev)                            
none on /sys/fs/fuse/connections type fusectl (rw)                          
none on /sys/kernel/debug type debugfs (rw)                                 
none on /sys/kernel/security type securityfs (rw)                           
udev on /dev type tmpfs (rw,mode=0755)                                      
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)             
none on /dev/shm type tmpfs (rw,nosuid,nodev)                               
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


and

sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4b0b8b6                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9544    76662148+  83  Linux 
/dev/sda2            9545        9726     1461915    5  Extended
/dev/sda5            9545        9726     1461883+  82  Linux swap / Solaris


But what does it mean?

---

### Post by abooks on 2009-11-09
Does this help?

mount /dev/cdrom
mount: block device /dev/sr1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by coldReactive on 2009-11-09
After it freezes, boot back up, open the dmesg log and output it here (between code bbcode so it won't take up so much space.)

---

### Post by abooks on 2009-11-09
So then: 

dmesg | tail
[15873.772122] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[15879.016978] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[15884.260102] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[15889.504096] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[15894.744106] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[15899.984125] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[15905.224141] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[15910.464155] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[15915.704127] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[15920.944108] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

---

### Post by coldReactive on 2009-11-09
> **abooks said:**
> So then:

No, go to /var/log/dmesg and post the whole output.

---

### Post by abooks on 2009-11-09
Sorry, Cold: our postings crossed. Here's what I got when I tried yours:

walt@desktop:~$ sudo /var/log/dmesg
[sudo] password for walt:
sudo: /var/log/dmesg: command not found

By the way, I tried the photo one again and it worked. Still have questions. . .will it work with a sound cd, and is it mounted?

---

### Post by coldReactive on 2009-11-09
> **abooks said:**
> Sorry, Cold: our postings crossed. Here's what I got when I tried yours:

walt@desktop:~$ sudo /var/log/dmesg
[sudo] password for walt:
sudo: /var/log/dmesg: command not found

By the way, I tried the photo one again and it worked. Still have questions. . .will it work with a sound cd, and is it mounted?

/var/log/dmesg is a log file, not a command:

gedit /var/log/dmesg

next time. I wouldn't know, sadly.

---

### Post by abooks on 2009-11-09
I didn't understand the parts you wanted, so here's the whole thing:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f651c00 (usable)
[    0.000000]  BIOS-e820: 000000001f651c00 - 000000001f653c00 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f655c00 - 000000001f657c00 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f657c00 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x1f651 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 000000000 write-back
[    0.000000]   1 base 01F800000 mask FFF800000 uncachable
[    0.000000]   2 base 01F700000 mask FFFF00000 uncachable
[    0.000000]   3 base 020000000 mask FE0000000 uncachable
[    0.000000]   4 base 040000000 mask FC0000000 uncachable
[    0.000000]   5 base 080000000 mask F80000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 000000001f700000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009ac00 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001f651c00 (usable)
[    0.000000]  modified: 000000001f651c00 - 000000001f653c00 (ACPI NVS)
[    0.000000]  modified: 000000001f655c00 - 000000001f657c00 (ACPI data)
[    0.000000]  modified: 000000001f657c00 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001f651000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001f400000 page 2M
[    0.000000]  001f400000 - 001f651000 page 4k
[    0.000000] kernel direct mapping tables up to 1f651000 @ 7000-c000
[    0.000000] RAMDISK: 1eef7000 - 1f641a7a
[    0.000000] ACPI: RSDP 000febf0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 000fd086 00064 (v01 DELL    B8K     00000014 ASL  00000061)
[    0.000000] ACPI: FACP 000fd1a6 000F4 (v03 DELL    B8K     00000014 ASL  00000061)
[    0.000000] ACPI: DSDT fffd642b 033DC (v01   DELL    dt_ex 00001000 INTL 20050624)
[    0.000000] ACPI: FACS 1f651c00 00040
[    0.000000] ACPI: SSDT fffd9928 000AC (v01   DELL    st_ex 00001000 INTL 20050624)
[    0.000000] ACPI: APIC 000fd29a 00092 (v01 DELL    B8K     00000014 ASL  00000061)
[    0.000000] ACPI: BOOT 000fd32c 00028 (v01 DELL    B8K     00000014 ASL  00000061)
[    0.000000] ACPI: MCFG 000fd354 0003E (v01 DELL    B8K     00000014 ASL  00000061)
[    0.000000] ACPI: HPET 000fd392 00038 (v01 DELL    B8K     00000014 ASL  00000061)
[    0.000000] ACPI: DUMY 1f655c00 00024 (v01 DELL    B8K     00000014 ASL  00000061)
[    0.000000] ACPI: SLIC 000fd3ca 00176 (v01 DELL    B8K     00000014 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1f651000
[    0.000000]   low ram: 0 - 1f651000
[    0.000000]   node 0 low ram: 00000000 - 1f651000
[    0.000000]   node 0 bootmap 00008000 - 0000becc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f651000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [001eef7000 - 001f641a7a]          RAMDISK ==> [001eef7000 - 001f641a7a]
[    0.000000]   #5 [000009ac00 - 0000100000]    BIOS reserved ==> [000009ac00 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac1e0]              BRK ==> [00008a9000 - 00008ac1e0]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001f651
[    0.000000]   HighMem  0x0001f651 -> 0x0001f651
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x0001f651
[    0.000000] On node 0 totalpages: 128487
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3958 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123524 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c13f2000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127482
[    0.000000] Kernel command line: root=UUID=bb211efb-27f3-4f85-ad77-66241c09a866 ro quiet splash 
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2571860 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 490880k/514372k available (4565k kernel code, 22756k reserved, 2143k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdfe51000 - 0xff7fe000   ( 505 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdf651000   ( 502 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:472
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2793.340 MHz processor.
[    0.001592] Console: colour VGA+ 80x25
[    0.001597] console [tty0] enabled
[    0.001724] hpet clockevent registered
[    0.001729] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.001735] Calibrating delay loop (skipped), value calculated using timer frequency.. 5586.68 BogoMIPS (lpj=11173360)
[    0.001756] Security Framework initialized
[    0.001777] AppArmor: AppArmor initialized
[    0.001787] Mount-cache hash table entries: 512
[    0.001939] Initializing cgroup subsys ns
[    0.001945] Initializing cgroup subsys cpuacct
[    0.001951] Initializing cgroup subsys memory
[    0.001959] Initializing cgroup subsys freezer
[    0.001962] Initializing cgroup subsys net_cls
[    0.001984] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.001988] CPU: L2 cache: 1024K
[    0.001991] CPU: Physical Processor ID: 0
[    0.001994] CPU: Processor Core ID: 0
[    0.001998] mce: CPU supports 4 MCE banks
[    0.002012] CPU0: Thermal monitoring enabled (TM1)
[    0.002017] using mwait in idle threads.
[    0.002024] Performance Counters: no PMU driver, software counters only.
[    0.002032] Checking 'hlt' instruction... OK.
[    0.019850] ACPI: Core revision 20090521
[    0.178967] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.218671] CPU0: Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.220001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5586.20 BogoMIPS (lpj=11172410)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 4 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.304913] CPU1: Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.304931] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.308020] Brought up 2 CPUs
[    0.308026] Total of 2 processors activated (11172.88 BogoMIPS).
[    0.308078] CPU0 attaching sched-domain:
[    0.308082]  domain 0: span 0-1 level CPU
[    0.308086]   groups: 0 1
[    0.308094] CPU1 attaching sched-domain:
[    0.308099]  domain 0: span 0-1 level CPU
[    0.308103]   groups: 1 0
[    0.308190] Dell E520 series board detected. Selecting BIOS-method for reboots.
[    0.308190] Booting paravirtualized kernel on bare hardware
[    0.308314] regulator: core version 0.5
[    0.308314] Time: 22:44:52  Date: 11/09/09
[    0.308314] NET: Registered protocol family 16
[    0.308314] EISA bus registered
[    0.308320] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.308324] ACPI: bus type pci registered
[    0.308406] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.308410] PCI: MCFG area at e0000000 reserved in E820
[    0.308413] PCI: Using MMCONFIG for extended config space
[    0.308416] PCI: Using configuration type 1 for base access
[    0.309947] bio: create slab <bio-0> at 0
[    0.312572] ACPI: EC: Look up EC in DSDT
[    0.355484] ACPI: BIOS _OSI(Linux) query ignored
[    0.377202] ACPI: Interpreter enabled
[    0.377214] ACPI: (supports S0 S1 S3 S4 S5)
[    0.377249] ACPI: Using IOAPIC for interrupt routing
[    0.460015] ACPI: No dock devices found.
[    0.466950] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.467098] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.467103] pci 0000:00:01.0: PME# disabled
[    0.467142] pci 0000:00:02.0: reg 10 32bit mmio: [0xdfe00000-0xdfefffff]
[    0.467155] pci 0000:00:02.0: reg 18 64bit mmio: [0xc0000000-0xcfffffff]
[    0.467162] pci 0000:00:02.0: reg 20 io port: [0xec98-0xec9f]
[    0.467213] pci 0000:00:02.1: reg 10 32bit mmio: [0xdff00000-0xdfffffff]
[    0.467319] pci 0000:00:19.0: reg 10 32bit mmio: [0xdfde0000-0xdfdfffff]
[    0.467328] pci 0000:00:19.0: reg 14 32bit mmio: [0xdfddb000-0xdfddbfff]
[    0.467336] pci 0000:00:19.0: reg 18 io port: [0xecc0-0xecdf]
[    0.467380] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.467385] pci 0000:00:19.0: PME# disabled
[    0.467433] pci 0000:00:1a.0: reg 20 io port: [0xff20-0xff3f]
[    0.467492] pci 0000:00:1a.1: reg 20 io port: [0xff00-0xff1f]
[    0.467559] pci 0000:00:1a.7: reg 10 32bit mmio: [0xdfddac00-0xdfddafff]
[    0.467620] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.467626] pci 0000:00:1a.7: PME# disabled
[    0.467676] pci 0000:00:1b.0: reg 10 64bit mmio: [0xdfddc000-0xdfddffff]
[    0.468016] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.468022] pci 0000:00:1b.0: PME# disabled
[    0.468096] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.468101] pci 0000:00:1c.0: PME# disabled
[    0.468164] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.468224] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.468283] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.468353] pci 0000:00:1d.7: reg 10 32bit mmio: [0xff980800-0xff980bff]
[    0.468414] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.468420] pci 0000:00:1d.7: PME# disabled
[    0.468561] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.468566] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH6 GPIO
[    0.468571] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0c00 (mask 007f)
[    0.468576] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 00e0 (mask 0007)
[    0.468650] pci 0000:00:1f.2: reg 10 io port: [0xfe00-0xfe07]
[    0.468658] pci 0000:00:1f.2: reg 14 io port: [0xfe10-0xfe13]
[    0.468666] pci 0000:00:1f.2: reg 18 io port: [0xfe20-0xfe27]
[    0.468673] pci 0000:00:1f.2: reg 1c io port: [0xfe30-0xfe33]
[    0.468681] pci 0000:00:1f.2: reg 20 io port: [0xfec0-0xfedf]
[    0.468689] pci 0000:00:1f.2: reg 24 32bit mmio: [0xff970000-0xff9707ff]
[    0.468724] pci 0000:00:1f.2: PME# supported from D3hot
[    0.468729] pci 0000:00:1f.2: PME# disabled
[    0.468759] pci 0000:00:1f.3: reg 10 32bit mmio: [0xdfddab00-0xdfddabff]
[    0.468781] pci 0000:00:1f.3: reg 20 io port: [0xece0-0xecff]
[    0.468855] pci 0000:00:01.0: bridge 32bit mmio: [0xdfc00000-0xdfcfffff]
[    0.468911] pci 0000:00:1c.0: bridge 32bit mmio: [0xdfb00000-0xdfbfffff]
[    0.468963] pci 0000:03:02.0: reg 10 io port: [0xdc00-0xdcff]
[    0.469024] pci 0000:03:02.0: supports D1 D2
[    0.469079] pci 0000:00:1e.0: transparent bridge
[    0.469084] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.469108] pci_bus 0000:00: on NUMA node 0
[    0.469114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.469787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    0.470197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.470599] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    1.487044] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    1.487862] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    1.488693] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    1.489500] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    1.490326] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.491129] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.491939] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.492777] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[    1.493191] SCSI subsystem initialized
[    1.493230] libata version 3.00 loaded.
[    1.493230] usbcore: registered new interface driver usbfs
[    1.493230] usbcore: registered new interface driver hub
[    1.493230] usbcore: registered new device driver usb
[    1.493230] ACPI: WMI: Mapper loaded
[    1.493230] PCI: Using ACPI for IRQ routing
[    1.504014] Bluetooth: Core ver 2.15
[    1.504036] NET: Registered protocol family 31
[    1.504036] Bluetooth: HCI device and connection manager initialized
[    1.504036] Bluetooth: HCI socket layer initialized
[    1.504036] NetLabel: Initializing
[    1.504036] NetLabel:  domain hash size = 128
[    1.504036] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.504056] NetLabel:  unlabeled traffic allowed by default
[    1.504100] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.504108] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.512028] Switched to high resolution mode on CPU 0
[    1.512972] Switched to high resolution mode on CPU 1
[    1.520017] pnp: PnP ACPI init
[    1.520038] ACPI: bus type pnp registered
[    1.530690] pnp 00:01: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    1.530696] pnp 00:01: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    1.562765] pnp: PnP ACPI: found 9 devices
[    1.562769] ACPI: ACPI bus type pnp unregistered
[    1.562775] PnPBIOS: Disabled by ACPI PNP
[    1.562794] system 00:01: ioport range 0xc00-0xc7f has been reserved
[    1.562808] system 00:06: iomem range 0x0-0x9ffff could not be reserved
[    1.562813] system 00:06: iomem range 0x100000-0xffffff could not be reserved
[    1.562817] system 00:06: iomem range 0x1000000-0x1f651bff could not be reserved
[    1.562821] system 00:06: iomem range 0xf0000-0xfffff could not be reserved
[    1.562825] system 00:06: iomem range 0xc0000-0xd3fff could not be reserved
[    1.562830] system 00:06: iomem range 0xfec00000-0xfecfffff could not be reserved
[    1.562834] system 00:06: iomem range 0xfee00000-0xfeefffff has been reserved
[    1.562838] system 00:06: iomem range 0xffb00000-0xffbfffff has been reserved
[    1.562842] system 00:06: iomem range 0xffc00000-0xffffffff has been reserved
[    1.562851] system 00:07: ioport range 0x100-0x1fe has been reserved
[    1.562855] system 00:07: ioport range 0x200-0x277 has been reserved
[    1.562859] system 00:07: ioport range 0x280-0x2e7 has been reserved
[    1.562863] system 00:07: ioport range 0x2e8-0x2ef has been reserved
[    1.562867] system 00:07: ioport range 0x2f0-0x2f7 has been reserved
[    1.562871] system 00:07: ioport range 0x2f8-0x2ff has been reserved
[    1.562875] system 00:07: ioport range 0x300-0x377 has been reserved
[    1.562879] system 00:07: ioport range 0x380-0x3bb has been reserved
[    1.562883] system 00:07: ioport range 0x3c0-0x3e7 could not be reserved
[    1.562887] system 00:07: ioport range 0x3f6-0x3f7 has been reserved
[    1.562891] system 00:07: ioport range 0x400-0x4cf has been reserved
[    1.562895] system 00:07: ioport range 0x4d2-0x57f has been reserved
[    1.562899] system 00:07: ioport range 0x580-0x677 has been reserved
[    1.562903] system 00:07: ioport range 0x680-0x777 has been reserved
[    1.562907] system 00:07: ioport range 0x780-0x7bb has been reserved
[    1.562913] system 00:07: ioport range 0x7c0-0x7ff has been reserved
[    1.562917] system 00:07: ioport range 0x8e0-0x8ff has been reserved
[    1.562921] system 00:07: ioport range 0x900-0x9fe has been reserved
[    1.562925] system 00:07: ioport range 0xa00-0xafe has been reserved
[    1.562929] system 00:07: ioport range 0xb00-0xbfe has been reserved
[    1.562933] system 00:07: ioport range 0xc80-0xcaf has been reserved
[    1.562937] system 00:07: ioport range 0xcb0-0xcbf has been reserved
[    1.562941] system 00:07: ioport range 0xcc0-0xcf7 has been reserved
[    1.562945] system 00:07: ioport range 0xd00-0xdfe has been reserved
[    1.562949] system 00:07: ioport range 0xe00-0xefe has been reserved
[    1.562953] system 00:07: ioport range 0xf00-0xffe has been reserved
[    1.562957] system 00:07: ioport range 0x2000-0x20fe has been reserved
[    1.562961] system 00:07: ioport range 0x2100-0x21fe has been reserved
[    1.562965] system 00:07: ioport range 0x2200-0x22fe has been reserved
[    1.562969] system 00:07: ioport range 0x2300-0x23fe has been reserved
[    1.562973] system 00:07: ioport range 0x2400-0x24fe has been reserved
[    1.562977] system 00:07: ioport range 0x2500-0x25fe has been reserved
[    1.562981] system 00:07: ioport range 0x2600-0x26fe has been reserved
[    1.562986] system 00:07: ioport range 0x2700-0x27fe has been reserved
[    1.562990] system 00:07: ioport range 0x2800-0x28fe has been reserved
[    1.562994] system 00:07: ioport range 0x2900-0x29fe has been reserved
[    1.562998] system 00:07: ioport range 0x2a00-0x2afe has been reserved
[    1.563002] system 00:07: ioport range 0x2b00-0x2bfe has been reserved
[    1.563006] system 00:07: ioport range 0x2c00-0x2cfe has been reserved
[    1.563010] system 00:07: ioport range 0x2d00-0x2dfe has been reserved
[    1.563014] system 00:07: ioport range 0x2e00-0x2efe has been reserved
[    1.563018] system 00:07: ioport range 0x2f00-0x2ffe has been reserved
[    1.563022] system 00:07: ioport range 0x5000-0x50fe has been reserved
[    1.563027] system 00:07: ioport range 0x5100-0x51fe has been reserved
[    1.563031] system 00:07: ioport range 0x5200-0x52fe has been reserved
[    1.563035] system 00:07: ioport range 0x5300-0x53fe has been reserved
[    1.563039] system 00:07: ioport range 0x5400-0x54fe has been reserved
[    1.563043] system 00:07: ioport range 0x5500-0x55fe has been reserved
[    1.563047] system 00:07: ioport range 0x5600-0x56fe has been reserved
[    1.563051] system 00:07: ioport range 0x5700-0x57fe has been reserved
[    1.563056] system 00:07: ioport range 0x5800-0x58fe has been reserved
[    1.563060] system 00:07: ioport range 0x5900-0x59fe has been reserved
[    1.563064] system 00:07: ioport range 0x5a00-0x5afe has been reserved
[    1.563068] system 00:07: ioport range 0x5b00-0x5bfe has been reserved
[    1.563072] system 00:07: ioport range 0x5c00-0x5cfe has been reserved
[    1.563076] system 00:07: ioport range 0x5d00-0x5dfe has been reserved
[    1.563081] system 00:07: ioport range 0x5e00-0x5efe has been reserved
[    1.563085] system 00:07: ioport range 0x5f00-0x5ffe has been reserved
[    1.563089] system 00:07: ioport range 0x6000-0x60fe has been reserved
[    1.563093] system 00:07: ioport range 0x6100-0x61fe has been reserved
[    1.563098] system 00:07: ioport range 0x6200-0x62fe has been reserved
[    1.563102] system 00:07: ioport range 0x6300-0x63fe has been reserved
[    1.563106] system 00:07: ioport range 0x6400-0x64fe has been reserved
[    1.563110] system 00:07: ioport range 0x6500-0x65fe has been reserved
[    1.563115] system 00:07: ioport range 0x6600-0x66fe has been reserved
[    1.563122] system 00:07: ioport range 0x6700-0x67fe has been reserved
[    1.563127] system 00:07: ioport range 0x6800-0x68fe has been reserved
[    1.563131] system 00:07: ioport range 0x6900-0x69fe has been reserved
[    1.563135] system 00:07: ioport range 0x6a00-0x6afe has been reserved
[    1.563139] system 00:07: ioport range 0x6b00-0x6bfe has been reserved
[    1.563144] system 00:07: ioport range 0x6c00-0x6cfe has been reserved
[    1.563148] system 00:07: ioport range 0x6d00-0x6dfe has been reserved
[    1.563152] system 00:07: ioport range 0x6e00-0x6efe has been reserved
[    1.563157] system 00:07: ioport range 0x6f00-0x6ffe has been reserved
[    1.563161] system 00:07: ioport range 0xa000-0xa0fe has been reserved
[    1.563166] system 00:07: ioport range 0xa100-0xa1fe has been reserved
[    1.563170] system 00:07: ioport range 0xa200-0xa2fe has been reserved
[    1.563175] system 00:07: ioport range 0xa300-0xa3fe has been reserved
[    1.563180] system 00:07: ioport range 0xa400-0xa4fe has been reserved
[    1.563184] system 00:07: ioport range 0xa500-0xa5fe has been reserved
[    1.563189] system 00:07: ioport range 0xa600-0xa6fe has been reserved
[    1.563193] system 00:07: ioport range 0xa700-0xa7fe has been reserved
[    1.563198] system 00:07: ioport range 0xa800-0xa8fe has been reserved
[    1.563202] system 00:07: ioport range 0xa900-0xa9fe has been reserved
[    1.563207] system 00:07: ioport range 0xaa00-0xaafe has been reserved
[    1.563211] system 00:07: ioport range 0xab00-0xabfe has been reserved
[    1.563216] system 00:07: ioport range 0xac00-0xacfe has been reserved
[    1.563220] system 00:07: ioport range 0xad00-0xadfe has been reserved
[    1.563225] system 00:07: ioport range 0xae00-0xaefe has been reserved
[    1.563230] system 00:07: ioport range 0xaf00-0xaffe has been reserved
[    1.563234] system 00:07: iomem range 0xe0000000-0xefffffff has been reserved
[    1.563239] system 00:07: iomem range 0xfeda0000-0xfedacfff has been reserved
[    1.597965] AppArmor: AppArmor Filesystem Enabled
[    1.598014] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.598018] pci 0000:00:01.0:   IO window: disabled
[    1.598024] pci 0000:00:01.0:   MEM window: 0xdfc00000-0xdfcfffff
[    1.598028] pci 0000:00:01.0:   PREFETCH window: disabled
[    1.598033] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.598036] pci 0000:00:1c.0:   IO window: disabled
[    1.598042] pci 0000:00:1c.0:   MEM window: 0xdfb00000-0xdfbfffff
[    1.598047] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.598052] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    1.598057] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    1.598062] pci 0000:00:1e.0:   MEM window: disabled
[    1.598067] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.598080]   alloc irq_desc for 16 on node -1
[    1.598084]   alloc kstat_irqs on node -1
[    1.598092] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.598099] pci 0000:00:01.0: setting latency timer to 64
[    1.598109] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.598114] pci 0000:00:1c.0: setting latency timer to 64
[    1.598123] pci 0000:00:1e.0: setting latency timer to 64
[    1.598128] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.598132] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    1.598136] pci_bus 0000:01: resource 1 mem: [0xdfc00000-0xdfcfffff]
[    1.598140] pci_bus 0000:02: resource 1 mem: [0xdfb00000-0xdfbfffff]
[    1.598144] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    1.598147] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    1.598151] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    1.598201] NET: Registered protocol family 2
[    1.598353] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    1.598739] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    1.598812] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    1.598880] TCP: Hash tables configured (established 16384 bind 16384)
[    1.598883] TCP reno registered
[    1.598991] NET: Registered protocol family 1
[    1.599071] Trying to unpack rootfs image as initramfs...
[    1.846574] Freeing initrd memory: 7466k freed
[    1.851261] Simple Boot Flag at 0x7a set to 0x1
[    1.851482] cpufreq-nforce2: No nForce2 chipset.
[    1.851523] Scanning for low memory corruption every 60 seconds
[    1.851656] audit: initializing netlink socket (disabled)
[    1.851674] type=2000 audit(1257806692.848:1): initialized
[    1.861062] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.863061] VFS: Disk quotas dquot_6.5.2
[    1.863147] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.863925] fuse init (API version 7.12)
[    1.864054] msgmni has been set to 973
[    1.864355] alg: No test for stdrng (krng)
[    1.864375] io scheduler noop registered
[    1.864379] io scheduler anticipatory registered
[    1.864382] io scheduler deadline registered
[    1.864442] io scheduler cfq registered (default)
[    1.864460] pci 0000:00:02.0: Boot video device
[    1.864733]   alloc irq_desc for 24 on node -1
[    1.864736]   alloc kstat_irqs on node -1
[    1.864749] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    1.864758] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.864894]   alloc irq_desc for 25 on node -1
[    1.864897]   alloc kstat_irqs on node -1
[    1.864907] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    1.864918] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.865041] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.865125] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.865301] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.865306] ACPI: Power Button [PWRF]
[    1.865374] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.865382] ACPI: Power Button [VBTN]
[    1.866303] processor LNXCPU:00: registered as cooling_device0
[    1.866359] processor LNXCPU:01: registered as cooling_device1
[    1.938728] isapnp: Scanning for PnP cards...
[    2.292075] isapnp: No Plug & Play device found
[    2.293885] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.295621] brd: module loaded
[    2.296285] loop: module loaded
[    2.296393] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.296501] ahci 0000:00:1f.2: version 3.0
[    2.296517]   alloc irq_desc for 20 on node -1
[    2.296520]   alloc kstat_irqs on node -1
[    2.296529] ahci 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    2.296564]   alloc irq_desc for 26 on node -1
[    2.296567]   alloc kstat_irqs on node -1
[    2.296578] ahci 0000:00:1f.2: irq 26 for MSI/MSI-X
[    2.296671] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x33 impl RAID mode
[    2.296676] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    2.296682] ahci 0000:00:1f.2: setting latency timer to 64
[    2.320087] scsi0 : ahci
[    2.320227] scsi1 : ahci
[    2.320309] scsi2 : ahci
[    2.320390] scsi3 : ahci
[    2.320479] scsi4 : ahci
[    2.320559] scsi5 : ahci
[    2.320611] ata1: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970100 irq 26
[    2.320616] ata2: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970180 irq 26
[    2.320620] ata3: DUMMY
[    2.320622] ata4: DUMMY
[    2.320625] ata5: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970300 irq 26
[    2.320629] ata6: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970380 irq 26
[    2.321987] Fixed MDIO Bus: probed
[    2.322041] PPP generic driver version 2.4.2
[    2.322190] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.322217]   alloc irq_desc for 22 on node -1
[    2.322220]   alloc kstat_irqs on node -1
[    2.322228] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.322246] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.322251] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.322324] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.326233] ehci_hcd 0000:00:1a.7: debug port 1
[    2.326241] ehci_hcd 0000:00:1a.7: cache line size of 128 is not supported
[    2.326259] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xdfddac00
[    2.340011] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.340111] usb usb1: configuration #1 chosen from 1 choice
[    2.340154] hub 1-0:1.0: USB hub found
[    2.340164] hub 1-0:1.0: 4 ports detected
[    2.340236]   alloc irq_desc for 23 on node -1
[    2.340240]   alloc kstat_irqs on node -1
[    2.340246] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.340258] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.340263] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.340312] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.344209] ehci_hcd 0000:00:1d.7: debug port 1
[    2.344217] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.344235] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff980800
[    2.360011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.360105] usb usb2: configuration #1 chosen from 1 choice
[    2.360145] hub 2-0:1.0: USB hub found
[    2.360155] hub 2-0:1.0: 6 ports detected
[    2.360236] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.360262] uhci_hcd: USB Universal Host Controller Interface driver
[    2.360299] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.360309] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.360314] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.360358] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.360394] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
[    2.360502] usb usb3: configuration #1 chosen from 1 choice
[    2.360540] hub 3-0:1.0: USB hub found
[    2.360549] hub 3-0:1.0: 2 ports detected
[    2.360613]   alloc irq_desc for 17 on node -1
[    2.360617]   alloc kstat_irqs on node -1
[    2.360623] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.360631] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.360636] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.360681] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.360715] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000ff00
[    2.360823] usb usb4: configuration #1 chosen from 1 choice
[    2.360863] hub 4-0:1.0: USB hub found
[    2.360872] hub 4-0:1.0: 2 ports detected
[    2.360939] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.360948] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.360952] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.361000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.361025] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff80
[    2.361134] usb usb5: configuration #1 chosen from 1 choice
[    2.361173] hub 5-0:1.0: USB hub found
[    2.361181] hub 5-0:1.0: 2 ports detected
[    2.361243] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.361251] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.361255] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.361296] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.361322] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[    2.361419] usb usb6: configuration #1 chosen from 1 choice
[    2.361460] hub 6-0:1.0: USB hub found
[    2.361469] hub 6-0:1.0: 2 ports detected
[    2.361528]   alloc irq_desc for 18 on node -1
[    2.361531]   alloc kstat_irqs on node -1
[    2.361537] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.361545] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.361549] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.361591] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.361624] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    2.361722] usb usb7: configuration #1 chosen from 1 choice
[    2.361764] hub 7-0:1.0: USB hub found
[    2.361772] hub 7-0:1.0: 2 ports detected
[    2.361910] PNP: No PS/2 controller found. Probing ports directly.
[    2.364355] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.364365] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.364467] mice: PS/2 mouse device common for all mice
[    2.364611] rtc_cmos 00:05: RTC can wake from S4
[    2.364657] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.364685] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    2.364829] device-mapper: uevent: version 1.0.3
[    2.364954] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    2.365061] device-mapper: multipath: version 1.1.0 loaded
[    2.365065] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.365230] EISA: Probing bus 0 at eisa.0
[    2.365235] EISA: Cannot allocate resource for mainboard
[    2.365243] Cannot allocate resource for EISA slot 2
[    2.365254] Cannot allocate resource for EISA slot 5
[    2.365257] Cannot allocate resource for EISA slot 6
[    2.365268] EISA: Detected 0 cards.
[    2.365398] cpuidle: using governor ladder
[    2.365402] cpuidle: using governor menu
[    2.366125] TCP cubic registered
[    2.366314] NET: Registered protocol family 10
[    2.367007] lo: Disabled Privacy Extensions
[    2.367519] NET: Registered protocol family 17
[    2.367545] Bluetooth: L2CAP ver 2.13
[    2.367548] Bluetooth: L2CAP socket layer initialized
[    2.367552] Bluetooth: SCO (Voice Link) ver 0.6
[    2.367554] Bluetooth: SCO socket layer initialized
[    2.367602] Bluetooth: RFCOMM TTY layer initialized
[    2.367606] Bluetooth: RFCOMM socket layer initialized
[    2.367609] Bluetooth: RFCOMM ver 1.11
[    2.367657] Using IPI No-Shortcut mode
[    2.367747] PM: Resume from disk failed.
[    2.367763] registered taskstats version 1
[    2.367927]   Magic number: 1:725:754
[    2.368016] rtc_cmos 00:05: setting system clock to 2009-11-09 22:44:54 UTC (1257806694)
[    2.368021] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.368024] EDD information not available.
[    2.640268] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.648266] ata5: SATA link down (SStatus 0 SControl 300)
[    2.648286] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.648305] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.650432] ata2.00: ATAPI: HL-DT-STDVD-ROM GDRH10N, 0D04, max UDMA/100
[    2.653433] ata2.00: configured for UDMA/100
[    2.661327] ata6.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L02, max UDMA/100, ATAPI AN
[    2.672024] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4
[    2.672028] ata2: irq_stat 0x40000001
[    2.672036] ata2: hard resetting link
[    2.674711] ata6.00: configured for UDMA/100
[    2.686414] ata1.00: ATA-7: ST3808110AS, 3.ADJ, max UDMA/133
[    2.686419] ata1.00: 156250000 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.688018] ata6: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4
[    2.688021] ata6: irq_stat 0x40000001
[    2.688027] ata6: hard resetting link
[    2.744739] ata1.00: configured for UDMA/133
[    2.760157] scsi 0:0:0:0: Direct-Access     ATA      ST3808110AS      3.AD PQ: 0 ANSI: 5
[    2.760364] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.760431] sd 0:0:0:0: [sda] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.760506] sd 0:0:0:0: [sda] Write Protect is off
[    2.760510] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.760547] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.760743]  sda: sda1 sda2 < sda5 >
[    2.804546] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.968013] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    3.166658] usb 7-1: configuration #1 chosen from 1 choice
[    3.396020] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.401270] ata2.00: configured for UDMA/100
[    3.404220] ata2: EH complete
[    3.408014] usb 7-2: new low speed USB device using uhci_hcd and address 3
[    3.408196] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDRH10N  0D04 PQ: 0 ANSI: 5
[    3.412020] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.417287] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    3.417291] Uniform CD-ROM driver Revision: 3.20
[    3.417398] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.417461] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.438438] ata6.00: configured for UDMA/100
[    3.439083] ata6: EH complete
[    3.440220] scsi 5:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L02 PQ: 0 ANSI: 5
[    3.445929] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.446027] sr 5:0:0:0: Attached scsi CD-ROM sr1
[    3.446084] sr 5:0:0:0: Attached scsi generic sg2 type 5
[    3.446117] Freeing unused kernel memory: 540k freed
[    3.446493] Write protecting the kernel text: 4568k
[    3.446555] Write protecting the kernel read-only data: 1836k
[    3.618950] usb 7-2: configuration #1 chosen from 1 choice
[    3.630659] Linux agpgart interface v0.103
[    3.634631] agpgart-intel 0000:00:00.0: Intel 965G Chipset
[    3.635138] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    3.638358] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    3.640101] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    3.640108] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    3.640171]   alloc irq_desc for 21 on node -1
[    3.640175]   alloc kstat_irqs on node -1
[    3.640185] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.640195] e1000e 0000:00:19.0: pci_enable_pcie_error_reporting failed 0xfffffffb
[    3.640204] e1000e 0000:00:19.0: setting latency timer to 64
[    3.640478]   alloc irq_desc for 27 on node -1
[    3.640482]   alloc kstat_irqs on node -1
[    3.640494] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[    3.723472] [drm] Initialized drm 1.1.0 20060810
[    3.745721] usbcore: registered new interface driver hiddev
[    3.745845] usbcore: registered new interface driver usbhid
[    3.745850] usbhid: v2.6:USB HID core driver
[    3.758693] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:37:b6:ef
[    3.758699] 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
[    3.758725] 0000:00:19.0: eth0: MAC: 6, PHY: 7, PBA No: 1021ff-0ff
[    3.758777] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.758786] i915 0000:00:02.0: setting latency timer to 64
[    3.760764] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
[    3.760770] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    3.760999]   alloc irq_desc for 28 on node -1
[    3.761004]   alloc kstat_irqs on node -1
[    3.761018] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    3.763841] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input3
[    3.763959] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2/input0
[    3.795503] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    3.796346] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input4
[    3.796533] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2/input1
[    3.883166] [drm] fb0: inteldrmfb frame buffer device
[    3.883189] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.952572] [drm] DAC-6: set mode 1280x1024 18
[    3.977984] Console: switching to colour frame buffer device 160x64
[    4.289430] PM: Starting manual resume from disk
[    4.289437] PM: Resume from partition 8:5
[    4.289439] PM: Checking hibernation image.
[    4.289566] PM: Resume from disk failed.
[    4.334678] kjournald starting.  Commit interval 5 seconds
[    4.334693] EXT3-fs: mounted filesystem with writeback data mode.
[    5.011287] type=1505 audit(1257806697.140:2): operation="profile_load" pid=410 name=/sbin/dhclient3
[    5.012088] type=1505 audit(1257806697.144:3): operation="profile_load" pid=410 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.012521] type=1505 audit(1257806697.144:4): operation="profile_load" pid=410 name=/usr/lib/connman/scripts/dhclient-script
[    5.026827] type=1505 audit(1257806697.156:5): operation="profile_load" pid=412 name=/usr/lib/cups/backend/cups-pdf
[    5.027744] type=1505 audit(1257806697.156:6): operation="profile_load" pid=412 name=/usr/sbin/cupsd
[    5.046344] type=1505 audit(1257806697.176:7): operation="profile_load" pid=413 name=/usr/sbin/mysqld-akonadi
[    5.057021] type=1505 audit(1257806697.188:8): operation="profile_load" pid=414 name=/usr/sbin/tcpdump
[    6.379650] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k 
[    6.895011] EXT3 FS on sda1, internal journal
[    7.344434] udev: starting version 147
[    9.233737] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.349617] lp: driver loaded but no devices found
[    9.817368] dell-wmi: No known WMI GUID found
[   10.235969] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.645746] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[   10.645792] usbcore: registered new interface driver usblp
[   10.712601] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.712639] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.242402] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   11.262793] C-Media PCI 0000:03:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.432264] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   11.432378] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   11.432461] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   11.432542] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   11.432633] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   11.432713] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.432796] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   11.432877] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   26.412050] type=1505 audit(1257806718.544:9): operation="profile_replace" pid=846 name=/sbin/dhclient3
[   26.412842] type=1505 audit(1257806718.544:10): operation="profile_replace" pid=846 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   26.413273] type=1505 audit(1257806718.544:11): operation="profile_replace" pid=846 name=/usr/lib/connman/scripts/dhclient-script
[   26.417199] type=1505 audit(1257806718.548:12): operation="profile_replace" pid=848 name=/usr/lib/cups/backend/cups-pdf
[   26.418118] type=1505 audit(1257806718.548:13): operation="profile_replace" pid=848 name=/usr/sbin/cupsd
[   26.421169] type=1505 audit(1257806718.552:14): operation="profile_replace" pid=849 name=/usr/sbin/mysqld-akonadi
[   26.423803] type=1505 audit(1257806718.552:15): operation="profile_replace" pid=852 name=/usr/sbin/tcpdump
[   28.118188] ppdev: user-space parallel port driver
[   28.156279] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[   28.212064] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[   28.212185] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by abooks on 2009-11-09
OK here's the latest: On a hunch I googled Linux cd programs, found one called ksCD, downloaded it, and it worked! still don't know if I need to unmount, and haven't tried thumb drives yet. We're making progress, though.

---

