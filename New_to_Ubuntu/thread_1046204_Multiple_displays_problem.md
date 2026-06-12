---
title: "Multiple displays problem"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by moody_mark on 2009-01-21
Everytime i connect another display to this PC (Dell 610 Latitude Laptop) and try to run two displays I have the following problems;

1. The external display resolution will only go up to 1024 x 768 (the laptop screen goes up to 1400 x 1050 using the "system --> preferences --> screen resolution" dialog

2. The local display seems to try to adjust the desktop to this resolution so the bottom panel moves up leaving a gap at the bottom of the screen

I appreciate that the system is probably trying its best to load a default driver for the new device. I usually have desktop effects on but the result is the same wether they are on or off. Commonly i use 4 workspaces. Is there any way to increase this resolution?

---

### Post by AegisTalons on 2009-01-21
What kind of video card are you running on the Dell 610 Latitude? If its discrete graphics, such as Nvidia, did you try to install the Nvidia drivers? Nvidia control window gives you more control over the graphics.

---

### Post by moody_mark on 2009-01-22
Heres the output of my "sudo lshw" command

```
barney                    
    description: Portable Computer
    product: Latitude D610
    vendor: Dell Inc.
    serial: 1MPD12J
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=docking uuid=44454C4C-4D00-1050-8044-B1C04F31324A
  *-core
       description: Motherboard
       product: 0U8082
       vendor: Dell Inc.
       physical id: 0
       serial: .1MPD12J.CN486435BU5526.
       slot: MiniPCI
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A06 (10/02/2005)
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.86GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.8
          slot: Microprocessor
          size: 1862MHz
          capacity: 1866MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: AD00000000000000
             physical id: 0
             serial: 00003031
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous [empty]
             physical id: 1
             slot: DIMM_B
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:14:22:cc:a1:ab
                size: 1GB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751-v3.29a ip=10.167.98.47 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=1GB/s
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCI6515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-communication UNCLAIMED
                description: Communication controller
                product: PCI6515 SmartCard Controller
                vendor: Texas Instruments
                physical id: 1.5
                bus info: pci@0000:03:01.5
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-network
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:ee:c9:7e
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: TOSHIBA MK4018GA
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: M0.0
                serial: 62GA0572T
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=232e232e
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 66594a9f-37b0-45f3-bc90-a2affff20abe
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-09-02 07:57:28 filesystem=ext3 modified=2009-01-21 18:50:48 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-01-21 10:43:09 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1608MiB
                   capacity: 1608MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1608MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD+-RW ND-6650A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 102C
                serial: [_NEC    DVD+-RW ND-6650A102C05051200
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
  *-battery
       product: DELL Y13385B
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 48000mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: cipsec0
       serial: 00:0b:fc:f8:01:8f
       capabilities: ethernet physical
```

---

### Post by AegisTalons on 2009-01-23
It looks like you got discrete graphics. More specifically an Intel Mobile 915GM/GMS/910GML Express Graphics Controller. I have no experience with that card and manufacturer. I would suggest trying to google your card plus linux or ubuntu and externel display. Sorry I could not have been more helpful.

---

### Post by Thelasko on 2009-01-23
Although I've never done this myself, [this documentation]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Overview") tells you how to edit your xorg.conf file to make it work.

[Specifically]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Summing_up"), you may have to increase the size of the Virtual line in the "Display" subsection.  Although, do not make it larger than 2048x2048 because then you will lose your direct rendering (3D) support.

---

### Post by moody_mark on 2009-01-27
> **Thelasko said:**
> tells you how to edit your xorg.conf file to make it work.

Ok, so once I edit my Xorg.conf file. How to I get gnome to take notice of that and not look at its own settings. Gnome must use some settings elsewhere as my Xorg.conf file is months old and I would have expected it to be recent if I change display settings recently?

---

### Post by Thelasko on 2009-01-27
> **moody_mark said:**
> Ok, so once I edit my Xorg.conf file. How to I get gnome to take notice of that and not look at its own settings. Gnome must use some settings elsewhere as my Xorg.conf file is months old and I would have expected it to be recent if I change display settings recently?

Gnome always looks at the Xorg.conf file first.  Every xorg.conf has the same settings (I think since Gusty).  They all say "Default Screen", "Generic Monitor", etc.  These default settings are ignored by Gnome and Gnome then proceeds to configure everything automatically.

By following the instructions I gave you, you should be leaving the majority of those settings default, and therefore Gnome will configure everything automatically.  However, we will add a few configuration options manually.  The most important being the "Display" subsection.  This is simply supplementing the information Gnome has about your system so it can come up with a better configuration for your system.

Remember to back up your xorg.conf file.  Although, Gnome is very good at detecting problems, and will help you out if you make any mistakes.  You can also boot into recovery mode if you make any big mistakes.

---

