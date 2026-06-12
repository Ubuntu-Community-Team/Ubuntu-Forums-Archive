---
title: "Internet doesn't work."
date: 2009-06-04
forum: New to Ubuntu
---

### Post by ubuntuforums on 2009-06-04
Hi, so I formatted my parents computer, and did a fresh install of Windows XP SP3, and Ubuntu 9.04. Everything went well with both installations. But the internet doesn't connect on the Ubuntu install. It's a wired connection hooked directly to the computer. The internet works fine on the Windows partition, no configuration was done, it was automatically detected and enabled.

I tried formatting the Ubuntu partition and installing 8.10 in it's place, same problem.

This is an older computer, the driver that's being used on the Windows set up is: SiS 900-Based PCI Fast Ethernet Adapter

I guess it's detected in the Ubuntu install since it does show an eth0 connection, but it doesn't actually connect. I haven't used Ubuntu as a desktop OS in a long time, so any help would be great.

Thanks.

---

### Post by victorbrca on 2009-06-04
What output do you get with the following commands?

```
ifconfig
sudo dhclient eth0
```

---

### Post by ubuntuforums on 2009-06-04
Thanks for responding.

Here is the output I get for 'ifconfig':
```
user@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```

The output for 'sudo dhclient eth0':
```
user@ubuntu:~$ sudo dhclient eth0
[sudo] password for user: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Listening on LPF/eth0/00:00:00:00:00:00
Sending on   LPF/eth0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
...
```

Then I didn't know if I should do it for 'lo' as well, so I did:
```
user@ubuntu:~$ sudo dhclient lo
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Here's a screenshot of my network connections:
[http://img171.imageshack.us/img171/7215/ubuntudesk.png](http://img171.imageshack.us/img171/7215/ubuntudesk.png)

---

### Post by ubuntuforums on 2009-06-04
Does nobody know how to get my internet working? This is really frustrating, it must be just a setting or something simple to fix it? I don't know what to do with any of that output. :s

---

### Post by Celauran on 2009-06-04
Your ethernet card isn't being recognized. Can you post output of:

```
sudo lshw -C network
```

---

### Post by ubuntuforums on 2009-06-04
Hey thanks for replying, here's the output for 'sudo lshw -C network':
```
user@ubuntu:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:92:73:79:44:eb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```
Does that mean I just have to enable it? If so, how?

Thanks.

@Celauran: btw, I live in ndg, near vendom metro.

---

### Post by Celauran on 2009-06-04
You'll need to figure out which kernel module is required, then load it. Try Googling "SiS900 PCI Fast Ethernet" and see where that takes you.

---

### Post by albinootje on 2009-06-04
Can you post the output of the following of this in a terminal in Ubuntu :
```

dmesg
lsmod|grep -i sis900
ifconfig

```

And after that can you post a screenshot of the command :
```

ipconfig /all

