---
title: "Lose network overnight, new NIC, new router. Same problem."
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by thezman007 on 2013-10-23
Hello everyone,

I am not completely new to Linux or Ubuntu, but am still a beginner and cannot seem to get this ironed out. I use a wired connection to my router which acts as an Access Point behind my landlord's modem/router (they know). Theirs is a Netgear WNDR4000. I often leave the computer on overnight as I use Dropbox and like to let it sync before shutting it down. I should mention that I have a Windows 7 Virtualbox guest that mainly does the syncing. I used this set up for many months without issue. Unfortunately, I do not know which update or upgrade may have brought the change, but now I lose my connection every night. I have not lost it yet during the day that I can remember. I thought that perhaps my wired interface was going bad on my MOBO, so I bought a new NIC card. That seemed to fix it...then it didn't. Ok, it must be my router right? I replaced that as well. Still this problem persists. I have tried to provide all the things listed in the ticket posting thread (post?) and here they are. I did not post the results of 'dmesg' because it was too much and I need to know what to specify to look for since the problem is not wireless. Thanks in advance :)

Oh, also, I was able to ping google.com last time the network went "down" so I don't know what that's about.

```
Network when DOWN

lspci

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx1 port A)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 9800 GT] (rev a2)
02:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE9172 SATA III 6Gb/s RAID Controller (rev 11)
04:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
04:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
06:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
 

lsusb

Bus 002 Device 004: ID 03f0:a011 Hewlett-Packard Deskjet 3050A
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 007 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

lsmod

Module                  Size  Used by
usblp                  18315  0 
pci_stub               12623  1 
vboxpci                23237  0 
vboxnetadp             25671  0 
vboxnetflt             27613  0 
vboxdrv               320275  3 vboxpci,vboxnetadp,vboxnetflt
nvidia               9425761  48 
bnep                   18240  2 
kvm_amd                56136  0 
snd_hda_codec_realtek    79855  1 
kvm                   422160  1 kvm_amd
snd_hda_intel          34063  5 
snd_hda_codec         135141  2 snd_hda_codec_realtek,snd_hda_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
snd_hwdep              17765  1 snd_hda_codec
aes_x86_64             17256  1 aesni_intel
rfcomm                 47562  0 
snd_pcm                97523  3 snd_hda_intel,snd_hda_codec
bluetooth             212001  10 bnep,rfcomm
snd_seq_midi           13325  0 
joydev                 17694  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
dm_multipath           23306  0 
snd                    83674  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
microcode              23030  0 
parport_pc             32867  0 
scsi_dh                14589  1 dm_multipath
ppdev                  17114  0 
soundcore              15092  1 snd
sp5100_tco             13792  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
serio_raw              13216  0 
edac_core              53053  0 
mxm_wmi                13022  0 
mac_hid                13254  0 
i2c_piix4              13302  0 
k10temp                13174  0 
edac_mce_amd           23548  0 
fam15h_power           13167  0 
wmi                    19257  1 mxm_wmi
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
binfmt_misc            17541  1 
usb_storage            49288  0 
hid_logitech_dj        18768  0 
hid_logitech           26586  0 
ff_memless             13098  1 hid_logitech
usbhid                 47259  2 hid_logitech_dj,hid_logitech
hid                   100815  3 hid_logitech_dj,hid_logitech,usbhid
firewire_ohci          41034  0 
dm_raid45              78156  0 
firewire_core          64697  1 firewire_ohci
crc_itu_t              12708  1 firewire_core
r8169                  62741  0 
pata_atiixp            13205  0 
ahci                   25869  1 
libahci                27338  1 ahci
xor                    17153  1 dm_raid45
dm_mirror              22204  0 
dm_region_hash         20962  1 dm_mirror
dm_log                 18565  3 dm_raid45,dm_mirror,dm_region_hash


sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:04:06.0
       logical name: eth1
       version: 10
       serial: 64:70:02:11:80:c9
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:bc00(size=256) memory:fddff000-fddff0ff memory:fdc00000-fdc1ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 90:2b:34:93:7e:55
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:ae00(size=256) memory:fd9ff000-fd9fffff memory:fd9f8000-fd9fbfff

sudo service networking restart
stop: Unknown instance: 
networking stop/waiting


```

---

### Post by Andy_Lee on 2013-10-23
Pls post output command:
```

ping your_router_ip -c 30
```

---

### Post by thezman007 on 2013-10-24
Here you go:

```
ping 192.168.1.137 -c 30
PING 192.168.1.137 (192.168.1.137) 56(84) bytes of data.
64 bytes from 192.168.1.137: icmp_req=1 ttl=64 time=0.472 ms
64 bytes from 192.168.1.137: icmp_req=2 ttl=64 time=0.453 ms
64 bytes from 192.168.1.137: icmp_req=3 ttl=64 time=0.455 ms
64 bytes from 192.168.1.137: icmp_req=4 ttl=64 time=0.450 ms
64 bytes from 192.168.1.137: icmp_req=5 ttl=64 time=0.457 ms
64 bytes from 192.168.1.137: icmp_req=6 ttl=64 time=0.446 ms
64 bytes from 192.168.1.137: icmp_req=7 ttl=64 time=0.431 ms
64 bytes from 192.168.1.137: icmp_req=8 ttl=64 time=0.447 ms
64 bytes from 192.168.1.137: icmp_req=9 ttl=64 time=0.442 ms
64 bytes from 192.168.1.137: icmp_req=10 ttl=64 time=0.425 ms
64 bytes from 192.168.1.137: icmp_req=11 ttl=64 time=0.441 ms
64 bytes from 192.168.1.137: icmp_req=12 ttl=64 time=0.441 ms
64 bytes from 192.168.1.137: icmp_req=13 ttl=64 time=0.441 ms
64 bytes from 192.168.1.137: icmp_req=14 ttl=64 time=0.450 ms
64 bytes from 192.168.1.137: icmp_req=15 ttl=64 time=0.450 ms
64 bytes from 192.168.1.137: icmp_req=16 ttl=64 time=0.452 ms
64 bytes from 192.168.1.137: icmp_req=17 ttl=64 time=0.446 ms
64 bytes from 192.168.1.137: icmp_req=18 ttl=64 time=0.448 ms
64 bytes from 192.168.1.137: icmp_req=19 ttl=64 time=0.462 ms
64 bytes from 192.168.1.137: icmp_req=20 ttl=64 time=0.448 ms
64 bytes from 192.168.1.137: icmp_req=21 ttl=64 time=0.441 ms
64 bytes from 192.168.1.137: icmp_req=22 ttl=64 time=0.446 ms
64 bytes from 192.168.1.137: icmp_req=23 ttl=64 time=0.449 ms
64 bytes from 192.168.1.137: icmp_req=24 ttl=64 time=0.436 ms
64 bytes from 192.168.1.137: icmp_req=25 ttl=64 time=0.456 ms
64 bytes from 192.168.1.137: icmp_req=26 ttl=64 time=0.442 ms
64 bytes from 192.168.1.137: icmp_req=27 ttl=64 time=0.450 ms
64 bytes from 192.168.1.137: icmp_req=28 ttl=64 time=0.464 ms
64 bytes from 192.168.1.137: icmp_req=29 ttl=64 time=0.463 ms
64 bytes from 192.168.1.137: icmp_req=30 ttl=64 time=0.442 ms

--- 192.168.1.137 ping statistics ---
30 packets transmitted, 30 received, 0% packet loss, time 29000ms
rtt min/avg/max/mdev = 0.425/0.448/0.472/0.016 ms

```

