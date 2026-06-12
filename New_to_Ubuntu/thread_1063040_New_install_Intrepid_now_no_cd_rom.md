---
title: "New install Intrepid now no cd rom"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Captaingracekidd on 2009-02-07
Recently installed Intrepid from live disc and did all the updates. The cd-rom doesnt exist. Help.

Code:

 sudo lshw -class disk
  *-disk                  
       description: ATA Disk
       product: TOSHIBA MK3252GS
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: LV01
       serial: 585FF2RLS
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=5eb0aa6b

Shows no cd rom.

Code:

ls -al /media
total 12
drwxr-xr-x  3 root root 4096 2008-10-29 20:53 .
drwxr-xr-x 22 root root 4096 2009-01-31 12:51 ..
lrwxrwxrwx  1 root root    6 2009-01-30 18:07 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-01-30 18:07 cdrom0

/etc/fstab states:

Code:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

It seems my machine has no idea I even have a cd rom. When inserting cds and dvds the cd rom spins them but nothing else happens.

---

### Post by taurus on 2009-02-07
Look in /var/log/messages to see if your CD/DVD even lists in there.

```
sudo more /var/log/messages
```
Hit the space bar for the next 24 lines.

p.s.  What types of CD/DVD have you tried to insert into the drive so far?

---

### Post by Captaingracekidd on 2009-02-08
I cannot see any text indicating a cd rom

heres what I get:

