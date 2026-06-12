---
title: "Realtek RTL8188cus usb wifi poor/no connection"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by john97 on 2013-09-11
Hi forum,

I am having difficulty getting my tp-link WN-723N (Realtek RTL8188cus) to work.
I have compiled 8192cu from realtek and blacklisted the native modules. This is a clean install of ubuntu 12.10.

From ifconfig it seems I am dropping a lot of packets.

Here is the ouput of some wireless related commands:

```
lsusb | grep Realtek

Bus 003 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter

```

```

ifconfig

eth0      Link encap:Ethernet  HWaddr 90:2b:34:9f:59:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7671 (7.6 KB)  TX bytes:7671 (7.6 KB)

wlan0     Link encap:Ethernet  HWaddr 64:70:02:28:e9:38  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6670:2ff:fe28:e938/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:167 overruns:0 frame:0
          TX packets:186 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43379 (43.3 KB)  TX bytes:26092 (26.0 KB)


```

```
iwconfig

wlan0     IEEE 802.11bgn  ESSID:"PlusnetWireless882FD0"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:26:44:88:2F:D0   
          Bit Rate:65 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-64 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
lsmod

nls_iso8859_1          12617  1 
usb_storage            39350  1 
uas                    17556  0 
rfcomm                 37276  0 
bnep                   17707  2 
bluetooth             183228  10 rfcomm,bnep
snd_hda_codec_hdmi     31423  1 
coretemp               13168  0 
snd_hda_codec_realtek    63356  1 
kvm                   357806  0 
8192cu                506828  0 
aesni_intel            17938  0 
cryptd                 15614  1 aesni_intel
aes_i586               16956  1 aesni_intel
snd_hda_intel          32515  5 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ppdev                  12817  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                84843  0 
serio_raw              13031  0 
joydev                 17161  0 
microcode              18209  0 
parport_pc             31968  1 
mac_hid                13037  0 
nouveau               823577  2 
lpc_ich                16925  0 
mei                    35796  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
ttm                    75534  1 nouveau
drm_kms_helper         45271  1 nouveau
drm                   230463  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13197  1 nouveau
mxm_wmi                12859  1 nouveau
video                  18847  1 nouveau
lp                     13299  0 
wmi                    18590  2 nouveau,mxm_wmi
parport                40753  3 ppdev,parport_pc,lp
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
r8169                  55976  0

```

