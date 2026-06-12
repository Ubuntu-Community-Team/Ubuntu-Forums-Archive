---
title: "network not working without usb 'memory' stick!"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by selim76 on 2007-04-16
hi,
the title may make you feel like "what???" But  it's true. Let me explain:
i have an old desktop pc (you will see the configuration from lshw output) i installed ubuntu 6.10. everyhting seemed ok but network card. i am using static internal ip:

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:60:97:B8:46:58  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1213 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:738152 (720.8 KiB)  TX bytes:174857 (170.7 KiB)
          Interrupt:3 Base address:0xb000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1756 (1.7 KiB)  TX bytes:1756 (1.7 KiB)

------------and------/etc/network/interfaces----------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.38
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.0
#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

------------------and--------lshw------------
description: Tower Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: P3V133
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS P3V133 ACPI BIOS Revision 1001a (12/23/1999)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: SLOT 1
          size: 600MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KB
             capacity: 512KB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 128MB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DIMM 3
     *-pci:0
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: e4000000
          bus info: pci@00:00.0
          version: 44
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e4000000-e7ffffff
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d8000000-dfffffff ioport:d800-d8ff iomemory:c7000000-c700ffff irq:9
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                resources: iomemory:c8000000-cfffffff iomemory:c6800000-c680ffff
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT82C596 ISA [Mobile South]
             vendor: VIA Technologies, Inc.
             physical id: 4
             bus info: pci@00:04.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 4.1
             bus info: pci@00:04.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=VIA_IDE
             resources: ioport:b800-b80f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: Maxtor 6E040L0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: NAR61EA0
                   serial: E1T5XKBE
                   size: 38GB
                   capacity: 38GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 37GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 729MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: RICOH CD-R/RW MP7083A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.10
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: **[COLOR="Red"]USB Controller[/COLOR]**
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 4.2
             bus info: pci@00:04.2
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:b400-b41f **[COLOR="Red"]irq:3[/COLOR]**
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   physical id: 1
                   bus info: usb@1:1
                   logical name: scsi1
                   version: 1.00
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: Flash Disk
                      vendor: USB2.0
                      physical id: 0.0.0
                      bus info: scsi@1:0.0.0
                      logical name: /dev/sda
                      version: 2.00
                      size: 499MB
                      capabilities: removable
                      configuration: ansiversion=2
                    *-disc
                         physical id: 0
                         logical name: /dev/sda
                         size: 499MB
                         capabilities: partitioned partitioned:dos
                       *-volume
                            description: FAT16 partition
                            physical id: 1
                            logical name: /dev/sda1
                            capacity: 498MB
                            capabilities: primary bootable
        *-network
             description: **[COLOR="Red"]Ethernet interface[/COLOR]**
             product: 3c905 100BaseTX [Boomerang]
             vendor: 3Com Corporation
             physical id: a
             bus info: pci@00:0a.0
             logical name: eth0
             version: 00
             serial: 00:60:97:b8:46:58
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.38 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:b000-b03f **[COLOR="Red"]irq:3[/COLOR]**
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: b
             bus info: pci@00:0b.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy
             resources: ioport:a800-a81f irq:7
        *-input
             description: Input device controller
             product: SB Live! MIDI/Game Port
             vendor: Creative Labs
             physical id: b.1
             bus info: pci@00:0b.1
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport
             resources: ioport:a400-a407
     *-pci:1
          description: Host bridge
          product: VT82C596 Power Management
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:04.3
          version: 20
          width: 32 bits
          clock: 33MHz
-------------

