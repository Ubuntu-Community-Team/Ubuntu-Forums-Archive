---
title: "choppy videos"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by wlg on 2009-05-17
Choppy videos in Jaunty/Opera

---

### Post by mapes12 on 2009-05-17
What's your machines spec? In Terminal ```
sudo lshw
```Post the output. And did things work before any upgrading?

---

### Post by TeaSwigger on 2009-05-17
It's choppy for me too (I have an old low spec system). But honestly I don't bother with it since videos work fine in Firefox. I presume it has something to do with Adobe Flash and Opera on Linux but haven't looked into it. So I suggest viewing videos in Firefox if that's possible until Opera or Adobe, whomever the issue lies with, fixes it. Otherwise keep lookin' for a fix if there is one and good luck. :)

---

### Post by wlg on 2009-05-18
Mapes12:  Here is the output, it's quite a tome but here goes:
  ```
description: Space-saving Computer
    product: Dimension 2400
    vendor: Dell Computer Corporation
    serial: 4YSWL81
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=space-saving cpus=1 power-on_password=enabled uuid=44454C4C-5900-1053-8057-B4C04F4C3831
  *-core
       description: Motherboard
       product: 0F5949
       vendor: Dell Computer Corp.
       physical id: 0
       version: A01
       serial: ..CN7082158V600O.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A05 (12/02/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2400MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 128KiB
             capacity: 128KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns) [empty]
             physical id: 1
             slot: DIMM_2
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
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
             version: 01
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
             version: 01
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
             version: 01
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
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant Systems, Inc.
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 01
                serial: 00:14:22:65:e5:96
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=65.35.80.117 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
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
             product: 82801DB (ICH4) IDE Controller
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
           *-disk
                description: ATA Disk
                product: ST380011A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.16
                serial: 5JVS6SK6
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8f800200
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 19dda75d-7203-4cb7-a41a-6fd7af612e7a
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-05-05 12:49:06 filesystem=ext3 modified=2009-05-18 16:04:45 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-05-18 16:04:45 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1451MiB
                   capacity: 1451MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1451MiB
                      capabilities: nofs
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-RW  CRX217E
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1DS1
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:c4:2d:2b:7a:81
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
wlgoode@Albert:~$ 
```

  Just had a demi of 8 O 'Clock Italian Roast brewed in my mocha pot.  Quite nice, cheap too!   wlg

---

### Post by wlg on 2009-05-18
Forgot to tell you Mapes12:  Yeah on Intrepid I had the problen until I installed SMPlayer that seemed to fix it.  I've installed it in Jaunty, no luck.  wlg

---

### Post by wlg on 2009-05-18
TeaSwigger:  Thanks for the tip I'll try it.  FF is such a sluggy behemoth though. Opera is a lean fast Ocelot. Tried Midori w/ webkit, talk about fast!  Super light speed. Still unstable & has crash problems in Alpha though.  wlg

Hoist a cuppa Earl Grey to ya!

---

### Post by wlg on 2009-05-18
Teaswigger:  Yeah Man -choppy on FF also.

---

### Post by wlg on 2009-05-31
Still Choppy videos ever Since 9.04 upgrade).  Choppy in both Opera and FF.  Note: When using Intrepid I had the same problem.  Someone suggested installing mplayer and that seemed to fix it.  I tried the same in Jaunty (Installing mplayer and SM) no luck this time.

  My ongoing lament:  Made the switch from Windows about 2 yrs. ago with Dapper Drake.  I'm still a Noob's Newbie.  It seems like I'll never get to take off my water wings and swim with confidence through the great Linux ocean.

---

### Post by anchorschmidt on 2009-05-31
Try to do a complete installation of flash player with both browsers closed. It worked for me.

---

### Post by rsgangr on 2009-05-31
Choppy video could be related to the amount of video RAM. This can be increased by changing the amount of main memory available for video use.

During boot-up, press "Del" (or whatever key will take you into the BIOS settings) and select Advanced Chipset features / AGP Aperture Size. The default is usually 64 MB but this can be increased to 256 MB in most cases. More memory for video translates into smooth (or at least smoother) videos. The disadvantage is that less memory is available for other applications - this could be problematic if you do a lot of number-crunching.

Note: If you are not familiar with changes like this, consult your motherboard manual or get assistance from a technical person.

---

