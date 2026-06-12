---
title: "Atmel firmware &amp; linux generic firmware/ lubuntu 13.10/hp slimline s7520n"
date: 2014-01-16
forum: Networking &amp; Wireless
---

### Post by johnnytwotimes on 2014-01-16
I have a gemtek wubr 177G adapter that uses Linux Generic firmware and a belkin wireless g usb 11mbs adapter that uses Atmel Firmware. These packages conflict eachother because I believe Atmel firmware is included in the linux generic firmware. However I can't seem to get my Belkin adapter to start with just the Linux generic. SO, I uninstalled linux generic, confirmed that the adapter works with the atmel firmware install only, and it even runs along side the linux if it's already active on my ram cache. When I restart the Gemtek adapter is gone. Is there a way I can get them to both run at the same time without conflicting? 

also I get a shutdown error that says rt2x00usb vendor not established at shutdown. this could be because I failed at installing the packet injection driver rt73. I wound up just quitting and unblacklisting the orginal drivers. For Dmesg im not sure if those are all errors just let me know if they are or not.

LSUSB command
```
yanni@xxxxxx:~$ lsusb
Bus 001 Device 006: ID 15a9:0004 Gemtek WUBR-177G [Ralink RT2571W]
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0d5c:a002 SMC Networks, Inc. SMC2662W v2 / SMC2662W-AR / Belkin F5D6050 [Atmel at76c503a]
Bus 003 Device 002: ID 05a9:8519 OmniVision Technologies, Inc. OV519 Webcam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c513 Logitech, Inc. MX3000 Cordless Desktop Receiver
Bus 002 Device 002: ID 10f5:0231 Turtle Beach 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
yanni@xxxxxx:~$ 


```
LSMOD 
```
yanni@xxxxxx:~$ lsmod
Module                  Size  Used by
at76c50x_usb           39504  0 
zram                   18070  1 
deflate                12545  0 
zlib_deflate           26445  1 deflate
ctr                    12905  0 
twofish_generic        16579  0 
twofish_i586           12787  0 
twofish_common         20985  2 twofish_generic,twofish_i586
camellia_generic       29212  0 
serpent_sse2_i586      33768  0 
xts                    12749  1 serpent_sse2_i586
serpent_generic        29615  1 serpent_sse2_i586
lrw                    13057  1 serpent_sse2_i586
gf128mul               14503  2 lrw,xts
glue_helper            13734  1 serpent_sse2_i586
ablk_helper            13357  1 serpent_sse2_i586
cryptd                 15578  1 ablk_helper
blowfish_generic       12474  0 
blowfish_common        16667  1 blowfish_generic
cast5_generic          21237  0 
cast_common            12839  1 cast5_generic
des_generic            21163  0 
cmac                   12692  0 
xcbc                   12711  0 
rmd160                 16664  0 
crypto_null            12720  0 
af_key                 31220  0 
xfrm_algo              14999  1 af_key
arc4                   12536  2 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
bluetooth             323656  10 bnep,rfcomm
rt73usb                26890  0 
rt2x00usb              20041  1 rt73usb
rt2x00lib              48933  2 rt73usb,rt2x00usb
mac80211              517444  3 rt2x00lib,rt2x00usb,at76c50x_usb
cfg80211              401762  2 mac80211,rt2x00lib
gspca_ov519            47970  0 
binfmt_misc            13140  1 
gspca_main             27772  1 gspca_ov519
videodev              107508  2 gspca_main,gspca_ov519
snd_usb_audio         119227  0 
snd_usbmidi_lib        24326  1 snd_usb_audio
joydev                 17097  0 
snd_hwdep              13272  1 snd_usb_audio
snd_atiixp             19264  4 
snd_ac97_codec        105668  1 snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                89488  4 snd_usb_audio,snd_ac97_codec,snd_atiixp
snd_page_alloc         14230  2 snd_pcm,snd_atiixp
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
psmouse                90642  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq
radeon               1307313  2 
serio_raw              13189  0 
snd                    60790  17 snd_usb_audio,snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_seq_device,snd_atiixp,snd_seq_midi
ttm                    75982  1 radeon
k8temp                 12842  0 
drm_kms_helper         46867  1 radeon
soundcore              12600  1 snd
drm                   242400  4 ttm,drm_kms_helper,radeon
i2c_piix4              17682  0 
i2c_algo_bit           13197  1 radeon
ati_agp                13177  0 
shpchp                 32129  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_logitech           22116  0 
ff_memless             13325  1 hid_logitech
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  3 hid_generic,hid_logitech,usbhid
usb_storage            48294  0 
pata_acpi              12886  0 
firewire_ohci          35463  0 
8139too                32530  0 
firewire_core          57656  1 firewire_ohci
8139cp                 27130  0 
mii                    13654  2 8139cp,8139too
crc_itu_t              12627  2 rt73usb,firewire_core
pata_atiixp            13058  0 
sata_sil               13256  3 

```

