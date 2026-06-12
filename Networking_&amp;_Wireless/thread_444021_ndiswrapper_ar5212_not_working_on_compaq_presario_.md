---
title: "ndiswrapper ar5212 not working on compaq presario 701"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by ozooha on 2007-05-15
Hi everyone,
I have installed 7.04 on my Presario 701 and it works fine with the native wireless driver for the
Netgear wpn511. However the connection is about 48%. I wanted this to increase this to around 100% or say somewhere close to it as i know 100% per se is not achievable.
I therefore decided to install the latest ndiswrapper-1.43 with the ar5212 driver - ar5211.sys  net5211.cat  net5211.inf
which were in my winxp systems folder.
I went through the whole process:
Here are the steps:
lsmod | grep 'ath' -> ath_hal; ath_pci; ath_rate_sample
which were all blacklisted in /etc/modprobe.d/blacklist
rebooted the laptop and there was no network signal on the card.
I then installed the latest ndiswrapper.(folllowed the instruction from the sourceforge website)
make distclean
make
make install
all went well.
then
installed the driver
ndiswrapper -i ~/Atheros_driver/net5211.inf
got the driver is installed with the command
ndiswrapper -l
  which said that the net5211 was installed and in brackets (alternate driver ath_pci)->Why should it say that when I blacklisted it?
anyways i went along and did the 
depmod -a (no output or errors)
ndiswrapper -m (made the alias)
To be on the safer side I went and put ndiswrapper in the /etc/modules as well
Now after this when I typed
modprobe ndiswrapper
the damn laptop freezes.????
I cannot understand this at all as I used the same card and the windows drivers
and install them on my other IBM laptop and it it worked..with 96% signal 
(These successful steps were replicated as mentioned above on the compaq laptop.)
I can't figure this out at all.
Any help or suggestion is welcomed.
Here is my outputs for the lspci and lsmod lshw
I could not print out the dmesg as with the card it would always freeze during bootup.
Thank you for spending your precious time on my post.
I appreciate your time and effort. 
I look forward to your pearls of wisdom.
OZooHA
ozooha@OKgroup-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 42)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

and after that
ozooha@OKgroup-laptop:~$ lsmod
Module                  Size  Used by
wlan_ccmp               9600  3 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
savage                 34048  2 
drm                    81044  3 savage
powernow_k7             8616  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 powernow_k7,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
asus_acpi              17308  0 
button                  8720  0 
ac                      6020  0 
container               5248  0 
backlight               7040  1 asus_acpi
video                  16388  0 
ipv6                  268704  8 
nls_utf8                3072  1 
ntfs                  107764  1 
lp                     12452  0 
fuse                   46612  0 
wlan_scan_sta          14976  1 
ath_rate_sample        14080  1 
ath_pci                97312  0 
wlan                  204484  5 wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
joydev                 10816  0 
pcmcia                 39212  0 
snd_via82xx            29208  1 
gameport               16520  1 snd_via82xx
snd_ac97_codec         98336  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
i2c_viapro             10132  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                38920  0 
via686a                17416  0 
pcspkr                  4224  0 
parport_pc             36388  1 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
via_agp                11264  1 
i2c_isa                 6272  1 via686a
snd                    54020  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                35400  2 drm,via_agp
soundcore               8672  1 snd
i2c_core               22784  4 i2c_ec,i2c_viapro,via686a,i2c_isa
parport                36936  3 ppdev,lp,parport_pc
af_packet              23816  8 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  4 
floppy                 59524  0 
via82cxxx              10372  0 [permanent]
generic                 5124  0 [permanent]
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
8139cp                 25088  0 
8139too                27648  0 
mii                     6528  2 8139cp,8139too
uhci_hcd               25360  0 
usbcore               134280  2 uhci_hcd
thermal                14856  0 
processor              31048  2 powernow_k7,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

