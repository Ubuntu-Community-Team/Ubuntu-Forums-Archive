---
title: "Belkin N150 F7D1101 v1 Basic Wireless Adapter not seen"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by paulwillliamkoehn on 2013-09-10
after a fresh install a wrong driver(from this post ([http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815))) was installed (Realtek RTL8188SU) but not working with Belkin F7D1101 USB Adapter - External - USB 2.0
the device is listed on the ndsiwrapper driver list, but the card is no longer"seen" by the system in adition wrapper itself does not accept the .inf files i found that were documented to work
i am running Ubuntu 12.04 with no major changes beyond compiling reaver and ndis wrapper (but not sure if i got it working as it freezes when i install net8192su.inf)

```
paul@computer:~$ sudo lshw
computer  description: Notebook
    product: Aspire 5251 (123456789)
    vendor: Acer
    version: V2.14
    serial: LXPWJ02001016117761601
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook family=Type1Family sku=123456789 uuid=ED95151D-1B23-2C07-94E9-705AB6DDC44A
  *-core
       description: Motherboard
       product: JE50_DN
       vendor: Acer
       physical id: 0
       version: Base Board Version
       serial: LXPWJ02001016117761601
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V2.14
          date: 07/27/2011
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: AMD V120 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 20
          bus info: cpu@0
          version: 15.6.3
          serial: NotSupport
          slot: Socket S1G4
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc up nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=1 enabledcores=1 threads=1
        *-cache:0 DISABLED
             description: L1 cache
             physical id: 21
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-through unified
        *-cache:1 DISABLED
             description: L1 cache
             physical id: 22
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-through unified
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: EBJ10UE8BDS0-AE-F
             vendor: Elpida
             physical id: 0
             serial: 0B110A68
             slot: DIMM0
             size: 1GiB
             width: 8 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: EBJ10UE8BDS0-AE-F
             vendor: Elpida
             physical id: 1
             serial: 1F110A68
             slot: DIMM1
             size: 1GiB
             width: 8 bits
             clock: 1066MHz (0.9ns)
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (int gfx)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:6000(size=4096) memory:92100000-922fffff ioport:80000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS880M [Mobility Radeon HD 4225/4250]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:80000000-8fffffff ioport:6000(size=256) memory:92200000-9220ffff memory:92100000-921fffff
           *-multimedia
                description: Audio device
                product: RS880 HDMI Audio [Radeon HD 4200 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:19 memory:92210000-92213fff
        *-pci:1
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=16384) memory:91100000-920fffff ioport:90000000(size=16777216)
           *-network
                description: Ethernet interface
                product: NetLink BCM57780 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 70:5a:b6:dd:c4:4a
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 memory:91100000-9110ffff
        *-pci:2
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:91000000-910fffff
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: 01
                serial: 00:17:c4:f5:30:5a
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.5.0-40-generic firmware=N/A ip=192.168.0.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:91000000-9100ffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:42 ioport:7038(size=8) ioport:704c(size=4) ioport:7030(size=8) ioport:7048(size=4) ioport:7010(size=16) memory:92307000-923073ff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:92306000-92306fff
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:92307500-923075ff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:92305000-92305fff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:92307400-923074ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 41
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:92300000-92303fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:92304000-92304fff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54502
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: PB2O
             serial: 100313PBG2063SGUL3JV
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0007bad7
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 6905ab65-b55a-43cf-bd30-a8e3ddfc144d
                size: 231GiB
                capacity: 231GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-09-01 08:47:09 filesystem=ext4 lastmountpoint=/ modified=2013-09-01 09:25:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-09-10 14:18:14 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1785MiB
                capacity: 1785MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1785MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7585H
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: KX04
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
while 

paul@computer:~$ sudo lshw -C network
[sudo] password for paul: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 70:5a:b6:dd:c4:4a
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 memory:91100000-9110ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:c4:f5:30:5a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-40-generic firmware=N/A ip=192.168.0.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:91000000-9100ffff



then

paul@computer:~$ sudo lsmod
Module                  Size  Used by
snd_hrtimer            12649  1 
rfcomm                 38104  0 
bnep                   17791  2 
bluetooth             189625  10 rfcomm,bnep
parport_pc             32115  0 
ppdev                  12850  0 
binfmt_misc            17293  1 
wl                   2906598  0 
snd_hda_codec_hdmi     31778  1 
snd_hda_codec_realtek    64959  1 
lib80211               14041  1 wl
arc4                   12474  2 
snd_hda_intel          32983  4 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ath9k                 117932  0 
mac80211              475546  1 ath9k
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
ath9k_common           13782  1 ath9k
snd_rawmidi            25426  1 snd_seq_midi
radeon                837142  3 
ath9k_hw              384090  2 ath9k,ath9k_common
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  3 snd_seq_midi,snd_seq_midi_event
ath                    19436  3 ath9k,ath9k_common,ath9k_hw
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
ttm                    76326  1 radeon
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
kvm_amd                50661  0 
drm_kms_helper         47459  1 radeon
kvm                   365588  1 kvm_amd
drm                   240443  5 radeon,ttm,drm_kms_helper
uvcvideo               72249  0 
snd                    62675  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf2_core         32212  1 uvcvideo
videodev              100265  2 uvcvideo,videobuf2_core
soundcore              14636  1 snd
videobuf2_vmalloc      12757  1 uvcvideo
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
videobuf2_memops       13213  1 videobuf2_vmalloc
cfg80211              181041  4 wl,ath9k,mac80211,ath
i2c_algo_bit           13317  1 radeon
psmouse                91408  0 
microcode              18396  0 
joydev                 17394  0 
shpchp                 32326  0 
serio_raw              13032  0 
sp5100_tco             13496  0 
acer_wmi               27975  0 
sparse_keymap          13659  1 acer_wmi
i2c_piix4              13094  0 
k10temp                12998  0 
wmi                    18745  1 acer_wmi
video                  19117  1 acer_wmi
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
tg3                   141848  0 
ahci                   25621  2 
libahci                26166  1 ahci

and

paul@computer:~$ rfkill list 
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

i do have the onboard wifi (ath9) working but i need the second to share music/video with other devices...
qny help would be appreciated, thanks

---

