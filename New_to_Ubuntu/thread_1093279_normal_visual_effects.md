---
title: "normal visual effects"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by ppillow on 2009-03-11
hi i was wondering how to get this working it just says Desktop effects could not be enabled can anyone help?

---

### Post by skymera on 2009-03-11
What is your graphics card? :)

---

### Post by ppillow on 2009-03-11
not sure how can i find out?

---

### Post by skymera on 2009-03-11
Hmm, run 

```
 sudo lshw 
``` and post that

Please use the [code] options in "Reply Post" to post, makes it easier to read.

---

### Post by ubudog on 2009-03-11
It should say somewhere on your computer, but if not open a terminal:Applications>Accessories>Terminal and type lspci | grep VGA.  I think that may show your graphics card.  Reply with the results.

---

### Post by ppillow on 2009-03-11
```
    description: Mini Tower Computer
    product: Compaq PC
    vendor: Compaq
    version: N/A
    serial: 3D09FPN7W4M0
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=mini-tower uuid=32313039-3031-3131-3230-343441413232
  *-core
       description: Motherboard
       product: 06E4h
       vendor: Compaq
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 0
          version: 786K1 (07/26/2001)
          size: 64KiB
          capacity: 192KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.4.2
          slot: U12A
          size: 900MHz
          capacity: 1100MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 5
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 512MiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM DRAM Synchronous 133 MHz (7.5 ns)
             physical id: 0
             slot: DIMM1
             size: 128MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 1
             slot: DIMM2
             size: 256MiB
             width: 64 bits
             clock: 100MHz (10.0ns)
        *-bank:2
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 2
             slot: DIMM3
             size: 128MiB
             width: 64 bits
             clock: 100MHz (10.0ns)
     *-pci
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via module=via_agp
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV6 [Vanta/Vanta LT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 15
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
        *-multimedia
             description: Multimedia audio controller
             product: 5880B [AudioPCI]
             vendor: Ensoniq
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ENS1371 latency=64 maxlatency=128 mingnt=12 module=snd_ens1371
        *-network:0
             description: Ethernet interface
             product: RTL8139 Ethernet
             vendor: D-Link System Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 10
             serial: 00:40:05:82:c5:1f
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=66 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
        *-network:1
             description: Ethernet interface
             product: SMC2-1211TX
             vendor: Accton Technology Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: eth1
             version: 10
             serial: 00:10:b5:95:ab:43
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.105 latency=66 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             logical name: scsi1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64 module=pata_via
           *-disk:0
                description: ATA Disk
                product: QUANTUM FIREBALL
                vendor: Quantum
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: A01.
                serial: 614024642059
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000675f
              *-volume
                   description: Linux filesystem partition
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 8d32d8e7-f374-4d0b-8342-8a73c7e25ec2
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable large_files huge_files recover ext2 initialized
                   configuration: filesystem=ext2 modified=2009-03-11 08:50:56 mount.fstype=ext2 mount.options=ro,errors=remount-ro mounted=2009-03-11 07:15:02 state=mounted
           *-disk:1
                description: ATA Disk
                product: WDC AC34300L
                vendor: Western Digital
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 21.1
                serial: WD-WT4732686072
                size: 4104MiB (4304MB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ed99ed99
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/disk
                   version: 1.0
                   serial: 4fed6eb0-50e4-4cad-94b4-825fecdf30c8
                   size: 3867MiB
                   capacity: 3867MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-03-10 16:18:08 filesystem=ext3 modified=2009-03-11 07:47:29 mount.fstype=ext3 mount.options=rw,nosuid,nodev,errors=continue,data=ordered mounted=2009-03-11 07:47:29 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 235MiB
                   capacity: 235MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 235MiB
                      capabilities: nofs
           *-cdrom:0
                description: CD-R/CD-RW writer
                product: CD-RW  CRX140E
                vendor: SONY
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.0n
                serial: [SONY    CD-RW  CRX140E  1.0n Feb21 ,2000
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: SCSI CD-ROM
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio
                configuration: status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=66 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=66 module=uhci_hcd
        *-bridge
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: driver=vt596_smbus latency=0 module=i2c_viapro
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:f6:d2:17:84:78
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by ubudog on 2009-03-11
Ahh.  Sorry wrong code.  Do this glxinfo in the terminal and paste the results in a reply.  Your graphics card info should be at the top.

---

### Post by ppillow on 2009-03-11
desktop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

---

### Post by ubudog on 2009-03-11
Mmm. It worked on my computer.

---

### Post by avtolle on 2009-03-11
Looks like a nvidia card from the lshw output. Are there any drivers to activate shown in  System>Administration>Hardware Drivers?

---

### Post by Therion on 2009-03-11
Whoops... Wrong thread.

---

### Post by ubudog on 2009-03-11
Yeah thats how I enabled mine.  There should be one there.

---

### Post by ppillow on 2009-03-11
nothings there

---

### Post by kanikilu on 2009-03-11
Looks like several people with your same display adapter did not have much luck...

[http://ubuntuforums.org/showthread.php?t=1067192](http://ubuntuforums.org/showthread.php?t=1067192)
[http://ubuntuforums.org/showthread.php?t=1052046](http://ubuntuforums.org/showthread.php?t=1052046)

Sorry, I know that's not much help.

---

### Post by ubudog on 2009-03-11
Sorry, the Desktop Effects probably won't work on your computer.

---

### Post by ppillow on 2009-03-11
do you guys know if theres a way to update my graphics card??

---

### Post by avtolle on 2009-03-11
> **ppillow said:**
> do you guys know if theres a way to update my graphics card??
If your question is directed towards updating the current card without purchasing and installing a replacement, no, I don't.

---

### Post by ppillow on 2009-03-11
yes that is

---

### Post by ubudog on 2009-03-11
You'd probably have to go buy a new one like nvida or something and install it in your computer.  I don't think that graphics card is supported by ubuntu at this time.

---