```
dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-17-generic (buildd@roseapple) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 (Ubuntu 3.5.0-17.28-generic 3.5.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000de2f9fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000de2fa000-0x00000000de527fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000de528000-0x00000000de528fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000de529000-0x00000000de64bfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000de64c000-0x00000000dee03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dee04000-0x00000000dee04fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dee05000-0x00000000dee47fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000dee48000-0x00000000df5b1fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000df5b2000-0x00000000df7dcfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df7dd000-0x00000000df7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021dffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. To be filled by O.E.M./B75M-D3H, BIOS F11 08/23/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x21e000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FF0000000 write-back
[    0.000000]   2 base 210000000 mask FF8000000 write-back
[    0.000000]   3 base 218000000 mask FFC000000 write-back
[    0.000000]   4 base 21C000000 mask FFE000000 write-back
[    0.000000]   5 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 256MB, type WB
[    0.000000] reg 2, base: 8448MB, range: 128MB, type WB
[    0.000000] reg 3, base: 8576MB, range: 64MB, type WB
[    0.000000] reg 4, base: 8640MB, range: 32MB, type WB
[    0.000000] reg 5, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 8160M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 6      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 512MB, type WB
[    0.000000] reg 5, base: 8672MB, range: 32MB, type UC
[    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
[    0.000000] found SMP MP-table at [mem 0x000fd7a0-0x000fd7af] mapped at [c00fd7a0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x36332000-0x37190fff]
[    0.000000] ACPI: RSDP 000f0490 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT de62d070 00064 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP de636d98 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT de62d170 09C24 (v02 ALASKA    A M I 00000012 INTL 20051117)
[    0.000000] ACPI: FACS de64af80 00040
[    0.000000] ACPI: APIC de636e90 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG de636f08 0003C (v01                 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET de636f48 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT de636f80 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT de6372f0 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT de637ca0 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: DMAR de638738 00080 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 7780MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x1dffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xde2f9fff]
[    0.000000]   node   0: [mem 0xdee04000-0xdee04fff]
[    0.000000]   node   0: [mem 0xdee48000-0xdf5b1fff]
[    0.000000]   node   0: [mem 0xdf7dd000-0xdf7fffff]
[    0.000000]   node   0: [mem 0x00000000-0x1dffffff]
[    0.000000] On node 0 totalpages: 2083349
[    0.000000] free_area_init_node: node 0, pgdat c18a0840, node_mem_map f1f72200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 15561 pages used for memmap
[    0.000000]   HighMem zone: 1839553 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] e820: [mem 0xdf800000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb2000 s34176 r0 d23168 u57344
[    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2066004
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=6659a6fd-920e-445b-b9e4-65083add5023 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 17760128 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0021e000)
[    0.000000] Memory: 8220248k/8880128k available (5956k kernel code, 113148k reserved, 2928k data, 756k init, 7420456k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc18ae000 - 0xc196b000   ( 756 kB)
[    0.000000]       .data : 0xc15d1358 - 0xc18ad6c0   (2928 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15d1358   (5956 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3192.884 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6385.76 BogoMIPS (lpj=12771536)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000016] Security Framework initialized
[    0.000025] AppArmor: AppArmor initialized
[    0.000025] Yama: becoming mindful.
[    0.000053] Mount-cache hash table entries: 512
[    0.000170] Initializing cgroup subsys cpuacct
[    0.000171] Initializing cgroup subsys memory
[    0.000174] Initializing cgroup subsys devices
[    0.000175] Initializing cgroup subsys freezer
[    0.000176] Initializing cgroup subsys blkio
[    0.000178] Initializing cgroup subsys perf_event
[    0.000196] CPU: Physical Processor ID: 0
[    0.000197] CPU: Processor Core ID: 0
[    0.000200] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000200] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.000750] mce: CPU supports 9 MCE banks
[    0.000760] CPU0: Thermal monitoring enabled (TM1)
[    0.000766] using mwait in idle threads.
[    0.002441] ACPI: Core revision 20120320
[    0.008359] ftrace: allocating 24585 entries in 49 pages
[    0.016554] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016941] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.056535] CPU0: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz stepping 09
[    0.160648] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.160653] ... version:                3
[    0.160653] ... bit width:              48
[    0.160654] ... generic registers:      8
[    0.160655] ... value mask:             0000ffffffffffff
[    0.160656] ... max period:             000000007fffffff
[    0.160656] ... fixed-purpose events:   3
[    0.160657] ... event mask:             00000007000000ff
[    0.160737] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.160777] CPU 1 irqstacks, hard=f750e000 soft=f7518000
[    0.171060] Initializing CPU#1
[    0.160778] Booting Node   0, Processors  #1
[    0.174437] CPU 2 irqstacks, hard=f7540000 soft=f7542000
[    0.184640] Initializing CPU#2
[    0.174439]  #2
[    0.188186] CPU 3 irqstacks, hard=f754c000 soft=f754e000
[    0.188188]  #3 Ok.
[    0.198389] Initializing CPU#3
[    0.201914] Brought up 4 CPUs
[    0.201917] Total of 4 processors activated (25543.07 BogoMIPS).
[    0.204677] devtmpfs: initialized
[    0.204788] EVM: security.selinux
[    0.204789] EVM: security.SMACK64
[    0.204790] EVM: security.capability
[    0.204834] PM: Registering ACPI NVS region [mem 0xde529000-0xde64bfff] (1191936 bytes)
[    0.204844] PM: Registering ACPI NVS region [mem 0xdee05000-0xdee47fff] (274432 bytes)
[    0.205410] dummy: 
[    0.205436] RTC time: 21:54:35, date: 09/10/13
[    0.205458] NET: Registered protocol family 16
[    0.205516] Trying to unpack rootfs image as initramfs...
[    0.205539] EISA bus registered
[    0.205590] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.205591] ACPI: bus type pci registered
[    0.205623] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.205624] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.205625] PCI: Using MMCONFIG for extended config space
[    0.205626] PCI: Using configuration type 1 for base access
[    0.206178] bio: create slab <bio-0> at 0
[    0.206224] ACPI: Added _OSI(Module Device)
[    0.206225] ACPI: Added _OSI(Processor Device)
[    0.206226] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.206228] ACPI: Added _OSI(Processor Aggregator Device)
[    0.207464] ACPI: EC: Look up EC in DSDT
[    0.208896] ACPI: Executed 1 blocks of module-level executable AML code
[    0.228748] ACPI: SSDT de4ca018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.229065] ACPI: Dynamic OEM Table Load:
[    0.229066] ACPI: SSDT   (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.256588] ACPI: SSDT de4cba98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.256923] ACPI: Dynamic OEM Table Load:
[    0.256925] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.260466] ACPI: SSDT de4d7c18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.260777] ACPI: Dynamic OEM Table Load:
[    0.260778] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.280830] ACPI: Interpreter enabled
[    0.280842] ACPI: (supports S0 S3 S4 S5)
[    0.280857] ACPI: Using IOAPIC for interrupt routing
[    0.284752] ACPI: Power Resource [FN00] (off)
[    0.284799] ACPI: Power Resource [FN01] (off)
[    0.284845] ACPI: Power Resource [FN02] (off)
[    0.284890] ACPI: Power Resource [FN03] (off)
[    0.284934] ACPI: Power Resource [FN04] (off)
[    0.285261] ACPI: No dock devices found.
[    0.285266] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.285477] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.285735] pci_root PNP0A08:00: >host bridge window [io  0x0000-0x0cf7]
[    0.285736] pci_root PNP0A08:00: >host bridge window [io  0x0d00-0xffff]
[    0.285738] pci_root PNP0A08:00: >host bridge window [mem 0x000a0000-0x000bffff]
[    0.285739] pci_root PNP0A08:00: >host bridge window [mem 0x000d0000-0x000d3fff]
[    0.285741] pci_root PNP0A08:00: >host bridge window [mem 0x000d4000-0x000d7fff]
[    0.285742] pci_root PNP0A08:00: >host bridge window [mem 0x000d8000-0x000dbfff]
[    0.285743] pci_root PNP0A08:00: >host bridge window [mem 0x000dc000-0x000dffff]
[    0.285744] pci_root PNP0A08:00: >host bridge window [mem 0x000e0000-0x000e3fff]
[    0.285746] pci_root PNP0A08:00: >host bridge window [mem 0x000e4000-0x000e7fff]
[    0.285747] pci_root PNP0A08:00: >host bridge window [mem 0xe0000000-0xfeafffff]
[    0.285768] PCI host bridge to bus 0000:00
[    0.285770] pci_bus 0000:00: >root bus resource [io  0x0000-0x0cf7]
[    0.285771] pci_bus 0000:00: >root bus resource [io  0x0d00-0xffff]
[    0.285772] pci_bus 0000:00: >root bus resource [mem 0x000a0000-0x000bffff]
[    0.285774] pci_bus 0000:00: >root bus resource [mem 0x000d0000-0x000d3fff]
[    0.285775] pci_bus 0000:00: >root bus resource [mem 0x000d4000-0x000d7fff]
[    0.285776] pci_bus 0000:00: >root bus resource [mem 0x000d8000-0x000dbfff]
[    0.285777] pci_bus 0000:00: >root bus resource [mem 0x000dc000-0x000dffff]
[    0.285779] pci_bus 0000:00: >root bus resource [mem 0x000e0000-0x000e3fff]
[    0.285780] pci_bus 0000:00: >root bus resource [mem 0x000e4000-0x000e7fff]
[    0.285781] pci_bus 0000:00: >root bus resource [mem 0xe0000000-0xfeafffff]
[    0.285788] pci 0000:00:00.0: >[8086:0150] type 00 class 0x060000
[    0.285818] pci 0000:00:01.0: >[8086:0151] type 01 class 0x060400
[    0.285844] pci 0000:00:01.0: >PME# supported from D0 D3hot D3cold
[    0.285880] pci 0000:00:14.0: >[8086:1e31] type 00 class 0x0c0330
[    0.285901] pci 0000:00:14.0: >reg 10: [mem 0xf7100000-0xf710ffff 64bit]
[    0.285966] pci 0000:00:14.0: >PME# supported from D3hot D3cold
[    0.285986] pci 0000:00:16.0: >[8086:1e3a] type 00 class 0x078000
[    0.286007] pci 0000:00:16.0: >reg 10: [mem 0xf711a000-0xf711a00f 64bit]
[    0.286079] pci 0000:00:16.0: >PME# supported from D0 D3hot D3cold
[    0.286108] pci 0000:00:1a.0: >[8086:1e2d] type 00 class 0x0c0320
[    0.286127] pci 0000:00:1a.0: >reg 10: [mem 0xf7118000-0xf71183ff]
[    0.286211] pci 0000:00:1a.0: >PME# supported from D0 D3hot D3cold
[    0.286234] pci 0000:00:1b.0: >[8086:1e20] type 00 class 0x040300
[    0.286247] pci 0000:00:1b.0: >reg 10: [mem 0xf7110000-0xf7113fff 64bit]
[    0.286310] pci 0000:00:1b.0: >PME# supported from D0 D3hot D3cold
[    0.286329] pci 0000:00:1c.0: >[8086:1e10] type 01 class 0x060400
[    0.286403] pci 0000:00:1c.0: >PME# supported from D0 D3hot D3cold
[    0.286428] pci 0000:00:1c.4: >[8086:1e18] type 01 class 0x060400
[    0.286502] pci 0000:00:1c.4: >PME# supported from D0 D3hot D3cold
[    0.286531] pci 0000:00:1d.0: >[8086:1e26] type 00 class 0x0c0320
[    0.286550] pci 0000:00:1d.0: >reg 10: [mem 0xf7117000-0xf71173ff]
[    0.286634] pci 0000:00:1d.0: >PME# supported from D0 D3hot D3cold
[    0.286652] pci 0000:00:1e.0: >[8086:244e] type 01 class 0x060401
[    0.286709] pci 0000:00:1f.0: >[8086:1e49] type 00 class 0x060100
[    0.286824] pci 0000:00:1f.2: >[8086:1e02] type 00 class 0x010601
[    0.286841] pci 0000:00:1f.2: >reg 10: [io  0xf070-0xf077]
[    0.286847] pci 0000:00:1f.2: >reg 14: [io  0xf060-0xf063]
[    0.286854] pci 0000:00:1f.2: >reg 18: [io  0xf050-0xf057]
[    0.286861] pci 0000:00:1f.2: >reg 1c: [io  0xf040-0xf043]
[    0.286867] pci 0000:00:1f.2: >reg 20: [io  0xf020-0xf03f]
[    0.286874] pci 0000:00:1f.2: >reg 24: [mem 0xf7116000-0xf71167ff]
[    0.286915] pci 0000:00:1f.2: >PME# supported from D3hot
[    0.286930] pci 0000:00:1f.3: >[8086:1e22] type 00 class 0x0c0500
[    0.286943] pci 0000:00:1f.3: >reg 10: [mem 0xf7115000-0xf71150ff 64bit]
[    0.286962] pci 0000:00:1f.3: >reg 20: [io  0xf000-0xf01f]
[    0.287010] pci 0000:01:00.0: >[10de:11c6] type 00 class 0x030000
[    0.287018] pci 0000:01:00.0: >reg 10: [mem 0xf6000000-0xf6ffffff]
[    0.287027] pci 0000:01:00.0: >reg 14: [mem 0xe8000000-0xefffffff 64bit pref]
[    0.287036] pci 0000:01:00.0: >reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.287042] pci 0000:01:00.0: >reg 24: [io  0xe000-0xe07f]
[    0.287048] pci 0000:01:00.0: >reg 30: [mem 0xf7000000-0xf707ffff pref]
[    0.287098] pci 0000:01:00.1: >[10de:0e0b] type 00 class 0x040300
[    0.287106] pci 0000:01:00.1: >reg 10: [mem 0xf7080000-0xf7083fff]
[    0.292353] pci 0000:00:01.0: >PCI bridge to [bus 01-01]
[    0.292355] pci 0000:00:01.0: >  bridge window [io  0xe000-0xefff]
[    0.292357] pci 0000:00:01.0: >  bridge window [mem 0xf6000000-0xf70fffff]
[    0.292360] pci 0000:00:01.0: >  bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.292400] pci 0000:00:1c.0: >PCI bridge to [bus 02-02]
[    0.292469] pci 0000:03:00.0: >[10ec:8168] type 00 class 0x020000
[    0.292488] pci 0000:03:00.0: >reg 10: [io  0xd000-0xd0ff]
[    0.292520] pci 0000:03:00.0: >reg 18: [mem 0xf2104000-0xf2104fff 64bit pref]
[    0.292541] pci 0000:03:00.0: >reg 20: [mem 0xf2100000-0xf2103fff 64bit pref]
[    0.292630] pci 0000:03:00.0: >supports D1 D2
[    0.292631] pci 0000:03:00.0: >PME# supported from D0 D1 D2 D3hot D3cold
[    0.300338] pci 0000:00:1c.4: >PCI bridge to [bus 03-03]
[    0.300341] pci 0000:00:1c.4: >  bridge window [io  0xd000-0xdfff]
[    0.300348] pci 0000:00:1c.4: >  bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.300403] pci 0000:00:1e.0: >PCI bridge to [bus 04-04] (subtractive decode)
[    0.300411] pci 0000:00:1e.0: >  bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.300412] pci 0000:00:1e.0: >  bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.300414] pci 0000:00:1e.0: >  bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.300415] pci 0000:00:1e.0: >  bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.300416] pci 0000:00:1e.0: >  bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.300417] pci 0000:00:1e.0: >  bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.300419] pci 0000:00:1e.0: >  bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.300420] pci 0000:00:1e.0: >  bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.300421] pci 0000:00:1e.0: >  bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.300423] pci 0000:00:1e.0: >  bridge window [mem 0xe0000000-0xfeafffff] (subtractive decode)
[    0.300437] pci_bus 0000:00: >on NUMA node 0
[    0.300439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.300557] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.300598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.300625] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.300652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.300739]  pci0000:00: >Requesting ACPI _OSC control (0x1d)
[    0.300856]  pci0000:00: >ACPI _OSC control (0x18) granted
[    0.303413] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.303443] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.303470] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.303498] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.303525] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.303553] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.303580] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.303607] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.303665] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.303667] vgaarb: loaded
[    0.303667] vgaarb: bridge control possible 0000:01:00.0
[    0.303775] SCSI subsystem initialized
[    0.303799] libata version 3.00 loaded.
[    0.303812] ACPI: bus type usb registered
[    0.303824] usbcore: registered new interface driver usbfs
[    0.303829] usbcore: registered new interface driver hub
[    0.303840] usbcore: registered new device driver usb
[    0.303880] PCI: Using ACPI for IRQ routing
[    0.305320] PCI: pci_cache_line_size set to 64 bytes
[    0.305365] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.305367] e820: reserve RAM buffer [mem 0xde2fa000-0xdfffffff]
[    0.305369] e820: reserve RAM buffer [mem 0xdee05000-0xdfffffff]
[    0.305370] e820: reserve RAM buffer [mem 0xdf5b2000-0xdfffffff]
[    0.305371] e820: reserve RAM buffer [mem 0xdf800000-0xdfffffff]
[    0.305372] e820: reserve RAM buffer [mem 0x21e000000-0x21fffffff]
[    0.305427] NetLabel: Initializing
[    0.305428] NetLabel:  domain hash size = 128
[    0.305428] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.305436] NetLabel:  unlabeled traffic allowed by default
[    0.305497] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.305501] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.307507] Switching to clocksource hpet
[    0.312162] AppArmor: AppArmor Filesystem Enabled
[    0.312172] pnp: PnP ACPI init
[    0.312179] ACPI: bus type pnp registered
[    0.312343] pnp 00:00: >[bus 00-3e]
[    0.312345] pnp 00:00: >[io  0x0000-0x0cf7 window]
[    0.312346] pnp 00:00: >[io  0x0cf8-0x0cff]
[    0.312347] pnp 00:00: >[io  0x0d00-0xffff window]
[    0.312349] pnp 00:00: >[mem 0x000a0000-0x000bffff window]
[    0.312350] pnp 00:00: >[mem 0x000c0000-0x000c3fff window]
[    0.312351] pnp 00:00: >[mem 0x000c4000-0x000c7fff window]
[    0.312352] pnp 00:00: >[mem 0x000c8000-0x000cbfff window]
[    0.312354] pnp 00:00: >[mem 0x000cc000-0x000cffff window]
[    0.312355] pnp 00:00: >[mem 0x000d0000-0x000d3fff window]
[    0.312356] pnp 00:00: >[mem 0x000d4000-0x000d7fff window]
[    0.312357] pnp 00:00: >[mem 0x000d8000-0x000dbfff window]
[    0.312358] pnp 00:00: >[mem 0x000dc000-0x000dffff window]
[    0.312360] pnp 00:00: >[mem 0x000e0000-0x000e3fff window]
[    0.312361] pnp 00:00: >[mem 0x000e4000-0x000e7fff window]
[    0.312362] pnp 00:00: >[mem 0x000e8000-0x000ebfff window]
[    0.312363] pnp 00:00: >[mem 0x000ec000-0x000effff window]
[    0.312364] pnp 00:00: >[mem 0x000f0000-0x000fffff window]
[    0.312366] pnp 00:00: >[mem 0xe0000000-0xfeafffff window]
[    0.312367] pnp 00:00: >[mem 0x00010000-0x0001ffff window]
[    0.312407] pnp 00:00: >Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.312421] pnp 00:01: >[mem 0xfed40000-0xfed44fff]
[    0.312443] system 00:01: >[mem 0xfed40000-0xfed44fff] has been reserved
[    0.312445] system 00:01: >Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.312452] pnp 00:02: >[io  0x0000-0x001f]
[    0.312454] pnp 00:02: >[io  0x0081-0x0091]
[    0.312455] pnp 00:02: >[io  0x0093-0x009f]
[    0.312456] pnp 00:02: >[io  0x00c0-0x00df]
[    0.312457] pnp 00:02: >[dma 4]
[    0.312468] pnp 00:02: >Plug and Play ACPI device, IDs PNP0200 (active)
[    0.312473] pnp 00:03: >[mem 0xff000000-0xffffffff]
[    0.312485] pnp 00:03: >Plug and Play ACPI device, IDs INT0800 (active)
[    0.312525] pnp 00:04: >[mem 0xfed00000-0xfed003ff]
[    0.312537] pnp 00:04: >Plug and Play ACPI device, IDs PNP0103 (active)
[    0.312544] pnp 00:05: >[io  0x002e-0x002f]
[    0.312545] pnp 00:05: >[io  0x004e-0x004f]
[    0.312547] pnp 00:05: >[io  0x0061]
[    0.312548] pnp 00:05: >[io  0x0063]
[    0.312549] pnp 00:05: >[io  0x0065]
[    0.312550] pnp 00:05: >[io  0x0067]
[    0.312551] pnp 00:05: >[io  0x0070]
[    0.312552] pnp 00:05: >[io  0x0080]
[    0.312553] pnp 00:05: >[io  0x0092]
[    0.312554] pnp 00:05: >[io  0x00b2-0x00b3]
[    0.312555] pnp 00:05: >[io  0x0680-0x069f]
[    0.312556] pnp 00:05: >[io  0x0200-0x020f]
[    0.312557] pnp 00:05: >[io  0xffff]
[    0.312559] pnp 00:05: >[io  0xffff]
[    0.312560] pnp 00:05: >[io  0x0400-0x0453]
[    0.312561] pnp 00:05: >[io  0x0458-0x047f]
[    0.312562] pnp 00:05: >[io  0x0500-0x057f]
[    0.312584] system 00:05: >[io  0x0680-0x069f] has been reserved
[    0.312586] system 00:05: >[io  0x0200-0x020f] has been reserved
[    0.312588] system 00:05: >[io  0xffff] has been reserved
[    0.312589] system 00:05: >[io  0xffff] has been reserved
[    0.312590] system 00:05: >[io  0x0400-0x0453] has been reserved
[    0.312592] system 00:05: >[io  0x0458-0x047f] has been reserved
[    0.312593] system 00:05: >[io  0x0500-0x057f] has been reserved
[    0.312595] system 00:05: >Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.312599] pnp 00:06: >[io  0x0070-0x0077]
[    0.312606] pnp 00:06: >[irq 8]
[    0.312618] pnp 00:06: >Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.312633] pnp 00:07: >[io  0x0454-0x0457]
[    0.312651] system 00:07: >[io  0x0454-0x0457] has been reserved
[    0.312653] system 00:07: >Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.312712] pnp 00:08: >[io  0x0000-0xffffffffffffffff disabled]
[    0.312714] pnp 00:08: >[io  0x0a00-0x0a0f]
[    0.312715] pnp 00:08: >[io  0x0a30-0x0a3f]
[    0.312716] pnp 00:08: >[io  0x0a20-0x0a2f]
[    0.312736] system 00:08: >[io  0x0a00-0x0a0f] has been reserved
[    0.312737] system 00:08: >[io  0x0a30-0x0a3f] has been reserved
[    0.312739] system 00:08: >[io  0x0a20-0x0a2f] has been reserved
[    0.312740] system 00:08: >Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.312913] pnp 00:09: >[io  0x03f8-0x03ff]
[    0.312917] pnp 00:09: >[irq 4]
[    0.312918] pnp 00:09: >[dma 0 disabled]
[    0.312951] pnp 00:09: >Plug and Play ACPI device, IDs PNP0501 (active)
[    0.313148] pnp 00:0a: >[io  0x0378-0x037f]
[    0.313151] pnp 00:0a: >[irq 7]
[    0.313153] pnp 00:0a: >[dma 0 disabled]
[    0.313234] pnp 00:0a: >Plug and Play ACPI device, IDs PNP0400 (active)
[    0.313247] pnp 00:0b: >[io  0x0010-0x001f]
[    0.313248] pnp 00:0b: >[io  0x0022-0x003f]
[    0.313249] pnp 00:0b: >[io  0x0044-0x005f]
[    0.313250] pnp 00:0b: >[io  0x0062-0x0063]
[    0.313251] pnp 00:0b: >[io  0x0065-0x006f]
[    0.313252] pnp 00:0b: >[io  0x0072-0x007f]
[    0.313253] pnp 00:0b: >[io  0x0080]
[    0.313255] pnp 00:0b: >[io  0x0084-0x0086]
[    0.313256] pnp 00:0b: >[io  0x0088]
[    0.313257] pnp 00:0b: >[io  0x008c-0x008e]
[    0.313258] pnp 00:0b: >[io  0x0090-0x009f]
[    0.313259] pnp 00:0b: >[io  0x00a2-0x00bf]
[    0.313260] pnp 00:0b: >[io  0x00e0-0x00ef]
[    0.313261] pnp 00:0b: >[io  0x04d0-0x04d1]
[    0.313284] system 00:0b: >[io  0x04d0-0x04d1] has been reserved
[    0.313286] system 00:0b: >Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.313291] pnp 00:0c: >[io  0x00f0-0x00ff]
[    0.313294] pnp 00:0c: >[irq 13]
[    0.313308] pnp 00:0c: >Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.313451] pnp 00:0d: >[mem 0xfed1c000-0xfed1ffff]
[    0.313452] pnp 00:0d: >[mem 0xfed10000-0xfed17fff]
[    0.313453] pnp 00:0d: >[mem 0xfed18000-0xfed18fff]
[    0.313454] pnp 00:0d: >[mem 0xfed19000-0xfed19fff]
[    0.313456] pnp 00:0d: >[mem 0xf8000000-0xfbffffff]
[    0.313457] pnp 00:0d: >[mem 0xfed20000-0xfed3ffff]
[    0.313458] pnp 00:0d: >[mem 0xfed90000-0xfed93fff]
[    0.313459] pnp 00:0d: >[mem 0xfed45000-0xfed8ffff]
[    0.313460] pnp 00:0d: >[mem 0xff000000-0xffffffff]
[    0.313461] pnp 00:0d: >[mem 0xfee00000-0xfeefffff]
[    0.313462] pnp 00:0d: >[mem 0xe0000000-0xe0000fff]
[    0.313497] system 00:0d: >[mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.313499] system 00:0d: >[mem 0xfed10000-0xfed17fff] has been reserved
[    0.313500] system 00:0d: >[mem 0xfed18000-0xfed18fff] has been reserved
[    0.313502] system 00:0d: >[mem 0xfed19000-0xfed19fff] has been reserved
[    0.313503] system 00:0d: >[mem 0xf8000000-0xfbffffff] has been reserved
[    0.313505] system 00:0d: >[mem 0xfed20000-0xfed3ffff] has been reserved
[    0.313506] system 00:0d: >[mem 0xfed90000-0xfed93fff] has been reserved
[    0.313509] system 00:0d: >[mem 0xfed45000-0xfed8ffff] has been reserved
[    0.313510] system 00:0d: >[mem 0xff000000-0xffffffff] has been reserved
[    0.313512] system 00:0d: >[mem 0xfee00000-0xfeefffff] could not be reserved
[    0.313513] system 00:0d: >[mem 0xe0000000-0xe0000fff] has been reserved
[    0.313515] system 00:0d: >Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.313600] pnp: PnP ACPI: found 14 devices
[    0.313601] ACPI: ACPI bus type pnp unregistered
[    0.313603] PnPBIOS: Disabled by ACPI PNP
[    0.349146] pci 0000:00:01.0: >PCI bridge to [bus 01-01]
[    0.349150] pci 0000:00:01.0: >  bridge window [io  0xe000-0xefff]
[    0.349153] pci 0000:00:01.0: >  bridge window [mem 0xf6000000-0xf70fffff]
[    0.349155] pci 0000:00:01.0: >  bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.349157] pci 0000:00:1c.0: >PCI bridge to [bus 02-02]
[    0.349167] pci 0000:00:1c.4: >PCI bridge to [bus 03-03]
[    0.349170] pci 0000:00:1c.4: >  bridge window [io  0xd000-0xdfff]
[    0.349176] pci 0000:00:1c.4: >  bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.349181] pci 0000:00:1e.0: >PCI bridge to [bus 04-04]
[    0.349211] pci 0000:00:1e.0: >setting latency timer to 64
[    0.349214] pci_bus 0000:00: >resource 4 [io  0x0000-0x0cf7]
[    0.349215] pci_bus 0000:00: >resource 5 [io  0x0d00-0xffff]
[    0.349217] pci_bus 0000:00: >resource 6 [mem 0x000a0000-0x000bffff]
[    0.349218] pci_bus 0000:00: >resource 7 [mem 0x000d0000-0x000d3fff]
[    0.349219] pci_bus 0000:00: >resource 8 [mem 0x000d4000-0x000d7fff]
[    0.349220] pci_bus 0000:00: >resource 9 [mem 0x000d8000-0x000dbfff]
[    0.349222] pci_bus 0000:00: >resource 10 [mem 0x000dc000-0x000dffff]
[    0.349223] pci_bus 0000:00: >resource 11 [mem 0x000e0000-0x000e3fff]
[    0.349224] pci_bus 0000:00: >resource 12 [mem 0x000e4000-0x000e7fff]
[    0.349226] pci_bus 0000:00: >resource 13 [mem 0xe0000000-0xfeafffff]
[    0.349227] pci_bus 0000:01: >resource 0 [io  0xe000-0xefff]
[    0.349228] pci_bus 0000:01: >resource 1 [mem 0xf6000000-0xf70fffff]
[    0.349230] pci_bus 0000:01: >resource 2 [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.349231] pci_bus 0000:03: >resource 0 [io  0xd000-0xdfff]
[    0.349233] pci_bus 0000:03: >resource 2 [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.349234] pci_bus 0000:04: >resource 4 [io  0x0000-0x0cf7]
[    0.349235] pci_bus 0000:04: >resource 5 [io  0x0d00-0xffff]
[    0.349237] pci_bus 0000:04: >resource 6 [mem 0x000a0000-0x000bffff]
[    0.349238] pci_bus 0000:04: >resource 7 [mem 0x000d0000-0x000d3fff]
[    0.349239] pci_bus 0000:04: >resource 8 [mem 0x000d4000-0x000d7fff]
[    0.349240] pci_bus 0000:04: >resource 9 [mem 0x000d8000-0x000dbfff]
[    0.349242] pci_bus 0000:04: >resource 10 [mem 0x000dc000-0x000dffff]
[    0.349243] pci_bus 0000:04: >resource 11 [mem 0x000e0000-0x000e3fff]
[    0.349244] pci_bus 0000:04: >resource 12 [mem 0x000e4000-0x000e7fff]
[    0.349246] pci_bus 0000:04: >resource 13 [mem 0xe0000000-0xfeafffff]
[    0.349266] NET: Registered protocol family 2
[    0.349301] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.349363] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.349499] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.349561] TCP: Hash tables configured (established 131072 bind 65536)
[    0.349562] TCP: reno registered
[    0.349564] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.349567] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.349594] NET: Registered protocol family 1
[    0.387559] pci 0000:01:00.0: >Boot video device
[    0.387571] PCI: CLS 64 bytes, default 64
[    0.387574] DMAR: Host address width 36
[    0.387575] DMAR: DRHD base: 0x000000fed90000 flags: 0x1
[    0.387580] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.387581] DMAR: RMRR base: 0x000000de491000 end: 0x000000de4bbfff
[    0.387898] audit: initializing netlink socket (disabled)
[    0.387905] type=2000 audit(1378850075.280:1): initialized
[    0.399269] Freeing initrd memory: 14716k freed
[    0.402440] highmem bounce pool size: 64 pages
[    0.402447] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.403868] VFS: Disk quotas dquot_6.5.2
[    0.403894] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.404175] fuse init (API version 7.19)
[    0.404222] msgmni has been set to 1590
[    0.404431] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.404446] io scheduler noop registered
[    0.404447] io scheduler deadline registered (default)
[    0.404451] io scheduler cfq registered
[    0.404526] pcieport 0000:00:01.0: >irq 40 for MSI/MSI-X
[    0.404639] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.404649] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.404690] intel_idle: MWAIT substates: 0x1120
[    0.404690] intel_idle: v0.4 model 0x3A
[    0.404691] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.404747] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.404751] ACPI: Power Button [PWRB]
[    0.404773] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.404775] ACPI: Power Button [PWRF]
[    0.404824] ACPI: Fan [FAN0] (off)
[    0.404841] ACPI: Fan [FAN1] (off)
[    0.404856] ACPI: Fan [FAN2] (off)
[    0.404872] ACPI: Fan [FAN3] (off)
[    0.404887] ACPI: Fan [FAN4] (off)
[    0.404922] ACPI: Requesting acpi_cpufreq
[    0.407722] thermal LNXTHERM:00: >registered as thermal_zone0
[    0.407724] ACPI: Thermal Zone [TZ00] (28 C)
[    0.407822] thermal LNXTHERM:01: >registered as thermal_zone1
[    0.407823] ACPI: Thermal Zone [TZ01] (30 C)
[    0.407846] GHES: HEST is not enabled!
[    0.407864] isapnp: Scanning for PnP cards...
[    0.407887] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.428223] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.449145] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.449312] Linux agpgart interface v0.103
[    0.450037] brd: module loaded
[    0.450421] loop: module loaded
[    0.450475] ahci 0000:00:1f.2: >version 3.0
[    0.450510] ahci 0000:00:1f.2: >irq 41 for MSI/MSI-X
[    0.450556] ahci 0000:00:1f.2: >AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
[    0.450558] ahci 0000:00:1f.2: >flags: 64bit ncq led clo pio slum part ems apst 
[    0.450561] ahci 0000:00:1f.2: >setting latency timer to 64
[    0.455619] scsi0 : ahci
[    0.455659] scsi1 : ahci
[    0.455689] scsi2 : ahci
[    0.455719] scsi3 : ahci
[    0.455751] scsi4 : ahci
[    0.455781] scsi5 : ahci
[    0.455944] ata1: SATA max UDMA/133 abar m2048@0xf7116000 port 0xf7116100 irq 41
[    0.455946] ata2: SATA max UDMA/133 abar m2048@0xf7116000 port 0xf7116180 irq 41
[    0.455946] ata3: DUMMY
[    0.455947] ata4: DUMMY
[    0.455948] ata5: DUMMY
[    0.455949] ata6: DUMMY
[    0.456104] Fixed MDIO Bus: probed
[    0.456128] tun: Universal TUN/TAP device driver, 1.6
[    0.456129] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.456149] PPP generic driver version 2.4.2
[    0.456171] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.456189] ehci_hcd 0000:00:1a.0: >setting latency timer to 64
[    0.456191] ehci_hcd 0000:00:1a.0: >EHCI Host Controller
[    0.456195] ehci_hcd 0000:00:1a.0: >new USB bus registered, assigned bus number 1
[    0.456212] ehci_hcd 0000:00:1a.0: >debug port 2
[    0.460090] ehci_hcd 0000:00:1a.0: >cache line size of 64 is not supported
[    0.460100] ehci_hcd 0000:00:1a.0: >irq 16, io mem 0xf7118000
[    0.471343] ehci_hcd 0000:00:1a.0: >USB 2.0 started, EHCI 1.00
[    0.471356] usb usb1: >New USB device found, idVendor=1d6b, idProduct=0002
[    0.471358] usb usb1: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.471359] usb usb1: >Product: EHCI Host Controller
[    0.471360] usb usb1: >Manufacturer: Linux 3.5.0-17-generic ehci_hcd
[    0.471362] usb usb1: >SerialNumber: 0000:00:1a.0
[    0.471428] hub 1-0:1.0: >USB hub found
[    0.471431] hub 1-0:1.0: >2 ports detected
[    0.471470] ehci_hcd 0000:00:1d.0: >setting latency timer to 64
[    0.471473] ehci_hcd 0000:00:1d.0: >EHCI Host Controller
[    0.471475] ehci_hcd 0000:00:1d.0: >new USB bus registered, assigned bus number 2
[    0.471491] ehci_hcd 0000:00:1d.0: >debug port 2
[    0.475374] ehci_hcd 0000:00:1d.0: >cache line size of 64 is not supported
[    0.475383] ehci_hcd 0000:00:1d.0: >irq 23, io mem 0xf7117000
[    0.487306] ehci_hcd 0000:00:1d.0: >USB 2.0 started, EHCI 1.00
[    0.487313] usb usb2: >New USB device found, idVendor=1d6b, idProduct=0002
[    0.487314] usb usb2: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.487315] usb usb2: >Product: EHCI Host Controller
[    0.487316] usb usb2: >Manufacturer: Linux 3.5.0-17-generic ehci_hcd
[    0.487317] usb usb2: >SerialNumber: 0000:00:1d.0
[    0.487373] hub 2-0:1.0: >USB hub found
[    0.487375] hub 2-0:1.0: >2 ports detected
[    0.487409] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.487417] uhci_hcd: USB Universal Host Controller Interface driver
[    0.487440] xhci_hcd 0000:00:14.0: >setting latency timer to 64
[    0.487442] xhci_hcd 0000:00:14.0: >xHCI Host Controller
[    0.487445] xhci_hcd 0000:00:14.0: >new USB bus registered, assigned bus number 3
[    0.487518] xhci_hcd 0000:00:14.0: >cache line size of 64 is not supported
[    0.487521] xhci_hcd 0000:00:14.0: >irq 16, io mem 0xf7100000
[    0.487556] xhci_hcd 0000:00:14.0: >irq 42 for MSI/MSI-X
[    0.487590] usb usb3: >New USB device found, idVendor=1d6b, idProduct=0002
[    0.487591] usb usb3: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.487593] usb usb3: >Product: xHCI Host Controller
[    0.487594] usb usb3: >Manufacturer: Linux 3.5.0-17-generic xhci_hcd
[    0.487595] usb usb3: >SerialNumber: 0000:00:14.0
[    0.487636] xHCI xhci_add_endpoint called for root hub
[    0.487637] xHCI xhci_check_bandwidth called for root hub
[    0.487649] hub 3-0:1.0: >USB hub found
[    0.487654] hub 3-0:1.0: >4 ports detected
[    0.487687] xhci_hcd 0000:00:14.0: >xHCI Host Controller
[    0.487689] xhci_hcd 0000:00:14.0: >new USB bus registered, assigned bus number 4
[    0.487702] usb usb4: >New USB device found, idVendor=1d6b, idProduct=0003
[    0.487703] usb usb4: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.487704] usb usb4: >Product: xHCI Host Controller
[    0.487705] usb usb4: >Manufacturer: Linux 3.5.0-17-generic xhci_hcd
[    0.487706] usb usb4: >SerialNumber: 0000:00:14.0
[    0.487744] xHCI xhci_add_endpoint called for root hub
[    0.487745] xHCI xhci_check_bandwidth called for root hub
[    0.487756] hub 4-0:1.0: >USB hub found
[    0.487761] hub 4-0:1.0: >4 ports detected
[    0.760056] isapnp: No Plug & Play device found
[    0.762771] usbcore: registered new interface driver libusual
[    0.762797] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.763193] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.763197] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.763267] mousedev: PS/2 mouse device common for all mice
[    0.763347] rtc_cmos 00:06: >RTC can wake from S4
[    0.763444] rtc_cmos 00:06: >rtc core: registered rtc_cmos as rtc0
[    0.763467] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.763492] device-mapper: uevent: version 1.0.3
[    0.763527] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.763541] EISA: Probing bus 0 at eisa.0
[    0.763543] EISA: Cannot allocate resource for mainboard
[    0.763544] Cannot allocate resource for EISA slot 1
[    0.763545] Cannot allocate resource for EISA slot 2
[    0.763546] Cannot allocate resource for EISA slot 3
[    0.763547] Cannot allocate resource for EISA slot 4
[    0.763547] Cannot allocate resource for EISA slot 5
[    0.763548] Cannot allocate resource for EISA slot 6
[    0.763549] Cannot allocate resource for EISA slot 7
[    0.763550] Cannot allocate resource for EISA slot 8
[    0.763550] EISA: Detected 0 cards.
[    0.763591] cpuidle: using governor ladder
[    0.763644] cpuidle: using governor menu
[    0.763645] EFI Variables Facility v0.08 2004-May-17
[    0.763781] ashmem: initialized
[    0.763856] TCP: cubic registered
[    0.763912] NET: Registered protocol family 10
[    0.764019] NET: Registered protocol family 17
[    0.764025] Key type dns_resolver registered
[    0.764069] Using IPI No-Shortcut mode
[    0.764153] PM: Hibernation image not present or could not be loaded.
[    0.764157] registered taskstats version 1
[    0.766223] Key type trusted registered
[    0.767924] Key type encrypted registered
[    0.769515]   Magic number: 13:887:954
[    0.769613] rtc_cmos 00:06: >setting system clock to 2013-09-10 21:54:36 UTC (1378850076)
[    0.770107] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.770108] EDD information not available.
[    0.774688] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.774717] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.775147] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.775154] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node f74308b8), AE_NOT_FOUND (20120320/psparse-536)
[    0.775549] ata2.00: ATA-8: ST2000DM001-1CH164, CC44, max UDMA/133
[    0.775552] ata2.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.776064] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.776070] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node f74308b8), AE_NOT_FOUND (20120320/psparse-536)
[    0.776434] ata2.00: configured for UDMA/133
[    0.777165] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.777170] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node f7430870), AE_NOT_FOUND (20120320/psparse-536)
[    0.777180] ata1.00: ATAPI: HL-DT-ST DVDRAM GH24NS95, RN00, max UDMA/133
[    0.778753] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.778758] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node f7430870), AE_NOT_FOUND (20120320/psparse-536)
[    0.778769] ata1.00: configured for UDMA/133
[    0.782654] usb 1-1: >new high-speed USB device number 2 using ehci_hcd
[    0.793975] scsi 0:0:0:0: >CD-ROM            HL-DT-ST DVDRAM GH24NS95  RN00 PQ: 0 ANSI: 5
[    0.804231] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.804234] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.804420] sr 0:0:0:0: >Attached scsi CD-ROM sr0
[    0.804506] sr 0:0:0:0: >Attached scsi generic sg0 type 5
[    0.804799] scsi 1:0:0:0: >Direct-Access     ATA      ST2000DM001-1CH1 CC44 PQ: 0 ANSI: 5
[    0.804916] sd 1:0:0:0: >Attached scsi generic sg1 type 0
[    0.804973] sd 1:0:0:0: >[sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    0.804975] sd 1:0:0:0: >[sda] 4096-byte physical blocks
[    0.805162] sd 1:0:0:0: >[sda] Write Protect is off
[    0.805165] sd 1:0:0:0: >[sda] Mode Sense: 00 3a 00 00
[    0.805251] sd 1:0:0:0: >[sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.852208]  sda: sda1 sda2 < sda5 >
[    0.853063] sd 1:0:0:0: >[sda] Attached SCSI disk
[    0.853260] Freeing unused kernel memory: 756k freed
[    0.853434] Write protecting the kernel text: 5960k
[    0.853483] Write protecting the kernel read-only data: 2424k
[    0.853483] NX-protecting the kernel data: 4280k
[    0.863471] udevd[111]: starting version 175
[    0.875373] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.880331] r8169 0000:03:00.0: >irq 43 for MSI/MSI-X
[    0.880479] r8169 0000:03:00.0: >eth0: RTL8168evl/8111evl at 0xf841c000, 90:2b:34:9f:59:02, XID 0c900800 IRQ 43
[    0.880481] r8169 0000:03:00.0: >eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.914769] usb 1-1: >New USB device found, idVendor=8087, idProduct=0024
[    0.914775] usb 1-1: >New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.915166] hub 1-1:1.0: >USB hub found
[    0.915253] hub 1-1:1.0: >6 ports detected
[    1.026090] usb 2-1: >new high-speed USB device number 2 using ehci_hcd
[    1.158220] usb 2-1: >New USB device found, idVendor=8087, idProduct=0024
[    1.158224] usb 2-1: >New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.158499] hub 2-1:1.0: >USB hub found
[    1.158567] hub 2-1:1.0: >6 ports detected
[    1.325413] usb 3-1: >new high-speed USB device number 2 using xhci_hcd
[    1.342963] usb 3-1: >New USB device found, idVendor=0bda, idProduct=8176
[    1.342967] usb 3-1: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.342970] usb 3-1: >Product: 802.11n WLAN Adapter
[    1.342972] usb 3-1: >Manufacturer: Realtek
[    1.342975] usb 3-1: >SerialNumber: 00e04c000001
[    1.343181] usb 3-1: >ep 0x81 - rounding interval to 32768 microframes, ep desc says 0 microframes
[    1.343185] usb 3-1: >ep 0x2 - rounding interval to 32768 microframes, ep desc says 0 microframes
[    1.343187] usb 3-1: >ep 0x3 - rounding interval to 32768 microframes, ep desc says 0 microframes
[    1.385271] Refined TSC clocksource calibration: 3192.747 MHz.
[    1.385276] Switching to clocksource tsc
[    1.413351] usb 1-1.3: >new low-speed USB device number 3 using ehci_hcd
[    1.510899] usb 1-1.3: >New USB device found, idVendor=046d, idProduct=c51b
[    1.510903] usb 1-1.3: >New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.510906] usb 1-1.3: >Product: USB Receiver
[    1.510908] usb 1-1.3: >Manufacturer: Logitech
[    1.519398] usbcore: registered new interface driver usbhid
[    1.519401] usbhid: USB HID core driver
[    1.520649] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input2
[    1.520706] hid-generic 0003:046D:C51B.0001: >input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1.3/input0
[    1.521342] hid-generic 0003:046D:C51B.0002: >hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.3/input1
[    1.585003] usb 1-1.5: >new low-speed USB device number 4 using ehci_hcd
[    1.602042] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.602044] EXT4-fs (sda1): write access will be enabled during recovery
[    1.684979] usb 1-1.5: >New USB device found, idVendor=0518, idProduct=0001
[    1.684984] usb 1-1.5: >New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.684987] usb 1-1.5: >Product: USB-compliant keyboard
[    1.684989] usb 1-1.5: >Manufacturer: Plus More Enterprise LTD.
[    1.688253] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input3
[    1.688351] hid-generic 0003:0518:0001.0003: >input,hidraw2: USB HID v1.10 Keyboard [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:1a.0-1.5/input0
[    1.691634] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.1/input/input4
[    1.691940] hid-generic 0003:0518:0001.0004: >input,hidraw3: USB HID v1.10 Mouse [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:1a.0-1.5/input1
[    2.346464] EXT4-fs (sda1): recovery complete
[    2.351940] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.032032] Adding 8332284k swap on /dev/sda5.  Priority:-1 extents:1 across:8332284k 
[    8.035295] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.055467] udevd[372]: starting version 175
[    8.086216] wmi: Mapper loaded
[    8.087391] [drm] Initialized drm 1.1.0 20060810
[    8.088356] mei 0000:00:16.0: >setting latency timer to 64
[    8.088403] mei 0000:00:16.0: >irq 44 for MSI/MSI-X
[    8.089263] lp: driver loaded but no devices found
[    8.090373] [drm] nouveau 0000:01:00.0: Detected an NVe0 generation card (0x0e6060a1)
[    8.092586] [drm] nouveau 0000:01:00.0: Checking PRAMIN for VBIOS
[    8.092592] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[    8.092592] [drm] nouveau 0000:01:00.0: Checking PROM for VBIOS
[    8.094544] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    8.094549] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.094550] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    8.094552] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    8.094555] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.094558] ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \LED_ 1 (20120320/utaddress-251)
[    8.094560] ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \GPIO 2 (20120320/utaddress-251)
[    8.094562] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.094563] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.111091] parport_pc 00:0a: >reported by Plug and Play ACPI
[    8.111179] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.135143] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x12
[    8.191108] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    8.191110] [drm] nouveau 0000:01:00.0: Using VBIOS from PROM
[    8.191111] [drm] nouveau 0000:01:00.0: BIT BIOS found
[    8.191113] [drm] nouveau 0000:01:00.0: Bios version 80.06.21.00
[    8.191115] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[    8.191277] [drm] nouveau 0000:01:00.0: MXM: no VBIOS data, nothing to do
[    8.191278] [drm] nouveau 0000:01:00.0: DCB version 4.0
[    8.191280] [drm] nouveau 0000:01:00.0: DCB outp 01: 02000f00 00020030
[    8.191281] [drm] nouveau 0000:01:00.0: DCB outp 02: 08011f82 0f420030
[    8.191282] [drm] nouveau 0000:01:00.0: DCB outp 03: 02022f62 0f420010
[    8.191283] [drm] nouveau 0000:01:00.0: DCB conn 00: 00000000
[    8.191284] [drm] nouveau 0000:01:00.0: DCB conn 01: 00002131
[    8.191285] [drm] nouveau 0000:01:00.0: DCB conn 02: 00010263
[    8.191288] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x886B
[    8.194393] ppdev: user-space parallel port driver
[    8.198772] snd_hda_intel 0000:00:1b.0: >irq 45 for MSI/MSI-X
[    8.209924] lp0: using parport0 (interrupt-driven).
[    8.213479] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x12
[    8.214229] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x12
[    8.215009] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x12
[    8.215748] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.218773] rtw driver version=v3.4.4_4749.20121105 
[    8.218775] Build at: Sep 10 2013 22:37:56
[    8.218792] register rtw_netdev_ops to netdev_ops
[    8.218793] CHIP TYPE: RTL8188C_8192C
[    8.218794] 
[    8.218794] usb_endpoint_descriptor(0):
[    8.218795] bLength=7
[    8.218796] bDescriptorType=5
[    8.218797] bEndpointAddress=81
[    8.218797] wMaxPacketSize=200
[    8.218798] bInterval=0
[    8.218799] RT_usb_endpoint_is_bulk_in = 1
[    8.218799] 
[    8.218799] usb_endpoint_descriptor(1):
[    8.218800] bLength=7
[    8.218801] bDescriptorType=5
[    8.218801] bEndpointAddress=2
[    8.218802] wMaxPacketSize=200
[    8.218802] bInterval=0
[    8.218803] RT_usb_endpoint_is_bulk_out = 2
[    8.218803] 
[    8.218803] usb_endpoint_descriptor(2):
[    8.218804] bLength=7
[    8.218805] bDescriptorType=5
[    8.218805] bEndpointAddress=3
[    8.218806] wMaxPacketSize=200
[    8.218807] bInterval=0
[    8.218807] RT_usb_endpoint_is_bulk_out = 3
[    8.218808] 
[    8.218808] usb_endpoint_descriptor(3):
[    8.218808] bLength=7
[    8.218809] bDescriptorType=5
[    8.218810] bEndpointAddress=84
[    8.218810] wMaxPacketSize=40
[    8.218811] bInterval=1
[    8.218811] RT_usb_endpoint_is_int_in = 4, Interval = 1
[    8.218812] nr_endpoint=4, in_num=2, out_num=2
[    8.218812] 
[    8.218813] USB_SPEED_HIGH
[    8.218838] Chip Version ID: VERSION_NORMAL_TSMC_CHIP_88C.
[    8.218840] RF_Type is 3!!
[    8.218952] EEPROM type is E-FUSE
[    8.218953] ====> ReadAdapterInfo8192C
[    8.218992] Boot from EFUSE, Autoload OK !
[    8.220161] kvm: disabled by bios
[    8.221065] [drm] nouveau 0000:01:00.0: 0x8B9E: Init table command not found: 0xA9
[    8.221067] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x904B
[    8.223608] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xAB24
[    8.223609] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xAB25
[    8.223617] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xABA9
[    8.223618] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xAC0E
[    8.226744] [TTM] Zone  kernel: Available graphics memory: 407632 kiB
[    8.226745] [TTM] Zone highmem: Available graphics memory: 4117860 kiB
[    8.226746] [TTM] Initializing pool allocator
[    8.226749] [TTM] Initializing DMA pool allocator
[    8.226754] [drm] nouveau 0000:01:00.0: Detected 1024MiB VRAM (GDDR5)
[    8.228572] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[    8.250719] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    8.250783] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    8.250852] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    8.250949] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    8.250996] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    8.252817] [drm] nouveau 0000:01:00.0: PGRAPH: unsupported chipset, please report!
[    8.253009] [drm] nouveau 0000:01:00.0: unknown connector type 63
[    8.253237] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.253238] [drm] No driver support for vblank timestamp query.
[    8.253302] [drm] nouveau 0000:01:00.0: voltage table 0x50 unknown
[    8.267828] EEPROMVID = 0x0bda
[    8.267829] EEPROMPID = 0x8176
[    8.267829] EEPROMCustomerID : 0x00
[    8.267830] EEPROMSubCustomerID: 0x00
[    8.267830] RT_CustomerID: 0x00
[    8.267832] _ReadMACAddress MAC Address from EFUSE = 64:70:02:28:e9:38
[    8.267833] EEPROMRegulatory = 0x0
[    8.267833] _ReadBoardType(0)
[    8.267834] BT Coexistance = disable
[    8.267835] RT_ChannelPlan: 0x02
[    8.267836] _ReadPSSetting...bHWPwrPindetect(0)-bHWPowerdown(0) ,bSupportRemoteWakeup(0)
[    8.267837] ### PS params=>  power_mgnt(1),usbss_enable(0) ###
[    8.267837] ### AntDivCfg(0)
[    8.267838] readAdapterInfo_8192CU(): REPLACEMENT = 1
[    8.267839] <==== ReadAdapterInfo8192C in 48 ms
[    8.267904] rtw_macaddr_cfg MAC Address  = 64:70:02:28:e9:38
[    8.267905] MAC Address from pnetdev->dev_addr= 64:70:02:28:e9:38
[    8.268013] bDriverStopped:1, bSurpriseRemoved:0, bup:0, hw_init_completed:0
[    8.268030] usbcore: registered new interface driver rtl8192cu
[    8.324688] kvm: disabled by bios
[    8.428752] kvm: disabled by bios
[    8.541850] kvm: disabled by bios
[    8.568951] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
[    8.568953] [drm] nouveau 0000:01:00.0: 0: core 162MHz shader 324MHz memory 648MHz voltage 100mV
[    8.568954] [drm] nouveau 0000:01:00.0: 1: core 405MHz shader 810MHz memory 1080MHz voltage 80mV
[    8.568956] [drm] nouveau 0000:01:00.0: 3: core 1350MHz shader 2700MHz memory 1080MHz voltage 40mV
[    8.568957] [drm] nouveau 0000:01:00.0: c:
[    8.641279] [drm] nouveau 0000:01:00.0: allocated 1920x1080 fb: 0x2e0000, bo ebdb9000
[    8.641367] fbcon: nouveaufb (fb0) is primary device
[    8.641446] Console: switching to colour frame buffer device 240x67
[    8.641486] fb0: nouveaufb frame buffer device
[    8.641487] drm: registered panic notifier
[    8.641490] [drm] Initialized nouveau 1.0.0 20120316 for 0000:01:00.0 on minor 0
[    8.641548] hda_intel: Disabling MSI
[    8.641555] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[    9.053218] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.127867] init: failsafe main process (799) killed by TERM signal
[    9.171737] Bluetooth: Core ver 2.16
[    9.171750] NET: Registered protocol family 31
[    9.171751] Bluetooth: HCI device and connection manager initialized
[    9.171901] Bluetooth: HCI socket layer initialized
[    9.171902] Bluetooth: L2CAP socket layer initialized
[    9.171905] Bluetooth: SCO socket layer initialized
[    9.173028] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.173030] Bluetooth: BNEP filters: protocol multicast
[    9.178474] Bluetooth: RFCOMM TTY layer initialized
[    9.178477] Bluetooth: RFCOMM socket layer initialized
[    9.178478] Bluetooth: RFCOMM ver 1.11
[    9.188370] type=1400 audit(1378850084.934:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=888 comm="apparmor_parser"
[    9.188379] type=1400 audit(1378850084.934:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=886 comm="apparmor_parser"
[    9.188386] type=1400 audit(1378850084.934:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=887 comm="apparmor_parser"
[    9.188394] type=1400 audit(1378850084.934:5): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=889 comm="apparmor_parser"
[    9.188595] type=1400 audit(1378850084.934:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=888 comm="apparmor_parser"
[    9.188601] type=1400 audit(1378850084.934:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=886 comm="apparmor_parser"
[    9.188609] type=1400 audit(1378850084.934:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=887 comm="apparmor_parser"
[    9.188669] type=1400 audit(1378850084.934:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=889 comm="apparmor_parser"
[    9.188822] type=1400 audit(1378850084.934:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=889 comm="apparmor_parser"
[    9.190641] type=1400 audit(1378850084.934:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=894 comm="apparmor_parser"
[    9.239533] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[    9.239649] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[    9.239762] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    9.239902] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    9.265857] bDriverStopped=1
[    9.266139] +871x_drv - drv_open, bup=0
[    9.268326]  ===> FirmwareDownload91C() fw:Rtl819XFwImageArray_TSMC
[    9.268330] FirmwareDownload92C accquire FW from embedded image
[    9.268332] fw_ver=v80, fw_subver=0, sig=0x88c0
[    9.312849] fw download ok!
[    9.312852] Set RF Chip ID to RF_6052 and RF type to 1T1R.
[    9.592843] IQK:Start!!!
[    9.596958] Path A IQK Success!!
[    9.600039] Path A IQK Success!!
[    9.601514] IQK: final_candidate is 0
[    9.601516] IQK: RegE94=101 RegE9C=10 RegEA4=fe RegEAC=3fe RegEB4=0 RegEBC=0 RegEC4=0 RegECC=0
[    9.601516]  Path A IQ Calibration Success !
[    9.707590] pdmpriv->TxPowerTrackControl = 1
[    9.709143] MAC Address from REG_MACID = 64:70:02:28:e9:38
[    9.709144] rtl8192cu_hal_init in 444ms
[    9.709145] MAC Address = 64:70:02:28:e9:38
[    9.711071] -871x_drv - drv_open, bup=1
[    9.711157] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.711318] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.711330] set_mode = IW_MODE_INFRA
[    9.807093] r8169 0000:03:00.0: >eth0: link down
[    9.807198] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.807413] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.815294] [rtw_wx_set_pmkid] IW_PMKSA_FLUSH!
[    9.815299] set_mode = IW_MODE_INFRA
[    9.815335] =>rtw_wx_set_essid
[    9.815336] ssid=g\xffffffc6isQ\xffffffffJ\xffffffec)\xffffffcd\xffffffba\xffffffba\xffffffab\xfffffff2\xfffffffb\xffffffe3F|\xffffffc2T\xfffffff8\x1b\xffffffe8\xffffffe7\xffffff8dvZ.c3\xffffff9f\xffffffc9\xffffff9a\xffffff9a l\xffffffcd\xfffffff6, len=32
[    9.815337] Set SSID under fw_state=0x00000008
[    9.815338] <=rtw_wx_set_essid, ret -1
[    9.822161] [rtw_wx_set_pmkid] IW_PMKSA_FLUSH!
[   11.128929] survey done event(1)
[   11.141404] IW_SCAN_THIS_ESSID, ssid=PlusnetWireless882FD0, len=21
[   12.441848] survey done event(5)
[   12.442071] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM
[   12.442074] set_mode = IW_MODE_INFRA
[   12.442079] 
[   12.442079]  wpa_ie(length:22):
[   12.442081] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x02 
[   12.442082] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00 
[   12.442083] 0x00 0x0f 0xac 0x02 0x00 0x00 0x00 0x00 
[   12.442088] =>rtw_wx_set_essid
[   12.442089] ssid=PlusnetWireless882FD0, len=21
[   12.442091] Set SSID under fw_state=0x00000008
[   12.442093] [by_bssid:0][assoc_ssid:PlusnetWireless882FD0][to_roaming:0] new candidate: PlusnetWireless882FD0(00:26:44:88:2f:d0) rssi:-75
[   12.442095] rtw_select_and_join_from_scanned_queue: candidate: PlusnetWireless882FD0(00:26:44:88:2f:d0)
[   12.442097] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set
[   12.442098] link to Ralink AP
[   12.442099] <=rtw_wx_set_essid, ret 0
[   12.442102] Set BSSID under fw_state=0x00000088
[   12.567303] link to Ralink AP
[   12.567309] issue_deauth to 00:26:44:88:2f:d0
[   12.571607] OnAuthClient
[   12.571615] network.SupportedRates[0]=82
[   12.571617] network.SupportedRates[1]=84
[   12.571618] network.SupportedRates[2]=8B
[   12.571620] network.SupportedRates[3]=96
[   12.571621] network.SupportedRates[4]=12
[   12.571623] network.SupportedRates[5]=24
[   12.571624] network.SupportedRates[6]=48
[   12.571625] network.SupportedRates[7]=6C
[   12.571627] network.SupportedRates[8]=0C
[   12.571628] network.SupportedRates[9]=18
[   12.571630] network.SupportedRates[10]=30
[   12.571631] network.SupportedRates[11]=60
[   12.571633] bssrate_len = 12
[   12.582293] OnAssocRsp
[   12.582300] report_join_res(3)
[   12.582302] rtw_joinbss_update_network
[   12.582305] +rtw_update_ht_cap()
[   12.582310] rtw_joinbss_update_stainfo
[   12.582405] HW_VAR_BASIC_RATE: BrateCfg(0x15d)
[   12.582463] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   12.582741] WMM(0): 0, a42b
[   12.582788] WMM(1): 0, a44f
[   12.582824] WMM(2): 0, 5e4322
[   12.582881] WMM(3): 0, 2f3222
[   12.582884] HTOnAssocRsp
[   12.584633] update raid entry, mask=0xfffff, arg=0x80
[   12.585109] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[   12.585388] SetFwRsvdPagePkt
[   12.585395] Set RSVD page location to Fw.
[   12.585747] =>mlmeext_joinbss_event_callback
[   12.596644] OnAction_back
[   12.596648] OnAction_back, action=0
[   12.596650] issue_action_BA, category=3, action=1, status=0
[   12.609563] 
[   12.609563]  ~~~~stastakey:unicastkey
[   12.609597] 
[   12.609597]  ~~~~stastakey:groupkey
[   12.609599] ==> rtw_set_key algorithm(2),keyid(1),key_mask(2)
[   12.727639] OnAction_back
[   12.727644] OnAction_back, action=0
[   12.727647] issue_action_BA, category=3, action=1, status=0
[   13.710730] rtl8192c_dm_RF_Saving(): RF_Normal
[   15.311519] survey done event(2)
[   15.514131] OnAction_back
[   15.514135] OnAction_back, action=2
[   15.514137] OnAction_back(): DELBA: 0(0)
[   15.514140] OnAction_back
[   15.514141] OnAction_back, action=2
[   15.514143] OnAction_back(): DELBA: 0(0)
[   25.706079] rtw_set_ps_mode(): Enter 802.11 power save mode...
[   25.706085] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[   27.705518] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[   27.705557] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[   29.705228] rtw_set_ps_mode(): Enter 802.11 power save mode...
[   29.705234] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[   56.995155] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[   56.995205] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[   58.348305] survey done event(2)
[   59.712097] rtw_set_ps_mode(): Enter 802.11 power save mode...
[   59.712102] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[   77.887912] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[   77.887956] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[   81.717166] rtw_set_ps_mode(): Enter 802.11 power save mode...
[   81.717171] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  119.878436] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  119.878465] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  121.232985] survey done event(3)
[  121.726293] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  121.726297] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  123.726810] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  123.726845] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  125.727241] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  125.727246] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  142.349789] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  142.349828] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  143.731366] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  143.731372] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  163.735952] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  163.736003] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  167.736867] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  167.736873] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  202.733017] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  202.733058] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  204.086295] survey done event(2)
[  205.745569] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  205.745574] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  305.551861] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  305.551902] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  306.904257] survey done event(3)
[  307.768935] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  307.768940] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  354.725293] 
[  354.725293]  ~~~~stastakey:groupkey
[  354.725299] ==> rtw_set_key algorithm(2),keyid(1),key_mask(2)
[  354.725838] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  354.725877] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  355.779933] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  355.779939] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  425.339366] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  425.339429] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  426.692247] survey done event(4)
[  427.796423] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  427.796429] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  432.072686] rx bc/mc packets, to perform sw rtw_tkip_decrypt
[  434.824364] 
[  434.824364]  ~~~~stastakey:groupkey
[  434.824369] ==> rtw_set_key algorithm(2),keyid(1),key_mask(2)
[  434.824989] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  434.825028] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  437.798715] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  437.798722] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  505.326420] rx bc/mc packets, to perform sw rtw_tkip_decrypt
[  545.126874] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  545.126939] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  546.480167] survey done event(3)
[  547.823905] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  547.823910] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  563.044239] 
[  563.044239]  ~~~~stastakey:groupkey
[  563.044245] ==> rtw_set_key algorithm(2),keyid(2),key_mask(6)
[  563.044827] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  563.044867] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  565.828015] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  565.828020] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  595.964791] usb 3-2: >new high-speed USB device number 3 using xhci_hcd
[  595.985694] usb 3-2: >New USB device found, idVendor=0951, idProduct=1689
[  595.985699] usb 3-2: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  595.985702] usb 3-2: >Product: DataTraveler SE9
[  595.985704] usb 3-2: >Manufacturer: Kingston
[  595.985707] usb 3-2: >SerialNumber: 00241D8CE3F7BC5189310365
[  595.986007] usb 3-2: >ep 0x81 - rounding interval to 32768 microframes, ep desc says 0 microframes
[  595.986012] usb 3-2: >ep 0x2 - rounding interval to 32768 microframes, ep desc says 0 microframes
[  596.029991] usbcore: registered new interface driver uas
[  596.031508] Initializing USB Mass Storage driver...
[  596.031668] scsi6 : usb-storage 3-2:1.0
[  596.031747] usbcore: registered new interface driver usb-storage
[  596.031748] USB Mass Storage support registered.
[  597.106869] scsi 6:0:0:0: >Direct-Access     Kingston DataTraveler SE9 PMAP PQ: 0 ANSI: 4
[  597.108198] sd 6:0:0:0: >Attached scsi generic sg2 type 0
[  598.219502] sd 6:0:0:0: >[sdb] 15458304 512-byte logical blocks: (7.91 GB/7.37 GiB)
[  598.219768] sd 6:0:0:0: >[sdb] Write Protect is off
[  598.219773] sd 6:0:0:0: >[sdb] Mode Sense: 23 00 00 00
[  598.220001] sd 6:0:0:0: >[sdb] No Caching mode page present
[  598.220006] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
[  598.222013] sd 6:0:0:0: >[sdb] No Caching mode page present
[  598.222018] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
[  598.267233]  sdb: sdb1
[  598.268881] sd 6:0:0:0: >[sdb] No Caching mode page present
[  598.268885] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
[  598.268888] sd 6:0:0:0: >[sdb] Attached SCSI removable disk
[  615.558653] OnAction_back
[  615.558658] OnAction_back, action=0
[  615.558661] issue_action_BA, category=3, action=1, status=0
[  615.827655] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  615.827710] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  619.826618] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  619.826624] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  664.878867] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  664.878917] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  665.815535] rtl8192c_dm_RF_Saving(): RF_Save
[  666.231075] survey done event(0)
[  667.813793] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  667.814392] rtl8192c_dm_RF_Saving(): RF_Normal
[  667.814397] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  784.607257] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  784.607322] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  785.782996] rtl8192c_dm_RF_Saving(): RF_Save
[  785.959100] survey done event(1)
[  787.781068] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  787.781548] rtl8192c_dm_RF_Saving(): RF_Normal
[  787.781553] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  890.361798] OnAction_back
[  890.361803] OnAction_back, action=2
[  890.361805] OnAction_back(): DELBA: 0(0)
[  891.740049] OnAction_back
[  891.740051] OnAction_back, action=0
[  891.740053] issue_action_BA, category=3, action=1, status=0
[  891.752865] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  891.752902] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  891.759416] rtw_issue_addbareq_cmd, p=0
[  891.759450] issue_action_BA, category=3, action=0, status=0
[  891.759452] BA_starting_seqctrl = 330 for TID=0
[  891.795974] OnAction_back
[  891.795977] OnAction_back, action=1
[  891.795978] agg_enable for TID=0
[  895.753317] rtl8192c_dm_RF_Saving(): RF_Save
[  897.751347] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  897.751823] rtl8192c_dm_RF_Saving(): RF_Normal
[  897.751828] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  904.335751] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  904.335809] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  905.687523] survey done event(4)
[  905.749057] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  905.749065] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  953.322922] 
[  953.322922]  ~~~~stastakey:groupkey
[  953.322929] ==> rtw_set_key algorithm(2),keyid(2),key_mask(6)
[  953.323518] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[  953.323556] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  953.737659] rtl8192c_dm_RF_Saving(): RF_Save
[  955.697206] OnAction_back
[  955.697211] OnAction_back, action=0
[  955.697214] issue_action_BA, category=3, action=1, status=0
[  958.474453] OnDeAuth Reason code(3)
[  958.474458] OnDeAuth, STA:00:26:44:88:2f:d0
[  958.474460] receive_disconnect
[  958.474462] report_del_sta_event: delete STA
[  958.474469] OnAction_back
[  958.476528] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  959.735601] rtl8192c_dm_RF_Saving(): RF_Normal
[  959.875796] survey done event(3)
[  959.876145] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM
[  959.876150] set_mode = IW_MODE_INFRA
[  959.876161] 
[  959.876161]  wpa_ie(length:22):
[  959.876165] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x02 
[  959.876167] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00 
[  959.876169] 0x00 0x0f 0xac 0x02 0x00 0x00 0x00 0x00 
[  959.876180] =>rtw_wx_set_essid
[  959.876182] ssid=PlusnetWireless882FD0, len=21
[  959.876195] Set SSID under fw_state=0x00000008
[  959.876199] [by_bssid:0][assoc_ssid:PlusnetWireless882FD0][to_roaming:0] new candidate: PlusnetWireless882FD0(00:26:44:88:2f:d0) rssi:-75
[  959.876202] rtw_select_and_join_from_scanned_queue: candidate: PlusnetWireless882FD0(00:26:44:88:2f:d0)
[  959.876207] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set
[  959.876209] link to Ralink AP
[  959.876212] <=rtw_wx_set_essid, ret 0
[  959.876216] Set BSSID under fw_state=0x00000088
[  959.963546] link to Ralink AP
[  959.963551] issue_deauth to 00:26:44:88:2f:d0
[  959.967976] OnAuthClient
[  959.967984] network.SupportedRates[0]=82
[  959.967986] network.SupportedRates[1]=84
[  959.967987] network.SupportedRates[2]=8B
[  959.967989] network.SupportedRates[3]=96
[  959.967990] network.SupportedRates[4]=12
[  959.967991] network.SupportedRates[5]=24
[  959.967993] network.SupportedRates[6]=48
[  959.967994] network.SupportedRates[7]=6C
[  959.967995] network.SupportedRates[8]=0C
[  959.967997] network.SupportedRates[9]=18
[  959.967998] network.SupportedRates[10]=30
[  959.968000] network.SupportedRates[11]=60
[  959.968002] bssrate_len = 12
[  959.976926] OnAssocRsp
[  959.976932] report_join_res(3)
[  959.976934] rtw_joinbss_update_network
[  959.976937] +rtw_update_ht_cap()
[  959.976941] rtw_joinbss_update_stainfo
[  959.976986] HW_VAR_BASIC_RATE: BrateCfg(0x15d)
[  959.977267] WMM(0): 0, a42b
[  959.977306] WMM(1): 0, a44f
[  959.977345] WMM(2): 0, 5e4322
[  959.977384] WMM(3): 0, 2f3222
[  959.977386] HTOnAssocRsp
[  959.979127] update raid entry, mask=0xfffff, arg=0x80
[  959.979603] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  959.979882] SetFwRsvdPagePkt
[  959.979888] Set RSVD page location to Fw.
[  959.980241] =>mlmeext_joinbss_event_callback
[  959.990274] OnAction_back
[  959.990278] OnAction_back, action=0
[  959.990280] issue_action_BA, category=3, action=1, status=0
[  960.004909] 
[  960.004909]  ~~~~stastakey:unicastkey
[  960.004986] 
[  960.004986]  ~~~~stastakey:groupkey
[  960.004997] ==> rtw_set_key algorithm(2),keyid(2),key_mask(4)
[  961.054302] OnAction_back
[  961.054308] OnAction_back, action=0
[  961.054311] issue_action_BA, category=3, action=1, status=0
[  961.735539] rtl8192c_dm_RF_Saving(): RF_Save
[  965.327291] OnAction_back
[  965.327297] OnAction_back, action=2
[  965.327299] OnAction_back(): DELBA: 0(0)
[  965.327302] OnAction_back
[  965.327304] OnAction_back, action=2
[  965.327305] OnAction_back(): DELBA: 0(0)
[  965.734223] rtl8192c_dm_RF_Saving(): RF_Normal
[  971.731187] rtw_set_ps_mode(): Enter 802.11 power save mode...
[  971.731193] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1024.063560] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[ 1024.063662] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1025.415036] survey done event(4)
[ 1025.716575] rtw_set_ps_mode(): Enter 802.11 power save mode...
[ 1025.716583] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1029.715485] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[ 1029.715549] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1031.716489] rtl8192c_dm_RF_Saving(): RF_Save
[ 1033.714393] rtw_set_ps_mode(): Enter 802.11 power save mode...
[ 1033.714868] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1033.714873] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1034.545804] 
[ 1034.545804]  ~~~~stastakey:groupkey
[ 1034.545809] ==> rtw_set_key algorithm(2),keyid(2),key_mask(4)
[ 1034.546433] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[ 1034.546483] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1035.713869] rtw_set_ps_mode(): Enter 802.11 power save mode...
[ 1035.713875] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1047.710603] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[ 1047.710667] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1049.710050] rtw_set_ps_mode(): Enter 802.11 power save mode...
[ 1049.710056] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1109.693757] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[ 1109.693789] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1110.688595] OnAction_back
[ 1110.688599] OnAction_back, action=0
[ 1110.688601] issue_action_BA, category=3, action=1, status=0
[ 1111.694819] rtl8192c_dm_RF_Saving(): RF_Save
[ 1111.695888] rtw_issue_addbareq_cmd, p=0
[ 1111.695927] issue_action_BA, category=3, action=0, status=0
[ 1111.695932] BA_starting_seqctrl = 235 for TID=0
[ 1111.703363] OnAction_back
[ 1111.703366] OnAction_back, action=1
[ 1111.703367] agg_enable for TID=0
[ 1112.197122] rx bc/mc packets, to perform sw rtw_tkip_decrypt
[ 1115.692128] rtw_set_ps_mode(): Enter 802.11 power save mode...
[ 1115.692519] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1115.692520] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2

```

