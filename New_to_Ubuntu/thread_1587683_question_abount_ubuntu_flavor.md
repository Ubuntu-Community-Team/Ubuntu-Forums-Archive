---
title: "question abount ubuntu flavor??"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by owners4life5 on 2010-10-04
this can be very much so defined as a 'noob question'...

but i have ubuntu installed, of course, but the graphics card is awful, there seems to be nothing i can do about it..

but from what i remember, there is a flavor of ubuntu made especially for computers with bad graphics, if i.m correct, right?

what is this, again??

thanks,

---

### Post by mikewhatever on 2010-10-04
No, there isn't. Unfortunately, some graphics cards are a PITA, thanks Intel.

---

### Post by owners4life5 on 2010-10-04
> **mikewhatever said:**
> No, there isn't. Unfortunately, some graphics cards are a PITA, thanks Intel.

even worse, my friend. the dreaded group if three letters. yep, you guessed it.

S.I.S.

yeah. that.s it. even worse than intel.

---

### Post by mastablasta on 2010-10-04
> **owners4life5 said:**
> S.I.S.
 
 
IMO they don't have much to show even in other OS.

---

### Post by robert shearer on 2010-10-04
this link may be of use....
[http://ubuntuforums.org/showthread.php?t=1526038](http://ubuntuforums.org/showthread.php?t=1526038)

---

### Post by owners4life5 on 2010-10-06
> **robert shearer said:**
> this link may be of use....
[http://ubuntuforums.org/showthread.php?t=1526038](http://ubuntuforums.org/showthread.php?t=1526038)

it actually seemed to be...at first i had trouble going to the website inside of the post...but then i eventually got it..and read into it.

i got the driver installed and re-booted, the graphics are the same, actually...just not 'glitchy', i guess.

i still can.t enable compiz, wobbly windows, etc. though.

oh well.

_________________________________________________________________
oh, another thing is that i figured out what i was talking about: "xubuntu". but it.s for computers that are 'slow' in general. not the horrible graphics.

---

### Post by robert shearer on 2010-10-06
> i got the driver installed and re-booted, the graphics are the same, actually...just not '**glitchy**', i guess.

Hey, an improvement is still an improvement.

I suspect that that is as much performance as you will get from SIS graphics. Their cards are notoriously badly supported as they have no official support for Linux.

Many of us who **can** run Compiz, Wobblies, et al turn them off anyway and enjoy the  performance bonus and lack of distractions. :)

If you want to improve your graphics further you will need to upgrade/replace the graphics card.

If you open a terminal and enter..
```
sudo lshw
```

and paste the output here then you can get some advice as to what would work with your hardware.

(lshw=List hardware)

---

### Post by owners4life5 on 2010-11-14
```
brian@brian-desktop:~$ sudo lshw
[sudo] password for brian: 
brian-desktop             
    description: Desktop Computer
    product: 00000000
    vendor: SiS
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       physical id: 0
       version: 1.0
       serial: 00000000
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (07/16/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DDR Synchronous 200 MHz (5.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 200MHz (5.0ns)
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci:0
          description: Host bridge
          product: 761/M761 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
          resources: memory:f0000000-f3ffffff
        *-pci:0
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:e000(size=4096) memory:feb00000-febfffff memory:d8000000-dfffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:d8000000-dfffffff(prefetchable) memory:febe0000-febfffff ioport:e800(size=128)
        *-isa
             description: ISA bridge
             product: SiS965 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 48
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD800EB-00DJ
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 77.0
                serial: WD-WCAHL2774400
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ebebf
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 41397e85-327f-4e99-a097-73c1047aa8f4
                   size: 38GiB
                   capacity: 38GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-05-26 18:20:35 filesystem=ext4 lastmountpoint=/&#65533;k&#65533;&#65533;&#65533;&#65533;&#1776;&#65533;z&#1856;&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;l!&#65533;&#65533;&#65533;z&#65533;@&#65533;&#65533; &#65533;f&#65533; &#65533;f&#1861;&#65533;&#65533;A&#65533;h&#65533;&#65533;yo!&#65533;&#65533;d modified=2010-11-13 17:33:02 mounted=2010-11-14 16:15:36 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1361MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 17GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 813MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: 87e76d77-53a6-4b00-a75a-78f6ababa007
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-11-13 23:24:19 filesystem=ext4 modified=2010-11-13 17:32:25 state=clean
           *-cdrom
                description: DVD reader
                product: COMBO LTC-48161H
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KTH2
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52
             resources: irq:18 ioport:d800(size=256) ioport:d400(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:feaff000-feafffff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:feafe000-feafefff
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:22 memory:feafd000-feafdfff
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:23 memory:feafc000-feafcfff
        *-network
             description: Ethernet interface
             product: 190 Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 00
             serial: 00:1b:b9:95:79:70
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.3 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
             resources: irq:19 memory:feafbc00-feafbc7f ioport:d000(size=128)
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-ide:1
             description: IDE interface
             product: Silicon Integrated Systems [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_sis latency=64
             resources: irq:17 ioport:c800(size=8) ioport:c400(size=4) ioport:c000(size=8) ioport:b800(size=4) ioport:b400(size=16)
        *-communication
             description: Modem
             product: SmartLink SmartPCI561 56K Modem
             vendor: ALi Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=serial latency=64
             resources: irq:18 memory:feafa000-feafafff ioport:a800(size=256)
        *-pci:3
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm bus_master cap_list
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          bus info: usb@1:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: iPod
             vendor: Apple
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.62
             serial: 5K94009V3QS2
             size: 7601MiB (7971MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 7601MiB (7971MB)
                configuration: signature=00069865
     *-scsi:1
          physical id: 2
          bus info: usb@1:6
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Gigaware
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
             version: 8.02
             serial: u
             size: 7663MiB (8036MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
                size: 7663MiB (8036MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=000e6aae
              *-volume
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 1
                   logical name: /dev/sdc1
                   logical name: /media/26CC-DDF2
                   version: FAT32
                   serial: 26cc-ddf2
                   size: 7657MiB
                   capacity: 7657MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:a4:85:fc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.254.4 multicast=yes wireless=IEEE 802.11bg
brian@brian-desktop:~$ 

```

---

