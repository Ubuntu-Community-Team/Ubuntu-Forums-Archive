---
title: "Get a &quot;device not ready&quot; error in 12.04, but only on one particular network"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by cmalk on 2013-09-10
I followed the instructions in the sticky at the top and posted the readouts below.

My wireless card usually works just fine, but for some reason this one particular home router is giving me issues. (I connected to it with no issues about 8 months ago.) When I boot up the network manager asks me to re-type the network password, though after I type it in it doesn't try to connect, it just gives up and says "wireless device not ready." I go to the coffee shop and connect there without any issues. I have no idea what's going on, but I ran the following commands and got the readouts below.

Any help would be greatly appreciated.
-Cary


The model is a Dell Inspiron 1464.

: lspci gives
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

: lsusb gives
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam

```

: ifconfig gives
```
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:55:ea:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xc000 


eth1      Link encap:Ethernet  HWaddr 70:f1:a1:11:a4:ed  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fe11:a4ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:852 errors:0 dropped:0 overruns:0 frame:617
          TX packets:726 errors:50 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:845083 (845.0 KB)  TX bytes:199304 (199.3 KB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47576 (47.5 KB)  TX bytes:47576 (47.5 KB)

```

: iwconfig gives
```
eth1      IEEE 802.11abg  ESSID:"Malkiewich"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:72:B5:C8   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```          
: lsmod gives
```
Module                  Size  Used by
dm_crypt               23125  0 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33719  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rfcomm                 47604  4 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
psmouse                97519  0 
serio_raw              13211  0 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
bnep                   18281  2 
parport_pc             32866  0 
mac_hid                13253  0 
bluetooth             180113  10 rfcomm,bnep
lib80211_crypt_tkip    17390  0 
ppdev                  17113  0 
intel_ips              18174  0 
snd_timer              29990  2 snd_pcm,snd_seq
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   3074895  0 
cfg80211              205774  1 wl
snd                    79041  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14381  2 lib80211_crypt_tkip,wl
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
wmi                    19256  1 dell_wmi
r8169                  62190  0 
i915                  478239  7 
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915

```

: dmesg gives
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-52-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 (Ubuntu 3.2.0-52.78-generic 3.2.48)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-52-generic root=UUID=c317cfb0-4e47-4451-a398-85b378b49064 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bb27c000 (usable)
[    0.000000]  BIOS-e820: 00000000bb27c000 - 00000000bb282000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb282000 - 00000000bb3ea000 (usable)
[    0.000000]  BIOS-e820: 00000000bb3ea000 - 00000000bb40f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb40f000 - 00000000bb46f000 (usable)
[    0.000000]  BIOS-e820: 00000000bb46f000 - 00000000bb470000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb470000 - 00000000bb4f1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bb4f1000 - 00000000bb70f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb70f000 - 00000000bb717000 (usable)
[    0.000000]  BIOS-e820: 00000000bb717000 - 00000000bb71f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb71f000 - 00000000bb77e000 (usable)
[    0.000000]  BIOS-e820: 00000000bb77e000 - 00000000bb79f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bb79f000 - 00000000bb7e2000 (usable)
[    0.000000]  BIOS-e820: 00000000bb7e2000 - 00000000bb7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bb7ff000 - 00000000bb800000 (usable)
[    0.000000]  BIOS-e820: 00000000bb800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0704000 - 00000000f0705000 (reserved)
[    0.000000]  BIOS-e820: 00000000feaff000 - 00000000feb00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Dell Inc. Inspiron 1464/0C6HFD, BIOS A04 01/17/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x138000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 100000000 mask FC0000000 write-back
[    0.000000]   4 base 138000000 mask FF8000000 uncachable
[    0.000000]   5 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbb800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f7260] f7260
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bb800000
[    0.000000]  0000000000 - 00bb800000 page 2M
[    0.000000] kernel direct mapping tables up to bb800000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000138000000
[    0.000000]  0100000000 - 0138000000 page 2M
[    0.000000] kernel direct mapping tables up to 138000000 @ bb7e0000-bb7e2000
[    0.000000] RAMDISK: 356e0000 - 36b68000
[    0.000000] ACPI: RSDP 00000000000f7180 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000bb7f467a 00064 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bb7e4000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 00000000bb7e5000 0A47C (v02 Intel  CALPELLA 06040000 INTL 20060912)
[    0.000000] ACPI: FACS 00000000bb79bfc0 00040
[    0.000000] ACPI: HPET 00000000bb7fecfa 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 00000000bb7fed32 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 00000000bb7fed6e 00084 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bb7fedf2 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 00000000bb7fee1a 00176 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: OSFR 00000000bb7fef90 00070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000bb7e3000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000138000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000138000000
[    0.000000]   NODE_DATA [0000000137ffb000 - 0000000137ffffff]
[    0.000000]  [ffffea0000000000-ffffea0004dfffff] PMD -> [ffff880133800000-ffff8801375fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00138000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000bb27c
[    0.000000]     0: 0x000bb282 -> 0x000bb3ea
[    0.000000]     0: 0x000bb40f -> 0x000bb46f
[    0.000000]     0: 0x000bb70f -> 0x000bb717
[    0.000000]     0: 0x000bb71f -> 0x000bb77e
[    0.000000]     0: 0x000bb79f -> 0x000bb7e2
[    0.000000]     0: 0x000bb7ff -> 0x000bb800
[    0.000000]     0: 0x00100000 -> 0x00138000
[    0.000000] On node 0 totalpages: 996475
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3911 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 746799 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 225792 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bb27c000 - 00000000bb282000
[    0.000000] PM: Registered nosave memory: 00000000bb3ea000 - 00000000bb40f000
[    0.000000] PM: Registered nosave memory: 00000000bb46f000 - 00000000bb470000
[    0.000000] PM: Registered nosave memory: 00000000bb470000 - 00000000bb4f1000
[    0.000000] PM: Registered nosave memory: 00000000bb4f1000 - 00000000bb70f000
[    0.000000] PM: Registered nosave memory: 00000000bb717000 - 00000000bb71f000
[    0.000000] PM: Registered nosave memory: 00000000bb77e000 - 00000000bb79f000
[    0.000000] PM: Registered nosave memory: 00000000bb7e2000 - 00000000bb7ff000
[    0.000000] PM: Registered nosave memory: 00000000bb800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f0704000
[    0.000000] PM: Registered nosave memory: 00000000f0704000 - 00000000f0705000
[    0.000000] PM: Registered nosave memory: 00000000f0705000 - 00000000feaff000
[    0.000000] PM: Registered nosave memory: 00000000feaff000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880137c00000 s83136 r8192 d23360 u524288
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 976502
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-52-generic root=UUID=c317cfb0-4e47-4451-a398-85b378b49064 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3819052k/5111808k available (6583k kernel code, 1125908k absent, 166848k reserved, 6623k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 32505856 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2127.902 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4255.80 BogoMIPS (lpj=8511608)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000031] Security Framework initialized
[    0.000047] AppArmor: AppArmor initialized
[    0.000049] Yama: becoming mindful.
[    0.000421] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001403] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001815] Mount-cache hash table entries: 256
[    0.001940] Initializing cgroup subsys cpuacct
[    0.001945] Initializing cgroup subsys memory
[    0.001953] Initializing cgroup subsys devices
[    0.001955] Initializing cgroup subsys freezer
[    0.001957] Initializing cgroup subsys blkio
[    0.001963] Initializing cgroup subsys perf_event
[    0.001993] CPU: Physical Processor ID: 0
[    0.001995] CPU: Processor Core ID: 0
[    0.002001] mce: CPU supports 9 MCE banks
[    0.002011] CPU0: Thermal monitoring handled by SMI
[    0.002020] using mwait in idle threads.
[    0.004431] ACPI: Core revision 20110623
[    0.023707] ftrace: allocating 26587 entries in 105 pages
[    0.033234] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072901] CPU0: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz stepping 02
[    0.180125] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.180133] ... version:                3
[    0.180134] ... bit width:              48
[    0.180136] ... generic registers:      4
[    0.180137] ... value mask:             0000ffffffffffff
[    0.180139] ... max period:             000000007fffffff
[    0.180140] ... fixed-purpose events:   3
[    0.180141] ... event mask:             000000070000000f
[    0.180309] NMI watchdog enabled, takes one hw-pmu counter.
[    0.180399] Booting Node   0, Processors  #1
[    0.180401] smpboot cpu 1: start_ip = 97000
[    0.268108] CPU1: Thermal monitoring handled by SMI
[    0.288204] NMI watchdog enabled, takes one hw-pmu counter.
[    0.288316]  #2
[    0.288318] smpboot cpu 2: start_ip = 97000
[    0.376062] CPU2: Thermal monitoring handled by SMI
[    0.396193] NMI watchdog enabled, takes one hw-pmu counter.
[    0.396309]  #3 Ok.
[    0.396311] smpboot cpu 3: start_ip = 97000
[    0.484011] CPU3: Thermal monitoring handled by SMI
[    0.504108] NMI watchdog enabled, takes one hw-pmu counter.
[    0.504153] Brought up 4 CPUs
[    0.504156] Total of 4 processors activated (17023.54 BogoMIPS).
[    0.507068] devtmpfs: initialized
[    0.508090] EVM: security.selinux
[    0.508092] EVM: security.SMACK64
[    0.508093] EVM: security.capability
[    0.508123] PM: Registering ACPI NVS region at bb470000 (528384 bytes)
[    0.508137] PM: Registering ACPI NVS region at bb77e000 (135168 bytes)
[    0.509088] print_constraints: dummy: 
[    0.509121] RTC time:  5:11:32, date: 09/10/13
[    0.509157] NET: Registered protocol family 16
[    0.509264] Trying to unpack rootfs image as initramfs...
[    0.509275] ACPI: bus type pci registered
[    0.509358] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.509362] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.575869] PCI: Using configuration type 1 for base access
[    0.576930] bio: create slab <bio-0> at 0
[    0.577028] ACPI: Added _OSI(Module Device)
[    0.577031] ACPI: Added _OSI(Processor Device)
[    0.577033] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.577035] ACPI: Added _OSI(Processor Aggregator Device)
[    0.578608] ACPI: EC: Look up EC in DSDT
[    0.604026] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.604976] ACPI: SSDT 00000000bb71ac18 003A0 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.605347] ACPI: Dynamic OEM Table Load:
[    0.605350] ACPI: SSDT           (null) 003A0 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.605482] ACPI: SSDT 00000000bb718698 005EC (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.605834] ACPI: Dynamic OEM Table Load:
[    0.605837] ACPI: SSDT           (null) 005EC (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.672217] ACPI: SSDT 00000000bb719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.672642] ACPI: Dynamic OEM Table Load:
[    0.672645] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.700058] ACPI: SSDT 00000000bb717d98 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.700454] ACPI: Dynamic OEM Table Load:
[    0.700457] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.724610] ACPI: Interpreter enabled
[    0.724616] ACPI: (supports S0 S3 S4 S5)
[    0.724640] ACPI: Using IOAPIC for interrupt routing
[    0.725096] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.730585] ACPI: Power Resource [FN00] (off)
[    0.730718] ACPI: Power Resource [FN01] (off)
[    0.731387] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.731648] ACPI: No dock devices found.
[    0.731651] HEST: Table not found.
[    0.731656] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.732331] \_SB_.PCI0:_OSC invalid UUID
[    0.732334] _OSC request data:1 8 0 
[    0.732340] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.733435] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.733440] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.733444] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.733449] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.733452] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.733455] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.733460] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.733463] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.733482] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    0.733508] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.733537] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    0.733553] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.733562] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.733570] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
[    0.733651] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    0.733685] pci 0000:00:16.0: reg 10: [mem 0xf0705800-0xf070580f 64bit]
[    0.733801] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.733809] pci 0000:00:16.0: PME# disabled
[    0.733857] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.733887] pci 0000:00:1a.0: reg 10: [mem 0xf0706000-0xf07063ff]
[    0.734008] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.734015] pci 0000:00:1a.0: PME# disabled
[    0.734054] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.734079] pci 0000:00:1b.0: reg 10: [mem 0xf0700000-0xf0703fff 64bit]
[    0.734188] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.734195] pci 0000:00:1b.0: PME# disabled
[    0.734228] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.734343] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.734349] pci 0000:00:1c.0: PME# disabled
[    0.734384] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    0.734498] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.734504] pci 0000:00:1c.1: PME# disabled
[    0.734543] pci 0000:00:1c.5: [8086:3b4c] type 1 class 0x000604
[    0.734657] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.734663] pci 0000:00:1c.5: PME# disabled
[    0.734712] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.734743] pci 0000:00:1d.0: reg 10: [mem 0xf0706400-0xf07067ff]
[    0.734865] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.734872] pci 0000:00:1d.0: PME# disabled
[    0.734902] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.735002] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
[    0.735149] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
[    0.735180] pci 0000:00:1f.2: reg 10: [io  0x1818-0x181f]
[    0.735194] pci 0000:00:1f.2: reg 14: [io  0x180c-0x180f]
[    0.735208] pci 0000:00:1f.2: reg 18: [io  0x1810-0x1817]
[    0.735221] pci 0000:00:1f.2: reg 1c: [io  0x1808-0x180b]
[    0.735234] pci 0000:00:1f.2: reg 20: [io  0x1820-0x183f]
[    0.735248] pci 0000:00:1f.2: reg 24: [mem 0xf0705000-0xf07057ff]
[    0.735324] pci 0000:00:1f.2: PME# supported from D3hot
[    0.735330] pci 0000:00:1f.2: PME# disabled
[    0.735357] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.735383] pci 0000:00:1f.3: reg 10: [mem 0xf0706800-0xf07068ff 64bit]
[    0.735417] pci 0000:00:1f.3: reg 20: [io  0x1840-0x185f]
[    0.735475] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    0.735508] pci 0000:00:1f.6: reg 10: [mem 0xf0704000-0xf0704fff 64bit]
[    0.735683] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.736235] pci 0000:03:00.0: [14e4:4315] type 0 class 0x000280
[    0.736719] pci 0000:03:00.0: reg 10: [mem 0xf0400000-0xf0403fff 64bit]
[    0.739517] pci 0000:03:00.0: supports D1 D2
[    0.739521] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.739615] pci 0000:03:00.0: PME# disabled
[    0.740742] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.740751] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.740844] pci 0000:04:00.0: [10ec:8136] type 0 class 0x000200
[    0.740864] pci 0000:04:00.0: reg 10: [io  0x2000-0x20ff]
[    0.740896] pci 0000:04:00.0: reg 18: [mem 0xf0810000-0xf0810fff 64bit pref]
[    0.740917] pci 0000:04:00.0: reg 20: [mem 0xf0800000-0xf080ffff 64bit pref]
[    0.740933] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.741005] pci 0000:04:00.0: supports D1 D2
[    0.741008] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.741015] pci 0000:04:00.0: PME# disabled
[    0.748014] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.748022] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.748035] pci 0000:00:1c.5:   bridge window [mem 0xf0800000-0xf08fffff 64bit pref]
[    0.748122] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.748138] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.748142] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.748146] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.748150] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.748154] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.748158] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.748162] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.748166] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.748201] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.748493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.748668] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.748752] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.748834] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.748961] \_SB_.PCI0:_OSC invalid UUID
[    0.748964] _OSC request data:1 1f 0 
[    0.748970]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.749022] \_SB_.PCI0:_OSC invalid UUID
[    0.749025] _OSC request data:1 0 1d 
[    0.749030]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    0.749033] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.753267] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.753378] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    0.753410] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    0.753439] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    0.753465] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    0.753490] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    0.753515] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    0.753562]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
[    0.753566]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.753569] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.753941] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.754017] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.754085] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.754154] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.754222] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.754294] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.754364] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.754432] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.754594] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.754607] vgaarb: loaded
[    0.754609] vgaarb: bridge control possible 0000:00:02.0
[    0.754764] i2c-core: driver [aat2870] using legacy suspend method
[    0.754767] i2c-core: driver [aat2870] using legacy resume method
[    0.754862] SCSI subsystem initialized
[    0.754932] libata version 3.00 loaded.
[    0.754997] usbcore: registered new interface driver usbfs
[    0.755014] usbcore: registered new interface driver hub
[    0.755040] usbcore: registered new device driver usb
[    0.755161] PCI: Using ACPI for IRQ routing
[    0.765786] PCI: pci_cache_line_size set to 64 bytes
[    0.766013] reserve RAM buffer: 000000000009c400 - 000000000009ffff 
[    0.766018] reserve RAM buffer: 00000000bb27c000 - 00000000bbffffff 
[    0.766022] reserve RAM buffer: 00000000bb3ea000 - 00000000bbffffff 
[    0.766026] reserve RAM buffer: 00000000bb46f000 - 00000000bbffffff 
[    0.766030] reserve RAM buffer: 00000000bb717000 - 00000000bbffffff 
[    0.766034] reserve RAM buffer: 00000000bb77e000 - 00000000bbffffff 
[    0.766037] reserve RAM buffer: 00000000bb7e2000 - 00000000bbffffff 
[    0.766040] reserve RAM buffer: 00000000bb800000 - 00000000bbffffff 
[    0.766217] NetLabel: Initializing
[    0.766219] NetLabel:  domain hash size = 128
[    0.766222] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.766240] NetLabel:  unlabeled traffic allowed by default
[    0.766328] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.766338] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.768362] Switching to clocksource hpet
[    0.775082] AppArmor: AppArmor Filesystem Enabled
[    0.775116] pnp: PnP ACPI init
[    0.775137] ACPI: bus type pnp registered
[    0.775540] pnp 00:00: [bus 00-fe]
[    0.775543] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.775545] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.775547] pnp 00:00: [io  0x0d00-0xffff window]
[    0.775549] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.775551] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.775553] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.775555] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.775557] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.775559] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.775561] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.775564] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.775566] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.775568] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.775570] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.775572] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.775574] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.775576] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.775578] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.775580] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.775582] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.775662] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.775719] pnp 00:01: [io  0x0000-0x001f]
[    0.775721] pnp 00:01: [io  0x0081-0x0091]
[    0.775723] pnp 00:01: [io  0x0093-0x009f]
[    0.775724] pnp 00:01: [io  0x00c0-0x00df]
[    0.775727] pnp 00:01: [dma 4]
[    0.775755] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.775764] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.775789] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.775863] pnp 00:03: [irq 0 disabled]
[    0.775875] pnp 00:03: [irq 8]
[    0.775877] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.775903] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.775913] pnp 00:04: [io  0x00f0]
[    0.775919] pnp 00:04: [irq 13]
[    0.775946] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.775957] pnp 00:05: [io  0x002e-0x002f]
[    0.775959] pnp 00:05: [io  0x004e-0x004f]
[    0.775961] pnp 00:05: [io  0x0061]
[    0.775963] pnp 00:05: [io  0x0063]
[    0.775964] pnp 00:05: [io  0x0065]
[    0.775966] pnp 00:05: [io  0x0067]
[    0.775967] pnp 00:05: [io  0x0068]
[    0.775969] pnp 00:05: [io  0x006c]
[    0.775972] pnp 00:05: [io  0x0070]
[    0.775974] pnp 00:05: [io  0x0080]
[    0.775975] pnp 00:05: [io  0x0092]
[    0.775977] pnp 00:05: [io  0x00b2-0x00b3]
[    0.775979] pnp 00:05: [io  0x0680-0x069f]
[    0.775981] pnp 00:05: [io  0x0500-0x050f]
[    0.775982] pnp 00:05: [io  0x0600-0x0603]
[    0.775984] pnp 00:05: [io  0xffff]
[    0.775986] pnp 00:05: [io  0x0400-0x047f]
[    0.775987] pnp 00:05: [io  0x1180-0x11ff]
[    0.775989] pnp 00:05: [io  0x164e-0x164f]
[    0.775991] pnp 00:05: [io  0xfe00]
[    0.776053] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.776056] system 00:05: [io  0x0500-0x050f] has been reserved
[    0.776058] system 00:05: [io  0x0600-0x0603] has been reserved
[    0.776060] system 00:05: [io  0xffff] has been reserved
[    0.776063] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.776065] system 00:05: [io  0x1180-0x11ff] has been reserved
[    0.776067] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.776070] system 00:05: [io  0xfe00] has been reserved
[    0.776073] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.776105] pnp 00:06: [io  0x0070-0x0077]
[    0.776133] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.776144] pnp 00:07: [io  0x0060]
[    0.776145] pnp 00:07: [io  0x0064]
[    0.776151] pnp 00:07: [irq 1]
[    0.776177] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.776188] pnp 00:08: [irq 12]
[    0.776218] pnp 00:08: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.776472] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.776475] pnp 00:09: [mem 0xfed10000-0xfed13fff]
[    0.776477] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    0.776478] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    0.776480] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    0.776482] pnp 00:09: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.776485] pnp 00:09: [mem 0xfeaff000-0xfeafffff]
[    0.776487] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.776488] pnp 00:09: [mem 0xfed90000-0xfed8ffff disabled]
[    0.776490] pnp 00:09: [mem 0xfed40000-0xfed44fff]
[    0.776492] pnp 00:09: [mem 0xfed45000-0xfed8ffff]
[    0.776494] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.776496] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    0.776579] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.776582] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.776584] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.776587] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.776589] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.776592] system 00:09: [mem 0xfeaff000-0xfeafffff] has been reserved
[    0.776595] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.776597] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.776600] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.776602] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.776605] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.776609] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.777353] pnp 00:0a: [bus ff]
[    0.777394] pnp 00:0a: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.777407] pnp: PnP ACPI: found 11 devices
[    0.777409] ACPI: ACPI bus type pnp unregistered
[    0.784560] PCI: max bus depth: 1 pci_try_num: 2
[    0.784613] pci 0000:00:1c.5: BAR 14: assigned [mem 0xc0000000-0xc00fffff]
[    0.784617] pci 0000:00:1c.5: BAR 14: reassigned [mem 0xc0000000-0xc04fffff]
[    0.784622] pci 0000:00:1c.1: BAR 15: assigned [mem 0xc0500000-0xc06fffff 64bit pref]
[    0.784626] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.784629] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0700000-0xc08fffff]
[    0.784632] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0900000-0xc0afffff 64bit pref]
[    0.784635] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.784638] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.784642] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.784649] pci 0000:00:1c.0:   bridge window [mem 0xc0700000-0xc08fffff]
[    0.784654] pci 0000:00:1c.0:   bridge window [mem 0xc0900000-0xc0afffff 64bit pref]
[    0.784662] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.784666] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.784672] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.784678] pci 0000:00:1c.1:   bridge window [mem 0xc0500000-0xc06fffff 64bit pref]
[    0.784687] pci 0000:04:00.0: BAR 6: assigned [mem 0xf0820000-0xf083ffff pref]
[    0.784690] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.784693] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.784700] pci 0000:00:1c.5:   bridge window [mem 0xc0000000-0xc04fffff]
[    0.784705] pci 0000:00:1c.5:   bridge window [mem 0xf0800000-0xf08fffff 64bit pref]
[    0.784713] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.784750] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.784756] pci 0000:00:1c.0: setting latency timer to 64
[    0.784768] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.784774] pci 0000:00:1c.1: setting latency timer to 64
[    0.784782] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.784787] pci 0000:00:1c.5: setting latency timer to 64
[    0.784796] pci 0000:00:1e.0: setting latency timer to 64
[    0.784801] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.784803] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.784806] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.784808] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.784810] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.784812] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.784814] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xdfffffff]
[    0.784817] pci_bus 0000:00: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.784819] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.784821] pci_bus 0000:02: resource 1 [mem 0xc0700000-0xc08fffff]
[    0.784824] pci_bus 0000:02: resource 2 [mem 0xc0900000-0xc0afffff 64bit pref]
[    0.784827] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.784829] pci_bus 0000:03: resource 1 [mem 0xf0400000-0xf04fffff]
[    0.784831] pci_bus 0000:03: resource 2 [mem 0xc0500000-0xc06fffff 64bit pref]
[    0.784834] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.784836] pci_bus 0000:04: resource 1 [mem 0xc0000000-0xc04fffff]
[    0.784839] pci_bus 0000:04: resource 2 [mem 0xf0800000-0xf08fffff 64bit pref]
[    0.784841] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.784844] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.784846] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.784848] pci_bus 0000:05: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.784851] pci_bus 0000:05: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.784853] pci_bus 0000:05: resource 9 [mem 0x000dc000-0x000dffff]
[    0.784855] pci_bus 0000:05: resource 10 [mem 0xc0000000-0xdfffffff]
[    0.784858] pci_bus 0000:05: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.784901] NET: Registered protocol family 2
[    0.785031] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.785848] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.788767] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.789119] TCP: Hash tables configured (established 524288 bind 65536)
[    0.789121] TCP reno registered
[    0.789136] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.789178] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.789294] NET: Registered protocol family 1
[    0.789312] pci 0000:00:02.0: Boot video device
[    0.789330] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.789367] pci 0000:00:1a.0: PCI INT A disabled
[    0.789400] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.789431] pci 0000:00:1d.0: PCI INT A disabled
[    0.789506] PCI: CLS 64 bytes, default 64
[    0.789508] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.789511] Placing 64MB software IO TLB between ffff8800b727c000 - ffff8800bb27c000
[    0.789513] software IO TLB at phys 0xb727c000 - 0xbb27c000
[    0.789525] Simple Boot Flag at 0x36 set to 0x1
[    0.790045] audit: initializing netlink socket (disabled)
[    0.790062] type=2000 audit(1378789891.620:1): initialized
[    0.814174] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.816286] VFS: Disk quotas dquot_6.5.2
[    0.816337] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.816892] fuse init (API version 7.17)
[    0.816991] msgmni has been set to 7459
[    0.817456] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.817494] io scheduler noop registered
[    0.817496] io scheduler deadline registered
[    0.817530] io scheduler cfq registered (default)
[    0.817817] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.817836] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.817889] intel_idle: MWAIT substates: 0x1120
[    0.817891] intel_idle: v0.4 model 0x25
[    0.817893] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.817994] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.818038] ACPI: AC Adapter [ADP1] (on-line)
[    0.818150] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.818156] ACPI: Power Button [PWRB]
[    0.818194] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.818197] ACPI: Sleep Button [SLPB]
[    0.818237] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.818787] ACPI: Lid Switch [LID0]
[    0.818830] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.818834] ACPI: Power Button [PWRF]
[    0.818894] ACPI: Fan [FAN0] (off)
[    0.818927] ACPI: Fan [FAN1] (off)
[    0.822441] thermal LNXTHERM:00: registered as thermal_zone0
[    0.822444] ACPI: Thermal Zone [TZ00] (27 C)
[    0.822659] thermal LNXTHERM:01: registered as thermal_zone1
[    0.822661] ACPI: Thermal Zone [TZ01] (0 C)
[    0.822682] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.822691] ACPI: Battery Slot [BAT0] (battery present)
[    0.822720] ERST: Table is not found!
[    0.822721] GHES: HEST is not enabled!
[    0.822823] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.836496] ACPI: Battery Slot [BAT0] (battery present)
[    0.930946] Freeing initrd memory: 21024k freed
[    1.068811] Linux agpgart interface v0.103
[    1.068893] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.069064] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.070198] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.070363] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.071832] brd: module loaded
[    1.072607] loop: module loaded
[    1.072743] ahci 0000:00:1f.2: version 3.0
[    1.072767] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.072821] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.072852] ahci: SSS flag set, parallel bus scan disabled
[    1.072889] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.072894] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems apst 
[    1.072900] ahci 0000:00:1f.2: setting latency timer to 64
[    1.080787] scsi0 : ahci
[    1.080902] scsi1 : ahci
[    1.080987] scsi2 : ahci
[    1.081069] scsi3 : ahci
[    1.081124] ata1: SATA max UDMA/133 abar m2048@0xf0705000 port 0xf0705100 irq 40
[    1.081129] ata2: SATA max UDMA/133 abar m2048@0xf0705000 port 0xf0705180 irq 40
[    1.081131] ata3: DUMMY
[    1.081132] ata4: DUMMY
[    1.081487] Fixed MDIO Bus: probed
[    1.081504] tun: Universal TUN/TAP device driver, 1.6
[    1.081506] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.081561] PPP generic driver version 2.4.2
[    1.081659] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.081677] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.081696] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.081700] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.081745] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.081779] ehci_hcd 0000:00:1a.0: debug port 2
[    1.085755] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.085773] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf0706000
[    1.100393] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.100557] hub 1-0:1.0: USB hub found
[    1.100562] hub 1-0:1.0: 3 ports detected
[    1.100632] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.100648] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.100651] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.100702] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.100729] ehci_hcd 0000:00:1d.0: debug port 2
[    1.104712] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.104727] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf0706400
[    1.120384] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.120540] hub 2-0:1.0: USB hub found
[    1.120543] hub 2-0:1.0: 3 ports detected
[    1.120605] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.120618] uhci_hcd: USB Universal Host Controller Interface driver
[    1.120662] usbcore: registered new interface driver libusual
[    1.120697] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.126631] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.126638] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.126763] mousedev: PS/2 mouse device common for all mice
[    1.126990] rtc_cmos 00:06: RTC can wake from S4
[    1.127106] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.127139] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.127212] device-mapper: uevent: version 1.0.3
[    1.127288] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.127390] cpuidle: using governor ladder
[    1.127537] cpuidle: using governor menu
[    1.127539] EFI Variables Facility v0.08 2004-May-17
[    1.127778] TCP cubic registered
[    1.127878] NET: Registered protocol family 10
[    1.128337] NET: Registered protocol family 17
[    1.128341] Registering the dns_resolver key type
[    1.128585] PM: Hibernation image not present or could not be loaded.
[    1.128598] registered taskstats version 1
[    1.132137] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.142605]   Magic number: 13:911:162
[    1.142803] rtc_cmos 00:06: setting system clock to 2013-09-10 05:11:32 UTC (1378789892)
[    1.144384] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.144386] EDD information not available.
[    1.400349] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.402260] ata1.00: ATA-8: ST9250315AS, D003DEM1, max UDMA/133
[    1.402265] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.404475] ata1.00: configured for UDMA/133
[    1.404803] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      D003 PQ: 0 ANSI: 5
[    1.405055] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.405103] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.405317] sd 0:0:0:0: [sda] Write Protect is off
[    1.405322] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.405499] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.412380] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.509632]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.511407] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.545089] hub 1-1:1.0: USB hub found
[    1.545298] hub 1-1:1.0: 6 ports detected
[    1.656206] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.724212] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.726858] ata2.00: ATAPI: HL-DT-STDVD+/-RW GT30N, A101, max UDMA/100
[    1.729886] ata2.00: configured for UDMA/100
[    1.732989] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GT30N    A101 PQ: 0 ANSI: 5
[    1.737025] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.737032] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.737314] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.737515] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.739720] Freeing unused kernel memory: 924k freed
[    1.739889] Write protecting the kernel read-only data: 12288k
[    1.745176] Freeing unused kernel memory: 1592k freed
[    1.749337] Freeing unused kernel memory: 1188k freed
[    1.772026] udevd[104]: starting version 175
[    1.788128] Refined TSC clocksource calibration: 2128.000 MHz.
[    1.788135] Switching to clocksource tsc
[    1.788784] hub 2-1:1.0: USB hub found
[    1.788864] hub 2-1:1.0: 8 ports detected
[    1.799899] [drm] Initialized drm 1.1.0 20060810
[    1.807355] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.807362] i915 0000:00:02.0: setting latency timer to 64
[    1.808540] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.808569] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.808619] r8169 0000:04:00.0: setting latency timer to 64
[    1.808686] r8169 0000:04:00.0: irq 41 for MSI/MSI-X
[    1.809301] r8169 0000:04:00.0: eth0: RTL8102e at 0xffffc9000066c000, b8:ac:6f:55:ea:90, XID 04e00000 IRQ 41
[    1.811125] wmi: Mapper loaded
[    1.860214] usb 1-1.4: new high-speed USB device number 3 using ehci_hcd
[    1.899110] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    1.899116] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.899118] [drm] Driver supports precise vblank timestamp query.
[    1.899168] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.527981] fbcon: inteldrmfb (fb0) is primary device
[    2.528075] Console: switching to colour frame buffer device 170x48
[    2.528110] fb0: inteldrmfb frame buffer device
[    2.528112] drm: registered panic notifier
[    2.528132] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    2.568583] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    2.571239] acpi device:01: registered as cooling_device6
[    2.571452] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.571528] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.571563] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.882269] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   25.054869] Adding 2618556k swap on /dev/sda7.  Priority:-1 extents:1 across:2618556k 
[   25.386316] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   26.060890] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.084775] udevd[519]: starting version 175
[   26.108367] lp: driver loaded but no devices found
[   26.134294] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   26.134748] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.134757] mei 0000:00:16.0: setting latency timer to 64
[   26.134838] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   26.140100] lib80211: common routines for IEEE802.11 drivers
[   26.140105] lib80211_crypt: registered algorithm 'NULL'
[   26.143716] cfg80211: Calling CRDA to update world regulatory domain
[   26.146780] wl: module license 'MIXED/Proprietary' taints kernel.
[   26.146784] Disabling lock debugging due to kernel taint
[   26.161285] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.161382] wl 0000:03:00.0: setting latency timer to 64
[   26.169255] Linux video capture interface: v2.00
[   26.202287] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   26.202293] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202296] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   26.202300] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202303] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   26.202307] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202309] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   26.202313] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202316] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   26.202319] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202322] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   26.202326] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202329] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   26.202333] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202335] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   26.202339] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202342] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   26.202345] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202348] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   26.202352] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202355] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   26.202358] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202362] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   26.202365] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202368] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   26.202372] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202375] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   26.202378] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   26.202381] cfg80211: Disabling freq 5170 MHz
[   26.202384] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   26.202387] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202391] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   26.202394] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202398] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   26.202402] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202405] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[   26.202409] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202412] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   26.202416] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202419] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   26.202423] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202426] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   26.202430] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202433] cfg80211: Disabling freq 5260 MHz
[   26.202435] cfg80211: Disabling freq 5280 MHz
[   26.202437] cfg80211: Disabling freq 5300 MHz
[   26.202439] cfg80211: Disabling freq 5320 MHz
[   26.202441] cfg80211: Disabling freq 5500 MHz
[   26.202443] cfg80211: Disabling freq 5520 MHz
[   26.202445] cfg80211: Disabling freq 5540 MHz
[   26.202447] cfg80211: Disabling freq 5560 MHz
[   26.202449] cfg80211: Disabling freq 5580 MHz
[   26.202451] cfg80211: Disabling freq 5600 MHz
[   26.202453] cfg80211: Disabling freq 5620 MHz
[   26.202456] cfg80211: Disabling freq 5640 MHz
[   26.202458] cfg80211: Disabling freq 5660 MHz
[   26.202460] cfg80211: Disabling freq 5680 MHz
[   26.202462] cfg80211: Disabling freq 5700 MHz
[   26.202465] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   26.202469] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202472] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   26.202476] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202479] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   26.202483] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202486] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   26.202490] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202493] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   26.202496] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   26.202499] cfg80211: Disabling freq 5920 MHz
[   26.202501] cfg80211: Disabling freq 5940 MHz
[   26.202503] cfg80211: Disabling freq 5960 MHz
[   26.202505] cfg80211: Disabling freq 5980 MHz
[   26.202507] cfg80211: Disabling freq 6000 MHz
[   26.202509] cfg80211: Disabling freq 6020 MHz
[   26.202511] cfg80211: Disabling freq 6040 MHz
[   26.202513] cfg80211: Disabling freq 6060 MHz
[   26.202515] cfg80211: Disabling freq 6080 MHz
[   26.209751] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   26.218691] lib80211_crypt: registered algorithm 'TKIP'
[   26.220258] Bluetooth: Core ver 2.16
[   26.220287] NET: Registered protocol family 31
[   26.220290] Bluetooth: HCI device and connection manager initialized
[   26.220294] Bluetooth: HCI socket layer initialized
[   26.220296] Bluetooth: L2CAP socket layer initialized
[   26.220304] Bluetooth: SCO socket layer initialized
[   26.226331] ppdev: user-space parallel port driver
[   26.237859] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.237863] Bluetooth: BNEP filters: protocol multicast
[   26.289773] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   26.289873] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   26.304904] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:6480)
[   26.315928] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   26.332451] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input6
[   26.332543] usbcore: registered new interface driver uvcvideo
[   26.332546] USB Video Class driver (1.1.1)
[   26.388843] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   26.459792] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   26.465816] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   26.484535] Bluetooth: RFCOMM TTY layer initialized
[   26.484543] Bluetooth: RFCOMM socket layer initialized
[   26.484545] Bluetooth: RFCOMM ver 1.11
[   26.490817] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   26.490822] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490826] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   26.490830] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490833] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   26.490837] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490841] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   26.490844] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490847] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   26.490851] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490854] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   26.490857] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490860] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   26.490863] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490866] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   26.490870] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490873] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   26.490876] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490879] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   26.490882] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490884] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   26.490888] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490891] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   26.490894] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.490897] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   26.490901] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.490904] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   26.490908] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.490911] cfg80211: Disabling freq 5170 MHz
[   26.490913] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   26.490917] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490920] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   26.490924] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490927] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   26.490930] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490933] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[   26.490937] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490940] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   26.490944] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490946] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   26.490950] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490953] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   26.490957] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490960] cfg80211: Disabling freq 5260 MHz
[   26.490962] cfg80211: Disabling freq 5280 MHz
[   26.490964] cfg80211: Disabling freq 5300 MHz
[   26.490966] cfg80211: Disabling freq 5320 MHz
[   26.490968] cfg80211: Disabling freq 5500 MHz
[   26.490970] cfg80211: Disabling freq 5520 MHz
[   26.490971] cfg80211: Disabling freq 5540 MHz
[   26.490973] cfg80211: Disabling freq 5560 MHz
[   26.490975] cfg80211: Disabling freq 5580 MHz
[   26.490977] cfg80211: Disabling freq 5600 MHz
[   26.490979] cfg80211: Disabling freq 5620 MHz
[   26.490982] cfg80211: Disabling freq 5640 MHz
[   26.490984] cfg80211: Disabling freq 5660 MHz
[   26.490986] cfg80211: Disabling freq 5680 MHz
[   26.490988] cfg80211: Disabling freq 5700 MHz
[   26.490990] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   26.490994] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.490997] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   26.491001] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.491004] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   26.491008] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.491011] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   26.491015] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.491018] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   26.491021] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.491024] cfg80211: Disabling freq 5920 MHz
[   26.491026] cfg80211: Disabling freq 5940 MHz
[   26.491027] cfg80211: Disabling freq 5960 MHz
[   26.491029] cfg80211: Disabling freq 5980 MHz
[   26.491031] cfg80211: Disabling freq 6000 MHz
[   26.491033] cfg80211: Disabling freq 6020 MHz
[   26.491036] cfg80211: Disabling freq 6040 MHz
[   26.491038] cfg80211: Disabling freq 6060 MHz
[   26.491040] cfg80211: Disabling freq 6080 MHz
[   26.491045] cfg80211: World regulatory domain updated:
[   26.491048] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.491051] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.491055] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.491058] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.491062] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.491065] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.493359] type=1400 audit(1378815117.854:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=637 comm="apparmor_parser"
[   26.493886] type=1400 audit(1378815117.858:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=637 comm="apparmor_parser"
[   26.494185] type=1400 audit(1378815117.858:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=637 comm="apparmor_parser"
[   26.494249] type=1400 audit(1378815117.858:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=689 comm="apparmor_parser"
[   26.495292] type=1400 audit(1378815117.858:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=689 comm="apparmor_parser"
[   26.495337] type=1400 audit(1378815117.858:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=739 comm="apparmor_parser"
[   26.495916] type=1400 audit(1378815117.858:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=739 comm="apparmor_parser"
[   26.496247] type=1400 audit(1378815117.858:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=739 comm="apparmor_parser"
[   26.504764] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   26.504848] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   26.504888] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   26.548116] init: failsafe main process (812) killed by TERM signal
[   26.561355] HDMI status: Codec=3 Pin=4 Presence_Detect=0 ELD_Valid=0
[   26.561464] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   26.561800] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   26.561898] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   26.603908] type=1400 audit(1378815117.966:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=909 comm="apparmor_parser"
[   26.604383] type=1400 audit(1378815117.966:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=908 comm="apparmor_parser"
[   26.892973] r8169 0000:04:00.0: eth0: link down
[   26.894226] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.894674] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.901164] init: gdm main process (997) killed by TERM signal
[   27.098213] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input11
[   27.117493] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12
[   30.016478] init: plymouth-stop pre-start process (1503) terminated with status 1
[   37.806227] r8169 0000:04:00.0: eth0: link down
[   37.806688] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.841851] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[   81.392046] r8169 0000:04:00.0: eth0: link down
[   81.392551] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   81.392621] INFO @wl_cfg80211_scan : system busy : scan for "" canceled
[   81.666392] INFO @wl_cfg80211_scan : system busy : scan for "" canceled
[   82.561376] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[   82.743311] r8169 0000:04:00.0: eth0: link down
[   82.743748] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   93.139380] cfg80211: All devices are disconnected, going to restore regulatory settings
[   93.139391] cfg80211: Restoring regulatory settings
[   93.139398] cfg80211: Calling CRDA to update world regulatory domain
[   93.147216] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   93.147221] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147224] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   93.147227] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147229] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   93.147231] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147233] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   93.147236] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147238] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   93.147241] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147243] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   93.147245] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147247] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   93.147250] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147252] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   93.147255] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147257] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   93.147259] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147261] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   93.147264] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147266] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   93.147269] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147271] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   93.147273] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   93.147275] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   93.147278] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   93.147280] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   93.147283] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   93.147285] cfg80211: Disabling freq 5170 MHz
[   93.147287] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   93.147290] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147292] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   93.147294] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147296] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   93.147299] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147301] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[   93.147304] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147306] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   93.147308] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147310] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   93.147313] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147315] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   93.147318] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147320] cfg80211: Disabling freq 5260 MHz
[   93.147321] cfg80211: Disabling freq 5280 MHz
[   93.147322] cfg80211: Disabling freq 5300 MHz
[   93.147324] cfg80211: Disabling freq 5320 MHz
[   93.147325] cfg80211: Disabling freq 5500 MHz
[   93.147327] cfg80211: Disabling freq 5520 MHz
[   93.147328] cfg80211: Disabling freq 5540 MHz
[   93.147329] cfg80211: Disabling freq 5560 MHz
[   93.147331] cfg80211: Disabling freq 5580 MHz
[   93.147332] cfg80211: Disabling freq 5600 MHz
[   93.147334] cfg80211: Disabling freq 5620 MHz
[   93.147335] cfg80211: Disabling freq 5640 MHz
[   93.147336] cfg80211: Disabling freq 5660 MHz
[   93.147338] cfg80211: Disabling freq 5680 MHz
[   93.147339] cfg80211: Disabling freq 5700 MHz
[   93.147341] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   93.147344] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147346] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   93.147348] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147351] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   93.147353] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147355] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   93.147358] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147360] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   93.147363] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147364] cfg80211: Disabling freq 5920 MHz
[   93.147366] cfg80211: Disabling freq 5940 MHz
[   93.147367] cfg80211: Disabling freq 5960 MHz
[   93.147369] cfg80211: Disabling freq 5980 MHz
[   93.147370] cfg80211: Disabling freq 6000 MHz
[   93.147371] cfg80211: Disabling freq 6020 MHz
[   93.147373] cfg80211: Disabling freq 6040 MHz
[   93.147374] cfg80211: Disabling freq 6060 MHz
[   93.147376] cfg80211: Disabling freq 6080 MHz
[   93.147380] cfg80211: World regulatory domain updated:
[   93.147382] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   93.147384] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147387] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   93.147389] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   93.147391] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.147394] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.517170] cfg80211: All devices are disconnected, going to restore regulatory settings
[  410.517179] cfg80211: Restoring regulatory settings
[  410.517186] cfg80211: Calling CRDA to update world regulatory domain
[  410.523459] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  410.523464] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523467] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  410.523470] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523472] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  410.523475] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523477] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  410.523479] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523481] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  410.523484] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523486] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  410.523489] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523491] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  410.523493] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523495] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  410.523498] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523500] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  410.523503] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523505] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  410.523507] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523509] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  410.523512] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523514] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  410.523517] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  410.523519] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  410.523521] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  410.523524] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  410.523526] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  410.523528] cfg80211: Disabling freq 5170 MHz
[  410.523530] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  410.523533] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523535] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[  410.523538] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523540] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  410.523542] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523544] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[  410.523547] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523549] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  410.523552] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523554] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[  410.523556] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523558] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  410.523561] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523563] cfg80211: Disabling freq 5260 MHz
[  410.523564] cfg80211: Disabling freq 5280 MHz
[  410.523566] cfg80211: Disabling freq 5300 MHz
[  410.523588] cfg80211: Disabling freq 5320 MHz
[  410.523590] cfg80211: Disabling freq 5500 MHz
[  410.523592] cfg80211: Disabling freq 5520 MHz
[  410.523594] cfg80211: Disabling freq 5540 MHz
[  410.523596] cfg80211: Disabling freq 5560 MHz
[  410.523598] cfg80211: Disabling freq 5580 MHz
[  410.523600] cfg80211: Disabling freq 5600 MHz
[  410.523603] cfg80211: Disabling freq 5620 MHz
[  410.523605] cfg80211: Disabling freq 5640 MHz
[  410.523607] cfg80211: Disabling freq 5660 MHz
[  410.523609] cfg80211: Disabling freq 5680 MHz
[  410.523611] cfg80211: Disabling freq 5700 MHz
[  410.523614] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[  410.523617] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523620] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[  410.523624] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523627] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[  410.523630] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523633] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[  410.523636] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523639] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[  410.523643] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523645] cfg80211: Disabling freq 5920 MHz
[  410.523647] cfg80211: Disabling freq 5940 MHz
[  410.523649] cfg80211: Disabling freq 5960 MHz
[  410.523651] cfg80211: Disabling freq 5980 MHz
[  410.523653] cfg80211: Disabling freq 6000 MHz
[  410.523655] cfg80211: Disabling freq 6020 MHz
[  410.523657] cfg80211: Disabling freq 6040 MHz
[  410.523659] cfg80211: Disabling freq 6060 MHz
[  410.523661] cfg80211: Disabling freq 6080 MHz
[  410.523668] cfg80211: World regulatory domain updated:
[  410.523670] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  410.523673] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523677] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  410.523680] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  410.523683] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.523686] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  410.748299] r8169 0000:04:00.0: eth0: link down
[  410.749192] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  412.243686] r8169 0000:04:00.0: eth0: link down
[  412.244605] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  496.393521] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  496.393530] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  496.393544] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  496.393550] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  496.393562] ERROR @wl_dev_intvar_get : error (-1)
[  496.393567] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  941.485610] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  941.485620] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  941.485634] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  941.485640] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  941.485652] ERROR @wl_dev_intvar_get : error (-1)
[  941.485657] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  967.500999] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  967.501009] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  967.501023] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  967.501029] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  967.501041] ERROR @wl_dev_intvar_get : error (-1)
[  967.501046] ERROR @wl_cfg80211_get_tx_power : error (-1)

```

: iwlist scan gives
```
eth1      Scan completed :
          Cell 01 - Address: 00:13:10:72:B5:C8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Malkiewich"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 811776ms ago
                    IE: Unknown: 000A4D616C6B696577696368
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010200

```

: lsb_release -d gives
```
Description:    Ubuntu 12.04.3 LTS

```

: uname -mr gives
```
3.2.0-52-generic x86_64

```

: restarting the network gives
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.

```

---

### Post by chili555 on 2013-09-10
Here is a fix that often works. With a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer
```Detach the ethernet, reboot and let us have your report.

---

### Post by cmalk on 2013-09-12
I did as instructed, unfortunately it was time for me to fly back home and I didn't have time to check whether it worked. I'll be back in December, if the problem is still there I'll add it to this thread.

Thank you so much for your help!
-Cary

---

### Post by chili555 on 2013-09-13
We'll look forward to your report.

---

### Post by cmalk on 2013-12-19
Came back and connected to the network right away with no problems! Thank you so much for your help chili555.

-Cary

---

### Post by chili555 on 2013-12-19
Awesome! Glad to hear it is fixed. You will have helped quite a few searchers, too. Have fun!

---

