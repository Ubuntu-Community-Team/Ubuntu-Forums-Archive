---
title: "no network after kernal update?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by rm2011 on 2009-02-21
I just installed ubuntu on my acer aspire one netbook today, and from an online guide i eventually got wifi to work. after i did the upgrade everything was not useable.  even the wired network isnt working.  any suggestions?:confused:

---

### Post by CoCoKnots on 2009-02-21
Can you tell us more information about your hardware ? What you are using for a wireless card & router ?  Thanks

---

### Post by rm2011 on 2009-02-21
Heres what i get from the command "lshw"  I am using a belkin54g router.


 description: Computer
    product: AOA110
    vendor: Acer
    version: 1
    serial: LUS030B0438482997C2536
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal uuid=A041774A-C3E5-D411-915F-00238B3FEDA2
  *-core
       description: Motherboard
       vendor: Acer
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: v0.3304 (05/09/2008)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x48594D503136345336344350362D59352020
             vendor: 0xAD00000000000000
             physical id: 0
             serial: 0x00000000
             slot: J2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x4D342037305436343634515A332D43453620
             vendor: 0xCE00000000000000
             physical id: 1
             serial: 0x78642764
             slot: J6H2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1c
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 1d
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 1e
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
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
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-generic
                description: Ethernet interface
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: ff
                serial: 00:23:8b:3f:ed:a2
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=MII speed=100MB/s
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list
                configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-system:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0 module=sdhci_pci
           *-system:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.2
                bus info: pci@0000:04:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
           *-system:2 UNCLAIMED
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.3
                bus info: pci@0000:04:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.4
                bus info: pci@0000:04:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
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
             product: 82801G (ICH7 Family) USB UHCI Controller #2
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
             product: 82801G (ICH7 Family) USB UHCI Controller #3
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
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
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
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
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
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: SSDPAMM0008G1
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: Ver2
                serial: CVPA8320820J2
                size: 7695MiB (8069MB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=aead4529
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: b31bfd14-6986-4e34-856e-99e18e0b551c
                   size: 7318MiB
                   capacity: 7318MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-22 02:27:16 filesystem=ext3 modified=2009-02-21 18:25:13 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-02-21 16:48:38 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 376MiB
                   capacity: 376MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 376MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1a:15:20:6f:74:ec
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ryan@ryan-laptop:~$

---

### Post by CoCoKnots on 2009-02-21
Are you able to connect online using a LAN cable to the router ? I ran into this same issue after an updated download. Later I found that a lot of other Ubuntu users were running into the wireless (or lack of) problem also. I am using an Intel  with a Linksys router. I had to 'Hardwire' my connection to get on line. After getting online with a Linksys rep, I had to enter 192.168.1.1 into my browser address line & reset my parameters. Hope this helps.

---

