---
title: "Adding e-sata controller"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by sardamil on 2009-08-28
I just bought an eSATA II PCI Express card to connect my external HDD to my system. Now I just can't find how to install the thing.

Can anybody tell me what I'm missing?

---

### Post by Ocxic on 2009-08-28
Turn off computer, Remove side pane/case (turn off power switch on power supply, and GROUND(touch) SELF TO CASE before touching your card), remove PCI slot protective shield, plug in and secure PCI card with screw, install hard drive and connect relevant cables, power on computer, test with "fdisk -l" or gparted application, to see if new HD is detected, if yes then mount the drive, if no then post output of 
"sudo lspci" and "sudo lshw".

---

### Post by sardamil on 2009-08-28
Perhaps I should have been clearer. Connecting the actual card is not the problem. Getting Ubuntu to find it and install the drivers is.

00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:05.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port B)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

    description: Desktop Computer
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: GA-MA770-DS3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2 (11/19/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          slot: Socket M2
          size: 2200MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          product: Athlon
          vendor: AMD
          physical id: 5
          bus info: cpu@1
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          slot: Socket M2
          size: 2200MHz
          capacity: 3200MHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1 DISABLED
             description: L2 cache
             physical id: e
             slot: External Cache
             capacity: 1MiB
             capabilities: synchronous internal write-through
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 2046MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM 800 MHz (1.2 ns) [empty]
             physical id: 2
             slot: A2
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM 800 MHz (1.2 ns) [empty]
             physical id: 3
             slot: A3
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: RX780/RX790 Chipset Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600 GTS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port B)
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
        *-pci:2
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port F)
             vendor: ATI Technologies Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: 00:1a:4d:5d:d0:e8
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.19.3.2 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=32 module=ahci
           *-disk:0
                description: ATA Disk
                product: ST3250310AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9RY17RQY
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00000012
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 039e062c-6b37-4696-bddf-8e476fb1b031
                   size: 227GiB
                   capacity: 227GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-07-09 20:07:39 filesystem=ext3 modified=2009-08-28 22:04:52 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-08-28 22:04:52 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5812MiB
                   capacity: 5812MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5812MiB
                      capabilities: nofs
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM GDRH20N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 0L02
                capabilities: removable audio dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted
           *-disk:1
                description: ATA Disk
                product: ST3250410AS
                vendor: Seagate
                physical id: 2
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 6RY2GDE6
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=323a323a
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /storage
                   version: 1.0
                   serial: e810ef80-8ad2-4585-9df7-964f6fcdf00c
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-01-25 12:09:30 filesystem=ext3 modified=2009-08-28 22:09:50 mount.fstype=ext3 mount.options=rw,errors=continue,data=ordered mounted=2009-08-28 22:09:50 state=mounted
           *-cdrom:1
                description: DVD-RAM writer
                product: DVDRAM GSA-H62N
                vendor: HL-DT-ST
                physical id: 3
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: CL00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master vga_palette
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: e
                bus info: pci@0000:04:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
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
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: 1
          bus info: usb@1:10
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@7:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@7:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@7:0.0.3
             logical name: /dev/sdf
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:df:5d:1d:d5:ee
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by sardamil on 2009-08-29
Can nobody help? Please?

---

### Post by sardamil on 2009-08-31
Is there really nobody that can help me?

---

### Post by Ocxic on 2009-08-31
what type of card is it?
(company, model, spec, website even?)

---

### Post by sardamil on 2009-09-02
[http://www.delock.com/produkte/suche/Delock_eSATA_II_PCI_Express_Card_1_Port_89119.html](http://www.delock.com/produkte/suche/Delock_eSATA_II_PCI_Express_Card_1_Port_89119.html)

Delock eSATA II PCI Express Card, 1 Port

---

### Post by cariboo on 2009-09-02
According to the output of lspci:

> 02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360


and lshw:

> *-storage
description: SATA controller
product: JMicron 20360/20363 AHCI Controller
vendor: JMicron Technologies, Inc.
physical id: 0
bus info: pci@0000:02:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: storage pm pciexpress bus_master cap_list
configuration: driver=ahci latency=0 module=ahci/20363 AHCI Controller (rev 02)]

Your device is detected and the driver is loaded.

When you connect a drive and reboot is the drive detected?
Open a terminal and type:

```
sudo fdisk -l
```

---

### Post by egalvan on 2009-09-02
> **sardamil said:**
> Perhaps I should have been clearer. Connecting the actual card is not the problem. Getting Ubuntu to find it and install the drivers is.

```

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 

     *-pci:0
        *-storage
              description: SATA controller
              product: JMicron 20360/20363 AHCI Controller
              vendor: JMicron Technologies, Inc.
              physical id: 0
              bus info: pci@0000:02:00.0

        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
...
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
```
 

Linux in general does not need specialized SATA drivers... they are built into the kernel.

You show several diffetent controllers in the listing.
Is the card installed?
Is there a drive attached?
Does gparted show anything?

try removing the card and see if one of the controlles disappears form the listing.

---

