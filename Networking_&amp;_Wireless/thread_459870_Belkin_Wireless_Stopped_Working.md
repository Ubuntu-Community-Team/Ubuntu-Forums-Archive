---
title: "Belkin Wireless Stopped Working"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by IanE on 2007-05-31
Hi,

I've been using Ubuntu 7.04 for a couple of months with no real
problems until yesterday when my wireless connection suddenly stopped
working.  It's a desktop with a wireless card in it that was working
fine in the morning, when I came home in the evening it just wouldn't
see the network anymore and I'm tearing my hair out trying to figure
out why, I swear I haven't changed anything on it or even upgraded/
updated any software on it or settings or anything.  I've got a
(windows) laptop as well which continues to see the network router and
connect the internet without any problem, so I don't think there's a
problem with the router or the network side of things.  I've run a
virus scan on Ubuntu which found nothing.  Originally I had to
download the bcm43xx firmware to get the wireless card running
properly in the first place, which was a bit of hassle but once it was
done I've not had any problems with it since.  It seems that it can
see available wireless networks but isn't connecting for some reason,
I think?

I've attached the output from ifconfig, lshw and lsmod (sorry for making it such a long post!):

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:10:DC:C1:BA:FA
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20

eth1      Link encap:Ethernet  HWaddr 00:11:50:F6:3E:3B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Memory:dfffa000-dfffc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

lshw:

jones
    description: Desktop Computer
    product: MS-6585
    vendor: MSI
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: MS-6585
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: Version 07.00T (07/03/02)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot
bootselect socketedrom edd int13floppy360 int13floppy1200
int13floppy720 int13floppy2880 int5printscreen int9keyboard
int17printer int10video acpi usb agp ls120boot zipboot
biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: Socket-478
          size: 2400MHz
          capacity: 3GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae
mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr
sse sse2 ss ht tm pbe up cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 8KB
             capacity: 1MB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-
back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 512KB
             capacity: 1MB
             clock: 25MHz (40.0ns)
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 1519MB
     *-pci
          description: Host bridge
          product: 645xx
          vendor: Silicon Integrated Systems [SiS]
          physical id: e0000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
          resources: iomemory:e0000000-e7ffffff
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1
mingnt=5
                resources: iomemory:de000000-deffffff
iomemory:d0000000-d7ffffff irq:21
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: ioport:c00-c1f
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=SIS_IDE latency=128
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:
170-177 iomemory:370-36f ioport:ff00-ff0f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: IC35L120AVV207-0
                   vendor: Hitachi
                   physical id: 0
                   bus info: i...@0.0
                   logical name: /dev/hda
                   version: V24OA66A
                   serial: VNVD06G4GP2NYL
                   size: 115GB
                   capacity: 115GB
                   capabilities: ata dma lba iordy smart security pm
apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: i...@0.0,1
                      logical name: /dev/hda1
                      capacity: 110GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: i...@0.0,2
                      logical name: /dev/hda2
                      size: 4447MB
                      capacity: 4447MB
                      capabilities: primary extended partitioned
partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 4447MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: CD-R/CD-RW writer
                   product: ATAPI CD-RW 52XMax
                   physical id: 0
                   bus info: i...@1.0
                   logical name: /dev/hdc
                   version: 150D
                   capabilities: packet atapi cdrom removable
nonmagnetic dma lba iordy audio cd-r cd-rw
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
              *-cdrom:1
                   description: DVD reader
                   product: ATAPI DVD-ROM 16XMax
                   physical id: 1
                   bus info: i...@1.1
                   logical name: /dev/hdd
                   version: VER 1.00
                   capabilities: packet atapi cdrom removable
nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11
mingnt=52
             resources: ioport:dc00-dcff ioport:d800-d87f irq:20
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:dfffe000-dfffefff irq:18
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2
speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:dfffd000-dfffdfff irq:17
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2
speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:dfffc000-dfffcfff irq:16
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2
speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: iomemory:dffff000-dfffffff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6
speed=480.0MB/s
              *-usb
                   description: USB hub
                   physical id: 6
                   bus info: usb@4:6
                   version: 0.07
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4
speed=480.0MB/s
                 *-usb
                      description: USB hub
                      physical id: 1
                      bus info: usb@4:6.1
                      version: 0.07
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=100mA slots=4
speed=480.0MB/s
                    *-usb:0
                         description: Generic USB device
                         product: eUSB ATA / ATAPI Adapter
                         vendor: SCM Microsystems Inc.
                         physical id: 1
                         bus info: usb@4:6.1.1
                         logical name: scsi0
                         version: 2.00
                         capabilities: usb-1.00 emulated scsi-host
                         configuration: driver=usb-storage