```

sudo lshw -C network

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 90:2b:34:9f:59:02
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@3:1
       logical name: wlan0
       serial: 64:70:02:28:e9:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu ip=192.168.1.66 multicast=yes wireless=IEEE 802.11bgn


```

```

iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:88:2F:D0
                    ESSID:"PlusnetWireless882FD0"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:on
                    Bit Rates:65 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=96/100  Signal level=-65 dBm  


```

```

lsb_release and uname

Description:    Ubuntu 12.10
3.5.0-17-generic i686


```

Thanks for reading.

---

### Post by chili555 on 2013-09-11
There is a lot of activity with power management going on here!> [ 1034.546433] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[ 1034.546483] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1035.713869] rtw_set_ps_mode(): Enter 802.11 power save mode...
[ 1035.713875] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1047.710603] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[ 1047.710667] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1049.710050] rtw_set_ps_mode(): Enter 802.11 power save mode...
[ 1049.710056] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1109.693757] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
[ 1109.693789] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0 Let's disable it and see if things improve:```
sudo -i
echo "options 8192cu rtw_power_mgnt=0 rtw_enusbss=0" > /etc/modprobe.d/8192cu.conf
modprobe -r 8192u
modprobe 8192u
exit
```Any improvement?

---

### Post by john97 on 2013-09-11
Thanks. Done.
There may be a slight improvement with that. I can now connect to services (for the most part) but my connection rate drops to zero every few seconds and sometimes just remains flat.

Any other options?

---

### Post by chili555 on 2013-09-12
In order to know or at least guess what to adjust, we need to see what's going on as it's misbehaving. When it does so, please run:```
dmesg | tail -n50 > j97.txt
```Find the file j97.txt in your user directory and post it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by john97 on 2013-09-12
Thanks.

This is the output when experiencing dropouts.

[http://paste.ubuntu.com/6099382/](http://paste.ubuntu.com/6099382/)

---

### Post by chili555 on 2013-09-13
I suggest you try the backported driver from kernel version 3.11. First, remove the blacklist for rtl8192cu. Second, uninstall 8192cu:```
cd Desktop/RTL8188C_8192C_8192D_USB [COLOR="#FF0000"]<---or wherever you compiled the driver[/COLOR]
sudo make uninstall
```Then, I suggest you download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:```
cd Desktop/backports-3.11-rc3-1/
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8192cu
```Now your wireless should be working properly.

You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile:

```
cd Desktop/backports-3.11-rc3-1/
make clean
make defconfig-rtlwifi
make
sudo make install
sudo modprobe -r rtl8192cu && sudo modprobe rtl8192cu
```

---

### Post by john97 on 2013-09-13
Thanks Chili, but runnning:

```
cd apps/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/
sudo make uninstall
```

Returns the error:

```
make: *** No rule to make target `uninstall'. Stop.
```

