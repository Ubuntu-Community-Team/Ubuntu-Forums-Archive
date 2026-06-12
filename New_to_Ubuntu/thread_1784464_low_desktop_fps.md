---
title: "low desktop fps"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by fartofagony on 2011-06-17
Hi!

I installed ubuntu again and whenever i move a window around with the mouse arrow, it doesnt move s smooth as it should move, same thing when I scroll up/down etc etc. :(

i installed the ATI drivers in ubuntu, dont know if tht causes more problems or if it helps.

thanks

---

### Post by wildmanne39 on 2011-06-17
> **fartofagony said:**
> Hi!

I installed ubuntu again and whenever i move a window around with the mouse arrow, it doesnt move s smooth as it should move, same thing when I scroll up/down etc etc. :(

i installed the ATI drivers in ubuntu, dont know if tht causes more problems or if it helps.

thanksHi, run this in a terminal
```
sudo lshw
```and post it back here by clicking on new reply and click # and paste the information between the brackets. Also tell us what version of ubuntu are you using? if natty are you logged in to unity or ubuntu classic, have you changed any settings in compiz?

---

### Post by fartofagony on 2011-06-17
```
 *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:da105c00-da105fff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:da100000-da103fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:5000(size=4096) memory:d9000000-d9ffffff ioport:d0000000(size=16777216)
           *-network
                description: Ethernet interface
                product: NetLink BCM57780 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:26:22:56:dd:75
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb ip=85.225.110.9 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:49 memory:d9000000-d900ffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:4000(size=4096) memory:d8000000-d8ffffff ioport:d1000000(size=16777216)
           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 00:22:fb:56:88:ac
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic-pae firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:47 memory:d8000000-d8001fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096) memory:d7000000-d7ffffff ioport:d2000000(size=16777216)
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:d5000000-d5ffffff ioport:d4000000(size=16777216)
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:16 memory:d5000000-d50007ff memory:d5000d00-d5000d7f memory:d5000c80-d5000cff memory:d5000c00-d5000c7f
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:06:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:d5000b00-d5000bff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:06:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:d5000a00-d5000aff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:06:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:d5000900-d50009ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:06:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:d5000800-d50008ff
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:da105800-da105bff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:7048(size=8) ioport:7054(size=4) ioport:7040(size=8) ioport:7050(size=4) ioport:7020(size=32) memory:da105000-da1057ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54505
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PB4O
                serial: 091007PBG400Q7J6830V
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2f383e35
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 206f-966f
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-10-17 10:08:23 filesystem=ntfs label=PQSERVICE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: a8db4ad9-5674-554a-b51f-7d739233b727
                   size: 3580MiB
                   capacity: 3584MiB
                   capabilities: primary boot ntfs initialized
                   configuration: clustersize=4096 created=2009-10-17 10:08:24 filesystem=ntfs label=ARCADE state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 2070-5c41
                   size: 97MiB
                   capacity: 101MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=512 created=2009-10-17 10:08:25 filesystem=ntfs label=SYSTEM RESERVED state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 450GiB
                   capacity: 450GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /host
                      capacity: 450GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: BD-ROM BDCTD01RS
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:da106000-da1060ff ioport:7000(size=32)
        *-generic:6 UNCLAIMED
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:da104000-da104fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=i7core_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:03.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:03.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Core Processor Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:ff:03.4
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:ff:04.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:ff:04.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:ff:04.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:ff:04.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:ff:05.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:ff:05.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:ff:05.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:ff:05.3
          version: 04
          width: 32 bits
          clock: 33MHz
  *-battery
       description: Lithium Ion Battery
       product: Li-lon Battery
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 10/12/2007
       serial: Battery 0
       slot: Fake
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 2
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh

```
I am using 11.04 inside windows.
After the installaton was complete I followed some instructions from youtube on how to get/intall codecs and the thing that popped up in the upper right corner that looked like a green chip which installed some ati drivers i think

---

### Post by fartofagony on 2011-06-17
i cant figure this out :( anyone?

---

### Post by wildmanne39 on 2011-06-17
> **fartofagony said:**
> ```
 *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:da105c00-da105fff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:da100000-da103fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:5000(size=4096) memory:d9000000-d9ffffff ioport:d0000000(size=16777216)
           *-network
                description: Ethernet interface
                product: NetLink BCM57780 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:26:22:56:dd:75
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb ip=85.225.110.9 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:49 memory:d9000000-d900ffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:4000(size=4096) memory:d8000000-d8ffffff ioport:d1000000(size=16777216)
           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 00:22:fb:56:88:ac
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic-pae firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:47 memory:d8000000-d8001fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096) memory:d7000000-d7ffffff ioport:d2000000(size=16777216)
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:d5000000-d5ffffff ioport:d4000000(size=16777216)
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:16 memory:d5000000-d50007ff memory:d5000d00-d5000d7f memory:d5000c80-d5000cff memory:d5000c00-d5000c7f
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:06:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:d5000b00-d5000bff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:06:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:d5000a00-d5000aff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:06:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:d5000900-d50009ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:06:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:d5000800-d50008ff
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:da105800-da105bff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:7048(size=8) ioport:7054(size=4) ioport:7040(size=8) ioport:7050(size=4) ioport:7020(size=32) memory:da105000-da1057ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54505
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PB4O
                serial: 091007PBG400Q7J6830V
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2f383e35
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 206f-966f
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-10-17 10:08:23 filesystem=ntfs label=PQSERVICE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: a8db4ad9-5674-554a-b51f-7d739233b727
                   size: 3580MiB
                   capacity: 3584MiB
                   capabilities: primary boot ntfs initialized
                   configuration: clustersize=4096 created=2009-10-17 10:08:24 filesystem=ntfs label=ARCADE state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 2070-5c41
                   size: 97MiB
                   capacity: 101MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=512 created=2009-10-17 10:08:25 filesystem=ntfs label=SYSTEM RESERVED state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 450GiB
                   capacity: 450GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /host
                      capacity: 450GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: BD-ROM BDCTD01RS
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:da106000-da1060ff ioport:7000(size=32)
        *-generic:6 UNCLAIMED
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:da104000-da104fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=i7core_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:03.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:03.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Core Processor Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:ff:03.4
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:ff:04.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:ff:04.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:ff:04.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:ff:04.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:ff:05.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:ff:05.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:ff:05.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:ff:05.3
          version: 04
          width: 32 bits
          clock: 33MHz
  *-battery
       description: Lithium Ion Battery
       product: Li-lon Battery
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 10/12/2007
       serial: Battery 0
       slot: Fake
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 2
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh

```
I am using 11.04 inside windows.
After the installaton was complete I followed some instructions from youtube on how to get/intall codecs and the thing that popped up in the upper right corner that looked like a green chip which installed some ati drivers i think
Hi, I do not see anything in the information you posted that would cause the problem. Did the problem start after you installed the ATI driver? At the log in screen click on your user name and go to the bottom of the screen and log in as ubuntu classic with no effects and see if the problem is still there.

---

### Post by fartofagony on 2011-06-17
> **wildmanne39 said:**
> Hi, I do not see anything in the information you posted that would cause the problem. Did the problem start after you installed the ATI driver? At the log in screen click on your user name and go to the bottom of the screen and log in as ubuntu classic with no effects and see if the problem is still there.

I did as you said I should do and problem solved!
Before the ATI drivers it was the same unfortnally.
do you know why it is smoother with the classic ubuntu with no effects? im very curious! if not, no problems!

Thank you sooo much! you saved my life! because sitting on this chair day&night is my life!

---

### Post by compmodder26 on 2011-06-17
It's smoother because no desktop effects are running, meaning that the 3D capabilities of your video card are not being used (or attempting to be used).  So it would still seem that you don't have the proper drivers installed to be able to leverage the 3D capabilities of your card.

---

### Post by wildmanne39 on 2011-06-17
> **fartofagony said:**
> I did as you said I should do and problem solved!
Before the ATI drivers it was the same unfortnally.
do you know why it is smoother with the classic ubuntu with no effects? im very curious! if not, no problems!

Thank you sooo much! you saved my life! because sitting on this chair day&night is my life!
Hi, also could be because it is easier on resources but I suspect it is a problem with the driver and your card with compiz, I have not used a wubi install before so I can not be totally sure, but it could work better with a normal install a wubi install is just to check ubuntu out and see if you like it then you can install it normally, but there is no guarantee that it would work better with a normal install, I am glad you have it working. would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by Jacobonbuntu on 2011-06-17
> **fartofagony said:**
> Hi!

I installed ubuntu again and whenever i move a window around with the mouse arrow, it doesnt move s smooth as it should move, same thing when I scroll up/down etc etc. :(

i installed the ATI drivers in ubuntu, dont know if tht causes more problems or if it helps.

thanks


Hi fartofagony,

open compiz (or install it if it is not there) go to open GL, switch off the "Sync to VBlank" -entry, I had the same with my ATI card, found this tip somewhere and in my case it improved a lot,

hope it helps!


edit: 
Ah, I should start reading posts better, didn't see the problem was solved already....

take care!

---

