---
title: "Glitchy text"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Pseudonym1911 on 2011-07-08
[FONT=Verdana]I just downloaded Ubuntu today and when I boot my computer it will look fine but after a while certain text starts to look like this:[/FONT]

[ATTACH]196960[/ATTACH]

[FONT=Verdana]Can anyone tell me what is wrong or how to fix it? Thanks.[/FONT]

---

### Post by wildmanne39 on 2011-07-08
> **Pseudonym1911 said:**
> [FONT=Verdana]I just downloaded Ubuntu today and when I boot my computer it will look fine but after a while certain text starts to look like this:[/FONT]

[ATTACH]196960[/ATTACH]

[FONT=Verdana]Can anyone tell me what is wrong or how to fix it? Thanks.[/FONT]Hi, run these commands in a terminal
```
sudo lshw
```
```
lspci | grep VGA
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Pseudonym1911 on 2011-07-08
[COLOR=Red]First one:[/COLOR]
 
description: Low Profile Desktop Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=low-profile cpus=1 family=103C_53307F sku=EN448UC#ABA uuid=9E7D45CC-C68D-DA11-BBDA-350F7C2E0016
  *-core
       description: Motherboard
       product: 09F8h
       vendor: Hewlett-Packard
       physical id: 0
       serial: 2UA60402CR
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786D1 v01.03
          date: 05/18/2005
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          slot: XU1 PROCESSOR
          size: 2800MHz
          width: 64 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 7
             slot: Internal L1 Cache
             size: 28KiB
             capacity: 28KiB
             capabilities: burst internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 8
             slot: Cache L2
             size: 1MiB
             capacity: 4MiB
             capabilities: burst internal write-back data
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
     *-cpu:1 DISABLED
          description: CPU [empty]
          vendor: Intel
          physical id: 6
          slot: XU1 PROCESSOR 2
     *-memory:0
          description: System Memory
          physical id: 36
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 64T32000HU3.7A
             vendor: JEDEC ID:C1 00 00 00 00 00 00 00
             physical id: 0
             serial: 10BA0903
             slot: XMM1
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR2 Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 1
             slot: XMM2
        *-bank:2
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 64T32000HU3.7A
             vendor: JEDEC ID:C1 00 00 00 00 00 00 00
             physical id: 2
             serial: 10BB0903
             slot: XMM3
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR2 Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 3
             slot: XMM4
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 37
          slot: System board or motherboard
          capacity: 1MiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 1MiB
             width: 2 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0400000-e047ffff ioport:10c0(size=8) memory:d0000000-dfffffff memory:e0480000-e04bffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:e04c0000-e04c3fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:20000000-201fffff ioport:20200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:e0500000-e07fffff ioport:20400000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:3f:00.0
                logical name: eth0
                version: 01
                serial: 00:16:35:0f:7c:2e
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5752-v3.10 ip=192.168.15.93 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:42 memory:e0500000-e050ffff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1000(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1020(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:1060(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:e04c4000-e04c43ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:10a0(size=16)
           *-cdrom
                description: DVD reader
                product: DVD-ROM GDR8164B
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0B07
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:10d8(size=8) ioport:10f0(size=4) ioport:10e0(size=8) ioport:10f4(size=4) ioport:10b0(size=16)
           *-disk
                description: ATA Disk
                product: Maxtor 6N040T0
                vendor: Maxtor
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: NAN5
                serial: N10GC7ZG
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000c0364
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 6536229b-9cc1-42af-ba26-2630af946717
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-07 19:24:15 filesystem=ext4 lastmountpoint=/ modified=2011-07-07 19:35:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-07-08 07:42:15 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 502MiB
                   capacity: 502MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 502MiB
                      capabilities: nofs
[COLOR=Red]Second one:[/COLOR]

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

---

### Post by OldBoy44 on 2011-07-08
Maybe I don't know what I am talking about but have you checked that your computer is combatible with Unity ?

In terminal run -

/usr/lib/nux/unity_support_test -p

---

### Post by Pseudonym1911 on 2011-07-08
You probably know more than me. I ran it and it said it is compatible.

---

### Post by OldBoy44 on 2011-07-08
Certainly not necessarily - I'm sure others can answer your question - :)

---

### Post by Pseudonym1911 on 2011-07-08
Thank you for trying though.

---

### Post by wildmanne39 on 2011-07-08
> **Pseudonym1911 said:**
> Thank you for trying though.Hi, from what I see you only have 512 mb of ram and your processor is a penthium 4, so that is going to make you system sluggish.Aslo you you one partition that is 5oo mb in size I am not sure what that is, did you create a separate boot partition? There are two things you can try because unity is a little heavy to run on your system.

1. [http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
2. log out click on your username and go to the bottom of the screen and choose ubuntu classic with no effects and see if that helps.

---

### Post by Pseudonym1911 on 2011-07-14
The partition is of windows xp. I was trying to dualboot ubuntu and Windows xp but I decided to just run ubuntu until I can upgrade my RAM. I haven't used it so I'm not sure if it still does this. Thanks for all the help.

---

### Post by wildmanne39 on 2011-07-14
> **Pseudonym1911 said:**
> The partition is of windows xp. I was trying to dualboot ubuntu and Windows xp but I decided to just run ubuntu until I can upgrade my RAM. I haven't used it so I'm not sure if it still does this. Thanks for all the help.
Hi, your welcome!

---

