---
title: "USB 2.0 card not detected"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by marktebbutt on 2009-02-08
Hi all,
Hopefully this is something simple, but it is pretty frustrating - my system seems to be working ok, but it does not detect my USB 2.0 slots. I have looked around but can't see how I can fix this. Can anybody point me in the right direction?
(I'm running 8.04 on a desktop PC.)
Thanks as always.

---

### Post by blueridgedog on 2009-02-08
To make things easier to trouble shoot, can you post the output of 

```
sudo lshw
```

and 

```
lsusb
```

Thanks.

Also, can you clarify if your USB 2.0 ports are via an add-on card or not and how you determined that it is the ports versus the devices you have plugged in to them.

---

### Post by marktebbutt on 2009-02-08
Hi,
The outputs from the commands you mentioned are:

mark-desktop              
    description: Desktop Computer
    product: VT82C694X
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 694T-686
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (07/13/2001)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.10
          slot: Socket 370
          size: 1GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 128KiB
             capacity: 2MiB
             capabilities: synchronous external write-back
     *-memory
          description: Flash Memory
          physical id: 1f
          slot: System board or motherboard
          size: 512MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 256MiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: BANK_1
             size: 256MiB
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: BANK_2
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: BANK_3
     *-pci
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c4
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 15
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: ST380013A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.1.0
                logical name: /dev/sda
                version: 3.54
                serial: 5JT1JA3M
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=07e30b32
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 480d9f50-f5fe-6348-b479-f676acd2c7d6
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-08-18 23:55:10 filesystem=ntfs state=clean
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: a47a71da-9a88-4001-b2ae-9819a3626c0e
                   size: 1906MiB
                   capacity: 1906MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.1.0,3
                   logical name: /dev/sda3
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: a3fd7296-1d3f-443f-972c-abb7b432a3e0
                   size: 23GiB
                   capacity: 23GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-10-09 21:57:44 filesystem=ext3 modified=2009-02-08 03:07:19 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-02-08 03:07:19 state=mounted
           *-cdrom:0
                description: DVD writer
                product: DVD_RW ND-2500A
                vendor: _NEC
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.06
                serial: [_NEC    DVD_RW ND-2500A 1.0603121900
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW CW5205
                vendor: ATAPI
                physical id: 1
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 180C
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: latency=0
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 9.1
             bus info: pci@0000:00:09.1
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 9.2
             bus info: pci@0000:00:09.2
             version: 65
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: RTL8139 Ethernet
             vendor: D-Link System Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: 10
             serial: 00:40:05:04:d0:7d
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.105 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-communication UNCLAIMED
             description: Communication controller
             product: HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem
             vendor: Rockwell International
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3 module=ohci1394
        *-multimedia
             description: Multimedia audio controller
             product: 5880 AudioPCI
             vendor: Ensoniq
             physical id: d
             bus info: pci@0000:00:0d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ENS1371 latency=32 maxlatency=128 mingnt=12 module=snd_ens1371
     *-scsi
          physical id: 1
          bus info: firewire@00101003001155cc
          logical name: scsi2
        *-disk
             description: SCSI Disk
             product: ST3500641A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 4.07
             serial: &
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=c3b0a73f
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/Music and Video
                version: 3.1
                serial: 9c354400-a036-ad4c-9330-5db0835902f8
                size: 146GiB
                capacity: 146GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2007-08-02 22:18:02 filesystem=ntfs label=Music and Video mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                size: 319GiB
                capacity: 319GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sdb5
                   logical name: /media/Back Up Drive
                   capacity: 83GiB
                   configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
              *-logicalvolume:1
                   description: HPFS/NTFS partition
                   physical id: 6
                   logical name: /dev/sdb6
                   logical name: /media/RawVideo
                   capacity: 166GiB
                   configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
              *-logicalvolume:2
                   description: HPFS/NTFS partition
                   physical id: 7
                   logical name: /dev/sdb7
                   logical name: /media/Photographs
                   capacity: 63GiB
                   configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted


mark@mark-desktop:~$ lsusb
Bus 005 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I am assuming it is the ports because the devices I am trying to connect work ok with windows - iPod, USB stick etc. The card was added recently, but works ok with windows.

Thanks for your help.

---

### Post by marktebbutt on 2009-02-08
Now that is odd - after responding to the previous email, the explorer windows have opened up for my USB stick - it now seems to be working. Should the command lsusb actually start up the USB card? (Sorry if this sounds dumb, but I don't know why it should suddenly start working - and I want to make sure that next time I know what to do.)

---

### Post by blueridgedog on 2009-02-08
No, lsusb simply shows what is there.  I was about to reply that it looks as if your add-in card is supported based on the hardware data.  If you have the problem again, plug in the device and view the output of lsusb.  It should show you the device then you can troubleshoot why you can (with forum members) interact with the device.

---

### Post by marktebbutt on 2009-02-08
Thanks for the help!

---

