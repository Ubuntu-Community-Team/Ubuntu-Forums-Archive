---
title: "Atheros AR5212/AR5213 not working on Ubuntu 7.10"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by sorin7486 on 2008-02-08
Hello everybody,

      I've just installed Ubuntu 7.10 on a friends Packard Bell EasyNote laptop ... the machine is about 2 years old and it has an Atheros wifi card. Now for some reason the madwifi driver seems to be loaded but the card shows as "UNCLAIMED" in lshw... The restricted modules where installed out of the box ... any ideas ??

here is the output of lspci, lshw and lsmod:


```
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
```

```
softylaptop
    description: Pizza Box Computer
    product: Packard Bell EasyNote
    vendor: NEC Computers International
    version: PB42D00606
    serial: 660000100232
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=pizzabox power-on_password=disabled uuid=2070E83B-8AD0-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: NEC Versa Premium
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 5a
       serial: 12345678
     *-firmware
          description: BIOS
          vendor: Insyde Software Corporation
          physical id: 0
          version: R1.01 (/08/0520)
          size: 84KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int17printer int10video acpi usb agp zipboot smartbattery netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: mPGA478
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KB
             capacity: 64KB
             capabilities: burst pipeline-burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: burst pipeline-burst external write-back
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 512MB
          capacity: 512MB
        *-bank:0
             description: DIMM DRAM EDO 166 MHz (6.0 ns)
             physical id: 0
             slot: DRAM Slot 0
             size: 256MB
             width: 64 bits
             clock: 166MHz (6.0ns)
        *-bank:1
             description: DIMM DRAM EDO 166 MHz (6.0 ns)
             physical id: 1
             slot: DRAM Slot 1
             size: 256MB
             width: 64 bits
             clock: 166MHz (6.0ns)
        *-bank:2
             description: DIMM DRAM EDO [empty]
             physical id: 2
             slot: DRAM Slot 2
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: CN400/PM880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: S3 Unichrome Pro VGA Adapter
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga bus_master cap_list
                configuration: latency=64 mingnt=2
        *-network:0 UNCLAIMED
             description: Ethernet controller
             product: AR5212/AR5213 Multiprotocol MAC/baseband processor
             vendor: Atheros Communications, Inc.
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=168 maxlatency=28 mingnt=10
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=22 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=22 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=22 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=22 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=VIA_IDE latency=64 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD600UE-22HCT0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 09.07D09
                   serial: WD-WXE306623620
                   size: 55GB
                   capacity: 55GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 7200MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 48GB
                      capacity: 48GB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: HPFS/NTFS partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 41GB
                    *-logicalvolume:1
                         description: Linux swap / Solaris partition
                         physical id: 6
                         logical name: /dev/hda6
                         capacity: 517MB
                         capabilities: nofs
                    *-logicalvolume:2
                         description: Linux filesystem partition
                         physical id: 7
                         logical name: /dev/hda7
                         capacity: 7146MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD writer
                   product: _NEC DVD_RW ND-6750A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 2.61
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0 module=snd_via82xx_modem
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:40:d0:8e:23:f9
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=10.0.0.3 latency=128 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: Host bridge
          product: CN400/PM880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN400/PM880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN400/PM880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN400/PM880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN400/PM880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
  *-battery
       product: DR36
       vendor: Duracell
       physical id: 1
       version: 01/06/05
       serial: 0042
       slot: Smart Battery Conn J37
       configuration: voltage=0.0V
```
```
Module                  Size  Used by
sg                     36764  0 
ath_pci                98336  0 
isofs                  36412  0 
udf                    87204  0 
ipv6                  273892  8 
af_packet              24840  2 
via                    43904  2 
drm                    83348  3 via
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_ondemand        9612  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
loop                   19076  0 
joydev                 11328  0 
snd_via82xx_modem      16264  0 
snd_via82xx            29336  1 
gameport               16776  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_ac97_codec        100644  2 snd_via82xx_modem,snd_via82xx
snd_seq_oss            33152  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
via_ircc               27668  0 
irda                  202300  1 via_ircc
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
crc_ccitt               3072  1 irda
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
shpchp                 34580  0 
i2c_viapro             10004  0 
serio_raw               8068  0 
psmouse                39952  0 
snd                    54660  14 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_via82xx_modem,snd_via82xx,snd_pcm
pci_hotplug            32704  1 shpchp
i2c_core               26112  1 i2c_viapro
via_agp                11264  1 
agpgart                35016  2 drm,via_agp
wlan                  206660  1 ath_pci
ath_hal               192720  1 ath_pci
evdev                  11136  1 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  5 
usbhid                 29536  0 
hid                    28928  1 usbhid
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  2 sg,libata
via_rhine              25992  0 
mii                     6528  1 via_rhine
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

---

### Post by Sticky on 2008-02-20
I have exactly the same problem on a Packard Bell Easynote I picked up second hand recently.  Any helpful comments would be greatly appreciated.  I've tried using ndiswrapper following a guide I found [here]("http://johnbokma.com/mexit/2007/12/29/") but sadly to no avail.  It all seems to work up until I get to the very end of the guide where it doesn't.

Help please - anyone??

---

### Post by chiacchio on 2008-02-24
Same problem for me... Can anyone help us? Just as information. I also followed this guide ([http://madwifi.org/wiki/UserDocs/MiniPCI]("http://madwifi.org/wiki/UserDocs/MiniPCI")), even masking pin 13, But I didn't succeed..

---

### Post by Luke.Hoersten on 2008-03-01
I convinced my roommate to get Ubuntu and sure enough, he has this wireless card that does not work. Anyone find any answers yet?

---

### Post by tad1073 on 2008-03-01
I have the same chipset and it worked out of the box.

---

### Post by NoWhereMan on 2008-03-04
try booting with acpi=force and enjoy your lost USBs :( (but working wireless... yeah great bios)

---

### Post by BDNiner on 2008-03-06
I am having a similar problem with this chipset. I have a DLink PCI card that works fine under 7.10 on my Pentium 4 computer. but when i put the same card in my AMD X2 computer also running 7.10 it doesn't work. When i run **lshw -C network** it lists the card as unclaimed. What does that mean? I can't find much when i google it.

---

### Post by chaime on 2008-03-31
I am having the same problem. It is listed as unclaimed. I've tried uninstalling and reinstalling madwifi but I don't seem to get anywhere...

ASUS P4C800 with Intel 2.4HT
512MB DDR-400 (PC3200)
ATI Radeon 9200
Trendnet TEW443PI aka Atheros AR5212/5213...etc...

Chaim

---

### Post by Snappo on 2008-05-24
I've also boarded this boat :(

---