DMESG
```

yanni@xxxxxx:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-15-generic (buildd@tipua) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 (Ubuntu 3.11.0-15.23-generic 3.11.10)
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
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000005beeffff] usable
[    0.000000] BIOS-e820: [mem 0x000000005bef0000-0x000000005bef2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000005bef3000-0x000000005befffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffff0000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: HP Pavilion 061 EX259AA-ABA s7520n/Opal  , BIOS  3.04 03/14/2006
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x5bef0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-CFFFF uncachable
[    0.000000]   D0000-D7FFF write-back
[    0.000000]   D8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 0040000000 mask FFF0000000 write-back
[    0.000000]   2 base 0050000000 mask FFF8000000 write-back
[    0.000000]   3 base 0058000000 mask FFFC000000 write-back
[    0.000000]   4 base 005BF00000 mask FFFFF00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1GB, range: 256MB, type WB
[    0.000000] reg 2, base: 1280MB, range: 128MB, type WB
[    0.000000] reg 3, base: 1408MB, range: 64MB, type WB
[    0.000000] reg 4, base: 1471MB, range: 1MB, type UC
[    0.000000] total RAM covered: 1471M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1GB, range: 512MB, type WB
[    0.000000] reg 2, base: 1471MB, range: 1MB, type UC
[    0.000000] reg 3, base: 1472MB, range: 64MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000f5980-0x000f598f] mapped at [c00f5980]
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
[    0.000000] RAMDISK: [mem 0x365e2000-0x372e8fff]
[    0.000000] ACPI: RSDP 000f7590 00014 (v00 HP-CPC)
[    0.000000] ACPI: RSDT 5bef3040 00030 (v01 HP-CPC AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 5bef30c0 00074 (v01 HP-CPC AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 5bef3180 0497C (v01 HP-CPC AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 5bef0000 00040
[    0.000000] ACPI: MCFG 5bef7c00 0003C (v01 HP-CPC AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 5bef7b40 0005A (v01 HP-CPC AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 578MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b4a000, 0x01b4afff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x5beeffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x5beeffff]
[    0.000000] On node 0 totalpages: 376462
[    0.000000] free_area_init_node: node 0, pgdat c1958bc0, node_mem_map f5a62020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1158 pages used for memmap
[    0.000000]   HighMem zone: 148210 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x12
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] e820: [mem 0x5bf00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7be7000 s36288 r0 d21056 u57344
[    0.000000] pcpu-alloc: s36288 r0 d21056 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 374678
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=e22855a9-849a-4b5e-b082-fe6fe8827329 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3012472 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0005bef0)
[    0.000000] Memory: 1465260K/1505848K available (6358K kernel code, 611K rwdata, 2692K rodata, 880K init, 908K bss, 40588K reserved, 592840K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1972000 - 0xc1a4e000   ( 880 kB)
[    0.000000]       .data : 0xc1635ee4 - 0xc1971f80   (3312 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1635ee4   (6359 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=1.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f7406000 soft=f7408000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1790.785 MHz processor
[    0.008004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3581.57 BogoMIPS (lpj=7163140)
[    0.008010] pid_max: default: 32768 minimum: 301
[    0.008073] Security Framework initialized
[    0.008102] AppArmor: AppArmor initialized
[    0.008104] Yama: becoming mindful.
[    0.008191] Mount-cache hash table entries: 512
[    0.012084] Initializing cgroup subsys memory
[    0.012110] Initializing cgroup subsys devices
[    0.012113] Initializing cgroup subsys freezer
[    0.012116] Initializing cgroup subsys blkio
[    0.012119] Initializing cgroup subsys perf_event
[    0.012124] Initializing cgroup subsys hugetlb
[    0.012164] mce: CPU supports 5 MCE banks
[    0.012192] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.012192] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.012192] tlb_flushall_shift: 4
[    0.022187] Freeing SMP alternatives memory: 28K (c1a4e000 - c1a55000)
[    0.025033] ACPI: Core revision 20130517
[    0.029159] ACPI: All ACPI Tables successfully acquired
[    0.032050] ftrace: allocating 27182 entries in 54 pages
[    0.044175] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044627] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.084466] smpboot: CPU0: AMD Turion(tm) 64 Mobile Technology ML-34 (fam: 0f, model: 24, stepping: 02)
[    0.088000] Performance Events: AMD PMU driver.
[    0.088000] ... version:                0
[    0.088000] ... bit width:              48
[    0.088000] ... generic registers:      4
[    0.088000] ... value mask:             0000ffffffffffff
[    0.088000] ... max period:             00007fffffffffff
[    0.088000] ... fixed-purpose events:   0
[    0.088000] ... event mask:             000000000000000f
[    0.088000] Brought up 1 CPUs
[    0.088000] smpboot: Total of 1 processors activated (3581.57 BogoMIPS)
[    0.088000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.088000] devtmpfs: initialized
[    0.088000] EVM: security.selinux
[    0.088000] EVM: security.SMACK64
[    0.088000] EVM: security.capability
[    0.088000] PM: Registering ACPI NVS region [mem 0x5bef0000-0x5bef2fff] (12288 bytes)
[    0.089374] regulator-dummy: no parameters
[    0.089418] RTC time:  9:08:22, date: 01/16/14
[    0.089472] NET: Registered protocol family 16
[    0.089672] EISA bus registered
[    0.089678] node 0 link 0: io port [d000, ffff]
[    0.089687] TOM: 0000000060000000 aka 1536M
[    0.089690] node 0 link 0: mmio [a0000, bffff]
[    0.089694] node 0 link 0: mmio [f0000000, f7ffffff]
[    0.089697] node 0 link 0: mmio [60000000, dfffffff]
[    0.089701] node 0 link 0: mmio [f8000000, fe02ffff]
[    0.089704] node 0 link 0: mmio [e0000000, e02fffff]
[    0.089708] bus: [bus 00-02] on node 0 link 0
[    0.089711] bus: 00 [io  0x0000-0xffff]
[    0.089713] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.089716] bus: 00 [mem 0xe0300000-0xfcffffffff]
[    0.089718] bus: 00 [mem 0x60000000-0xe02fffff]
[    0.089793] ACPI: bus type PCI registered
[    0.089797] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.089877] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.089881] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.089883] PCI: Using MMCONFIG for extended config space
[    0.089885] PCI: Using configuration type 1 for base access
[    0.091433] bio: create slab <bio-0> at 0
[    0.091629] ACPI: Added _OSI(Module Device)
[    0.091632] ACPI: Added _OSI(Processor Device)
[    0.091634] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.091637] ACPI: Added _OSI(Processor Aggregator Device)
[    0.092489] ACPI: EC: Look up EC in DSDT
[    0.093439] ACPI: Actual Package length (7) is larger than NumElements field (3), truncated
[    0.095993] ACPI: Interpreter enabled
[    0.096025] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.096043] ACPI: (supports S0 S1 S3 S4 S5)
[    0.096045] ACPI: Using IOAPIC for interrupt routing
[    0.096109] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.096203] ACPI: No dock devices found.
[    0.096777] ACPI BIOS Error (bug): \_SB_.PCI0.USB0._PSW: Object (Integer) must be a control method with 1 arguments (20130517/nsarguments-147)
[    0.096883] ACPI BIOS Error (bug): \_SB_.PCI0.USB1._PSW: Object (Integer) must be a control method with 1 arguments (20130517/nsarguments-147)
[    0.096980] ACPI BIOS Error (bug): \_SB_.PCI0.USB2._PSW: Object (Integer) must be a control method with 1 arguments (20130517/nsarguments-147)
[    0.100991] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.101000] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.101004] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.101121] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.101125] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.101128] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.101132] acpi PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.101136] acpi PNP0A03:00: host bridge window [mem 0x60000000-0xfebfffff] (ignored)
[    0.101139] PCI: root bus 00: hardware-probed resources
[    0.101264] PCI host bridge to bus 0000:00
[    0.101269] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.101272] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.101276] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.101279] pci_bus 0000:00: root bus resource [mem 0xe0300000-0xfcffffffff]
[    0.101282] pci_bus 0000:00: root bus resource [mem 0x60000000-0xe02fffff]
[    0.101294] pci 0000:00:00.0: [1002:5950] type 00 class 0x060000
[    0.101394] pci 0000:00:01.0: [1002:5a3f] type 01 class 0x060400
[    0.101549] pci 0000:00:12.0: [1002:4379] type 00 class 0x01018f
[    0.101580] pci 0000:00:12.0: reg 0x10: [io  0xff00-0xff07]
[    0.101594] pci 0000:00:12.0: reg 0x14: [io  0xfe00-0xfe03]
[    0.101609] pci 0000:00:12.0: reg 0x18: [io  0xfd00-0xfd07]
[    0.101624] pci 0000:00:12.0: reg 0x1c: [io  0xfc00-0xfc03]
[    0.101638] pci 0000:00:12.0: reg 0x20: [io  0xfb00-0xfb0f]
[    0.101654] pci 0000:00:12.0: reg 0x24: [mem 0xfe02f000-0xfe02f1ff]
[    0.101669] pci 0000:00:12.0: reg 0x30: [mem 0xfdf80000-0xfdffffff pref]
[    0.101726] pci 0000:00:12.0: supports D1 D2
[    0.101819] pci 0000:00:13.0: [1002:4374] type 00 class 0x0c0310
[    0.101847] pci 0000:00:13.0: reg 0x10: [mem 0xfe02e000-0xfe02efff]
[    0.102011] ACPI BIOS Error (bug): \_SB_.PCI0.USB0._PSW: Object (Integer) must be a control method with 1 arguments (20130517/nsarguments-147)
[    0.102018] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.102072] pci 0000:00:13.1: [1002:4375] type 00 class 0x0c0310
[    0.102098] pci 0000:00:13.1: reg 0x10: [mem 0xfe02d000-0xfe02dfff]
[    0.102259] ACPI BIOS Error (bug): \_SB_.PCI0.USB1._PSW: Object (Integer) must be a control method with 1 arguments (20130517/nsarguments-147)
[    0.102266] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.102329] pci 0000:00:13.2: [1002:4373] type 00 class 0x0c0320
[    0.102360] pci 0000:00:13.2: reg 0x10: [mem 0xfe02c000-0xfe02cfff]
[    0.102484] pci 0000:00:13.2: supports D1 D2
[    0.102487] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.102547] ACPI BIOS Error (bug): \_SB_.PCI0.USB2._PSW: Object (Integer) must be a control method with 1 arguments (20130517/nsarguments-147)
[    0.102554] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.102613] pci 0000:00:14.0: [1002:4372] type 00 class 0x0c0500
[    0.102636] pci 0000:00:14.0: reg 0x10: [io  0x0b00-0x0b0f]
[    0.102651] pci 0000:00:14.0: reg 0x14: [mem 0xfe02b000-0xfe02b3ff]
[    0.102715] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.102850] pci 0000:00:14.1: [1002:4376] type 00 class 0x010182
[    0.102877] pci 0000:00:14.1: reg 0x10: [io  0x0000-0x0007]
[    0.102892] pci 0000:00:14.1: reg 0x14: [io  0x0000-0x0003]
[    0.102907] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.102924] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.102938] pci 0000:00:14.1: reg 0x20: [io  0xf900-0xf90f]
[    0.103087] pci 0000:00:14.3: [1002:4377] type 00 class 0x060100
[    0.103264] pci 0000:00:14.4: [1002:4371] type 01 class 0x060401
[    0.103361] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.103412] pci 0000:00:14.5: [1002:4370] type 00 class 0x040100
[    0.103438] pci 0000:00:14.5: reg 0x10: [mem 0xfe02a000-0xfe02a0ff]
[    0.103602] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.103651] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.103743] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.103827] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.103915] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.104058] pci 0000:01:05.0: [1002:5954] type 00 class 0x030000
[    0.104069] pci 0000:01:05.0: reg 0x10: [mem 0xf0000000-0xf7ffffff pref]
[    0.104076] pci 0000:01:05.0: reg 0x14: [io  0xee00-0xeeff]
[    0.104083] pci 0000:01:05.0: reg 0x18: [mem 0xfddf0000-0xfddfffff]
[    0.104102] pci 0000:01:05.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.104117] pci 0000:01:05.0: supports D1 D2
[    0.104164] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.104172] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.104176] pci 0000:00:01.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.104182] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.104240] pci 0000:02:01.0: [11c1:5811] type 00 class 0x0c0010
[    0.104270] pci 0000:02:01.0: reg 0x10: [mem 0xfdcff000-0xfdcfffff]
[    0.104406] pci 0000:02:01.0: supports D1 D2
[    0.104410] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot
[    0.104484] pci 0000:02:03.0: [10ec:8139] type 00 class 0x020000
[    0.104514] pci 0000:02:03.0: reg 0x10: [io  0xde00-0xdeff]
[    0.104532] pci 0000:02:03.0: reg 0x14: [mem 0xfdcfe000-0xfdcfe0ff]
[    0.104653] pci 0000:02:03.0: supports D1 D2
[    0.104656] pci 0000:02:03.0: PME# supported from D1 D2 D3hot D3cold
[    0.104766] pci 0000:00:14.4: PCI bridge to [bus 02] (subtractive decode)
[    0.104776] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
[    0.104783] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.104790] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.104794] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.104797] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.104801] pci 0000:00:14.4:   bridge window [mem 0xe0300000-0xfcffffffff] (subtractive decode)
[    0.104805] pci 0000:00:14.4:   bridge window [mem 0x60000000-0xe02fffff] (subtractive decode)
[    0.104821] pci_bus 0000:00: on NUMA node 0
[    0.104924] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.104999] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.105073] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.105148] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.105221] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.105295] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11)
[    0.105368] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11)
[    0.105441] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.106140] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.106149] ACPI: \_SB_.PCI0: notify handler is installed
[    0.106185] Found 1 acpi root devices
[    0.106332] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.106335] vgaarb: loaded
[    0.106337] vgaarb: bridge control possible 0000:01:05.0
[    0.106667] SCSI subsystem initialized
[    0.106671] ACPI: bus type ATA registered
[    0.106733] libata version 3.00 loaded.
[    0.106760] ACPI: bus type USB registered
[    0.106793] usbcore: registered new interface driver usbfs
[    0.106807] usbcore: registered new interface driver hub
[    0.106837] usbcore: registered new device driver usb
[    0.106998] PCI: Using ACPI for IRQ routing
[    0.119484] PCI: pci_cache_line_size set to 64 bytes
[    0.119542] Expanded resource reserved due to conflict with PCI Bus #00
[    0.119544] Expanded resource reserved due to conflict with PCI Bus #00
[    0.119548] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.119551] e820: reserve RAM buffer [mem 0x5bef0000-0x5bffffff]
[    0.119699] NetLabel: Initializing
[    0.119702] NetLabel:  domain hash size = 128
[    0.119703] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.119721] NetLabel:  unlabeled traffic allowed by default
[    0.119852] Switched to clocksource refined-jiffies
[    0.129140] AppArmor: AppArmor Filesystem Enabled
[    0.129198] pnp: PnP ACPI init
[    0.129221] ACPI: bus type PNP registered
[    0.129712] pnp 00:00: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.129756] system 00:00: [io  0x0228-0x022f] has been reserved
[    0.129760] system 00:00: [io  0x040b] has been reserved
[    0.129763] system 00:00: [io  0x04d6] has been reserved
[    0.129767] system 00:00: [io  0x0c00-0x0c01] has been reserved
[    0.129771] system 00:00: [io  0x0c14] has been reserved
[    0.129775] system 00:00: [io  0x0c50-0x0c52] has been reserved
[    0.129779] system 00:00: [io  0x0c6c-0x0c6d] has been reserved
[    0.129783] system 00:00: [io  0x0c6f] has been reserved
[    0.129786] system 00:00: [io  0x0cd4-0x0cdf] has been reserved
[    0.129791] system 00:00: [io  0x4000-0x40fe] could not be reserved
[    0.129795] system 00:00: [io  0x4210-0x4217] has been reserved
[    0.129800] system 00:00: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.129808] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.129956] pnp 00:01: [dma 4]
[    0.129985] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.130042] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.130077] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.130116] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.130219] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.130223] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.130227] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.130612] system 00:06: [mem 0xe0000000-0xefffffff] could not be reserved
[    0.130617] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.130874] system 00:07: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.130878] system 00:07: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.130882] system 00:07: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.130886] system 00:07: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.130890] system 00:07: [mem 0x5bf00000-0x5bffffff] could not be reserved
[    0.130894] system 00:07: [mem 0x5bef0000-0x5befffff] could not be reserved
[    0.130898] system 00:07: [mem 0xffff0000-0xffffffff] has been reserved
[    0.130902] system 00:07: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.130906] system 00:07: [mem 0x00100000-0x5beeffff] could not be reserved
[    0.130909] system 00:07: [mem 0x5c000000-0x5fffffff] has been reserved
[    0.130914] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.130918] system 00:07: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.130922] system 00:07: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.130926] system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.130939] pnp: PnP ACPI: found 8 devices
[    0.130941] ACPI: bus type PNP unregistered
[    0.130945] PnPBIOS: Disabled by ACPI PNP
[    0.167613] Switched to clocksource acpi_pm
[    0.167646] pci 0000:01:05.0: BAR 6: assigned [mem 0xfdd00000-0xfdd1ffff pref]
[    0.167653] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.167657] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.167661] pci 0000:00:01.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.167667] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.167672] pci 0000:00:14.4: PCI bridge to [bus 02]
[    0.167677] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
[    0.167685] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.167691] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.167715] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.167719] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.167722] pci_bus 0000:00: resource 6 [mem 0xe0300000-0xfcffffffff]
[    0.167725] pci_bus 0000:00: resource 7 [mem 0x60000000-0xe02fffff]
[    0.167729] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.167732] pci_bus 0000:01: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.167736] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.167739] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.167743] pci_bus 0000:02: resource 1 [mem 0xfdc00000-0xfdcfffff]
[    0.167746] pci_bus 0000:02: resource 2 [mem 0xfde00000-0xfdefffff pref]
[    0.167749] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.167752] pci_bus 0000:02: resource 5 [mem 0x000a0000-0x000bffff]
[    0.167756] pci_bus 0000:02: resource 6 [mem 0xe0300000-0xfcffffffff]
[    0.167759] pci_bus 0000:02: resource 7 [mem 0x60000000-0xe02fffff]
[    0.167803] NET: Registered protocol family 2
[    0.167987] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.167987] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.167987] TCP: Hash tables configured (established 8192 bind 8192)
[    0.167987] TCP: reno registered
[    0.167987] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.167987] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.167987] NET: Registered protocol family 1
[    0.167987] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.167987] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.288285] pci 0000:01:05.0: Boot video device
[    0.288297] PCI: CLS 32 bytes, default 64
[    0.288353] Trying to unpack rootfs image as initramfs...
[    0.714588] Freeing initrd memory: 13340K (f65e2000 - f72e9000)
[    0.714816] Scanning for low memory corruption every 60 seconds
[    0.715162] Initialise module verification
[    0.715237] audit: initializing netlink socket (disabled)
[    0.715257] type=2000 audit(1389863302.711:1): initialized
[    0.746351] bounce pool size: 64 pages
[    0.746366] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.748081] zbud: loaded
[    0.748152] VFS: Disk quotas dquot_6.5.2
[    0.748220] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.748881] fuse init (API version 7.22)
[    0.748988] msgmni has been set to 1730
[    0.749396] Key type asymmetric registered
[    0.749398] Asymmetric key parser 'x509' registered
[    0.749443] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.749476] io scheduler noop registered
[    0.749478] io scheduler deadline registered (default)
[    0.749514] io scheduler cfq registered
[    0.749670] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.749695] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.749881] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.749890] ACPI: Power Button [PWRB]
[    0.749947] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.749950] ACPI: Power Button [PWRF]
[    0.750002] ACPI: Fan [FAN] (on)
[    0.751866] thermal LNXTHERM:00: registered as thermal_zone0
[    0.751869] ACPI: Thermal Zone [THRM] (40 C)
[    0.751925] GHES: HEST is not enabled!
[    0.752038] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.753699] Linux agpgart interface v0.103
[    0.754286] isapnp: Scanning for PnP cards...
[    0.804878] brd: module loaded
[    0.805805] loop: module loaded
[    0.806414] libphy: Fixed MDIO Bus: probed
[    0.806571] tun: Universal TUN/TAP device driver, 1.6
[    0.806573] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.806620] PPP generic driver version 2.4.2
[    0.806684] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.806686] ehci-pci: EHCI PCI platform driver
[    0.806854] ehci-pci 0000:00:13.2: EHCI Host Controller
[    0.806864] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.806954] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe02c000
[    0.850607] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.850673] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.850677] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.850680] usb usb1: Product: EHCI Host Controller
[    0.850683] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    0.850687] usb usb1: SerialNumber: 0000:00:13.2
[    0.850812] hub 1-0:1.0: USB hub found
[    0.850820] hub 1-0:1.0: 8 ports detected
[    0.851016] ehci-platform: EHCI generic platform driver
[    0.851027] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.851029] ohci-pci: OHCI PCI platform driver
[    0.851124] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    0.851131] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.851152] ohci-pci 0000:00:13.0: irq 19, io mem 0xfe02e000
[    0.942438] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.942442] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.942445] usb usb2: Product: OHCI PCI host controller
[    0.942448] usb usb2: Manufacturer: Linux 3.11.0-15-generic ohci_hcd
[    0.942452] usb usb2: SerialNumber: 0000:00:13.0
[    0.986238] hub 2-0:1.0: USB hub found
[    0.986247] hub 2-0:1.0: 4 ports detected
[    0.986449] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    0.986460] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.986479] ohci-pci 0000:00:13.1: irq 19, io mem 0xfe02d000
[    1.077325] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.077328] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.077332] usb usb3: Product: OHCI PCI host controller
[    1.077335] usb usb3: Manufacturer: Linux 3.11.0-15-generic ohci_hcd
[    1.077338] usb usb3: SerialNumber: 0000:00:13.1
[    1.121061] isapnp: No Plug & Play device found
[    1.121170] hub 3-0:1.0: USB hub found
[    1.121178] hub 3-0:1.0: 4 ports detected
[    1.121296] ohci-platform: OHCI generic platform driver
[    1.121306] uhci_hcd: USB Universal Host Controller Interface driver
[    1.121396] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.124336] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.124342] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.124474] mousedev: PS/2 mouse device common for all mice
[    1.124622] rtc_cmos 00:02: RTC can wake from S4
[    1.124782] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.124815] rtc_cmos 00:02: alarms up to one month, 242 bytes nvram
[    1.124902] device-mapper: uevent: version 1.0.3
[    1.124972] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    1.125001] platform eisa.0: Probing EISA bus 0
[    1.125042] platform eisa.0: EISA: Detected 0 cards
[    1.125050] cpufreq-nforce2: No nForce2 chipset.
[    1.125055] cpuidle: using governor ladder
[    1.125058] cpuidle: using governor menu
[    1.125070] ledtrig-cpu: registered to indicate activity on CPUs
[    1.125202] TCP: cubic registered
[    1.125337] NET: Registered protocol family 10
[    1.125588] NET: Registered protocol family 17
[    1.125606] Key type dns_resolver registered
[    1.125769] Using IPI No-Shortcut mode
[    1.125880] PM: Hibernation image not present or could not be loaded.
[    1.125885] Loading module verification certificates
[    1.130741] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 20cb30850ee856675c288816dd8cff0153e91a4b'
[    1.130758] registered taskstats version 1
[    1.133916] Key type trusted registered
[    1.136408] Key type encrypted registered
[    1.138864] AppArmor: AppArmor sha1 policy hashing enabled
[    1.139145]   Magic number: 14:188:121
[    1.139292] rtc_cmos 00:02: setting system clock to 2014-01-16 09:08:23 UTC (1389863303)
[    1.139460] powernow-k8: fid 0xa (1800 MHz), vid 0x4
[    1.139463] powernow-k8: fid 0x8 (1600 MHz), vid 0x6
[    1.139465] powernow-k8: fid 0x0 (800 MHz), vid 0x16
[    1.139495] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-34 (1 cpu cores) (version 2.20.00)
[    1.139501] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.139503] EDD information not available.
[    1.140452] Freeing unused kernel memory: 880K (c1972000 - c1a4e000)
[    1.140493] Write protecting the kernel text: 6360k
[    1.140579] Write protecting the kernel read-only data: 2700k
[    1.140581] NX-protecting the kernel data: 5928k
[    1.160250] systemd-udevd[88]: starting version 204
[    1.209263] sata_sil 0000:00:12.0: version 2.4
[    1.212520] scsi0 : sata_sil
[    1.220810] scsi1 : sata_sil
[    1.220938] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 22
[    1.220942] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 22
[    1.232161] scsi2 : pata_atiixp
[    1.237805] scsi3 : pata_atiixp
[    1.238041] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    1.238045] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    1.250098] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.250121] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.308895] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.310286] 8139too 0000:02:03.0 eth0: RealTek RTL8139 at 0x0001de00, 00:17:31:a6:94:f4, IRQ 21
[    1.316116] firewire_ohci 0000:02:01.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x80
[    1.540067] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.548340] ata1.00: ATA-8: Hitachi HTS547550A9E384, JE3OA50A, max UDMA/100
[    1.548345] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.564319] ata1.00: configured for UDMA/100
[    1.564480] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54755 JE3O PQ: 0 ANSI: 5
[    1.564884] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.564888] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.564962] sd 0:0:0:0: [sda] Write Protect is off
[    1.564967] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.564999] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.565479] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.596482]  sda: sda1
[    1.596817] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.712033] tsc: Refined TSC clocksource calibration: 1790.825 MHz
[    1.816098] firewire_core 0000:02:01.0: created device fw0: GUID 0011d80000b1114b, S400
[    1.884067] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.892318] ata2.00: ATA-7: ST3200827AS, 3.AHH, max UDMA/100
[    1.892323] ata2.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.908318] ata2.00: configured for UDMA/100
[    1.908419] scsi 1:0:0:0: Direct-Access     ATA      ST3200827AS      3.AH PQ: 0 ANSI: 5
[    1.908583] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.908666] sd 1:0:0:0: [sdb] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.908736] sd 1:0:0:0: [sdb] Write Protect is off
[    1.908740] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.908772] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.946408]  sdb: sdb1 sdb2 < sdb5 >
[    1.946883] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.012038] usb 1-5: new high-speed USB device number 5 using ehci-pci
[    2.146172] usb 1-5: New USB device found, idVendor=058f, idProduct=6362
[    2.146178] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.146181] usb 1-5: Product: Mass Storage Device
[    2.146184] usb 1-5: Manufacturer: Generic
[    2.146187] usb 1-5: SerialNumber: 058F312D81B1
[    2.256036] usb 1-7: new high-speed USB device number 6 using ehci-pci
[    2.582617] usb 1-7: New USB device found, idVendor=15a9, idProduct=0004
[    2.582622] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.582627] usb 1-7: Product: USB Wireless 802.11b/g adaptor
[    2.582630] usb 1-7: Manufacturer: Gemtek
[    2.596568] usb-storage 1-5:1.0: USB Mass Storage device detected
[    2.596663] scsi4 : usb-storage 1-5:1.0
[    2.597001] usbcore: registered new interface driver usb-storage
[    2.624934] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[    2.624940] EXT4-fs (sdb1): write access will be enabled during recovery
[    2.712077] Switched to clocksource tsc
[    2.884027] usb 2-1: new full-speed USB device number 2 using ohci-pci
[    3.098478] usb 2-1: New USB device found, idVendor=10f5, idProduct=0231
[    3.098481] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.098485] usb 2-1: Product: Turtle Beach P11 Headset
[    3.098488] usb 2-1: Manufacturer: Generic
[    3.098491] usb 2-1: SerialNumber: 0000000001
[    3.113467] hidraw: raw HID events driver (C) Jiri Kosina
[    3.126715] usbcore: registered new interface driver usbhid
[    3.126718] usbhid: USB HID core driver
[    3.139876] input: Generic Turtle Beach P11 Headset as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.3/input/input2
[    3.140416] hid-generic 0003:10F5:0231.0001: input,hidraw0: USB HID v1.00 Device [Generic Turtle Beach P11 Headset] on usb-0000:00:13.0-1/input3
[    3.404016] usb 2-2: new full-speed USB device number 3 using ohci-pci
[    3.596753] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    3.597506] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    3.598127] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    3.598757] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    3.599028] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    3.599312] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    3.599520] sd 4:0:0:2: Attached scsi generic sg4 type 0
[    3.599758] sd 4:0:0:3: Attached scsi generic sg5 type 0
[    3.605511] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    3.606125] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[    3.607512] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[    3.610876] sd 4:0:0:2: [sde] Attached SCSI removable disk
[    3.616507] usb 2-2: New USB device found, idVendor=046d, idProduct=c513
[    3.616513] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.616516] usb 2-2: Product: USB Receiver
[    3.616519] usb 2-2: Manufacturer: Logitech
[    3.653969] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input3
[    3.654547] logitech 0003:046D:C513.0002: input,hidraw1: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-2/input0
[    3.654565] logitech 0003:046D:C513.0003: fixing up Logitech keyboard report descriptor
[    3.657481] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.1/input/input4
[    3.658846] logitech 0003:046D:C513.0003: input,hiddev0,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2/input1
[    3.973662] EXT4-fs (sdb1): recovery complete
[    4.008988] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    4.312025] usb 3-1: new full-speed USB device number 2 using ohci-pci
[    4.518374] usb 3-1: New USB device found, idVendor=05a9, idProduct=8519
[    4.518379] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.518383] usb 3-1: Product: USB Camera
[    4.518386] usb 3-1: Manufacturer: OmniVision Technologies, Inc.
[   14.228443] Adding 1504252k swap on /dev/sdb5.  Priority:-1 extents:1 across:1504252k FS
[   14.490939] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.630768] systemd-udevd[262]: starting version 204
[   14.849712] lp: driver loaded but no devices found
[   15.002675] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.114225] ACPI Warning: 0x00000b00-0x00000b07 SystemIO conflicts with Region \SM00 1 (20130517/utaddress-251)
[   15.114239] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.158964] [drm] Initialized drm 1.1.0 20060810
[   15.396892] [drm] radeon kernel modesetting enabled.
[   15.397427] [drm] initializing kernel modesetting (RS480 0x1002:0x5954 0x103C:0x2A2F).
[   15.397451] [drm] register mmio base: 0xFDDF0000
[   15.397453] [drm] register mmio size: 65536
[   15.398027] [drm] Generation 2 PCI interface, using max accessible memory
[   15.398037] radeon 0000:01:05.0: VRAM: 64M 0x000000005C000000 - 0x000000005FFFFFFF (64M used)
[   15.398041] radeon 0000:01:05.0: GTT: 512M 0x0000000060000000 - 0x000000007FFFFFFF
[   15.398050] [drm] Detected VRAM RAM=64M, BAR=128M
[   15.398053] [drm] RAM width 128bits DDR
[   15.404066] [TTM] Zone  kernel: Available graphics memory: 443334 kiB
[   15.404071] [TTM] Zone highmem: Available graphics memory: 739754 kiB
[   15.404073] [TTM] Initializing pool allocator
[   15.404079] [TTM] Initializing DMA pool allocator
[   15.404116] [drm] radeon: 64M of VRAM memory ready
[   15.404118] [drm] radeon: 512M of GTT memory ready.
[   15.404139] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   15.413612] [drm] radeon: 4 quad pipes, 1 z pipes initialized.
[   15.419920] [drm] PCIE GART of 512M enabled (table at 0x0000000033000000).
[   15.426859] radeon 0000:01:05.0: WB enabled
[   15.426870] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x0000000060000000 and cpu addr 0xf398d000
[   15.426874] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.426877] [drm] Driver supports precise vblank timestamp query.
[   15.426910] [drm] radeon: irq initialized.
[   15.426925] [drm] Loading R300 Microcode
[   15.536844] type=1400 audit(1389863317.894:2): apparmor="STATUS" operation="profile_load" parent=311 profile="unconfined" name="/sbin/dhclient" pid=320 comm="apparmor_parser"
[   15.536857] type=1400 audit(1389863317.894:3): apparmor="STATUS" operation="profile_load" parent=311 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=320 comm="apparmor_parser"
[   15.536864] type=1400 audit(1389863317.894:4): apparmor="STATUS" operation="profile_load" parent=311 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=320 comm="apparmor_parser"
[   15.537824] type=1400 audit(1389863317.894:5): apparmor="STATUS" operation="profile_replace" parent=311 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=320 comm="apparmor_parser"
[   15.537833] type=1400 audit(1389863317.894:6): apparmor="STATUS" operation="profile_replace" parent=311 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=320 comm="apparmor_parser"
[   15.538343] type=1400 audit(1389863317.894:7): apparmor="STATUS" operation="profile_replace" parent=311 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=320 comm="apparmor_parser"
[   15.553990] type=1400 audit(1389863317.910:8): apparmor="STATUS" operation="profile_load" parent=311 profile="unconfined" name="/usr/sbin/ntpd" pid=330 comm="apparmor_parser"
[   15.615880] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   15.692727] microcode: AMD CPU family 0xf not supported
[   15.700834] [drm] radeon: ring at 0x0000000060001000
[   15.700861] [drm] ring test succeeded in 2 usecs
[   15.701037] [drm] ib test succeeded in 0 usecs
[   15.701557] [drm] Radeon Display Connectors
[   15.701561] [drm] Connector 0:
[   15.701563] [drm]   VGA-1
[   15.701567] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   15.701569] [drm]   Encoders:
[   15.701571] [drm]     CRT1: INTERNAL_DAC2
[   15.701573] [drm] Connector 1:
[   15.701575] [drm]   SVIDEO-1
[   15.701577] [drm]   Encoders:
[   15.701579] [drm]     TV1: INTERNAL_DAC2
[   15.806535] [drm] fb mappable at 0xF0040000
[   15.806540] [drm] vram apper at 0xF0000000
[   15.806543] [drm] size 9216000
[   15.806545] [drm] fb depth is 24
[   15.806547] [drm]    pitch is 7680
[   15.808881] fbcon: radeondrmfb (fb0) is primary device
[   15.901062] Console: switching to colour frame buffer device 240x75
[   15.923831] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[   15.923835] radeon 0000:01:05.0: registered panic notifier
[   15.981866] [drm] Initialized radeon 2.34.0 20080528 for 0000:01:05.0 on minor 0
[   16.209652] Linux video capture interface: v2.00
[   16.258944] usbcore: registered new interface driver snd-usb-audio
[   16.291817] gspca_main: v2.14.0 registered
[   16.378433] gspca_main: ov519-2.14.0 probing 05a9:8519
[   16.459341] cfg80211: Calling CRDA to update world regulatory domain
[   16.858874] Bluetooth: Core ver 2.16
[   16.858912] NET: Registered protocol family 31
[   16.858915] Bluetooth: HCI device and connection manager initialized
[   16.858927] Bluetooth: HCI socket layer initialized
[   16.858932] Bluetooth: L2CAP socket layer initialized
[   16.858939] Bluetooth: SCO socket layer initialized
[   16.860147] input: ov519 as /devices/pci0000:00/0000:00:13.1/usb3/3-1/input/input5
[   16.860752] usbcore: registered new interface driver ov519
[   16.925867] Bluetooth: RFCOMM TTY layer initialized
[   16.925886] Bluetooth: RFCOMM socket layer initialized
[   16.925889] Bluetooth: RFCOMM ver 1.11
[   16.929967] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.929975] Bluetooth: BNEP filters: protocol multicast
[   16.929991] Bluetooth: BNEP socket layer initialized
[   16.985482] usb 1-7: reset high-speed USB device number 6 using ehci-pci
[   17.141798] ppdev: user-space parallel port driver
[   17.163018] init: avahi-cups-reload main process (480) terminated with status 1
[   17.207197] type=1400 audit(1389863319.562:9): apparmor="STATUS" operation="profile_load" parent=499 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=504 comm="apparmor_parser"
[   17.207213] type=1400 audit(1389863319.562:10): apparmor="STATUS" operation="profile_load" parent=499 profile="unconfined" name="/usr/sbin/cupsd" pid=504 comm="apparmor_parser"
[   17.218728] type=1400 audit(1389863319.574:11): apparmor="STATUS" operation="profile_replace" parent=499 profile="unconfined" name="/usr/sbin/cupsd" pid=504 comm="apparmor_parser"
[   17.511210] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[   17.605457] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   17.612972] usbcore: registered new interface driver rt73usb
[   18.054623] init: failsafe main process (542) killed by TERM signal
[   18.382138] NET: Registered protocol family 15
[   18.647178] cfg80211: World regulatory domain updated:
[   18.647188] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.647191] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.647194] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.647197] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.647200] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.647202] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.073330] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[   20.074744] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[   20.155652] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.156136] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.166443] 8139too 0000:02:03.0 eth0: link down
[   20.166619] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.167112] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.966374] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   20.980415] zram: Created 1 device(s) ...
[   21.083996] Adding 739752k swap on /dev/zram0.  Priority:5 extents:1 across:739752k SSFS
[   25.044337] init: plymouth-stop pre-start process (1457) terminated with status 1
[   85.212130] tsc: Marking TSC unstable due to cpufreq changes
[   85.212247] Switched to clocksource acpi_pm
[  171.468591] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  171.484950] 8139too 0000:02:03.0 eth0: link down
[  171.488373] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  217.848284] show_signal_msg: 108 callbacks suppressed
[  217.848300] rutilt[1950]: segfault at 50 ip b71cd4f7 sp bf8558c0 error 4 in libgdk-x11-2.0.so.0.2400.20[b7166000+ab000]
[  230.509478] wlan0: authenticate with 0c:d5:02:ca:49:ab
[  230.569340] wlan0: send auth to 0c:d5:02:ca:49:ab (try 1/3)
[  230.576515] wlan0: authenticated
[  230.577101] rt73usb 1-7:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  230.577135] rt73usb 1-7:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  230.577143] rt73usb 1-7:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  230.580515] wlan0: associate with 0c:d5:02:ca:49:ab (try 1/3)
[  230.587138] wlan0: RX AssocResp from 0c:d5:02:ca:49:ab (capab=0x411 status=0 aid=2)
[  230.598868] wlan0: associated
[  230.598949] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  823.000101] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[  823.168065] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1092.000076] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 1093.000066] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 1093.168050] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1094.000111] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 1095.000070] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 1128.000062] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 1142.000062] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 2261.504061] ieee80211 phy0: wlan0: No probe response from AP 0c:d5:02:ca:49:ab after 500ms, disconnecting.
[ 2261.534506] cfg80211: Calling CRDA to update world regulatory domain
[ 2261.561348] cfg80211: World regulatory domain updated:
[ 2261.561364] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2261.561372] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2261.561379] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2261.561385] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2261.561391] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2261.561397] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2262.536068] usb 3-2: new full-speed USB device number 3 using ohci-pci
[ 2262.737226] usb 3-2: New USB device found, idVendor=0d5c, idProduct=a002
[ 2262.737241] usb 3-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 2262.793865] Atmel at76x USB Wireless LAN Driver 0.17 loading
[ 2262.808518] usb 3-2: firmware atmel_at76c503-rfmd-acc.bin not found!
[ 2262.808537] usb 3-2: you may need to download the firmware from http://developer.berlios.de/projects/at76c503a/
[ 2262.808557] at76c50x-usb: probe of 3-2:1.0 failed with error -2
[ 2262.808612] usbcore: registered new interface driver at76c50x-usb
[ 2275.257234] wlan0: authenticate with 0c:d5:02:ca:49:ab
[ 2275.309501] wlan0: send auth to 0c:d5:02:ca:49:ab (try 1/3)
[ 2275.319331] wlan0: authenticated
[ 2275.319594] rt73usb 1-7:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2275.319599] rt73usb 1-7:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2275.319602] rt73usb 1-7:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2275.320213] wlan0: associate with 0c:d5:02:ca:49:ab (try 1/3)
[ 2275.328596] wlan0: RX AssocResp from 0c:d5:02:ca:49:ab (capab=0x411 status=0 aid=2)
[ 2275.342600] wlan0: associated
[ 2278.000115] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 2282.000264] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 2283.000095] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 2284.000081] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 3599.000087] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 3814.000088] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 4039.750885] perf samples too long (2509 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 4113.000065] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 4448.000057] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 4449.000082] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 4453.000086] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 4463.000104] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 5243.000072] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 5603.000064] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 5609.000055] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 5610.000064] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 5613.000048] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 5614.000056] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 5616.000102] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 5629.000157] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6802.000073] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6807.000047] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6920.000073] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6923.000064] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6948.000049] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6950.000066] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6950.164050] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6951.000071] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6955.000043] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6955.164054] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6957.000062] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6958.000069] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6958.164037] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6959.000060] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6959.160155] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6960.000084] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6960.164045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6961.000095] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6963.000072] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6963.164065] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6964.000053] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6964.164063] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6965.000074] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6965.168049] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6966.000069] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6967.000148] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6969.000087] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6969.164048] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6970.000060] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6972.000051] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6972.164066] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6973.000048] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6973.164051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6974.000104] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6974.164049] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6975.000060] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6975.164058] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 6980.000048] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6982.000088] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 6998.000094] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7000.000083] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7003.000068] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7004.000068] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7004.160119] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 7005.000070] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7006.000051] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7007.000095] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7009.000099] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7009.168097] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 7010.000058] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7011.000073] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7013.000084] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7013.164063] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 7014.000079] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7015.000089] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7015.164063] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 7016.000044] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7017.000077] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7019.000053] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7020.000073] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7021.000074] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7022.000049] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7023.000061] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7025.000096] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7036.000054] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7037.000086] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 7040.000203] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8257.000317] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8258.000094] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8259.000044] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8259.164058] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8260.001604] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8260.168069] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8261.000083] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8262.000067] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8263.000054] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8263.164051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8264.000057] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8265.000086] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8265.164067] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8268.000070] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8269.000076] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8269.172058] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8271.000090] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8273.000080] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8281.000103] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8282.000066] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8313.000085] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8335.000055] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8338.000105] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8341.000071] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8343.000059] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8343.168055] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8348.000063] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8350.000093] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8350.168041] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8352.000052] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8352.164032] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8353.000057] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8355.000046] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8356.000055] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8356.164088] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8357.000097] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8358.000066] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8360.000045] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8362.000062] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8364.000061] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8364.164045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8370.000065] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8371.000067] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8385.000082] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8386.000063] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8436.000040] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8442.000241] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8442.168056] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8444.000106] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8444.164052] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8445.000111] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8447.000099] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8447.168063] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8449.000090] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8449.168074] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8451.000094] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8451.164051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 8452.000112] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8453.000098] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8464.000100] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8465.000149] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[ 8465.160055] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 9371.000042] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
yanni@xxxxxx:~$ 


```

