---
title: "rt61 chipset, no wireless connection"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by xvedejas on 2008-03-17
Last thread got a little crazy, so I'm going to restart it with all the information I  have right here. I only hope an expert of the issue will take their time to go through what I've posted and help me solve this problem.

This is a fresh install of Ubuntu 7.10 32-bit. Everything has gone great except that I cannot connect to the internet. I see my wireless networks and it seems the machine detects the wireless card, but nothing will get it to connect.

And the info;

lspci

```
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0a.0 Network controller: RaLink RT2561/RT61 802.11g PCI
06:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod

```
Module                  Size  Used by
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
ac                      6148  0 
dock                   10656  0 
video                  18060  0 
button                  8976  0 
sbs                    19592  0 
container               5504  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
arc4                    2944  2 
snd_seq_dummy           4740  0 
ecb                     4608  2 
blkcipher               7556  1 ecb
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rc80211_simple          6912  1 
rt61pci                24576  0 
rt2x00pci              11520  1 rt61pci
rt2x00lib              19584  2 rt61pci,rt2x00pci
rfkill                  8208  1 rt2x00lib
agpgart                35016  0 
mac80211              171016  4 rc80211_simple,rt61pci,rt2x00pci,rt2x00lib
usblp                  15104  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211                7304  1 mac80211
soundcore               8800  1 snd
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
eeprom_93cx6            3200  1 rt61pci
pcspkr                  4224  0 
k8temp                  6656  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_nforce2             7040  0 
i2c_core               26112  1 i2c_nforce2
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
usbhid                 29536  0 
hid                    28928  1 usbhid
sata_nv                20612  3 
floppy                 60004  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
ehci_hcd               36492  0 
forcedeth              51592  0 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  4 sbp2,sg,sd_mod,libata
ohci_hcd               22916  0 
usbcore               138632  5 usblp,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