ozooha@OKgroup-laptop:~$ sudo lshw 
okgroup-laptop            
    description: Computer
    product: Presario 705US 470023-551
    vendor: Compaq
    version: 0F0C
    serial: 1V1AKDKNV7JC
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: uuid=007AB982-D364-0010-9C5B-2C77106C8B7B
  *-core
       description: Motherboard
       product: 0760h
       vendor: Compaq
       physical id: 0
       version: Rev.A
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: 4.06CJ15 (06/28/2002)
          size: 104KB
          capacity: 192KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: mobile AMD Athlon(tm) 4 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.6.2
          slot: Socket A
          size: 996MHz
          capacity: 2GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts fid vid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KB
             capacity: 512KB
             capabilities: synchronous external write-through
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 384MB
          capacity: 1536MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 256MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: ec000000
          bus info: pci@00:00.0
          version: 80
          width: 32 bits
          clock: 33MHz
          configuration: latency=8
          resources: iomemory:ec000000-efffffff
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=4
                resources: iomemory:e8100000-e817ffff iomemory:f0000000-f7ffffff irq:5
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@00:07.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE latency=64
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:1840-184f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK8032GAX
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: AD001A
                   serial: 66171744T
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 52GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 21GB
                      capabilities: primary
                 *-volume:2
                      description: Extended partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      size: 996MB
                      capacity: 996MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 996MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: TOSHIBA DVD-ROM SD-R2002
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1Q35
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: ioport:1800-181f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge cap_list
             configuration: latency=0
             resources: irq:10
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: ioport:1000-10ff ioport:1854-1857 ioport:1850-1853 irq:5
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k HSFi Modem
             vendor: Conexant
             physical id: 9
             bus info: pci@00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=64
             resources: iomemory:e8000000-e800ffff ioport:1858-185f irq:4
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5
             resources: iomemory:ffbfe000-ffbfefff irq:11
           *-network
                description: AR5001-0000-0000
                product: Wireless LAN Reference Card
                vendor: Atheros Communications, Inc.
                physical id: 0
                version: 00
                slot: Socket 0
                resources: irq:11
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@00:0b.0
             logical name: eth0
             version: 10
             serial: 00:02:a5:a7:46:54
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
             resources: ioport:1400-14ff iomemory:e8010000-e80100ff irq:11
     *-network
          description: Wireless interface
          product: AR5212 802.11abg NIC
          vendor: Atheros Communications, Inc.
          physical id: 1
          bus info: pci@02:00.0
          logical name: wifi0
          version: 01
          serial: 00:0f:b5:a6:84:44
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3) ip=192.168.1.2 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
          resources: iomemory:24000000-2400ffff irq:11

---

### Post by chili555 on 2007-05-15
Evidently your blacklist did not go successfully, because your lsmod includes:```
ath_rate_sample 14080 1
ath_pci 97312 0 
```The blacklist entries should look like:```
blacklist   ath_pci
blacklist   ath_rate_sample
```Amend as needed, reboot and try again.

---

### Post by ozooha on 2007-05-16
> **chili555 said:**
> Evidently your blacklist did not go successfully, because your lsmod includes:```
ath_rate_sample 14080 1
ath_pci 97312 0 
```The blacklist entries should look like:```
blacklist   ath_pci
blacklist   ath_rate_sample
```Amend as needed, reboot and try again.

That wasn't the issue...I did include ath_pci,ath_rate_sample & ath_hal in the blacklist...a oversight on your part.
I fixed the issue wth the 1.44rc1 ndiswrapper..it did the job. I now have 89 to 95% signal strength.
Thanks for the response.
OZooHA

---

### Post by chili555 on 2007-05-16
I am wondering why the modules loaded:```
fuse 46612 0
wlan_scan_sta 14976 1
[B]ath_rate_sample 14080 1
ath_pci 97312 0
wlan 204484 5 wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal 192592 3 ath_rate_sample,ath_pci[/B]
joydev 10816 0
pcmcia 39212 0
snd_via82xx 29208 1 
```if they were blacklisted?

---