What's happening here?

---

### Post by chili555 on 2013-09-13
> cd apps/[COLOR="#FF0000"]RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/[/COLOR]Is that the directory where you ran the install; make and sudo make install, originally? I don't know for sure, it's not my system. You want to be in the same directory as the Makefile.

---

### Post by john97 on 2013-09-14
> **chili555 said:**
> Is that the directory where you ran the install; make and sudo make install, originally? I don't know for sure, it's not my system. You want to be in the same directory as the Makefile.

That is the directory I ran the install script. However I ran no make commands and there is no Makefile in that directory.

Inside: '/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/'
there is a locked directory named '[COLOR=#ff0000]rtl[/COLOR]8188C_8192C_[COLOR=#ff0000]usb[/COLOR]_linux_v3.4.4_4749.20121105/' and a tarball of the same name.
I can see that the tarball does contain a Makefile.

Have I done something stupid or maybe missed an important step?

I took the same steps as can be seen on the first post here [http://ubuntuforums.org/showthread.php?t=2092934](http://ubuntuforums.org/showthread.php?t=2092934) but also used chmod 755 and added 8192cu to /modules.

Any clearer what the problem is?

---

### Post by varunendra on 2013-09-14
> **john97 said:**
> Inside: '/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/'
there is a locked directory named '[COLOR=#ff0000]rtl[/COLOR]8188C_8192C_[COLOR=#ff0000]usb[/COLOR]_linux_v3.4.4_4749.20121105/' and a tarball of the same name.
I can see that the tarball does contain a Makefile.

Have I done something stupid or maybe missed an important step?
No, nothing stupid. That package is designed that way. The desired Makefile is within that directory you see in the "driver" folder. (if not, delete the folder, right-click the .tar.bz > "Extract here")

You'd have to cd to that directory within the 'driver' folder, and run "make uninstall" from there. It should get the job done (from within '/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/') -
```
cd rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
sudo make uninstall
```
Closely watch the output and report back if any errors occur.

> I took the same steps as can be seen on the first post here [http://ubuntuforums.org/showthread.php?t=2092934](http://ubuntuforums.org/showthread.php?t=2092934) but also used chmod 755 and added 8192cu to /modules.
/modules or /etc/modules file? Whatever it is, you'll have to undo that as well. After cleaning everything up, proceed with the installation of the backported driver.

---

### Post by john97 on 2013-09-14
Thanks.

I extracted the tar, ran sudo make uninstall inside the new directory and received no errors.

I then removed the line 8192cu in /etc/modules

I downloaded the backportd driver, extracted to Desktop and ran:

```
cd Desktop/backports-3.11-rc3-1/
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8192cu
```

Again no errors.

Still no success though. The device no longer detects any wireless networks.

"lsusb" shows the device as normal
"lsmod" shows rtl8192cu is loaded
"modprobe 8192" shows 8192 does not exist.

:confused:

---

### Post by varunendra on 2013-09-14
Please follow the "Wireless Script" link in my signature and download the 'alternative' script from the link at the bottom of the linked post. Follow the "No Internet" method to run the script, and post back the result.

Let's hope we can find some useful clue in it.

---

### Post by john97 on 2013-09-15
> **varunendra said:**
> Please follow the "Wireless Script" link in my signature and download the 'alternative' script from the link at the bottom of the linked post. Follow the "No Internet" method to run the script, and post back the result.

Let's hope we can find some useful clue in it.

Thanks. Done.

[http://paste.ubuntu.com/6111239/](http://paste.ubuntu.com/6111239/)

---

### Post by varunendra on 2013-09-16
Which country you are in?

From your dmesg part -
```
[  509.521022] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[  509.521024] cfg80211: Disabling freq **[COLOR="#FF0000"]2472 MHz[/COLOR]** as** custom regd **has no rule that fits a **20 MHz** wide channel
[  509.521026] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
```
Note that 2.472 GHz is the frequency that you are using as per iwconfig output in your first post.

It seems the cfg80211 driver (or its subsystem) is unable to automatically get your country code and thus has to use a default setting that does not match your router's frequency range. I think we can tell it to use a desired country's regdomain settings using a parameter "ieee80211_regdom".

For example, if you are in Japan *(country code "JP" seems to be one of the very few who support that frequency on a 20MHz channel)*, then do -
```
sudo modprobe -rv rtl8192cu rtlwifi mac80211 cfg80211
sudo modprobe -v cfg80211 ieee80211_regdom=JP
sudo modprobe -v rtl8192cu
sudo iwlist scan
```
Can you scan now? The above parameter "JP" is temporary and will be reset at next boot. Tell us your country code (or name) and we may try that one. For a test, you may try JP.

If it doesn't help, please post the output of -
```
dmesg | egrep 'rtl8192|wlan|80211'
```

---

### Post by john97 on 2013-09-16
Thanks.
I am in the UK so tried ...regdom=UK

```
sudo iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:88:2F:D0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"PlusnetWireless882FD0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000228bc150
                    Extra: Last beacon: 7552ms ago
                    IE: Unknown: 0015506C75736E6574576972656C657373383832464430
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C330C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000400000000000000000000000000000000000000

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```


I am still unable to connect to the network. Here is the dmesg output:
[http://paste.ubuntu.com/6116248/](http://paste.ubuntu.com/6116248/)

---

### Post by praseodym on 2013-09-16
Change the encryption mode to WPA2-AES only, if possible. 

Alternatively, try the patched driver from 13.04 instead. Uninstall the other one and install it according to this:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

---

### Post by frederic-pege on 2013-10-27
> [COLOR=#000000]Alternatively, try the patched driver from 13.04 instead. Uninstall the other one and install it according to this:[/COLOR]

[http://forum.ubuntuusers.de/topic/wl.../#post-5638107]("http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107")

Worked like a charm for me !!
thanks guys !

---

