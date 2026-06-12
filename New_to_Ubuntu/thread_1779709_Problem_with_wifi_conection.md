---
title: "Problem with wifi conection"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by TheLinuxMarc on 2011-06-10
I just installed Linux 10.34 and I have NETGEAR WNDA3100v2 driver. Its not being read by Linux, so i cant connect my network adapter(i dont have a laptop so i have to have the adapter). The adapter isnt even functioning, so thats an obvious sign thatsd its being ignored by Linux. What can I do to fix this.
I did the sudo lshw thing these are the results:
 description: Desktop Computer
    product: HP Compaq dx2390 Microtower (KV070EA#ABV)
    vendor: Hewlett-Packard
    serial: 3CB91521K6
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=103C_53307F sku=KV070EA#ABV uuid=00AC8855-A88B-1410-8163-E93F9C4CA036
  *-core
       description: Motherboard
       product: 2A78h
       vendor: MSI
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 5.18
          date: 02/20/2009
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Socket 775
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=4
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous external write-back unified
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
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 2G-UDIMM
             vendor: Kingston
             physical id: 0
             serial: B8CCB159
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 2G-UDIMM
             vendor: Kingston
             physical id: 1
             serial: AECCB9DB
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 2800MHz
          capacity: 2800MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:f8000000-fbffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G96 [GeForce 9400 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:cf00(size=128) memory:fb000000-fb07ffff
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
             resources: irq:43 memory:fdff8000-fdffbfff
        *-pci:1
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
             resources: irq:41 ioport:d000(size=4096) memory:fdb00000-fdbfffff ioport:fdc00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:24:21:28:d4:70
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.10 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdc00000-fdc1ffff
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
             resources: irq:23 ioport:f500(size=32)
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
             resources: irq:19 ioport:f600(size=32)
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
             resources: irq:18 ioport:f700(size=32)
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
             resources: irq:16 ioport:f800(size=32)
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
             resources: irq:23 memory:fdfff000-fdfff3ff
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
             resources: ioport:e000(size=4096) memory:fdd00000-fddfffff ioport:fde00000(size=1048576)
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
        *-ide
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f900(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD1600AAJS-6
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 02.0
                serial: WD-WMAV33541813
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=418b418b
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: c27e2826-0e7c-da4e-9ce8-ba5f2905d065
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-07-18 08:17:43 filesystem=ntfs state=clean
           *-disk:1
                description: ATA Disk
                product: WDC WD2500AAJS-7
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WCAT15916440
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=eacceacc
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 182dd100-30be-1348-b290-f2f03cf29cfa
                   size: 204GiB
                   capacity: 204GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-07-23 04:07:59 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /
                      capacity: 24GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 4093MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-H653Z
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/WNDA3100v2
                version: HD00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/WNDA3100v2
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
     *-scsi
          physical id: 2
          bus info: usb@1:7
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sdf
        *-disk:4
             description: SCSI Disk
             physical id: 0.0.4
             bus info: scsi@2:0.0.4
             logical name: /dev/sdg

---

### Post by wildmanne39 on 2011-06-11
> **TheLinuxMarc said:**
> I just installed Linux 10.34 and I have NETGEAR WNDA3100v2 driver. Its not being read by Linux, so i cant connect my network adapter(i dont have a laptop so i have to have the adapter). The adapter isnt even functioning, so thats an obvious sign thatsd its being ignored by Linux. What can I do to fix this.
I did the sudo lshw thing these are the results:
 description: Desktop Computer
    product: HP Compaq dx2390 Microtower (KV070EA#ABV)
    vendor: Hewlett-Packard
    serial: 3CB91521K6
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=103C_53307F sku=KV070EA#ABV uuid=00AC8855-A88B-1410-8163-E93F9C4CA036
  *-core
       description: Motherboard
       product: 2A78h
       vendor: MSI
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 5.18
          date: 02/20/2009
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Socket 775
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=4
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous external write-back unified
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
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 2G-UDIMM
             vendor: Kingston
             physical id: 0
             serial: B8CCB159
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 2G-UDIMM
             vendor: Kingston
             physical id: 1
             serial: AECCB9DB
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 2800MHz
          capacity: 2800MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:f8000000-fbffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G96 [GeForce 9400 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:cf00(size=128) memory:fb000000-fb07ffff
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
             resources: irq:43 memory:fdff8000-fdffbfff
        *-pci:1
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
             resources: irq:41 ioport:d000(size=4096) memory:fdb00000-fdbfffff ioport:fdc00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:24:21:28:d4:70
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.10 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdc00000-fdc1ffff
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
             resources: irq:23 ioport:f500(size=32)
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
             resources: irq:19 ioport:f600(size=32)
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
             resources: irq:18 ioport:f700(size=32)
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
             resources: irq:16 ioport:f800(size=32)
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
             resources: irq:23 memory:fdfff000-fdfff3ff
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
             resources: ioport:e000(size=4096) memory:fdd00000-fddfffff ioport:fde00000(size=1048576)
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
        *-ide
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f900(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD1600AAJS-6
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 02.0
                serial: WD-WMAV33541813
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=418b418b
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: c27e2826-0e7c-da4e-9ce8-ba5f2905d065
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-07-18 08:17:43 filesystem=ntfs state=clean
           *-disk:1
                description: ATA Disk
                product: WDC WD2500AAJS-7
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WCAT15916440
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=eacceacc
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 182dd100-30be-1348-b290-f2f03cf29cfa
                   size: 204GiB
                   capacity: 204GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-07-23 04:07:59 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /
                      capacity: 24GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 4093MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-H653Z
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/WNDA3100v2
                version: HD00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/WNDA3100v2
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
     *-scsi
          physical id: 2
          bus info: usb@1:7
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sdf
        *-disk:4
             description: SCSI Disk
             physical id: 0.0.4
             bus info: scsi@2:0.0.4
             logical name: /dev/sdg
Hi, I found  a thread of a person with the same card as yours follow the instructions on this thread and it also refers to another thread go there as well and you will get it working.
[http://ubuntuforums.org/showthread.php?t=1740963&highlight=RTL8101E%2FRTL8102E+PCI+Express](http://ubuntuforums.org/showthread.php?t=1740963&highlight=RTL8101E%2FRTL8102E+PCI+Express)

---