```
in MS-Windows.

---

### Post by ubuntuforums on 2009-06-04
Hi albinootje.

The output of 'dmesg':
```
user@ubuntu:~$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fff8000 - 0000000030000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff0ffff (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  modified: 000000002fff0000 - 000000002fff8000 (ACPI data)
[    0.000000]  modified: 000000002fff8000 - 0000000030000000 (ACPI NVS)
[    0.000000]  modified: 00000000fec00000 - 00000000fed00000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ffee0000 - 00000000fff0ffff (reserved)
[    0.000000]  modified: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 2fff0000 @ 10000-16000
[    0.000000] RAMDISK: 2f870000 - 2ffdff61
[    0.000000] ACPI: RSDP 000FA130, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 2FFF0000, 002C (r1 AMIINT SiS645XX       10 MSFT  100000B)
[    0.000000] ACPI: FACP 2FFF0030, 0081 (r1 AMIINT SiS645XX       11 MSFT  100000B)
[    0.000000] ACPI: DSDT 2FFF0120, 3514 (r1    SiS      645     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 2FFF8000, 0040
[    0.000000] ACPI: APIC 2FFF00C0, 0058 (r1 AMIINT SiS645XX     1000 MSFT  100000B)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2fff0000
[    0.000000]   low ram: 00000000 - 2fff0000
[    0.000000]   bootmap 00012000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [002f870000 - 002ffdff61]          RAMDISK ==> [002f870000 - 002ffdff61]
[    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000018000]          BOOTMAP ==> [0000012000 - 0000018000]
[    0.000000] found SMP MP-table at [c00fbaf0] 000fbaf0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002fff0
[    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002fff0
[    0.000000] On node 0 totalpages: 196479
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1504 pages used for memmap
[    0.000000]   Normal zone: 190992 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194943
[    0.000000] Kernel command line: root=UUID=98D865D1D865ADE6 loop=/ubuntu/disks/root.disk ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1802.980 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 3931520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 759580k/786368k available (4126k kernel code, 26208k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf07f0000 - 0xff3fe000   ( 236 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 3605.96 BogoMIPS (lpj=7211920)
[    0.004048] Security Framework initialized
[    0.004060] SELinux:  Disabled at boot.
[    0.004091] AppArmor: AppArmor initialized
[    0.004112] Mount-cache hash table entries: 512
[    0.004353] Initializing cgroup subsys ns
[    0.004362] Initializing cgroup subsys cpuacct
[    0.004368] Initializing cgroup subsys memory
[    0.004378] Initializing cgroup subsys freezer
[    0.004405] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004413] CPU: L2 cache: 512K
[    0.004419] CPU: Hyper-Threading is disabled
[    0.004445] Checking 'hlt' instruction... OK.
[    0.021148] SMP alternatives: switching to UP code
[    0.180036] ACPI: Core revision 20080926
[    0.186639] ACPI: Checking initramfs for custom DSDT
[    0.702591] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.742285] CPU0: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 04
[    0.744002] Brought up 1 CPUs
[    0.744002] Total of 1 processors activated (3605.96 BogoMIPS).
[    0.744002] CPU0 attaching NULL sched-domain.
[    0.744002] net_namespace: 776 bytes
[    0.744002] Booting paravirtualized kernel on bare hardware
[    0.744002] Time: 20:38:27  Date: 06/04/09
[    0.744002] regulator: core version 0.5
[    0.744002] NET: Registered protocol family 16
[    0.744002] EISA bus registered
[    0.744002] ACPI: bus type pci registered
[    0.744250] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
[    0.744254] PCI: Using configuration type 1 for base access
[    0.747017] ACPI: EC: Look up EC in DSDT
[    0.755827] ACPI: Interpreter enabled
[    0.755834] ACPI: (supports S0 S1 S4 S5)
[    0.755866] ACPI: Using IOAPIC for interrupt routing
[    0.762967] ACPI: No dock devices found.
[    0.762988] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.763074] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.763258] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.763319] pci 0000:00:02.1: reg 20 io port: [0xc00-0xc1f]
[    0.763396] pci 0000:00:02.5: reg 20 io port: [0xff00-0xff0f]
[    0.763461] pci 0000:00:02.7: reg 10 io port: [0xdc00-0xdcff]
[    0.763472] pci 0000:00:02.7: reg 14 io port: [0xd800-0xd87f]
[    0.763520] pci 0000:00:02.7: supports D1 D2
[    0.763524] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.763531] pci 0000:00:02.7: PME# disabled
[    0.763579] pci 0000:00:03.0: reg 10 32bit mmio: [0xdfffc000-0xdfffcfff]
[    0.763633] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.763639] pci 0000:00:03.0: PME# disabled
[    0.763687] pci 0000:00:03.1: reg 10 32bit mmio: [0xdfffd000-0xdfffdfff]
[    0.763742] pci 0000:00:03.1: PME# supported from D0 D3hot D3cold
[    0.763749] pci 0000:00:03.1: PME# disabled
[    0.763796] pci 0000:00:03.2: reg 10 32bit mmio: [0xdfffe000-0xdfffefff]
[    0.763850] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    0.763856] pci 0000:00:03.2: PME# disabled
[    0.763903] pci 0000:00:03.3: reg 10 32bit mmio: [0xdffff000-0xdfffffff]
[    0.763957] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.763964] pci 0000:00:03.3: PME# disabled
[    0.764034] pci 0000:00:04.0: reg 10 io port: [0xd400-0xd4ff]
[    0.764046] pci 0000:00:04.0: reg 14 32bit mmio: [0xdfffb000-0xdfffbfff]
[    0.764084] pci 0000:00:04.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.764099] pci 0000:00:04.0: supports D1 D2
[    0.764102] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.764108] pci 0000:00:04.0: PME# disabled
[    0.764165] pci 0000:00:0a.0: reg 10 32bit mmio: [0xdffe0000-0xdffeffff]
[    0.764175] pci 0000:00:0a.0: reg 14 io port: [0xd000-0xd007]
[    0.764222] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.764229] pci 0000:00:0a.0: PME# disabled
[    0.764327] pci 0000:01:00.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
[    0.764337] pci 0000:01:00.0: reg 14 32bit mmio: [0xc0000000-0xcfffffff]
[    0.764367] pci 0000:01:00.0: reg 30 32bit mmio: [0xdfee0000-0xdfefffff]
[    0.764438] pci 0000:00:01.0: bridge 32bit mmio: [0xddd00000-0xdfefffff]
[    0.764446] pci 0000:00:01.0: bridge 32bit mmio pref: [0xbda00000-0xddbfffff]
[    0.764459] bus 00 -> node 0
[    0.764470] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.766955] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.767171] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.767377] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.767585] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.767789] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.768011] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.768221] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.768428] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 *12 14 15)
[    0.768577] ACPI: Power Resource [URP1] (off)
[    0.768635] ACPI: Power Resource [URP2] (off)
[    0.768688] ACPI: Power Resource [FDDP] (off)
[    0.768745] ACPI: Power Resource [LPTP] (off)
[    0.768873] ACPI: WMI: Mapper loaded
[    0.769240] SCSI subsystem initialized
[    0.769308] libata version 3.00 loaded.
[    0.769400] usbcore: registered new interface driver usbfs
[    0.769435] usbcore: registered new interface driver hub
[    0.769487] usbcore: registered new device driver usb
[    0.769704] PCI: Using ACPI for IRQ routing
[    0.769852] Bluetooth: Core ver 2.13
[    0.769852] NET: Registered protocol family 31
[    0.769852] Bluetooth: HCI device and connection manager initialized
[    0.769852] Bluetooth: HCI socket layer initialized
[    0.769852] NET: Registered protocol family 8
[    0.769852] NET: Registered protocol family 20
[    0.769852] NetLabel: Initializing
[    0.769852] NetLabel:  domain hash size = 128
[    0.769852] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.769852] NetLabel:  unlabeled traffic allowed by default
[    0.769852] AppArmor: AppArmor Filesystem Enabled
[    0.769852] pnp: PnP ACPI init
[    0.769852] ACPI: bus type pnp registered
[    0.775934] pnp: PnP ACPI: found 11 devices
[    0.775939] ACPI: ACPI bus type pnp unregistered
[    0.775945] PnPBIOS: Disabled by ACPI PNP
[    0.775964] system 00:01: ioport range 0x290-0x297 has been reserved
[    0.775969] system 00:01: ioport range 0x480-0x48f has been reserved
[    0.775973] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.775978] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.775982] system 00:01: ioport range 0x880-0x8ff has been reserved
[    0.775986] system 00:01: ioport range 0xc00-0xc1f has been reserved
[    0.775990] system 00:01: ioport range 0x3f0-0x3f1 has been reserved
[    0.776011] system 00:01: iomem range 0xfec00000-0xfecfffff has been reserved
[    0.776017] system 00:01: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.810882] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.810886] pci 0000:00:01.0:   IO window: disabled
[    0.810895] pci 0000:00:01.0:   MEM window: 0xddd00000-0xdfefffff
[    0.810902] pci 0000:00:01.0:   PREFETCH window: 0x000000bda00000-0x000000ddbfffff
[    0.810924] bus: 00 index 0 io port: [0x00-0xffff]
[    0.810928] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.810932] bus: 01 index 0 mmio: [0x0-0x0]
[    0.810936] bus: 01 index 1 mmio: [0xddd00000-0xdfefffff]
[    0.810940] bus: 01 index 2 mmio: [0xbda00000-0xddbfffff]
[    0.810943] bus: 01 index 3 mmio: [0x0-0x0]
[    0.810960] NET: Registered protocol family 2
[    0.811184] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.811724] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.813117] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.813994] TCP: Hash tables configured (established 131072 bind 65536)
[    0.814001] TCP reno registered
[    0.814302] NET: Registered protocol family 1
[    0.814543] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.324989]  it is
[    1.883212] Freeing initrd memory: 7615k freed
[    1.883328] cpufreq: No nForce2 chipset.
[    1.883617] audit: initializing netlink socket (disabled)
[    1.883650] type=2000 audit(1244147907.880:1): initialized
[    1.894536] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.896666] VFS: Disk quotas dquot_6.5.1
[    1.896769] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.897871] fuse init (API version 7.10)
[    1.898031] msgmni has been set to 1498
[    1.898352] alg: No test for stdrng (krng)
[    1.898375] io scheduler noop registered
[    1.898379] io scheduler anticipatory registered
[    1.898383] io scheduler deadline registered
[    1.898418] io scheduler cfq registered (default)
[    1.898551] pci 0000:01:00.0: Boot video device
[    1.903435] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.903454] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.903681] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.903687] ACPI: Power Button (FF) [PWRF]
[    1.903768] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.903773] ACPI: Power Button (CM) [PWRB]
[    1.904073] processor ACPI_CPU:00: registered as cooling_device0
[    1.907142] isapnp: Scanning for PnP cards...
[    2.261054] isapnp: No Plug & Play device found
[    2.263429] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.263552] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.264131] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.265468] brd: module loaded
[    2.266068] loop: module loaded
[    2.266210] Fixed MDIO Bus: probed
[    2.266222] PPP generic driver version 2.4.2
[    2.266345] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.266403] Driver 'sd' needs updating - please use bus_type methods
[    2.266422] Driver 'sr' needs updating - please use bus_type methods
[    2.267434] pata_sis 0000:00:02.5: version 0.5.2
[    2.267747] scsi0 : pata_sis
[    2.267921] scsi1 : pata_sis
[    2.269225] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.269231] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.449648] ata1.00: ATA-8: WDC WD1600AAJB-56WRA0, 58.01H58, max UDMA/100
[    2.449653] ata1.00: 312581808 sectors, multi 16: LBA48 
[    2.457003] ata1.00: configured for UDMA/100
[    2.620355] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.01, max UDMA/66
[    2.620399] ata2.00: limited to UDMA/33 due to 40-wire cable
[    2.636393] ata2.00: configured for UDMA/33
[    2.637723] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AAJB-5 58.0 PQ: 0 ANSI: 5
[    2.637907] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.637937] sd 0:0:0:0: [sda] Write Protect is off
[    2.637941] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.637986] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.638102] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.638126] sd 0:0:0:0: [sda] Write Protect is off
[    2.638131] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.638174] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.638180]  sda: sda1
[    2.645872] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.645982] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.647400] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.01 PQ: 0 ANSI: 5
[    2.651609] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.651616] Uniform CD-ROM driver Revision: 3.20
[    2.651802] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.651886] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.652127] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.652175] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.652214] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    2.652322] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    2.652371] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
[    2.652395] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdffff000
[    2.664021] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    2.664141] usb usb1: configuration #1 chosen from 1 choice
[    2.664189] hub 1-0:1.0: USB hub found
[    2.664204] hub 1-0:1.0: 6 ports detected
[    2.664387] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.664429] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.664458] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    2.664551] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    2.664583] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdfffc000
[    2.722107] usb usb2: configuration #1 chosen from 1 choice
[    2.722152] hub 2-0:1.0: USB hub found
[    2.722168] hub 2-0:1.0: 2 ports detected
[    2.722317] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.722336] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    2.722416] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    2.722444] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdfffd000
[    2.778088] usb usb3: configuration #1 chosen from 1 choice
[    2.778132] hub 3-0:1.0: USB hub found
[    2.778148] hub 3-0:1.0: 2 ports detected
[    2.778294] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.778312] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    2.778388] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[    2.778416] ohci_hcd 0000:00:03.2: irq 22, io mem 0xdfffe000
[    2.834090] usb usb4: configuration #1 chosen from 1 choice
[    2.834139] hub 4-0:1.0: USB hub found
[    2.834155] hub 4-0:1.0: 2 ports detected
[    2.834301] uhci_hcd: USB Universal Host Controller Interface driver
[    2.834442] usbcore: registered new interface driver libusual
[    2.834503] usbcore: registered new interface driver usbserial
[    2.834528] USB Serial support registered for generic
[    2.834555] usbcore: registered new interface driver usbserial_generic
[    2.834559] usbserial: USB Serial Driver core
[    2.834634] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.834639] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.834735] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.834919] mice: PS/2 mouse device common for all mice
[    2.835141] rtc_cmos 00:03: RTC can wake from S4
[    2.835208] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.835239] rtc0: alarms up to one month, 114 bytes nvram
[    2.835354] device-mapper: uevent: version 1.0.3
[    2.835553] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.835638] device-mapper: multipath: version 1.0.5 loaded
[    2.835644] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.835783] EISA: Probing bus 0 at eisa.0
[    2.835829] EISA: Detected 0 cards.
[    2.835874] cpuidle: using governor ladder
[    2.835878] cpuidle: using governor menu
[    2.836801] TCP cubic registered
[    2.836936] NET: Registered protocol family 10
[    2.837642] lo: Disabled Privacy Extensions
[    2.838185] NET: Registered protocol family 17
[    2.838221] Bluetooth: L2CAP ver 2.11
[    2.838224] Bluetooth: L2CAP socket layer initialized
[    2.838229] Bluetooth: SCO (Voice Link) ver 0.6
[    2.838233] Bluetooth: SCO socket layer initialized
[    2.838301] Bluetooth: RFCOMM socket layer initialized
[    2.838316] Bluetooth: RFCOMM TTY layer initialized
[    2.838319] Bluetooth: RFCOMM ver 1.10
[    2.838402] Using IPI No-Shortcut mode
[    2.838571] registered taskstats version 1
[    2.838742]   Magic number: 13:3:649
[    2.838863] rtc_cmos 00:03: setting system clock to 2009-06-04 20:38:29 UTC (1244147909)
[    2.838870] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.838873] EDD information not available.
[    2.839661] Freeing unused kernel memory: 532k freed
[    2.839849] Write protecting the kernel text: 4128k
[    2.839910] Write protecting the kernel read-only data: 1532k
[    2.874899] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.928439] hub 1-0:1.0: unable to enumerate USB device on port 4
[    3.333528] Floppy drive(s): fd0 is 1.44M
[    3.351936] FDC 0 is a post-1991 82077
[    3.388465] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    3.560970] sis900.c: v1.08.10 Apr. 2 2006
[    3.561060] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.562390] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    3.575830] 0000:00:04.0: Using transceiver found at address 1 as default
[    3.586261] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 19, 00:00:00:00:00:00
[    3.616765] usb 3-2: configuration #1 chosen from 1 choice
[    3.618158] hub 3-2:1.0: USB hub found
[    3.620975] hub 3-2:1.0: 2 ports detected
[    3.816466] hub 1-0:1.0: unable to enumerate USB device on port 4
[    4.120050] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    4.336620] usb 4-2: configuration #1 chosen from 1 choice
[    4.361939] usbcore: registered new interface driver hiddev
[    4.384557] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:03.2/usb4/4-2/4-2:1.0/input/input4
[    4.410953] generic-usb 0003:046D:C510.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:03.2-2/input0
[    4.410990] usbcore: registered new interface driver usbhid
[    4.410997] usbhid: v2.6:USB HID core driver
[    4.524521] hub 1-0:1.0: unable to enumerate USB device on port 4
[    4.601859] usb 3-2.1: new full speed USB device using ohci_hcd and address 3
[    4.717574] usb 3-2.1: configuration #1 chosen from 1 choice
[    4.801843] usb 3-2.2: new full speed USB device using ohci_hcd and address 4
[    4.827234] kjournald starting.  Commit interval 5 seconds
[    4.827268] EXT3-fs: mounted filesystem with ordered data mode.
[    4.919181] usb 3-2.2: configuration #1 chosen from 1 choice
[    5.104457] hub 1-0:1.0: unable to enumerate USB device on port 4
[    5.288438] hub 1-0:1.0: unable to enumerate USB device on port 4
[    5.528054] usb 1-4: new high speed USB device using ehci_hcd and address 9
[    5.584410] hub 1-0:1.0: unable to enumerate USB device on port 4
[    5.824104] usb 1-4: new high speed USB device using ehci_hcd and address 10
[    5.888356] hub 1-0:1.0: unable to enumerate USB device on port 4
[    6.272203] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    6.472988] usb 2-2: not running at top speed; connect to a high speed hub
[    6.491148] usb 2-2: configuration #1 chosen from 1 choice
[    6.859027] Initializing USB Mass Storage driver...
[    6.859269] scsi2 : SCSI emulation for USB Mass Storage devices
[    6.859411] usbcore: registered new interface driver usb-storage
[    6.859417] USB Mass Storage support registered.
[    6.859902] usb-storage: device found at 2
[    6.859907] usb-storage: waiting for device to settle before scanning
[    9.640800] udev: starting version 141
[    9.801028] Linux agpgart interface v0.103
[    9.824458] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.840259] agpgart-sis 0000:00:00.0: SiS chipset [1039/0650]
[    9.849994] agpgart-sis 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    9.879785] parport_pc 00:09: reported by Plug and Play ACPI
[    9.879911] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[    9.954494] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[    9.954505] ACPI: I/O resource 0000:00:02.1 [0xc00-0xc1f] conflicts with ACPI region SMRG [0xc00-0xc1f]
[    9.954509] ACPI: Device needs an ACPI driver
[   10.175793] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x413C pid 0x5106
[   10.175836] usbcore: registered new interface driver usblp
[   10.402058] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   10.706307] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   11.028077] intel8x0_measure_ac97_clock: measured 54778 usecs
[   11.028083] intel8x0: clocking to 48000
[   11.100210] ppdev: user-space parallel port driver
[   11.383738] lp0: using parport0 (interrupt-driven).
[   11.857651] usb-storage: device scan complete
[   11.864483] scsi 2:0:0:0: Direct-Access     DMI      Ultra HDD        1.21 PQ: 0 ANSI: 0
[   11.896498] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   11.909447] sd 2:0:0:0: [sdb] Write Protect is off
[   11.909452] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[   11.909456] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.920443] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   11.933439] sd 2:0:0:0: [sdb] Write Protect is off
[   11.933443] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[   11.933447] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.933453]  sdb: sdb1
[   11.943660] sd 2:0:0:0: [sdb] Attached SCSI disk
[   11.943788] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   12.091030] EXT3 FS on loop0, internal journal
[   17.479141] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k
[   17.776669] type=1505 audit(1244162324.437:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1905
[   17.860446] type=1505 audit(1244162324.521:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1909
[   17.860762] type=1505 audit(1244162324.521:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1909
[   17.860869] type=1505 audit(1244162324.521:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1909
[   17.860947] type=1505 audit(1244162324.521:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1909
[   18.097872] type=1505 audit(1244162324.757:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1914
[   18.098308] type=1505 audit(1244162324.757:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1914
[   18.151229] type=1505 audit(1244162324.809:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1918
[   21.679434] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.679441] Bluetooth: BNEP filters: protocol multicast
[   21.753605] Bridge firewalling registered
```

Output of 'lsmod|grep -i sis900':
```
user@ubuntu:~$ lsmod|grep -i sis900
sis900                 28288  0 
mii                    13312  1 sis900
```

Output of 'ifconfig':
```
user@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```

Thanks albinootje. I hope you can figure out the problem, in the mean time I'll do some more googling as Celauran suggested.

---

### Post by ubuntuforums on 2009-06-04
I forgot to post the output from 'ipconfig /all' in ms-dos. Here:

```
C:\Documents and Settings\user>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : my-desktop
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : SiS 900-Based PCI Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-00-00-00-00-00
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : (hiding this k)
        Subnet Mask . . . . . . . . . . . : 255.255.254.0
        Default Gateway . . . . . . . . . : (hiding this k)
        DHCP Server . . . . . . . . . . . : 192.168.175.3
        DNS Servers . . . . . . . . . . . : 192.168.175.2
                                            142.166.86.18
                                            142.166.86.19
        Lease Obtained. . . . . . . . . . : Thursday, June 04, 2009 8:15:26 PM
        Lease Expires . . . . . . . . . . : Friday, June 05, 2009 8:15:26 AM
```

I haven't found any solutions googling, yet. I'm currently connected on this NIC in Windows.

---

### Post by albinootje on 2009-06-04
> **ubuntuforums said:**
> 
[    3.560970] sis900.c: v1.08.10 Apr. 2 2006
[    3.561060] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.562390] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    3.575830] 0000:00:04.0: Using transceiver found at address 1 as default
[    3.586261] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 19, 00:00:00:00:00:00
=====================
[    9.954505] ACPI: I/O resource 0000:00:02.1 [0xc00-0xc1f] conflicts with ACPI region SMRG [0xc00-0xc1f]
[    9.954509] ACPI: Device needs an ACPI driver
[/code]

Not many errors or warnings at all from dmesg, and also no hints given.

> 
Output of 'lsmod|grep -i sis900':
```
user@ubuntu:~$ lsmod|grep -i sis900
sis900                 28288  0 
mii                    13312  1 sis900
```

The sis900 module is loaded but is not used (the value is 0 instead of 1).

Can you also post the output of :
```

lspci

```
Thanks.

---

### Post by albinootje on 2009-06-04
> **ubuntuforums said:**
> 
```
C:\Documents and Settings\user>ipconfig /all


Okay. I asked for this (apart from seeing whether you get a LAN address or a public internet ip) with the idea that you can then try to fill in this information in Ubuntu to have a static ip address (instead of using DHCP), and test with that.

This could be useful, but in your case there's not even an eth0 visible..
http://www.linuxquestions.org/questions/linux-hardware-18/sis900-pci-ethernet-wont-connect-to-network-617944/

And can you try :
[code]
ifconfig -a   (with the -a, I forgot that first)

```
Does any eth1 or eth2 show up ?

---

### Post by ubuntuforums on 2009-06-04
Output for 'lspci':
```
user@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)
```

I'll try 'ifconfig -a' in a minute (have to shutdown windows, start ubuntu, etc).

---

### Post by ubuntuforums on 2009-06-04
Output from 'ifconfig -a':
```
user@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

pan0      Link encap:Ethernet  HWaddr 5e:b3:67:45:2a:96  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

So nope, there isn't any eth1 or eth2 unfortunately. :(

---

### Post by albinootje on 2009-06-04
> **ubuntuforums said:**
> Output from 'ifconfig -a':


Thanks. So.. eth0 is there, instead of no ethX at all..
And lspci shows sis900 indeed.

I'm off to sleep, hopefully others can help you a little further, or a search on the net can help.

Try the ethtool tool.
It looked (from the output in one of your comments) like your card was configured for 10 Mbit instead of 100 Mbit, but I could have misread that.

---

### Post by alphacrucis2 on 2009-06-04
Try booting with ACPI turned off. You add 

```
acpi=off
```

to the end of the kernel line in the GRUB menu. You can test this without actually editing the grub boot menu by typing 'e' when the grub boot menu appears. Arrow down to the kernel line and type e again. Then type acpi=off so it is appended after the word splash. Hit enter then b to boot. If this works you can make it a permanent change by editing /boot/grub/menu.lst. From a terminal:

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by ubuntuforums on 2009-06-04
I've been googling, I haven't found a solution, but I'll keep at it. I'll look up that ethtool. Thank you for your help albinootje.

If anyone else has any ideas, please post. Thanks.

Edit: Alright, I'll try that right now.

---

### Post by ubuntuforums on 2009-06-04
Thanks for trying, unfortunately that didn't make a difference.

---

### Post by victorbrca on 2009-06-04
Lets try this...

1-
```
sudo ifconfig eth0 up
sudo dhclient eth0
```

then

```
ifconfig eth0
```

if you are still with no address, try this:

```
sudo ifconfig eth0 [same IP Address as on windows] netmask 255.255.254.0
sudo route add default gw [same Default Gateway as on windows]
ifconfig eth0
ping [default gw ip]
ping google.com
cat /etc/resolv.conf
```

Paste everything here.

---

### Post by ubuntuforums on 2009-06-04
Thanks for all the help guys, I actually got it working! I missed the link that albinootje posted, I just read through it. I changed my mac address, and voila, the internet is working.

[http://www.linuxquestions.org/questions/linux-hardware-18/sis900-pci-ethernet-wont-connect-to-network-617944/](http://www.linuxquestions.org/questions/linux-hardware-18/sis900-pci-ethernet-wont-connect-to-network-617944/)

Thanks again everyone! I really appreciate the effort you all put into helping me. :)

---

