---
title: "HDD Light on Thinkpad T23 Following 10.04 Upgrade"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by mapes12 on 2010-05-30
Hi

Recently upgraded from 9,04 to 9.10 which was only on this machine for an hour or so with updates so that I could then upgrade to 10.04

This is an IBM Thinkpad T23. I'll put the output to lshw at the end of this.

Since upgrading to 10.04 I have some issues that were not there with 9.04 which I had on here for some months. The issues:-

[LIST]
[*]10.04 takes much longer to boot than 9.04?
[*]The HDD light stays on for about 5 mins once boot has completed but I can't hear the drive working? This didn't happen in 9.04.
[*]Some websites freeze in FF (ebay) and I have to reset and reboot. This didn't happen in 9.04?
[/LIST]

Any thoughts.

> mark@mark-laptop:~$ sudo lshw
[sudo] password for mark: 
mark-laptop               
    description: Notebook
    product: 26474MG
    vendor: IBM
    version: Not Available
    serial: 55RYP8G
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=normal chassis=notebook uuid=DD868401-457D-11CB-91FB-8B19CE137CC0
  *-core
       description: Motherboard
       product: 26474MG
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: J1LG223X24W
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 1AET53WW (1.10 ) (03/07/2002)
          size: 144KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect pcmciaboot edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) III Mobile CPU      1133MHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.11.1
          slot: None
          size: 1130MHz
          capacity: 1133MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-dfffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82830 830 Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:c0100000-c01fffff memory:e0000000-ebffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: SuperSavage IX/C SDR
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 05
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=4
                resources: memory:c0100000-c017ffff memory:e8000000-ebffffff(prefetchable) memory:e4000000-e7ffffff(prefetchable) memory:e0000000-e1ffffff(prefetchable) memory:e2000000-e200ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1820(size=32)
        *-usb:2
             description: USB Controller
             product: 82801CA/CAM USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1840(size=32)
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 41
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:2000(size=20480) memory:c0200000-cfffffff memory:f0000000-f7ffffff(prefetchable)
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: irq:11 memory:50000000-50000fff ioport:2000(size=256) ioport:2400(size=256) memory:f0000000-f3ffffff(prefetchable) memory:c4000000-c7ffffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:51000000-51000fff ioport:2800(size=256) ioport:2c00(size=256) memory:f4000000-f7ffffff(prefetchable) memory:c8000000-cbffffff
           *-communication UNCLAIMED
                description: Communication controller
                product: WinModem 56k
                vendor: Agere Systems
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=0 maxlatency=14 mingnt=252
                resources: memory:c0201000-c02010ff ioport:6440(size=8) ioport:6000(size=256)
           *-network
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 41
                serial: 00:d0:59:be:75:66
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
                resources: irq:11 memory:c0200000-c0200fff ioport:6400(size=64)
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1860(size=16) memory:40000000-400003ff
           *-disk
                description: ATA Disk
                product: IC25N060ATMR04-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MO3O
                serial: MRG3W9KCJ60T9H
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00063d74
              *-volume
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 6683MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 47GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 2392MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: UJDA720 DVD/CDRW
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801CA/CAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: irq:11 ioport:1c00(size=256) ioport:18c0(size=64)
     *-network
          description: Wireless interface
          product: RT2500 802.11g Cardbus/mini-PCI
          vendor: RaLink
          physical id: 1
          bus info: pci@0000:03:00.0
          logical name: wlan1
          version: 01
          serial: 00:11:09:e6:90:ad
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=rt2500pci ip=192.168.1.67 latency=64 multicast=yes wireless=IEEE 802.11bg
          resources: irq:11 memory:c4000000-c4001fff
mark@mark-laptop:~$ 


---

### Post by mikewhatever on 2010-05-30
The freezes are probably related to Intel 8xx graphics rather then Firefox. 
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes)
I don't know about the disk issue.

---

