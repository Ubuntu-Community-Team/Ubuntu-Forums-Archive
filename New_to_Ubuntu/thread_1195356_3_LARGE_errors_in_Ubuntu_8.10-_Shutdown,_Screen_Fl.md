---
title: "3 LARGE errors in Ubuntu 8.10- Shutdown, Screen Flicker, Random Desktops Flashing"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by BastardNamban on 2009-06-23
I am posting this for a friend, who needs some help. He doesn't have an account here yet.

3 Major problems with his 8.10 Intrepid install- 

1. His desktop is randomly changing every so many seconds, not regularly, between 2 backgrounds. The main one stays up, and flashes to the same other one for a couple seconds, then returns. I can't figure out why.

2. Most annoying- computer refuses to shut down! Going to shutdown supposedly shuts down the computer, no activity, but bumping the mouse restarts it. He can't shut it down without hitting the physical switch. I am not hitting hibernate by accident- this is for real.

3. Gave him Gstreamer XINE to watch DVDs finally, and it worked, but the same problem he had before keeps occuring- the media player output now reads the DVD, plays and all, but it keeps flickering to black fast, making the movie unwatchable, even though you can tell it is playing fine otherwise.

Ideas? We're headed out to dinner now, I'll check back in a few hours.

---

### Post by LewRockwell on 2009-06-23
> **BastardNamban said:**
> I am posting this for a friend, who needs some help. He doesn't have an account here yet.

3 Major problems with his 8.10 Intrepid install- 

1. His desktop is randomly changing every so many seconds, not regularly, between 2 backgrounds. The main one stays up, and flashes to the same other one for a couple seconds, then returns. I can't figure out why.

2. Most annoying- computer refuses to shut down! Going to shutdown supposedly shuts down the computer, no activity, but bumping the mouse restarts it. He can't shut it down without hitting the physical switch. I am not hitting hibernate by accident- this is for real.

3. Gave him Gstreamer XINE to watch DVDs finally, and it worked, but the same problem he had before keeps occuring- the media player output now reads the DVD, plays and all, but it keeps flickering to black fast, making the movie unwatchable, even though you can tell it is playing fine otherwise.

Ideas? We're headed out to dinner now, I'll check back in a few hours.

How did it operate in the live-run mode?

Did the memory fail or pass using the memtest function of the live-run?

also, please take note of my signature commentary found below.

as always, help up help you by including information we require to help us help you

---

### Post by BastardNamban on 2009-06-23
Forgive me, I try NOT to be a help vampire. But I myself am not extremely knowledgeable on ubuntu, as I'm self taught myself. 
> PRECISE and DETAILED account of difficulties! well, this is going to sound snarky any way I say it after posting that, but I'm sorry, can you give precise & detailed account of what exactly "live run mode" is, and what the memtest function is?

Before you shoot back at me, I admit to not knowing a lot. I can google these things endlessly, and get it maybe, or someone like you who seems to know could have explained it simply and what to do/how to access it for me, and helped teach me, to get a quicker answer, spared me endless googling for one helpful page. I still don't know what "live-run mode" is or what that has to do with all this. I'm sorry.

Specs: I was specific with Ubuntu (gnome interface 2.24.1) 8.10, Intrepid,
kernel 2.6.27-14. This is the sole OS installed, no windows, no dual boot.
My friend supposedly had a guru put all this on for him that I've never met, and from what I can tell, he put a lot of stuff on that my friend neither uses or knows of. And the movie thing flashing to black happened after the guru last touched this, he says. I'm thinking the supposed guru knows even less about what he's doing than I do, and I don't know much myself.

