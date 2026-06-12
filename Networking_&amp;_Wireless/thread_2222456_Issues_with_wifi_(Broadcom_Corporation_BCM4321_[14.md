---
title: "Issues with wifi (Broadcom Corporation BCM4321 [14e4:4328])"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by Ertyui on 2014-05-06
Hello All,

I am here seeking for help with an issue I am having regarding my wireless connection.
I have recently switched from Ubuntu 13.04 to 14.04 which I did by matters of a full reinstall. So I formatted my partition first and then installed Ubuntu 14.04.

Wifi used to work just fine, but I do remember that I had some trouble getting it to work back when I first installed Ubuntu (I think it was 11.04).
Though this time, something else seems to be wrong.

**To the point**. My wifi works, but only once every 15 or so reboots. And I don't find that a very ideal situation.
I've tried installing various modules that have been suggested around fora, but the only one that I can currently find working somewhat, is the one that Chili555 pointed out in the stickied forumpost.
I'm talking about the linux-firmware-nonfree package.

The network-manager does appear to acknowledge the existence of my wifi adapter, but it can't find any networks, unless I reboot 15 or so times.

I have saved output of the following commands: lspci, lsmod, dmesg and lshw for both the sessions where I do and don't have wifi, hoping that a diff between the outputs would result in any obvious issues. But sadly it doesn't, nothing appears to be out of order, at least to my glance over the data.

Also maybe relevant to point out, I've installed the 64-bit version of Ubuntu this time where it was 32-bit before, though I hardly think that would be the cause of the issue.

So after explaining the problem, here's a bunch of data:

System info:
It's a Mac Mini of about 4.5 years old, with a Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 05)

I also have the following outputs for a session without wifi:

lspci:
```

00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: NVIDIA Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: NVIDIA Corporation C79 [GeForce 9400] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 05)
04:00.0 FireWire (IEEE 1394): LSI Corporation FW643 [TrueFire] PCIe 1394b Controller (rev 07)

```

lshw:
```

emile-ubuntu
    description: Lunch Box Computer
    product: Macmini3,1 (System SKU#)
    vendor: Apple Inc.
    version: 1.0
    serial: VM925N8Y1BU
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=lunchbox family=Macmini sku=System SKU# uuid=978369DC-54FA-F24C-82C8-B1B5307A6A7F
  *-core
       description: Motherboard
       product: Mac-F22C86C8
       vendor: Apple Inc.
       physical id: 0
       serial: Base Board Serial#
       slot: Part Component
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
          slot: U2E1
          size: 1596MHz
          capacity: 2GHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
        *-cache
             description: L1 cache
             physical id: 2
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
     *-cache:0
          description: L1 cache
          physical id: 1
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-cpu:1
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 3
          bus info: cpu@1
          version: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
          slot: U2E1
          size: 1995MHz
          capacity: 2GHz
          clock: 266MHz
          capabilities: cpufreq
        *-cache
             description: L1 cache
             physical id: 5
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
     *-cache:1
          description: L1 cache
          physical id: 4
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 6
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0,9 ns)
             product: HMT112S6AFR6C-G7
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: 0x0D103222
             slot: DIMM0
             size: 1GiB
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1067 MHz (0,9 ns)
             product: HMT112S6AFR6C-G7
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             serial: 0x0C807646
             slot: DIMM0
             size: 1GiB
             clock: 1067MHz (0.9ns)
     *-firmware
          description: BIOS
          vendor: Apple Inc.
          physical id: e
          version: MM31.88Z.0081.B06.0904271717
          date: 04/27/09
          size: 1MiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect acpi ieee1394boot smartbattery netboot
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: NVIDIA Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:2000(size=256)
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: NVIDIA Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:0 ioport:2180(size=64) ioport:2140(size=64) ioport:2100(size=64)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.4
             bus info: pci@0000:00:03.4
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor UNCLAIMED
             description: Co-processor
             product: MCP79 Co-processor
             vendor: NVIDIA Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: latency=0 maxlatency=1 mingnt=3
             resources: memory:93400000-9347ffff
        *-usb:0
             description: USB controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: NVIDIA Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:17 memory:93488000-93488fff
        *-usb:1
             description: USB controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: NVIDIA Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:93489200-934892ff
        *-usb:2
             description: USB controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: NVIDIA Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:18 memory:93487000-93487fff
        *-usb:3
             description: USB controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: NVIDIA Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:23 memory:93489100-934891ff
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: NVIDIA Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
             resources: irq:20 memory:93480000-93483fff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: NVIDIA Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode cap_list
             resources: memory:93300000-933fffff
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: NVIDIA Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:23:df:9d:48:98
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
             resources: irq:44 memory:93486000-93486fff ioport:21e0(size=8) memory:93489000-934890ff memory:93489300-9348930f
        *-storage
             description: SATA controller
             product: MCP79 AHCI Controller
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:43 ioport:21d8(size=8) ioport:21ec(size=4) ioport:21d0(size=8) ioport:21e8(size=4) ioport:21c0(size=16) memory:93484000-93485fff
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi normal_decode bus_master cap_list
             resources: ioport:1000(size=4096) memory:92000000-930fffff ioport:80000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: C79 [GeForce 9400]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:45 memory:92000000-92ffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:1000(size=128) memory:93000000-9301ffff
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:93200000-932fffff
           *-network
                description: Network controller
                product: BCM4321 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 05
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:21 memory:93200000-93203fff
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:93100000-931fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW643 [TrueFire] PCIe 1394b Controller
                vendor: LSI Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 07
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:42 memory:93100000-93100fff
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54321
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: FBBA
             serial: 090409FB1B00LGGTNUEF
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00001f78
           *-volume:0 UNCLAIMED
                description: EFI GPT partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                capacity: 200MiB
                capabilities: primary nofs
           *-volume:1
                description: Darwin/OS X HFS+ partition
                vendor: Mac OS X (journaled)
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 4
                serial: b58b4aad-aad6-381e-0000-000000800000
                size: 110GiB
                capacity: 110GiB
                capabilities: primary bootable journaled osx hfsplus initialized
                configuration: boot=osx checked=2009-01-14 13:30:16 created=2009-01-14 04:30:16 filesystem=hfsplus lastmountedby=HFSJ modified=2012-10-15 23:39:54 state=clean
           *-volume:2
                description: EXT3 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1.0
                serial: 83681391-c9a4-4922-a418-3af134b16899
                size: 972MiB
                capacity: 972MiB
                capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2011-08-02 00:03:36 filesystem=ext3 modified=2013-04-10 21:52:09 mounted=2013-04-10 20:18:58 state=clean
     *-scsi:1
          physical id: 5
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD-RW  DVRTS08
             vendor: PIONEER
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: Q81B
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=open
     *-scsi:2
          physical id: 7
          bus info: usb@2:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=81a994f6
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/emile/Emile's Data 2
                version: 3.1
                serial: 70b04f25-e352-254a-b0ce-0aba7afa8472
                size: 743GiB
                capacity: 743GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-07-12 13:09:52 filesystem=ntfs label=Emile's Data 2 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@6:0.0.0,2
                logical name: /dev/sdb2
                logical name: /media/emile/COVERS
                version: FAT32
                serial: 1ae8-17cf
                size: 10GiB
                capacity: 10GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
           *-volume:2
                description: FAT16 partition
                physical id: 3
                bus info: scsi@6:0.0.0,3
                logical name: /dev/sdb3
                capacity: 78GiB
                capabilities: primary
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@6:0.0.0,4
                logical name: /dev/sdb4
                size: 99GiB
                capacity: 99GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 3906MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sdb6
                   logical name: /
                   capacity: 95GiB
                   capabilities: bootable
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:36:eb:74:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.13.0-24-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg

```

lsmod:
```

Module                  Size  Used by
ipt_MASQUERADE         12880  3 
iptable_nat            13011  1 
nf_nat_ipv4            13263  1 iptable_nat
nf_nat                 21798  3 ipt_MASQUERADE,nf_nat_ipv4,iptable_nat
nf_conntrack_ipv4      15012  2 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  1 
nf_conntrack           96976  6 ipt_MASQUERADE,nf_nat,nf_nat_ipv4,xt_conntrack,iptable_nat,nf_conntrack_ipv4
ipt_REJECT             12541  2 
xt_CHECKSUM            12549  1 
iptable_mangle         12695  1 
xt_tcpudp              12884  6 
bridge                110754  0 
stp                    12976  1 bridge
llc                    14552  2 stp,bridge
ip6table_filter        12815  0 
ip6_tables             27025  1 ip6table_filter
iptable_filter         12810  1 
ip_tables              27239  3 iptable_filter,iptable_mangle,iptable_nat
ebtable_nat            12807  0 
ebtables               30913  1 ebtable_nat
x_tables               34059  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
snd_hda_codec_realtek    61438  1 
rfcomm                 69160  8 
bnep                   19624  2 
arc4                   12608  2 
applesmc               19308  0 
input_polldev          13896  1 applesmc
nls_iso8859_1          12713  2 
snd_usb_audio         153411  1 
snd_usbmidi_lib        29215  1 snd_usb_audio
coretemp               13435  0 
kvm_intel             143060  0 
b43                   387371  0 
kvm                   451511  1 kvm_intel
bcma                   52096  1 b43
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
mac80211              626489  1 b43
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102099  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
cfg80211              484040  2 b43,mac80211
ssb_hcd                12869  0 
hid_appleir            13010  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
shpchp                 37032  0 
snd_rawmidi            30144  2 snd_usbmidi_lib,snd_seq_midi
btusb                  32412  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  20 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
bluetooth             395423  22 bnep,btusb,rfcomm
nvidia              10675249  39 
soundcore              12680  1 snd
drm                   302817  2 nvidia
i2c_nforce2            13221  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  3 hid_generic,usbhid,hid_appleir
usb_storage            62209  4 
firewire_ohci          40409  0 
firewire_core          68769  1 firewire_ohci
ssb                    62379  2 b43,ssb_hcd
ahci                   25819  1 
forcedeth              67509  0 
crc_itu_t              12707  1 firewire_core
libahci                32168  1 ahci

```


dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@panlong) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 (Ubuntu 3.13.0-24.46-generic 3.13.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=7145f873-9989-43ee-ac3d-deb6443d224d ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000008f000-0x000000000008ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000000090000-0x000000000009ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x000000004fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000050000000-0x000000007e483fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e484000-0x000000007e488fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007e489000-0x000000007e4b3fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e4b4000-0x000000007e4b4fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007e4b5000-0x000000007e4b6fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e4b7000-0x000000007e6b7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007e6b8000-0x000000007e6cbfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e6cc000-0x000000007e6ccfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007e6cd000-0x000000007e796fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e797000-0x000000007e797fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007e798000-0x000000007e821fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e822000-0x000000007e822fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007e823000-0x000000007e848fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e849000-0x000000007e84cfff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007e84d000-0x000000007e84efff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e84f000-0x000000007e853fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007e854000-0x000000007e855fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e856000-0x000000007e856fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007e857000-0x000000007e858fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e859000-0x000000007e859fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007e85a000-0x000000007e85ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e860000-0x000000007e861fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007e862000-0x000000007e862fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e863000-0x000000007e864fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007e865000-0x000000007e866fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e867000-0x000000007e86afff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007e86b000-0x000000007e872fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e873000-0x000000007e875fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007e876000-0x000000007e97cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e97d000-0x000000007e97dfff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007e97e000-0x000000007e97ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e980000-0x000000007e991fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007e992000-0x000000007e994fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007e995000-0x000000007e99afff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e99b000-0x000000007e99cfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007e99d000-0x000000007e9fbfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007e9fc000-0x000000007e9fefff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007e9ff000-0x000000007ea06fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ea07000-0x000000007ea08fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007ea09000-0x000000007ea0afff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007ea0b000-0x000000007ea0bfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ea0c000-0x000000007ea0cfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007ea0d000-0x000000007ea0dfff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007ea0e000-0x000000007ea0efff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ea0f000-0x000000007ea11fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007ea12000-0x000000007eed5fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007eed6000-0x000000007eed6fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007eed7000-0x000000007eed8fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007eed9000-0x000000007eed9fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007eeda000-0x000000007eee0fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007eee1000-0x000000007eee2fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007eee3000-0x000000007eee5fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007eee6000-0x000000007eee6fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007eee7000-0x000000007fa86fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007fa87000-0x000000007fa87fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007fa88000-0x000000007fe9dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007fe9e000-0x000000007fe9efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007fe9f000-0x000000007fec5fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007fec6000-0x000000007fec7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007fec8000-0x000000007fec8fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007fec9000-0x000000007fecafff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007fecb000-0x000000007feccfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007fecd000-0x000000007fedefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007fedf000-0x000000007feeefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007feef000-0x000000007fef8fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007fef9000-0x000000007fefffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000093400000-0x0000000093400fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v1.10 by Apple
[    0.000000] efi:  ACPI=0x7feee000  ACPI 2.0=0x7feee014  SMBIOS=0x7fec7000 
[    0.000000] efi: mem00: type=7, attr=0xf, range=[0x0000000000000000-0x000000000008f000) (0MB)
[    0.000000] efi: mem01: type=10, attr=0xf, range=[0x000000000008f000-0x0000000000090000) (0MB)
[    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000090000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem03: type=2, attr=0xf, range=[0x0000000000100000-0x00000000014ff000) (19MB)
[    0.000000] efi: mem04: type=7, attr=0xf, range=[0x00000000014ff000-0x0000000002000000) (11MB)
[    0.000000] efi: mem05: type=2, attr=0xf, range=[0x0000000002000000-0x00000000033ff000) (19MB)
[    0.000000] efi: mem06: type=7, attr=0xf, range=[0x00000000033ff000-0x0000000025606000) (546MB)
[    0.000000] efi: mem07: type=2, attr=0xf, range=[0x0000000025606000-0x0000000040000000) (425MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x0000000050000000-0x000000007a85e000) (680MB)
[    0.000000] efi: mem09: type=2, attr=0xf, range=[0x000000007a85e000-0x000000007a948000) (0MB)
[    0.000000] efi: mem10: type=1, attr=0xf, range=[0x000000007a948000-0x000000007aa7c000) (1MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x000000007aa7c000-0x000000007aa99000) (0MB)
[    0.000000] efi: mem12: type=4, attr=0xf, range=[0x000000007aa99000-0x000000007aadb000) (0MB)
[    0.000000] efi: mem13: type=2, attr=0xf, range=[0x000000007aadb000-0x000000007abc7000) (0MB)
[    0.000000] efi: mem14: type=4, attr=0xf, range=[0x000000007abc7000-0x000000007e3b1000) (55MB)
[    0.000000] efi: mem15: type=3, attr=0xf, range=[0x000000007e3b1000-0x000000007e434000) (0MB)
[    0.000000] efi: mem16: type=4, attr=0xf, range=[0x000000007e434000-0x000000007e484000) (0MB)
[    0.000000] efi: mem17: type=5, attr=0x800000000000000f, range=[0x000000007e484000-0x000000007e489000) (0MB)
[    0.000000] efi: mem18: type=3, attr=0xf, range=[0x000000007e489000-0x000000007e493000) (0MB)
[    0.000000] efi: mem19: type=4, attr=0xf, range=[0x000000007e493000-0x000000007e496000) (0MB)
[    0.000000] efi: mem20: type=3, attr=0xf, range=[0x000000007e496000-0x000000007e497000) (0MB)
[    0.000000] efi: mem21: type=4, attr=0xf, range=[0x000000007e497000-0x000000007e4a7000) (0MB)
[    0.000000] efi: mem22: type=3, attr=0xf, range=[0x000000007e4a7000-0x000000007e4ad000) (0MB)
[    0.000000] efi: mem23: type=4, attr=0xf, range=[0x000000007e4ad000-0x000000007e4b4000) (0MB)
[    0.000000] efi: mem24: type=5, attr=0x800000000000000f, range=[0x000000007e4b4000-0x000000007e4b5000) (0MB)
[    0.000000] efi: mem25: type=4, attr=0xf, range=[0x000000007e4b5000-0x000000007e4b6000) (0MB)
[    0.000000] efi: mem26: type=3, attr=0xf, range=[0x000000007e4b6000-0x000000007e4b7000) (0MB)
[    0.000000] efi: mem27: type=10, attr=0xf, range=[0x000000007e4b7000-0x000000007e6b8000) (2MB)
[    0.000000] efi: mem28: type=4, attr=0xf, range=[0x000000007e6b8000-0x000000007e6c6000) (0MB)
[    0.000000] efi: mem29: type=3, attr=0xf, range=[0x000000007e6c6000-0x000000007e6c9000) (0MB)
[    0.000000] efi: mem30: type=4, attr=0xf, range=[0x000000007e6c9000-0x000000007e6cc000) (0MB)
[    0.000000] efi: mem31: type=6, attr=0x800000000000000f, range=[0x000000007e6cc000-0x000000007e6cd000) (0MB)
[    0.000000] efi: mem32: type=4, attr=0xf, range=[0x000000007e6cd000-0x000000007e6ce000) (0MB)
[    0.000000] efi: mem33: type=3, attr=0xf, range=[0x000000007e6ce000-0x000000007e6fa000) (0MB)
[    0.000000] efi: mem34: type=4, attr=0xf, range=[0x000000007e6fa000-0x000000007e6fb000) (0MB)
[    0.000000] efi: mem35: type=3, attr=0xf, range=[0x000000007e6fb000-0x000000007e753000) (0MB)
[    0.000000] efi: mem36: type=4, attr=0xf, range=[0x000000007e753000-0x000000007e754000) (0MB)
[    0.000000] efi: mem37: type=3, attr=0xf, range=[0x000000007e754000-0x000000007e75a000) (0MB)
[    0.000000] efi: mem38: type=4, attr=0xf, range=[0x000000007e75a000-0x000000007e75d000) (0MB)
[    0.000000] efi: mem39: type=3, attr=0xf, range=[0x000000007e75d000-0x000000007e75f000) (0MB)
[    0.000000] efi: mem40: type=4, attr=0xf, range=[0x000000007e75f000-0x000000007e761000) (0MB)
[    0.000000] efi: mem41: type=3, attr=0xf, range=[0x000000007e761000-0x000000007e762000) (0MB)
[    0.000000] efi: mem42: type=4, attr=0xf, range=[0x000000007e762000-0x000000007e766000) (0MB)
[    0.000000] efi: mem43: type=3, attr=0xf, range=[0x000000007e766000-0x000000007e768000) (0MB)
[    0.000000] efi: mem44: type=4, attr=0xf, range=[0x000000007e768000-0x000000007e769000) (0MB)
[    0.000000] efi: mem45: type=3, attr=0xf, range=[0x000000007e769000-0x000000007e776000) (0MB)
[    0.000000] efi: mem46: type=4, attr=0xf, range=[0x000000007e776000-0x000000007e777000) (0MB)
[    0.000000] efi: mem47: type=3, attr=0xf, range=[0x000000007e777000-0x000000007e779000) (0MB)
[    0.000000] efi: mem48: type=4, attr=0xf, range=[0x000000007e779000-0x000000007e77b000) (0MB)
[    0.000000] efi: mem49: type=3, attr=0xf, range=[0x000000007e77b000-0x000000007e77c000) (0MB)
[    0.000000] efi: mem50: type=4, attr=0xf, range=[0x000000007e77c000-0x000000007e77f000) (0MB)
[    0.000000] efi: mem51: type=3, attr=0xf, range=[0x000000007e77f000-0x000000007e781000) (0MB)
[    0.000000] efi: mem52: type=4, attr=0xf, range=[0x000000007e781000-0x000000007e782000) (0MB)
[    0.000000] efi: mem53: type=3, attr=0xf, range=[0x000000007e782000-0x000000007e784000) (0MB)
[    0.000000] efi: mem54: type=4, attr=0xf, range=[0x000000007e784000-0x000000007e786000) (0MB)
[    0.000000] efi: mem55: type=3, attr=0xf, range=[0x000000007e786000-0x000000007e787000) (0MB)
[    0.000000] efi: mem56: type=4, attr=0xf, range=[0x000000007e787000-0x000000007e788000) (0MB)
[    0.000000] efi: mem57: type=3, attr=0xf, range=[0x000000007e788000-0x000000007e78a000) (0MB)
[    0.000000] efi: mem58: type=4, attr=0xf, range=[0x000000007e78a000-0x000000007e78b000) (0MB)
[    0.000000] efi: mem59: type=3, attr=0xf, range=[0x000000007e78b000-0x000000007e792000) (0MB)
[    0.000000] efi: mem60: type=4, attr=0xf, range=[0x000000007e792000-0x000000007e793000) (0MB)
[    0.000000] efi: mem61: type=3, attr=0xf, range=[0x000000007e793000-0x000000007e796000) (0MB)
[    0.000000] efi: mem62: type=4, attr=0xf, range=[0x000000007e796000-0x000000007e797000) (0MB)
[    0.000000] efi: mem63: type=6, attr=0x800000000000000f, range=[0x000000007e797000-0x000000007e798000) (0MB)
[    0.000000] efi: mem64: type=3, attr=0xf, range=[0x000000007e798000-0x000000007e799000) (0MB)
[    0.000000] efi: mem65: type=4, attr=0xf, range=[0x000000007e799000-0x000000007e79b000) (0MB)
[    0.000000] efi: mem66: type=3, attr=0xf, range=[0x000000007e79b000-0x000000007e79f000) (0MB)
[    0.000000] efi: mem67: type=4, attr=0xf, range=[0x000000007e79f000-0x000000007e7a0000) (0MB)
[    0.000000] efi: mem68: type=3, attr=0xf, range=[0x000000007e7a0000-0x000000007e7a6000) (0MB)
[    0.000000] efi: mem69: type=4, attr=0xf, range=[0x000000007e7a6000-0x000000007e7a8000) (0MB)
[    0.000000] efi: mem70: type=3, attr=0xf, range=[0x000000007e7a8000-0x000000007e7a9000) (0MB)
[    0.000000] efi: mem71: type=4, attr=0xf, range=[0x000000007e7a9000-0x000000007e7ab000) (0MB)
[    0.000000] efi: mem72: type=3, attr=0xf, range=[0x000000007e7ab000-0x000000007e7b0000) (0MB)
[    0.000000] efi: mem73: type=4, attr=0xf, range=[0x000000007e7b0000-0x000000007e7b8000) (0MB)
[    0.000000] efi: mem74: type=3, attr=0xf, range=[0x000000007e7b8000-0x000000007e7cb000) (0MB)
[    0.000000] efi: mem75: type=4, attr=0xf, range=[0x000000007e7cb000-0x000000007e7cd000) (0MB)
[    0.000000] efi: mem76: type=3, attr=0xf, range=[0x000000007e7cd000-0x000000007e7d7000) (0MB)
[    0.000000] efi: mem77: type=4, attr=0xf, range=[0x000000007e7d7000-0x000000007e7d9000) (0MB)
[    0.000000] efi: mem78: type=3, attr=0xf, range=[0x000000007e7d9000-0x000000007e7dd000) (0MB)
[    0.000000] efi: mem79: type=4, attr=0xf, range=[0x000000007e7dd000-0x000000007e7df000) (0MB)
[    0.000000] efi: mem80: type=3, attr=0xf, range=[0x000000007e7df000-0x000000007e7e1000) (0MB)
[    0.000000] efi: mem81: type=4, attr=0xf, range=[0x000000007e7e1000-0x000000007e7e3000) (0MB)
[    0.000000] efi: mem82: type=3, attr=0xf, range=[0x000000007e7e3000-0x000000007e7e8000) (0MB)
[    0.000000] efi: mem83: type=4, attr=0xf, range=[0x000000007e7e8000-0x000000007e7e9000) (0MB)
[    0.000000] efi: mem84: type=3, attr=0xf, range=[0x000000007e7e9000-0x000000007e7fc000) (0MB)
[    0.000000] efi: mem85: type=4, attr=0xf, range=[0x000000007e7fc000-0x000000007e7fd000) (0MB)
[    0.000000] efi: mem86: type=3, attr=0xf, range=[0x000000007e7fd000-0x000000007e80b000) (0MB)
[    0.000000] efi: mem87: type=4, attr=0xf, range=[0x000000007e80b000-0x000000007e80e000) (0MB)
[    0.000000] efi: mem88: type=3, attr=0xf, range=[0x000000007e80e000-0x000000007e810000) (0MB)
[    0.000000] efi: mem89: type=4, attr=0xf, range=[0x000000007e810000-0x000000007e814000) (0MB)
[    0.000000] efi: mem90: type=3, attr=0xf, range=[0x000000007e814000-0x000000007e81f000) (0MB)
[    0.000000] efi: mem91: type=4, attr=0xf, range=[0x000000007e81f000-0x000000007e821000) (0MB)
[    0.000000] efi: mem92: type=3, attr=0xf, range=[0x000000007e821000-0x000000007e822000) (0MB)
[    0.000000] efi: mem93: type=6, attr=0x800000000000000f, range=[0x000000007e822000-0x000000007e823000) (0MB)
[    0.000000] efi: mem94: type=4, attr=0xf, range=[0x000000007e823000-0x000000007e824000) (0MB)
[    0.000000] efi: mem95: type=3, attr=0xf, range=[0x000000007e824000-0x000000007e827000) (0MB)
[    0.000000] efi: mem96: type=4, attr=0xf, range=[0x000000007e827000-0x000000007e828000) (0MB)
[    0.000000] efi: mem97: type=3, attr=0xf, range=[0x000000007e828000-0x000000007e843000) (0MB)
[    0.000000] efi: mem98: type=4, attr=0xf, range=[0x000000007e843000-0x000000007e845000) (0MB)
[    0.000000] efi: mem99: type=3, attr=0xf, range=[0x000000007e845000-0x000000007e846000) (0MB)
[    0.000000] efi: mem100: type=4, attr=0xf, range=[0x000000007e846000-0x000000007e849000) (0MB)
[    0.000000] efi: mem101: type=5, attr=0x800000000000000f, range=[0x000000007e849000-0x000000007e84d000) (0MB)
[    0.000000] efi: mem102: type=4, attr=0xf, range=[0x000000007e84d000-0x000000007e84f000) (0MB)
[    0.000000] efi: mem103: type=5, attr=0x800000000000000f, range=[0x000000007e84f000-0x000000007e854000) (0MB)
[    0.000000] efi: mem104: type=3, attr=0xf, range=[0x000000007e854000-0x000000007e855000) (0MB)
[    0.000000] efi: mem105: type=4, attr=0xf, range=[0x000000007e855000-0x000000007e856000) (0MB)
[    0.000000] efi: mem106: type=6, attr=0x800000000000000f, range=[0x000000007e856000-0x000000007e857000) (0MB)
[    0.000000] efi: mem107: type=4, attr=0xf, range=[0x000000007e857000-0x000000007e859000) (0MB)
[    0.000000] efi: mem108: type=5, attr=0x800000000000000f, range=[0x000000007e859000-0x000000007e85a000) (0MB)
[    0.000000] efi: mem109: type=4, attr=0xf, range=[0x000000007e85a000-0x000000007e85c000) (0MB)
[    0.000000] efi: mem110: type=3, attr=0xf, range=[0x000000007e85c000-0x000000007e85e000) (0MB)
[    0.000000] efi: mem111: type=4, attr=0xf, range=[0x000000007e85e000-0x000000007e860000) (0MB)
[    0.000000] efi: mem112: type=10, attr=0xf, range=[0x000000007e860000-0x000000007e862000) (0MB)
[    0.000000] efi: mem113: type=4, attr=0xf, range=[0x000000007e862000-0x000000007e863000) (0MB)
[    0.000000] efi: mem114: type=10, attr=0xf, range=[0x000000007e863000-0x000000007e865000) (0MB)
[    0.000000] efi: mem115: type=4, attr=0xf, range=[0x000000007e865000-0x000000007e867000) (0MB)
[    0.000000] efi: mem116: type=5, attr=0x800000000000000f, range=[0x000000007e867000-0x000000007e86b000) (0MB)
[    0.000000] efi: mem117: type=4, attr=0xf, range=[0x000000007e86b000-0x000000007e871000) (0MB)
[    0.000000] efi: mem118: type=3, attr=0xf, range=[0x000000007e871000-0x000000007e873000) (0MB)
[    0.000000] efi: mem119: type=5, attr=0x800000000000000f, range=[0x000000007e873000-0x000000007e876000) (0MB)
[    0.000000] efi: mem120: type=4, attr=0xf, range=[0x000000007e876000-0x000000007e87b000) (0MB)
[    0.000000] efi: mem121: type=3, attr=0xf, range=[0x000000007e87b000-0x000000007e87d000) (0MB)
[    0.000000] efi: mem122: type=4, attr=0xf, range=[0x000000007e87d000-0x000000007e88d000) (0MB)
[    0.000000] efi: mem123: type=3, attr=0xf, range=[0x000000007e88d000-0x000000007e897000) (0MB)
[    0.000000] efi: mem124: type=4, attr=0xf, range=[0x000000007e897000-0x000000007e89f000) (0MB)
[    0.000000] efi: mem125: type=3, attr=0xf, range=[0x000000007e89f000-0x000000007e8a3000) (0MB)
[    0.000000] efi: mem126: type=4, attr=0xf, range=[0x000000007e8a3000-0x000000007e95b000) (0MB)
[    0.000000] efi: mem127: type=3, attr=0xf, range=[0x000000007e95b000-0x000000007e968000) (0MB)
[    0.000000] efi: mem128: type=4, attr=0xf, range=[0x000000007e968000-0x000000007e979000) (0MB)
[    0.000000] efi: mem129: type=3, attr=0xf, range=[0x000000007e979000-0x000000007e97c000) (0MB)
[    0.000000] efi: mem130: type=4, attr=0xf, range=[0x000000007e97c000-0x000000007e97d000) (0MB)
[    0.000000] efi: mem131: type=5, attr=0x800000000000000f, range=[0x000000007e97d000-0x000000007e97e000) (0MB)
[    0.000000] efi: mem132: type=3, attr=0xf, range=[0x000000007e97e000-0x000000007e97f000) (0MB)
[    0.000000] efi: mem133: type=4, attr=0xf, range=[0x000000007e97f000-0x000000007e980000) (0MB)
[    0.000000] efi: mem134: type=6, attr=0x800000000000000f, range=[0x000000007e980000-0x000000007e992000) (0MB)
[    0.000000] efi: mem135: type=5, attr=0x800000000000000f, range=[0x000000007e992000-0x000000007e995000) (0MB)
[    0.000000] efi: mem136: type=3, attr=0xf, range=[0x000000007e995000-0x000000007e996000) (0MB)
[    0.000000] efi: mem137: type=4, attr=0xf, range=[0x000000007e996000-0x000000007e998000) (0MB)
[    0.000000] efi: mem138: type=3, attr=0xf, range=[0x000000007e998000-0x000000007e99b000) (0MB)
[    0.000000] efi: mem139: type=6, attr=0x800000000000000f, range=[0x000000007e99b000-0x000000007e99d000) (0MB)
[    0.000000] efi: mem140: type=4, attr=0xf, range=[0x000000007e99d000-0x000000007e9a0000) (0MB)
[    0.000000] efi: mem141: type=3, attr=0xf, range=[0x000000007e9a0000-0x000000007e9a1000) (0MB)
[    0.000000] efi: mem142: type=4, attr=0xf, range=[0x000000007e9a1000-0x000000007e9a2000) (0MB)
[    0.000000] efi: mem143: type=3, attr=0xf, range=[0x000000007e9a2000-0x000000007e9a3000) (0MB)
[    0.000000] efi: mem144: type=4, attr=0xf, range=[0x000000007e9a3000-0x000000007e9a4000) (0MB)
[    0.000000] efi: mem145: type=3, attr=0xf, range=[0x000000007e9a4000-0x000000007e9a5000) (0MB)
[    0.000000] efi: mem146: type=4, attr=0xf, range=[0x000000007e9a5000-0x000000007e9a8000) (0MB)
[    0.000000] efi: mem147: type=3, attr=0xf, range=[0x000000007e9a8000-0x000000007e9ab000) (0MB)
[    0.000000] efi: mem148: type=4, attr=0xf, range=[0x000000007e9ab000-0x000000007e9ed000) (0MB)
[    0.000000] efi: mem149: type=3, attr=0xf, range=[0x000000007e9ed000-0x000000007e9fc000) (0MB)
[    0.000000] efi: mem150: type=5, attr=0x800000000000000f, range=[0x000000007e9fc000-0x000000007e9ff000) (0MB)
[    0.000000] efi: mem151: type=3, attr=0xf, range=[0x000000007e9ff000-0x000000007ea04000) (0MB)
[    0.000000] efi: mem152: type=4, attr=0xf, range=[0x000000007ea04000-0x000000007ea07000) (0MB)
[    0.000000] efi: mem153: type=5, attr=0x800000000000000f, range=[0x000000007ea07000-0x000000007ea09000) (0MB)
[    0.000000] efi: mem154: type=6, attr=0x800000000000000f, range=[0x000000007ea09000-0x000000007ea0b000) (0MB)
[    0.000000] efi: mem155: type=3, attr=0xf, range=[0x000000007ea0b000-0x000000007ea0c000) (0MB)
[    0.000000] efi: mem156: type=6, attr=0x800000000000000f, range=[0x000000007ea0c000-0x000000007ea0d000) (0MB)
[    0.000000] efi: mem157: type=5, attr=0x800000000000000f, range=[0x000000007ea0d000-0x000000007ea0e000) (0MB)
[    0.000000] efi: mem158: type=4, attr=0xf, range=[0x000000007ea0e000-0x000000007ea0f000) (0MB)
[    0.000000] efi: mem159: type=5, attr=0x800000000000000f, range=[0x000000007ea0f000-0x000000007ea12000) (0MB)
[    0.000000] efi: mem160: type=4, attr=0xf, range=[0x000000007ea12000-0x000000007ee33000) (4MB)
[    0.000000] efi: mem161: type=3, attr=0xf, range=[0x000000007ee33000-0x000000007ee3c000) (0MB)
[    0.000000] efi: mem162: type=4, attr=0xf, range=[0x000000007ee3c000-0x000000007eed5000) (0MB)
[    0.000000] efi: mem163: type=3, attr=0xf, range=[0x000000007eed5000-0x000000007eed6000) (0MB)
[    0.000000] efi: mem164: type=6, attr=0x800000000000000f, range=[0x000000007eed6000-0x000000007eed7000) (0MB)
[    0.000000] efi: mem165: type=4, attr=0xf, range=[0x000000007eed7000-0x000000007eed9000) (0MB)
[    0.000000] efi: mem166: type=6, attr=0x800000000000000f, range=[0x000000007eed9000-0x000000007eeda000) (0MB)
[    0.000000] efi: mem167: type=3, attr=0xf, range=[0x000000007eeda000-0x000000007eedb000) (0MB)
[    0.000000] efi: mem168: type=4, attr=0xf, range=[0x000000007eedb000-0x000000007eedd000) (0MB)
[    0.000000] efi: mem169: type=3, attr=0xf, range=[0x000000007eedd000-0x000000007eee1000) (0MB)
[    0.000000] efi: mem170: type=5, attr=0x800000000000000f, range=[0x000000007eee1000-0x000000007eee3000) (0MB)
[    0.000000] efi: mem171: type=4, attr=0xf, range=[0x000000007eee3000-0x000000007eee4000) (0MB)
[    0.000000] efi: mem172: type=3, attr=0xf, range=[0x000000007eee4000-0x000000007eee5000) (0MB)
[    0.000000] efi: mem173: type=4, attr=0xf, range=[0x000000007eee5000-0x000000007eee6000) (0MB)
[    0.000000] efi: mem174: type=5, attr=0x800000000000000f, range=[0x000000007eee6000-0x000000007eee7000) (0MB)
[    0.000000] efi: mem175: type=4, attr=0xf, range=[0x000000007eee7000-0x000000007fa87000) (11MB)
[    0.000000] efi: mem176: type=6, attr=0x800000000000000f, range=[0x000000007fa87000-0x000000007fa88000) (0MB)
[    0.000000] efi: mem177: type=4, attr=0xf, range=[0x000000007fa88000-0x000000007fe9e000) (4MB)
[    0.000000] efi: mem178: type=6, attr=0x800000000000000f, range=[0x000000007fe9e000-0x000000007fe9f000) (0MB)
[    0.000000] efi: mem179: type=7, attr=0xf, range=[0x000000007fe9f000-0x000000007feb9000) (0MB)
[    0.000000] efi: mem180: type=2, attr=0xf, range=[0x000000007feb9000-0x000000007fec6000) (0MB)
[    0.000000] efi: mem181: type=10, attr=0xf, range=[0x000000007fec6000-0x000000007fec8000) (0MB)
[    0.000000] efi: mem182: type=9, attr=0xf, range=[0x000000007fec8000-0x000000007fec9000) (0MB)
[    0.000000] efi: mem183: type=10, attr=0xf, range=[0x000000007fec9000-0x000000007fecb000) (0MB)
[    0.000000] efi: mem184: type=9, attr=0xf, range=[0x000000007fecb000-0x000000007fecd000) (0MB)
[    0.000000] efi: mem185: type=10, attr=0xf, range=[0x000000007fecd000-0x000000007fedf000) (0MB)
[    0.000000] efi: mem186: type=9, attr=0xf, range=[0x000000007fedf000-0x000000007feef000) (0MB)
[    0.000000] efi: mem187: type=7, attr=0xf, range=[0x000000007feef000-0x000000007fef9000) (0MB)
[    0.000000] efi: mem188: type=0, attr=0xf, range=[0x000000007fef9000-0x000000007feff000) (0MB)
[    0.000000] efi: mem189: type=6, attr=0x800000000000000f, range=[0x000000007feff000-0x000000007ff00000) (0MB)
[    0.000000] efi: mem190: type=0, attr=0x8000000000000000, range=[0x0000000040000000-0x0000000050000000) (256MB)
[    0.000000] efi: mem191: type=11, attr=0x8000000000000000, range=[0x0000000093400000-0x0000000093401000) (0MB)
[    0.000000] efi: mem192: type=11, attr=0x8000000000000000, range=[0x00000000ffc00000-0x00000000ffc40000) (0MB)
[    0.000000] efi: mem193: type=11, attr=0x8000000000000000, range=[0x00000000ffc40000-0x00000000ffc80000) (0MB)
[    0.000000] efi: mem194: type=11, attr=0x8000000000000000, range=[0x00000000ffc80000-0x00000000ffca4000) (0MB)
[    0.000000] efi: mem195: type=11, attr=0x8000000000000000, range=[0x00000000ffca4000-0x00000000ffcb4000) (0MB)
[    0.000000] efi: mem196: type=11, attr=0x8000000000000000, range=[0x00000000ffcb4000-0x00000000ffffc000) (3MB)
[    0.000000] efi: mem197: type=11, attr=0x8000000000000000, range=[0x00000000ffffc000-0x0000000100000000) (0MB)
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Apple Inc. Macmini3,1/Mac-F22C86C8, BIOS     MM31.88Z.0081.B06.0904271717 04/27/09
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x7fef9 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 disabled
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 1, base: 0GB, range: 2GB, type WB
[    0.000000] reg 2, base: 2047MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2047M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 2      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fdd000, 0x02fddfff] PGTABLE
[    0.000000] BRK [0x02fde000, 0x02fdefff] PGTABLE
[    0.000000] BRK [0x02fdf000, 0x02fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x7a800000-0x7a9fffff]
[    0.000000]  [mem 0x7a800000-0x7a9fffff] page 2M
[    0.000000] BRK [0x02fe0000, 0x02fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x78000000-0x7a7fffff]
[    0.000000]  [mem 0x78000000-0x7a7fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x3fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x50000000-0x77ffffff]
[    0.000000]  [mem 0x50000000-0x77ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x7aa00000-0x7e483fff]
[    0.000000]  [mem 0x7aa00000-0x7e3fffff] page 2M
[    0.000000]  [mem 0x7e400000-0x7e483fff] page 4k
[    0.000000] BRK [0x02fe1000, 0x02fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x7e489000-0x7e4b3fff]
[    0.000000]  [mem 0x7e489000-0x7e4b3fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e4b5000-0x7e4b6fff]
[    0.000000]  [mem 0x7e4b5000-0x7e4b6fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e6b8000-0x7e6cbfff]
[    0.000000]  [mem 0x7e6b8000-0x7e6cbfff] page 4k
[    0.000000] BRK [0x02fe2000, 0x02fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x7e6cd000-0x7e796fff]
[    0.000000]  [mem 0x7e6cd000-0x7e796fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e798000-0x7e821fff]
[    0.000000]  [mem 0x7e798000-0x7e821fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e823000-0x7e848fff]
[    0.000000]  [mem 0x7e823000-0x7e848fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e84d000-0x7e84efff]
[    0.000000]  [mem 0x7e84d000-0x7e84efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e854000-0x7e855fff]
[    0.000000]  [mem 0x7e854000-0x7e855fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e857000-0x7e858fff]
[    0.000000]  [mem 0x7e857000-0x7e858fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e85a000-0x7e85ffff]
[    0.000000]  [mem 0x7e85a000-0x7e85ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e862000-0x7e862fff]
[    0.000000]  [mem 0x7e862000-0x7e862fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e865000-0x7e866fff]
[    0.000000]  [mem 0x7e865000-0x7e866fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e86b000-0x7e872fff]
[    0.000000]  [mem 0x7e86b000-0x7e872fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e876000-0x7e97cfff]
[    0.000000]  [mem 0x7e876000-0x7e97cfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e97e000-0x7e97ffff]
[    0.000000]  [mem 0x7e97e000-0x7e97ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e995000-0x7e99afff]
[    0.000000]  [mem 0x7e995000-0x7e99afff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e99d000-0x7e9fbfff]
[    0.000000]  [mem 0x7e99d000-0x7e9fbfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7e9ff000-0x7ea06fff]
[    0.000000]  [mem 0x7e9ff000-0x7ea06fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7ea0b000-0x7ea0bfff]
[    0.000000]  [mem 0x7ea0b000-0x7ea0bfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7ea0e000-0x7ea0efff]
[    0.000000]  [mem 0x7ea0e000-0x7ea0efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7ea12000-0x7eed5fff]
[    0.000000]  [mem 0x7ea12000-0x7ebfffff] page 4k
[    0.000000]  [mem 0x7ec00000-0x7edfffff] page 2M
[    0.000000]  [mem 0x7ee00000-0x7eed5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7eed7000-0x7eed8fff]
[    0.000000]  [mem 0x7eed7000-0x7eed8fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7eeda000-0x7eee0fff]
[    0.000000]  [mem 0x7eeda000-0x7eee0fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7eee3000-0x7eee5fff]
[    0.000000]  [mem 0x7eee3000-0x7eee5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7eee7000-0x7fa86fff]
[    0.000000]  [mem 0x7eee7000-0x7effffff] page 4k
[    0.000000]  [mem 0x7f000000-0x7f9fffff] page 2M
[    0.000000]  [mem 0x7fa00000-0x7fa86fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7fa88000-0x7fe9dfff]
[    0.000000]  [mem 0x7fa88000-0x7fbfffff] page 4k
[    0.000000]  [mem 0x7fc00000-0x7fdfffff] page 2M
[    0.000000]  [mem 0x7fe00000-0x7fe9dfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7fe9f000-0x7fec5fff]
[    0.000000]  [mem 0x7fe9f000-0x7fec5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7feef000-0x7fef8fff]
[    0.000000]  [mem 0x7feef000-0x7fef8fff] page 4k
[    0.000000] RAMDISK: [mem 0x35b9e000-0x36dc6fff]
[    0.000000] ACPI: RSDP 000000007feee014 000024 (v02 APPLE )
[    0.000000] ACPI: XSDT 000000007feee1c0 00006C (v01 APPLE   Apple00 00000081      01000013)
[    0.000000] ACPI: FACP 000000007feec000 0000F4 (v03 APPLE   Apple00 00000081 Loki 0000005F)
[    0.000000] ACPI: DSDT 000000007fee0000 0050B8 (v01 APPLE   Macmini 00030001 INTL 20061109)
[    0.000000] ACPI: FACS 000000007fecd000 000040
[    0.000000] ACPI: HPET 000000007feeb000 000038 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: APIC 000000007feea000 000068 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: MCFG 000000007fee9000 00003C (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ASF! 000000007fee8000 0000A5 (v32 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SBST 000000007fee7000 000030 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ECDT 000000007fee6000 000053 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SSDT 000000007fecb000 0002C3 (v00        SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 000000007fec8000 0004DC (v01  APPLE    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007fef8fff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x7fef8fff]
[    0.000000]   NODE_DATA [mem 0x7fef4000-0x7fef8fff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff880078600000-ffff88007a1fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0008efff]
[    0.000000]   node   0: [mem 0x00090000-0x0009ffff]
[    0.000000]   node   0: [mem 0x00100000-0x3fffffff]
[    0.000000]   node   0: [mem 0x50000000-0x7e483fff]
[    0.000000]   node   0: [mem 0x7e489000-0x7e4b3fff]
[    0.000000]   node   0: [mem 0x7e4b5000-0x7e4b6fff]
[    0.000000]   node   0: [mem 0x7e6b8000-0x7e6cbfff]
[    0.000000]   node   0: [mem 0x7e6cd000-0x7e796fff]
[    0.000000]   node   0: [mem 0x7e798000-0x7e821fff]
[    0.000000]   node   0: [mem 0x7e823000-0x7e848fff]
[    0.000000]   node   0: [mem 0x7e84d000-0x7e84efff]
[    0.000000]   node   0: [mem 0x7e854000-0x7e855fff]
[    0.000000]   node   0: [mem 0x7e857000-0x7e858fff]
[    0.000000]   node   0: [mem 0x7e85a000-0x7e85ffff]
[    0.000000]   node   0: [mem 0x7e862000-0x7e862fff]
[    0.000000]   node   0: [mem 0x7e865000-0x7e866fff]
[    0.000000]   node   0: [mem 0x7e86b000-0x7e872fff]
[    0.000000]   node   0: [mem 0x7e876000-0x7e97cfff]
[    0.000000]   node   0: [mem 0x7e97e000-0x7e97ffff]
[    0.000000]   node   0: [mem 0x7e995000-0x7e99afff]
[    0.000000]   node   0: [mem 0x7e99d000-0x7e9fbfff]
[    0.000000]   node   0: [mem 0x7e9ff000-0x7ea06fff]
[    0.000000]   node   0: [mem 0x7ea0b000-0x7ea0bfff]
[    0.000000]   node   0: [mem 0x7ea0e000-0x7ea0efff]
[    0.000000]   node   0: [mem 0x7ea12000-0x7eed5fff]
[    0.000000]   node   0: [mem 0x7eed7000-0x7eed8fff]
[    0.000000]   node   0: [mem 0x7eeda000-0x7eee0fff]
[    0.000000]   node   0: [mem 0x7eee3000-0x7eee5fff]
[    0.000000]   node   0: [mem 0x7eee7000-0x7fa86fff]
[    0.000000]   node   0: [mem 0x7fa88000-0x7fe9dfff]
[    0.000000]   node   0: [mem 0x7fe9f000-0x7fec5fff]
[    0.000000]   node   0: [mem 0x7feef000-0x7fef8fff]
[    0.000000] On node 0 totalpages: 457763
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 25 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7091 pages used for memmap
[    0.000000]   DMA32 zone: 453765 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0008f000-0x0008ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40000000-0x4fffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e484000-0x7e488fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e4b4000-0x7e4b4fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e4b7000-0x7e6b7fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e6cc000-0x7e6ccfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e797000-0x7e797fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e822000-0x7e822fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e849000-0x7e84cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e84f000-0x7e853fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e856000-0x7e856fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e859000-0x7e859fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e860000-0x7e861fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e863000-0x7e864fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e867000-0x7e86afff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e873000-0x7e875fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e97d000-0x7e97dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e980000-0x7e991fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e992000-0x7e994fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e99b000-0x7e99cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e9fc000-0x7e9fefff]
[    0.000000] PM: Registered nosave memory: [mem 0x7ea07000-0x7ea08fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7ea09000-0x7ea0afff]
[    0.000000] PM: Registered nosave memory: [mem 0x7ea0c000-0x7ea0cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7ea0d000-0x7ea0dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7ea0f000-0x7ea11fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7eed6000-0x7eed6fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7eed9000-0x7eed9fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7eee1000-0x7eee2fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7eee6000-0x7eee6fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7fa87000-0x7fa87fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7fe9e000-0x7fe9efff]
[    0.000000] PM: Registered nosave memory: [mem 0x7fec6000-0x7fec7fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7fec8000-0x7fec8fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7fec9000-0x7fecafff]
[    0.000000] PM: Registered nosave memory: [mem 0x7fecb000-0x7feccfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7fecd000-0x7fedefff]
[    0.000000] PM: Registered nosave memory: [mem 0x7fedf000-0x7feeefff]
[    0.000000] e820: [mem 0x93401000-0xffbfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88007a800000 s86336 r8192 d24256 u1048576
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 450583
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=7145f873-9989-43ee-ac3d-deb6443d224d ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1684132K/1831052K available (7338K kernel code, 1138K rwdata, 3388K rodata, 1332K init, 1440K bss, 146920K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-1.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 7340032 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1989.801 MHz processor
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3979.60 BogoMIPS (lpj=7959204)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.028330] Security Framework initialized
[    0.028354] AppArmor: AppArmor initialized
[    0.028356] Yama: becoming mindful.
[    0.028679] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.029868] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.030372] Mount-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.030382] Mountpoint-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.030726] Initializing cgroup subsys memory
[    0.030739] Initializing cgroup subsys devices
[    0.030743] Initializing cgroup subsys freezer
[    0.030746] Initializing cgroup subsys blkio
[    0.030749] Initializing cgroup subsys perf_event
[    0.030753] Initializing cgroup subsys hugetlb
[    0.030789] CPU: Physical Processor ID: 0
[    0.030791] CPU: Processor Core ID: 0
[    0.030794] mce: CPU supports 6 MCE banks
[    0.030805] CPU0: Thermal monitoring enabled (TM2)
[    0.030815] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.030815] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.030815] tlb_flushall_shift: -1
[    0.030961] Freeing SMP alternatives memory: 32K (ffffffff81e6b000 - ffffffff81e73000)
[    0.033264] ACPI: Core revision 20131115
[    0.038170] ACPI: All ACPI Tables successfully acquired
[    0.043976] ftrace: allocating 28408 entries in 111 pages
[    0.056592] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.097809] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz (fam: 06, model: 17, stepping: 0a)
[    0.100000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.100000] ... version:                2
[    0.100000] ... bit width:              40
[    0.100000] ... generic registers:      2
[    0.100000] ... value mask:             000000ffffffffff
[    0.100000] ... max period:             000000007fffffff
[    0.100000] ... fixed-purpose events:   3
[    0.100000] ... event mask:             0000000700000003
[    0.102759] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.102919] x86: Booting SMP configuration:
[    0.102923] .... node  #0, CPUs:      #1
[    0.116016] x86: Booted up 1 node, 2 CPUs
[    0.116022] smpboot: Total of 2 processors activated (7959.20 BogoMIPS)
[    0.118712] devtmpfs: initialized
[    0.126738] EVM: security.selinux
[    0.126741] EVM: security.SMACK64
[    0.126744] EVM: security.ima
[    0.126746] EVM: security.capability
[    0.128037] PM: Registering ACPI NVS region [mem 0x0008f000-0x0008ffff] (4096 bytes)
[    0.128040] PM: Registering ACPI NVS region [mem 0x7e4b7000-0x7e6b7fff] (2101248 bytes)
[    0.128086] PM: Registering ACPI NVS region [mem 0x7e860000-0x7e861fff] (8192 bytes)
[    0.128088] PM: Registering ACPI NVS region [mem 0x7e863000-0x7e864fff] (8192 bytes)
[    0.128091] PM: Registering ACPI NVS region [mem 0x7fec6000-0x7fec7fff] (8192 bytes)
[    0.128093] PM: Registering ACPI NVS region [mem 0x7fec9000-0x7fecafff] (8192 bytes)
[    0.128096] PM: Registering ACPI NVS region [mem 0x7fecd000-0x7fedefff] (73728 bytes)
[    0.128102] reboot: Apple Macmini3,1 series board detected. Selecting PCI-method for reboots.
[    0.129220] pinctrl core: initialized pinctrl subsystem
[    0.129220] regulator-dummy: no parameters
[    0.129220] RTC time: 18:55:22, date: 05/05/14
[    0.129220] NET: Registered protocol family 16
[    0.129220] cpuidle: using governor ladder
[    0.129220] cpuidle: using governor menu
[    0.129220] ACPI: bus type PCI registered
[    0.129220] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.129230] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xf0000000-0xffffffff] (base 0xf0000000)
[    0.129236] PCI: not using MMCONFIG
[    0.129239] PCI: Using configuration type 1 for base access
[    0.132082] bio: create slab <bio-0> at 0
[    0.132126] ACPI: Added _OSI(Module Device)
[    0.132129] ACPI: Added _OSI(Processor Device)
[    0.132131] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.132134] ACPI: Added _OSI(Processor Aggregator Device)
[    0.133178] ACPI : EC: EC description table is found, configuring boot EC
[    0.138876] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.140459] ACPI: SSDT 000000007fecac98 0001F6 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    0.140925] ACPI: Dynamic OEM Table Load:
[    0.140930] ACPI: SSDT           (null) 0001F6 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    0.141066] ACPI: SSDT 000000007fec9c18 0002AD (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    0.141514] ACPI: Dynamic OEM Table Load:
[    0.141518] ACPI: SSDT           (null) 0002AD (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    0.148282] ACPI: SSDT 000000007fecaf18 0000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
[    0.148740] ACPI: Dynamic OEM Table Load:
[    0.148744] ACPI: SSDT           (null) 0000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
[    0.148855] ACPI: SSDT 000000007fec9f18 000085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
[    0.149301] ACPI: Dynamic OEM Table Load:
[    0.149305] ACPI: SSDT           (null) 000085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
[    0.156325] ACPI: Interpreter enabled
[    0.156333] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.156340] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.156360] ACPI: (supports S0 S3 S4 S5)
[    0.156363] ACPI: Using IOAPIC for interrupt routing
[    0.156386] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xf0000000-0xffffffff] (base 0xf0000000)
[    0.158940] PCI: MMCONFIG at [mem 0xf0000000-0xffffffff] reserved in ACPI motherboard resources
[    0.158945] PCI: MMCONFIG for 0000 [bus00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000) (size reduced!)
[    0.198283] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.198516] ACPI: No dock devices found.
[    0.208592] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.208602] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.208912] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.209042] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.209381] PCI host bridge to bus 0000:00
[    0.209385] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.209389] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.209392] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.209396] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.209399] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.209402] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.209406] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.209409] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.209412] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.209415] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.209418] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.209421] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.209425] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.209428] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.209431] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.209435] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.209438] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    0.209441] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfebfffff]
[    0.209459] pci 0000:00:00.0: [10de:0a82] type 00 class 0x060000
[    0.209689] pci 0000:00:00.1: [10de:0a88] type 00 class 0x050000
[    0.209936] pci 0000:00:03.0: [10de:0aae] type 00 class 0x060100
[    0.209949] pci 0000:00:03.0: reg 0x10: [io  0x2000-0x20ff]
[    0.210122] pci 0000:00:03.1: [10de:0aa4] type 00 class 0x050000
[    0.210316] pci 0000:00:03.2: [10de:0aa2] type 00 class 0x0c0500
[    0.210332] pci 0000:00:03.2: reg 0x10: [io  0x2180-0x21bf]
[    0.210352] pci 0000:00:03.2: reg 0x20: [io  0x2140-0x217f]
[    0.210360] pci 0000:00:03.2: reg 0x24: [io  0x2100-0x213f]
[    0.210400] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.210547] pci 0000:00:03.3: [10de:0a89] type 00 class 0x050000
[    0.210783] pci 0000:00:03.4: [10de:0a98] type 00 class 0x050000
[    0.210961] pci 0000:00:03.5: [10de:0aa3] type 00 class 0x0b4000
[    0.210983] pci 0000:00:03.5: reg 0x10: [mem 0x93400000-0x9347ffff]
[    0.211237] pci 0000:00:04.0: [10de:0aa5] type 00 class 0x0c0310
[    0.211253] pci 0000:00:04.0: reg 0x10: [mem 0x93488000-0x93488fff]
[    0.211312] pci 0000:00:04.0: supports D1 D2
[    0.211315] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.211415] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.211464] pci 0000:00:04.1: [10de:0aa6] type 00 class 0x0c0320
[    0.211482] pci 0000:00:04.1: reg 0x10: [mem 0x93489200-0x934892ff]
[    0.211553] pci 0000:00:04.1: supports D1 D2
[    0.211556] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.211657] pci 0000:00:04.1: System wakeup disabled by ACPI
[    0.211713] pci 0000:00:06.0: [10de:0aa7] type 00 class 0x0c0310
[    0.211729] pci 0000:00:06.0: reg 0x10: [mem 0x93487000-0x93487fff]
[    0.211788] pci 0000:00:06.0: supports D1 D2
[    0.211791] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.211893] pci 0000:00:06.0: System wakeup disabled by ACPI
[    0.211944] pci 0000:00:06.1: [10de:0aa9] type 00 class 0x0c0320
[    0.211961] pci 0000:00:06.1: reg 0x10: [mem 0x93489100-0x934891ff]
[    0.212035] pci 0000:00:06.1: supports D1 D2
[    0.212038] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212140] pci 0000:00:06.1: System wakeup disabled by ACPI
[    0.212197] pci 0000:00:08.0: [10de:0ac0] type 00 class 0x040300
[    0.212211] pci 0000:00:08.0: reg 0x10: [mem 0x93480000-0x93483fff]
[    0.212261] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.212399] pci 0000:00:09.0: [10de:0aab] type 01 class 0x060401
[    0.212569] pci 0000:00:0a.0: [10de:0ab0] type 00 class 0x020000
[    0.212586] pci 0000:00:0a.0: reg 0x10: [mem 0x93486000-0x93486fff]
[    0.212594] pci 0000:00:0a.0: reg 0x14: [io  0x21e0-0x21e7]
[    0.212603] pci 0000:00:0a.0: reg 0x18: [mem 0x93489000-0x934890ff]
[    0.212611] pci 0000:00:0a.0: reg 0x1c: [mem 0x93489300-0x9348930f]
[    0.212661] pci 0000:00:0a.0: supports D1 D2
[    0.212664] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212783] pci 0000:00:0a.0: System wakeup disabled by ACPI
[    0.212838] pci 0000:00:0b.0: [10de:0ab9] type 00 class 0x010601
[    0.212854] pci 0000:00:0b.0: reg 0x10: [io  0x21d8-0x21df]
[    0.212862] pci 0000:00:0b.0: reg 0x14: [io  0x21ec-0x21ef]
[    0.212871] pci 0000:00:0b.0: reg 0x18: [io  0x21d0-0x21d7]
[    0.212879] pci 0000:00:0b.0: reg 0x1c: [io  0x21e8-0x21eb]
[    0.212887] pci 0000:00:0b.0: reg 0x20: [io  0x21c0-0x21cf]
[    0.212896] pci 0000:00:0b.0: reg 0x24: [mem 0x93484000-0x93485fff]
[    0.213072] pci 0000:00:10.0: [10de:0aa0] type 01 class 0x060400
[    0.213127] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213310] pci 0000:00:15.0: [10de:0ac6] type 01 class 0x060400
[    0.213545] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213765] pci 0000:00:16.0: [10de:0ac7] type 01 class 0x060400
[    0.214000] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.214254] pci 0000:00:09.0: PCI bridge to [bus 01] (subtractive decode)
[    0.214261] pci 0000:00:09.0:   bridge window [mem 0x93300000-0x933fffff]
[    0.214266] pci 0000:00:09.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.214270] pci 0000:00:09.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.214273] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.214277] pci 0000:00:09.0:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.214280] pci 0000:00:09.0:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.214283] pci 0000:00:09.0:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.214287] pci 0000:00:09.0:   bridge window [mem 0x000cc000-0x000cffff] (subtractive decode)
[    0.214290] pci 0000:00:09.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.214294] pci 0000:00:09.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.214297] pci 0000:00:09.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.214300] pci 0000:00:09.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.214304] pci 0000:00:09.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.214307] pci 0000:00:09.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.214311] pci 0000:00:09.0:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.214314] pci 0000:00:09.0:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.214317] pci 0000:00:09.0:   bridge window [mem 0x000f0000-0x000fffff] (subtractive decode)
[    0.214321] pci 0000:00:09.0:   bridge window [mem 0x80000000-0xfebfffff] (subtractive decode)
[    0.214392] pci 0000:02:00.0: [10de:0861] type 00 class 0x030000
[    0.214410] pci 0000:02:00.0: reg 0x10: [mem 0x92000000-0x92ffffff]
[    0.214425] pci 0000:02:00.0: reg 0x14: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.214439] pci 0000:02:00.0: reg 0x1c: [mem 0x90000000-0x91ffffff 64bit pref]
[    0.214449] pci 0000:02:00.0: reg 0x24: [io  0x1000-0x107f]
[    0.214459] pci 0000:02:00.0: reg 0x30: [mem 0x93000000-0x9301ffff pref]
[    0.214574] pci 0000:00:10.0: PCI bridge to [bus 02]
[    0.214580] pci 0000:00:10.0:   bridge window [io  0x1000-0x1fff]
[    0.214585] pci 0000:00:10.0:   bridge window [mem 0x92000000-0x930fffff]
[    0.214591] pci 0000:00:10.0:   bridge window [mem 0x80000000-0x91ffffff 64bit pref]
[    0.214957] pci 0000:03:00.0: [14e4:4328] type 00 class 0x028000
[    0.214981] pci 0000:03:00.0: reg 0x10: [mem 0x93200000-0x93203fff 64bit]
[    0.215092] pci 0000:03:00.0: supports D1 D2
[    0.215095] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.220219] pci 0000:00:15.0: PCI bridge to [bus 03]
[    0.220242] pci 0000:00:15.0:   bridge window [mem 0x93200000-0x932fffff]
[    0.220430] pci 0000:04:00.0: [11c1:5901] type 00 class 0x0c0010
[    0.220455] pci 0000:04:00.0: reg 0x10: [mem 0x93100000-0x93100fff 64bit]
[    0.220563] pci 0000:04:00.0: supports D1 D2
[    0.220567] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.228025] pci 0000:00:16.0: PCI bridge to [bus 04]
[    0.228047] pci 0000:00:16.0:   bridge window [mem 0x93100000-0x931fffff]
[    0.228556] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *16
[    0.228693] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 11 14 15) *16
[    0.228828] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *16
[    0.228961] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *16
[    0.229095] ACPI: PCI Interrupt Link [Z003] (IRQs *16 17 18 19 20 21 22 23)
[    0.229229] ACPI: PCI Interrupt Link [Z004] (IRQs *16 17 18 19 20 21 22 23)
[    0.229363] ACPI: PCI Interrupt Link [Z005] (IRQs *16 17 18 19 20 21 22 23)
[    0.229497] ACPI: PCI Interrupt Link [Z006] (IRQs *16 17 18 19 20 21 22 23)
[    0.229628] ACPI: PCI Interrupt Link [Z007] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.229760] ACPI: PCI Interrupt Link [Z008] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.229892] ACPI: PCI Interrupt Link [Z009] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.230025] ACPI: PCI Interrupt Link [Z00A] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.230157] ACPI: PCI Interrupt Link [Z00B] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.230290] ACPI: PCI Interrupt Link [Z00C] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.230427] ACPI: PCI Interrupt Link [Z00D] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.230559] ACPI: PCI Interrupt Link [Z00E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.230695] ACPI: PCI Interrupt Link [Z00F] (IRQs 16 17 18 19 20 *21 22 23)
[    0.230829] ACPI: PCI Interrupt Link [Z00G] (IRQs 16 17 18 19 20 *21 22 23)
[    0.230963] ACPI: PCI Interrupt Link [Z00H] (IRQs 16 17 18 19 20 *21 22 23)
[    0.231098] ACPI: PCI Interrupt Link [Z00I] (IRQs 16 17 18 19 20 *21 22 23)
[    0.231233] ACPI: PCI Interrupt Link [Z00J] (IRQs 16 17 18 *19 20 21 22 23)
[    0.231369] ACPI: PCI Interrupt Link [Z00K] (IRQs 16 17 18 *19 20 21 22 23)
[    0.231503] ACPI: PCI Interrupt Link [Z00L] (IRQs 16 17 18 *19 20 21 22 23)
[    0.231638] ACPI: PCI Interrupt Link [Z00M] (IRQs 16 17 18 *19 20 21 22 23)
[    0.231772] ACPI: PCI Interrupt Link [Z00N] (IRQs 16 17 18 19 20 21 22 *23)
[    0.231906] ACPI: PCI Interrupt Link [Z00O] (IRQs 16 17 18 19 20 21 22 *23)
[    0.232048] ACPI: PCI Interrupt Link [Z00P] (IRQs 16 17 18 19 20 21 22 *23)
[    0.232183] ACPI: PCI Interrupt Link [Z00Q] (IRQs 16 17 18 19 20 21 22 *23)
[    0.232318] ACPI: PCI Interrupt Link [Z00R] (IRQs 16 17 18 19 20 21 22 *23)
[    0.232453] ACPI: PCI Interrupt Link [Z00S] (IRQs 16 17 18 19 20 21 22 *23)
[    0.232590] ACPI: PCI Interrupt Link [Z00T] (IRQs 16 17 18 19 20 21 22 *23)
[    0.232726] ACPI: PCI Interrupt Link [Z00U] (IRQs 16 17 18 19 20 21 22 *23)
[    0.232865] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 *22 23)
[    0.232999] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 *17 18 19 20 21 22 23)
[    0.233132] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 *22 23)
[    0.233265] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 *17 18 19 20 21 22 23)
[    0.233398] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 *20 21 22 23)
[    0.233531] ACPI: PCI Interrupt Link [LGPU] (IRQs *16 17 18 19 20 21 22 23)
[    0.233662] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.233798] ACPI: PCI Interrupt Link [LSI0] (IRQs 16 17 *18 19 20 21 22 23)
[    0.233930] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 *18 19 20 21 22 23)
[    0.234063] ACPI: PCI Interrupt Link [Z000] (IRQs 16 17 *18 19 20 21 22 23)
[    0.234195] ACPI: PCI Interrupt Link [Z001] (IRQs 16 17 18 19 20 21 22 *23)
[    0.234325] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.234839] ACPI: Enabled 3 GPEs in block 00 to 1F
[    0.234850] ACPI: Enabled 1 GPEs in block 20 to 5F
[    0.234860] ACPI: \_SB_.PCI0: notify handler is installed
[    0.234946] Found 1 acpi root devices
[    0.234978] ACPI : EC: GPE = 0x3f, I/O: command/status = 0x66, data = 0x62
[    0.235092] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
[    0.235092] vgaarb: loaded
[    0.235092] vgaarb: bridge control possible 0000:02:00.0
[    0.235092] SCSI subsystem initialized
[    0.235092] libata version 3.00 loaded.
[    0.235092] ACPI: bus type USB registered
[    0.235092] usbcore: registered new interface driver usbfs
[    0.235092] usbcore: registered new interface driver hub
[    0.235092] usbcore: registered new device driver usb
[    0.235092] PCI: Using ACPI for IRQ routing
[    0.237780] PCI: pci_cache_line_size set to 64 bytes
[    0.238256] e820: reserve RAM buffer [mem 0x0008f000-0x0008ffff]
[    0.238260] e820: reserve RAM buffer [mem 0x7e484000-0x7fffffff]
[    0.238275] e820: reserve RAM buffer [mem 0x7e4b4000-0x7fffffff]
[    0.238290] e820: reserve RAM buffer [mem 0x7e4b7000-0x7fffffff]
[    0.238305] e820: reserve RAM buffer [mem 0x7e6cc000-0x7fffffff]
[    0.238320] e820: reserve RAM buffer [mem 0x7e797000-0x7fffffff]
[    0.238334] e820: reserve RAM buffer [mem 0x7e822000-0x7fffffff]
[    0.238348] e820: reserve RAM buffer [mem 0x7e849000-0x7fffffff]
[    0.238362] e820: reserve RAM buffer [mem 0x7e84f000-0x7fffffff]
[    0.238376] e820: reserve RAM buffer [mem 0x7e856000-0x7fffffff]
[    0.238389] e820: reserve RAM buffer [mem 0x7e859000-0x7fffffff]
[    0.238402] e820: reserve RAM buffer [mem 0x7e860000-0x7fffffff]
[    0.238415] e820: reserve RAM buffer [mem 0x7e863000-0x7fffffff]
[    0.238427] e820: reserve RAM buffer [mem 0x7e867000-0x7fffffff]
[    0.238439] e820: reserve RAM buffer [mem 0x7e873000-0x7fffffff]
[    0.238451] e820: reserve RAM buffer [mem 0x7e97d000-0x7fffffff]
[    0.238462] e820: reserve RAM buffer [mem 0x7e980000-0x7fffffff]
[    0.238473] e820: reserve RAM buffer [mem 0x7e99b000-0x7fffffff]
[    0.238484] e820: reserve RAM buffer [mem 0x7e9fc000-0x7fffffff]
[    0.238494] e820: reserve RAM buffer [mem 0x7ea07000-0x7fffffff]
[    0.238503] e820: reserve RAM buffer [mem 0x7ea0c000-0x7fffffff]
[    0.238512] e820: reserve RAM buffer [mem 0x7ea0f000-0x7fffffff]
[    0.238521] e820: reserve RAM buffer [mem 0x7eed6000-0x7fffffff]
[    0.238529] e820: reserve RAM buffer [mem 0x7eed9000-0x7fffffff]
[    0.238536] e820: reserve RAM buffer [mem 0x7eee1000-0x7fffffff]
[    0.238543] e820: reserve RAM buffer [mem 0x7eee6000-0x7fffffff]
[    0.238549] e820: reserve RAM buffer [mem 0x7fa87000-0x7fffffff]
[    0.238555] e820: reserve RAM buffer [mem 0x7fe9e000-0x7fffffff]
[    0.238561] e820: reserve RAM buffer [mem 0x7fec6000-0x7fffffff]
[    0.238566] e820: reserve RAM buffer [mem 0x7fef9000-0x7fffffff]
[    0.238690] NetLabel: Initializing
[    0.238693] NetLabel:  domain hash size = 128
[    0.238695] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.238716] NetLabel:  unlabeled traffic allowed by default
[    0.238737] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.238737] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.238737] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.240051] Switched to clocksource hpet
[    0.250332] AppArmor: AppArmor Filesystem Enabled
[    0.250378] pnp: PnP ACPI init
[    0.250401] ACPI: bus type PNP registered
[    0.250567] system 00:00: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.250573] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.250632] pnp 00:01: Plug and Play ACPI device, IDs APP0001 (active)
[    0.250652] pnp 00:02: [dma 4]
[    0.250682] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.250830] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.250836] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.250881] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.251074] system 00:05: [io  0x0400-0x047f] could not be reserved
[    0.251078] system 00:05: [io  0x0480-0x04ff] has been reserved
[    0.251082] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.251086] system 00:05: [io  0x0580-0x05ff] has been reserved
[    0.251089] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.251093] system 00:05: [io  0x0880-0x08ff] has been reserved
[    0.251097] system 00:05: [io  0x2140-0x217f] has been reserved
[    0.251101] system 00:05: [io  0x2100-0x213f] has been reserved
[    0.251105] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.251109] system 00:05: [io  0x0295-0x0296] has been reserved
[    0.251114] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.251151] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.252047] pnp: PnP ACPI: found 7 devices
[    0.252050] ACPI: bus type PNP unregistered
[    0.259660] pci 0000:00:09.0: PCI bridge to [bus 01]
[    0.259669] pci 0000:00:09.0:   bridge window [mem 0x93300000-0x933fffff]
[    0.259678] pci 0000:00:10.0: PCI bridge to [bus 02]
[    0.259682] pci 0000:00:10.0:   bridge window [io  0x1000-0x1fff]
[    0.259688] pci 0000:00:10.0:   bridge window [mem 0x92000000-0x930fffff]
[    0.259693] pci 0000:00:10.0:   bridge window [mem 0x80000000-0x91ffffff 64bit pref]
[    0.259699] pci 0000:00:15.0: PCI bridge to [bus 03]
[    0.259711] pci 0000:00:15.0:   bridge window [mem 0x93200000-0x932fffff]
[    0.259732] pci 0000:00:16.0: PCI bridge to [bus 04]
[    0.259744] pci 0000:00:16.0:   bridge window [mem 0x93100000-0x931fffff]
[    0.259765] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.259769] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.259772] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.259775] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.259779] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.259782] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.259785] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.259788] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.259791] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.259795] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.259798] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.259801] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.259804] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.259807] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.259810] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.259813] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.259817] pci_bus 0000:00: resource 20 [mem 0x80000000-0xfebfffff]
[    0.259820] pci_bus 0000:01: resource 1 [mem 0x93300000-0x933fffff]
[    0.259824] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.259827] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.259830] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.259834] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.259837] pci_bus 0000:01: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.259840] pci_bus 0000:01: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.259844] pci_bus 0000:01: resource 10 [mem 0x000cc000-0x000cffff]
[    0.259847] pci_bus 0000:01: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.259850] pci_bus 0000:01: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.259853] pci_bus 0000:01: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.259856] pci_bus 0000:01: resource 14 [mem 0x000dc000-0x000dffff]
[    0.259859] pci_bus 0000:01: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.259862] pci_bus 0000:01: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.259865] pci_bus 0000:01: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.259868] pci_bus 0000:01: resource 18 [mem 0x000ec000-0x000effff]
[    0.259872] pci_bus 0000:01: resource 19 [mem 0x000f0000-0x000fffff]
[    0.259875] pci_bus 0000:01: resource 20 [mem 0x80000000-0xfebfffff]
[    0.259878] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.259882] pci_bus 0000:02: resource 1 [mem 0x92000000-0x930fffff]
[    0.259885] pci_bus 0000:02: resource 2 [mem 0x80000000-0x91ffffff 64bit pref]
[    0.259889] pci_bus 0000:03: resource 1 [mem 0x93200000-0x932fffff]
[    0.259892] pci_bus 0000:04: resource 1 [mem 0x93100000-0x931fffff]
[    0.259939] NET: Registered protocol family 2
[    0.260165] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.260265] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.260397] TCP: Hash tables configured (established 16384 bind 16384)
[    0.260452] TCP: reno registered
[    0.260460] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.260485] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.260576] NET: Registered protocol family 1
[    0.260993] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 17
[    0.316503] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.316999] ACPI: PCI Interrupt Link [Z000] enabled at IRQ 18
[    0.372496] ACPI: PCI Interrupt Link [Z001] enabled at IRQ 23
[    0.372985] PCI: CLS 256 bytes, default 64
[    0.373071] Trying to unpack rootfs image as initramfs...
[    0.873321] Freeing initrd memory: 18596K (ffff880035b9e000 - ffff880036dc7000)
[    0.873610] microcode: CPU0 sig=0x1067a, pf=0x80, revision=0xa07
[    0.873619] microcode: CPU1 sig=0x1067a, pf=0x80, revision=0xa07
[    0.873727] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.873730] Scanning for low memory corruption every 60 seconds
[    0.873741] efifb: dmi detected Macmini3,1 - framebuffer at 0x80010000 (1440x900, stride 8192)
[    0.874054] Initialise system trusted keyring
[    0.874128] audit: initializing netlink socket (disabled)
[    0.874146] type=2000 audit(1399316122.872:1): initialized
[    0.915642] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.917728] VFS: Disk quotas dquot_6.5.2
[    0.917796] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.918525] fuse init (API version 7.22)
[    0.918645] msgmni has been set to 3487
[    0.918724] Key type big_key registered
[    0.919241] Key type asymmetric registered
[    0.919245] Asymmetric key parser 'x509' registered
[    0.919295] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.919340] io scheduler noop registered
[    0.919343] io scheduler deadline registered (default)
[    0.919382] io scheduler cfq registered
[    0.919892] ACPI: PCI Interrupt Link [Z00F] enabled at IRQ 21
[    0.919975] pcieport 0000:00:15.0: irq 40 for MSI/MSI-X
[    0.920484] ACPI: PCI Interrupt Link [Z00J] enabled at IRQ 19
[    0.920554] pcieport 0000:00:16.0: irq 41 for MSI/MSI-X
[    0.920760] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    0.920764] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.920773] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    0.920816] pcieport 0000:00:16.0: Signaling PME through PCIe PME interrupt
[    0.920820] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.920829] pcie_pme 0000:00:16.0:pcie01: service driver pcie_pme loaded
[    0.920849] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.920870] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.920943] efifb: probing for efifb
[    0.926090] efifb: framebuffer at 0x80010000, mapped to 0xffffc90004400000, using 7232k, total 7232k
[    0.926093] efifb: mode is 1440x900x32, linelength=8192, pages=1
[    0.926095] efifb: scrolling: redraw
[    0.926098] efifb: Truecolor: size=8:8:8:8, shift=24:0:8:16
[    0.931188] Console: switching to colour frame buffer device 180x56
[    0.936150] fb0: EFI VGA frame buffer device
[    0.936177] intel_idle: does not run on family 6 model 23
[    0.936186] ipmi message handler version 39.2
[    0.936265] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.936272] ACPI: Power Button [PWRB]
[    0.936326] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.936330] ACPI: Sleep Button [SLPB]
[    0.936435] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.936439] ACPI: Power Button [PWRF]
[    0.936580] Monitor-Mwait will be used to enter C-1 state
[    0.936589] Monitor-Mwait will be used to enter C-2 state
[    0.936596] Monitor-Mwait will be used to enter C-3 state
[    0.936600] tsc: Marking TSC unstable due to TSC halts in idle
[    0.936612] ACPI: acpi_idle registered with cpuidle
[    0.936940] GHES: HEST is not enabled!
[    0.937057] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.939461] Linux agpgart interface v0.103
[    0.941715] brd: module loaded
[    0.942875] loop: module loaded
[    0.943445] libphy: Fixed MDIO Bus: probed
[    0.943584] tun: Universal TUN/TAP device driver, 1.6
[    0.943586] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.943658] PPP generic driver version 2.4.2
[    0.943731] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.943737] ehci-pci: EHCI PCI platform driver
[    0.943960] ehci-pci 0000:00:04.1: EHCI Host Controller
[    0.943970] ehci-pci 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.943982] ehci-pci 0000:00:04.1: debug port 1
[    0.944039] ehci-pci 0000:00:04.1: cache line size of 256 is not supported
[    0.944078] ehci-pci 0000:00:04.1: irq 22, io mem 0x93489200
[    0.956042] ehci-pci 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.956119] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.956123] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.956126] usb usb1: Product: EHCI Host Controller
[    0.956130] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    0.956133] usb usb1: SerialNumber: 0000:00:04.1
[    0.956298] hub 1-0:1.0: USB hub found
[    0.956314] hub 1-0:1.0: 7 ports detected
[    0.956807] ehci-pci 0000:00:06.1: EHCI Host Controller
[    0.956816] ehci-pci 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.956826] ehci-pci 0000:00:06.1: debug port 1
[    0.956855] ehci-pci 0000:00:06.1: cache line size of 256 is not supported
[    0.956876] ehci-pci 0000:00:06.1: irq 23, io mem 0x93489100
[    0.968126] ehci-pci 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.968222] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.968226] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.968229] usb usb2: Product: EHCI Host Controller
[    0.968233] usb usb2: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    0.968236] usb usb2: SerialNumber: 0000:00:06.1
[    0.968469] hub 2-0:1.0: USB hub found
[    0.968485] hub 2-0:1.0: 5 ports detected
[    0.968807] ehci-platform: EHCI generic platform driver
[    0.968827] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.968830] ohci-pci: OHCI PCI platform driver
[    0.969061] ohci-pci 0000:00:04.0: OHCI PCI host controller
[    0.969072] ohci-pci 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.969117] ohci-pci 0000:00:04.0: irq 17, io mem 0x93488000
[    1.026186] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.026192] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.026195] usb usb3: Product: OHCI PCI host controller
[    1.026199] usb usb3: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.026202] usb usb3: SerialNumber: 0000:00:04.0
[    1.026419] hub 3-0:1.0: USB hub found
[    1.026433] hub 3-0:1.0: 7 ports detected
[    1.026977] ohci-pci 0000:00:06.0: OHCI PCI host controller
[    1.026989] ohci-pci 0000:00:06.0: new USB bus registered, assigned bus number 4
[    1.027023] ohci-pci 0000:00:06.0: irq 18, io mem 0x93487000
[    1.082179] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.082185] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.082189] usb usb4: Product: OHCI PCI host controller
[    1.082192] usb usb4: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.082195] usb usb4: SerialNumber: 0000:00:06.0
[    1.082418] hub 4-0:1.0: USB hub found
[    1.082432] hub 4-0:1.0: 5 ports detected
[    1.082742] ohci-platform: OHCI generic platform driver
[    1.082761] uhci_hcd: USB Universal Host Controller Interface driver
[    1.082853] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.110095] i8042: No controller found
[    2.110208] mousedev: PS/2 mouse device common for all mice
[    2.110786] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.110843] rtc_cmos 00:06: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.110934] device-mapper: uevent: version 1.0.3
[    2.111042] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    2.111051] ledtrig-cpu: registered to indicate activity on CPUs
[    2.111054] EFI Variables Facility v0.08 2004-May-17
[    2.263623] TCP: cubic registered
[    2.263761] NET: Registered protocol family 10
[    2.264019] NET: Registered protocol family 17
[    2.264034] Key type dns_resolver registered
[    2.264425] Loading compiled-in X.509 certificates
[    2.266054] Loaded X.509 cert 'Magrathea: Glacier signing key: 00a5a65759de474bc5c43120880c1b94a539f431'
[    2.266084] registered taskstats version 1
[    2.270041] Key type trusted registered
[    2.273511] Key type encrypted registered
[    2.276983] AppArmor: AppArmor sha1 policy hashing enabled
[    2.276988] IMA: No TPM chip found, activating TPM-bypass!
[    2.277771] regulator-dummy: disabling
[    2.277845]   Magic number: 14:169:948
[    2.277901] tty tty5: hash matches
[    2.277950] memory memory1: hash matches
[    2.278026] rtc_cmos 00:06: setting system clock to 2014-05-05 18:55:25 UTC (1399316125)
[    2.278611] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.278613] EDD information not available.
[    2.278809] PM: Hibernation image not present or could not be loaded.
[    2.280713] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[    2.280716] Write protecting the kernel read-only data: 12288k
[    2.283896] Freeing unused kernel memory: 844K (ffff88000272d000 - ffff880002800000)
[    2.286433] Freeing unused kernel memory: 708K (ffff880002b4f000 - ffff880002c00000)
[    2.303343] systemd-udevd[98]: starting version 204
[    2.341593] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.341924] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    2.350084] firewire_ohci 0000:04:00.0: irq 42 for MSI/MSI-X
[    2.380292] ssb: Found chip with id 0x4321, rev 0x05 and package 0x00
[    2.380301] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x13, vendor 0x4243)
[    2.380307] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0C, vendor 0x4243)
[    2.380314] ssb: Core 2 found: PCI-E (cc 0x820, rev 0x08, vendor 0x4243)
[    2.380320] ssb: Core 3 found: PCI (cc 0x804, rev 0x0D, vendor 0x4243)
[    2.380326] ssb: Core 4 found: USB 1.1 Host (cc 0x817, rev 0x04, vendor 0x4243)
[    2.407979] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:23:df:9d:48:98
[    2.407984] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    2.408529] firewire_ohci 0000:04:00.0: added OHCI v1.10 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    2.408915] ahci 0000:00:0b.0: version 3.0
[    2.409232] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 16
[    2.409291] ahci 0000:00:0b.0: irq 43 for MSI/MSI-X
[    2.409304] ahci 0000:00:0b.0: controller can't do PMP, turning off CAP_PMP
[    2.409355] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl SATA mode
[    2.409359] ahci 0000:00:0b.0: flags: 64bit ncq sntf pm led pio slum part boh 
[    2.410246] scsi0 : ahci
[    2.410353] scsi1 : ahci
[    2.410436] scsi2 : ahci
[    2.410518] scsi3 : ahci
[    2.410599] scsi4 : ahci
[    2.410674] scsi5 : ahci
[    2.410727] ata1: SATA max UDMA/133 abar m8192@0x93484000 port 0x93484100 irq 43
[    2.410730] ata2: SATA max UDMA/133 abar m8192@0x93484000 port 0x93484180 irq 43
[    2.410732] ata3: DUMMY
[    2.410733] ata4: DUMMY
[    2.410735] ata5: DUMMY
[    2.410737] ata6: DUMMY
[    2.428396] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.728093] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.728110] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.729027] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.729256] ata1.00: ATA-8: Hitachi HTS543212L9SA02, FBBAC50F, max UDMA/133
[    2.729260] ata1.00: 234441648 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.730391] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.730622] ata1.00: configured for UDMA/133
[    2.730820] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FBBA PQ: 0 ANSI: 5
[    2.731009] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.731034] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.731103] sd 0:0:0:0: [sda] Write Protect is off
[    2.731107] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.731131] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.738804] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.738815] ata2.00: ATAPI: PIONEER DVD-RW  DVRTS08, Q81B, max UDMA/33
[    2.751235] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.751241] ata2.00: configured for UDMA/33
[    2.782278]  sda: sda1 sda2 sda3
[    2.782671] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.806044] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVRTS08  Q81B PQ: 0 ANSI: 5
[    2.859878] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    2.859882] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.860025] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.860309] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.908153] firewire_core 0000:04:00.0: created device fw0: GUID 0023dffffe9d4898, S800
[    2.916131] usb 2-4: new high-speed USB device number 4 using ehci-pci
[    3.049049] usb 2-4: New USB device found, idVendor=059f, idProduct=1019
[    3.049054] usb 2-4: New USB device strings: Mfr=10, Product=11, SerialNumber=3
[    3.049057] usb 2-4: Product: LaCie Desktop Hard Drive
[    3.049059] usb 2-4: Manufacturer: LaCie
[    3.049062] usb 2-4: SerialNumber: 00E00100D88AA
[    3.053983] usb-storage 2-4:1.0: USB Mass Storage device detected
[    3.054107] scsi6 : usb-storage 2-4:1.0
[    3.054181] usbcore: registered new interface driver usb-storage
[    3.736122] usb 3-3: new low-speed USB device number 2 using ohci-pci
[    3.950214] usb 3-3: New USB device found, idVendor=046d, idProduct=c05a
[    3.950219] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.950222] usb 3-3: Product: USB Optical Mouse
[    3.950226] usb 3-3: Manufacturer: Logitech
[    3.957178] hidraw: raw HID events driver (C) Jiri Kosina
[    3.965500] usbcore: registered new interface driver usbhid
[    3.965503] usbhid: USB HID core driver
[    3.967539] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb3/3-3/3-3:1.0/input/input3
[    3.967658] hid-generic 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:04.0-3/input0
[    4.095074] scsi 6:0:0:0: Direct-Access     Hitachi  HDT721010SLA360       PQ: 0 ANSI: 2 CCS
[    4.095331] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.096559] sd 6:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.099101] sd 6:0:0:0: [sdb] Write Protect is off
[    4.099106] sd 6:0:0:0: [sdb] Mode Sense: 34 00 00 00
[    4.101054] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    4.156316]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 sdb6 >
[    4.163051] sd 6:0:0:0: [sdb] Attached SCSI disk
[    4.256118] usb 3-5: new low-speed USB device number 3 using ohci-pci
[    4.470160] usb 3-5: New USB device found, idVendor=05ac, idProduct=8242
[    4.470166] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.470169] usb 3-5: Product: IR Receiver
[    4.470172] usb 3-5: Manufacturer: Apple Computer, Inc.
[    4.735536] random: nonblocking pool is initialized
[    4.788073] usb 3-7: new low-speed USB device number 4 using ohci-pci
[    5.002157] usb 3-7: New USB device found, idVendor=046d, idProduct=c315
[    5.002162] usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.002165] usb 3-7: Product: Logitech USB Keyboard
[    5.002168] usb 3-7: Manufacturer: Logitech
[    5.013696] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7:1.0/input/input4
[    5.013864] hid-generic 0003:046D:C315.0003: input,hidraw1: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:04.0-7/input0
[    5.177685] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[    5.320118] usb 4-1: new full-speed USB device number 2 using ohci-pci
[    5.541210] usb 4-1: New USB device found, idVendor=0a5c, idProduct=4500
[    5.541215] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.541218] usb 4-1: Product: BRCM2046 Hub
[    5.541221] usb 4-1: Manufacturer: Apple Inc.
[    5.544220] hub 4-1:1.0: USB hub found
[    5.547161] hub 4-1:1.0: 3 ports detected
[    5.864036] usb 4-2: new full-speed USB device number 3 using ohci-pci
[    6.082156] usb 4-2: New USB device found, idVendor=1415, idProduct=0000
[    6.082163] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.082166] usb 4-2: Product: USBMIC Serial# 091204423 
[    6.082170] usb 4-2: Manufacturer: Nam Tai E&E Products Ltd.
[    6.421165] usb 4-1.1: new full-speed USB device number 4 using ohci-pci
[    6.544166] usb 4-1.1: New USB device found, idVendor=05ac, idProduct=8216
[    6.544171] usb 4-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    6.544175] usb 4-1.1: Product: Bluetooth USB Host Controller
[    6.544178] usb 4-1.1: Manufacturer: Apple Inc.
[    6.544181] usb 4-1.1: SerialNumber: 002436EB681B
[    6.621163] usb 4-1.2: new full-speed USB device number 5 using ohci-pci
[    6.732169] usb 4-1.2: New USB device found, idVendor=05ac, idProduct=820a
[    6.732175] usb 4-1.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    6.741633] input: HID 05ac:820a as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.2/4-1.2:1.0/input/input5
[    6.741729] hid-generic 0003:05AC:820A.0004: input,hidraw2: USB HID v1.11 Keyboard [HID 05ac:820a] on usb-0000:00:06.0-1.2/input0
[    6.817160] usb 4-1.3: new full-speed USB device number 6 using ohci-pci
[    6.928186] usb 4-1.3: New USB device found, idVendor=05ac, idProduct=820b
[    6.928191] usb 4-1.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    6.937644] input: HID 05ac:820b as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.3/4-1.3:1.0/input/input6
[    6.937829] hid-generic 0003:05AC:820B.0005: input,hidraw3: USB HID v1.11 Mouse [HID 05ac:820b] on usb-0000:00:06.0-1.3/input0
[   21.787367] Adding 3999740k swap on /dev/sdb5.  Priority:-1 extents:1 across:3999740k FS
[   21.818374] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.932905] systemd-udevd[337]: starting version 204
[   22.045876] lp: driver loaded but no devices found
[   22.056500] ppdev: user-space parallel port driver
[   22.082975] i2c i2c-0: nForce2 SMBus adapter at 0x2140
[   22.083014] i2c i2c-1: nForce2 SMBus adapter at 0x2100
[   22.159892] [drm] Initialized drm 1.1.0 20060810
[   22.174856] nvidia: module license 'NVIDIA' taints kernel.
[   22.174861] Disabling lock debugging due to kernel taint
[   22.195692] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   22.211149] EXT4-fs (sdb6): re-mounted. Opts: errors=remount-ro
[   22.252998] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 23
[   22.253040] nvidia: probe of 0000:00:03.5 failed with error -1
[   22.253115] nvidia 0000:02:00.0: enabling device (0002 -> 0003)
[   22.253283] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   22.253410] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[   22.254006] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:02:00.0 on minor 0
[   22.254291] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.38  Wed Jan  8 19:32:30 PST 2014
[   22.276027] Bluetooth: Core ver 2.17
[   22.282247] NET: Registered protocol family 31
[   22.282252] Bluetooth: HCI device and connection manager initialized
[   22.284462] Bluetooth: HCI socket layer initialized
[   22.284468] Bluetooth: L2CAP socket layer initialized
[   22.284477] Bluetooth: SCO socket layer initialized
[   22.289102] type=1400 audit(1399316145.507:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=409 comm="apparmor_parser"
[   22.289111] type=1400 audit(1399316145.507:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=409 comm="apparmor_parser"
[   22.289116] type=1400 audit(1399316145.507:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=409 comm="apparmor_parser"
[   22.289683] type=1400 audit(1399316145.507:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=409 comm="apparmor_parser"
[   22.289691] type=1400 audit(1399316145.507:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=409 comm="apparmor_parser"
[   22.289983] type=1400 audit(1399316145.507:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=409 comm="apparmor_parser"
[   22.331028] usbcore: registered new interface driver btusb
[   22.345440] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.366277] usb 4-1.2: USB disconnect, device number 5
[   22.371752] input: Apple Computer, Inc. IR Receiver as /devices/pci0000:00/0000:00:04.0/usb3/3-5/3-5:1.0/input/input7
[   22.424960] appleir 0003:05AC:8242.0002: input,hiddev0,hidraw2: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
[   22.448257] cfg80211: Calling CRDA to update world regulatory domain
[   22.498397] snd_hda_intel 0000:00:08.0: enabling device (0000 -> 0002)
[   22.498706] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   22.498716] hda_intel: Disabling MSI
[   22.498769] hda-intel 0000:00:08.0: Disabling 64bit DMA
[   22.510557] b43-phy0: Broadcom 4321 WLAN found (core revision 12)
[   22.515545] hda-intel 0000:00:08.0: Enable delay in RIRB handling
[   22.563127] b43-phy0: Found PHY: Analog 5, Type 4 (N), Revision 2
[   22.590561] Broadcom 43xx driver loaded [ Features: PNL ]
[   22.598148] usb 4-1.3: USB disconnect, device number 6
[   22.654510] usbcore: registered new interface driver snd-usb-audio
[   22.822465] applesmc: key=154 fan=1 temp=8 index=8 acc=0 lux=0 kbd=0
[   22.952065] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   23.021229] cfg80211: World regulatory domain updated:
[   23.021234] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.021237] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.021240] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.021242] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.021244] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.021246] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.107519] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.107523] Bluetooth: BNEP filters: protocol multicast
[   23.107536] Bluetooth: BNEP socket layer initialized
[   23.121294] Bluetooth: RFCOMM TTY layer initialized
[   23.121308] Bluetooth: RFCOMM socket layer initialized
[   23.121321] Bluetooth: RFCOMM ver 1.11
[   23.132075] hda_codec: ALC889A: SKU not ready 0x400000f0
[   23.172032] autoconfig: line_outs=1 (0x18/0x0/0x0/0x0/0x0) type:speaker
[   23.172037]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   23.172039]    hp_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   23.172041]    mono: mono_out=0x0
[   23.172043]    dig-out=0x1e/0x0
[   23.172044]    inputs:
[   23.172046]      Line=0x15
[   23.172048]    dig-in=0x1f
[   23.172051] realtek: No valid SSID, checking pincfg 0x400000f0 for NID 0x1d
[   23.172052] realtek: Enable default setup for auto mode as fallback
[   23.225969] type=1400 audit(1399316146.443:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=622 comm="apparmor_parser"
[   23.225979] type=1400 audit(1399316146.443:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=622 comm="apparmor_parser"
[   23.230805] type=1400 audit(1399316146.447:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=622 comm="apparmor_parser"
[   23.428423] init: failsafe main process (606) killed by TERM signal
[   23.428841] init: cups main process (640) killed by HUP signal
[   23.428858] init: cups main process ended, respawning
[   23.705640] type=1400 audit(1399316146.923:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=783 comm="apparmor_parser"
[   23.772974] forcedeth 0000:00:0a.0: irq 44 for MSI/MSI-X
[   23.773010] forcedeth 0000:00:0a.0 eth0: MSI enabled
[   23.773234] forcedeth 0000:00:0a.0 eth0: no link during initialization
[   23.773653] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.774101] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.956230] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   24.052909] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.053330] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.320183] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input9
[   24.320433] input: HDA NVidia Line as /devices/pci0000:00/0000:00:08.0/sound/card0/input8
[   24.522415] init: udev-fallback-graphics main process (947) terminated with status 1
[   25.069707] init: gdm main process (926) killed by TERM signal
[   26.053814] Ebtables v2.0 registered
[   26.295227] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.310562] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   26.727923] nvidia 0000:02:00.0: irq 45 for MSI/MSI-X
[   26.740621] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   26.740666] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   26.740688] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   26.740710] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   26.740731] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   26.740752] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   26.740773] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   26.740794] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   27.099101] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   27.120331] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   27.164331] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   27.188267] ACPI Warning: \_SB_.PCI0.IXVE.IGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   27.532555] Bridge firewalling registered
[   27.650928] init: plymouth-upstart-bridge main process (167) killed by TERM signal
[   27.712848] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   27.729483] cgroup: systemd-logind (623) created nested cgroup for controller "memory" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[   27.729487] cgroup: "memory" requires setting use_hierarchy to 1 on the root.
[   27.768673] IPv6: ADDRCONF(NETDEV_UP): virbr0: link is not ready
[   39.923842] FAT-fs (sdb2): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[   53.390743] audit_printk_skb: 156 callbacks suppressed
[   53.390747] type=1400 audit(1399316176.607:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2230 comm="apparmor_parser"
[   53.390756] type=1400 audit(1399316176.607:65): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2230 comm="apparmor_parser"
[   53.391317] type=1400 audit(1399316176.607:66): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2230 comm="apparmor_parser"

```

I'm sorry for the enormous amount of data, but I'd rather give too much than too little.

Thanks in advance, for anybody that could help me :)

Gr. Emile

---

### Post by harobed on 2014-05-06
Personnaly I did :

```


$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
$ sudo apt-get install linux-firmware-nonfree
$ sudo reboot

```

I reported this bug here : [https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/1316816](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/1316816)

---

### Post by Ertyui on 2014-05-06
Thanks for your answer! Unfortunately this would give me my current setup already.
I have all modules purged except for linux-firmware-nonfree. I know this module works, it just works very occasionally..

---

### Post by Ertyui on 2014-05-07
Or perhaps there are other diagnostics I could run?

---

### Post by Ertyui on 2014-05-13
Ok so now it doesn't work at all anymore. It is very frustrating as normally everything works just fine.

---

### Post by Hadaka on 2014-05-13
hi, please copy and paste ...
```
 grep -v "*" /etc/motd
lspci -n | egrep '0200|0280' | awk '{print$3}'
lsmod | egrep 'wl|b43'
rfkill list all
```
post the output..
thanks

---

### Post by Ertyui on 2014-05-14
Hello!
Thank you very much for your reply.
The first command didn't work, because that file doesn't exist.

The other commands give the following output:
```

**$lspci -n | egrep '0200|0280'| awk '{print$3}' :**
10de:0ab0
14e4:4328

**$lsmod | egrep 'wl|b43':**
b43                   387371  0 
bcma                   52096  1 b43
mac80211              626489  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  2 b43,ssb_hcd

**$rfkill list all:**
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Hope this will give you what you need!

Thanks again!

Gr. Emile

---

### Post by Hadaka on 2014-05-14
Hi, please try the first command again.
```
grep -v "*" /etc/motd
```
then please COPY and paste..
```
sudo su
touch /etc/modprobe.d/b43.conf
echo "options b43 nohwcrypt=1" >> /etc/modprobe.db43.conf
exit 0
```
BOOT 
then do...to verify..
```
cat /etc/modprobe.d/b43.conf
```
is the connection now more stable?

---

### Post by Ertyui on 2014-05-14
Well, it is definitely a bit more stable.
Out of the now +- 7 reboots I got wifi 3 times.
So thanks already for that :D

To answer your questions this is the output of the first command:
```

**$ grep -v "*" /etc/motd**
grep: /etc/motd: No such file or directory

```

I did what you asked me (but put an additional slash in the third line so we're actually writing to the b43.conf file)

The first boot resulted in wifi, the one after that didn't, the one after that did.
Then I think there were 3 boots without wifi. And then one with wifi again.

The verification command gives the following:
```

**$ cat /etc/modprobe.d/b43.conf**
options b43 nohwcrypt=1

```

May I ask what nohwcrypt does?
And do you have additional steps I can try?

---

### Post by Hadaka on 2014-05-14
hi, sorry about the "/"...
try this motd command...maybe its not used in 14.04
```
cat /etc/motd
```.

the nohowcrypt you can view with..
```
modinfo b43
```

the parameters are for turning on/off features.
no hardware encryption =1  turns off the N speed
for the card. which has a history of causing dropouts
and no connects...
we can try a few more things if you are in the mood to experiment.

---

### Post by Ertyui on 2014-05-14
Hi,

The "cat /etc/motd" also gives "No such file or directory" I checked, the file is definitly not there ;)

Ah ok thanks for the information, very helpful!
I am very in the mood for experimenting, as I would like a stable setup, as it used to be.
Although I will probably reply tomorrow again, it's 23:50 here.

Thanks for the help so far!

Gr. Emile

---

### Post by Ertyui on 2014-05-15
Okay, so what experiments do you have in mind?

---

### Post by Hadaka on 2014-05-15
ok, first please COPY and paste this command.
```
cat /etc/motd
```Then , and i doubt
it will work, try special case # 1 on the sticky
at the top of the wireless posting page.
thanks.

---

### Post by Ertyui on 2014-05-15
This is what I get, like I said:
```

emile@Emile-Ubuntu:~$ cat /etc/motd
cat: /etc/motd: No such file or directory

```

I copied it in.

I will now try special case #1

---

### Post by Ertyui on 2014-05-15
Special case #1 didn't work. I removed the blacklists again.
Something else I could try? Or some more diagnostics? Perhaps we can try toggling some more module options like nohwcrypt?
Or wouldn't that affect it?

---

### Post by Hadaka on 2014-05-15
I think the real problem or atleast one of a possible couple
is the still somewhat buggy 14.04 in combination with a broadcom
dirver that is not all that common. messing with the other options
would probably cause more issues than are current. Untill 14.04
is a little more setteled..this is my opinion only..I would load the
stable 12.04 or you could try the 32bit 14.04.

---

### Post by Ertyui on 2014-05-15
Alright, I will try that. Thank you very much for your help!
Should I mark this thread as something?

---

### Post by Hadaka on 2014-05-15
Hi, sorry i wasnt able to find a magic answer, leave the thread
open for now, perhaps someone else has some great ideas. Having
an aapl machine also puts a bit of a twist in this. I have had great luck
with aapl boxes in the past..so it is possible. Hang tight for now and
see what happens.

---

### Post by keithspg on 2014-05-25
> **harobed said:**
> Personnaly I did :

```


$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
$ sudo apt-get install linux-firmware-nonfree
$ sudo reboot

```

I reported this bug here : [https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/1316816](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/1316816)

Worked for me, too. Pretty frustrating. Could see the networks, just not connect. This driver should be disabled until it can be fixed. If it does not work, and a (gasp) non-free driver must be loaded, don't tease me with something that almost works.

---

