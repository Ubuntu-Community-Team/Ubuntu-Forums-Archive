---
title: "WIFI cardbus adaptor AR5212/5213 can scan, cannot connect v.14.04"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by Stefanos_K on 2014-05-08
Dear friends, 
I am new comer to Lubuntu 14.04 LTS on an old IBM Thinkpad r31 (Celeron 1,2) and I have a TL-WN610G (Atheros AR5212/5213) Wireless Buscard.

With Lubuntu everything ok, I'm very happy, ethernet works perfect. The last 2 days, I'm trying to set up wireless internet.

I can scan wireless networks, but I cannot connect. I installed with ndisgtk the windows drivers of the card and again the same.
I tried to disable key on router, nothing changed. I also tried 802.1 g/n or b-g connections, nothing changed.

I am missing something here and I am looking for your help

Thanks a lot.

Stef.

```

ibm                       
    description: Notebook
    product: 2656MLG
    &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: IBM
    version: Not Available
    serial: 5517PML
    &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=8DBD6320-E159-11D6-AB27-B477191095F1
  *-core
       description: &#924;&#951;&#964;&#961;&#953;&#954;&#942; &#954;&#940;&#961;&#964;&#945;
       product: 2656MLG
       &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: IBM
       physical id: 0
       version: Not Available
       serial: 5510AHM
     *-firmware
          description: BIOS
          &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: IBM
          physical id: 0
          version: 1FETE2WW (3.020)
          date: 08/20/2002
          &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 64KiB
          &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp smartbattery biosbootspecification uefi
     *-cpu:0 DISABLED
          description: &#922;&#949;&#957;&#964;&#961;&#953;&#954;&#942; &#956;&#959;&#957;&#940;&#948;&#945; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962; (CPU) [empty]
          product: Celeron
          &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel
          physical id: 400
          version: Celeron(TM)
          &#965;&#960;&#959;&#948;&#959;&#967;&#942;: U11
        *-cache:0
             description: L1 cache
             physical id: 700
             &#965;&#960;&#959;&#948;&#959;&#967;&#942;: Internal L1 Cache
             &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 32KiB
             &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 32KiB
             capabilities: internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 701
             &#965;&#960;&#959;&#948;&#959;&#967;&#942;: Internal L2 Cache
             &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 256KiB
             &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 256KiB
             capabilities: pipeline-burst internal write-through unified
     *-memory
          description: &#924;&#957;&#942;&#956;&#951; &#963;&#965;&#963;&#964;&#942;&#956;&#945;&#964;&#959;&#962;
          physical id: 1000
          &#965;&#960;&#959;&#948;&#959;&#967;&#942;: &#928;&#955;&#945;&#954;&#941;&#964;&#945; &#963;&#965;&#963;&#964;&#942;&#956;&#945;&#964;&#959;&#962; &#942; &#956;&#951;&#964;&#961;&#953;&#954;&#942; &#960;&#955;&#945;&#954;&#941;&#964;&#945;
          &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 256MiB
          &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             physical id: 0
             &#965;&#960;&#959;&#948;&#959;&#967;&#942;: DM2
             &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 128MiB
             &#960;&#955;&#940;&#964;&#959;&#962;: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             physical id: 1
             &#965;&#960;&#959;&#948;&#959;&#967;&#942;: CN22
             &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 128MiB
             &#960;&#955;&#940;&#964;&#959;&#962;: 64 bits
     *-cpu:1
          product: Mobile Intel(R) Celeron(TM) CPU         1200MHz
          &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corp.
          physical id: 1
          &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: cpu@0
          version: 6.11.4
          &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 500MHz
          &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 256KiB
     *-pci
          description: Host bridge
          product: 82830M/MG/MP Host Bridge
          &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
          physical id: 100
          &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:00.0
          version: 04
          &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
          &#961;&#959;&#955;&#972;&#953;: 33MHz
          configuration: driver=agpgart-intel
          &#960;&#972;&#961;&#959;&#953;: irq:0
        *-display:0
             description: VGA compatible controller
             product: 82830M/MG Integrated Graphics Controller
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 2
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:02.0
             version: 04
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             &#960;&#972;&#961;&#959;&#953;: irq:11 &#956;&#957;&#942;&#956;&#951;:98000000-9fffffff &#956;&#957;&#942;&#956;&#951;:90100000-9017ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830M/MG Integrated Graphics Controller
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 2.1
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:02.1
             version: 00
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0 maxlatency=11
             &#960;&#972;&#961;&#959;&#953;: &#956;&#957;&#942;&#956;&#951;:88000000-8fffffff &#956;&#957;&#942;&#956;&#951;:80200000-8027ffff
        *-usb:0
             description: USB controller
             product: 82801CA/CAM USB Controller #1
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 1d
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:1d.0
             version: 02
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             &#960;&#972;&#961;&#959;&#953;: irq:11 ioport:a4a0(size=32)
        *-usb:1
             description: USB controller
             product: 82801CA/CAM USB Controller #2
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 1d.1
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:1d.1
             version: 02
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             &#960;&#972;&#961;&#959;&#953;: irq:11 ioport:a4e0(size=32)
        *-usb:2
             description: USB controller
             product: 82801CA/CAM USB Controller #3
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 1d.2
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:1d.2
             version: 02
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             &#960;&#972;&#961;&#959;&#953;: irq:11 ioport:a800(size=32)
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 1e
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:1e.0
             version: 42
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             capabilities: pci normal_decode bus_master
             &#960;&#972;&#961;&#959;&#953;: ioport:7000(size=4096) &#956;&#957;&#942;&#956;&#951;:80100000-801fffff &#956;&#957;&#942;&#956;&#951;:10000000-13ffffff
           *-network
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
                &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
                physical id: 8
                &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:01:08.0
                &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: eth0
                version: 42
                serial: 00:00:e2:8c:9b:ee
                &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 100Mbit/s
                &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 100Mbit/s
                &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
                &#961;&#959;&#955;&#972;&#953;: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.1.64 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                &#960;&#972;&#961;&#959;&#953;: irq:11 &#956;&#957;&#942;&#956;&#951;:80100000-80100fff ioport:7000(size=64)
           *-pcmcia
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Texas Instruments
                physical id: 9
                &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:01:09.0
                version: 02
                &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
                &#961;&#959;&#955;&#972;&#953;: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                &#960;&#972;&#961;&#959;&#953;: irq:11 &#956;&#957;&#942;&#956;&#951;:18000000-18000fff ioport:7400(size=256) ioport:7800(size=256) &#956;&#957;&#942;&#956;&#951;:10000000-13ffffff &#956;&#957;&#942;&#956;&#951;:1c000000-1fffffff
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 1f
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:1f.0
             version: 02
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             &#960;&#972;&#961;&#959;&#953;: irq:0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 1f.1
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:1f.1
             version: 02
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             &#960;&#972;&#961;&#959;&#953;: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:a890(size=16) &#956;&#957;&#942;&#956;&#951;:14000000-140003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801CA/CAM SMBus Controller
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 1f.3
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:1f.3
             version: 02
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             configuration: latency=0
             &#960;&#972;&#961;&#959;&#953;: ioport:8000(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 1f.5
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:1f.5
             version: 02
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             capabilities: bus_master
             configuration: driver=snd_intel8x0 latency=0
             &#960;&#972;&#961;&#959;&#953;: irq:11 ioport:9800(size=256) ioport:9c00(size=64)
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
             physical id: 1f.6
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:00:1f.6
             version: 02
             &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
             &#961;&#959;&#955;&#972;&#953;: 33MHz
             capabilities: generic
             configuration: latency=0
             &#960;&#972;&#961;&#959;&#953;: ioport:a000(size=256) ioport:a400(size=128)
     *-network UNCLAIMED
          description: Ethernet controller
          product: AR5212/AR5213 Wireless Network Adapter
          &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Qualcomm Atheros
          physical id: 2
          &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:02:00.0
          version: 01
          &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
          &#961;&#959;&#955;&#972;&#953;: 33MHz
          capabilities: pm cap_list
          configuration: latency=128 maxlatency=28 mingnt=10
          &#960;&#972;&#961;&#959;&#953;: &#956;&#957;&#942;&#956;&#951;:1c000000-1c00ffff
     *-scsi:0
          physical id: 3
          &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: IC25N020ATCS04-0
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Hitachi
             physical id: 0.0.0
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: scsi@0:0.0.0
             &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: /dev/sda
             version: CA2O
             serial: CSH206D9G4NYJF
             &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 18GiB (20GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=b7e8b7e8
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: scsi@0:0.0.0,1
                &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: /dev/sda1
                version: 3.1
                serial: 62e1faee-8b0b-c24d-8483-1348cd440135
                &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 10239MiB
                &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 10239MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2014-05-03 21:05:10 filesystem=ntfs state=clean
           *-volume:1
                description: Linux swap volume
                physical id: 2
                &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: scsi@0:0.0.0,2
                &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: /dev/sda2
                version: 1
                &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 509MiB
                &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 509MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: Windows FAT volume
                &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: MSWIN4.1
                physical id: 3
                &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: scsi@0:0.0.0,3
                &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: /dev/sda3
                version: FAT32
                serial: 3d4f-15f0
                &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 1146MiB
                &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 1151MiB
                capabilities: primary hidden fat initialized
                configuration: FATs=2 filesystem=fat label=IBM_SERVICE
           *-volume:3
                description: Extended partition
                physical id: 4
                &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: scsi@0:0.0.0,4
                &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: /dev/sda4
                &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 7174MiB
                &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 7174MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: /dev/sda5
                   &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: /
                   &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 7174MiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 4
          &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: scsi1
          capabilities: emulated
        *-cdrom
             description: SCSI CD-ROM
             product: CD-224E
             &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: TEAC
             physical id: 0.0.0
             &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: scsi@1:0.0.0
             &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: /dev/cdrom
             &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: /dev/sr0
             version: 2.9A
             serial: [
             capabilities: removable audio
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: &#921;&#972;&#957;&#964;&#969;&#957; &#923;&#953;&#952;&#943;&#959;&#965; Battery
       physical id: 1
       &#965;&#960;&#959;&#948;&#959;&#967;&#942;: On the Right-hand side
stefanos@ibm:~$ iwconfig
irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

stefanos@ibm:~$ lsmod
Module                  Size  Used by
cfg80211              409394  0 
ndiswrapper           192915  0 
gpio_ich               13229  0 
thinkpad_acpi          69003  0 
nvram                  14027  1 thinkpad_acpi
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 51828  0 
snd_intel8x0           33110  1 
snd_rawmidi            25135  1 snd_seq_midi
snd_ac97_codec        105709  1 snd_intel8x0
yenta_socket           40201  0 
psmouse                91033  0 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
pcmcia_rsrc            18319  1 yenta_socket
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
serio_raw              13230  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_timer              28584  2 snd_pcm,snd_seq
bnep                   18895  2 
lpc_ich                16864  0 
rfcomm                 53664  0 
shpchp                 32128  0 
snd                    60871  11 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,thinkpad_acpi,snd_seq_device,snd_seq_midi
nsc_ircc               22475  0 
i915                  705396  2 
bluetooth             342263  10 bnep,rfcomm
irda                  107386  1 nsc_ircc
drm_kms_helper         46907  1 i915
soundcore              12600  1 snd
crc_ccitt              12627  1 irda
drm                   243792  3 i915,drm_kms_helper
video                  18903  1 i915
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47035  0 
hid                    87604  2 hid_generic,usbhid
e100                   35945  0 
mii                    13654  1 e100

  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Intel Corporation
       physical id: 8
       &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:01:08.0
       &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: eth0
       version: 42
       serial: 00:00:e2:8c:9b:ee
       &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 100Mbit/s
       &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 100Mbit/s
       &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
       &#961;&#959;&#955;&#972;&#953;: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.1.64 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       &#960;&#972;&#961;&#959;&#953;: irq:11 &#956;&#957;&#942;&#956;&#951;:80100000-80100fff ioport:7000(size=64)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Wireless Network Adapter
       &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Qualcomm Atheros
       physical id: 2
       &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:02:00.0
       version: 01
       &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
       &#961;&#959;&#955;&#972;&#953;: 33MHz
       capabilities: pm cap_list
       configuration: latency=128 maxlatency=28 mingnt=10
       &#960;&#972;&#961;&#959;&#953;: &#956;&#957;&#942;&#956;&#951;:1c000000-1c00ffff
stefanos@ibm:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:00:E2:8C:9B:EE

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


```

finaly it was a matter of my router (Thomson). I changed router and everything works fine.

Happy about it.

Hugs everybody
Stefanos

---