I can also ping 8.8.8.8  or google.com just as well, but my browser says no go, as well as any other internet services (Software Updater, etc.)

That's what I don't get...

---

### Post by thezman007 on 2013-10-26
Bump please

---

### Post by thezman007 on 2013-11-02
Come on guys and gals, nothing?! At least tell me some commands to run...By the way I was thinking about upgrading to 13.04 to see if that would fix it (not realizing I would need to upgrade incrementally) when the LiveCD informed me of this:

You have Ubuntu 12.04.3 LTS and Ubuntu 12.04.3 LTS installed. Would you like to...etc.etc.etc. 

What the heck? I took a screenshot but apparently tried to save it to the CD instead of the file system. Could this be my problem?

Here is the /var/log/dmesg file:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-42-generic (buildd@batsu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #65~precise1-Ubuntu SMP Wed Oct 2 20:57:18 UTC 2013 (Ubuntu 3.5.0-42.65~precise1-generic 3.5.7.21)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-42-generic root=UUID=b6c7efe4-1f0d-40ef-acec-fb172d5ff066 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cfd9ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cfda0000-0x00000000cfdd0fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cfdd1000-0x00000000cfdfffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cfe00000-0x00000000cfefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-990FXA-UD3/GA-990FXA-UD3, BIOS F9 10/22/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x22f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000CFE00000 mask FFFFFFE00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000022f000000 aka 8944M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
[    0.000000] total RAM covered: 3326M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 4M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xcfe00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcfda0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f4c20-0x000f4c2f] mapped at [ffff8800000f4c20]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xcfd9ffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfbfffff] page 2M
[    0.000000]  [mem 0xcfc00000-0xcfd9ffff] page 4k
[    0.000000] kernel direct mapping tables up to 0xcfd9ffff @ [mem 0x1fffd000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x22effffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000]  [mem 0x200000000-0x22effffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x22effffff @ [mem 0xcfd9e000-0xcfd9ffff]
[    0.000000] RAMDISK: [mem 0x361a4000-0x370c9fff]
[    0.000000] ACPI: RSDP 00000000000f6b40 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfdd1000 0004C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000cfdd1080 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfdd1100 07997 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfda0000 00040
[    0.000000] ACPI: MSDM 00000000cfdd8b80 00055 (v03 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: HPET 00000000cfdd8c00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfdd8c40 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: EUDS 00000000cfdd8cc0 00740 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: MATS 00000000cfdd9400 00034 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 00000000cfdd9470 00182 (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 00000000cfdd8ac0 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: MATS 00000000cfdd9600 0648F (v01        MATS RCM 80000001 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000cfddfb00 013CE (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22effffff]
[    0.000000]   NODE_DATA [mem 0x22effc000-0x22effffff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880226600000-ffff88022e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xcfd9ffff]
[    0.000000]   node   0: [mem 0x100000000-0x22effffff]
[    0.000000] On node 0 totalpages: 2092335
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 830944 pages, LIFO batch:31
[    0.000000]   Normal zone: 19392 pages used for memmap
[    0.000000]   Normal zone: 1221696 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfda0000 - 00000000cfdd1000
[    0.000000] PM: Registered nosave memory: 00000000cfdd1000 - 00000000cfe00000
[    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] e820: [mem 0xcff00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88022ec00000 s83584 r8192 d22912 u262144
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2056553
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-42-generic root=UUID=b6c7efe4-1f0d-40ef-acec-fb172d5ff066 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ c4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 8074404k/9158656k available (6827k kernel code, 789316k absent, 294936k reserved, 6342k data, 948k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3825.515 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 7651.03 BogoMIPS (lpj=15302060)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000023] Security Framework initialized
[    0.000032] AppArmor: AppArmor initialized
[    0.000033] Yama: becoming mindful.
[    0.000531] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002328] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003109] Mount-cache hash table entries: 256
[    0.003254] Initializing cgroup subsys cpuacct
[    0.003256] Initializing cgroup subsys memory
[    0.003263] Initializing cgroup subsys devices
[    0.003264] Initializing cgroup subsys freezer
[    0.003265] Initializing cgroup subsys blkio
[    0.003267] Initializing cgroup subsys perf_event
[    0.003285] tseg: 00cff00000
[    0.003286] CPU: Physical Processor ID: 0
[    0.003287] CPU: Processor Core ID: 0
[    0.003288] mce: CPU supports 7 MCE banks
[    0.003294] LVT offset 1 assigned for vector 0xf9
[    0.004594] ACPI: Core revision 20120320
[    0.054876] ftrace: allocating 27640 entries in 108 pages
[    0.617305] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.656890] CPU0: AMD FX(tm)-6200 Six-Core Processor              stepping 02
[    0.762168] Performance Events: AMD Family 15h PMU driver.
[    0.762171] ... version:                0
[    0.762172] ... bit width:              48
[    0.762173] ... generic registers:      6
[    0.762174] ... value mask:             0000ffffffffffff
[    0.762175] ... max period:             00007fffffffffff
[    0.762176] ... fixed-purpose events:   0
[    0.762177] ... event mask:             000000000000003f
[    0.762274] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.762364] Booting Node   0, Processors  #1 #2 #3 #4 #5
[    0.828039] Brought up 6 CPUs
[    0.828041] Total of 6 processors activated (45906.18 BogoMIPS).
[    0.837590] devtmpfs: initialized
[    0.838992] EVM: security.selinux
[    0.838993] EVM: security.SMACK64
[    0.838994] EVM: security.capability
[    0.839043] PM: Registering ACPI NVS region [mem 0xcfda0000-0xcfdd0fff] (200704 bytes)
[    0.839673] dummy: 
[    0.839695] RTC time: 17:10:12, date: 11/02/13
[    0.839724] NET: Registered protocol family 16
[    0.839833] Trying to unpack rootfs image as initramfs...
[    0.839907] ACPI: bus type pci registered
[    0.839950] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.839952] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.853558] PCI: Using configuration type 1 for base access
[    0.854535] bio: create slab <bio-0> at 0
[    0.854609] ACPI: Added _OSI(Module Device)
[    0.854611] ACPI: Added _OSI(Processor Device)
[    0.854612] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.854613] ACPI: Added _OSI(Processor Aggregator Device)
[    0.855462] ACPI: EC: Look up EC in DSDT
[    0.863404] ACPI Warning: Incorrect checksum in table [TAMG] - 0xD2, should be 0xD1 (20120320/tbutils-323)
[    0.863540] ACPI: Interpreter enabled
[    0.863544] ACPI: (supports S0 S3 S4 S5)
[    0.863563] ACPI: Using IOAPIC for interrupt routing
[    0.995720] ACPI: No dock devices found.
[    0.995725] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.995777] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.995858] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.995861] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.995863] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.995864] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.995866] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.995868] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xfebfffff]
[    0.995897] PCI host bridge to bus 0000:00
[    0.995899] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.995901] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.995902] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.995904] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.995906] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff]
[    0.995907] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xfebfffff]
[    0.995918] pci 0000:00:00.0: [1002:5a14] type 00 class 0x060000
[    0.995930] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.995979] pci 0000:00:02.0: [1002:5a16] type 01 class 0x060400
[    0.996011] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.996029] pci 0000:00:09.0: [1002:5a1c] type 01 class 0x060400
[    0.996061] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.996073] pci 0000:00:0a.0: [1002:5a1d] type 01 class 0x060400
[    0.996104] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.996125] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
[    0.996140] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
[    0.996147] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
[    0.996154] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
[    0.996161] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
[    0.996169] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
[    0.996176] pci 0000:00:11.0: reg 24: [mem 0xfdfff000-0xfdfff3ff]
[    0.996191] pci 0000:00:11.0: set SATA to AHCI mode
[    0.996228] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.996238] pci 0000:00:12.0: reg 10: [mem 0xfdffe000-0xfdffefff]
[    0.996291] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.996305] pci 0000:00:12.2: reg 10: [mem 0xfdffd000-0xfdffd0ff]
[    0.996366] pci 0000:00:12.2: supports D1 D2
[    0.996368] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.996386] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.996396] pci 0000:00:13.0: reg 10: [mem 0xfdffc000-0xfdffcfff]
[    0.996450] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.996464] pci 0000:00:13.2: reg 10: [mem 0xfdffb000-0xfdffb0ff]
[    0.996525] pci 0000:00:13.2: supports D1 D2
[    0.996527] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.996544] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.996599] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.996609] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.996616] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.996623] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.996630] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.996637] pci 0000:00:14.1: reg 20: [io  0xfa00-0xfa0f]
[    0.996666] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.996682] pci 0000:00:14.2: reg 10: [mem 0xfdff4000-0xfdff7fff 64bit]
[    0.996731] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.996742] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.996799] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.996830] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.996840] pci 0000:00:14.5: reg 10: [mem 0xfdffa000-0xfdffafff]
[    0.996893] pci 0000:00:15.0: [1002:43a0] type 01 class 0x060400
[    0.996947] pci 0000:00:15.0: supports D1 D2
[    0.996966] pci 0000:00:15.1: [1002:43a1] type 01 class 0x060400
[    0.997019] pci 0000:00:15.1: supports D1 D2
[    0.997037] pci 0000:00:15.2: [1002:43a2] type 01 class 0x060400
[    0.997090] pci 0000:00:15.2: supports D1 D2
[    0.997108] pci 0000:00:15.3: [1002:43a3] type 01 class 0x060400
[    0.997161] pci 0000:00:15.3: supports D1 D2
[    0.997180] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    0.997190] pci 0000:00:16.0: reg 10: [mem 0xfdff9000-0xfdff9fff]
[    0.997243] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    0.997257] pci 0000:00:16.2: reg 10: [mem 0xfdff8000-0xfdff80ff]
[    0.997318] pci 0000:00:16.2: supports D1 D2
[    0.997320] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.997337] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
[    0.997355] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
[    0.997369] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
[    0.997385] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
[    0.997403] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
[    0.997416] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
[    0.997468] pci 0000:01:00.0: [10de:0614] type 00 class 0x030000
[    0.997477] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.997486] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.997495] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit]
[    0.997502] pci 0000:01:00.0: reg 24: [io  0xef00-0xef7f]
[    0.997508] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    1.001572] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    1.001576] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    1.001578] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    1.001582] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.001615] pci 0000:02:00.0: [1b6f:7023] type 00 class 0x0c0330
[    1.001629] pci 0000:02:00.0: reg 10: [mem 0xfd1f8000-0xfd1fffff 64bit]
[    1.001695] pci 0000:02:00.0: supports D1 D2
[    1.001696] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.009551] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    1.009555] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    1.009557] pci 0000:00:09.0:   bridge window [mem 0xfd100000-0xfd1fffff]
[    1.009560] pci 0000:00:09.0:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    1.009590] pci 0000:03:00.0: [1b4b:917a] type 00 class 0x01018f
[    1.009600] pci 0000:03:00.0: reg 10: [io  0xcf00-0xcf07]
[    1.009606] pci 0000:03:00.0: reg 14: [io  0xce00-0xce03]
[    1.009612] pci 0000:03:00.0: reg 18: [io  0xcd00-0xcd07]
[    1.009619] pci 0000:03:00.0: reg 1c: [io  0xcc00-0xcc03]
[    1.009625] pci 0000:03:00.0: reg 20: [io  0xcb00-0xcb0f]
[    1.009632] pci 0000:03:00.0: reg 24: [mem 0xfdbff000-0xfdbff1ff]
[    1.009638] pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    1.009667] pci 0000:03:00.0: PME# supported from D3hot
[    1.017529] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    1.017533] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
[    1.017535] pci 0000:00:0a.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    1.017538] pci 0000:00:0a.0:   bridge window [mem 0xfd200000-0xfd2fffff 64bit pref]
[    1.017566] pci 0000:04:06.0: [10ec:8169] type 00 class 0x020000
[    1.017583] pci 0000:04:06.0: reg 10: [io  0xbc00-0xbcff]
[    1.017593] pci 0000:04:06.0: reg 14: [mem 0xfddff000-0xfddff0ff]
[    1.017636] pci 0000:04:06.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    1.017665] pci 0000:04:06.0: supports D1 D2
[    1.017667] pci 0000:04:06.0: PME# supported from D1 D2 D3hot D3cold
[    1.017695] pci 0000:04:0e.0: [1106:3044] type 00 class 0x0c0010
[    1.017714] pci 0000:04:0e.0: reg 10: [mem 0xfddfe000-0xfddfe7ff]
[    1.017724] pci 0000:04:0e.0: reg 14: [io  0xbf00-0xbf7f]
[    1.017799] pci 0000:04:0e.0: supports D2
[    1.017800] pci 0000:04:0e.0: PME# supported from D2 D3hot D3cold
[    1.017831] pci 0000:00:14.4: PCI bridge to [bus 04-04] (subtractive decode)
[    1.017835] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    1.017838] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    1.017841] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    1.017843] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.017845] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.017846] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.017851] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    1.017852] pci 0000:00:14.4:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
[    1.017854] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xfebfffff] (subtractive decode)
[    1.017906] pci 0000:05:00.0: [10ec:8168] type 00 class 0x020000
[    1.017921] pci 0000:05:00.0: reg 10: [io  0xae00-0xaeff]
[    1.017946] pci 0000:05:00.0: reg 18: [mem 0xfd9ff000-0xfd9fffff 64bit pref]
[    1.017961] pci 0000:05:00.0: reg 20: [mem 0xfd9f8000-0xfd9fbfff 64bit pref]
[    1.018029] pci 0000:05:00.0: supports D1 D2
[    1.018030] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.025512] pci 0000:00:15.0: PCI bridge to [bus 05-05]
[    1.025517] pci 0000:00:15.0:   bridge window [io  0xa000-0xafff]
[    1.025520] pci 0000:00:15.0:   bridge window [mem 0xfda00000-0xfdafffff]
[    1.025525] pci 0000:00:15.0:   bridge window [mem 0xfd900000-0xfd9fffff 64bit pref]
[    1.025575] pci 0000:06:00.0: [1b6f:7023] type 00 class 0x0c0330
[    1.025595] pci 0000:06:00.0: reg 10: [mem 0xfd8f8000-0xfd8fffff 64bit]
[    1.025683] pci 0000:06:00.0: supports D1 D2
[    1.025685] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.033492] pci 0000:00:15.1: PCI bridge to [bus 06-06]
[    1.033497] pci 0000:00:15.1:   bridge window [io  0x9000-0x9fff]
[    1.033500] pci 0000:00:15.1:   bridge window [mem 0xfd800000-0xfd8fffff]
[    1.033504] pci 0000:00:15.1:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
[    1.033539] pci 0000:00:15.2: PCI bridge to [bus 07-07]
[    1.033544] pci 0000:00:15.2:   bridge window [io  0x8000-0x8fff]
[    1.033546] pci 0000:00:15.2:   bridge window [mem 0xfd600000-0xfd6fffff]
[    1.033551] pci 0000:00:15.2:   bridge window [mem 0xfd500000-0xfd5fffff 64bit pref]
[    1.033585] pci 0000:00:15.3: PCI bridge to [bus 08-08]
[    1.033589] pci 0000:00:15.3:   bridge window [io  0x7000-0x7fff]
[    1.033592] pci 0000:00:15.3:   bridge window [mem 0xfd400000-0xfd4fffff]
[    1.033596] pci 0000:00:15.3:   bridge window [mem 0xfd300000-0xfd3fffff 64bit pref]
[    1.033620] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.033903] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    1.033932] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    1.033961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    1.033988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    1.034020] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    1.034063] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    1.034101] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[    1.034129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    1.034161]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.034164]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    1.034165] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.045757] Freeing initrd memory: 15512k freed
[    1.048025] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0
[    1.048065] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0
[    1.048102] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0
[    1.048139] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0
[    1.048175] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0
[    1.048211] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0
[    1.048247] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0
[    1.048282] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0
[    1.048387] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.048390] vgaarb: loaded
[    1.048392] vgaarb: bridge control possible 0000:01:00.0
[    1.048544] SCSI subsystem initialized
[    1.048599] libata version 3.00 loaded.
[    1.048619] ACPI: bus type usb registered
[    1.048634] usbcore: registered new interface driver usbfs
[    1.048643] usbcore: registered new interface driver hub
[    1.048668] usbcore: registered new device driver usb
[    1.048735] PCI: Using ACPI for IRQ routing
[    1.054830] PCI: pci_cache_line_size set to 64 bytes
[    1.054840] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    1.054924] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    1.054926] e820: reserve RAM buffer [mem 0xcfda0000-0xcfffffff]
[    1.054927] e820: reserve RAM buffer [mem 0x22f000000-0x22fffffff]
[    1.055001] NetLabel: Initializing
[    1.055002] NetLabel:  domain hash size = 128
[    1.055003] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.055011] NetLabel:  unlabeled traffic allowed by default
[    1.055063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.055067] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    1.057101] Switching to clocksource hpet
[    1.062881] AppArmor: AppArmor Filesystem Enabled
[    1.062895] pnp: PnP ACPI init
[    1.062908] ACPI: bus type pnp registered
[    1.062979] pnp 00:00: [bus 00-ff]
[    1.062981] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.062983] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.062985] pnp 00:00: [io  0x0d00-0xffff window]
[    1.062987] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.062988] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    1.062990] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.062991] pnp 00:00: [mem 0xd0000000-0xfebfffff window]
[    1.063026] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.063036] pnp 00:01: [io  0x0010-0x001f]
[    1.063038] pnp 00:01: [io  0x0022-0x003f]
[    1.063039] pnp 00:01: [io  0x0044-0x004d]
[    1.063040] pnp 00:01: [io  0x0050-0x005f]
[    1.063042] pnp 00:01: [io  0x0062-0x0063]
[    1.063043] pnp 00:01: [io  0x0065-0x006f]
[    1.063046] pnp 00:01: [io  0x0074-0x007f]
[    1.063048] pnp 00:01: [io  0x0091-0x0093]
[    1.063049] pnp 00:01: [io  0x00a2-0x00bf]
[    1.063050] pnp 00:01: [io  0x00e0-0x00ef]
[    1.063052] pnp 00:01: [io  0x04d0-0x04d1]
[    1.063053] pnp 00:01: [io  0x0220-0x0225]
[    1.063055] pnp 00:01: [io  0x0290-0x0294]
[    1.063101] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    1.063103] system 00:01: [io  0x0220-0x0225] has been reserved
[    1.063105] system 00:01: [io  0x0290-0x0294] has been reserved
[    1.063107] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.063606] pnp 00:02: [io  0x0900-0x091f]
[    1.063609] pnp 00:02: [io  0x0228-0x022f]
[    1.063611] pnp 00:02: [io  0x040b]
[    1.063613] pnp 00:02: [io  0x04d6]
[    1.063614] pnp 00:02: [io  0x0c00-0x0c01]
[    1.063615] pnp 00:02: [io  0x0c14]
[    1.063617] pnp 00:02: [io  0x0c50-0x0c52]
[    1.063618] pnp 00:02: [io  0x0c6c-0x0c6d]
[    1.063620] pnp 00:02: [io  0x0c6f]
[    1.063621] pnp 00:02: [io  0x0cd0-0x0cd1]
[    1.063622] pnp 00:02: [io  0x0cd2-0x0cd3]
[    1.063624] pnp 00:02: [io  0x0cd4-0x0cdf]
[    1.063625] pnp 00:02: [io  0x0800-0x08fe]
[    1.063626] pnp 00:02: [io  0x0a10-0x0a17]
[    1.063628] pnp 00:02: [io  0x0b00-0x0b0f]
[    1.063629] pnp 00:02: [io  0x0b10-0x0b1f]
[    1.063630] pnp 00:02: [io  0x0b20-0x0b3f]
[    1.063632] pnp 00:02: [mem 0x00000000-0x00000fff window]
[    1.063634] pnp 00:02: [mem 0xfee00400-0xfee00fff window]
[    1.063639] pnp 00:02: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.063671] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    1.063678] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:03:00.0 BAR 6 [mem 0x00000000-0x0000ffff pref]
[    1.063681] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:04:06.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    1.063719] system 00:02: [io  0x0900-0x091f] has been reserved
[    1.063722] system 00:02: [io  0x0228-0x022f] has been reserved
[    1.063723] system 00:02: [io  0x040b] has been reserved
[    1.063725] system 00:02: [io  0x04d6] has been reserved
[    1.063727] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    1.063729] system 00:02: [io  0x0c14] has been reserved
[    1.063730] system 00:02: [io  0x0c50-0x0c52] has been reserved
[    1.063732] system 00:02: [io  0x0c6c-0x0c6d] has been reserved
[    1.063734] system 00:02: [io  0x0c6f] has been reserved
[    1.063736] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    1.063737] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    1.063739] system 00:02: [io  0x0cd4-0x0cdf] has been reserved
[    1.063741] system 00:02: [io  0x0800-0x08fe] has been reserved
[    1.063743] system 00:02: [io  0x0a10-0x0a17] has been reserved
[    1.063744] system 00:02: [io  0x0b00-0x0b0f] has been reserved
[    1.063746] system 00:02: [io  0x0b10-0x0b1f] has been reserved
[    1.063748] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    1.063750] system 00:02: [mem 0xfee00400-0xfee00fff window] has been reserved
[    1.063753] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.063840] pnp 00:03: [dma 4]
[    1.063842] pnp 00:03: [io  0x0000-0x000f]
[    1.063843] pnp 00:03: [io  0x0080-0x0090]
[    1.063845] pnp 00:03: [io  0x0094-0x009f]
[    1.063846] pnp 00:03: [io  0x00c0-0x00df]
[    1.063871] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.063920] pnp 00:04: [irq 0 disabled]
[    1.063933] pnp 00:04: [irq 8]
[    1.063935] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    1.063959] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.063985] pnp 00:05: [io  0x0070-0x0073]
[    1.064010] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.064017] pnp 00:06: [io  0x0061]
[    1.064039] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.064046] pnp 00:07: [io  0x00f0-0x00ff]
[    1.064049] pnp 00:07: [irq 13]
[    1.064073] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.064338] pnp 00:08: [io  0x03f8-0x03ff]
[    1.064341] pnp 00:08: [irq 4]
[    1.064385] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    1.064439] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    1.064488] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    1.064490] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.064630] pnp 00:0a: [mem 0x000cd200-0x000cffff]
[    1.064631] pnp 00:0a: [mem 0x000f0000-0x000f7fff]
[    1.064633] pnp 00:0a: [mem 0x000f8000-0x000fbfff]
[    1.064634] pnp 00:0a: [mem 0x000fc000-0x000fffff]
[    1.064636] pnp 00:0a: [mem 0xcfda0000-0xcfdfffff]
[    1.064637] pnp 00:0a: [mem 0xffff0000-0xffffffff]
[    1.064639] pnp 00:0a: [mem 0x00000000-0x0009ffff]
[    1.064640] pnp 00:0a: [mem 0x00100000-0xcfd9ffff]
[    1.064641] pnp 00:0a: [mem 0xcfe00000-0xcfefffff]
[    1.064643] pnp 00:0a: [mem 0xcff00000-0xcfffffff]
[    1.064644] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    1.064646] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    1.064647] pnp 00:0a: [mem 0xfff80000-0xfffeffff]
[    1.064650] pnp 00:0a: disabling [mem 0x000cd200-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.064652] pnp 00:0a: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.064654] pnp 00:0a: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.064656] pnp 00:0a: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.064658] pnp 00:0a: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.064660] pnp 00:0a: disabling [mem 0x00100000-0xcfd9ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.064720] system 00:0a: [mem 0xcfda0000-0xcfdfffff] could not be reserved
[    1.064722] system 00:0a: [mem 0xffff0000-0xffffffff] has been reserved
[    1.064724] system 00:0a: [mem 0xcfe00000-0xcfefffff] has been reserved
[    1.064726] system 00:0a: [mem 0xcff00000-0xcfffffff] could not be reserved
[    1.064728] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    1.064730] system 00:0a: [mem 0xfee00000-0xfee00fff] could not be reserved
[    1.064732] system 00:0a: [mem 0xfff80000-0xfffeffff] has been reserved
[    1.064734] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.064751] pnp: PnP ACPI: found 11 devices
[    1.064752] ACPI: ACPI bus type pnp unregistered
[    1.070977] pci 0000:01:00.0: BAR 6: assigned [mem 0xfb000000-0xfb01ffff pref]
[    1.070980] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    1.070982] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    1.070985] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    1.070988] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.070991] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    1.070992] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    1.070995] pci 0000:00:09.0:   bridge window [mem 0xfd100000-0xfd1fffff]
[    1.070998] pci 0000:00:09.0:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    1.071001] pci 0000:03:00.0: BAR 6: assigned [mem 0xfd200000-0xfd20ffff pref]
[    1.071003] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    1.071005] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
[    1.071007] pci 0000:00:0a.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    1.071010] pci 0000:00:0a.0:   bridge window [mem 0xfd200000-0xfd2fffff 64bit pref]
[    1.071013] pci 0000:04:06.0: BAR 6: assigned [mem 0xfdc00000-0xfdc1ffff pref]
[    1.071015] pci 0000:00:14.4: PCI bridge to [bus 04-04]
[    1.071017] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    1.071021] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    1.071024] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    1.071029] pci 0000:00:15.0: PCI bridge to [bus 05-05]
[    1.071031] pci 0000:00:15.0:   bridge window [io  0xa000-0xafff]
[    1.071034] pci 0000:00:15.0:   bridge window [mem 0xfda00000-0xfdafffff]
[    1.071037] pci 0000:00:15.0:   bridge window [mem 0xfd900000-0xfd9fffff 64bit pref]
[    1.071041] pci 0000:00:15.1: PCI bridge to [bus 06-06]
[    1.071043] pci 0000:00:15.1:   bridge window [io  0x9000-0x9fff]
[    1.071047] pci 0000:00:15.1:   bridge window [mem 0xfd800000-0xfd8fffff]
[    1.071050] pci 0000:00:15.1:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
[    1.071054] pci 0000:00:15.2: PCI bridge to [bus 07-07]
[    1.071056] pci 0000:00:15.2:   bridge window [io  0x8000-0x8fff]
[    1.071059] pci 0000:00:15.2:   bridge window [mem 0xfd600000-0xfd6fffff]
[    1.071062] pci 0000:00:15.2:   bridge window [mem 0xfd500000-0xfd5fffff 64bit pref]
[    1.071066] pci 0000:00:15.3: PCI bridge to [bus 08-08]
[    1.071068] pci 0000:00:15.3:   bridge window [io  0x7000-0x7fff]
[    1.071071] pci 0000:00:15.3:   bridge window [mem 0xfd400000-0xfd4fffff]
[    1.071074] pci 0000:00:15.3:   bridge window [mem 0xfd300000-0xfd3fffff 64bit pref]
[    1.071108] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.071110] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.071112] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.071113] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    1.071115] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    1.071117] pci_bus 0000:00: resource 9 [mem 0xd0000000-0xfebfffff]
[    1.071118] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    1.071120] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbffffff]
[    1.071121] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.071123] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    1.071125] pci_bus 0000:02: resource 1 [mem 0xfd100000-0xfd1fffff]
[    1.071126] pci_bus 0000:02: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
[    1.071128] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    1.071130] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    1.071131] pci_bus 0000:03: resource 2 [mem 0xfd200000-0xfd2fffff 64bit pref]
[    1.071133] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
[    1.071135] pci_bus 0000:04: resource 1 [mem 0xfdd00000-0xfddfffff]
[    1.071136] pci_bus 0000:04: resource 2 [mem 0xfdc00000-0xfdcfffff pref]
[    1.071138] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    1.071139] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    1.071141] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    1.071143] pci_bus 0000:04: resource 7 [mem 0x000c0000-0x000dffff]
[    1.071144] pci_bus 0000:04: resource 8 [mem 0xfed40000-0xfed44fff]
[    1.071146] pci_bus 0000:04: resource 9 [mem 0xd0000000-0xfebfffff]
[    1.071147] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    1.071149] pci_bus 0000:05: resource 1 [mem 0xfda00000-0xfdafffff]
[    1.071151] pci_bus 0000:05: resource 2 [mem 0xfd900000-0xfd9fffff 64bit pref]
[    1.071152] pci_bus 0000:06: resource 0 [io  0x9000-0x9fff]
[    1.071154] pci_bus 0000:06: resource 1 [mem 0xfd800000-0xfd8fffff]
[    1.071156] pci_bus 0000:06: resource 2 [mem 0xfd700000-0xfd7fffff 64bit pref]
[    1.071157] pci_bus 0000:07: resource 0 [io  0x8000-0x8fff]
[    1.071159] pci_bus 0000:07: resource 1 [mem 0xfd600000-0xfd6fffff]
[    1.071160] pci_bus 0000:07: resource 2 [mem 0xfd500000-0xfd5fffff 64bit pref]
[    1.071162] pci_bus 0000:08: resource 0 [io  0x7000-0x7fff]
[    1.071164] pci_bus 0000:08: resource 1 [mem 0xfd400000-0xfd4fffff]
[    1.071165] pci_bus 0000:08: resource 2 [mem 0xfd300000-0xfd3fffff 64bit pref]
[    1.071186] NET: Registered protocol family 2
[    1.071349] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.072229] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.073877] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.074067] TCP: Hash tables configured (established 524288 bind 65536)
[    1.074068] TCP: reno registered
[    1.074079] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.074114] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.074180] NET: Registered protocol family 1
[    1.360438] pci 0000:01:00.0: Boot video device
[    1.360510] PCI: CLS 64 bytes, default 64
[    1.360865] PCI-DMA: Disabling AGP.
[    1.360933] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.360934] PCI-DMA: using GART IOMMU.
[    1.360936] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.364968] LVT offset 0 assigned for vector 0x400
[    1.364995] perf: AMD IBS detected (0x000000ff)
[    1.365163] audit: initializing netlink socket (disabled)
[    1.365172] type=2000 audit(1383412211.664:1): initialized
[    1.382910] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.384680] VFS: Disk quotas dquot_6.5.2
[    1.384710] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.385091] fuse init (API version 7.19)
[    1.385156] msgmni has been set to 15929
[    1.385464] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.385490] io scheduler noop registered
[    1.385493] io scheduler deadline registered (default)
[    1.385513] io scheduler cfq registered
[    1.385777] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.385789] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.385876] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.385879] ACPI: Power Button [PWRB]
[    1.385912] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.385914] ACPI: Power Button [PWRF]
[    1.385954] ACPI: acpi_idle registered with cpuidle
[    1.388977] GHES: HEST is not enabled!
[    1.389037] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.409325] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.430539] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.430733] Linux agpgart interface v0.103
[    1.431764] brd: module loaded
[    1.432342] loop: module loaded
[    1.432673] Fixed MDIO Bus: probed
[    1.432707] tun: Universal TUN/TAP device driver, 1.6
[    1.432708] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.432740] PPP generic driver version 2.4.2
[    1.432775] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.432812] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.432817] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.432823] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.432839] QUIRK: Enable AMD PLL fix
[    1.432848] ehci_hcd 0000:00:12.2: debug port 1
[    1.432865] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfdffd000
[    1.444169] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.444185] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.444187] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.444189] usb usb1: Product: EHCI Host Controller
[    1.444190] usb usb1: Manufacturer: Linux 3.5.0-42-generic ehci_hcd
[    1.444192] usb usb1: SerialNumber: 0000:00:12.2
[    1.444276] hub 1-0:1.0: USB hub found
[    1.444279] hub 1-0:1.0: 5 ports detected
[    1.444345] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.444349] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.444354] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.444368] ehci_hcd 0000:00:13.2: debug port 1
[    1.444377] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfdffb000
[    1.456138] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.456155] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.456157] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.456158] usb usb2: Product: EHCI Host Controller
[    1.456160] usb usb2: Manufacturer: Linux 3.5.0-42-generic ehci_hcd
[    1.456161] usb usb2: SerialNumber: 0000:00:13.2
[    1.456234] hub 2-0:1.0: USB hub found
[    1.456237] hub 2-0:1.0: 5 ports detected
[    1.456301] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.456306] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.456311] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.456325] ehci_hcd 0000:00:16.2: debug port 1
[    1.456334] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfdff8000
[    1.468108] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.468125] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.468126] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.468128] usb usb3: Product: EHCI Host Controller
[    1.468129] usb usb3: Manufacturer: Linux 3.5.0-42-generic ehci_hcd
[    1.468131] usb usb3: SerialNumber: 0000:00:16.2
[    1.468204] hub 3-0:1.0: USB hub found
[    1.468207] hub 3-0:1.0: 4 ports detected
[    1.468264] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.468286] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.468290] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.468307] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfdffe000
[    1.527939] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.527941] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.527942] usb usb4: Product: OHCI Host Controller
[    1.527944] usb usb4: Manufacturer: Linux 3.5.0-42-generic ohci_hcd
[    1.527945] usb usb4: SerialNumber: 0000:00:12.0
[    1.528021] hub 4-0:1.0: USB hub found
[    1.528026] hub 4-0:1.0: 5 ports detected
[    1.528093] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.528097] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.528108] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfdffc000
[    1.587788] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.587791] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.587792] usb usb5: Product: OHCI Host Controller
[    1.587794] usb usb5: Manufacturer: Linux 3.5.0-42-generic ohci_hcd
[    1.587795] usb usb5: SerialNumber: 0000:00:13.0
[    1.587873] hub 5-0:1.0: USB hub found
[    1.587878] hub 5-0:1.0: 5 ports detected
[    1.587944] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.587947] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.587959] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfdffa000
[    1.647636] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.647638] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.647640] usb usb6: Product: OHCI Host Controller
[    1.647641] usb usb6: Manufacturer: Linux 3.5.0-42-generic ohci_hcd
[    1.647642] usb usb6: SerialNumber: 0000:00:14.5
[    1.647719] hub 6-0:1.0: USB hub found
[    1.647723] hub 6-0:1.0: 2 ports detected
[    1.647787] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.647791] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.647803] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfdff9000
[    1.707488] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.707490] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.707492] usb usb7: Product: OHCI Host Controller
[    1.707493] usb usb7: Manufacturer: Linux 3.5.0-42-generic ohci_hcd
[    1.707495] usb usb7: SerialNumber: 0000:00:16.0
[    1.707572] hub 7-0:1.0: USB hub found
[    1.707577] hub 7-0:1.0: 4 ports detected
[    1.707631] uhci_hcd: USB Universal Host Controller Interface driver
[    1.707669] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.707673] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    1.707776] xhci_hcd 0000:02:00.0: irq 40 for MSI/MSI-X
[    1.707817] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.707819] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.707821] usb usb8: Product: xHCI Host Controller
[    1.707822] usb usb8: Manufacturer: Linux 3.5.0-42-generic xhci_hcd
[    1.707824] usb usb8: SerialNumber: 0000:02:00.0
[    1.707874] xHCI xhci_add_endpoint called for root hub
[    1.707875] xHCI xhci_check_bandwidth called for root hub
[    1.707892] hub 8-0:1.0: USB hub found
[    1.707896] hub 8-0:1.0: 2 ports detected
[    1.707941] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.707944] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    1.707961] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.707962] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.707964] usb usb9: Product: xHCI Host Controller
[    1.707965] usb usb9: Manufacturer: Linux 3.5.0-42-generic xhci_hcd
[    1.707966] usb usb9: SerialNumber: 0000:02:00.0
[    1.708017] xHCI xhci_add_endpoint called for root hub
[    1.708018] xHCI xhci_check_bandwidth called for root hub
[    1.708033] hub 9-0:1.0: USB hub found
[    1.708038] hub 9-0:1.0: 2 ports detected
[    1.708127] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.708133] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 10
[    1.708270] xhci_hcd 0000:06:00.0: irq 41 for MSI/MSI-X
[    1.708321] usb usb10: New USB device found, idVendor=1d6b, idProduct=0002
[    1.708323] usb usb10: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.708325] usb usb10: Product: xHCI Host Controller
[    1.708326] usb usb10: Manufacturer: Linux 3.5.0-42-generic xhci_hcd
[    1.708328] usb usb10: SerialNumber: 0000:06:00.0
[    1.708384] xHCI xhci_add_endpoint called for root hub
[    1.708385] xHCI xhci_check_bandwidth called for root hub
[    1.708404] hub 10-0:1.0: USB hub found
[    1.708410] hub 10-0:1.0: 2 ports detected
[    1.708460] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.708464] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 11
[    1.708484] usb usb11: New USB device found, idVendor=1d6b, idProduct=0003
[    1.708485] usb usb11: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.708487] usb usb11: Product: xHCI Host Controller
[    1.708489] usb usb11: Manufacturer: Linux 3.5.0-42-generic xhci_hcd
[    1.708490] usb usb11: SerialNumber: 0000:06:00.0
[    1.708540] xHCI xhci_add_endpoint called for root hub
[    1.708541] xHCI xhci_check_bandwidth called for root hub
[    1.708557] hub 11-0:1.0: USB hub found
[    1.708562] hub 11-0:1.0: 2 ports detected
[    1.708703] usbcore: registered new interface driver libusual
[    1.708728] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.742704] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.742705] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    1.934920] usb 2-4: new high-speed USB device number 4 using ehci_hcd
[    1.990849] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.990944] mousedev: PS/2 mouse device common for all mice
[    1.991051] rtc_cmos 00:05: RTC can wake from S4
[    1.991135] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.991152] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.991203] device-mapper: uevent: version 1.0.3
[    1.991253] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.991315] cpuidle: using governor ladder
[    1.991412] cpuidle: using governor menu
[    1.991413] EFI Variables Facility v0.08 2004-May-17
[    1.991572] ashmem: initialized
[    1.991663] TCP: cubic registered
[    1.991734] NET: Registered protocol family 10
[    1.991865] NET: Registered protocol family 17
[    1.991872] Key type dns_resolver registered
[    1.991978] PM: Hibernation image not present or could not be loaded.
[    1.991985] registered taskstats version 1
[    1.994358] Key type trusted registered
[    1.996386] Key type encrypted registered
[    1.998554]   Magic number: 5:599:187
[    1.998614] rtc_cmos 00:05: setting system clock to 2013-11-02 17:10:13 UTC (1383412213)
[    1.998666] powernow-k8: Found 1 AMD FX(tm)-6200 Six-Core Processor              (6 cpu cores) (version 2.20.00)
[    1.998681] powernow-k8: Core Performance Boosting: on.
[    1.998723] powernow-k8:    0 : pstate 0 (3800 MHz)
[    1.998724] powernow-k8:    1 : pstate 1 (3500 MHz)
[    1.998741] powernow-k8:    2 : pstate 2 (3100 MHz)
[    1.998742] powernow-k8:    3 : pstate 3 (2500 MHz)
[    1.998743] powernow-k8:    4 : pstate 4 (1900 MHz)
[    1.998744] powernow-k8:    5 : pstate 5 (1400 MHz)
[    1.999338] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.999340] EDD information not available.
[    2.001479] Freeing unused kernel memory: 948k freed
[    2.001636] Write protecting the kernel read-only data: 12288k
[    2.007200] Freeing unused kernel memory: 1356k freed
[    2.011240] Freeing unused kernel memory: 1060k freed
[    2.025091] udevd[109]: starting version 175
[    2.034502] xor: automatically using best checksumming function:
[    2.044580] ahci 0000:00:11.0: version 3.0
[    2.044680] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.044683] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.047449] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.047491] r8169 0000:04:06.0: (unregistered net_device): not PCI Express
[    2.047649] r8169 0000:04:06.0: eth0: RTL8169sb/8110sb at 0xffffc900117aa000, 64:70:02:11:80:c9, XID 10000000 IRQ 20
[    2.047652] r8169 0000:04:06.0: eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
[    2.048044] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.048146] r8169 0000:05:00.0: irq 42 for MSI/MSI-X
[    2.048238] scsi0 : ahci
[    2.048350] r8169 0000:05:00.0: eth1: RTL8168evl/8111evl at 0xffffc900117b4000, 90:2b:34:93:7e:55, XID 0c900800 IRQ 42
[    2.048355] r8169 0000:05:00.0: eth1: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.049204] scsi1 : ahci
[    2.049388] scsi2 : ahci
[    2.050126] scsi3 : ahci
[    2.050266] ata1: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff100 irq 19
[    2.050269] ata2: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff180 irq 19
[    2.050272] ata3: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff200 irq 19
[    2.050274] ata4: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff280 irq 19
[    2.050375] ahci 0000:03:00.0: irq 43 for MSI/MSI-X
[    2.050419] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl IDE mode
[    2.050423] ahci 0000:03:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
[    2.050801] scsi4 : ahci
[    2.050924] scsi5 : ahci
[    2.050973] ata5: SATA max UDMA/133 abar m512@0xfdbff000 port 0xfdbff100 irq 43
[    2.050976] ata6: SATA max UDMA/133 abar m512@0xfdbff000 port 0xfdbff180 irq 43
[    2.052213] scsi6 : pata_atiixp
[    2.052348] scsi7 : pata_atiixp
[    2.052951] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    2.052953] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    2.068238] usb 2-4: New USB device found, idVendor=03f0, idProduct=a011
[    2.068243] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.068245] usb 2-4: Product: Deskjet 3050A J611 series
[    2.068248] usb 2-4: Manufacturer: HP
[    2.068251] usb 2-4: SerialNumber: CN239540V805PJ
[    2.070558]    avx       :  7746.000 MB/sec
[    2.228039] ata7.01: ATAPI: ASUS    DRW-24B1ST   c, 1.05, max UDMA/100
[    2.228049] ata7.01: limited to UDMA/33 due to 40-wire cable
[    2.242556] ata7.01: configured for UDMA/33
[    2.361922] Refined TSC clocksource calibration: 3825.543 MHz.
[    2.361941] Switching to clocksource tsc
[    2.369916] ata3: SATA link down (SStatus 0 SControl 300)
[    2.369926] ata6: SATA link down (SStatus 0 SControl 300)
[    2.369959] ata5: SATA link down (SStatus 0 SControl 300)
[    2.369964] ata4: SATA link down (SStatus 0 SControl 300)
[    2.369993] ata2: SATA link down (SStatus 0 SControl 300)
[    2.537546] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.539629] ata1.00: ATA-8: WDC WD5000AAKX-001CA0, 15.01H15, max UDMA/133
[    2.539631] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.541419] ata1.00: configured for UDMA/133
[    2.541656] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKX-0 15.0 PQ: 0 ANSI: 5
[    2.541772] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.541789] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.541875] sd 0:0:0:0: [sda] Write Protect is off
[    2.541878] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.541928] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.569471] usb 5-2: new low-speed USB device number 2 using ohci_hcd
[    2.580951]  sda: sda1 sda2 < sda5 >
[    2.581535] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.584932] scsi 6:0:1:0: CD-ROM            ASUS     DRW-24B1ST   c   1.05 PQ: 0 ANSI: 5
[    2.588806] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.588809] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.589010] sr 6:0:1:0: Attached scsi CD-ROM sr0
[    2.589078] sr 6:0:1:0: Attached scsi generic sg1 type 5
[    2.589890] device-mapper: dm-raid45: initialized v0.2594b
[    2.653152] firewire_ohci 0000:04:0e.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    2.736927] usb 5-2: New USB device found, idVendor=046d, idProduct=c517
[    2.736930] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.736932] usb 5-2: Product: USB Receiver
[    2.736934] usb 5-2: Manufacturer: Logitech
[    2.752936] usbcore: registered new interface driver usbhid
[    2.752939] usbhid: USB HID core driver
[    2.754970] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input2
[    2.755057] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-2/input0
[    2.755065] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    2.755570] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.1/input/input3
[    2.755986] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2/input1
[    2.896359] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[    3.000318] usb 5-3: new full-speed USB device number 3 using ohci_hcd
[    3.152137] firewire_core 0000:04:0e.0: created device fw0: GUID 0049e550485c0900, S400
[    3.172929] usb 5-3: New USB device found, idVendor=046d, idProduct=c52b
[    3.172936] usb 5-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.172942] usb 5-3: Product: USB Receiver
[    3.172947] usb 5-3: Manufacturer: Logitech
[    3.451173] usb 7-4: new full-speed USB device number 2 using ohci_hcd
[    3.619799] usb 7-4: New USB device found, idVendor=058f, idProduct=9360
[    3.619807] usb 7-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.619813] usb 7-4: Product: USB Reader
[    3.619817] usb 7-4: Manufacturer:  
[    3.619821] usb 7-4: SerialNumber: 2004888
[    4.811519] Initializing USB Mass Storage driver...
[    4.811714] scsi8 : usb-storage 7-4:1.0
[    4.811758] usbcore: registered new interface driver usb-storage
[    4.811760] USB Mass Storage support registered.
[    5.816268] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    5.822340] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    5.828323] scsi 8:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    5.834308] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    5.835051] sd 8:0:0:0: Attached scsi generic sg2 type 0
[    5.835149] sd 8:0:0:1: Attached scsi generic sg3 type 0
[    5.835241] sd 8:0:0:2: Attached scsi generic sg4 type 0
[    5.835337] sd 8:0:0:3: Attached scsi generic sg5 type 0
[    5.924066] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[    5.933899] sd 8:0:0:1: [sdc] Attached SCSI removable disk
[    5.944015] sd 8:0:0:2: [sdd] Attached SCSI removable disk
[    5.953992] sd 8:0:0:3: [sde] Attached SCSI removable disk
[   11.121409] Adding 8369148k swap on /dev/mapper/pdc_ifegacda5.  Priority:-1 extents:1 across:8369148k 
[   11.124796] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.124801] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   11.128418] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   11.166317] udevd[610]: starting version 175
[   11.172213] lp: driver loaded but no devices found
[   11.190994] wmi: Mapper loaded
[   11.198951] nvidia: module license 'NVIDIA' taints kernel.
[   11.198955] Disabling lock debugging due to kernel taint
[   11.213192] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.213309] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  319.32  Wed Jun 19 15:51:20 PDT 2013
[   11.217629] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20120320/utaddress-251)
[   11.217636] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.218099] sp5100_tco: SP5100 TCO WatchDog Timer Driver v0.01
[   11.218176] sp5100_tco: mmio address 0xb8fe00 already in use
[   11.245463] MCE: In-kernel MCE decoding enabled.
[   11.245966] EDAC MC: Ver: 2.1.0
[   11.248678] AMD64 EDAC driver v3.4.0
[   11.248723] EDAC amd64: DRAM ECC disabled.
[   11.248732] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   11.248732]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   11.248732]  (Note that use of the override may cause unknown side effects.)
[   11.254305] device-mapper: multipath: version 1.4.0 loaded
[   11.271758] microcode: CPU0: patch_level=0x06000629
[   11.340498] logitech-djreceiver 0003:046D:C52B.0005: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-3/input2
[   11.345199] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[   11.345335] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[   11.345398] input: Logitech Unifying Device. Wireless PID:1025 as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.2/0003:046D:C52B.0005/input/input6
[   11.345449] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   11.345573] logitech-djdevice 0003:046D:C52B.0006: input,hidraw3: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1025] on usb-0000:00:13.0-3:1
[   11.345597] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   11.345683] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   11.345742] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   11.345820] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   11.345890] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   11.458570] type=1400 audit(1383412222.980:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=978 comm="apparmor_parser"
[   11.458581] type=1400 audit(1383412222.980:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=867 comm="apparmor_parser"
[   11.458591] type=1400 audit(1383412222.980:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1000 comm="apparmor_parser"
[   11.458994] type=1400 audit(1383412222.984:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=978 comm="apparmor_parser"
[   11.459000] type=1400 audit(1383412222.984:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=867 comm="apparmor_parser"
[   11.459014] type=1400 audit(1383412222.984:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1000 comm="apparmor_parser"
[   11.459225] type=1400 audit(1383412222.984:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=978 comm="apparmor_parser"
[   11.459233] type=1400 audit(1383412222.984:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=867 comm="apparmor_parser"
[   11.459249] type=1400 audit(1383412222.984:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1000 comm="apparmor_parser"
[   11.586499] microcode: CPU0: new patch_level=0x0600063d
[   11.586523] microcode: CPU1: patch_level=0x06000629
[   11.622148] microcode: CPU1: new patch_level=0x0600063d
[   11.622159] microcode: CPU2: patch_level=0x06000629
[   11.635978] microcode: CPU2: new patch_level=0x0600063d
[   11.635997] microcode: CPU3: patch_level=0x06000629
[   11.648616] microcode: CPU3: new patch_level=0x0600063d
[   11.648644] microcode: CPU4: patch_level=0x06000629
[   11.661295] microcode: CPU4: new patch_level=0x0600063d
[   11.661310] microcode: CPU5: patch_level=0x06000629
[   11.675206] microcode: CPU5: new patch_level=0x0600063d
[   11.675279] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   11.680205] kvm: Nested Virtualization enabled
[   11.680210] kvm: Nested Paging enabled
[   12.550938] init: failsafe main process (1322) killed by TERM signal
[   12.672191] ppdev: user-space parallel port driver
[   12.728813] Bluetooth: Core ver 2.16
[   12.728829] NET: Registered protocol family 31
[   12.728830] Bluetooth: HCI device and connection manager initialized
[   12.728832] Bluetooth: HCI socket layer initialized
[   12.728833] Bluetooth: L2CAP socket layer initialized
[   12.728838] Bluetooth: SCO socket layer initialized
[   12.730302] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.730305] Bluetooth: BNEP filters: protocol multicast
[   12.731053] type=1400 audit(1383412224.256:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1401 comm="apparmor_parser"
[   12.731919] Bluetooth: RFCOMM TTY layer initialized
[   12.731923] Bluetooth: RFCOMM socket layer initialized
[   12.731925] Bluetooth: RFCOMM ver 1.11
[   12.980855] r8169 0000:04:06.0: eth1: link down
[   12.981469] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   12.981704] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

