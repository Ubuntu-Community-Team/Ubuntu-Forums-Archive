---
title: "My computer boots fine in safemode"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by Darris on 2011-07-04
so my computer kept stopping during booting, so I started in failsafe mode and it works perfectly... but only in safemode
I don't really know where to start because I don't know what's causing the problem. So how do I get more information/fix it?

---

### Post by Autodave on 2011-07-04
> **Darris said:**
> so my computer kept stopping during booting, so I started in failsafe mode and it works perfectly... but only in safemode
I don't really know where to start because I don't know what's causing the problem. So how do I get more information/fix it?

What version are you trying to install?  And what are the specs of you machine?  If your are installing 11.04, you may noy have enough power to run UNITY and you need to boot into CLASSICAL instead.

Please give us some info first.....

---

### Post by wildmanne39 on 2011-07-04
> **Darris said:**
> so my computer kept stopping during booting, so I started in failsafe mode and it works perfectly... but only in safemode
I don't really know where to start because I don't know what's causing the problem. So how do I get more information/fix it?Hi, run these command in a terminal
```
sudo lshw
```
```
lspci | grep VGA
```
```
/usr/lib/nux/unity_support_test -p
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Darris on 2011-07-04
I'm not even attempting to install natty, I'm running 10.10, it just stopped working today when I turned my laptop back on.
It begins to boot but then it just sits there forever. I left it for over an hour in case I was just being impatient.
I did manage to get it to allow me to log in textually, but then it brought me to the command line and when I pressed ctrl+F7 it just went back to that booting text screen and sat there forever again xD.

---

### Post by Darris on 2011-07-04
```
version: AMD Athlon(tm) X2 Dual-Core QL-62
          serial: NotSupport
          slot: Socket M2/S1G1
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 1800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit arat lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 1c
             slot: L1 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 1d
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 3GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: 0x48594D503131325336344350362D53362020
             vendor: 0x48594D503131325336344350362D53362020
             physical id: 0
             serial: 0x48594D503131325336344350362D53362020
             slot: 0x48594D503131325336344350362D53362020
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: 0x48594D503132355336344350382D53362020
             vendor: 0x48594D503132355336344350382D53362020
             physical id: 1
             serial: 0x48594D503132355336344350382D53362020
             slot: SODIMM 1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (int gfx)
             vendor: Advanced Micro Devices [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:6000(size=4096) memory:d6200000-d63fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780MC [Radeon HD 3100 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:18 memory:c0000000-cfffffff ioport:6000(size=256) memory:d6300000-d630ffff memory:d6200000-d62fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:d5200000-d61fffff ioport:d0000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=8192) memory:d4200000-d51fffff ioport:d1000000(size=17825792)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 02
                serial: 00:1e:33:b6:88:1e
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:44 ioport:3000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d103ffff
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:d3100000-d41fffff ioport:d2100000(size=16777216)
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 00:24:d2:67:b3:d9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=2.6.35-30-generic firmware=N/A ip=192.168.31.197 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:18 memory:d3100000-d310ffff
        *-pci:4
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:7038(size=8) ioport:704c(size=4) ioport:7030(size=8) ioport:7048(size=4) ioport:7010(size=16) memory:d6408000-d64083ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54323
                vendor: Hitachi
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: FB4O
                serial: 090321FB2406LEDXZUAC
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ef799
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: 2e43eb02-4b4a-4dad-a1b2-eff1a4f9d951
                   size: 235MiB
                   capacity: 235MiB
                   capabilities: primary bootable journaled extended_attributes huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-06-30 17:49:15 filesystem=ext4 lastmountpoint=/boot&#65533;\&#15048;&#65533;&#65533;"C;&#65533;&#65533;&#31304;&#65533;&#65533;&#65533;&#43528;&#65533;&#65533;@«&#65533;&#65533;&#65533;&#1060;&#65533;&#65533;&#65533;&#65533;&#65533;]&#15048;&#65533;&#65533;&#65533;. modified=2011-07-04 21:13:26 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-07-04 21:13:26 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 297GiB
                   capacity: 297GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 18GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /tmp
                      capacity: 1906MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /var
                      capacity: 1906MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 2863MiB
                      capabilities: nofs
                 *-logicalvolume:4
                      description: Linux filesystem partition
                      physical id: 9
                      logical name: /dev/sda9
                      logical name: /home
                      capacity: 272GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ880AS
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.50
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:d6407000-d6407fff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:d6406000-d6406fff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:d6408500-d64085ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d6405000-d6405fff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d6404000-d6404fff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:d6408400-d64084ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:7000(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:d6400000-d6403fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:5
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:1000(size=4096)
     *-pci:1
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 11h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          bus info: usb@2:4
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
     *-scsi:1
          physical id: 2
          bus info: usb@1:3
          logical name: scsi9
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: U3 Cruzer Micro
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/sdc
             version: 8.02
             serial: u
             size: 1927MiB (2021MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
                size: 1927MiB (2021MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=000e4307
              *-volume
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 1
                   logical name: /dev/sdc1
                   logical name: /media/New Volume
                   version: FAT32
                   serial: 8511-31a7
                   size: 1925MiB
                   capacity: 1926MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=New Volume mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=winnt,errors=remount-ro state=mounted

```
That's as much of the output as I can get, I don't know how to make my terminal remember more lines
```
lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]

```

---

### Post by wildmanne39 on 2011-07-04
> **Darris said:**
> I'm not even attempting to install natty, I'm running 10.10, it just stopped working today when I turned my laptop back on.
It begins to boot but then it just sits there forever. I left it for over an hour in case I was just being impatient.
I did manage to get it to allow me to log in textually, but then it brought me to the command line and when I pressed ctrl+F7 it just went back to that booting text screen and sat there forever again xD.Hi, I imagine that your video card driver was updated or got corrupted. Here is a link see if you can boot with one of these options then you can check your driver, let us know, so we will know how to proceed.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Darris on 2011-07-11
I have tried the things in that post and nothing has changed.
I can boot normally but there is no gui. It can drop to a shell and if I log in it's just my terminal. If I press ctrl+alt+F7, it just brings me back to the gibberish text it says during boot.
Before it was stopping on "saned disabled; edit /etc/default/saned", but now it has gone on to "enabling additional executable binary formats binfmt-support".
It stops there, but I can still ctrl+alt+F1 like I said.

Just as an experiment, I ran the command "firefox" and the response from the terminal is "Error: no display specified".

---

### Post by Darris on 2011-07-11
Sorry it's been so long, I was away from the internet. I hope this thread isn't too far dead to bring back to the forums eyes :(

---

### Post by Darris on 2011-07-11
I don't know what startx does specifically, but it does start if I use the command in the ctrl+alt+f1
however, certain programs still don't run, so I guess it must be still a form of failsafex

---

### Post by Darris on 2011-07-12
bump

---

### Post by Darris on 2011-07-14
bump
if i don't get a reply soon I think i'll make a separate more detailed thread.

---

### Post by wildmanne39 on 2011-07-14
> **Darris said:**
> bump
if i don't get a reply soon I think i'll make a separate more detailed thread.Hi, run this command
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Darris on 2011-07-15
```
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  194 
aes_generic            27631  1 aes_x86_64
radeon                910771  0 
ttm                    68212  1 radeon
drm_kms_helper         32836  1 radeon
drm                   206198  3 radeon,ttm,drm_kms_helper
i2c_algo_bit            6208  1 radeon
dm_crypt               13381  0 
snd_hda_codec_realtek   300109  1 
joydev                 11395  0 
snd_hda_intel          26147  2 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
arc4                    1497  2 
fglrx                2525261  0 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
ath5k                 143332  0 
uvcvideo               62411  0 
mac80211              267099  1 ath5k
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
lp                     10201  0 
ath                    10413  1 ath5k
cfg80211              170581  3 ath5k,mac80211,ath
v4l2_compat_ioctl32    12614  1 videodev
edac_core              46822  0 
edac_mce_amd            9387  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                62080  0 
serio_raw               4910  0 
i2c_piix4              10047  0 
k10temp                 3535  0 
led_class               3393  1 ath5k
snd                    64277  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
parport                37032  1 lp
usb_storage            50788  0 
ahci                   22370  6 
video                  22176  0 
output                  2527  1 video
libahci                26148  1 ahci
pata_atiixp             4405  0 
r8169                  42286  0 
mii                     5261  1 r8169
```

thank you for replying I was beginning to get worried lol

---

### Post by wildmanne39 on 2011-07-15
Hi, I think this is your problem Fglrx Inteferes With Radeon Driver have a look at this link.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
You both of these drivers installed.

---

### Post by Darris on 2011-07-15
It did not work :(.
Here, have some screenshots lol

---

### Post by Darris on 2011-07-15
That's where it stops.

---

### Post by wildmanne39 on 2011-07-15
> **Darris said:**
> That's where it stops.Hi, what did you try from that link I gave you? Did you remove fglrx driver? Upgrade your radeon?

---

### Post by Darris on 2011-07-15
> **wildmanne39 said:**
> Hi, what did you try from that link I gave you? Did you remove fglrx driver? Upgrade your radeon?
I did the commands listed under 
**Problem:  Need to fully remove -fglrx and reinstall -ati from scratch**

---

### Post by wildmanne39 on 2011-07-15
> **Darris said:**
> I did the commands listed under 
**Problem:  Need to fully remove -fglrx and reinstall -ati from scratch**

That should have worked, try the method on this page to get you into ubuntu so we can fix it.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
once in run this command again so I can see what driver it is using.
```
lsmod
```

---

### Post by Darris on 2011-07-16
> **wildmanne39 said:**
> That should have worked, try the method on this page to get you into ubuntu so we can fix it.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
once in run this command again so I can see what driver it is using.
```
lsmod
```
I've done all of those. It doesn't change anything. 
I'll try again tomorrow though. This day has been way to long to troubleshoot lol
I'm going to bed

---

### Post by Psyco430404 on 2011-07-16
startx begins the xserver, what you may want to do once your in there is reinstall your video drivers, or update them.

---

### Post by Darris on 2011-07-17
Is it important to mention I use openbox and tint2?
I was trying to make this ubuntu into an ubuntu-lite
kind of like #!

---

### Post by Darris on 2011-07-18
So I tried to start gdm for a completely unrelated task and it gave me an error 
```
**  (gdm-binary:2883): WARNING **: Failed to acquire  org.gnome.DisplayManager: Connection ":1.34" is not allowed to own the  service "org.gnome.DisplayManager" due to security policies in the  configuration file

** (gdm-binary:2883): WARNING **: Could not acquire name; bailing out
```

so I googled it and it led me to a thread which implied that my tmp file wasn't clearing itself out.
So I ran bleachbit and rebooted my computer.
When it started back up I let it go to the screen where it stops and did ctrl+alt+f1 and logged in then i did 
```
sudo gdm
```

and it actually went in without going into the recovery console.
however,  my graphics are in failsafe mode, so that might be due to the fact that  my grub still says "acpi=off". What do you think?

I had it set  up to open up the themes box when I got to the log in screen and that  worked perfectly, except that when I went to add more backgrounds, I was  in the username "gdm" and couldn't access my actual home file  (permission denied). I think this might also have to do with why my  graphics are in failsafe mode. 

I don't really know how to interpret all of this, but i'm glad to not be in recovery console anymore lol

---

### Post by Darris on 2011-07-18
Okay, it was NOT the "acpi=off" thing that did it, because I have removed that and the resolution is still painful to the eyes.
Is there anyway to change the resolution from the command line?

---

### Post by Darris on 2011-07-18
Also, I don't believe the xserver is running, because if I use the command ```
grandr
```
In the gui, it says X Server at the top left, but when I change the resolution nothing happens.
I attempted to verify that by running 
```
sudo dpkg-reconfigure xserver-xorg
```
but it doesn't give any output, so maybe the command is working and maybe I'm on a complete tangent.

---

### Post by Darris on 2011-07-18
I'm sorry I can't tell you exactly how I fixed it :(
I accidentally had to reboot, because I was in the ctrl+alt+f1 screen to log in, so when I pressed ctrl+alt+f7, it brought me back to the screen it gets stuck on so I had to power down manually.
But I know that I reinstalled xserver and a number of other things
if I knew how to go to the terminal history, I would tell you what I did.

In any case, when I rebooted, I planned on going to an earlier kernel, but I forgot to hold shift, so it just booted ... and it went straight to my log in screen >_>
so problem solved, I guess? lol

---

### Post by wildmanne39 on 2011-07-18
Hi, I am glad you have it working, if it continues to work for the next few restarts would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