---

### Post by chili555 on 2014-01-16
The Ralink wants the firmware file rt73.bin:```
$ modinfo rt73usb
filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
[COLOR="#FF0000"]firmware:       rt73.bin[/COLOR]
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
<snip>
```And the Atmel wants, well, a bunch of things:```
$ modinfo at76c50x_usb
filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/at76c50x-usb.ko
license:        GPL
description:    Atmel at76x USB Wireless LAN Driver
author:         Sebastian Smolorz <sesmo@gmx.net>
author:         Kalle Valo <kalle.valo@iki.fi>
author:         Guido Guenther <agx@sigxcpu.org>
author:         Pavel Roskin <proski@gnu.org>
author:         Balint Seeber <n0_5p4m_p13453@hotmail.com>
author:         Nick Jones
author:         Alex <alex@foogod.com>
author:         Joerg Albert <joerg.albert@gmx.de>
author:         Oliver Kurth <oku@masqmail.cx>
[COLOR="#FF0000"]firmware:       atmel_at76c505amx-rfmd.bin
firmware:       atmel_at76c505a-rfmd2958.bin
firmware:       atmel_at76c505-rfmd2958.bin
firmware:       atmel_at76c505-rfmd.bin
firmware:       atmel_at76c503-rfmd-acc.bin
firmware:       atmel_at76c503-rfmd.bin
firmware:       atmel_at76c503-i3863.bin
firmware:       atmel_at76c503-i3861.bin[/COLOR]
<snip>
```I suggest you install the Atmel firmware package. Then download the linux-firmware .deb file to your desktop. [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.116_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.116_all.deb) Right-click it and select 'Extract Here.' Then, in a terminal:```
sudo cp ~/Desktop/linux-firmware_1.116_all/lib/firmware/rt73.bin  /lib/firmware 
```Now unload and reload the driver so it sees the firmware:```
sudo modprobe -r rt73usb && sudo modprobe rt73usb
```As for patching drivers for injection, I have no knowledge and no comment.

