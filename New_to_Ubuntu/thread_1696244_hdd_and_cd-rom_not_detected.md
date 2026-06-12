---
title: "hdd and cd-rom not detected"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by vik.gelin on 2011-02-27
hello friends 
i installed a P4M800-M7 motherboard in my system and  BIOS detects my  HDD and cd rom but  Ubuntu 9.10  is not detecting them
and this is the IDE/SATA info of the lshw command ::



```
ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Desktop Computer
    product: P4M800-M7
    vendor: ECS
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4M800-M7
       vendor: ECS
       physical id: 0
       version: 1.0
       serial: 00000000
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080011 (07/29/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          slot: CPU 1
          size: 2660MHz
          capacity: 2660MHz
          width: 64 bits
          clock: 532MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: P4M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:f8000000-fbffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: memory:fca00000-feafffff memory:eff00000-f7efffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: KM400/KN400/P4M800 [S3 UniChrome]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:f0000000-f3ffffff(prefetchable) memory:fd000000-fdffffff memory:feaf0000-feafffff(prefetchable)
        *-network:0
             description: Ethernet interface
             product: SC92031 PCI Fast Ethernet Adapter
             vendor: Hangzhou Silan Microelectronics Co., Ltd.
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: eth1
             version: 01
             serial: 00:e0:20:b4:30:3c
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sc92031 duplex=half latency=64 link=no maxlatency=40 mingnt=20 multicast=yes port=MII speed=10MB/s
             resources: irq:16 memory:febffc00-febffcff ioport:e800(size=256) memory:febc0000-febdffff(prefetchable)
        *-communication
             description: Modem
             product: SM56 Data Fax Modem
             vendor: Motorola
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=serial latency=64 maxlatency=62 mingnt=1
             resources: irq:17 memory:febfe000-febfefff ioport:e400(size=256)
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=64
             resources: irq:20 ioport:ec00(size=8) ioport:e080(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d880(size=16) ioport:d400(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:d800(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:d080(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:d000(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:cc00(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:21 memory:febff800-febff8ff
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:c800(size=256)
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:14:2a:56:bd:7f
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=10.1.132.78 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: irq:23 ioport:c400(size=256) memory:febff400-febff4ff
     *-pci:1
          description: Host bridge
          product: P4M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: P4M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@1:7
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             size: 3824MiB (4009MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000b8743
           *-volume
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /cdrom
                logical name: /casper-rw-backing
                version: FAT32
                serial: 0123-c91b
                size: 3821MiB
                capacity: 3821MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,errors=remount-ro state=mounted
ubuntu@ubuntu:~$
```

---

### Post by fabricator4 on 2011-02-27
> **vik.gelin said:**
> *-disk
description: SCSI Disk
physical id: 0.0.0
bus info: scsi@4:0.0.0
logical name: /dev/sda
size: 3824MiB (4009MB)
capabilities: partitioned partitioned:dos
configuration: signature=000b8743

Obviously Ubuntu is seeing the HDD fine, it is a 4GB FAT32 partition.  The CD is also working - you've booted off the live CD by the look of it.

The reason you may only be seeing 4Gb of the partition (if it's larger than that) is that fat 32 has a **file**size limit of 4 GB.  There may be a work around, but regardless of whether you stay with windows, have a dual boot system, or migrate entirely to Ubuntu you really need to update that FAT32 Partition.

Even windows will have a problem, if its boot files get moved outside of the 4GB address range.  That's one of the reasons that Microsoft disabled FAT32 installations on larger drives in XP and beyond. (ME and 95 could do it however, as long as you avoided the gotcha in the previous sentence.

What are you trying to do?  If you want to install Ubuntu on that machine the easiest way is to just run the installation program and select "Use the entire disk", in which case it will repartition and format the disk for you before installing Ubuntu.  Backup any important data first, of course.

The current version is 10.10 by the way, or you might consider the LTS release, 10.04

Chris

---

### Post by vik.gelin on 2011-02-27
> **fabricator4 said:**
> Obviously Ubuntu is seeing the HDD fine, it is a 4GB FAT32 partition.  The CD is also working - you've booted off the live CD by the look of it.

The reason you may only be seeing 4Gb of the partition (if it's larger than that) is that fat 32 has a **file**size limit of 4 GB.  There may be a work around, but regardless of whether you stay with windows, have a dual boot system, or migrate entirely to Ubuntu you really need to update that FAT32 Partition.

Even windows will have a problem, if its boot files get moved outside of the 4GB address range.  That's one of the reasons that Microsoft disabled FAT32 installations on larger drives in XP and beyond. (ME and 95 could do it however, as long as you avoided the gotcha in the previous sentence.

What are you trying to do?  If you want to install Ubuntu on that machine the easiest way is to just run the installation program and select "Use the entire disk", in which case it will repartition and format the disk for you before installing Ubuntu.  Backup any important data first, of course.

The current version is 10.10 by the way, or you might consider the LTS release, 10.04

Chris
friend neither i am trying to install Ubuntu nor do i have windows installed on my system.i had a gigabyte motherboard and that was having some problems so i replaced it with the current one.when i started the system for the first time with fedora-14 being installed in my 40 gb hard disc,i started facing the resolution problems.the link to tht problem is 
[http://ubuntuforums.org/showthread.php?t=1695554](http://ubuntuforums.org/showthread.php?t=1695554)
.so i formatted fedora and installed mendriva inside tht partition.but after installing mandriva the system failed to boot from hard disc.then i used a live cd of Ubuntu 9.10 (having same resolution problem) to use my pc but it failed to detect the hard disc.then i made a bootable USB which is a 4 -gb kingston with FAT32 format. currently i am running my machine with that bootable live usb only.now here came the problem ,the BIOS was detecting the hard disc but Ubuntu failed to mount it.the problems were same with ubuntu 10.10 installed and even worse i guess.that was all.
what all things i need to do so that my system may detect the hdd.thank u .:confused:

---

### Post by Hoopz on 2011-02-27
You may have a dead hard drive judging by that BIOS POST screenshot SMART command failed

---

### Post by vik.gelin on 2011-02-27
> **Hoopz said:**
> You may have a dead hard drive judging by that BIOS POST screenshot SMART command failed
plz tell me how to know if the hard drive is dead .it is spinning inside and is getting heated as far as i know .

---

### Post by Hoopz on 2011-02-27
what you can do is download samsung's diagnostics program to test it.  Here's a link to it [http://www.samsung.com/global/business/hdd/support/utilities/Support_Shdiag.html](http://www.samsung.com/global/business/hdd/support/utilities/Support_Shdiag.html)

or download Hiren's Boot cd and boot from the cd and run samsung's or one of the other diagnostics programs it offers

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

---

### Post by davidmohammed on 2011-02-27
it could be a sata1.0 vs sata2.0 issue - on your motherboard are there any jumper settings you can change (jumper 5 & 6 maybe?)

Also - in the bios - you've got a RAID controller - suggest change the settings to make it a standard sata connection (or may be run in IDE compatibility mode if you've got that option).

---