maxpower=0mA speed=12.0MB/s
                       *-disk
                            description: SCSI Disk
                            product: A
                            vendor: ST310232
                            physical id: 0.0.0
                            bus info: scsi@0:0.0.0
                            logical name: /dev/sda
                            serial: B70Q354N
                            size: 9768MB
                            capabilities: partitioned partitioned:dos
                            configuration: ansiversion=2
                          *-volume
                               description: Extended partition
                               physical id: 1
                               bus info: scsi@0:0.0.0,1
                               logical name: /dev/sda1
                               size: 2047MB
                               capacity: 2047MB
                               capabilities: primary extended
partitioned partitioned:extended
                             *-logicalvolume
                                  description: FAT16 partition
                                  physical id: 5
                                  logical name: /dev/sda5
                                  capacity: 2047MB
                    *-usb:1
                         description: Keyboard
                         product: Wireless Keyboard & Mouse
                         vendor: Darfon
                         physical id: 2
                         bus info: usb@4:6.1.2
                         version: 1.00
                         capabilities: usb-1.10
                         configuration: driver=usbhid maxpower=100mA
speed=1.5MB/s
        *-network:0
             description: Wireless interface
             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN
Controller
             vendor: Broadcom Corporation
             physical id: 7
             bus info: pci@00:07.0
             logical name: eth1
             version: 02
             serial: 00:11:50:f6:3e:3b
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper
driverversion=1.38 firmware=Broadcom,02/11/2005, 3.100.64.0 latency=64
link=no multicast=yes wireless=IEEE 802.11g
             resources: iomemory:dfffa000-dfffbfff irq:20
        *-communication UNCLAIMED
             description: Communication controller
             product: 536EP Data Fax Modem
             vendor: Intel Corporation
             physical id: b
             bus info: pci@00:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=64
             resources: iomemory:df800000-dfbfffff irq:10
        *-network:1
             description: Ethernet interface
             product: BCM4401 100Base-T
             vendor: Broadcom Corporation
             physical id: f
             bus info: pci@00:0f.0
             logical name: eth0
             version: 01
             serial: 00:10:dc:c1:ba:fa
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical mii
10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes
driver=b44 driverversion=1.01 duplex=half latency=64 link=no
multicast=yes port=twisted pair speed=10MB/s
             resources: iomemory:dfff8000-dfff9fff irq:20

lsmod:

Module                  Size  Used by
nls_iso8859_1           5120  1
nls_cp437               6784  1
vfat                   14208  1
fat                    53916  1 vfat
sg                     36252  0
sd_mod                 23428  2
joydev                 10816  0
usbhid                 26592  0
hid                    27392  1 usbhid
usb_storage            72256  1
libusual               17936  1 usb_storage
binfmt_misc            12680  1
ipv6                  268704  12
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_stats           7360  0
cpufreq_conservative     8200  0
cpufreq_powersave       2688  0
cpufreq_userspace       5408  0
cpufreq_ondemand        9228  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0
dev_acpi               12292  0
tc1100_wmi              8068  0
sony_acpi               6284  0
container               5248  0
sbs                    15652  0
dock                   10268  0
battery                10756  0
ac                      6020  0
asus_acpi              17308  0
button                  8720  0
video                  16388  0
i2c_ec                  5888  1 sbs
backlight               7040  1 asus_acpi
af_packet              23816  0
ndiswrapper           194608  0
lp                     12452  0
fuse                   46612  1
snd_intel8x0           34204  0
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3
snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
nvidia               4713780  22
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0
sis_agp                 9604  1
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
i2c_sis96x              6532  0
snd                    54020  10
snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
agpgart                35400  2 nvidia,sis_agp
pcspkr                  4224  0
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
psmouse                38920  0
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
i2c_core               22784  3 i2c_ec,nvidia,i2c_sis96x
evdev                  11008  5
tsdev                   8768  0
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0
cdrom                  37664  1 ide_cd
ide_disk               17024  3
ata_generic             9092  0
pata_sis               14220  0
libata                125720  2 ata_generic,pata_sis
scsi_mod              142348  4 sg,sd_mod,usb_storage,libata
generic                 5124  0 [permanent]
floppy                 59524  0
b44                    28044  0
mii                     6528  1 b44
ehci_hcd               34188  0
ohci_hcd               22532  0
usbcore               134280  7
usbhid,usb_storage,libusual,ndiswrapper,ehci_hcd,ohci_hcd
sis5513                14856  0 [permanent]
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

---