```
Feb  7 19:27:04 pi -- MARK --
Feb  7 19:47:04 pi -- MARK --
Feb  7 20:07:04 pi -- MARK --
Feb  7 20:27:04 pi -- MARK --
Feb  7 20:47:04 pi -- MARK --
Feb  7 21:07:04 pi -- MARK --
Feb  7 21:27:04 pi -- MARK --
Feb  7 21:47:04 pi -- MARK --
Feb  7 22:07:04 pi -- MARK --
Feb  7 22:27:04 pi -- MARK --
Feb  7 22:47:04 pi -- MARK --
Feb  7 23:07:04 pi -- MARK --
Feb  7 23:27:04 pi -- MARK --
Feb  7 23:47:04 pi -- MARK --
Feb  8 00:07:04 pi -- MARK --
Feb  8 00:27:04 pi -- MARK --
Feb  8 00:47:04 pi -- MARK --
Feb  8 01:07:04 pi -- MARK --
Feb  8 01:27:04 pi -- MARK --
Feb  8 01:47:04 pi -- MARK --
Feb  8 02:07:04 pi -- MARK --
Feb  8 02:27:04 pi -- MARK --
Feb  8 02:47:04 pi -- MARK --
Feb  8 03:07:04 pi -- MARK --
Feb  8 03:27:04 pi -- MARK --
Feb  8 03:47:04 pi -- MARK --
Feb  8 04:07:04 pi -- MARK --
Feb  8 04:27:04 pi -- MARK --
Feb  8 04:47:04 pi -- MARK --
Feb  8 05:07:04 pi -- MARK --
Feb  8 05:27:04 pi -- MARK --
Feb  8 05:47:04 pi -- MARK --
Feb  8 06:07:04 pi -- MARK --
Feb  8 06:27:04 pi -- MARK --
Feb  8 06:47:04 pi -- MARK --
Feb  8 07:07:04 pi -- MARK --
Feb  8 07:27:04 pi -- MARK --
Feb  8 07:47:04 pi -- MARK --
Feb  8 08:07:04 pi -- MARK --
Feb  8 08:21:24 pi syslogd 1.5.0#2ubuntu6: restart.
Feb  8 08:47:04 pi -- MARK --
Feb  8 09:07:04 pi -- MARK --
Feb  8 09:27:04 pi -- MARK --
Feb  8 09:47:04 pi -- MARK --
Feb  8 10:07:04 pi -- MARK --
Feb  8 10:27:04 pi -- MARK --
Feb  8 10:47:04 pi -- MARK --
Feb  8 11:03:21 pi kernel: [88595.872275] CE: hpet increasing min_delta_ns to 11
3904 nsec
Feb  8 15:19:22 pi syslogd 1.5.0#2ubuntu6: restart.
Feb  8 15:19:22 pi kernel: Inspecting /boot/System.map-2.6.27-7-generic
Feb  8 15:19:22 pi kernel: Cannot find map file.
Feb  8 15:19:22 pi kernel: Loaded 54432 symbols from 102 modules.
Feb  8 15:19:22 pi kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  8 15:19:22 pi kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  8 15:19:22 pi kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd
@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20
 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
Feb  8 15:19:22 pi kernel: [    0.000000] BIOS-provided physical RAM map:
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000
00009f800 (usable)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 0000000
0000a0000 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 0000000
0000d4000 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000
000100000 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000
07f670000 (usable)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 000000007f670000 - 0000000
07f680000 (ACPI NVS)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 000000007f680000 - 0000000
080000000 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 0000000
0f0000000 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000
0fec10000 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 0000000
0fed00400 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 0000000
0fed1a000 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 0000000
0fed90000 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 0000000
0fee01000 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000
100000000 (reserved)
Feb  8 15:19:22 pi kernel: [    0.000000] last_pfn = 0x7f670 max_arch_pfn = 0x10
0000
Feb  8 15:19:22 pi kernel: [    0.000000] RAMDISK: 3781e000 - 37fefea0
Feb  8 15:19:22 pi kernel: [    0.000000] DMI present.
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: RSDP 000F74E0, 0024 (r2 PTLTD )
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: XSDT 7F676EE3, 0094 (r1 PTLTD  ^
I XSDT    6040000  LTP        0)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: FACP 7F67ECDD, 00F4 (r3 INTEL  C
RESTLNE  6040000 ALAN        1)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: DSDT 7F678CBE, 5FAB (r2 INTEL  C
RESTLNE  6040000 INTL 20050624)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: FACS 7F67FFC0, 0040
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: APIC 7F67EDD1, 0068 (r1 INTEL  C
RESTLNE  6040000 LOHR       5A)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: HPET 7F67EE39, 0038 (r1 INTEL  C
RESTLNE  6040000 LOHR       5A)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: MCFG 7F67EE71, 003C (r1 INTEL  C
RESTLNE  6040000 LOHR       5A)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: TCPA 7F67EEAD, 0032 (r1 Intel   
CRESTLN  6040000          5A52)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: TMOR 7F67EEDF, 0026 (r1 PTLTD   
         6040000 PTL         3)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: ASF! 7F67EF05, 006B (r32 OEMID  
OEMTBL    6040000 PTL         1)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: APIC 7F67EF70, 0068 (r1 PTLTD  ^
I APIC    6040000  LTP        0)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: BOOT 7F67EFD8, 0028 (r1 PTLTD  $
SBFTBL$  6040000  LTP        1)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: SSDT 7F67866F, 064F (r1 SataRe  
SataPri     1000 INTL 20050624)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: SSDT 7F677FD3, 069C (r1 SataRe  
SataSec     1000 INTL 20050624)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: SSDT 7F677503, 025F (r1  PmRef  
Cpu0Tst     3000 INTL 20050624)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: SSDT 7F67745D, 00A6 (r1  PmRef  
Cpu1Tst     3000 INTL 20050624)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: SSDT 7F676F77, 04E6 (r1  PmRef  
  CpuPm     3000 INTL 20050624)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT fou
nd, using 0
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works 
better, notify linux-acpi@vger.kernel.org
Feb  8 15:19:22 pi kernel: [    0.000000] 1142MB HIGHMEM available.
Feb  8 15:19:22 pi kernel: [    0.000000] 896MB LOWMEM available.
Feb  8 15:19:22 pi kernel: [    0.000000]   mapped low ram: 0 - 38000000
Feb  8 15:19:22 pi kernel: [    0.000000]   low ram: 00000000 - 38000000
Feb  8 15:19:22 pi kernel: [    0.000000]   bootmap 00008000 - 0000f000
Feb  8 15:19:22 pi kernel: [    0.000000] (9 early reservations) ==> bootmem [00
00000000 - 0038000000]
Feb  8 15:19:22 pi kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS 
data page ==> [0000000000 - 0000001000]
Feb  8 15:19:22 pi kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX T
RAMPOLINE ==> [0000001000 - 0000002000]
Feb  8 15:19:22 pi kernel: [    0.000000]   #2 [0000006000 - 0000007000]       T
RAMPOLINE ==> [0000006000 - 0000007000]
Feb  8 15:19:22 pi kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT
 DATA BSS ==> [0000100000 - 00005c0a20]
Feb  8 15:19:22 pi kernel: [    0.000000]   #4 [003781e000 - 0037fefea0]        
  RAMDISK ==> [003781e000 - 0037fefea0]
Feb  8 15:19:22 pi kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT
_PG_TABLE ==> [00005c1000 - 00005c4000]
Feb  8 15:19:22 pi kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS
 reserved ==> [000009f800 - 0000100000]
Feb  8 15:19:22 pi kernel: [    0.000000]   #7 [0000007000 - 0000008000]        
  PGTABLE ==> [0000007000 - 0000008000]
Feb  8 15:19:22 pi kernel: [    0.000000]   #8 [0000008000 - 000000f000]        
  BOOTMAP ==> [0000008000 - 000000f000]
Feb  8 15:19:22 pi kernel: [    0.000000] found SMP MP-table at [c00f7510] 000f7
510
Feb  8 15:19:22 pi kernel: [    0.000000] Zone PFN ranges:
Feb  8 15:19:22 pi kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Feb  8 15:19:22 pi kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Feb  8 15:19:22 pi kernel: [    0.000000]   HighMem  0x00038000 -> 0x0007f670
Feb  8 15:19:22 pi kernel: [    0.000000] Movable zone start PFN for each node
Feb  8 15:19:22 pi kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb  8 15:19:22 pi kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Feb  8 15:19:22 pi kernel: [    0.000000]     0: 0x00000100 -> 0x0007f670
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x
00] enabled)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x
01] enabled)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high ed
ge lint[0x1])
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high ed
ge lint[0x1])
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00
000] gsi_base[0])
Feb  8 15:19:22 pi kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, addr
ess 0xfec00000, GSI 0-23
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 glo
bal_irq 2 dfl dfl)
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 glo
bal_irq 9 high level)
Feb  8 15:19:22 pi kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/
O APICs
Feb  8 15:19:22 pi kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed0
0000
Feb  8 15:19:22 pi kernel: [    0.000000] Using ACPI (MADT) for SMP configuratio
n information
Feb  8 15:19:22 pi kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Feb  8 15:19:22 pi kernel: [    0.000000] PM: Registered nosave memory: 00000000
0009f000 - 00000000000a0000
Feb  8 15:19:22 pi kernel: [    0.000000] PM: Registered nosave memory: 00000000
000a0000 - 00000000000d2000
Feb  8 15:19:22 pi kernel: [    0.000000] PM: Registered nosave memory: 00000000
000d2000 - 00000000000d4000
Feb  8 15:19:22 pi kernel: [    0.000000] PM: Registered nosave memory: 00000000
000d4000 - 00000000000dc000
Feb  8 15:19:22 pi kernel: [    0.000000] PM: Registered nosave memory: 00000000
000dc000 - 0000000000100000
Feb  8 15:19:22 pi kernel: [    0.000000] Allocating PCI resources starting at 8
8000000 (gap: 80000000:60000000)
Feb  8 15:19:22 pi kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per 
cpu data
Feb  8 15:19:22 pi kernel: [    0.000000] Built 1 zonelists in Zone order, mobil
ity grouping on.  Total pages: 517156
Feb  8 15:19:22 pi kernel: [    0.000000] Kernel command line: root=UUID=70909c1
f-66da-43b7-9e0e-122bffb7586b ro quiet splash 
Feb  8 15:19:22 pi kernel: [    0.000000] Enabling fast FPU save and restore... 
done.
Feb  8 15:19:22 pi kernel: [    0.000000] Enabling unmasked SIMD FPU exception s
upport... done.
Feb  8 15:19:22 pi kernel: [    0.000000] Initializing CPU#0
Feb  8 15:19:22 pi kernel: [    0.000000] PID hash table entries: 4096 (order: 1
2, 16384 bytes)
Feb  8 15:19:22 pi kernel: [    0.000000] Extended CMOS year: 2000
Feb  8 15:19:22 pi kernel: [    0.000000] TSC: PIT calibration confirmed by PMTI
MER.
Feb  8 15:19:22 pi kernel: [    0.000000] TSC: using PIT calibration value
Feb  8 15:19:22 pi kernel: [    0.000000] Detected 1994.973 MHz processor.
Feb  8 15:19:22 pi kernel: [    0.004000] Console: colour VGA+ 80x25
Feb  8 15:19:22 pi kernel: [    0.004000] console [tty0] enabled
Feb  8 15:19:22 pi kernel: [    0.004000] Dentry cache hash table entries: 13107
2 (order: 7, 524288 bytes)
Feb  8 15:19:22 pi kernel: [    0.004000] Inode-cache hash table entries: 65536 
(order: 6, 262144 bytes)
Feb  8 15:19:22 pi kernel: [    0.004000] Memory: 2053876k/2087360k available (2
572k kernel code, 32196k reserved, 1160k data, 424k init, 1169856k highmem)
Feb  8 15:19:22 pi kernel: [    0.004000] virtual kernel memory layout:
Feb  8 15:19:22 pi kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000 
  (3616 kB)
Feb  8 15:19:22 pi kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000 
  (4096 kB)
Feb  8 15:19:22 pi kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000 
  ( 107 MB)
Feb  8 15:19:22 pi kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000 
  ( 896 MB)
Feb  8 15:19:22 pi kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000 
  ( 424 kB)
Feb  8 15:19:22 pi kernel: [    0.004000]       .data : 0xc03832aa - 0xc04a5680 
  (1160 kB)
Feb  8 15:19:22 pi kernel: [    0.004000]       .text : 0xc0100000 - 0xc03832aa 
  (2572 kB)
Feb  8 15:19:22 pi kernel: [    0.004000] Checking if this processor honours the
 WP bit even in supervisor mode...Ok.
Feb  8 15:19:22 pi kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0
-3, MinObjects=0, CPUs=2, Nodes=1
Feb  8 15:19:22 pi kernel: [    0.004000] Calibrating delay loop (skipped), valu
e calculated using timer frequency.. 3989.94 BogoMIPS (lpj=7979892)
Feb  8 15:19:22 pi kernel: [    0.004000] Security Framework initialized
Feb  8 15:19:22 pi kernel: [    0.004000] SELinux:  Disabled at boot.
Feb  8 15:19:22 pi kernel: [    0.004000] AppArmor: AppArmor initialized
Feb  8 15:19:22 pi kernel: [    0.004000] Mount-cache hash table entries: 512
Feb  8 15:19:22 pi kernel: [    0.004000] Initializing cgroup subsys ns
Feb  8 15:19:22 pi kernel: [    0.004000] Initializing cgroup subsys cpuacct
Feb  8 15:19:22 pi kernel: [    0.004000] Initializing cgroup subsys memory
Feb  8 15:19:22 pi kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  8 15:19:22 pi kernel: [    0.004000] CPU: L2 cache: 2048K
Feb  8 15:19:22 pi kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  8 15:19:22 pi kernel: [    0.004000] CPU: Processor Core ID: 0
Feb  8 15:19:22 pi kernel: [    0.004000] using mwait in idle threads.
Feb  8 15:19:22 pi kernel: [    0.004000] Checking 'hlt' instruction... OK.
Feb  8 15:19:22 pi kernel: [    0.017691] ACPI: Core revision 20080609
Feb  8 15:19:22 pi kernel: [    0.019701] ACPI: Checking initramfs for custom DS
DT
Feb  8 15:19:22 pi kernel: [    0.328262] ENABLING IO-APIC IRQs
Feb  8 15:19:22 pi kernel: [    0.328471] ..TIMER: vector=0x31 apic1=0 pin1=2 ap
ic2=-1 pin2=-1
Feb  8 15:19:22 pi kernel: [    0.369149] CPU0: Intel(R) Core(TM)2 Duo CPU     T
7250  @ 2.00GHz stepping 0d
Feb  8 15:19:22 pi kernel: [    0.372023] Booting processor 1/1 ip 6000
Feb  8 15:19:22 pi kernel: [    0.004000] Initializing CPU#1
Feb  8 15:19:22 pi kernel: [    0.004000] Calibrating delay using timer specific
 routine.. 3989.97 BogoMIPS (lpj=7979948)
Feb  8 15:19:22 pi kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  8 15:19:22 pi kernel: [    0.004000] CPU: L2 cache: 2048K
Feb  8 15:19:22 pi kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  8 15:19:22 pi kernel: [    0.004000] CPU: Processor Core ID: 1
Feb  8 15:19:22 pi kernel: [    0.456498] CPU1: Intel(R) Core(TM)2 Duo CPU     T
7250  @ 2.00GHz stepping 0d
Feb  8 15:19:22 pi kernel: [    0.456516] checking TSC synchronization [CPU#0 ->
 CPU#1]: passed.
Feb  8 15:19:22 pi kernel: [    0.460049] Brought up 2 CPUs
Feb  8 15:19:22 pi kernel: [    0.460052] Total of 2 processors activated (7979.
92 BogoMIPS).
Feb  8 15:19:22 pi kernel: [    0.460168] net_namespace: 840 bytes
Feb  8 15:19:22 pi kernel: [    0.460168] Booting paravirtualized kernel on bare
 hardware
Feb  8 15:19:22 pi kernel: [    0.460291] Time: 17:18:54  Date: 02/08/09
Feb  8 15:19:22 pi kernel: [    0.460318] NET: Registered protocol family 16
Feb  8 15:19:22 pi kernel: [    0.460337] EISA bus registered
Feb  8 15:19:22 pi kernel: [    0.460337] ACPI: bus type pci registered
Feb  8 15:19:22 pi kernel: [    0.460337] PCI: MCFG configuration 0: base e00000
00 segment 0 buses 0 - 255
Feb  8 15:19:22 pi kernel: [    0.460337] PCI: MCFG area at e0000000 reserved in
 E820
Feb  8 15:19:22 pi kernel: [    0.460337] PCI: Using MMCONFIG for extended confi
g space
Feb  8 15:19:22 pi kernel: [    0.460337] PCI: Using configuration type 1 for ba
se access
Feb  8 15:19:22 pi kernel: [    0.464659] ACPI Error (evregion-0315): No handler
 for Region [ERAM] (f7417168) [EmbeddedControl] [20080609]
Feb  8 15:19:22 pi kernel: [    0.464665] ACPI Error (exfldio-0291): Region Embe
ddedControl(3) has no handler [20080609]
Feb  8 15:19:22 pi kernel: [    0.464670] ACPI Error (psparse-0530): Method pars
e/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node f7416be8), AE_NOT_EXIST
Feb  8 15:19:22 pi kernel: [    0.466949] ACPI: BIOS _OSI(Linux) query ignored
Feb  8 15:19:22 pi kernel: [    0.466952] ACPI: DMI System Vendor: Zepto
Feb  8 15:19:22 pi kernel: [    0.466953] ACPI: DMI Product Name: Znote
Feb  8 15:19:22 pi kernel: [    0.466955] ACPI: DMI Product Version: 6025WD
Feb  8 15:19:22 pi kernel: [    0.466957] ACPI: DMI Board Name: Znote
Feb  8 15:19:22 pi kernel: [    0.466959] ACPI: DMI BIOS Vendor: Phoenix Technol
ogies LTD
Feb  8 15:19:22 pi kernel: [    0.466961] ACPI: DMI BIOS Date: 09/12/2007
Feb  8 15:19:22 pi kernel: [    0.466963] ACPI: Please send DMI info above to li
nux-acpi@vger.kernel.org
Feb  8 15:19:22 pi kernel: [    0.466965] ACPI: If "acpi_osi=Linux" works better
, please notify linux-acpi@vger.kernel.org
Feb  8 15:19:22 pi kernel: [    1.468302] ACPI: Interpreter enabled
Feb  8 15:19:22 pi kernel: [    1.468305] ACPI: (supports S0 S3 S4 S5)
Feb  8 15:19:22 pi kernel: [    1.468320] ACPI: Using IOAPIC for interrupt routi
ng
Feb  8 15:19:22 pi kernel: [    1.468377] ACPI: EC: non-query interrupt received
, switching to interrupt mode
Feb  8 15:19:22 pi kernel: [    1.608928] ACPI: EC: GPE = 0x17, I/O: command/sta
tus = 0x66, data = 0x62
Feb  8 15:19:22 pi kernel: [    1.608928] ACPI: EC: driver started in poll mode
Feb  8 15:19:22 pi kernel: [    1.612049] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb  8 15:19:22 pi kernel: [    1.612533] pci 0000:00:1a.7: PME# supported from 
D0 D3hot D3cold
Feb  8 15:19:22 pi kernel: [    1.612540] pci 0000:00:1a.7: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.612765] pci 0000:00:1b.0: PME# supported from 
D0 D3hot D3cold
Feb  8 15:19:22 pi kernel: [    1.612775] pci 0000:00:1b.0: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.612933] pci 0000:00:1c.0: PME# supported from 
D0 D3hot D3cold
Feb  8 15:19:22 pi kernel: [    1.612943] pci 0000:00:1c.0: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.613101] pci 0000:00:1c.1: PME# supported from 
D0 D3hot D3cold
Feb  8 15:19:22 pi kernel: [    1.613110] pci 0000:00:1c.1: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.613259] pci 0000:00:1c.2: PME# supported from 
D0 D3hot D3cold
Feb  8 15:19:22 pi kernel: [    1.613269] pci 0000:00:1c.2: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.613434] pci 0000:00:1c.3: PME# supported from 
D0 D3hot D3cold
Feb  8 15:19:22 pi kernel: [    1.613444] pci 0000:00:1c.3: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.614127] pci 0000:00:1d.7: PME# supported from 
D0 D3hot D3cold
Feb  8 15:19:22 pi kernel: [    1.614137] pci 0000:00:1d.7: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.614449] pci 0000:00:1f.0: quirk: region 1000-1
07f claimed by ICH6 ACPI/GPIO/TCO
Feb  8 15:19:22 pi kernel: [    1.614456] pci 0000:00:1f.0: quirk: region 1180-1
1bf claimed by ICH6 GPIO
Feb  8 15:19:22 pi kernel: [    1.614843] pci 0000:00:1f.2: PME# supported from 
D3hot
Feb  8 15:19:22 pi kernel: [    1.614853] pci 0000:00:1f.2: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.615261] pci 0000:02:00.0: PME# supported from 
D0 D3hot D3cold
Feb  8 15:19:22 pi kernel: [    1.615276] pci 0000:02:00.0: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.616191] pci 0000:05:00.0: PME# supported from 
D3hot D3cold
Feb  8 15:19:22 pi kernel: [    1.616206] pci 0000:05:00.0: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.616505] pci 0000:06:06.0: PME# supported from 
D0 D1 D2 D3hot D3cold
Feb  8 15:19:22 pi kernel: [    1.616514] pci 0000:06:06.0: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.616720] pci 0000:06:06.1: PME# supported from 
D0 D1 D2 D3hot
Feb  8 15:19:22 pi kernel: [    1.616730] pci 0000:06:06.1: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.616929] pci 0000:06:06.2: PME# supported from 
D0 D1 D2 D3hot
Feb  8 15:19:22 pi kernel: [    1.616939] pci 0000:06:06.2: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.617147] pci 0000:06:06.3: PME# supported from 
D0 D1 D2 D3hot
Feb  8 15:19:22 pi kernel: [    1.617156] pci 0000:06:06.3: PME# disabled
Feb  8 15:19:22 pi kernel: [    1.617262] pci 0000:00:1e.0: transparent bridge
Feb  8 15:19:22 pi kernel: [    1.632142] ACPI: PCI Interrupt Link [LNKA] (IRQs 
1 3 4 5 6 7 10 12 14 15) *11
Feb  8 15:19:22 pi kernel: [    1.632275] ACPI: PCI Interrupt Link [LNKB] (IRQs 
1 3 4 5 6 7 *11 12 14 15)
Feb  8 15:19:22 pi kernel: [    1.632405] ACPI: PCI Interrupt Link [LNKC] (IRQs 
1 3 4 5 6 7 *10 12 14 15)
Feb  8 15:19:22 pi kernel: [    1.632534] ACPI: PCI Interrupt Link [LNKD] (IRQs 
1 3 4 5 6 7 11 12 14 15) *10
Feb  8 15:19:22 pi kernel: [    1.632663] ACPI: PCI Interrupt Link [LNKE] (IRQs 
1 3 4 5 6 7 10 12 14 15) *0, disabled.
Feb  8 15:19:22 pi kernel: [    1.632790] ACPI: PCI Interrupt Link [LNKF] (IRQs 
1 3 4 5 6 *7 11 12 14 15)
Feb  8 15:19:22 pi kernel: [    1.632919] ACPI: PCI Interrupt Link [LNKG] (IRQs 
1 3 4 5 6 7 *10 12 14 15)
Feb  8 15:19:22 pi kernel: [    1.633047] ACPI: PCI Interrupt Link [LNKH] (IRQs 
1 3 4 5 6 7 *11 12 14 15)
Feb  8 15:19:22 pi kernel: [    1.633138] ACPI: Power Resource [FN00] (off)
Feb  8 15:19:22 pi kernel: [    1.633138] ACPI: EC: non-query interrupt received
, switching to interrupt mode
Feb  8 15:19:22 pi kernel: [    1.633138] Linux Plug and Play Support v0.97 (c) 
Adam Belay
Feb  8 15:19:22 pi kernel: [    1.633138] ACPI: EC: non-query interrupt received
, switching to interrupt mode
Feb  8 15:19:22 pi kernel: [    1.633138] pnp: PnP ACPI init
Feb  8 15:19:22 pi kernel: [    1.633138] ACPI: bus type pnp registered
Feb  8 15:19:22 pi kernel: [    2.512830] ACPI: EC: non-query interrupt received
, switching to interrupt mode
Feb  8 15:19:22 pi kernel: [    2.516869] pnp: PnP ACPI: found 15 devices
Feb  8 15:19:22 pi kernel: [    2.516869] ACPI: ACPI bus type pnp unregistered
Feb  8 15:19:22 pi kernel: [    2.516869] PnPBIOS: Disabled by ACPI PNP
Feb  8 15:19:22 pi kernel: [    2.516869] PCI: Using ACPI for IRQ routing
Feb  8 15:19:22 pi kernel: [    2.520042] NET: Registered protocol family 8
Feb  8 15:19:22 pi kernel: [    2.520045] NET: Registered protocol family 20
Feb  8 15:19:22 pi kernel: [    2.520068] NetLabel: Initializing
Feb  8 15:19:22 pi kernel: [    2.520068] NetLabel:  domain hash size = 128
Feb  8 15:19:22 pi kernel: [    2.520068] NetLabel:  protocols = UNLABELED CIPSO
v4
Feb  8 15:19:22 pi kernel: [    2.520068] NetLabel:  unlabeled traffic allowed b
y default
Feb  8 15:19:22 pi kernel: [    2.520068] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 
0
Feb  8 15:19:22 pi kernel: [    2.520068] hpet0: 3 64-bit timers, 14318180 Hz
Feb  8 15:19:22 pi kernel: [    2.521540] tracer: 772 pages allocated for 65536 
entries of 48 bytes
Feb  8 15:19:22 pi kernel: [    2.521543]    actual entries 65620
Feb  8 15:19:22 pi kernel: [    2.521634] AppArmor: AppArmor Filesystem Enabled
Feb  8 15:19:22 pi kernel: [    2.521667] ACPI: RTC can wake from S4
Feb  8 15:19:22 pi kernel: [    2.524562] system 00:01: iomem range 0xfed1c000-0
xfed1ffff could not be reserved
Feb  8 15:19:22 pi kernel: [    2.524566] system 00:01: iomem range 0xfed14000-0
xfed17fff could not be reserved
Feb  8 15:19:22 pi kernel: [    2.524569] system 00:01: iomem range 0xfed18000-0
xfed18fff could not be reserved
Feb  8 15:19:22 pi kernel: [    2.524572] system 00:01: iomem range 0xfed19000-0
xfed19fff could not be reserved
Feb  8 15:19:22 pi kernel: [    2.524575] system 00:01: iomem range 0xe0000000-0
xefffffff could not be reserved
Feb  8 15:19:22 pi kernel: [    2.524578] system 00:01: iomem range 0xfed20000-0
xfed3ffff could not be reserved
Feb  8 15:19:22 pi kernel: [    2.524581] system 00:01: iomem range 0xfed45000-0
xfed8ffff could not be reserved
Feb  8 15:19:22 pi kernel: [    2.524590] system 00:04: iomem range 0xfed00000-0
xfed003ff could not be reserved
Feb  8 15:19:22 pi kernel: [    2.524597] system 00:06: ioport range 0x680-0x69f
 has been reserved
Feb  8 15:19:22 pi kernel: [    2.524600] system 00:06: ioport range 0x800-0x80f
 has been reserved
Feb  8 15:19:22 pi kernel: [    2.524603] system 00:06: ioport range 0x1000-0x10
7f has been reserved
Feb  8 15:19:22 pi kernel: [    2.524606] system 00:06: ioport range 0x1180-0x11
bf has been reserved
Feb  8 15:19:22 pi kernel: [    2.524609] system 00:06: ioport range 0x1640-0x16
4f has been reserved
Feb  8 15:19:22 pi kernel: [    2.524612] system 00:06: ioport range 0xfe00-0xfe
00 has been reserved
Feb  8 15:19:22 pi kernel: [    2.559782] pci 0000:00:1c.0: PCI bridge, secondar
y bus 0000:02
Feb  8 15:19:22 pi kernel: [    2.559788] pci 0000:00:1c.0:   IO window: 0x2000-
0x2fff
Feb  8 15:19:22 pi kernel: [    2.559802] pci 0000:00:1c.0:   MEM window: 0xf000
0000-0xf0ffffff
Feb  8 15:19:22 pi kernel: [    2.559809] pci 0000:00:1c.0:   PREFETCH window: d
isabled
Feb  8 15:19:22 pi kernel: [    2.559824] pci 0000:00:1c.1: PCI bridge, secondar
y bus 0000:03
Feb  8 15:19:22 pi kernel: [    2.559830] pci 0000:00:1c.1:   IO window: 0x3000-
0x3fff
Feb  8 15:19:22 pi kernel: [    2.559843] pci 0000:00:1c.1:   MEM window: 0xf100
0000-0xf1ffffff
Feb  8 15:19:22 pi kernel: [    2.559850] pci 0000:00:1c.1:   PREFETCH window: d
isabled
Feb  8 15:19:22 pi kernel: [    2.559867] pci 0000:00:1c.2: PCI bridge, secondar
y bus 0000:04
Feb  8 15:19:22 pi kernel: [    2.559873] pci 0000:00:1c.2:   IO window: 0x4000-
0x4fff
Feb  8 15:19:22 pi kernel: [    2.559884] pci 0000:00:1c.2:   MEM window: 0xf200
0000-0xf2ffffff
Feb  8 15:19:22 pi kernel: [    2.559891] pci 0000:00:1c.2:   PREFETCH window: d
isabled
Feb  8 15:19:22 pi kernel: [    2.559906] pci 0000:00:1c.3: PCI bridge, secondar
y bus 0000:05
Feb  8 15:19:22 pi kernel: [    2.559912] pci 0000:00:1c.3:   IO window: 0x5000-
0x5fff
Feb  8 15:19:22 pi kernel: [    2.559923] pci 0000:00:1c.3:   MEM window: 0xf300
0000-0xf3ffffff
Feb  8 15:19:22 pi kernel: [    2.559932] pci 0000:00:1c.3:   PREFETCH window: d
isabled
Feb  8 15:19:22 pi kernel: [    2.559951] pci 0000:06:06.0: CardBus bridge, seco
ndary bus 0000:07
Feb  8 15:19:22 pi kernel: [    2.559953] pci 0000:06:06.0:   IO window: 0x00600
0-0x0060ff
Feb  8 15:19:22 pi kernel: [    2.559963] pci 0000:06:06.0:   IO window: 0x00640
0-0x0064ff
Feb  8 15:19:22 pi kernel: [    2.559972] pci 0000:06:06.0:   PREFETCH window: 0
x88000000-0x8bffffff
Feb  8 15:19:22 pi kernel: [    2.559980] pci 0000:06:06.0:   MEM window: 0x9000
0000-0x93ffffff
Feb  8 15:19:22 pi kernel: [    2.559989] pci 0000:00:1e.0: PCI bridge, secondar
y bus 0000:06
Feb  8 15:19:22 pi kernel: [    2.559995] pci 0000:00:1e.0:   IO window: 0x6000-
0x6fff
Feb  8 15:19:22 pi kernel: [    2.560007] pci 0000:00:1e.0:   MEM window: 0xf420
0000-0xf42fffff
Feb  8 15:19:22 pi kernel: [    2.560014] pci 0000:00:1e.0:   PREFETCH window: 0
x00000088000000-0x0000008bffffff
Feb  8 15:19:22 pi kernel: [    2.560042] pci 0000:00:1c.0: PCI INT A -> GSI 17 
(level, low) -> IRQ 17
Feb  8 15:19:22 pi kernel: [    2.560069] pci 0000:00:1c.1: PCI INT B -> GSI 16 
(level, low) -> IRQ 16
Feb  8 15:19:22 pi kernel: [    2.560095] pci 0000:00:1c.2: PCI INT C -> GSI 18 
(level, low) -> IRQ 18
Feb  8 15:19:22 pi kernel: [    2.560121] pci 0000:00:1c.3: PCI INT D -> GSI 19 
(level, low) -> IRQ 19
Feb  8 15:19:22 pi kernel: [    2.560164] pci 0000:06:06.0: PCI INT A -> GSI 18 
(level, low) -> IRQ 18
Feb  8 15:19:22 pi kernel: [    2.560175] bus: 00 index 0 io port: [0, ffff]
Feb  8 15:19:22 pi kernel: [    2.560177] bus: 00 index 1 mmio: [0, ffffffff]
Feb  8 15:19:22 pi kernel: [    2.560179] bus: 02 index 0 io port: [2000, 2fff]

```

:S

---

