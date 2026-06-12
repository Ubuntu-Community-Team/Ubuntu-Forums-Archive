---
title: "Wifi driver for DELL LATITUDE D520 / Intel PRO Wireless 3945ABG"
date: 2014-02-17
forum: Networking &amp; Wireless
---

### Post by Nayab Basha Sayed on 2014-02-17
I am using dell latitude d520 laptop installed withe lubuntu 13.10. I tried preferences --> Software & Updates --> Additional Drivers. Couldn't find it. Need help.

---

### Post by mörgæs on 2014-02-17
Please post the output from the commands listed here:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Nayab Basha Sayed on 2014-02-18
```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

```
lsusb
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
lspci -nn | grep 'Wireless Brand'

found nothing

```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:b5:9f:eb  
          inet addr:172.16.86.41  Bcast:172.16.86.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feb5:9feb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45853 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41148302 (41.1 MB)  TX bytes:2269978 (2.2 MB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53515 (53.5 KB)  TX bytes:53515 (53.5 KB)


wlan0     Link encap:Ethernet  HWaddr 00:18:de:94:75:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


```
basha@basha260:~$ lspci -nn | grep 'Wireless Brand'clear
basha@basha260:~$ clear


basha@basha260:~$ ifcofig
No command 'ifcofig' found, did you mean:
 Command 'ifconfig' from package 'net-tools' (main)