---

### Post by johnnytwotimes on 2014-01-16
thank you, and yes I downloaded the packet injection driver by accident. I thought it was the actual firmware :/ going to try this now and thank you very much! and sorry for the computer name....roommate thinks hes funny. 

And did I leave anything out that would be helpful for future reference?

---

### Post by chili555 on 2014-01-16
> sorry for the computer name....roommate thinks hes funny. Not funny in the least. You can change it easily. Then I, who almost didn't answer,  and the several others who didn't answer might not be offended.

---

### Post by johnnytwotimes on 2014-01-17
My apologies. Thanks for answering. Wasn't intentional

---

### Post by chili555 on 2014-01-17
> **johnnytwotimes said:**
> My apologies. Thanks for answering. Wasn't intentionalIt's also sometimes preferable to copy and paste the result of the command without the prompt, like this:```
$ dmesg | grep -i scsi
[118488.910756] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[119587.185428] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[129136.383380] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[140039.918290] scsi11 : usb-storage 1-1.2:1.0
```...instead of this:```
[COLOR="#FF0000"]chili@Think410:~[/COLOR]$ dmesg | grep -i scsi
[118488.910756] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[119587.185428] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[129136.383380] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[140039.918290] scsi11 : usb-storage 1-1.2:1.0
```

---

### Post by johnnytwotimes on 2014-01-25
Won't have a problem remembering that lol

---