He has AWN installed as well as compiz settings manager (2 things that often seem to give issues to other people's computers, I noticed, which is why I mention them), and I've already tried running through the shutdown preferences and workarounds tab in compiz to see if I could find an things that might be causing these. I turned off legacy screen support in workarounds, still nothing.

The mouse that upon moving wakes up the shutdown computer is a Toshiba 3 button mouse, red light. From what I can tell, he's running a custom rig of some sort that looks old. I'm not even sure if he knows what he has. He left it all to his guru I never met.

Lastly, I looked for a hardware list and did this ```
sudo lshw
```.

Here's what I got (could it be a graphics card issue?)
```
 version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0401 (03/02/2007)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Socket 775
          size: 2394MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back instruction
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 40
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 18EHz
          capabilities: vmx ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: Radeon X1650 Pro
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: Radeon X1650 Pro (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: L1 Gigabit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: b0
                serial: 00:1a:92:e9:eb:36
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                logical name: scsi6
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
              *-cdrom
                   description: DVD-RAM writer
                   product: DVD RW DRU-830A
                   vendor: SONY
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   logical name: /media/cdrom0
                   version: SS25
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/cdrom
                      logical name: /media/cdrom0
                      configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@0000:05:03.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: WDC WD2500YS-01S
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 20.0
                serial: WD-WCANY3046979
                size: 233GiB (251GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e22ae22a
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 49f5bdfe-3c61-4d0d-a5f5-ddfc403158e0
                   size: 224GiB
                   capacity: 224GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-18 19:56:12 filesystem=ext3 modified=2009-06-23 17:28:02 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-06-23 17:10:57 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 21e30128-95cc-4510-8feb-ea5d6a57c638
                   size: 9530MiB
                   capacity: 9530MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-disk:1
                description: ATA Disk
                product: WDC WD2500YS-01S
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 20.0
                serial: WD-WCANY3061064
                size: 233GiB (251GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=96a196a1
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /home
                   version: 1.0
                   serial: a6e5757c-7ef3-41d4-be44-b2efc2fb41f8
                   size: 233GiB
                   capacity: 233GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-05 18:42:54 filesystem=ext3 modified=2009-06-23 19:06:44 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2009-06-23 19:06:44 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
     *-scsi
          physical id: 2
          bus info: usb@7:5
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@8:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: MS/MSPRO
             vendor: USB2.0
             physical id: 0.0.3
             bus info: scsi@8:0.0.3
             logical name: /dev/sdf
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:89:77:f0:53:d9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0401 (03/02/2007)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Socket 775
          size: 2394MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back instruction
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 40
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 18EHz
          capabilities: vmx ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: Radeon X1650 Pro
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: Radeon X1650 Pro (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: L1 Gigabit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: b0
                serial: 00:1a:92:e9:eb:36
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                logical name: scsi6
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
              *-cdrom
                   description: DVD-RAM writer
                   product: DVD RW DRU-830A
                   vendor: SONY
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   logical name: /media/cdrom0
                   version: SS25
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/cdrom
                      logical name: /media/cdrom0
                      configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@0000:05:03.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: WDC WD2500YS-01S
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 20.0
                serial: WD-WCANY3046979
                size: 233GiB (251GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e22ae22a
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 49f5bdfe-3c61-4d0d-a5f5-ddfc403158e0
                   size: 224GiB
                   capacity: 224GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-18 19:56:12 filesystem=ext3 modified=2009-06-23 17:28:02 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-06-23 17:10:57 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 21e30128-95cc-4510-8feb-ea5d6a57c638
                   size: 9530MiB
                   capacity: 9530MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-disk:1
                description: ATA Disk
                product: WDC WD2500YS-01S
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 20.0
                serial: WD-WCANY3061064
                size: 233GiB (251GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=96a196a1
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /home
                   version: 1.0
                   serial: a6e5757c-7ef3-41d4-be44-b2efc2fb41f8
                   size: 233GiB
                   capacity: 233GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-05 18:42:54 filesystem=ext3 modified=2009-06-23 19:06:44 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2009-06-23 19:06:44 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
     *-scsi
          physical id: 2
          bus info: usb@7:5
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@8:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: MS/MSPRO
             vendor: USB2.0
             physical id: 0.0.3
             bus info: scsi@8:0.0.3
             logical name: /dev/sdf
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:89:77:f0:53:d9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0401 (03/02/2007)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Socket 775
          size: 2394MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back instruction
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 40
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 18EHz
          capabilities: vmx ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: Radeon X1650 Pro
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: Radeon X1650 Pro (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: L1 Gigabit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: b0
                serial: 00:1a:92:e9:eb:36
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                logical name: scsi6
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
              *-cdrom
                   description: DVD-RAM writer
                   product: DVD RW DRU-830A
                   vendor: SONY
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   logical name: /media/cdrom0
                   version: SS25
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/cdrom
                      logical name: /media/cdrom0
                      configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@0000:05:03.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: WDC WD2500YS-01S
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 20.0
                serial: WD-WCANY3046979
                size: 233GiB (251GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e22ae22a
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 49f5bdfe-3c61-4d0d-a5f5-ddfc403158e0
                   size: 224GiB
                   capacity: 224GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-18 19:56:12 filesystem=ext3 modified=2009-06-23 17:28:02 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-06-23 17:10:57 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 21e30128-95cc-4510-8feb-ea5d6a57c638
                   size: 9530MiB
                   capacity: 9530MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-disk:1
                description: ATA Disk
                product: WDC WD2500YS-01S
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 20.0
                serial: WD-WCANY3061064
                size: 233GiB (251GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=96a196a1
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /home
                   version: 1.0
                   serial: a6e5757c-7ef3-41d4-be44-b2efc2fb41f8
                   size: 233GiB
                   capacity: 233GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-05 18:42:54 filesystem=ext3 modified=2009-06-23 19:06:44 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2009-06-23 19:06:44 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
     *-scsi
          physical id: 2
          bus info: usb@7:5
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@8:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: MS/MSPRO
             vendor: USB2.0
             physical id: 0.0.3
             bus info: scsi@8:0.0.3
             logical name: /dev/sdf
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:89:77:f0:53:d9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

And yes I realize that's cut off- I don't know how to get the top part, the terminal erases it before I can see it since the thing is all so long. Sorry.

I know this is probably not enough to diagnose, but I don't know where to start or what else you need to know. Honestly, I'm thinking of wiping his computer and just reinstalling 8.04 and building it for him personally, as I understand that, I feel.

Does anything here help?

---

### Post by LewRockwell on 2009-06-23
A for effort!

The Ubuntu disk should be a live-run CD AND it will also have memtest on it as well as the installer.

Put the disk in the machine and have the machine boot from the disk

you should see a screen with some different selections

one of the selections will be to "try ubuntu without changing anything"

that is your live-run so please select "try ubuntu" and allow the system to load

now experiment to see how a "straight ubuntu install" would work

---

### Post by LewRockwell on 2009-06-23
[http://ubuntuforums.org/showthread.php?t=611492](http://ubuntuforums.org/showthread.php?t=611492)


getting a fresh 9.04 disk and using it may well correct your issues without having to attempt the "fix" above

---

### Post by LewRockwell on 2009-06-23
here I found a decent report on using 9.04 with your video card


[http://groups.google.com/group/comp.os.linux.x/browse_thread/thread/d74c0aab5f370c73](http://groups.google.com/group/comp.os.linux.x/browse_thread/thread/d74c0aab5f370c73)

---

### Post by BastardNamban on 2009-06-23
Ok, thanks for the feedback. Unfortunately for now, I have to get home- I am visiting my friend's place today, and he lives far away from me. I don't have time now to try any of this- today. I'll have to come back sometime next week or something.

It looks like this could be an issue with his graphics card then?

I don't have a live disk here, he doesn't either. I'll have to burn one when I get home. He's using Intrepid, but would this issue be fixed on a newer release if I installed one (ie: Jaunty)?

---

### Post by 3rdalbum on 2009-06-23
Turn off desktop effects when you want to play video. ATI's driver has the flickering problem when you have desktop effects AND you play video or use an OpenGL program at the same time.

ATI doesn't seem to want to fix the problem :-(  Get an Nvidia card if possible as it doesn't have this issue.

---

### Post by BastardNamban on 2009-06-26
Ah- That's a big 10-4 on that. I'm not at his place, but I don't remember him having desktop effects enabled- I think I came across that. I'll relay it to him though.

Honestly, we can apologize for people who code anyday, saying it's hard, the problem was just found, etc.,  but if this has been a known problem for some time and they don't care to fix it, that's atrocious. I see why Nvidia is so prevalent now under linux.

---

### Post by jocko on 2009-06-26
> **BastardNamban said:**
> 1. His desktop is randomly changing every so many seconds, not regularly, between 2 backgrounds. The main one stays up, and flashes to the same other one for a couple seconds, then returns. I can't figure out why.
That could be wallpaper-tray. Open up synaptic, search for wallpaper-tray. If it's installed, uninstall it and that problem should be solved.

---