i was constantly getting messages like this in system log messages...
"eth0 ......irq used by another device?"
i checked with lshw and saw that (can be seen above) usb controller and eth0 are sharing the same irq . i tried to re-assign the irq manually from bios. but the usb controller was again having the same irq with eth0. and by the way...`destination net unreachable" was the message that i was getting when i tried to ping my default gateway (adsl router)
and when i went totally crazy with the problem i just plugged my usb memory stick into one of the two usb ports of my desktop hoping that it would initiate something...and yes! it did i was able to ping my def. gateway; reach the internet and write you this message. but now i have a very very very slow network. i can use my windows notebook with the same wired connection and it's definitely fast. so i am quite sure that theres something wrong with my ubuntu desktop. and it's really strange ..these ping replies:

 ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=1028 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=18.3 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=1026 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=26.8 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=254 time=1034 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=254 time=34.4 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=254 time=1043 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=254 time=43.0 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=254 time=1050 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=254 time=50.5 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=254 time=1058 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=254 time=58.1 ms

ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (216.239.37.104) 56(84) bytes of data.
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=1 ttl=238 time=2003 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=2 ttl=240 time=994 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=3 ttl=240 time=2008 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=4 ttl=240 time=999 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=5 ttl=238 time=2007 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=6 ttl=240 time=998 ms


so its slow-faster-slow-faster-slow-faster and so on.

when i ping from my notebook (wireless connection) to ubuntu desktop the situation is similar, slow-faster-slow faster...

so, to summarize, i have a very very very slow network connection with my ubuntu desktop which is running only when i have my usb stick attached to one of the slots. please comment and help me get rid of this problem.
thanks and regards

---

### Post by chili555 on 2007-04-16
Are the IRQ's set in the BIOS explicitly, IRQ 1, IRQ 2, etc.? Can you reset all to AUTO? I would try that first. Let us know.

---

### Post by selim76 on 2007-04-17
i will check it and inform you, 
thanks

---

### Post by selim76 on 2007-04-18
setting irq settings to auto also didnt work, as far as i know it was already auto in the beginning and it was not working.after that i had changed them manually.
i have a solution for this now. i disabled usb support in BIOS. now my network is perfect, but obviously no usb port running...another thing in lshw now:

                 
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.1
          size: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci:0
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: e4000000
          bus info: pci@00:00.0
          version: 44
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e4000000-e7ffffff
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d8000000-dfffffff ioport:d800-d8ff iomemory:c7000000-c700ffff [COLOR="Red"]**irq:11**[/COLOR]
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                resources: iomemory:c8000000-cfffffff iomemory:c6800000-c680ffff
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT82C596 ISA [Mobile South]
             vendor: VIA Technologies, Inc.
             physical id: 4
             bus info: pci@00:04.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 4.1
             bus info: pci@00:04.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=VIA_IDE
             resources: ioport:b800-b80f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: Maxtor 6E040L0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 38GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: RICOH CD-R/RW MP7083A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-network
             description: Ethernet interface
             product: 3c905 100BaseTX [Boomerang]
             vendor: 3Com Corporation
             physical id: a
             bus info: pci@00:0a.0
             logical name: eth0
             version: 00
             serial: 00:60:97:b8:46:58
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical
             configuration: broadcast=yes driver=3c59x ip=192.168.1.38 multicast=yes
             resources: ioport:b000-b03f [COLOR="Red"]**irq:11**[/COLOR]
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: b
             bus info: pci@00:0b.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy
             resources: ioport:a800-a81f irq:11
        *-input
             description: Input device controller
             product: SB Live! MIDI/Game Port
             vendor: Creative Labs
             physical id: b.1
             bus info: pci@00:0b.1
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport
             resources: ioport:a400-a407
     *-pci:1
          description: Host bridge
          product: VT82C596 Power Management
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:04.3
          version: 20
          width: 32 bits
          clock: 33MHz
selo@UBUSELO:~$ clear

selo@UBUSELO:~$ sudo lshw
ubuselo                   
    description: Tower Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: P3V133
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS P3V133 ACPI BIOS Revision 1001a (12/23/1999)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: SLOT 1
          size: 600MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KB
             capacity: 512KB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 128MB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DIMM 3
     *-pci:0
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: e4000000
          bus info: pci@00:00.0
          version: 44
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e4000000-e7ffffff
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d8000000-dfffffff ioport:d800-d8ff iomemory:c7000000-c700ffff irq:11
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                resources: iomemory:c8000000-cfffffff iomemory:c6800000-c680ffff
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT82C596 ISA [Mobile South]
             vendor: VIA Technologies, Inc.
             physical id: 4
             bus info: pci@00:04.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 4.1
             bus info: pci@00:04.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=VIA_IDE
             resources: ioport:b800-b80f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: Maxtor 6E040L0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: NAR61EA0
                   serial: E1T5XKBE
                   size: 38GB
                   capacity: 38GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 37GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 729MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: RICOH CD-R/RW MP7083A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.10
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-network
             description: Ethernet interface
             product: 3c905 100BaseTX [Boomerang]
             vendor: 3Com Corporation
             physical id: a
             bus info: pci@00:0a.0
             logical name: eth0
             version: 00
             serial: 00:60:97:b8:46:58
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.38 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:b000-b03f irq:11
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: b
             bus info: pci@00:0b.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy
             resources: ioport:a800-a81f irq:11
        *-input
             description: Input device controller
             product: SB Live! MIDI/Game Port
             vendor: Creative Labs
             physical id: b.1
             bus info: pci@00:0b.1
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport
             resources: ioport:a400-a407
     *-pci:1
          description: Host bridge
          product: VT82C596 Power Management
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:04.3
          version: 20
          width: 32 bits
          clock: 33MHz

meaning that i now have same irq for ethernet card and graphics card, but network is perfect:

 ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (216.239.37.104) 56(84) bytes of data.
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=1 ttl=238 time=165 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=2 ttl=240 time=165 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=3 ttl=238 time=166 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=4 ttl=238 time=164 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=5 ttl=240 time=164 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=6 ttl=239 time=163 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=7 ttl=238 time=162 ms
64 bytes from va-in-f104.google.com (216.239.37.104): icmp_seq=8 ttl=239 time=162 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7284ms
rtt min/avg/max/mdev = 162.446/164.425/166.297/1.434 ms

~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=3.05 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=17.1 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=16.7 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=16.3 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=254 time=15.9 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=254 time=12.4 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=254 time=11.1 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=254 time=10.7 ms

--- 192.168.1.1 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7006ms
rtt min/avg/max/mdev = 3.052/12.949/17.157/4.461 ms


any newer ideas? 
kind regards
selim

---

### Post by Jouke74 on 2007-04-18
Open your computer, try plugging your 3com ethernet card into a different PCI slot if you have one or two free, otherwise, exchange the soundblaster card with your 3com. If you have free PCI slots, do this using different PCI slots until you have your IRQs arranged in such way that all hardware uses free IRQs if possible. You can see the IRQ assignment in your post screen right after boot-up so you wont have to load all your system. Probably one exchange is enough. PS. Enable your USB first, so the IRQ3 is used again, then start switching positions.

---

### Post by selim76 on 2007-04-21
guys thanks for the opinions, i set the settings to default in BIOS, after a few changes of the slots now i am running both usb and network without problem (even though now sound card and usb have the same irq!

 lshw          
    description: Tower Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: P3V133
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS P3V133 ACPI BIOS Revision 1001a (12/23/1999)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: SLOT 1
          size: 600MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KB
             capacity: 512KB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 128MB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DIMM 3
     *-pci:0
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: e4000000
          bus info: pci@00:00.0
          version: 44
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e4000000-e7ffffff
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d8000000-dfffffff ioport:d800-d8ff iomemory:c7000000-c700ffff irq:11
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                resources: iomemory:c8000000-cfffffff iomemory:c6800000-c680ffff
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT82C596 ISA [Mobile South]
             vendor: VIA Technologies, Inc.
             physical id: 4
             bus info: pci@00:04.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 4.1
             bus info: pci@00:04.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=VIA_IDE
             resources: ioport:b800-b80f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: Maxtor 6E040L0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: NAR61EA0
                   serial: E1T5XKBE
                   size: 38GB
                   capacity: 38GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 37GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 729MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: RICOH CD-R/RW MP7083A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.10
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: [COLOR="Red"]**USB Controller**[/COLOR]
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 4.2
             bus info: pci@00:04.2
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:b400-b41f [COLOR="Red"]**irq:5**[/COLOR]
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: [COLOR="Red"]**SB Live! EMU10k1**[/COLOR]
             vendor: Creative Labs
             physical id: 9
             bus info: pci@00:09.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy
             resources: ioport:b000-b01f [COLOR="Red"]**irq:5**[/COLOR]
        *-input
             description: Input device controller
             product: SB Live! MIDI/Game Port
             vendor: Creative Labs
             physical id: 9.1
             bus info: pci@00:09.1
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport
             resources: ioport:a800-a807
        [COLOR="Red"]***-network**[/COLOR]
             description: Ethernet interface
             product: 3c905 100BaseTX [Boomerang]
             vendor: 3Com Corporation
             physical id: b
             bus info: pci@00:0b.0
             logical name: eth0
             version: 00
             serial: 00:60:97:b8:46:58
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.38 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:a400-a43f [COLOR="Red"]**irq:10**[/COLOR]
     *-pci:1
          description: Host bridge
          product: VT82C596 Power Management
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:04.3
          version: 20
          width: 32 bits
          clock: 33MHz

---

