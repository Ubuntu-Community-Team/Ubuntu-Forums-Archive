---
title: "Wireless help with HP tx 2524 ca notebook"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by alexpwalsh on 2008-11-27
Hello all.... I've tried many things, and I cannot get my Hp tx 2524ca to work on my university network. I can get it working fine at home with my wep network, but needless to say, the university does not use wep. Here, they are using WPA2 Enterprise, and my laptop cannot connect to it. It does fine in windows, but not in ubuntu 8.10. I got it to work fine in 8.04 after some restriced driver updates and such, but with 8.10, I'm out of luck. 

I have tried a few things and have made a few posts, but I hope for this one to be the last about this issue.I found the sticky post on how to submit wireless problems and I now have some rather lengthly messages for this post (seen below) I was informed that with these messages, you Ubuntu Elite could possibly help me. I dont want to have to revert back to 8.04.... Help me...

Here it goes.... 
**********************************************
lspci
**********************************************
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

**********************************************
lsusb
**********************************************
```
Bus 007 Device 002: ID 056a:0093 Wacom Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 062a:0000 Creative Labs Optical mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f2:b103 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

***********************************************
 lspci -nn | grep 'Broadcom'
***********************************************
```
08:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
```

**********************************************
 ifconfig
**********************************************
```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:82:5a:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:32:0b:82  
          inet6 addr: fe80::221:ff:fe32:b82/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:4333
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4414 (4.4 KB)  TX bytes:4414 (4.4 KB)
```


**********************************************
iwconfig
**********************************************
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:169
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:169
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.
```


**********************************************
lsmod
**********************************************
```
Module                  Size  Used by
af_packet              29568  2 
binfmt_misc            18700  1 
rfcomm                 51104  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  16 rfcomm,bnep
ipv6                  314312  18 
vboxdrv              1653120  0 
ppdev                  16904  0 
powernow_k8            23684  0 
cpufreq_stats          14468  0 
cpufreq_ondemand       16400  2 
cpufreq_conservative    16392  0 
freq_table             13568  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave      10368  0 
cpufreq_userspace      12420  0 
container              12288  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
snd_hda_intel         489776  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              14596  0 
uvcvideo               68616  0 
evdev                  20512  14 
soundcore              16800  1 snd
psmouse                51612  0 
i2c_piix4              17936  0 
pcspkr                 11136  0 
compat_ioctl32         18176  1 uvcvideo
videodev               46720  2 uvcvideo,compat_ioctl32
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
i2c_core               36128  1 i2c_piix4
v4l1_compat            24580  2 uvcvideo,videodev
btusb                  22040  3 
bluetooth              70820  11 rfcomm,bnep,sco,l2cap,btusb
ieee80211_crypt_tkip    18048  0 
wl                   1085520  0 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
fglrx                2135688  32 
video                  28948  0 
output                 11776  1 video
wmi                    15808  0 
battery                21128  0 
ac                     13448  0 
button                 15904  0 
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
usbhid                 39776  0 
hid                    59072  1 usbhid
usb_storage            92992  0 
pata_acpi              13568  0 
libusual               31912  1 usb_storage
pata_atiixp            14208  0 
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sg                     45408  0 
ata_generic            14212  0 
ohci_hcd               35100  0 
ehci_hcd               49164  0 
ahci                   43148  2 
usbcore               175888  8 uvcvideo,btusb,usbhid,usb_storage,libusual,ohci_hcd,ehci_hcd
libata                200160  4 pata_acpi,pata_atiixp,ata_generic,ahci
scsi_mod              183160  5 usb_storage,sd_mod,sr_mod,sg,libata
dock                   18464  1 libata
r8169                  40452  0 
mii                    14592  1 r8169
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 
```



**********************************************
 dmesg
