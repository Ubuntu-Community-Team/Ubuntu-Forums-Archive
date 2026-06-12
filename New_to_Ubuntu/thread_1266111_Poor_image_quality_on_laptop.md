---
title: "Poor image quality on laptop"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by guru_ian on 2009-09-14
Hi,

I am new to all this but have been finding my way since I installed Ubuntu a couple of weeks ago; however, I have one remaining problem that I am unable to solve.

I have installed onto my laptop a HP G60 which has native image ratio of 16:9 1360x768, when I set the resolution to 1360x768 the image is very poor and grainy, instead I am using 1024x768 for a crystal display but black strips on either side of the screen.

Here is the information about my system:

   description: Notebook
    product: HP G60 Notebook PC
    vendor: Hewlett-Packard
    version: F.36
    serial: 2CE84206SK
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=78563412-3412-7856-90AB-CDDEEFAABBCC
  *-core
       description: Motherboard
       product: 3612
       vendor: Wistron
       physical id: 0
       version: 09.51
       serial: 2CE84206SK
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.36 (03/12/2009)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: JM667QSU-2G
             vendor: Transcend
             physical id: 0
             serial: 00037496
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: HYMP112S64CP6-Y5
             vendor: AD00000000000000
             physical id: 1
             serial: 00002291
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1c
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU
          size: 1GHz
          capacity: 2GHz
          width: 64 bits
          clock: 667MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: 1d
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 1f
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 1e
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:1f:16:46:cb:d8
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:23:4d:61:ef:d9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.65 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVT-6
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 13.0
                serial: WD-WXE908T73294
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cc50cc50
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9746eb8c-694d-438b-b45a-4d59f57084bf
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-09-10 16:39:00 filesystem=ext3 modified=2009-09-14 11:20:03 mount.fstype=ext3 mount.options=rw,errors=continue,data=ordered mounted=2009-09-14 09:42:42 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/documents
                   version: 3.1
                   serial: 03f54686-a068-4d9a-94f9-cc08a92070d9
                   size: 214GiB
                   capacity: 214GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-09-13 21:32:16 filesystem=ntfs label=documents mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7581S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 4H02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 82801I (ICH9 Family) Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:82:1c:1a:04:81
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Any advice gratefully received, many thanks in advance.

---

### Post by dream_coder on 2009-09-14
is there a restriced graphics driver available for your graphics card? if there is it may be worth while installing it.

[https://help.ubuntu.com/8.04/hardware/C/restricted-manager.html](https://help.ubuntu.com/8.04/hardware/C/restricted-manager.html)

---

### Post by realzippy on 2009-09-14
Do you use ubuntu 9.04?
There have been several issues with intel graphiccards on 9.04,E.G.:

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)




Maybe the best solution would be downgrading to 8.10.

---

### Post by guru_ian on 2009-09-15
Hi,

Thanks for the reply.

I have followed the trail from the first link and found that solutions offered seem to rely on the Hardware Drivers or Proprietary Drivers sub-menus of the Administation menu. Unfortunately my set up has neither of these - any idea how I can add these?

I also followed the second link and added the third-party software as recommended but this hasn't changed anything either.

I am running 9.04, but am reluctant to downgrade just yet as in all other ways it is great, also I'd like to add the Hardware Drivers or Proprietary Drivers options and see what can be done there. Any ideas?

Many thanks

---

### Post by guru_ian on 2009-09-15
UPDATE:

Have added Hardware drivers menu with 

sudo apt-get install jockey-gtk

but the app only mentions wifi drivers and doesn't seem to have any mangable functions.

Just looking for proprietary drivers menu now...

---

### Post by guru_ian on 2009-09-15
This article tends to suggest a downgrade might be the way forward after all

[http://www.h-online.com/open/Ubuntu-9-04-and-Intel-graphics--/features/113196](http://www.h-online.com/open/Ubuntu-9-04-and-Intel-graphics--/features/113196)

---

### Post by guru_ian on 2009-09-15
SOLVED!

After running Update Manager I now have the option to set to 768x1366 which appears perfect although I must be losing 3 lines on each side of the screen it doesn't seem to notice.

---

### Post by freak42 on 2009-09-15
as far as i can see the native resolution of this notebook IS 1366x768 ??

---

