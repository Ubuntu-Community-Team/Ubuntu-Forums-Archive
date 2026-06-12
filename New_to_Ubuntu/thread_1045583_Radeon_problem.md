---
title: "Radeon problem"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by christopher.were on 2009-01-20
Hi,

I have a problem with Ubuntu 8.10 and my radeon graphics 512mb card, (it keeps hanging on ubuntu even with the standard open source drivers and no compiz effects or anything), how would I go about reporting this. I know there's a few commands I need to put into the terminal to determine my card's specs and stuff, but I can't remember what they are. Would anyone be able to help?

Chris

---

### Post by snova on 2009-01-20
> **christopher.were said:**
> I know there's a few commands I need to put into the terminal to determine my card's specs and stuff, but I can't remember what they are. Would anyone be able to help?

```
lspci
```

also

```
sudo lshw
```

---

### Post by christopher.were on 2009-02-02
I've put those commands into the console and this is what comes up.

christopher@cw-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
01:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary) (rev 9a)
02:01.0 Ethernet controller: Intel Corporation 82547GI Gigabit Ethernet Controller
03:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:03.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
christopher@cw-desktop:~$ 
christopher@cw-desktop:~$ 
```
christopher@cw-desktop:~$ sudo lshw
[sudo] password for christopher: 
cw-desktop                
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00000000-0000-0000-0000-00508DE3BF1D
  *-core
       description: Motherboard
       product: IC7-MAX3(Intel i875P-ICH5)
       vendor: [http://www.abit.com.tw/](http://www.abit.com.tw/)
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (11/01/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: Socket 478
          size: 3GHz
          capacity: 4GHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             physical id: 0
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             physical id: 1
             slot: A1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             physical id: 2
             slot: A2
             size: 512MiB
             width: 64 bits
        *-bank:3
             description: DIMM SDRAM Synchronous
             physical id: 3
             slot: A3
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82875P/E7210 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82875P Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV570 [Radeon X1950 Pro]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 9a
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 msi bus_master cap_list
                configuration: latency=32 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV570 [Radeon X1950 Pro] (secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 9a
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=32 mingnt=8
        *-pci:1
             description: PCI bridge
             product: 82875P/E7210 Processor to PCI to CSA Bridge
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 82547GI Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 00
                serial: 00:50:8d:e3:bf:1d
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
        *-system UNCLAIMED
             description: System peripheral
             product: 82875P/E7210 Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 2
                bus info: pci@0000:03:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: RAID bus controller
                product: SiI 3114 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: 3
                bus info: pci@0000:03:03.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=sata_sil latency=32 module=sata_sil
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi5
             logical name: scsi6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: Maxtor 6L160P0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@5:0.0.0
                logical name: /dev/sda
                version: BAJ4
                serial: L328G39G
                size: 152GiB (163GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=90909090
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: b1857e77-4932-4790-aa08-87e8236786cc
                   size: 146GiB
                   capacity: 146GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-01 15:12:57 filesystem=ext3 modified=2009-02-01 18:11:43 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-02-01 17:14:44 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sda2
                   size: 5922MiB
                   capacity: 5922MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5922MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD_RW ND-3540A
                vendor: _NEC
                physical id: 1
                bus info: scsi@6:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                serial: [_NEC    DVD_RW ND-3540A 1.0305091500
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
     *-scsi
          physical id: 1
          bus info: usb@4:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 31MiB (32MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=5f932f57
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/disk
                version: FAT16
                serial: 1469-ca45
                size: 15EiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:80:43:29:9b:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
christopher@cw-desktop:~$
```

---

