---
title: "No wireless networks found"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by Valshar on 2007-04-04
Well, a few days ago I upgraded to the Feisty beta, and all went fine. I just turned the laptop a few minutes ago, and network manager shows no wireless networks! Can anyone help? don't really know what to do... I'm sure the wireless network's there, I was using it just now on windows...

---

### Post by flossgeek on 2007-04-04
What wireless card do you have? Could you issue the command:-

```
lshw
``` 

and paste your output, we need to see if your card is recognised before going any further.

---

### Post by Valshar on 2007-04-04
Well I just got home and it seems it's working again,but not at full power. The signal keeps ranging from 5% to full capacity, which is kind of off, given I'm pretty sure the router's working fine.

```
laptop                    
    description: Computer
    product: Aspire 1690
    vendor: Acer, inc.
    version: Not Applicable
    serial: LXA6605034538089CCEM01
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=80A6E1E3-E963-0010-85BD-00C09FC866CA
  *-core
       description: Motherboard
       product: Crane II
       vendor: Acer, Inc.
       physical id: 0
       version: Not Applicable
       serial: LXA6605034538089CCEM01
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: 3A30 (08/10/05)
          size: 97KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1995MHz
          capacity: 2GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 16KB
             capacity: 16KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 2MB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 1010MB
          capacity: 3GB
        *-bank:0
             description: SODIMM DDR Synchronous [empty]
             physical id: 0
             slot: M1
        *-bank:1
             description: SODIMM DDR Synchronous [empty]
             physical id: 1
             slot: M2
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 915GM/PM Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: Radeon Mobility X700 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0
                resources: iomemory:d0000000-d7ffffff ioport:3000-30ff iomemory:c8100000-c810ffff irq:16
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1800-181f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-13-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1820-183f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-13-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1840-185f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-13-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1860-187f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-13-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:c8000000-c80003ff irq:20
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-13-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@06:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:c8216000-c8216fff irq:18
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 1.2
                bus info: pci@06:01.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3
                resources: iomemory:c8217000-c82177ff iomemory:c8210000-c8213fff irq:18
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 1.3
                bus info: pci@06:01.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: iomemory:c8214000-c8215fff irq:18
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@06:03.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:1d:c5:59
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.0.3 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
                resources: iomemory:c8218000-c8218fff irq:17
           *-network:1
                description: Ethernet interface
                product: NetXtreme BCM5788 Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 8
                bus info: pci@06:08.0
                logical name: eth0
                version: 03
                serial: 00:c0:9f:c8:66:ca
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 duplex=full firmware=5788-v3.01 latency=32 link=no mingnt=64 multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:c8200000-c820ffff irq:16
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@00:1e.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:1c00-1cff ioport:1880-18bf iomemory:c8000800-c80009ff iomemory:c8000400-c80004ff irq:17
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@00:1e.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:2400-24ff ioport:2000-207f irq:19
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:18c0-18cf irq:18
           *-disk
                description: SCSI Disk
                product: ST9100822A
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.01
                serial: 3LG0QJTZ
                size: 93GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Compaq diagnostics partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 3004MB
                   capabilities: primary boot
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 83GB
                   capabilities: primary bootable
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 5781MB
                   capabilities: primary
              *-volume:3
                   description: Linux swap / Solaris partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 1019MB
                   capabilities: primary nofs
           *-cdrom
                description: DVD writer
                product: DVDRW SLW-831S
                vendor: Slimtype
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: WRS1
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:20a0-20bf irq:11

```

Just posted it anyway to check if there's anything wrong, I don't think there is though. It's probably some interference, I guess

---

### Post by flossgeek on 2007-04-04
```

*-network:0
               description: Wireless interface
               product: PRO/Wireless 2200BG Network Connection
               vendor: Intel Corporation
               physical id: 3
               bus info: pci@06:03.0
               logical name: eth1
               version: 05
               serial: 00:13:ce:1d:c5:59
               width: 32 bits
               clock: 33MHz
               capabilities: bus_master cap_list ethernet physical wireless
               configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.0.3 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
               resources: iomemory:c8218000-c8218fff irq:17

```

Your card has been detected, I have the same card at it works fine for me on current feisty beta with all updates. The intel PRO/Wireless 2200BG works out of the box. 

However I had issues with mine on feisty  in the beggining but it was actually my router. Try reseting your router and reconfiguring it. If your hoster allows you to do **not** enter anything in your routers "Host Name" and "Domain Name" fields. **Leave them blank**. 

Try that....

---

### Post by Valshar on 2007-04-04
Actually I might have spotted some weird glitch or somethin', at that the time I posted I was doing an apt-get upgrade, and right after it was finished, the signal kept strong all the time, I tried it again and the same thing happened. It's working just fine anyway, so nevermind!

edit: oh, and thanks for the help, heh!

---

