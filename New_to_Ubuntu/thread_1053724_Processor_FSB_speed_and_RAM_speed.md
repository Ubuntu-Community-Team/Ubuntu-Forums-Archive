---
title: "Processor FSB speed and RAM speed"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by CoreyB. on 2009-01-28
I have a Dell Inspiron 1525 laptop with a T7250 Intel Core 2 Duo processer with a 800 MHz FSB.  The RAM that shipped with it was 3 GB @ 667 MHz.  Down the road, if I upgrade to 4 GB of RAM and buy ones that run @ 800 MHz, will my computer be able to run the RAM at 800 MHz or will it stay at 667 MHz?  Is there an easy way to tell the top speed of RAM that will run on a given system?  What effects that limit?

Thanks to anyone who can help me out! :)

---

### Post by Ng Oon-Ee on 2009-01-28
Hmm, a laptop. If it was a desktop you could just look at the m-board specs, and I'm sure you still can on a laptop, just not sure whether its easy to tell what motherboard you're using.

And the limitation is a motherboard limitation, AFAIK.

---

### Post by kavon89 on 2009-01-29
What northbridge chip does your system's board have? You could find what maximum speed it can handle.

To get some system information (with the sanitize flag to remove serial numbers before posting it here):

```
sudo lshw -sanitize
```

---

### Post by CoreyB. on 2009-01-29
> **kavon89 said:**
> What northbridge chip does your system's board have? You could find what maximum speed it can handle.

To get some system information (with the sanitize flag to remove serial numbers before posting it here):

```
sudo lshw -sanitize
```

I ran the above code, here is what was spit out. (Thanks for the -sanitize flag, I wouldn't have thought anything of it.)

computer                  
    description: Portable Computer
    product: Inspiron 1525
    vendor: Dell Inc.
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-3700-1038-8036-CAC04F584731
  *-core
       description: Motherboard
       product: 0U990C
       vendor: Dell Inc.
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A16 (10/16/2008)
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.13
          serial: [REMOVED]
          slot: Microprocessor
          size: 2001MHz
          capacity: 2001MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
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
          physical id: 1000
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: HYMP125S64CP8-Y5
             vendor: AD00000000000000
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: NT1GT64UH8C0FN-3C
             vendor: 7F7F7F0B00000000
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
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
        *-pci:0
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
           *-network
                description: Ethernet interface
                product: 88E8040 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 12
                serial: [REMOVED]
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: wmaster0
                version: 61
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=[REMOVED] latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-pci:2
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
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 9
                bus info: pci@0000:02:09.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:02:09.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:02:09.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ricoh-mmc latency=64 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 9.3
                bus info: pci@0000:02:09.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 9.4
                bus info: pci@0000:02:09.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD writer
                product: DVD+-RW DS-8W1P
                vendor: PBDS
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BD1C
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVS-7
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: [REMOVED]
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d0000000
              *-volume:0
                   description: Windows FAT volume
                   vendor: Dell 8.0
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT16
                   serial: [REMOVED]
                   size: 70MiB
                   capacity: 70MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: [REMOVED]
                   size: 10231MiB
                   capacity: 10239MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-10-24 22:15:51 filesystem=ntfs label=Recovery state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /media/OS
                   version: 3.1
                   serial: [REMOVED]
                   size: 180GiB
                   capacity: 180GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-07-27 18:26:31 filesystem=ntfs label=OS mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 42GiB
                   capacity: 42GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2559MiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 34GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 5851MiB
                      capabilities: nofs
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
  *-battery
       product: DELL WK37987
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 78000mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by kavon89 on 2009-01-29
Here is what I found on the north bridge chip (one that is in the same family or pretty much the same thing) from Intel's site:

> Supports DDR2 667 and 533Mhz

Source: [http://www.intel.com/Assets/PDF/datasheet/316273.pdf](http://www.intel.com/Assets/PDF/datasheet/316273.pdf)

---

### Post by -kg- on 2009-01-29
Also I think (it at least used to be) that, if you mix RAM with different speeds, it defaults to the lower speed, if the RAM is compatible with each other at all.

I might be wrong on this, especially now that technology has whizzed by me.

Also, if the specs that kavon89 gave are correct for your machine, the max it will support is 667, so if the new RAM will work in your machine, it will be limited to that just due to the limitations of the MOBO alone.

---

### Post by mc4man on 2009-01-29
I'd be careful if you buy non dell memory, make sure it's compatible. Dell's bios is extremely restricted, you won't be able to adjust the memory timing's ect.

You could also just replace the 1 Gb stick with a 2 Gb one from dell.

If you just purchased recently you could try to get a reduced price from dell. It's a little tricky, but did work here last year with a m1300.
Dell misrepresents the 3 Gb as 'dual channel'. While the memory is dual channel capable it's not possible to run in dual channel mode in the 3 Gb configuration.
While it's noted as such in small print elsewhere on the site it's never stated on the order page. I got offered $75.00 off of the price of a 2Gb stick or a 50.00 credit (I took the credit, ( you need to deal with customer service and be nice, being within the 30 day return is also a factor

---

### Post by CoreyB. on 2009-01-29
[QUOTE=kavon89;6638949]Here is what I found on the north bridge chip (one that is in the same family or pretty much the same thing) from Intel's site:
QUOTE]

Yeah, thanks kavon, I ran PC Wizard 2008 on my Vista partition and under "NorthBridge" it says "Intel GM965" so the pdf you linked must by my chipset.

-kg-, I am aware that if I put mixed speeds in my computer, that it will run to the lower speed.  I was duped into buying a faster speed for my old Dell Dimension 2400 desktop because I was told that my computer would take advantage of the DDR 400 speed by the chat support at crucial.com.  My computer came with DDR 333 so I took it out and replaced it with DDR 400, but it turns out my computer could only run at DDR 333.

mc4man, I buy my RAM from Crucial.  I've never purchased RAM anywhere else and all for Dell computers.  Does anyone on these forums not like Crucial?  I don't know how it stacks up against other companies.

---

