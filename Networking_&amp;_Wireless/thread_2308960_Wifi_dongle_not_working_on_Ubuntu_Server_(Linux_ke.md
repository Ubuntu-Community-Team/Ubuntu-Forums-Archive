---
title: "Wifi dongle not working on Ubuntu Server (Linux kernel 4.3)"
date: 2016-01-06
forum: Networking &amp; Wireless
---

### Post by swoncen2 on 2016-01-06
Hi,

I have installed Ubuntu Server on a new PC with a Skylake CPU and since I need the GPU support from the Skylake Chip for playing media files on Kodi (server + media-PC hybrid) I installed the 4.3 kernel. So, now I need wifi access with my Edimax 7811UN wifi dongle, but It doesn't seem to work.

iwconfig shows this:

```

wlx74da38547289  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

enp0s31f6  no wireless extensions.

lo        no wireless extensions.

```

ifconfig shows this:

```

enp0s31f6 Link encap:Ethernet  HWaddr d0:50:99:82:08:b6  
          inet addr:192.168.0.112  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::d250:99ff:fe82:8b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14774 (14.7 KB)  TX bytes:17348 (17.3 KB)
          Interrupt:16 Memory:df000000-df020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:758480 (758.4 KB)  TX bytes:758480 (758.4 KB)

```

lsusb:

```

Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]

```

/etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto enp0s31f6
iface enp0s31f6 inet static
address 192.168.0.112
netmask 255.255.255.0
gateway 192.168.0.1

auto wlx74da38547289
allow-hotplug wlx74da38547289
iface wlan0 inet static
address 192.168.0.111
netmask 255.255.255.0
gateway 192.168.0.1
wpa-ap-scan 1
wpa-scan-ssid 1
wpa-ssid "myssid"
wpa-psk "mypassword"

```

/etc/modprobe.d/8192cu.conf

```

options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

```

dmesg:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.3.0-040300-generic (kernel@gomeisa) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #201511020949 SMP Mon Nov 2 14:50:44 UTC 2015
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-040300-generic root=UUID=aa459486-ac1a-40d8-bdbe-c882b3aa9a04 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: xstate_offset[3]: 03c0, xstate_sizes[3]: 0040
[    0.000000] x86/fpu: xstate_offset[4]: 0400, xstate_sizes[4]: 0040
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x08: 'MPX bounds registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x10: 'MPX CSR'
[    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 0x440 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009c7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009c800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000005dc18fff] usable
[    0.000000] BIOS-e820: [mem 0x000000005dc19000-0x000000005dc19fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000005dc1a000-0x000000005dc43fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000005dc44000-0x000000005dc91fff] usable
[    0.000000] BIOS-e820: [mem 0x000000005dc92000-0x000000005e2d8fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000005e2d9000-0x0000000077044fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000077045000-0x0000000077118fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000077119000-0x0000000077326fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000077327000-0x0000000077ab8fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000077ab9000-0x0000000077ffefff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000077fff000-0x0000000077ffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000274ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./H170M Pro4S, BIOS P1.00 07/14/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x275000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0080000000 mask 7F80000000 uncachable
[    0.000000]   1 base 007C000000 mask 7FFC000000 uncachable
[    0.000000]   2 base 007A000000 mask 7FFE000000 uncachable
[    0.000000]   3 base 0079000000 mask 7FFF000000 uncachable
[    0.000000]   4 base 0078800000 mask 7FFF800000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: last_pfn = 0x78000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fc610-0x000fc61f] mapped at [ffff8800000fc610]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
[    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
[    0.000000] BRK [0x01ff4000, 0x01ff4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x274e00000-0x274ffffff]
[    0.000000]  [mem 0x274e00000-0x274ffffff] page 2M
[    0.000000] BRK [0x01ff5000, 0x01ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x260000000-0x274dfffff]
[    0.000000]  [mem 0x260000000-0x274dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x240000000-0x25fffffff]
[    0.000000]  [mem 0x240000000-0x25fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x5dc18fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x5dbfffff] page 2M
[    0.000000]  [mem 0x5dc00000-0x5dc18fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x5dc44000-0x5dc91fff]
[    0.000000]  [mem 0x5dc44000-0x5dc91fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x5e2d9000-0x77044fff]
[    0.000000]  [mem 0x5e2d9000-0x5e3fffff] page 4k
[    0.000000]  [mem 0x5e400000-0x76ffffff] page 2M
[    0.000000]  [mem 0x77000000-0x77044fff] page 4k
[    0.000000] BRK [0x01ff6000, 0x01ff6fff] PGTABLE
[    0.000000] BRK [0x01ff7000, 0x01ff7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x77119000-0x77326fff]
[    0.000000]  [mem 0x77119000-0x77326fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x77fff000-0x77ffffff]
[    0.000000]  [mem 0x77fff000-0x77ffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x23fffffff]
[    0.000000]  [mem 0x100000000-0x23fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x34780000-0x363b7fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F05B0 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x0000000077A79098 0000AC (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x0000000077A99FD8 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x0000000077A791D8 020E00 (v02 ALASKA A M I    01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000077AB8F80 000040
[    0.000000] ACPI: APIC 0x0000000077A9A0E8 000084 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x0000000077A9A170 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x0000000077A9A1B8 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x0000000077A9A258 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x0000000077A9A298 000038 (v01 ALASKA A M I    01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x0000000077A9A2D0 00036D (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: LPIT 0x0000000077A9A640 000094 (v01 INTEL  SKL      00000000 MSFT 0000005F)
[    0.000000] ACPI: DBGP 0x0000000077A9A6D8 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x0000000077A9A710 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x0000000077A9A768 00061A (v02 INTEL  xh_rvp08 00000000 INTL 20120913)
[    0.000000] ACPI: AAFT 0x0000000077A9AD88 000345 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x0000000077A9B0D0 0051E8 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x0000000077AA02B8 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: SSDT 0x0000000077AA0300 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x0000000077AA1158 0000A8 (v01 INTEL  SKL      00000001 INTL 00000001)
[    0.000000] ACPI: ASF! 0x0000000077AA1200 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000274ffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x274ff7000-0x274ffbfff]
[    0.000000]  [ffffea0000000000-ffffea0009dfffff] PMD -> [ffff88026ca00000-ffff8802745fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x0000000274ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009bfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000005dc18fff]
[    0.000000]   node   0: [mem 0x000000005dc44000-0x000000005dc91fff]
[    0.000000]   node   0: [mem 0x000000005e2d9000-0x0000000077044fff]
[    0.000000]   node   0: [mem 0x0000000077119000-0x0000000077326fff]
[    0.000000]   node   0: [mem 0x0000000077fff000-0x0000000077ffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x0000000274ffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x0000000274ffffff]
[    0.000000] On node 0 totalpages: 2014077
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3995 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7536 pages used for memmap
[    0.000000]   DMA32 zone: 482274 pages, LIFO batch:31
[    0.000000]   Normal zone: 23872 pages used for memmap
[    0.000000]   Normal zone: 1527808 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x79000000-0x88ffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x5dc19000-0x5dc19fff]
[    0.000000] PM: Registered nosave memory: [mem 0x5dc1a000-0x5dc43fff]
[    0.000000] PM: Registered nosave memory: [mem 0x5dc92000-0x5e2d8fff]
[    0.000000] PM: Registered nosave memory: [mem 0x77045000-0x77118fff]
[    0.000000] PM: Registered nosave memory: [mem 0x77327000-0x77ab8fff]
[    0.000000] PM: Registered nosave memory: [mem 0x77ab9000-0x77ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x78000000-0x78ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x79000000-0x88ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x89000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfdffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x89000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff880274c00000 s97240 r8192 d29736 u524288
[    0.000000] pcpu-alloc: s97240 r8192 d29736 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1982584
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-040300-generic root=UUID=aa459486-ac1a-40d8-bdbe-c882b3aa9a04 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7817132K/8056308K available (7904K kernel code, 1248K rwdata, 3900K rodata, 1448K init, 1300K bss, 239176K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Unable to calibrate against PIT
[    0.000000] tsc: using HPET reference calibration
[    0.000000] tsc: Detected 3696.331 MHz processor
[    0.000018] Calibrating delay loop (skipped), value calculated using timer frequency.. 7392.66 BogoMIPS (lpj=14785324)
[    0.000023] pid_max: default: 32768 minimum: 301
[    0.000027] ACPI: Core revision 20150818
[    0.014686] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20150818/dswload-210)
[    0.014692] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20150818/psobject-227)
[    0.014714] ACPI Exception: AE_NOT_FOUND, (SSDT:xh_rvp08) while loading table (20150818/tbxfload-193)
[    0.020327] ACPI Error: 1 table load failures, 4 successful (20150818/tbxfload-214)
[    0.020340] Security Framework initialized
[    0.020343] Yama: becoming mindful.
[    0.020349] AppArmor: AppArmor initialized
[    0.020651] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.021592] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.022001] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.022008] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.022121] Initializing cgroup subsys io
[    0.022125] Initializing cgroup subsys memory
[    0.022130] Initializing cgroup subsys devices
[    0.022132] Initializing cgroup subsys freezer
[    0.022135] Initializing cgroup subsys net_cls
[    0.022137] Initializing cgroup subsys perf_event
[    0.022139] Initializing cgroup subsys net_prio
[    0.022141] Initializing cgroup subsys hugetlb
[    0.022144] Initializing cgroup subsys pids
[    0.022162] CPU: Physical Processor ID: 0
[    0.022164] CPU: Processor Core ID: 0
[    0.022168] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.022170] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.023137] mce: CPU supports 8 MCE banks
[    0.023148] CPU0: Thermal monitoring enabled (TM1)
[    0.023155] process: using mwait in idle threads
[    0.023157] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.023159] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.023390] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.024724] ftrace: allocating 31162 entries in 122 pages
[    0.033209] DMAR: Host address width 39
[    0.033212] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.033218] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e3ff0505e
[    0.033221] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.033225] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.033228] DMAR: RMRR base: 0x0000007707b000 end: 0x0000007709afff
[    0.033230] DMAR: RMRR base: 0x00000078800000 end: 0x00000088ffffff
[    0.033233] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.033234] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.033236] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.033237] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.034568] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.034571] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.038517] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078204] TSC deadline timer enabled
[    0.078209] smpboot: CPU0: Intel(R) Core(TM) i3-6100 CPU @ 3.70GHz (family: 0x6, model: 0x5e, stepping: 0x3)
[    0.078227] Performance Events: PEBS fmt3+, 32-deep LBR, Skylake events, full-width counters, Intel PMU driver.
[    0.078257] ... version:                4
[    0.078259] ... bit width:              48
[    0.078260] ... generic registers:      4
[    0.078262] ... value mask:             0000ffffffffffff
[    0.078263] ... max period:             0000ffffffffffff
[    0.078265] ... fixed-purpose events:   3
[    0.078267] ... event mask:             000000070000000f
[    0.078751] x86: Booting SMP configuration:
[    0.078754] .... node  #0, CPUs:      #1
[    0.092753] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.092796]  #2 #3
[    0.120969] x86: Booted up 1 node, 4 CPUs
[    0.120974] smpboot: Total of 4 processors activated (29570.64 BogoMIPS)
[    0.123497] devtmpfs: initialized
[    0.124831] evm: security.selinux
[    0.124833] evm: security.SMACK64
[    0.124835] evm: security.SMACK64EXEC
[    0.124836] evm: security.SMACK64TRANSMUTE
[    0.124838] evm: security.SMACK64MMAP
[    0.124839] evm: security.ima
[    0.124841] evm: security.capability
[    0.124872] PM: Registering ACPI NVS region [mem 0x5dc19000-0x5dc19fff] (4096 bytes)
[    0.124875] PM: Registering ACPI NVS region [mem 0x77327000-0x77ab8fff] (7938048 bytes)
[    0.124972] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.125020] pinctrl core: initialized pinctrl subsystem
[    0.125162] RTC time:  0:17:00, date: 01/07/16
[    0.125235] NET: Registered protocol family 16
[    0.135388] cpuidle: using governor ladder
[    0.140748] cpuidle: using governor menu
[    0.140761] PCCT header not found.
[    0.140846] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.140849] ACPI: bus type PCI registered
[    0.140851] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.140900] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.140903] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.140912] PCI: Using configuration type 1 for base access
[    0.148991] ACPI: Added _OSI(Module Device)
[    0.148993] ACPI: Added _OSI(Processor Device)
[    0.148995] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.148996] ACPI: Added _OSI(Processor Aggregator Device)
[    0.153590] ACPI: Executed 21 blocks of module-level executable AML code
[    0.157138] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.159160] ACPI: Dynamic OEM Table Load:
[    0.159165] ACPI: SSDT 0xFFFF88026AC0B000 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.159706] ACPI: Dynamic OEM Table Load:
[    0.159711] ACPI: SSDT 0xFFFF88026AC12800 000726 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.160953] ACPI: Dynamic OEM Table Load:
[    0.160958] ACPI: SSDT 0xFFFF88026AC13000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.161614] ACPI: Dynamic OEM Table Load:
[    0.161618] ACPI: SSDT 0xFFFF88026ACA8600 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.163467] ACPI: Interpreter enabled
[    0.163475] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150818/hwxface-580)
[    0.163482] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150818/hwxface-580)
[    0.163498] ACPI: (supports S0 S3 S4 S5)
[    0.163499] ACPI: Using IOAPIC for interrupt routing
[    0.163547] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.166451] ACPI: Power Resource [WRST] (off)
[    0.166658] ACPI: Power Resource [WRST] (off)
[    0.166848] ACPI: Power Resource [WRST] (off)
[    0.167037] ACPI: Power Resource [WRST] (off)
[    0.167225] ACPI: Power Resource [WRST] (off)
[    0.167417] ACPI: Power Resource [WRST] (off)
[    0.167607] ACPI: Power Resource [WRST] (off)
[    0.167796] ACPI: Power Resource [WRST] (off)
[    0.167985] ACPI: Power Resource [WRST] (off)
[    0.168173] ACPI: Power Resource [WRST] (off)
[    0.168377] ACPI: Power Resource [WRST] (off)
[    0.168572] ACPI: Power Resource [WRST] (off)
[    0.168761] ACPI: Power Resource [WRST] (off)
[    0.168952] ACPI: Power Resource [WRST] (off)
[    0.169156] ACPI: Power Resource [WRST] (off)
[    0.169346] ACPI: Power Resource [WRST] (off)
[    0.169535] ACPI: Power Resource [WRST] (off)
[    0.169738] ACPI: Power Resource [WRST] (off)
[    0.169926] ACPI: Power Resource [WRST] (off)
[    0.170115] ACPI: Power Resource [WRST] (off)
[    0.174906] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.174911] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.175982] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.175985] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.176379] PCI host bridge to bus 0000:00
[    0.176382] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.176384] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.176386] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.176388] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.176391] pci_bus 0000:00: root bus resource [mem 0x89000000-0xdfffffff window]
[    0.176395] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff window]
[    0.176402] pci 0000:00:00.0: [8086:190f] type 00 class 0x060000
[    0.176589] pci 0000:00:02.0: [8086:1912] type 00 class 0x030000
[    0.176598] pci 0000:00:02.0: reg 0x10: [mem 0xde000000-0xdeffffff 64bit]
[    0.176602] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.176605] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.176732] pci 0000:00:14.0: [8086:a12f] type 00 class 0x0c0330
[    0.176754] pci 0000:00:14.0: reg 0x10: [mem 0xdf030000-0xdf03ffff 64bit]
[    0.176795] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.176856] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.176883] pci 0000:00:14.2: [8086:a131] type 00 class 0x118000
[    0.176904] pci 0000:00:14.2: reg 0x10: [mem 0xdf04e000-0xdf04efff 64bit]
[    0.177012] pci 0000:00:16.0: [8086:a13a] type 00 class 0x078000
[    0.177040] pci 0000:00:16.0: reg 0x10: [mem 0xdf04d000-0xdf04dfff 64bit]
[    0.177086] pci 0000:00:16.0: PME# supported from D3hot
[    0.177182] pci 0000:00:17.0: [8086:a102] type 00 class 0x010601
[    0.177200] pci 0000:00:17.0: reg 0x10: [mem 0xdf048000-0xdf049fff]
[    0.177205] pci 0000:00:17.0: reg 0x14: [mem 0xdf04c000-0xdf04c0ff]
[    0.177211] pci 0000:00:17.0: reg 0x18: [io  0xf090-0xf097]
[    0.177217] pci 0000:00:17.0: reg 0x1c: [io  0xf080-0xf083]
[    0.177222] pci 0000:00:17.0: reg 0x20: [io  0xf060-0xf07f]
[    0.177228] pci 0000:00:17.0: reg 0x24: [mem 0xdf04b000-0xdf04b7ff]
[    0.177248] pci 0000:00:17.0: PME# supported from D3hot
[    0.177330] pci 0000:00:1b.0: [8086:a169] type 01 class 0x060400
[    0.177377] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.177448] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.177493] pci 0000:00:1c.0: [8086:a112] type 01 class 0x060400
[    0.177540] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.177607] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.177654] pci 0000:00:1d.0: [8086:a118] type 01 class 0x060400
[    0.177701] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.177768] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.177815] pci 0000:00:1f.0: [8086:a144] type 00 class 0x060100
[    0.177972] pci 0000:00:1f.2: [8086:a121] type 00 class 0x058000
[    0.177983] pci 0000:00:1f.2: reg 0x10: [mem 0xdf044000-0xdf047fff]
[    0.178096] pci 0000:00:1f.3: [8086:a170] type 00 class 0x040300
[    0.178126] pci 0000:00:1f.3: reg 0x10: [mem 0xdf040000-0xdf043fff 64bit]
[    0.178154] pci 0000:00:1f.3: reg 0x20: [mem 0xdf020000-0xdf02ffff 64bit]
[    0.178180] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.178271] pci 0000:00:1f.3: System wakeup disabled by ACPI
[    0.178300] pci 0000:00:1f.4: [8086:a123] type 00 class 0x0c0500
[    0.178353] pci 0000:00:1f.4: reg 0x10: [mem 0xdf04a000-0xdf04a0ff 64bit]
[    0.178421] pci 0000:00:1f.4: reg 0x20: [io  0xf040-0xf05f]
[    0.178559] pci 0000:00:1f.6: [8086:15b8] type 00 class 0x020000
[    0.178592] pci 0000:00:1f.6: reg 0x10: [mem 0xdf000000-0xdf01ffff]
[    0.178670] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.178732] pci 0000:00:1f.6: System wakeup disabled by ACPI
[    0.178787] pci 0000:00:1b.0: PCI bridge to [bus 01]
[    0.178827] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.178868] pci 0000:00:1d.0: PCI bridge to [bus 03]
[    0.180003] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.180038] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.180072] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.180105] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.180138] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.180171] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.180203] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.180236] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.180386] ACPI: Enabled 5 GPEs in block 00 to 7F
[    0.180452] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.180455] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.180458] vgaarb: loaded
[    0.180460] vgaarb: bridge control possible 0000:00:02.0
[    0.180592] SCSI subsystem initialized
[    0.180618] libata version 3.00 loaded.
[    0.180631] ACPI: bus type USB registered
[    0.180641] usbcore: registered new interface driver usbfs
[    0.180647] usbcore: registered new interface driver hub
[    0.180657] usbcore: registered new device driver usb
[    0.180741] PCI: Using ACPI for IRQ routing
[    0.208405] PCI: pci_cache_line_size set to 64 bytes
[    0.208435] e820: reserve RAM buffer [mem 0x0009c800-0x0009ffff]
[    0.208436] e820: reserve RAM buffer [mem 0x5dc19000-0x5fffffff]
[    0.208437] e820: reserve RAM buffer [mem 0x5dc92000-0x5fffffff]
[    0.208438] e820: reserve RAM buffer [mem 0x77045000-0x77ffffff]
[    0.208438] e820: reserve RAM buffer [mem 0x77327000-0x77ffffff]
[    0.208439] e820: reserve RAM buffer [mem 0x275000000-0x277ffffff]
[    0.208506] NetLabel: Initializing
[    0.208507] NetLabel:  domain hash size = 128
[    0.208509] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.208516] NetLabel:  unlabeled traffic allowed by default
[    0.208591] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.208596] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.210637] clocksource: Switched to clocksource hpet
[    0.213919] AppArmor: AppArmor Filesystem Enabled
[    0.213955] pnp: PnP ACPI init
[    0.214119] system 00:00: [io  0x0280-0x028f] has been reserved
[    0.214121] system 00:00: [io  0x0290-0x029f] has been reserved
[    0.214123] system 00:00: [io  0x02a0-0x02af] has been reserved
[    0.214125] system 00:00: [io  0x02b0-0x02bf] has been reserved
[    0.214128] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.214428] pnp 00:01: [dma 0 disabled]
[    0.214513] pnp 00:01: Plug and Play ACPI device, IDs PNP0400 PNP0401 (active)
[    0.214669] pnp 00:02: [dma 0 disabled]
[    0.214693] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.214760] system 00:03: [io  0x0680-0x069f] has been reserved
[    0.214762] system 00:03: [io  0xffff] has been reserved
[    0.214764] system 00:03: [io  0xffff] has been reserved
[    0.214766] system 00:03: [io  0xffff] has been reserved
[    0.214768] system 00:03: [io  0x1800-0x18fe] could not be reserved
[    0.214770] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.214773] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.214820] system 00:04: [io  0x0800-0x087f] has been reserved
[    0.214822] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.214834] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.214856] system 00:06: [io  0x1854-0x1857] has been reserved
[    0.214859] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.214982] system 00:07: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.214984] system 00:07: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.214986] system 00:07: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.214988] system 00:07: [mem 0xe0000000-0xefffffff] has been reserved
[    0.214990] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.214993] system 00:07: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.214995] system 00:07: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.214997] system 00:07: [mem 0xff000000-0xffffffff] has been reserved
[    0.214999] system 00:07: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.215001] system 00:07: [mem 0xdffc0000-0xdffdffff] has been reserved
[    0.215004] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.215025] system 00:08: [mem 0xfd000000-0xfdabffff] has been reserved
[    0.215028] system 00:08: [mem 0xfdad0000-0xfdadffff] has been reserved
[    0.215030] system 00:08: [mem 0xfdb00000-0xfdffffff] has been reserved
[    0.215032] system 00:08: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.215034] system 00:08: [mem 0xfe036000-0xfe03bfff] has been reserved
[    0.215036] system 00:08: [mem 0xfe03d000-0xfe3fffff] has been reserved
[    0.215038] system 00:08: [mem 0xfe410000-0xfe7fffff] has been reserved
[    0.215040] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.215630] system 00:09: [mem 0xfdaf0000-0xfdafffff] has been reserved
[    0.215632] system 00:09: [mem 0xfdae0000-0xfdaeffff] has been reserved
[    0.215634] system 00:09: [mem 0xfdac0000-0xfdacffff] has been reserved
[    0.215637] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.216092] pnp: PnP ACPI: found 10 devices
[    0.223921] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.223940] pci 0000:00:1b.0: PCI bridge to [bus 01]
[    0.223948] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.223956] pci 0000:00:1d.0: PCI bridge to [bus 03]
[    0.223964] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.223965] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.223966] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.223967] pci_bus 0000:00: resource 7 [mem 0x89000000-0xdfffffff window]
[    0.223968] pci_bus 0000:00: resource 8 [mem 0xfd000000-0xfe7fffff window]
[    0.223986] NET: Registered protocol family 2
[    0.224095] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.224191] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.224266] TCP: Hash tables configured (established 65536 bind 65536)
[    0.224281] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.224296] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.224327] NET: Registered protocol family 1
[    0.224336] pci 0000:00:02.0: Video device with shadowed ROM
[    0.224763] PCI: CLS 0 bytes, default 64
[    0.224789] Trying to unpack rootfs image as initramfs...
[    0.510174] Freeing initrd memory: 28896K (ffff880034780000 - ffff8800363b8000)
[    0.510193] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.510196] software IO TLB [mem 0x73045000-0x77045000] (64MB) mapped at [ffff880073045000-ffff880077044fff]
[    0.510296] microcode: CPU0 sig=0x506e3, pf=0x2, revision=0x1f
[    0.510304] microcode: CPU1 sig=0x506e3, pf=0x2, revision=0x1f
[    0.510315] microcode: CPU2 sig=0x506e3, pf=0x2, revision=0x1f
[    0.510326] microcode: CPU3 sig=0x506e3, pf=0x2, revision=0x1f
[    0.510369] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.510394] Scanning for low memory corruption every 60 seconds
[    0.510667] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.510683] audit: initializing netlink subsys (disabled)
[    0.510692] audit: type=2000 audit(1452125820.520:1): initialized
[    0.510857] Initialise system trusted keyring
[    0.510914] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.510916] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.511735] zbud: loaded
[    0.511884] VFS: Disk quotas dquot_6.6.0
[    0.511903] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.512185] fuse init (API version 7.23)
[    0.512276] Key type big_key registered
[    0.513060] Key type asymmetric registered
[    0.513063] Asymmetric key parser 'x509' registered
[    0.513073] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.513135] io scheduler noop registered
[    0.513139] io scheduler deadline registered (default)
[    0.513158] io scheduler cfq registered
[    0.513705] aer 0000:00:1b.0:pcie02: service driver aer loaded
[    0.513723] aer 0000:00:1c.0:pcie02: service driver aer loaded
[    0.513740] aer 0000:00:1d.0:pcie02: service driver aer loaded
[    0.513748] pcieport 0000:00:1b.0: Signaling PME through PCIe PME interrupt
[    0.513752] pcie_pme 0000:00:1b.0:pcie01: service driver pcie_pme loaded
[    0.513757] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.513760] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.513765] pcieport 0000:00:1d.0: Signaling PME through PCIe PME interrupt
[    0.513768] pcie_pme 0000:00:1d.0:pcie01: service driver pcie_pme loaded
[    0.513771] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.513775] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.513791] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    0.513793] vesafb: scrolling: redraw
[    0.513795] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.513804] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90001000000, using 8128k, total 8128k
[    0.632640] Console: switching to colour frame buffer device 240x67
[    0.751576] fb0: VESA VGA frame buffer device
[    0.751947] intel_idle: MWAIT substates: 0x142120
[    0.751948] intel_idle: v0.4 model 0x5E
[    0.751949] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.752121] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.752818] ACPI: Sleep Button [SLPB]
[    0.753142] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.753838] ACPI: Power Button [PWRB]
[    0.754160] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.754814] ACPI: Power Button [PWRF]
[    0.755326] GHES: HEST is not enabled!
[    0.755722] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.776786] 00:02: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.779436] Linux agpgart interface v0.103
[    0.782756] brd: module loaded
[    0.784476] loop: module loaded
[    0.784933] libphy: Fixed MDIO Bus: probed
[    0.785277] tun: Universal TUN/TAP device driver, 1.6
[    0.785698] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.786262] PPP generic driver version 2.4.2
[    0.786812] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.787252] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.787951] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    0.788659] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.788763] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.789329] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.789932] usb usb1: Product: xHCI Host Controller
[    0.790339] usb usb1: Manufacturer: Linux 4.3.0-040300-generic xhci-hcd
[    0.790917] usb usb1: SerialNumber: 0000:00:14.0
[    0.791393] hub 1-0:1.0: USB hub found
[    0.791719] hub 1-0:1.0: 16 ports detected
[    0.798705] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.799142] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.799776] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.800342] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.800945] usb usb2: Product: xHCI Host Controller
[    0.801352] usb usb2: Manufacturer: Linux 4.3.0-040300-generic xhci-hcd
[    0.801904] usb usb2: SerialNumber: 0000:00:14.0
[    0.802373] hub 2-0:1.0: USB hub found
[    0.802728] hub 2-0:1.0: 8 ports detected
[    0.806334] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.806913] ehci-pci: EHCI PCI platform driver
[    0.807292] ehci-platform: EHCI generic platform driver
[    0.807733] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.808251] ohci-pci: OHCI PCI platform driver
[    0.808629] ohci-platform: OHCI generic platform driver
[    0.833058] uhci_hcd: USB Universal Host Controller Interface driver
[    0.857994] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.885991] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.911040] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.936019] mousedev: PS/2 mouse device common for all mice
[    0.961041] rtc_cmos 00:05: RTC can wake from S4
[    0.986207] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.011284] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.036495] i2c /dev entries driver
[    1.061418] device-mapper: uevent: version 1.0.3
[    1.086364] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    1.111681] Intel P-state driver initializing.
[    1.122531] usb 1-10: new high-speed USB device number 2 using xhci_hcd
[    1.162801] intel_pstate: HWP enabled
[    1.188285] intel_pstate: HWP enabled
[    1.213811] intel_pstate: HWP enabled
[    1.239356] intel_pstate: HWP enabled
[    1.264525] ledtrig-cpu: registered to indicate activity on CPUs
[    1.264848] usb 1-10: New USB device found, idVendor=7392, idProduct=7811
[    1.264849] usb 1-10: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.264849] usb 1-10: Product: 802.11n WLAN Adapter
[    1.264850] usb 1-10: Manufacturer: Realtek
[    1.264850] usb 1-10: SerialNumber: 00e04c000001
[    1.416431] NET: Registered protocol family 10
[    1.430492] usb 1-11: new full-speed USB device number 3 using xhci_hcd
[    1.466032] NET: Registered protocol family 17
[    1.490496] Key type dns_resolver registered
[    1.506488] tsc: Refined TSC clocksource calibration: 3695.998 MHz
[    1.506489] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x6a8d2284b57, max_idle_ns: 881590451434 ns
[    1.563465] registered taskstats version 1
[    1.587631] Loading compiled-in X.509 certificates
[    1.612154] Loaded X.509 cert 'Build time autogenerated kernel key: 57d62c37587c99cd510d22fbde8cf1ac069cb6f6'
[    1.612176] usb 1-11: New USB device found, idVendor=413c, idProduct=1003
[    1.612177] usb 1-11: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.612178] usb 1-11: Product: Dell USB Keyboard Hub
[    1.612179] usb 1-11: Manufacturer: Dell
[    1.612266] usb 1-11: ep 0x81 - rounding interval to 128 microframes, ep desc says 192 microframes
[    1.612702] hub 1-11:1.0: USB hub found
[    1.612757] hub 1-11:1.0: 3 ports detected
[    1.810802] zswap: loaded using pool lzo/zbud
[    1.837325] Key type trusted registered
[    1.865033] Key type encrypted registered
[    1.889567] AppArmor: AppArmor sha1 policy hashing enabled
[    1.914259] ima: No TPM chip found, activating TPM-bypass!
[    1.914375] usb 1-11.1: new full-speed USB device number 4 using xhci_hcd
[    1.963517] evm: HMAC attrs: 0x1
[    1.988512]   Magic number: 0:210:253
[    2.013043] rtc_cmos 00:05: setting system clock to 2016-01-07 00:17:02 UTC (1452125822)
[    2.018865] usb 1-11.1: New USB device found, idVendor=413c, idProduct=2010
[    2.018866] usb 1-11.1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[    2.018866] usb 1-11.1: Product: Dell USB Keyboard
[    2.018867] usb 1-11.1: Manufacturer: Dell
[    2.018956] usb 1-11.1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.018958] usb 1-11.1: ep 0x82 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[    2.188793] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.214117] EDD information not available.
[    2.239275] PM: Hibernation image not present or could not be loaded.
[    2.239577] Freeing unused kernel memory: 1448K (ffffffff81d3a000 - ffffffff81ea4000)
[    2.265148] Write protecting the kernel read-only data: 12288k
[    2.291010] Freeing unused kernel memory: 276K (ffff8800017bb000 - ffff880001800000)
[    2.317173] Freeing unused kernel memory: 196K (ffff880001bcf000 - ffff880001c00000)
[    2.402630] random: systemd-udevd urandom read with 13 bits of entropy available
[    2.432481] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    2.459404] hidraw: raw HID events driver (C) Jiri Kosina
[    2.486729] wmi: Mapper loaded
[    2.513323] clocksource: Switched to clocksource tsc
[    2.541241] pps_core: LinuxPPS API ver. 1 registered
[    2.541288] [drm] Initialized drm 1.1.0 20060810
[    2.567889] usbcore: registered new interface driver usbhid
[    2.567890] usbhid: USB HID core driver
[    2.646904] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    2.674408] ahci 0000:00:17.0: version 3.0
[    2.675546] PTP clock support registered
[    2.702634] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    2.730157] ahci 0000:00:17.0: flags: 64bit ncq sntf led clo only pio slum part ems deso sadm sds apst 
[    2.730453] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11.1/1-11.1:1.0/0003:413C:2010.0001/input/input6
[    2.786167] hid-generic 0003:413C:2010.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:14.0-11.1/input0
[    2.786446] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11.1/1-11.1:1.1/0003:413C:2010.0002/input/input7
[    2.842175] hid-generic 0003:413C:2010.0002: input,hidraw1: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:14.0-11.1/input1
[    2.874933] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    2.904648] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    2.915002] scsi host0: ahci
[    2.915112] scsi host1: ahci
[    2.915211] scsi host2: ahci
[    2.915306] scsi host3: ahci
[    2.915402] scsi host4: ahci
[    2.915498] scsi host5: ahci
[    2.915574] ata1: SATA max UDMA/133 abar m2048@0xdf04b000 port 0xdf04b100 irq 126
[    2.915576] ata2: SATA max UDMA/133 abar m2048@0xdf04b000 port 0xdf04b180 irq 126
[    2.915577] ata3: SATA max UDMA/133 abar m2048@0xdf04b000 port 0xdf04b200 irq 126
[    2.915578] ata4: SATA max UDMA/133 abar m2048@0xdf04b000 port 0xdf04b280 irq 126
[    2.915579] ata5: SATA max UDMA/133 abar m2048@0xdf04b000 port 0xdf04b300 irq 126
[    2.915580] ata6: SATA max UDMA/133 abar m2048@0xdf04b000 port 0xdf04b380 irq 126
[    3.234034] ata6: SATA link down (SStatus 4 SControl 300)
[    3.234048] ata4: SATA link down (SStatus 4 SControl 300)
[    3.234060] ata3: SATA link down (SStatus 4 SControl 300)
[    3.234071] ata5: SATA link down (SStatus 4 SControl 300)
[    3.234082] ata1: SATA link down (SStatus 4 SControl 300)
[    3.242038] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.245978] ata2.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
[    3.245979] ata2.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.249981] ata2.00: configured for UDMA/133
[    3.250068] scsi 1:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M AB51 PQ: 0 ANSI: 5
[    3.250181] sd 1:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.250196] sd 1:0:0:0: [sda] Write Protect is off
[    3.250197] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.250200] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    3.250203] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.290829]  sda: sda1 sda2 < sda5 sda6 >
[    3.290997] sd 1:0:0:0: [sda] Attached SCSI disk
[    3.338159] [drm] Memory usable by graphics device = 4096M
[    3.338160] checking generic (c0000000 7f0000) vs hw (c0000000 10000000)
[    3.338160] fb: switching to inteldrmfb from VESA VGA
[    3.749120] Console: switching to colour dummy device 80x25
[    3.749176] [drm] Replacing VGA console driver
[    3.756344] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.756347] [drm] Driver supports precise vblank timestamp query.
[    3.766006] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.770622] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.770972] acpi device:0f: registered as cooling_device0
[    3.771027] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[    3.771082] [drm] Initialized i915 1.6.0 20150731 for 0000:00:02.0 on minor 0
[    3.771390] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.914599] fbcon: inteldrmfb (fb0) is primary device
[    3.941342] e1000e 0000:00:1f.6 eth0: registered PHC clock
[    3.941344] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) d0:50:99:82:08:b6
[    3.941344] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    3.941374] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF
[    3.941911] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[    4.106197] Console: switching to colour frame buffer device 240x67
[    4.113324] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    4.217235] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.662632] random: nonblocking pool is initialized
[    4.770130] [drm] RC6 on
[    5.023512] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    5.050710] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    5.051198] systemd[1]: Detected architecture x86-64.
[    5.059433] systemd[1]: Set hostname to <icarus>.
[    6.303410] systemd[1]: display-manager.service: Cannot add dependency job, ignoring: Unit display-manager.service failed to load: No such file or directory.
[    6.304530] systemd[1]: Reached target Encrypted Volumes.
[    6.304889] systemd[1]: Created slice Root Slice.
[    6.305129] systemd[1]: Listening on udev Control Socket.
[    6.305380] systemd[1]: Listening on Journal Socket.
[    6.306002] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    6.306403] systemd[1]: Listening on Journal Audit Socket.
[    6.306658] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    6.310150] systemd[1]: Listening on udev Kernel Socket.
[    6.316674] systemd[1]: Reached target User and Group Name Lookups.
[    6.323458] systemd[1]: Created slice User and Session Slice.
[    6.330152] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    6.334786] systemd[1]: Listening on fsck to fsckd communication Socket.
[    6.338387] systemd[1]: Reached target Remote File Systems (Pre).
[    6.341621] systemd[1]: Created slice System Slice.
[    6.344346] systemd[1]: Reached target Slices.
[    6.346856] systemd[1]: Created slice system-getty.slice.
[    6.349149] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    6.351583] systemd[1]: Starting udev Coldplug all Devices...
[    6.353816] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    6.356000] systemd[1]: Mounting POSIX Message Queue File System...
[    6.357975] systemd[1]: Mounting Huge Pages File System...
[    6.359950] systemd[1]: Mounting Debug File System...
[    6.361890] systemd[1]: Starting Increase datagram queue length...
[    6.389953] systemd[1]: Starting Load Kernel Modules...
[    6.427441] systemd[1]: Starting Setup Virtual Console...
[    6.435559] systemd[1]: Started Read required files in advance.
[    6.445248] systemd[1]: Starting Uncomplicated firewall...
[    6.452096] systemd[1]: Listening on Journal Socket (/dev/log).
[    6.457604] systemd[1]: Started Load Kernel Modules.
[    6.461138] systemd[1]: Started Setup Virtual Console.
[    6.464373] systemd[1]: Mounting FUSE Control File System...
[    6.467136] systemd[1]: Starting Apply Kernel Variables...
[    6.513608] systemd[1]: Started Apply Kernel Variables.
[    6.518975] systemd[1]: Started udev Coldplug all Devices.
[    6.550795] systemd[1]: Mounted Debug File System.
[    6.554233] systemd[1]: Mounted POSIX Message Queue File System.
[    6.557571] systemd[1]: Mounted FUSE Control File System.
[    6.560822] systemd[1]: Mounted Huge Pages File System.
[    6.565895] systemd[1]: Started Increase datagram queue length.
[    6.569993] systemd[1]: Listening on Syslog Socket.
[    6.572987] systemd[1]: Starting Journal Service...
[    6.585092] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    6.589661] systemd[1]: Starting Create Static Device Nodes in /dev...
[    6.591256] systemd[1]: Started Uncomplicated firewall.
[    6.772248] systemd[1]: Started Journal Service.
[    7.177898] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    7.268360] systemd-journald[259]: Received request to flush runtime journal from PID 1
[    7.473129] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.654589] parport_pc 00:01: reported by Plug and Play ACPI
[    7.654669] parport0: PC-style at 0x378 (0x778), irq 5, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[    7.663024] Bluetooth: Core ver 2.20
[    7.663033] NET: Registered protocol family 31
[    7.663034] Bluetooth: HCI device and connection manager initialized
[    7.663037] Bluetooth: HCI socket layer initialized
[    7.663039] Bluetooth: L2CAP socket layer initialized
[    7.663042] Bluetooth: SCO socket layer initialized
[    7.694699] 8192cu: module verification failed: signature and/or required key missing - tainting kernel
[    7.760659] usbcore: registered new interface driver rtl8192cu
[    7.808846] AVX2 version of gcm_enc/dec engaged.
[    7.808848] AES CTR mode by8 optimization enabled
[    7.816966] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[    7.852159] Bluetooth: HCI UART driver ver 2.3
[    7.852167] Bluetooth: HCI UART protocol H4 registered
[    7.852172] Bluetooth: HCI UART protocol BCSP registered
[    7.852175] Bluetooth: HCI UART protocol LL registered
[    7.852179] Bluetooth: HCI UART protocol ATH3K registered
[    7.852182] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    7.852243] Bluetooth: HCI UART protocol Intel registered
[    7.852277] Bluetooth: HCI UART protocol BCM registered
[    7.852281] Bluetooth: HCI UART protocol QCA registered
[    7.863790] ppdev: user-space parallel port driver
[    7.868669] rtl8192cu 1-10:1.0 wlx74da38547289: renamed from wlan0
[    8.080398] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    8.158917] intel_rapl: Found RAPL domain package
[    8.158930] intel_rapl: Found RAPL domain core
[    8.158942] intel_rapl: Found RAPL domain uncore
[    8.158951] intel_rapl: Found RAPL domain dram
[    8.189688] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC892: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[    8.189696] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    8.189701] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    8.189705] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    8.189708] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    8.189712] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[    8.189716] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[    8.189720] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[    8.219759] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input9
[    8.219932] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input10
[    8.220106] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
[    8.220254] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[    8.220406] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[    8.220538] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[    8.220682] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[    8.220820] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
[    8.620318] Adding 16307196k swap on /dev/sda5.  Priority:-1 extents:1 across:16307196k FS
[    8.937534] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    8.998684] ifquery[417]: segfault at 1 ip 0000000000403187 sp 00007ffe7b803220 error 4 in ifup[400000+d000]
[    9.648690] audit: type=1400 audit(1452125830.132:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=485 comm="apparmor_parser"
[    9.648708] audit: type=1400 audit(1452125830.132:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=485 comm="apparmor_parser"
[    9.648745] audit: type=1400 audit(1452125830.132:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=485 comm="apparmor_parser"
[    9.648757] audit: type=1400 audit(1452125830.136:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=485 comm="apparmor_parser"
[    9.667624] audit: type=1400 audit(1452125830.152:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=485 comm="apparmor_parser"
[    9.695726] audit: type=1400 audit(1452125830.180:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=485 comm="apparmor_parser"
[   10.013471] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[   11.590195] e1000e: enp0s31f6 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   11.590207] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO
[   11.590270] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready

```

segfault at 8.998684 seems to be a known problem.

I installed the driver from [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)

It always happens to me, that I try to solve a problem for hours, then post to a forum and then I find the problem. In the interfaces file I had a "wlan0" which should be wlx74da38547289. Solved

Well, It works now, but very unstable. I have to restart the network from time to time and it's very slow. I would need some help here.

I think I should delete the old drivers and install the "right" drivers. Wherever I can get them. I don't know.

I give up. Kodi is also not working. All in all, it's very unstable and  nothing seems to work with the 4.3 kernel right now. Also in my home  folder I just saw the following:

```

lrwxrwxrwx   1 root root        32 Jan  7 00:03 initrd.img -> boot/initrd.img-4.2.0-23-generic
lrwxrwxrwx   1 root root        36 Jan  6 23:53 initrd.img.old -> boot/initrd.img-4.3.0-040300-generic

lrwxrwxrwx   1 root root        29 Jan  7 00:03 vmlinuz -> boot/vmlinuz-4.2.0-23-generic
lrwxrwxrwx   1 root root        33 Jan  6 23:53 vmlinuz.old -> boot/vmlinuz-4.3.0-040300-generic

```

When  did that happen? I did nothing in my knowledge to set back the kernel  to 4.2. I think it is better to use debian stable until Ubuntu 16.04 is  out with a newer kernel as standard kernel and use my RPi as media  center until then. :-(


EDIT: Now after a reboot I get: "xyz is not in the sudoers file.  This incident will be reported.". xyz is my user. samba share stopped working and everything else. This was the first and the last time, I install a newer kernel on a linux system.

---

