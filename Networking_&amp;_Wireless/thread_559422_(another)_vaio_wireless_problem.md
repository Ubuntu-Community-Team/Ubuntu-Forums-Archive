---
title: "(another) vaio wireless problem"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by crab on 2007-09-25
Hi Everyone,
here's my problem. I have a vaio  pcg srx41P laptop running feisy 7.04. everything runs fine except the wireless car will not connect: I can see available wireless networks (but without their status) but cannot connect - the network automatically reverts to wired network.

I have another vaio (running identical system) with a different card which can connect to the various available networks so i am assuming it is not an encryption issue but a driver/harware issue?

card is, i think, : orinoco 802.11b mini pc

here's the output from lspci

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem (rev 03)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02)
01:02.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
01:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

and from lshw:

  description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 254MB
     *-cpu
          product: Intel(R) Pentium(R) III Mobile CPU       800MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.1
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82815 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 11
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus latency=0
             resources: iomemory:f8000000-fbffffff iomemory:f4000000-f407ffff irq:9
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@01:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3
                resources: iomemory:f4101000-f41017ff iomemory:f4104000-f4107fff irq:9
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c475
                vendor: Ricoh Co Ltd
                physical id: 2
                bus info: pci@01:02.0
                version: 80
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:f4102000-f4102fff iomemory:b00502010-b0050200f irq:9
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 5
                bus info: pci@01:05.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=64
                resources: iomemory:f4103000-f4103fff irq:9
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@01:08.0
                logical name: eth0
                version: 03
                serial: 08:00:46:45:98:27
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=195.224.189.36 latency=66 maxlatency=56 mingnt=8 multicast=yes
                resources: iomemory:f4100000-f4100fff ioport:3000-303f irq:9
        *-isa
             description: ISA bridge
             product: 82801BAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix latency=0
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:1800-180f
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1820-183f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: LaCie StudioDrive USB2
                   vendor: LaCie
                   physical id: 1
                   bus info: usb@1:1
                   version: 11.06
                   serial: 11100E0005E72258
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=98mA speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1810-181f irq:9
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:2400-241f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB Memory Stick Slot
                   vendor: Sony
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.01
                   capabilities: usb-1.10
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: ioport:1c00-1cff ioport:1840-187f irq:9
        *-communication UNCLAIMED
             description: Modem
             product: 82801BA/BAM AC'97 Modem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
             resources: ioport:2000-20ff ioport:1880-18ff irq:9
  *-scsi:0
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@3
       logical name: scsi3
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Wireless interface
       physical id: 3
       logical name: eth1
       serial: 00:02:2d:44:95:14
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=wlags49 driverversion=7.18 multicast=yes wireless=IEEE 802.11b

any help most appreciated,

thanks!

crab

---

### Post by crab on 2007-09-28
Hi all,

Finally managed to solve my own problem by installing WICD ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) to replace the default network manager. WICD allows the user to change driver through a graphic menu. I selected 'hostap' driver for my lucent/orinoco and lo and behold, it just works.

brilliant! hope this is useful to others

cheers!

crab

---