ifcofig: command not found
basha@basha260:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:b5:9f:eb  
          inet addr:172.16.86.41  Bcast:172.16.86.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feb5:9feb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41278600 (41.2 MB)  TX bytes:2289476 (2.2 MB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53779 (53.7 KB)  TX bytes:53779 (53.7 KB)


wlan0     Link encap:Ethernet  HWaddr 00:18:de:94:75:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=12 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


eth0      no wireless extensions.

iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=12 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
lsmod
Module                  Size  Used by
zram                   18070  2 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
bluetooth             323656  10 bnep,rfcomm
coretemp               13195  0 
joydev                 17097  0 
gpio_ich               13229  0 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
dell_laptop            17161  0 
dcdbas                 14383  1 dell_laptop
snd_hda_codec_idt      44605  1 
snd_hda_intel          42658  1 
snd_hda_codec         164003  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
arc4                   12536  2 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
microcode              18830  0 
mac80211              517444  2 iwl3945,iwlegacy
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                16864  0 
psmouse                90642  0 
serio_raw              13189  0 
cfg80211              401762  3 iwl3945,iwlegacy,mac80211
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  12 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
mac_hid                13037  0 
i915                  594380  2 
drm_kms_helper         46867  1 i915
wmi                    18590  1 dell_wmi
drm                   242400  3 i915,drm_kms_helper
video                  18777  1 i915
i2c_algo_bit           13197  1 i915
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
b44                    31234  0 
ssb                    51596  1 b44
mii                    13654  1 b44

lsmod | grep "wlan_module_name"
found nothing

```



```
dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-15-generic (buildd@komainu) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #25-Ubuntu SMP Thu Jan 30 17:25:07 UTC 2014 (Ubuntu 3.11.0-15.25-generic 3.11.10)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000009f6d33ff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f6d3400-0x000000009fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f4006fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f4008000-0x00000000f400bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed9ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Dell Inc. Latitude D520                   /0NF743, BIOS A07 08/06/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x9f6d3 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09F800000 mask FFF800000 uncachable
[    0.000000]   3 base 09F700000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2552MB, range: 8MB, type UC
[    0.000000] reg 3, base: 2551MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2551M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2551MB, range: 1MB, type UC
[    0.000000] reg 3, base: 2552MB, range: 8MB, type UC
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b49000, 0x01b49fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35f6c000-0x36fadfff]
[    0.000000] ACPI: RSDP 000fc1f0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 9f6d3a0f 0003C (v01 DELL    M07     27D80806 ASL  00000061)
[    0.000000] ACPI: FACP 9f6d4800 00074 (v01 DELL    M07     27D80806 ASL  00000061)
[    0.000000] ACPI: DSDT 9f6d5400 049A3 (v01 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 9f6e3c00 00040
[    0.000000] ACPI: HPET 9f6d4f00 00038 (v01 DELL    M07     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 9f6d5000 00068 (v01 DELL    M07     27D80806 ASL  00000047)
[    0.000000] ACPI: MCFG 9f6d4fc0 0003E (v16 DELL    M07     27D80806 ASL  00000061)
[    0.000000] ACPI: SLIC 9f6d509c 00176 (v01 DELL    M07     27D80806 ASL  00000061)
[    0.000000] ACPI: SSDT 9f6d3a4b 004DC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1658MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b4a000, 0x01b4afff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x9f6d2fff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x9f6d2fff]
[    0.000000] On node 0 totalpages: 652913
[    0.000000] free_area_init_node: node 0, pgdat c1958bc0, node_mem_map f4b7c020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3318 pages used for memmap
[    0.000000]   HighMem zone: 424661 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] e820: [mem 0xa0000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bd6000 s36288 r0 d21056 u57344
[    0.000000] pcpu-alloc: s36288 r0 d21056 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 651129
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=eba77145-5012-426a-b264-eda6fc496ab5 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5224080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0009f6d3)
[    0.000000] Memory: 2556888K/2611652K available (6358K kernel code, 611K rwdata, 2692K rodata, 880K init, 908K bss, 54764K reserved, 1698644K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1972000 - 0xc1a4e000   ( 880 kB)
[    0.000000]       .data : 0xc1635ee4 - 0xc1971f80   (3312 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1635ee4   (6359 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7008000 soft=f700a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1662.435 MHz processor
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.87 BogoMIPS (lpj=6649740)
[    0.004023] pid_max: default: 32768 minimum: 301
[    0.004125] Security Framework initialized
[    0.004181] AppArmor: AppArmor initialized
[    0.004186] Yama: becoming mindful.
[    0.004427] Mount-cache hash table entries: 512
[    0.005290] Initializing cgroup subsys memory
[    0.005324] Initializing cgroup subsys devices
[    0.005330] Initializing cgroup subsys freezer
[    0.005336] Initializing cgroup subsys blkio
[    0.005352] Initializing cgroup subsys perf_event
[    0.005361] Initializing cgroup subsys hugetlb
[    0.005434] Disabled fast string operations
[    0.005455] CPU: Physical Processor ID: 0
[    0.005459] CPU: Processor Core ID: 0
[    0.005466] mce: CPU supports 6 MCE banks
[    0.005495] CPU0: Thermal monitoring enabled (TM2)
[    0.005526] Last level iTLB entries: 4KB 128, 2MB 0, 4MB 2
[    0.005526] Last level dTLB entries: 4KB 128, 2MB 0, 4MB 8
[    0.005526] tlb_flushall_shift: 6
[    0.008144] Freeing SMP alternatives memory: 28K (c1a4e000 - c1a55000)
[    0.017310] ACPI: Core revision 20130517
[    0.028641] ACPI: All ACPI Tables successfully acquired
[    0.032027] ftrace: allocating 27182 entries in 54 pages
[    0.056247] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056958] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.097950] smpboot: CPU0: Genuine Intel(R) CPU           T2300  @ 1.66GHz (fam: 06, model: 0e, stepping: 08)
[    0.100000] Performance Events: Core events, core PMU driver.
[    0.100000] ... version:                1
[    0.100000] ... bit width:              40
[    0.100000] ... generic registers:      2
[    0.100000] ... value mask:             000000ffffffffff
[    0.100000] ... max period:             000000007fffffff
[    0.100000] ... fixed-purpose events:   0
[    0.100000] ... event mask:             0000000000000003
[    0.100103] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.100319] CPU 1 irqstacks, hard=f70f0000 soft=f70f2000
[    0.100325] smpboot: Booting Node   0, Processors  #1 OK
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.112000] TSC synchronization [CPU#0 -> CPU#1]:
[    0.112000] Measured 2941403890 cycles TSC warp between CPUs, turning off TSC clock.
[    0.112000] tsc: Marking TSC unstable due to check_tsc_sync_source failed
[    0.112088] Brought up 2 CPUs
[    0.112094] smpboot: Total of 2 processors activated (6649.74 BogoMIPS)
[    0.120145] devtmpfs: initialized
[    0.120577] EVM: security.selinux
[    0.120582] EVM: security.SMACK64
[    0.120585] EVM: security.capability
[    0.122742] regulator-dummy: no parameters
[    0.122808] RTC time: 15:31:57, date: 02/18/14
[    0.122919] NET: Registered protocol family 16
[    0.123329] EISA bus registered
[    0.123522] ACPI: bus type PCI registered
[    0.123529] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.123682] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.123690] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.123694] PCI: Using MMCONFIG for extended config space
[    0.123698] PCI: Using configuration type 1 for base access
[    0.123723] dmi type 0xB1 record - unknown flag
[    0.128171] bio: create slab <bio-0> at 0
[    0.128235] ACPI: Added _OSI(Module Device)
[    0.128242] ACPI: Added _OSI(Processor Device)
[    0.128247] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.128253] ACPI: Added _OSI(Processor Aggregator Device)
[    0.130168] ACPI: EC: Look up EC in DSDT
[    0.140744] ACPI: SSDT 9f6d4172 00202 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.141480] ACPI: Dynamic OEM Table Load:
[    0.141487] ACPI: SSDT   (null) 00202 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.141730] ACPI: SSDT 9f6d3f27 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.142421] ACPI: Dynamic OEM Table Load:
[    0.142428] ACPI: SSDT   (null) 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.143040] ACPI: SSDT 9f6d4374 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.143767] ACPI: Dynamic OEM Table Load:
[    0.143774] ACPI: SSDT   (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.144021] ACPI: SSDT 9f6d40ed 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.144721] ACPI: Dynamic OEM Table Load:
[    0.144728] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.145239] ACPI: Interpreter enabled
[    0.145263] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.145275] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.145313] ACPI: (supports S0 S3 S4 S5)
[    0.145317] ACPI: Using IOAPIC for interrupt routing
[    0.145382] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.152068] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.238557] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.238572] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.238578] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.267401] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.267802] PCI host bridge to bus 0000:00
[    0.267811] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.267818] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.267825] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.267831] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.267838] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.267844] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xefffffff]
[    0.267851] pci_bus 0000:00: root bus resource [mem 0xf4007000-0xf4007fff]
[    0.267857] pci_bus 0000:00: root bus resource [mem 0xf400c000-0xfebfffff]
[    0.267864] pci_bus 0000:00: root bus resource [mem 0xfec10000-0xfecfffff]
[    0.267870] pci_bus 0000:00: root bus resource [mem 0xfed00400-0xfed1ffff]
[    0.267877] pci_bus 0000:00: root bus resource [mem 0xfee10000-0xffafffff]
[    0.267901] pci 0000:00:00.0: [8086:27a0] type 00 class 0x060000
[    0.268191] pci 0000:00:02.0: [8086:27a2] type 00 class 0x030000
[    0.268220] pci 0000:00:02.0: reg 0x10: [mem 0xeff00000-0xeff7ffff]
[    0.268235] pci 0000:00:02.0: reg 0x14: [io  0xeff8-0xefff]
[    0.268251] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff pref]
[    0.268266] pci 0000:00:02.0: reg 0x1c: [mem 0xefec0000-0xefefffff]
[    0.268538] pci 0000:00:02.1: [8086:27a6] type 00 class 0x038000
[    0.268562] pci 0000:00:02.1: reg 0x10: [mem 0xeff80000-0xefffffff]
[    0.268930] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.268968] pci 0000:00:1b.0: reg 0x10: [mem 0xefebc000-0xefebffff 64bit]
[    0.269124] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.269282] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.269387] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.269551] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.269712] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.269819] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.269983] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.270143] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.270255] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.270341] pci 0000:00:1d.0: reg 0x20: [io  0xbf80-0xbf9f]
[    0.273543] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.273644] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.273730] pci 0000:00:1d.1: reg 0x20: [io  0xbf60-0xbf7f]
[    0.277107] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.277208] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.277293] pci 0000:00:1d.2: reg 0x20: [io  0xbf40-0xbf5f]
[    0.280550] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.280655] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.280741] pci 0000:00:1d.3: reg 0x20: [io  0xbf20-0xbf3f]
[    0.284028] pci 0000:00:1d.3: System wakeup disabled by ACPI
[    0.284146] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.284188] pci 0000:00:1d.7: reg 0x10: [mem 0xffa80000-0xffa803ff]
[    0.284346] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.287546] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.287654] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.287916] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.288035] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
[    0.288195] pci 0000:00:1f.0: address space collision: [io  0x1000-0x107f] conflicts with ACPI CPU throttle [??? 0x00001010-0x00001015 flags 0x80000000]
[    0.288208] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.288217] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.288229] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.288513] pci 0000:00:1f.2: [8086:27c4] type 00 class 0x010180
[    0.288548] pci 0000:00:1f.2: reg 0x10: [io  0x01f0-0x01f7]
[    0.288569] pci 0000:00:1f.2: reg 0x14: [io  0x03f4-0x03f7]
[    0.288590] pci 0000:00:1f.2: reg 0x18: [io  0x0170-0x0177]
[    0.288610] pci 0000:00:1f.2: reg 0x1c: [io  0x0374-0x0377]
[    0.288631] pci 0000:00:1f.2: reg 0x20: [io  0xbfa0-0xbfaf]
[    0.288718] pci 0000:00:1f.2: PME# supported from D3hot
[    0.288946] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.289049] pci 0000:00:1f.3: reg 0x20: [io  0x10c0-0x10df]
[    0.289456] pci 0000:00:1c.0: PCI bridge to [bus 0b]
[    0.289741] pci 0000:0c:00.0: [8086:4222] type 00 class 0x028000
[    0.289811] pci 0000:0c:00.0: reg 0x10: [mem 0xefdff000-0xefdfffff]
[    0.290287] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.290503] pci 0000:0c:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.290541] pci 0000:00:1c.1: PCI bridge to [bus 0c]
[    0.290556] pci 0000:00:1c.1:   bridge window [mem 0xefd00000-0xefdfffff]
[    0.290724] acpiphp_glue: can't evaluate _ADR (0x5)
[    0.290771] acpiphp: Slot [1] registered
[    0.290809] pci 0000:02:00.0: [14e4:170c] type 00 class 0x020000
[    0.290844] pci 0000:02:00.0: reg 0x10: [mem 0xefcfe000-0xefcfffff]
[    0.290984] pci 0000:02:00.0: supports D1 D2
[    0.290990] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.291188] pci 0000:00:1e.0: PCI bridge to [bus 02] (subtractive decode)
[    0.291203] pci 0000:00:1e.0:   bridge window [mem 0xefc00000-0xefcfffff]
[    0.291218] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.291225] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.291232] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.291239] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.291245] pci 0000:00:1e.0:   bridge window [mem 0xa0000000-0xefffffff] (subtractive decode)
[    0.291252] pci 0000:00:1e.0:   bridge window [mem 0xf4007000-0xf4007fff] (subtractive decode)
[    0.291259] pci 0000:00:1e.0:   bridge window [mem 0xf400c000-0xfebfffff] (subtractive decode)
[    0.291266] pci 0000:00:1e.0:   bridge window [mem 0xfec10000-0xfecfffff] (subtractive decode)
[    0.291273] pci 0000:00:1e.0:   bridge window [mem 0xfed00400-0xfed1ffff] (subtractive decode)
[    0.291279] pci 0000:00:1e.0:   bridge window [mem 0xfee10000-0xffafffff] (subtractive decode)
[    0.291314] pci_bus 0000:00: on NUMA node 0
[    0.299287] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.299528] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
[    0.299730] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *0, disabled.
[    0.299936] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    0.300189] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.300436] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.300683] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.300929] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.305307] ACPI: Enabled 3 GPEs in block 00 to 1F
[    0.305340] ACPI: \_SB_.PCI0: notify handler is installed
[    0.308115] Found 1 acpi root devices
[    0.308519] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.308535] vgaarb: loaded
[    0.308539] vgaarb: bridge control possible 0000:00:02.0
[    0.309133] SCSI subsystem initialized
[    0.309140] ACPI: bus type ATA registered
[    0.309194] libata version 3.00 loaded.
[    0.309194] ACPI: bus type USB registered
[    0.309194] usbcore: registered new interface driver usbfs
[    0.309194] usbcore: registered new interface driver hub
[    0.309194] usbcore: registered new device driver usb
[    0.309194] PCI: Using ACPI for IRQ routing
[    0.314715] PCI: pci_cache_line_size set to 64 bytes
[    0.314817] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.314823] e820: reserve RAM buffer [mem 0x9f6d3400-0x9fffffff]
[    0.315069] NetLabel: Initializing
[    0.315074] NetLabel:  domain hash size = 128
[    0.315078] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.315106] NetLabel:  unlabeled traffic allowed by default
[    0.315139] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.315139] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.315139] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.317025] Switched to clocksource hpet
[    0.336571] AppArmor: AppArmor Filesystem Enabled
[    0.336639] pnp: PnP ACPI init
[    0.336681] ACPI: bus type PNP registered
[    0.358510] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.358520] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.358528] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.358536] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.358544] system 00:00: [mem 0x00100000-0x9f6d33ff] could not be reserved
[    0.358552] system 00:00: [mem 0x9f6d3400-0x9f6fffff] has been reserved
[    0.358559] system 00:00: [mem 0x9f700000-0x9f7fffff] has been reserved
[    0.358567] system 00:00: [mem 0x9f700000-0x9fefffff] could not be reserved
[    0.358575] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
[    0.358583] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.358590] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.358598] system 00:00: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.358606] system 00:00: [mem 0xffa80000-0xffa83fff] could not be reserved
[    0.358614] system 00:00: [mem 0xf4000000-0xf4003fff] has been reserved
[    0.358621] system 00:00: [mem 0xf4004000-0xf4004fff] has been reserved
[    0.358629] system 00:00: [mem 0xf4005000-0xf4005fff] has been reserved
[    0.358637] system 00:00: [mem 0xf4006000-0xf4006fff] has been reserved
[    0.358644] system 00:00: [mem 0xf4008000-0xf400bfff] has been reserved
[    0.358652] system 00:00: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.358663] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.358742] pnp 00:01: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.358751] pnp 00:01: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.358827] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.358837] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.358907] pnp 00:02: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.358915] pnp 00:02: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.358923] pnp 00:02: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.358931] pnp 00:02: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.359004] system 00:02: [io  0xf400-0xf4fe] has been reserved
[    0.359012] system 00:02: [io  0x1080-0x10bf] has been reserved
[    0.359019] system 00:02: [io  0x10c0-0x10df] has been reserved
[    0.359027] system 00:02: [io  0x0809] has been reserved
[    0.359036] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.359155] pnp 00:03: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.359260] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.359363] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.359469] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.359599] system 00:07: [io  0x0c80-0x0cff] could not be reserved
[    0.359607] system 00:07: [io  0x0910-0x091f] has been reserved
[    0.359615] system 00:07: [io  0x0920-0x092f] has been reserved
[    0.359622] system 00:07: [io  0x0cb0-0x0cbf] has been reserved
[    0.359630] system 00:07: [io  0x0930-0x097f] has been reserved
[    0.359639] system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.359688] pnp 00:08: [dma 4]
[    0.359757] pnp 00:08: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.359862] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.360072] system 00:0a: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.360083] system 00:0a: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.369475] pnp: PnP ACPI: found 11 devices
[    0.369481] ACPI: bus type PNP unregistered
[    0.369488] PnPBIOS: Disabled by ACPI PNP
[    0.409990] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 0b] add_size 1000
[    0.410003] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0b] add_size 200000
[    0.410011] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 0b] add_size 200000
[    0.410032] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 0c] add_size 1000
[    0.410041] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0c] add_size 200000
[    0.410068] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.410078] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.410086] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.410093] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.410100] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.410108] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.410121] pci 0000:00:1c.0: BAR 14: assigned [mem 0xa0000000-0xa01fffff]
[    0.410130] pci 0000:00:1c.0: BAR 15: assigned [mem 0xa0200000-0xa03fffff 64bit pref]
[    0.410140] pci 0000:00:1c.1: BAR 15: assigned [mem 0xa0400000-0xa05fffff 64bit pref]
[    0.410150] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.410159] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.410167] pci 0000:00:1c.0: PCI bridge to [bus 0b]
[    0.410176] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.410189] pci 0000:00:1c.0:   bridge window [mem 0xa0000000-0xa01fffff]
[    0.410200] pci 0000:00:1c.0:   bridge window [mem 0xa0200000-0xa03fffff 64bit pref]
[    0.410215] pci 0000:00:1c.1: PCI bridge to [bus 0c]
[    0.410224] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.410236] pci 0000:00:1c.1:   bridge window [mem 0xefd00000-0xefdfffff]
[    0.410247] pci 0000:00:1c.1:   bridge window [mem 0xa0400000-0xa05fffff 64bit pref]
[    0.410261] pci 0000:00:1e.0: PCI bridge to [bus 02]
[    0.410274] pci 0000:00:1e.0:   bridge window [mem 0xefc00000-0xefcfffff]
[    0.411177] pci 0000:00:1e.0: setting latency timer to 64
[    0.411188] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.411195] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.411201] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.411208] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.411214] pci_bus 0000:00: resource 8 [mem 0xa0000000-0xefffffff]
[    0.411221] pci_bus 0000:00: resource 9 [mem 0xf4007000-0xf4007fff]
[    0.411228] pci_bus 0000:00: resource 10 [mem 0xf400c000-0xfebfffff]
[    0.411234] pci_bus 0000:00: resource 11 [mem 0xfec10000-0xfecfffff]
[    0.411241] pci_bus 0000:00: resource 12 [mem 0xfed00400-0xfed1ffff]
[    0.411247] pci_bus 0000:00: resource 13 [mem 0xfee10000-0xffafffff]
[    0.411254] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.411261] pci_bus 0000:0b: resource 1 [mem 0xa0000000-0xa01fffff]
[    0.411268] pci_bus 0000:0b: resource 2 [mem 0xa0200000-0xa03fffff 64bit pref]
[    0.411275] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.411281] pci_bus 0000:0c: resource 1 [mem 0xefd00000-0xefdfffff]
[    0.411288] pci_bus 0000:0c: resource 2 [mem 0xa0400000-0xa05fffff 64bit pref]
[    0.411295] pci_bus 0000:02: resource 1 [mem 0xefc00000-0xefcfffff]
[    0.411302] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    0.411308] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    0.411314] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    0.411321] pci_bus 0000:02: resource 7 [mem 0x000d0000-0x000dffff]
[    0.411327] pci_bus 0000:02: resource 8 [mem 0xa0000000-0xefffffff]
[    0.411334] pci_bus 0000:02: resource 9 [mem 0xf4007000-0xf4007fff]
[    0.411340] pci_bus 0000:02: resource 10 [mem 0xf400c000-0xfebfffff]
[    0.411347] pci_bus 0000:02: resource 11 [mem 0xfec10000-0xfecfffff]
[    0.411353] pci_bus 0000:02: resource 12 [mem 0xfed00400-0xfed1ffff]
[    0.411360] pci_bus 0000:02: resource 13 [mem 0xfee10000-0xffafffff]
[    0.411434] NET: Registered protocol family 2
[    0.411813] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.411897] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.411977] TCP: Hash tables configured (established 8192 bind 8192)
[    0.412037] TCP: reno registered
[    0.412045] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.412065] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.412216] NET: Registered protocol family 1
[    0.412247] pci 0000:00:02.0: Boot video device
[    0.416515] PCI: CLS 64 bytes, default 64
[    0.416611] Trying to unpack rootfs image as initramfs...
[    1.228372] Freeing initrd memory: 16648K (f5f6c000 - f6fae000)
[    1.228806] Scanning for low memory corruption every 60 seconds
[    1.229371] Initialise module verification
[    1.229485] audit: initializing netlink socket (disabled)
[    1.229512] type=2000 audit(1392737518.228:1): initialized
[    1.286299] bounce pool size: 64 pages
[    1.286340] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.290349] zbud: loaded
[    1.290481] VFS: Disk quotas dquot_6.5.2
[    1.290615] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.292082] fuse init (API version 7.22)
[    1.292315] msgmni has been set to 1708
[    1.293461] Key type asymmetric registered
[    1.293467] Asymmetric key parser 'x509' registered
[    1.293559] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.293642] io scheduler noop registered
[    1.293647] io scheduler deadline registered (default)
[    1.293728] io scheduler cfq registered
[    1.294008] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.294185] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    1.294374] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.294418] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.294621] intel_idle: does not run on family 6 model 14
[    1.295944] ACPI: AC Adapter [AC] (off-line)
[    1.297219] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.297864] ACPI: Lid Switch [LID]
[    1.297973] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.297983] ACPI: Power Button [PBTN]
[    1.298088] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.298096] ACPI: Sleep Button [SBTN]
[    1.298277] ACPI: Requesting acpi_cpufreq
[    1.298772] ACPI: acpi_idle registered with cpuidle
[    1.308235] thermal LNXTHERM:00: registered as thermal_zone0
[    1.308242] ACPI: Thermal Zone [THM] (29 C)
[    1.308322] GHES: HEST is not enabled!
[    1.312364] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.321538] isapnp: Scanning for PnP cards...
[    1.338153] Linux agpgart interface v0.103
[    1.338330] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    1.338418] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.339343] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.351260] ACPI: Battery Slot [BAT0] (battery present)
[    1.351330] ACPI: Battery Slot [BAT1] (battery absent)
[    1.351474] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.355327] brd: module loaded
[    1.357390] loop: module loaded
[    1.357704] ata_piix 0000:00:1f.2: version 2.13
[    1.358152] ata_piix 0000:00:1f.2: MAP [
[    1.358157]  P0 P2 IDE IDE ]
[    1.358231] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.358931] scsi0 : ata_piix
[    1.359536] scsi1 : ata_piix
[    1.360134] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.360141] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.360979] libphy: Fixed MDIO Bus: probed
[    1.361267] tun: Universal TUN/TAP device driver, 1.6
[    1.361271] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.361385] PPP generic driver version 2.4.2
[    1.361492] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.361498] ehci-pci: EHCI PCI platform driver
[    1.361965] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.361989] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.362005] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.362033] ehci-pci 0000:00:1d.7: debug port 1
[    1.365954] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.366102] ehci-pci 0000:00:1d.7: irq 20, io mem 0xffa80000
[    1.376035] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.376119] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.376126] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.376132] usb usb1: Product: EHCI Host Controller
[    1.376139] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    1.376145] usb usb1: SerialNumber: 0000:00:1d.7
[    1.376417] hub 1-0:1.0: USB hub found
[    1.376430] hub 1-0:1.0: 8 ports detected
[    1.377257] ehci-platform: EHCI generic platform driver
[    1.377279] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.377283] ohci-pci: OHCI PCI platform driver
[    1.377313] ohci-platform: OHCI generic platform driver
[    1.377332] uhci_hcd: USB Universal Host Controller Interface driver
[    1.377784] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.377793] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.377806] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.377848] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    1.377919] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.377926] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.377932] usb usb2: Product: UHCI Host Controller
[    1.377939] usb usb2: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.377945] usb usb2: SerialNumber: 0000:00:1d.0
[    1.378195] hub 2-0:1.0: USB hub found
[    1.378207] hub 2-0:1.0: 2 ports detected
[    1.378869] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.378878] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.378891] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.378955] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    1.379026] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.379033] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.379039] usb usb3: Product: UHCI Host Controller
[    1.379045] usb usb3: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.379052] usb usb3: SerialNumber: 0000:00:1d.1
[    1.379292] hub 3-0:1.0: USB hub found
[    1.379306] hub 3-0:1.0: 2 ports detected
[    1.379966] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.379975] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.379988] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.380084] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    1.380156] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.380163] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.380169] usb usb4: Product: UHCI Host Controller
[    1.380175] usb usb4: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.380181] usb usb4: SerialNumber: 0000:00:1d.2
[    1.380424] hub 4-0:1.0: USB hub found
[    1.380436] hub 4-0:1.0: 2 ports detected
[    1.381111] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.381120] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.381133] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.381195] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    1.381267] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.381273] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.381279] usb usb5: Product: UHCI Host Controller
[    1.381286] usb usb5: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.381292] usb usb5: SerialNumber: 0000:00:1d.3
[    1.381550] hub 5-0:1.0: USB hub found
[    1.381561] hub 5-0:1.0: 2 ports detected
[    1.381978] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.385318] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.385332] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.385608] mousedev: PS/2 mouse device common for all mice
[    1.385958] rtc_cmos 00:05: RTC can wake from S4
[    1.386201] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.386246] rtc_cmos 00:05: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.386428] device-mapper: uevent: version 1.0.3
[    1.386602] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.386658] platform eisa.0: Probing EISA bus 0
[    1.386730] eisa 00:00: [io  0x0c80-0x0c83]
[    1.386736] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.386777] platform eisa.0: EISA: Detected 0 cards
[    1.386793] cpufreq-nforce2: No nForce2 chipset.
[    1.386907] cpuidle: using governor ladder
[    1.387065] cpuidle: using governor menu
[    1.387091] ledtrig-cpu: registered to indicate activity on CPUs
[    1.387313] TCP: cubic registered
[    1.387617] NET: Registered protocol family 10
[    1.388223] NET: Registered protocol family 17
[    1.388246] Key type dns_resolver registered
[    1.388706] Using IPI No-Shortcut mode
[    1.388897] PM: Hibernation image not present or could not be loaded.
[    1.388906] Loading module verification certificates
[    1.389050] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.400740] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 5f32dde6ae99ae14b29fb35e935289fb4b6cfb20'
[    1.400769] registered taskstats version 1
[    1.406047] Key type trusted registered
[    1.410573] Key type encrypted registered
[    1.415144] AppArmor: AppArmor sha1 policy hashing enabled
[    1.415712]   Magic number: 2:396:538
[    1.415754] tty ttyS18: hash matches
[    1.415878] rtc_cmos 00:05: setting system clock to 2014-02-18 15:31:58 UTC (1392737518)
[    1.417250] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.417255] EDD information not available.
[    1.528544] ata1.00: ATA-7: Hitachi HTS541060G9SA00, MB3OC60R, max UDMA/100
[    1.528552] ata1.00: 117210240 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.544625] ata2.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462D, DE10, max UDMA/33
[    1.545043] ata1.00: configured for UDMA/100
[    1.576359] ata2.00: configured for UDMA/33
[    1.682056] isapnp: No Plug & Play device found
[    1.682368] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54106 MB3O PQ: 0 ANSI: 5
[    1.682691] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.682749] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.682815] sd 0:0:0:0: [sda] Write Protect is off
[    1.682824] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.683090] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.683684] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRWDVD TSL462D  DE10 PQ: 0 ANSI: 5
[    1.685553] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.685563] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.685905] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.686121] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.688076] usb 1-2: new high-speed USB device number 2 using ehci-pci
[    1.733255]  sda: sda1 sda2 < sda5 >
[    1.734210] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.734870] Freeing unused kernel memory: 880K (c1972000 - c1a4e000)
[    1.734979] Write protecting the kernel text: 6360k
[    1.735201] Write protecting the kernel read-only data: 2700k
[    1.735205] NX-protecting the kernel data: 5928k
[    1.763153] systemd-udevd[101]: starting version 204
[    1.820421] usb 1-2: New USB device found, idVendor=413c, idProduct=a005
[    1.820432] usb 1-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.820728] hub 1-2:1.0: USB hub found
[    1.820780] hub 1-2:1.0: 4 ports detected
[    1.908140] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[    1.908156] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.908168] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.908179] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.948229] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    1.948287] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.968844] b44 ssb0:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:15:c5:b5:9f:eb
[    2.124118] usb 4-2: new low-speed USB device number 2 using uhci_hcd
[    2.298106] usb 4-2: New USB device found, idVendor=0458, idProduct=003a
[    2.298117] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.298124] usb 4-2: Product: Optical Mouse
[    2.298130] usb 4-2: Manufacturer: Genius
[    2.335455] hidraw: raw HID events driver (C) Jiri Kosina
[    2.368346] usbcore: registered new interface driver usbhid
[    2.368354] usbhid: USB HID core driver
[    2.381875] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input4
[    2.382132] hid-generic 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:1d.2-2/input0
[    2.404203] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.117741] Adding 2610172k swap on /dev/sda5.  Priority:-1 extents:1 across:2610172k FS
[   13.345364] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.520517] systemd-udevd[263]: starting version 204
[   13.677666] lp: driver loaded but no devices found
[   13.755501] [drm] Initialized drm 1.1.0 20060810
[   13.785918] wmi: Mapper loaded
[   13.792312] acpi device:23: registered as cooling_device2
[   13.792571] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   13.792698] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5
[   13.794178] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   13.849254] [drm] Memory usable by graphics device = 256M
[   13.849267] i915 0000:00:02.0: setting latency timer to 64
[   13.851017] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.851022] [drm] Driver supports precise vblank timestamp query.
[   13.851126] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.941129] intel_rng: FWH not detected
[   13.941294] cfg80211: Calling CRDA to update world regulatory domain
[   14.069079] microcode: CPU0 sig=0x6e8, pf=0x20, revision=0x39
[   14.101732] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.101738] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   14.101798] iwl3945 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.158340] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 4 802.11a channels
[   14.158348] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.158426] iwl3945 0000:0c:00.0: irq 42 for MSI/MSI-X
[   14.187303] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   14.224236] [drm] initialized overlay support
[   14.257078] type=1400 audit(1392737531.338:2): apparmor="STATUS" operation="profile_load" parent=311 profile="unconfined" name="/sbin/dhclient" pid=325 comm="apparmor_parser"
[   14.257091] type=1400 audit(1392737531.338:3): apparmor="STATUS" operation="profile_load" parent=311 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=325 comm="apparmor_parser"
[   14.257100] type=1400 audit(1392737531.338:4): apparmor="STATUS" operation="profile_load" parent=311 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=325 comm="apparmor_parser"
[   14.258115] type=1400 audit(1392737531.338:5): apparmor="STATUS" operation="profile_replace" parent=311 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=325 comm="apparmor_parser"
[   14.258126] type=1400 audit(1392737531.338:6): apparmor="STATUS" operation="profile_replace" parent=311 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=325 comm="apparmor_parser"
[   14.258674] type=1400 audit(1392737531.338:7): apparmor="STATUS" operation="profile_replace" parent=311 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=325 comm="apparmor_parser"
[   14.262599] type=1400 audit(1392737531.342:8): apparmor="STATUS" operation="profile_load" parent=311 profile="unconfined" name="/usr/sbin/ntpd" pid=340 comm="apparmor_parser"
[   14.666304] fbcon: inteldrmfb (fb0) is primary device
[   14.896681] Console: switching to colour frame buffer device 128x48
[   14.901854] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   14.901857] i915 0000:00:02.0: registered panic notifier
[   14.901869] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.902729] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   14.910537] leds_ss4200: no LED devices found
[   14.928650] autoconfig: line_outs=1 (0xe/0x0/0x0/0x0/0x0) type:speaker
[   14.928657]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.928660]    hp_outs=1 (0xd/0x0/0x0/0x0/0x0)
[   14.928662]    mono: mono_out=0x0
[   14.928665]    dig-out=0x9/0x0
[   14.928667]    inputs:
[   14.928670]      Mic=0x10
[   14.928673]      Internal Mic=0xf
[   14.940372] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   14.940502] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   14.970061] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.077165] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   15.078726] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   15.094217] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   15.131245] microcode: CPU1 sig=0x6e8, pf=0x20, revision=0x39
[   15.153954] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   15.194188] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   15.585895] cfg80211: World regulatory domain updated:
[   15.585902] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.585906] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.585909] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.585913] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.585916] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.585919] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.683643] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.481839] init: failsafe main process (540) killed by TERM signal
[   16.987151] Bluetooth: Core ver 2.16
[   16.987183] NET: Registered protocol family 31
[   16.987186] Bluetooth: HCI device and connection manager initialized
[   16.987614] Bluetooth: HCI socket layer initialized
[   16.987619] Bluetooth: L2CAP socket layer initialized
[   16.987629] Bluetooth: SCO socket layer initialized
[   17.007994] Bluetooth: RFCOMM TTY layer initialized
[   17.008124] Bluetooth: RFCOMM socket layer initialized
[   17.008128] Bluetooth: RFCOMM ver 1.11
[   17.064936] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.064943] Bluetooth: BNEP filters: protocol multicast
[   17.064956] Bluetooth: BNEP socket layer initialized
[   17.679096] init: avahi-cups-reload main process (711) terminated with status 1
[   17.808957] ppdev: user-space parallel port driver
[   17.838614] type=1400 audit(1392737534.919:9): apparmor="STATUS" operation="profile_load" parent=726 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=730 comm="apparmor_parser"
[   17.838629] type=1400 audit(1392737534.919:10): apparmor="STATUS" operation="profile_load" parent=726 profile="unconfined" name="/usr/sbin/cupsd" pid=730 comm="apparmor_parser"
[   17.839807] type=1400 audit(1392737534.919:11): apparmor="STATUS" operation="profile_replace" parent=726 profile="unconfined" name="/usr/sbin/cupsd" pid=730 comm="apparmor_parser"
[   19.054468] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   19.126979] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.127515] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.135307] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.135800] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.260736] type=1400 audit(1392737536.343:12): apparmor="STATUS" operation="profile_load" parent=775 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=780 comm="apparmor_parser"
[   19.260752] type=1400 audit(1392737536.343:13): apparmor="STATUS" operation="profile_load" parent=775 profile="unconfined" name="chromium_browser" pid=780 comm="apparmor_parser"
[   19.261597] type=1400 audit(1392737536.343:14): apparmor="STATUS" operation="profile_replace" parent=775 profile="unconfined" name="chromium_browser" pid=780 comm="apparmor_parser"
[   19.263964] type=1400 audit(1392737536.343:15): apparmor="STATUS" operation="profile_replace" parent=775 profile="unconfined" name="/sbin/dhclient" pid=781 comm="apparmor_parser"
[   19.263979] type=1400 audit(1392737536.343:16): apparmor="STATUS" operation="profile_replace" parent=775 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=781 comm="apparmor_parser"
[   19.263988] type=1400 audit(1392737536.343:17): apparmor="STATUS" operation="profile_replace" parent=775 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=781 comm="apparmor_parser"
[   19.265439] type=1400 audit(1392737536.347:18): apparmor="STATUS" operation="profile_replace" parent=775 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=781 comm="apparmor_parser"
[   19.265450] type=1400 audit(1392737536.347:19): apparmor="STATUS" operation="profile_replace" parent=775 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=781 comm="apparmor_parser"
[   19.266001] type=1400 audit(1392737536.347:20): apparmor="STATUS" operation="profile_replace" parent=775 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=781 comm="apparmor_parser"
[   19.273961] type=1400 audit(1392737536.355:21): apparmor="STATUS" operation="profile_replace" parent=775 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=784 comm="apparmor_parser"
[   19.761521] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   19.782504] zram: Created 2 device(s) ...
[   19.823366] Adding 643608k swap on /dev/zram0.  Priority:5 extents:1 across:643608k SSFS
[   19.848088] Adding 643608k swap on /dev/zram1.  Priority:5 extents:1 across:643608k SSFS
[   22.816221] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[   22.816229] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[   22.816335] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  201.844459] iwl3945 0000:0c:00.0: Card state received: HW:Kill SW:On
[  201.880041] iwl3945 0000:0c:00.0: Not sending command - RF KILL
[  201.880052] iwl3945 0000:0c:00.0: Error sending C_RXON: enqueue_hcmd failed: -5
[  201.880057] iwl3945 0000:0c:00.0: Error setting new configuration (-5).
[  201.884012] iwl3945 0000:0c:00.0: Master Disable Timed Out, 100 usec
[  203.894218] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.000181] CE: hpet increased min_delta_ns to 20115 nsec
```

```
iwlist scan
wlan0     No scan results


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


sudo iwlist wlan0 scan
wlan0     No scan results


lsb_release -d
Description:    Ubuntu 13.10

uname -mr
3.11.0-15-generic i686

sudo service networking restart
blank screen with cross mark on it
```

---

### Post by chili555 on 2014-02-18
> iwl3945 0000:0c:00.0: Card state received: HW:Kill SW:OnHmmmm...What does this tell us?```
rfkill list all
```

---

