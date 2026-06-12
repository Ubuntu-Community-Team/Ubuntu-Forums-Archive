---
title: "wireless help"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by cic.11 on 2008-06-26
im new to linux and ubuntu so i have little to no idea of what to do :(, can some one help me?

i recently decided to put Xubuntu Version 8.04 on my old computer, its an emachines T1801 to be exact. then i connected a usb linksys wireless g adapter model# WUSB54G ver.4, then when i went to Network Manager it recognized the card as wireless after i put the essid and wep key. after that i tried going on the internet, but the internet would not work.  

 can some one help me? am i missing something? :confused:


when i put $sudo lshw i get

code:
ubuntu                    
    description: Desktop Computer
    product: Emachines
    vendor: TriGem Computer, Inc.
    version: 100
    serial: 0000000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=oem-specific chassis=desktop frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       product: TriGem System Board
       vendor: TriGem Computer, Inc.
       physical id: 0
       version: 000000
       serial: 000000000000000000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: Ver 1.05 (04/06/2001)
          size: 98KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.6
          slot: U1
          size: 800MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 128MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 64MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 64MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 82810 GMCH (Graphics Memory Controller Hub)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82810 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-pci
             description: PCI bridge
             product: 82801AA PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
        *-isa
             description: ISA bridge
             product: 82801AA ISA Bridge (LPC)
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
             product: 82801AA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: QUANTUM FIREBALL
                vendor: Quantum
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: APL.
                serial: 052113662126
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=06a806a7
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: ef3f9208-b801-4ffc-8e4f-6e3a8a40ba09
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-26 07:34:34 filesystem=ext3 modified=2008-06-27 13:27:12 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-06-27 13:27:12 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 352MiB
                   capacity: 352MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 352MiB
                      capabilities: nofs
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-RW  CRX168B
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.0a
                serial: [SONY    CD-RW  CRX168B  1.0a Mar23 ,2001
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-usb
             description: USB Controller
             product: 82801AA USB Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801AA AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801AA AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: DataTraveler 2.0
             vendor: Kingston
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             size: 953MiB (999MB)
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 953MiB (999MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=04030201
              *-volume
                   description: Windows FAT volume
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /media/KINGSTON
                   version: FAT16
                   serial: e0fd-1813
                   size: 953MiB
                   capacity: 953MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=KINGSTON mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=winnt,utf8 state=mounted
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:75:bb:fc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


when i put  lspci i get 

code:
carlos@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)

---