dmesg

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3a90
[    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524272
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524272
[    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7A50 checksum 0
[    0.000000] ACPI: RSDP 000F7A50, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FFF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF3180, 6897 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: MCFG 7FFF9B40, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FFF9A80, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] Built 1 zonelists.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=71dd6d58-435f-4991-afcd-8c97b0ea3798 ro quiet splash noapic
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2200.225 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 2067328k/2097088k available (2015k kernel code, 28456k reserved, 916k data, 364k init, 1179584k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.084000] Calibrating delay using timer specific routine.. 4404.12 BogoMIPS (lpj=8808243)
[    0.084000] Security Framework v1.0.0 initialized
[    0.084000] SELinux:  Disabled at boot.
[    0.084000] Mount-cache hash table entries: 512
[    0.084000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.084000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.084000] CPU 0(2) -> Core 0
[    0.084000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.084000] Compat vDSO mapped to ffffe000.
[    0.084000] Checking 'hlt' instruction... OK.
[    0.100000] SMP alternatives: switching to UP code
[    0.100000] Early unpacking initramfs... done
[    0.368000] ACPI: Core revision 20070126
[    0.368000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.372000] ACPI: setting ELCR to 0200 (from 0c20)
[    0.376000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.376000] SMP alternatives: switching to SMP code
[    0.380000] Booting processor 1/1 eip 3000
[    0.388000] Initializing CPU#1
[    0.468000] Calibrating delay using timer specific routine.. 4400.73 BogoMIPS (lpj=8801469)
[    0.468000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.468000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.468000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.468000] CPU 1(2) -> Core 1
[    0.468000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.468000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.468000] Total of 2 processors activated (8804.85 BogoMIPS).
[    0.468000] Brought up 2 CPUs
[    0.516000] migration_cost=4000
[    0.516000] Booting paravirtualized kernel on bare hardware
[    0.516000] Time:  0:36:35  Date: 02/17/108
[    0.516000] NET: Registered protocol family 16
[    0.516000] EISA bus registered
[    0.516000] ACPI: bus type pci registered
[    0.520000] PCI: PCI BIOS revision 3.00 entry at 0xfa870, last bus=6
[    0.520000] PCI: Using configuration type 1
[    0.520000] Setting up standard PCI resources
[    0.524000] ACPI: EC: Look up EC in DSDT
[    0.528000] ACPI: Interpreter enabled
[    0.528000] ACPI: (supports S0 S3 S4 S5)
[    0.528000] ACPI: Using PIC for interrupt routing
[    0.540000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.540000] PCI: Probing PCI hardware (bus 00)
[    0.540000] PCI: Transparent bridge - 0000:00:06.0
[    0.540000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.540000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.624000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.624000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.624000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.624000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 *10 11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.624000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.624000] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.624000] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LMC1] (IRQs 5 7 9 10 *11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LPMU] (IRQs *5 7 9 10 11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.624000] ACPI: PCI Interrupt Link [LSID] (IRQs *5 7 9 10 11 14 15)
[    0.624000] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.628000] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 10 *11 14 15)
[    0.628000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [AMC1] (IRQs 20 21 22 23) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.628000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.632000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.632000] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0, disabled.
[    0.632000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.632000] pnp: PnP ACPI init
[    0.632000] ACPI: bus type pnp registered
[    0.636000] pnp: PnP ACPI: found 11 devices
[    0.636000] ACPI: ACPI bus type pnp unregistered
[    0.636000] PnPBIOS: Disabled by ACPI PNP
[    0.636000] PCI: Using ACPI for IRQ routing
[    0.636000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.708000] NET: Registered protocol family 8
[    0.708000] NET: Registered protocol family 20
[    0.708000] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[    0.708000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.708000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.708000] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.708000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.708000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.708000] pnp: 00:09: iomem range 0x0-0x0 could not be reserved
[    0.708000] pnp: 00:0a: iomem range 0xf0000-0xfffff could not be reserved
[    0.708000] pnp: 00:0a: iomem range 0x7fff0000-0x7fffffff could not be reserved
[    0.708000] pnp: 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.708000] pnp: 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.736000] PCI: Bridge: 0000:00:06.0
[    0.736000]   IO window: 9000-9fff
[    0.736000]   MEM window: fdd00000-fddfffff
[    0.736000]   PREFETCH window: fde00000-fdefffff
[    0.736000] PCI: Bridge: 0000:00:0a.0
[    0.736000]   IO window: 8000-8fff
[    0.736000]   MEM window: fdc00000-fdcfffff
[    0.736000]   PREFETCH window: fdb00000-fdbfffff
[    0.736000] PCI: Bridge: 0000:00:0c.0
[    0.736000]   IO window: 7000-7fff
[    0.736000]   MEM window: fda00000-fdafffff
[    0.736000]   PREFETCH window: fd900000-fd9fffff
[    0.736000] PCI: Bridge: 0000:00:0d.0
[    0.736000]   IO window: 6000-6fff
[    0.736000]   MEM window: fd800000-fd8fffff
[    0.736000]   PREFETCH window: fd700000-fd7fffff
[    0.736000] PCI: Bridge: 0000:00:0e.0
[    0.736000]   IO window: 5000-5fff
[    0.736000]   MEM window: fd600000-fd6fffff
[    0.736000]   PREFETCH window: fd500000-fd5fffff
[    0.736000] PCI: Bridge: 0000:00:0f.0
[    0.736000]   IO window: 4000-4fff
[    0.736000]   MEM window: fa000000-fcffffff
[    0.736000]   PREFETCH window: e0000000-efffffff
[    0.736000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.736000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    0.736000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.736000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.736000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.736000] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[    0.736000] NET: Registered protocol family 2
[    0.740000] Time: acpi_pm clocksource has been installed.
[    0.740000] Switched to high resolution mode on CPU 0
[    0.740000] Switched to high resolution mode on CPU 1
[    0.784000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.784000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.784000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.784000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.784000] TCP reno registered
[    0.800000] checking if image is initramfs... it is
[    1.332000] Freeing initrd memory: 7334k freed
[    1.332000] audit: initializing netlink socket (disabled)
[    1.332000] audit(1205714195.240:1): initialized
[    1.332000] highmem bounce pool size: 64 pages
[    1.332000] VFS: Disk quotas dquot_6.5.1
[    1.332000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.332000] io scheduler noop registered
[    1.332000] io scheduler anticipatory registered
[    1.332000] io scheduler deadline registered
[    1.332000] io scheduler cfq registered (default)
[    1.332000] Boot video device is 0000:06:00.0
[    1.332000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    1.332000] assign_interrupt_mode Found MSI capability
[    1.332000] Allocate Port Service[0000:00:0a.0:pcie00]
[    1.332000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    1.332000] assign_interrupt_mode Found MSI capability
[    1.332000] Allocate Port Service[0000:00:0c.0:pcie00]
[    1.332000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    1.332000] assign_interrupt_mode Found MSI capability
[    1.332000] Allocate Port Service[0000:00:0d.0:pcie00]
[    1.332000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    1.332000] assign_interrupt_mode Found MSI capability
[    1.332000] Allocate Port Service[0000:00:0e.0:pcie00]
[    1.332000] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[    1.332000] assign_interrupt_mode Found MSI capability
[    1.332000] Allocate Port Service[0000:00:0f.0:pcie00]
[    1.332000] isapnp: Scanning for PnP cards...
[    1.688000] isapnp: No Plug & Play device found
[    1.704000] Real Time Clock Driver v1.12ac
[    1.704000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.704000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.708000] input: Macintosh mouse button emulation as /class/input/input0
[    1.708000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.708000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    1.960000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.960000] mice: PS/2 mouse device common for all mice
[    1.960000] EISA: Probing bus 0 at eisa.0
[    1.960000] Cannot allocate resource for EISA slot 1
[    1.960000] Cannot allocate resource for EISA slot 4
[    1.960000] Cannot allocate resource for EISA slot 5
[    1.960000] Cannot allocate resource for EISA slot 6
[    1.960000] Cannot allocate resource for EISA slot 7
[    1.960000] Cannot allocate resource for EISA slot 8
[    1.960000] EISA: Detected 0 cards.
[    1.960000] TCP cubic registered
[    1.960000] NET: Registered protocol family 1
[    1.960000] Using IPI No-Shortcut mode
[    1.960000]   Magic number: 0:834:607
[    1.960000]   hash matches device ptyae
[    1.960000] Freeing unused kernel memory: 364k freed
[    1.980000] input: AT Translated Set 2 keyboard as /class/input/input1
[    3.152000] AppArmor: AppArmor initialized<5>audit(1205714196.740:2):  type=1505 info="AppArmor initialized" pid=1266
[    3.156000] fuse init (API version 7.8)
[    3.160000] Failure registering capabilities with primary security module.
[    3.188000] ACPI: Fan [FAN] (on)
[    3.196000] ACPI: Thermal Zone [THRM] (24 C)
[    3.724000] usbcore: registered new interface driver usbfs
[    3.724000] usbcore: registered new interface driver hub
[    3.724000] usbcore: registered new device driver usb
[    3.724000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.724000] ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 5
[    3.724000] PCI: setting IRQ 5 as level-triggered
[    3.724000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUBA] -> GSI 5 (level, low) -> IRQ 5
[    3.724000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    3.724000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.724000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    3.724000] ohci_hcd 0000:00:02.0: irq 5, io mem 0xfe02f000
[    3.728000] SCSI subsystem initialized
[    3.732000] libata version 2.21 loaded.
[    3.736000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    3.748000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.748000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.780000] usb usb1: configuration #1 chosen from 1 choice
[    3.780000] hub 1-0:1.0: USB hub found
[    3.780000] hub 1-0:1.0: 10 ports detected
[    3.808000] Floppy drive(s): fd0 is 1.44M
[    3.824000] FDC 0 is a post-1991 82077
[    3.884000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[    3.884000] PCI: setting IRQ 10 as level-triggered
[    3.884000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[    3.884000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    3.884000] forcedeth: using HIGHDMA
[    4.188000] usb 1-8: new low speed USB device using ohci_hcd and address 2
[    4.408000] eth0: forcedeth.c: subsystem: 0147b:1c20 bound to 0000:00:08.0
[    4.408000] ACPI: PCI Interrupt Link [LMC1] enabled at IRQ 11
[    4.408000] PCI: setting IRQ 11 as level-triggered
[    4.408000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LMC1] -> GSI 11 (level, low) -> IRQ 11
[    4.408000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    4.408000] forcedeth: using HIGHDMA
[    4.520000] usb 1-8: configuration #1 chosen from 1 choice
[    4.832000] usb 1-10: new full speed USB device using ohci_hcd and address 3
[    4.928000] eth1: forcedeth.c: subsystem: 0147b:1c20 bound to 0000:00:09.0
[    4.928000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 10
[    4.928000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 10 (level, low) -> IRQ 10
[    4.928000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    4.928000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.928000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    4.928000] ehci_hcd 0000:00:02.1: debug port 1
[    4.928000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    4.928000] ehci_hcd 0000:00:02.1: irq 10, io mem 0xfe02e000
[    5.008000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.008000] usb usb2: configuration #1 chosen from 1 choice
[    5.008000] hub 2-0:1.0: USB hub found
[    5.008000] hub 2-0:1.0: 10 ports detected
[    5.112000] NFORCE-MCP55: IDE controller at PCI slot 0000:00:04.0
[    5.112000] NFORCE-MCP55: chipset revision 161
[    5.112000] NFORCE-MCP55: not 100% native mode: will probe irqs later
[    5.112000] NFORCE-MCP55: 0000:00:04.0 (rev a1) UDMA133 controller
[    5.112000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[    5.112000] Probing IDE interface ide0...
[    5.416000] usb 1-10: device not accepting address 3, error -62
[    5.472000] usbcore: registered new interface driver hiddev
[    5.472000] usb 1-8: USB disconnect, address 2
[    5.848000] hda: HL-DT-ST RW/DVD GCC-4481B, ATAPI CD/DVD-ROM drive
[    6.152000] usbcore: registered new interface driver usbhid
[    6.152000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    6.456000] usb 1-8: new low speed USB device using ohci_hcd and address 5
[    6.520000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    6.520000] sata_nv 0000:00:05.0: version 3.4
[    6.520000] ACPI: PCI Interrupt Link [LSID] enabled at IRQ 5
[    6.520000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LSID] -> GSI 5 (level, low) -> IRQ 5
[    6.520000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    6.520000] scsi0 : sata_nv
[    6.520000] scsi1 : sata_nv
[    6.520000] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001dc00 irq 5
[    6.520000] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001dc08 irq 5
[    6.524000] hda: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.524000] Uniform CD-ROM driver Revision: 3.20
[    6.788000] usb 1-8: configuration #1 chosen from 1 choice
[    6.804000] input: Razer Razer 1600dpi Mouse as /class/input/input2
[    6.804000] input: USB HID v1.10 Mouse [Razer Razer 1600dpi Mouse] on usb-0000:00:02.0-8
[    6.988000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.032000] ata1.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
[    7.032000] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    7.100000] ata1.00: configured for UDMA/133
[    7.108000] usb 1-10: new full speed USB device using ohci_hcd and address 6
[    7.320000] usb 1-10: configuration #1 chosen from 1 choice
[    7.412000] ata2: SATA link down (SStatus 0 SControl 300)
[    7.420000] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
[    7.420000] ACPI: PCI Interrupt Link [LFID] enabled at IRQ 10
[    7.420000] ACPI: PCI Interrupt 0000:00:05.1[B] -> Link [LFID] -> GSI 10 (level, low) -> IRQ 10
[    7.420000] PCI: Setting latency timer of device 0000:00:05.1 to 64
[    7.420000] scsi2 : sata_nv
[    7.420000] scsi3 : sata_nv
[    7.420000] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001c800 irq 10
[    7.420000] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001c808 irq 10
[    7.732000] ata3: SATA link down (SStatus 0 SControl 300)
[    8.052000] ata4: SATA link down (SStatus 0 SControl 300)
[    8.060000] ACPI: PCI Interrupt Link [LSA2] enabled at IRQ 11
[    8.060000] ACPI: PCI Interrupt 0000:00:05.2[C] -> Link [LSA2] -> GSI 11 (level, low) -> IRQ 11
[    8.060000] PCI: Setting latency timer of device 0000:00:05.2 to 64
[    8.060000] scsi4 : sata_nv
[    8.060000] scsi5 : sata_nv
[    8.060000] ata5: SATA max UDMA/133 cmd 0x0001c400 ctl 0x0001c002 bmdma 0x0001b400 irq 11
[    8.060000] ata6: SATA max UDMA/133 cmd 0x0001bc00 ctl 0x0001b802 bmdma 0x0001b408 irq 11
[    8.372000] ata5: SATA link down (SStatus 0 SControl 300)
[    8.692000] ata6: SATA link down (SStatus 0 SControl 300)
[    8.700000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[    8.700000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[    8.700000] PCI: Setting latency timer of device 0000:01:08.0 to 64
[    8.752000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    8.756000] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    8.756000] sd 0:0:0:0: [sda] Write Protect is off
[    8.756000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.756000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.756000] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    8.756000] sd 0:0:0:0: [sda] Write Protect is off
[    8.756000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.756000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.756000]  sda: sda1 sda2 sda3
[    8.788000] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.792000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    9.096000] Attempting manual resume
[    9.096000] swsusp: Resume From Partition 8:2
[    9.096000] PM: Checking swsusp image.
[    9.096000] PM: Resume from disk failed.
[    9.128000] kjournald starting.  Commit interval 5 seconds
[    9.128000] EXT3-fs: mounted filesystem with ordered data mode.
[   10.024000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508d0000924b3d]
[   14.128000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   14.128000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   14.144000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.144000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.364000] input: PC Speaker as /class/input/input3
[   14.520000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10A0
[   14.520000] usbcore: registered new interface driver usblp
[   14.520000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   14.572000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.596000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 11
[   14.596000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNK3] -> GSI 11 (level, low) -> IRQ 11
[   14.596000] PCI: Setting latency timer of device 0000:01:0a.0 to 64
[   14.676000] ieee80211_init: failed to initialize WME (err=-17)
[   14.696000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   14.696000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   14.696000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   14.696000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   14.696000] wmaster0: Selected rate control algorithm 'simple'
[   14.812000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 5
[   14.812000] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LAZA] -> GSI 5 (level, low) -> IRQ 5
[   14.812000] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   15.020000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   16.072000] lp: driver loaded but no devices found
[   16.120000] Adding 498004k swap on /dev/sda2.  Priority:-1 extents:1 across:498004k
[   16.460000] EXT3 FS on sda3, internal journal
[   17.508000] input: Power Button (FF) as /class/input/input4
[   17.508000] ACPI: Power Button (FF) [PWRF]
[   17.508000] input: Power Button (CM) as /class/input/input5
[   17.508000] ACPI: Power Button (CM) [PWRB]
[   17.608000] No dock devices found.
[   17.852000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   17.852000] powernow-k8: MP systems not supported by PSB BIOS structure
[   17.852000] powernow-k8: MP systems not supported by PSB BIOS structure
[   18.864000] ppdev: user-space parallel port driver
[   18.972000] audit(1205732213.773:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5193 profile="/usr/sbin/cupsd"
[   19.012000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   19.012000] apm: disabled - APM is not SMP safe.
[   19.072000] eth0: no link during initialization.
[   19.160000] eth1: no link during initialization.
[   19.536000] Failure registering capabilities with primary security module.
[   19.984000] Bluetooth: Core ver 2.11
[   19.984000] NET: Registered protocol family 31
[   19.984000] Bluetooth: HCI device and connection manager initialized
[   19.984000] Bluetooth: HCI socket layer initialized
[   20.048000] Bluetooth: L2CAP ver 2.8
[   20.048000] Bluetooth: L2CAP socket layer initialized
[   20.108000] Bluetooth: RFCOMM socket layer initialized
[   20.108000] Bluetooth: RFCOMM TTY layer initialized
[   20.108000] Bluetooth: RFCOMM ver 1.8
```

Thanks for your time and help!

---

### Post by xvedejas on 2008-03-17
I've attempted installing the rt61 serialmonkey drivers. The module* does* load, but I still can't connect to the internet. Why? :confused:

---

### Post by xvedejas on 2008-03-19
Two days, nobody seems to have given any thought to my problem. My wireless cards should work, shouldn't they?

Do you need more information?

---

### Post by xvedejas on 2008-03-19
Does the lack of replies mean I'm in bad luck?

---

### Post by rustybronco on 2008-03-19
No...
Considering you tried at least two different ways to install the rt61 drivers
did you try connecting from the command line per Kevdogs guide [http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)
have you tried connecting without encryption?
if you have, then I suggest ndiswrapper. ONE GUIDE [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

