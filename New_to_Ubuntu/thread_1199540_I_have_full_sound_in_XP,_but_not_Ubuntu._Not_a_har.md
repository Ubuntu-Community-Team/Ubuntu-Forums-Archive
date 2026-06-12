---
title: "I have full sound in XP, but not Ubuntu. Not a hardware issue."
date: 2009-06-29
forum: New to Ubuntu
---

### Post by danny_galaga on 2009-06-29
So, I've been using Ubuntu on this computer since 8.04 and only had a few minor issues. This computer is dual boot with XP and currently 9.04 . A few days ago i lost sound. The only thing unusual that happened before that, that i can think of is that i was using a flakey USB memory stick (one of those crappy Toshiba U3 sticks. I had tried to remove the stupid U3 thingo without success. The stick is now in the bin :) ).

I have tried an earlier kernel from the boot up menu as suggested in another thread, but without success. I can boot into XP and there are no sound issues, so this is definitely NOT a hardware problem. Is there something i can type in the terminal to help diagnose what the problem is?

---

### Post by binbash on 2009-06-29
paste the output of lspci and sudo lshw

---

### Post by danny_galaga on 2009-06-29
danny@danny-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
03:0c.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by danny_galaga on 2009-06-29
danny@danny-desktop:~$ lshw -c sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: c
       bus info: pci@0000:03:0c.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=cx8800 latency=165 maxlatency=55 mingnt=20 module=cx8800
  *-multimedia
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

danny@danny-desktop:~$ 
danny@danny-desktop:~$ clear

danny@danny-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
03:0c.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
danny@danny-desktop:~$ clear

danny@danny-desktop:~$ sudo lshw
[sudo] password for danny: 
danny-desktop             
    description: Computer
    product: DN035A-ABG a320a
    vendor: HP Pavilion 061
    version: 01N0211RE101GLEND10
    serial: CNC344009P AN300
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=E0ADAC9B-CE08-D811-86F2-92D72947A9DF
  *-core
       description: Motherboard
       product: Glendale motherboard
       vendor: TriGem Computer Inc.
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          physical id: 0
          version: 3.24 (10/14/2003)
          size: 108KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: WMT478/NWD
          size: 2600MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 8KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst internal write-back
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: J5G3
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             physical id: 1
             slot: J5G2
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
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
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
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
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
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
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:40:2b:72:7f:63
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.5 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-pci
                description: PCI bridge
                product: HB6 Universal PCI-PCI bridge (non-transparent mode)
                vendor: Hint Corp
                physical id: a
                bus info: pci@0000:02:0a.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm hotswap bus_master cap_list
              *-multimedia
                   description: Multimedia video controller
                   product: CX23880/1/2/3 PCI Video and Audio Decoder
                   vendor: Conexant Systems, Inc.
                   physical id: c
                   bus info: pci@0000:03:0c.0
                   version: 05
                   width: 32 bits
                   clock: 33MHz
                   capabilities: vpd pm bus_master cap_list
                   configuration: driver=cx8800 latency=165 maxlatency=55 mingnt=20 module=cx8800
              *-firewire
                   description: FireWire (IEEE 1394)
                   product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                   vendor: Texas Instruments
                   physical id: d
                   bus info: pci@0000:03:0d.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk:0
                description: ATA Disk
                product: WDC WD400EB-00CP
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 06.0
                serial: WD-WMAATF499984
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a2ae67c7
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 6055084c-2542-4a48-b875-086553293c4f
                   size: 24GiB
                   capacity: 24GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2004-07-04 05:32:06 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 11GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 580MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST3160815A
                vendor: Seagate
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 9RA51NXE
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9c6d8e01
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: e08b09ac-f81b-b04d-aeb0-35b4df12e74e
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-04-12 18:05:26 filesystem=ntfs label=New Volume state=clean
           *-cdrom:0
                description: CD-R/CD-RW writer
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw
                configuration: status=nodisc
           *-cdrom:1
                description: DVD writer
                product: DVD-RW  DVR-109
                vendor: PIONEER
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.09
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ba:4f:a8:87:e0:51
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by danny_galaga on 2009-06-29
](*,)

the answer is in this thread!

[http://ubuntuforums.org/showthread.php?t=1198985](http://ubuntuforums.org/showthread.php?t=1198985)

i had checked the master volume thingo, but hadnt looked at all the other sliders in 'volume control'. I fiddled with a few and turning on the PCM (whatever that is) did the trick! god knows how it got turned off in the first place!

Thanks for the replies though (",)

edit: hmmm, how do i change the title to 'solved'?

---

### Post by ginestre on 2009-06-29
> **danny_galaga said:**
> ](*,)

edit: hmmm, how do i change the title to 'solved'?

click on 'thread tools' at the top of the thread list, on the right

---