**********************************************
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-10-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Fri Nov 21 19:19:18 UTC 2008 (Ubuntu 2.6.27-10.20-generic)
[    0.000000] Command line: root=UUID=951f879a-cc18-408a-ad1a-2764fc897a04 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afb8f000 (usable)
[    0.000000]  BIOS-e820: 00000000afb8f000 - 00000000afc3c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afc3c000 - 00000000afd70000 (usable)
[    0.000000]  BIOS-e820: 00000000afd70000 - 00000000afdbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000afdbf000 - 00000000afe58000 (usable)
[    0.000000]  BIOS-e820: 00000000afe58000 - 00000000afebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afeee000 (usable)
[    0.000000]  BIOS-e820: 00000000afeee000 - 00000000afeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00aff00000 page 4k
[    0.000000] kernel direct mapping tables up to aff00000 @ 8000-d000
[    0.000000] last_map_addr: aff00000 end: aff00000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ b000-11000
[    0.000000] last_map_addr: 140000000 end: 140000000
[    0.000000] RAMDISK: 377ab000 - 37fef09f
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT AFEFE120, 005C (r1 HPQOEM SLIC-MPC        3       1000013)
[    0.000000] ACPI: FACP AFEFD000, 00F4 (r4 HP     30F1            3 MSFT  100000D)
[    0.000000] ACPI: DSDT AFEF1000, 8EE2 (r1 HP     30F1     F0000000 INTL 20051117)
[    0.000000] ACPI: FACS AFE61000, 0040
[    0.000000] ACPI: HPET AFEFC000, 0038 (r1 HP     30F1            1 MSFT    F4240)
[    0.000000] ACPI: APIC AFEFB000, 0084 (r2 HP     30F1            1 TFSM    F4240)
[    0.000000] ACPI: MCFG AFEFA000, 003C (r1 HP     30F1            1 TFSM    F4240)
[    0.000000] ACPI: BOOT AFEF0000, 0028 (r1 HP     30F1            1            1)
[    0.000000] ACPI: SLIC AFEEF000, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: SSDT AFEEE000, 0386 (r1 AMD    PowerNow        1 AMD         1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000c000 -  0000000000033fff] pages 28
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b9f5c]    TEXT DATA BSS ==> [0000200000 - 00008b9f5c]
[    0.000000]   #3 [00377ab000 - 0037fef09f]          RAMDISK ==> [00377ab000 - 0037fef09f]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000]   #6 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
[    0.000000]  [ffffe20000000000-ffffe20004ffffff] PMD -> [ffff880028200000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000afb8f
[    0.000000]     0: 0x000afc3c -> 0x000afd70
[    0.000000]     0: 0x000afdbf -> 0x000afe58
[    0.000000]     0: 0x000afebf -> 0x000afeee
[    0.000000]     0: 0x000afeff -> 0x000aff00
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 982315
[    0.000000]   DMA zone: 2111 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 699852 pages, LIFO batch:31
[    0.000000]   Normal zone: 258048 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000afb8f000 - 00000000afc3c000
[    0.000000] PM: Registered nosave memory: 00000000afd70000 - 00000000afdbf000
[    0.000000] PM: Registered nosave memory: 00000000afe58000 - 00000000afebf000
[    0.000000] PM: Registered nosave memory: 00000000afeee000 - 00000000afeff000
[    0.000000] PM: Registered nosave memory: 00000000aff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000e4000000
[    0.000000] PM: Registered nosave memory: 00000000e4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at b0000000 (gap: aff00000:30100000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 960011
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=951f879a-cc18-408a-ad1a-2764fc897a04 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 999.582 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 3786000k/5242880k available (3114k kernel code, 143260k reserved, 1573k data, 540k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004025] Calibrating delay loop (skipped), value calculated using timer frequency.. 3998.31 BogoMIPS (lpj=7996628)
[    0.004161] Security Framework initialized
[    0.004179] SELinux:  Disabled at boot.
[    0.004227] AppArmor: AppArmor initialized
[    0.006107] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009814] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.012000] Mount-cache hash table entries: 256
[    0.012000] Initializing cgroup subsys ns
[    0.012000] Initializing cgroup subsys cpuacct
[    0.012000] Initializing cgroup subsys memory
[    0.012000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.012000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.012000] CPU 0/0 -> Node 0
[    0.012000] tseg: 00aff00000
[    0.012000] CPU: Physical Processor ID: 0
[    0.012000] CPU: Processor Core ID: 0
[    0.012000] using C1E aware idle routine
[    0.012076] ACPI: Core revision 20080609
[    0.019622] ACPI: Checking initramfs for custom DSDT
[    0.729209] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.772031] CPU0: AMD Turion(tm) X2 Dual-Core Mobile RM-70 stepping 01
[    0.772031] Using local APIC timer interrupts.
[    0.772063] APIC timer calibration result 569922
[    0.772076] Detected 0.569 MHz APIC timer.
[    0.772083] APIC frequency too slow, disabling apic timer
[    0.772733] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.20 BogoMIPS (lpj=7980404)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.860399] CPU1: AMD Turion(tm) X2 Dual-Core Mobile RM-70 stepping 01
[    0.860452] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.864031] Measured 194683645 cycles TSC warp between CPUs, turning off TSC clock.
[    0.864031] Marking TSC unstable due to check_tsc_sync_source failed
[    0.864107] Brought up 2 CPUs
[    0.864116] Total of 2 processors activated (7988.51 BogoMIPS).
[    0.864294] CPU0 attaching sched-domain:
[    0.864304]  domain 0: span 0-1 level CPU
[    0.864313]   groups: 0 1
[    0.864328]   domain 1: span 0-1 level NODE
[    0.864336]    groups: 0-1
[    0.864353] CPU1 attaching sched-domain:
[    0.864360]  domain 0: span 0-1 level CPU
[    0.864368]   groups: 1 0
[    0.864380]   domain 1: span 0-1 level NODE
[    0.864388]    groups: 0-1
[    0.864725] net_namespace: 1552 bytes
[    0.864725] Booting paravirtualized kernel on bare hardware
[    0.865116] Time:  8:21:47  Date: 11/27/08
[    0.865255] NET: Registered protocol family 16
[    0.865340] TOM: 00000000c0000000 aka 3072M
[    0.865340] Fam 10h mmconf [e0000000, e0ffffff]
[    0.865340] TOM2: 0000000140000000 aka 5120M
[    0.865340] ACPI: bus type pci registered
[    0.865340] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.865340] PCI: MCFG area at e0000000 reserved in E820
[    0.876031] PCI: Using MMCONFIG at e0000000 - e3ffffff
[    0.876031] PCI: Using configuration type 1 for base access
[    0.879395] ACPI: EC: Look up EC in DSDT
[    0.892031] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.892031] ACPI: Interpreter enabled
[    0.892031] ACPI: (supports S0 S3 S4 S5)
[    0.892031] ACPI: Using IOAPIC for interrupt routing
[    0.892686] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.912477] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.912477] ACPI: EC: driver started in interrupt mode
[    0.912532] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.912532] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.912532] pci 0000:00:04.0: PME# disabled
[    0.912532] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.912532] pci 0000:00:05.0: PME# disabled
[    0.912539] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.912546] pci 0000:00:06.0: PME# disabled
[    0.912726] PCI: 0000:00:11.0 reg 10 io port: [6038, 603f]
[    0.912741] PCI: 0000:00:11.0 reg 14 io port: [604c, 604f]
[    0.912757] PCI: 0000:00:11.0 reg 18 io port: [6030, 6037]
[    0.912773] PCI: 0000:00:11.0 reg 1c io port: [6048, 604b]
[    0.912788] PCI: 0000:00:11.0 reg 20 io port: [6010, 601f]
[    0.912804] PCI: 0000:00:11.0 reg 24 32bit mmio: [d2409000, d24093ff]
[    0.912893] PCI: 0000:00:12.0 reg 10 32bit mmio: [d2408000, d2408fff]
[    0.913016] PCI: 0000:00:12.1 reg 10 32bit mmio: [d2407000, d2407fff]
[    0.913129] PCI: 0000:00:12.2 reg 10 32bit mmio: [d2409500, d24095ff]
[    0.913129] pci 0000:00:12.2: supports D1
[    0.913129] pci 0000:00:12.2: supports D2
[    0.913129] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.913129] pci 0000:00:12.2: PME# disabled
[    0.913129] PCI: 0000:00:13.0 reg 10 32bit mmio: [d2406000, d2406fff]
[    0.913129] PCI: 0000:00:13.1 reg 10 32bit mmio: [d2405000, d2405fff]
[    0.913129] PCI: 0000:00:13.2 reg 10 32bit mmio: [d2409400, d24094ff]
[    0.913129] pci 0000:00:13.2: supports D1
[    0.913129] pci 0000:00:13.2: supports D2
[    0.913129] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.913129] pci 0000:00:13.2: PME# disabled
[    0.913129] PCI: 0000:00:14.1 reg 10 io port: [0, 7]
[    0.913129] PCI: 0000:00:14.1 reg 14 io port: [0, 3]
[    0.913129] PCI: 0000:00:14.1 reg 18 io port: [0, 7]
[    0.913129] PCI: 0000:00:14.1 reg 1c io port: [0, 3]
[    0.913129] PCI: 0000:00:14.1 reg 20 io port: [6000, 600f]
[    0.913173] PCI: 0000:00:14.2 reg 10 64bit mmio: [d2400000, d2403fff]
[    0.913264] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.913274] pci 0000:00:14.2: PME# disabled
[    0.913495] PCI: 0000:00:14.5 reg 10 32bit mmio: [d2404000, d2404fff]
[    0.913935] PCI: 0000:01:05.0 reg 10 32bit mmio: [c0000000, cfffffff]
[    0.913945] PCI: 0000:01:05.0 reg 14 io port: [5000, 50ff]
[    0.913955] PCI: 0000:01:05.0 reg 18 32bit mmio: [d2300000, d230ffff]
[    0.913976] PCI: 0000:01:05.0 reg 24 32bit mmio: [d2200000, d22fffff]
[    0.914002] pci 0000:01:05.0: supports D1
[    0.914006] pci 0000:01:05.0: supports D2
[    0.914184] PCI: bridge 0000:00:01.0 io port: [5000, 5fff]
[    0.914191] PCI: bridge 0000:00:01.0 32bit mmio: [d2200000, d23fffff]
[    0.914201] PCI: bridge 0000:00:01.0 64bit mmio pref: [c0000000, cfffffff]
[    0.914309] PCI: bridge 0000:00:04.0 io port: [3000, 4fff]
[    0.914316] PCI: bridge 0000:00:04.0 32bit mmio: [d1200000, d21fffff]
[    0.914325] PCI: bridge 0000:00:04.0 64bit mmio pref: [d0000000, d0ffffff]
[    0.914439] PCI: 0000:08:00.0 reg 10 64bit mmio: [d1100000, d1103fff]
[    0.914543] pci 0000:08:00.0: supports D1
[    0.914546] pci 0000:08:00.0: supports D2
[    0.914727] PCI: bridge 0000:00:05.0 32bit mmio: [d1100000, d11fffff]
[    0.914813] PCI: 0000:09:00.0 reg 10 io port: [2000, 20ff]
[    0.914849] PCI: 0000:09:00.0 reg 18 64bit mmio: [d1010000, d1010fff]
[    0.914875] PCI: 0000:09:00.0 reg 20 64bit mmio: [d1000000, d100ffff]
[    0.914890] PCI: 0000:09:00.0 reg 30 32bit mmio: [ffff0000, ffffffff]
[    0.914940] pci 0000:09:00.0: supports D1
[    0.914943] pci 0000:09:00.0: supports D2
[    0.914947] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.914957] pci 0000:09:00.0: PME# disabled
[    0.915120] PCI: bridge 0000:00:06.0 io port: [2000, 2fff]
[    0.915132] PCI: bridge 0000:00:06.0 64bit mmio pref: [d1000000, d10fffff]
[    0.915262] pci 0000:00:14.4: transparent bridge
[    0.915272] PCI: bridge 0000:00:14.4 io port: [1000, 1fff]
[    0.915347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.916031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.916031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.916031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.916031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.916031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.936457] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.936965] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.937466] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.937965] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.938464] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.938963] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.939462] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.939961] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.940031] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.940031] pnp: PnP ACPI init
[    0.940031] ACPI: bus type pnp registered
[    0.945165] pnp: PnP ACPI: found 12 devices
[    0.945171] ACPI: ACPI bus type pnp unregistered
[    0.945257] PCI: Using ACPI for IRQ routing
[    0.956054] NET: Registered protocol family 8
[    0.956059] NET: Registered protocol family 20
[    0.960062] NetLabel: Initializing
[    0.960062] NetLabel:  domain hash size = 128
[    0.960062] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.960093] NetLabel:  unlabeled traffic allowed by default
[    0.960133] PCI-GART: No AMD northbridge found.
[    0.960216] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.960225] hpet0: 4 32-bit timers, 14318180 Hz
[    0.964031] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.964031]    actual entries 65586
[    0.964042] Clockevents: could not switch to one-shot mode: lapic is not functional.
[    0.964058] Could not switch to high resolution mode on CPU 0
[    0.964031] AppArmor: AppArmor Filesystem Enabled
[    0.964031] ACPI: RTC can wake from S4
[    0.968030] Clockevents: could not switch to one-shot mode: lapic is not functional.
[    0.968037] Could not switch to high resolution mode on CPU 1
[    0.984088] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.984095] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.984122] system 00:09: ioport range 0x400-0x4cf has been reserved
[    0.984129] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.984135] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
[    0.984141] system 00:09: ioport range 0x680-0x6ff has been reserved
[    0.984146] system 00:09: ioport range 0x77a-0x77a has been reserved
[    0.984152] system 00:09: ioport range 0xc00-0xc01 has been reserved
[    0.984158] system 00:09: ioport range 0xc14-0xc14 has been reserved
[    0.984164] system 00:09: ioport range 0xc50-0xc52 has been reserved
[    0.984170] system 00:09: ioport range 0xc6c-0xc6c has been reserved
[    0.984177] system 00:09: ioport range 0xc6f-0xc6f has been reserved
[    0.984183] system 00:09: ioport range 0xcd0-0xcdb has been reserved
[    0.984205] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[    0.984211] system 00:0a: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.992019] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.992019] pci 0000:00:01.0:   IO window: 0x5000-0x5fff
[    0.992019] pci 0000:00:01.0:   MEM window: 0xd2200000-0xd23fffff
[    0.992019] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.992019] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.992019] pci 0000:00:04.0:   IO window: 0x3000-0x4fff
[    0.992019] pci 0000:00:04.0:   MEM window: 0xd1200000-0xd21fffff
[    0.992019] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000d0ffffff
[    0.992019] pci 0000:00:05.0: PCI bridge, secondary bus 0000:08
[    0.992019] pci 0000:00:05.0:   IO window: disabled
[    0.992019] pci 0000:00:05.0:   MEM window: 0xd1100000-0xd11fffff
[    0.992019] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.992019] pci 0000:00:06.0: PCI bridge, secondary bus 0000:09
[    0.992019] pci 0000:00:06.0:   IO window: 0x2000-0x2fff
[    0.992019] pci 0000:00:06.0:   MEM window: 0xb0000000-0xb00fffff
[    0.992019] pci 0000:00:06.0:   PREFETCH window: 0x000000d1000000-0x000000d10fffff
[    0.992019] pci 0000:00:14.4: PCI bridge, secondary bus 0000:80
[    0.992019] pci 0000:00:14.4:   IO window: 0x1000-0x1fff
[    0.992019] pci 0000:00:14.4:   MEM window: disabled
[    0.992019] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.992019] pci 0000:00:01.0: setting latency timer to 64
[    0.992019] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.992019] pci 0000:00:04.0: setting latency timer to 64
[    0.992019] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.992019] pci 0000:00:05.0: setting latency timer to 64
[    0.992019] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.992019] pci 0000:00:06.0: setting latency timer to 64
[    0.992019] bus: 00 index 0 io port: [0, ffff]
[    0.992019] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.992019] bus: 01 index 0 io port: [5000, 5fff]
[    0.992019] bus: 01 index 1 mmio: [d2200000, d23fffff]
[    0.992019] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    0.992019] bus: 01 index 3 mmio: [0, 0]
[    0.992019] bus: 02 index 0 io port: [3000, 4fff]
[    0.992019] bus: 02 index 1 mmio: [d1200000, d21fffff]
[    0.992019] bus: 02 index 2 mmio: [d0000000, d0ffffff]
[    0.992019] bus: 02 index 3 mmio: [0, 0]
[    0.992019] bus: 08 index 0 mmio: [0, 0]
[    0.992019] bus: 08 index 1 mmio: [d1100000, d11fffff]
[    0.992019] bus: 08 index 2 mmio: [0, 0]
[    0.992019] bus: 08 index 3 mmio: [0, 0]
[    0.992019] bus: 09 index 0 io port: [2000, 2fff]
[    0.992019] bus: 09 index 1 mmio: [b0000000, b00fffff]
[    0.992019] bus: 09 index 2 mmio: [d1000000, d10fffff]
[    0.992019] bus: 09 index 3 mmio: [0, 0]
[    0.992019] bus: 80 index 0 io port: [1000, 1fff]
[    0.992019] bus: 80 index 1 mmio: [0, 0]
[    0.992019] bus: 80 index 2 mmio: [0, 0]
[    0.992019] bus: 80 index 3 io port: [0, ffff]
[    0.992019] bus: 80 index 4 mmio: [0, ffffffffffffffff]
[    0.992019] NET: Registered protocol family 2
[    1.032357] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.035614] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.040025] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.040025] TCP: Hash tables configured (established 524288 bind 65536)
[    1.040025] TCP reno registered
[    1.048279] NET: Registered protocol family 1
[    1.048543] checking if image is initramfs... it is
[    1.764068] Clocksource tsc unstable (delta = -98962328 ns)
[    2.040036] Freeing initrd memory: 8464k freed
[    2.045164] Simple Boot Flag at 0x44 set to 0x1
[    2.047651] audit: initializing netlink socket (disabled)
[    2.047664] type=2000 audit(1227774108.044:1): initialized
[    2.055185] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.059156] VFS: Disk quotas dquot_6.5.1
[    2.059342] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.059552] msgmni has been set to 7411
[    2.059798] io scheduler noop registered
[    2.059798] io scheduler anticipatory registered
[    2.059798] io scheduler deadline registered
[    2.060021] io scheduler cfq registered (default)
[    2.280133] pci 0000:01:05.0: Boot video device
[    2.280477] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.280515] pcieport-driver 0000:00:04.0: found MSI capability
[    2.280588] pci_express 0000:00:04.0:pcie00: allocate port service
[    2.280737] pci_express 0000:00:04.0:pcie02: allocate port service
[    2.280737] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    2.280795] pcieport-driver 0000:00:05.0: found MSI capability
[    2.280856] pci_express 0000:00:05.0:pcie00: allocate port service
[    2.280992] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    2.281005] pcieport-driver 0000:00:06.0: found MSI capability
[    2.281067] pci_express 0000:00:06.0:pcie00: allocate port service
[    2.374696] hpet_resources: 0xfed00000 is busy
[    2.374998] Linux agpgart interface v0.103
[    2.374998] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.379774] brd: module loaded
[    2.380010] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.380200] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.401730] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.401745] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.416294] mice: PS/2 mouse device common for all mice
[    2.416543] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.416562] rtc0: alarms up to one day, hpet irqs
[    2.416637] cpuidle: using governor ladder
[    2.416637] cpuidle: using governor menu
[    2.417384] TCP cubic registered
[    2.417689] registered taskstats version 1
[    2.417759]   Magic number: 0:729:372
[    2.418147] rtc_cmos 00:05: setting system clock to 2008-11-27 08:21:49 UTC (1227774109)
[    2.418154] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.418159] EDD information not available.
[    2.418332] Freeing unused kernel memory: 540k freed
[    2.418904] Write protecting the kernel read-only data: 4348k
[    2.430568] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.644361] fuse init (API version 7.9)
[    2.772897] processor ACPI0007:00: registered as cooling_device0
[    2.772918] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.773252] processor ACPI0007:01: registered as cooling_device1
[    2.780621] thermal LNXTHERM:01: registered as thermal_zone0
[    2.784029] ACPI: Thermal Zone [THRM] (45 C)
[    3.393827] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.393882] r8169 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.393923] r8169 0000:09:00.0: setting latency timer to 64
[    3.394599] eth0: RTL8168c/8111c at 0xffffc20000648000, 00:1e:68:82:5a:18, XID 3c4000c0 IRQ 2300
[    3.396026] No dock devices found.
[    3.411194] SCSI subsystem initialized
[    3.453148] libata version 3.00 loaded.
[    3.456412] usbcore: registered new interface driver usbfs
[    3.456482] usbcore: registered new interface driver hub
[    3.456659] usbcore: registered new device driver usb
[    3.456915] ahci 0000:00:11.0: version 3.0
[    3.457029] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.457397] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    3.457406] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio 
[    3.459183] scsi0 : ahci
[    3.460009] scsi1 : ahci
[    3.460027] scsi2 : ahci
[    3.460027] scsi3 : ahci
[    3.460027] scsi4 : ahci
[    3.460027] scsi5 : ahci
[    3.460027] ata1: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409100 irq 22
[    3.460027] ata2: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409180 irq 22
[    3.460027] ata3: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409200 irq 22
[    3.460027] ata4: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409280 irq 22
[    3.460027] ata5: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409300 irq 22
[    3.460027] ata6: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409380 irq 22
[    3.488028] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.956055] ata1: softreset failed (device not ready)
[    3.956069] ata1: failed due to HW bug, retry pmp=0
[    4.128153] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.128838] ata1.00: ATA-8: FUJITSU MHZ2320BH G2, 8909, max UDMA/100
[    4.128838] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.129682] ata1.00: configured for UDMA/100
[    4.628288] ata2: softreset failed (device not ready)
[    4.628288] ata2: failed due to HW bug, retry pmp=0
[    4.800063] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.814316] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633L, 0400, max UDMA/100
[    4.827737] ata2.00: configured for UDMA/100
[    5.156053] ata3: SATA link down (SStatus 0 SControl 300)
[    5.488060] ata4: SATA link down (SStatus 0 SControl 300)
[    5.820045] ata5: SATA link down (SStatus 0 SControl 300)
[    6.152040] ata6: SATA link down (SStatus 0 SControl 300)
[    6.152311] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2320B 8909 PQ: 0 ANSI: 5
[    6.154948] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633L  0400 PQ: 0 ANSI: 5
[    6.155350] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.155388] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    6.155397] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    6.155503] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[    6.155670] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2408000
[    6.216292] usb usb1: configuration #1 chosen from 1 choice
[    6.216358] hub 1-0:1.0: USB hub found
[    6.216452] hub 1-0:1.0: 3 ports detected
[    6.324593] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.324632] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    6.324641] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    6.324699] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[    6.324740] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2407000
[    6.388328] usb usb2: configuration #1 chosen from 1 choice
[    6.388395] hub 2-0:1.0: USB hub found
[    6.388489] hub 2-0:1.0: 3 ports detected
[    6.604595] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.604635] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    6.604644] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    6.604709] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 3
[    6.604796] ehci_hcd 0000:00:12.2: debug port 1
[    6.604847] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2409500
[    6.620000] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.620299] usb usb3: configuration #1 chosen from 1 choice
[    6.620365] hub 3-0:1.0: USB hub found
[    6.620400] hub 3-0:1.0: 6 ports detected
[    6.839501] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.839540] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    6.839550] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    6.839620] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    6.839769] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2406000
[    6.900311] usb usb4: configuration #1 chosen from 1 choice
[    6.900379] hub 4-0:1.0: USB hub found
[    6.900473] hub 4-0:1.0: 3 ports detected
[    6.960022] usb 3-4: new high speed USB device using ehci_hcd and address 2
[    7.116477] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.116516] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    7.116526] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    7.116593] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 5
[    7.116637] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2405000
[    7.181833] usb usb5: configuration #1 chosen from 1 choice
[    7.181920] hub 5-0:1.0: USB hub found
[    7.181948] hub 5-0:1.0: 3 ports detected
[    7.363447] usb 3-4: configuration #1 chosen from 1 choice
[    7.399941] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    7.399941] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    7.399941] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    7.399941] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 6
[    7.399941] ehci_hcd 0000:00:13.2: debug port 1
[    7.399941] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd2409400
[    7.515998] usb 4-2: new full speed USB device using ohci_hcd and address 2
[    7.531986] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.534217] usb usb6: configuration #1 chosen from 1 choice
[    7.535846] hub 6-0:1.0: USB hub found
[    7.535871] hub 6-0:1.0: 6 ports detected
[    7.592010] hub 4-0:1.0: unable to enumerate USB device on port 2
[    7.756965] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    7.757001] ohci_hcd 0000:00:14.5: setting latency timer to 64
[    7.757011] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    7.757123] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    7.757238] ohci_hcd 0000:00:14.5: irq 18, io mem 0xd2404000
[    7.757990] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.758090] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    7.785988] Driver 'sr' needs updating - please use bus_type methods
[    7.800530] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.800544] Uniform CD-ROM driver Revision: 3.20
[    7.800795] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.803973] Driver 'sd' needs updating - please use bus_type methods
[    7.803973] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    7.803973] sd 0:0:0:0: [sda] Write Protect is off
[    7.803973] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.803973] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.803973] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    7.803973] sd 0:0:0:0: [sda] Write Protect is off
[    7.803973] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.803973] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.803973]  sda:<6>usb usb7: configuration #1 chosen from 1 choice
[    7.816674] hub 7-0:1.0: USB hub found
[    7.816768] hub 7-0:1.0: 2 ports detected
[    7.882977]  sda1 sda2 sda3 sda4
[    7.907982] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.996012] usb 6-2: new high speed USB device using ehci_hcd and address 2
[    8.037016] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.037041] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    8.040532] scsi6 : pata_atiixp
[    8.040532] scsi7 : pata_atiixp
[    8.040925] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6000 irq 14
[    8.040925] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6008 irq 15
[    8.040925] ata7: port disabled. ignoring.
[    8.178468] usb 6-2: configuration #1 chosen from 1 choice
[    8.475963] usb 7-2: new full speed USB device using ohci_hcd and address 2
[    8.659462] usb 7-2: configuration #1 chosen from 1 choice
[    8.665127] usbcore: registered new interface driver libusual
[    8.675955] Initializing USB Mass Storage driver...
[    8.677153] scsi8 : SCSI emulation for USB Mass Storage devices
[    8.683787] usb-storage: device found at 2
[    8.683794] usb-storage: waiting for device to settle before scanning
[    8.983936] usb 5-1: new full speed USB device using ohci_hcd and address 2
[    9.188914] usb 5-1: configuration #1 chosen from 1 choice
[    9.206512] usbcore: registered new interface driver usb-storage
[    9.206513] usbcore: registered new interface driver hiddev
[    9.206538] USB Mass Storage support registered.
[    9.206695] usbcore: registered new interface driver usbhid
[    9.206711] usbhid: v2.6:USB HID core driver
[    9.299704] PM: Starting manual resume from disk
[    9.299713] PM: Resume from partition 8:4
[    9.299716] PM: Checking hibernation image.
[    9.299882] PM: Resume from disk failed.
[    9.342533] kjournald starting.  Commit interval 5 seconds
[    9.342577] EXT3-fs: mounted filesystem with ordered data mode.
[   13.684305] usb-storage: device scan complete
[   13.686247] scsi 8:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   13.689385] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[   13.689766] sd 8:0:0:0: Attached scsi generic sg2 type 0
[   16.172524] udevd version 124 started
[   16.566247] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.627819] shpchp: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   16.627819] shpchp: shpc_init: cannot reserve MMIO region
[   16.627819] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.689554] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   16.719893] ACPI: Power Button (FF) [PWRF]
[   16.720234] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   16.751839] ACPI: Power Button (CM) [PWRB]
[   16.752191] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   16.775904] ACPI: Sleep Button (CM) [SLPB]
[   16.776399] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   16.778796] ACPI: Lid Switch [LID]
[   16.792376] ACPI: AC Adapter [ACAD] (on-line)
[   17.069907] ACPI: Battery Slot [BAT0] (battery present)
[   17.070787] ACPI: WMI: Mapper loaded
[   17.331832] acpi device:05: registered as cooling_device2
[   17.331832] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[   17.351908] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.359019] acpi device:0c: registered as cooling_device3
[   17.359843] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:09/input/input7
[   17.375870] ACPI: Video Device [DVGA] (multi-head: yes  rom: no  post: no)
[   17.620299] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   17.643823] [fglrx] Maximum main memory to use for locked dma buffers: 3548 MBytes.
[   17.643823] [fglrx]   vendor: 1002 device: 9612 count: 1
[   17.643831] [fglrx] ioport: bar 1, base 0x5000, size: 0x100
[   17.643831] pci 0000:01:05.0: power state changed by ACPI to D0
[   17.643831] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.643831] pci 0000:01:05.0: setting latency timer to 64
[   17.645106] [fglrx] PAT is enabled successfully!
[   17.647283] [fglrx] module loaded - fglrx 8.55.2 [Oct 28 2008] with 1 minors
[   17.664415] ieee80211_crypt: registered algorithm 'NULL'
[   17.675827] wl 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.675827] wl 0000:08:00.0: setting latency timer to 64
[   17.707829] ieee80211_crypt: registered algorithm 'TKIP'
[   17.707829] eth1: Broadcom BCM432b 802.11 Wireless Controller 5.10.27.6
[   18.067818] Bluetooth: Core ver 2.13
[   18.080152] NET: Registered protocol family 31
[   18.080158] Bluetooth: HCI device and connection manager initialized
[   18.080167] Bluetooth: HCI socket layer initialized
[   18.111832] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   18.111832] usbcore: registered new interface driver btusb
[   18.639813] Linux video capture interface: v2.00
[   18.655802] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   18.663828] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   18.784517] uvcvideo: Found UVC 1.00 device CKF7073 (04f2:b103)
[   18.799783] input: CKF7073 as /devices/pci0000:00/0000:00:13.2/usb6/6-2/6-2:1.0/input/input9
[   19.076461] usbcore: registered new interface driver uvcvideo
[   19.076480] USB Video Class driver (v0.1.0)
[   19.326180] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.326338] HDA Intel 0000:00:14.2: setting latency timer to 64
[   19.483777] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04711/0xa00000
[   19.551767] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   21.153762] lp: driver loaded but no devices found
[   21.426725] Adding 562264k swap on /dev/sda4.  Priority:-1 extents:1 across:562264k
[   39.095568] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   39.270783] usb 1-1: configuration #1 chosen from 1 choice
[   39.284461] input: HID 062a:0000 as /devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1:1.0/input/input11
[   39.347897] input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:12.0-1
[  221.663602] EXT3 FS on sda3, internal journal
[  222.704817] type=1505 audit(1227786929.785:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=6016
[  223.024262] type=1505 audit(1227786930.105:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=6021
[  223.024988] type=1505 audit(1227786930.105:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=6021
[  223.168430] ip_tables: (C) 2000-2006 Netfilter Core Team
[  224.325885] powernow-k8: Found 1 AMD Turion(tm) X2 Dual-Core Mobile RM-70 processors (2 cpu cores) (version 2.20.00)
[  224.325913] powernow-k8:    0 : pstate 0 (2000 MHz)
[  224.325913] powernow-k8:    1 : pstate 1 (1000 MHz)
[  224.325913] powernow-k8:    2 : pstate 2 (500 MHz)
[  224.974959] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  225.228955] ppdev: user-space parallel port driver
[  227.240928] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  227.240928] vboxdrv: Successfully done.
[  227.240928] vboxdrv: Found 2 processor cores.
[  227.248935] vboxdrv: fAsync=1 offMin=0xb9a951f offMax=0xb9a951f
[  227.248935] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[  227.248935] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[  227.555654] NET: Registered protocol family 10
[  227.557409] lo: Disabled Privacy Extensions
[  229.905237] Bluetooth: L2CAP ver 2.11
[  229.905263] Bluetooth: L2CAP socket layer initialized
[  229.922443] Bluetooth: SCO (Voice Link) ver 0.6
[  229.922443] Bluetooth: SCO socket layer initialized
[  229.954001] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  229.954001] Bluetooth: BNEP filters: protocol multicast
[  229.981195] Bridge firewalling registered
[  229.981716] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  230.102629] Bluetooth: RFCOMM socket layer initialized
[  230.102711] Bluetooth: RFCOMM TTY layer initialized
[  230.102720] Bluetooth: RFCOMM ver 1.10
[  234.276804] r8169: eth0: link down
[  234.280819] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  234.423987] NET: Registered protocol family 17
[  234.628615] [fglrx] GART Table is not in FRAME_BUFFER range 
[  234.751742] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  238.940780] eth1: no IPv6 routers present
[  255.473522] CPU0 attaching NULL sched-domain.
[  255.473550] CPU1 attaching NULL sched-domain.
[  255.486388] CPU0 attaching sched-domain:
[  255.486448]  domain 0: span 0-1 level CPU
[  255.486469]   groups: 0 1
[  255.486501]   domain 1: span 0-1 level NODE
[  255.486519]    groups: 0-1
[  255.486565] CPU1 attaching sched-domain:
[  255.486579]  domain 0: span 0-1 level CPU
[  255.486594]   groups: 1 0
[  255.486623]   domain 1: span 0-1 level NODE
[  255.486638]    groups: 0-1
[  531.851268] usb 1-1: USB disconnect, address 2
[  534.272784] usb 1-1: new low speed USB device using ohci_hcd and address 3
[  534.459973] usb 1-1: configuration #1 chosen from 1 choice
[  534.465542] input: HID 062a:0000 as /devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1:1.0/input/input12
[  534.517636] input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:12.0-1
[  610.465308] usb 1-1: USB disconnect, address 3
[  616.307607] usb 1-1: new low speed USB device using ohci_hcd and address 4
[  616.490426] usb 1-1: configuration #1 chosen from 1 choice
[  616.511558] input: HID 062a:0000 as /devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1:1.0/input/input13
[  616.564396] input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:12.0-1
```




**********************************************
 sudo lshw -C network
**********************************************
```
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:32:0b:82
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:82:5a:18
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:19:e1:90:1a:76
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


******************************************
 iwlist scan
*****************************************
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```


*******************************************
 lsb_release -d
*******************************************
```
Description:	Ubuntu 8.10
```

*******************************************
uname -mr
******************************************
```
2.6.27-10-generic x86_64
```

****************************************
sudo /etc/init.d/networking restart
****************************************
```
 * Reconfiguring network interfaces...                                                                                                          [ OK ] 

```


Help me everyone.... I'm lost

---

### Post by Ayuthia on 2008-11-27
The setup of the wl driver looks fine.  Are you using wpa_supplicant?  You might try this guide:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
It is kevdog's guide on how to connect manually.  There is a section for WPA further down in the guide.

Another guide is from wieman01:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
It is about how to use wpa_supplicant.

I am not for sure about if it will work for you or not.  There has been problems with WEP/WPA with the wl driver.  I have not had a chance to see if I can find the code changes that are being made for the wl driver.

---

