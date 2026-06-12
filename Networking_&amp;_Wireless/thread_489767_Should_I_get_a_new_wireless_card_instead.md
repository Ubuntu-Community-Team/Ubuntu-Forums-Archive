---
title: "Should I get a new wireless card instead?"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by thychan on 2007-07-01
I installed ubuntu 6.06 LTS and then install kubuntu 6.06.  Bought a D-LINK Air D-LINK 650 (not the rev or + one).  It seems to recognize my card but it just can't communicate to my access point. Can any of you help?  Or should I get a different card.  I have reading a lot of posting about this card.  It seems people have all kind of different problems.  Here are my information:
lchan@lchan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"chanhome"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:CC:31:04
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/92  Signal level=12/153  Noise level=107/153
          Rx invalid nwid:0  Rx invalid crypt:8  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Note:  It actually list my Access point MAC address correctly

lchan@lchan-laptop:~$ sudo pccardctl ident
Password:
Socket 0:
  no product info available
Socket 1:
  product info: "", "Link DWL-650 11Mbps WLAN Card", "Version 01.02", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

lchan@lchan-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:40:05:de:3d:43
Sending on   LPF/eth1/00:40:05:de:3d:43
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



lchan@lchan-laptop:~$ sudo lshw
lchan-laptop
    description: Portable Computer
    product: Latitude C610
    vendor: Dell Computer Corporation
    serial: H2ZBD11
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-3200-105A-8042-C8C04F443131
  *-core
       description: Motherboard
       product: Latitude C610
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A16 (05/16/2003)
          size: 64KB
          capacity: 448KB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect pcmciaboot int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) III Mobile CPU      1000MHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.11.1
          slot: Microprocessor
          size: 731MHz
          capacity: 1333MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal varies unified
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KB
             capacity: 512KB
             clock: 66MHz (15ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM_A
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM_B
             size: 512MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: d0000000
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d0000000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82830 830 Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon Mobility M6 LY
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master vga_palette cap_list
                resources: iomemory:e0000000-e7ffffff ioport:c000-c0ff iomemory:fcff0000-fcffffff irq:11
        *-usb
             description: USB Controller
             product: 82801CA/CAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf80-bf9f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-28-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 78
                serial: 00:06:5b:db:ca:8c
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=full ip=192.168.1.102 link=yes multicast=yes port=MII speed=100MB/s
                resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1420
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:f8000000-f8000fff irq:11
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1420
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:f8001000-f8001fff irq:11
              *-network
                   description: Link DWL-650 11Mbps WLAN Card
                   product: Version 01.02
                   vendor: D
                   physical id: 0
                   slot: Socket 1
                   resources: irq:3
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:bfa0-bfaf iomemory:55000000-550003ff irq:11
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: HITACHI_DK23DA-20
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 00J2A0G0
                   serial: 115LCE
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 17GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 807MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: SAMSUNG CD-ROM SN-124
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: N001
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:d800-d8ff ioport:dc80-dcbf irq:5
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             resources: ioport:d400-d4ff ioport:dc00-dc7f irq:5
  *-battery
       product: DL
       vendor: SANYOU
       physical id: 1
       slot: Left Module Bay
       capacity: 247040mWh
       configuration: voltage=14.8V
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:40:05:de:3d:43
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 0.7.6 link=yes multicast=yes wireless=IEEE 802.11b

Thanks for the help.

---

