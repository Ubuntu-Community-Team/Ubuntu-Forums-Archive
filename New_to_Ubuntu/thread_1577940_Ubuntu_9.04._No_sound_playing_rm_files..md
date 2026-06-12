---
title: "Ubuntu 9.04. No sound playing rm files."
date: 2010-09-19
forum: New to Ubuntu
---

### Post by fredscripts on 2010-09-19
Hi!

When I open an rm file (video) with totem I can see the image but there's no sound. The error it gives is a python error:

```
diffred@fredlab:~/Desktop$ totem 13457.rm 
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: don't know how to handle audio/x-sipro, flavor=(int)3, rate=(int)16000, channels=(int)1, width=(int)16, leaf_size=(int)0, packet_size=(int)320, height=(int)6
```

I have an external USB soundcard and an audio mess installed in order to work properly (I attach screencap).

I also attach lshw command.

```
fredlab
    description: Desktop Computer
    product: MS-6547
    vendor: MSI
    version: 2.00
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: MS-6547
       vendor: MSI
       physical id: 0
       version: 2.00
       serial: 00000000
       slot: PCI2
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (12/20/01)
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.4
          slot: PGA478
          size: 2200MHz
          capacity: 3GHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 8KiB
             capacity: 1MiB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 512KiB
             capacity: 1MiB
             clock: 25MHz (40.0ns)
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 511MiB
     *-pci
          description: Host bridge
          product: SiS645 Host & Memory & AGP Controller
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-isa
             description: ISA bridge
             product: SiS961 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
           *-disk
                description: ATA Disk
                product: ST380011A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.01
                serial: 5JVKPHLK
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0a240a23
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 7acb84dd-0311-234c-a3de-70cb9a334856
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-11-09 20:12:34 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 23GiB
                   capacity: 23GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 10236MiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 13GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 345461c6-09e1-492a-87d2-3cef0a428483
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-06-12 13:53:32 filesystem=ext3 modified=2010-09-19 21:45:12 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-09-19 21:45:12 state=mounted
              *-volume:3
                   description: Linux swap volume
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 1
                   serial: 355d286b-7cb6-41f7-88de-1b7fb83458af
                   size: 972MiB
                   capacity: 972MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-M1612
                vendor: TOSHIBA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 1004
                capabilities: removable audio dvd
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 6
             bus info: pci@0000:00:06.0
             logical name: eth0
             version: 10
             serial: 00:a0:c5:b3:5e:48
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.2 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
     *-scsi
          physical id: 2
          bus info: usb@2:1.2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=454c4fc9
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/LaCie
                version: 3.1
                serial: 2e22dcba-646e-8e4b-8efd-f9a82cbf00d1
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2008-09-01 19:19:38 filesystem=ntfs label=LaCie mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6e:2b:cb:f1:0c:12
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by PriceChild on 2010-09-19
Wild stab in the dark, probably like taking a sledgehammer to a nail, but have you installed anything extra as this page explains: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

(There's also a link at the bottom showing how to install realplayer on Ubuntu)

---

### Post by cariboo on 2010-09-19
I seem to remember if you install the w32/w64codecs from the [Medibuntu]("http://medibuntu.org/") repositories, you should be able to play .rm files.

---

