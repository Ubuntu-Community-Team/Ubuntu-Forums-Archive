---
title: "Display problem"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by sunwatt on 2011-06-01
Where do I change the settings so I get the wide scale display as seen in screenshot and screenshot1?

Its more than the size of the desktop icons. See in shot1 and 3 the way the browser is seen. 

Normally I get the display seen in shot2 and 3, and I cant see the whole browser window  :(

But the display changes by itself sometimes, and today I snapped these shots in hopes I can figure this out.

Then rebooted, and back to as seen in 2 and 3.

Seems to happen when I unplug the VGA cable, and reconnect.

Thanks

Jim
Mini 9 32gb ssd
Acer LCD model x183h
Ubuntu 10.04

---

### Post by johngreth on 2011-06-01
Preferences -> Monitors -> Resolution

Although it should auto detect the proper settings. I'm not sure why it doesn't...

---

### Post by wildmanne39 on 2011-06-01
> **sunwatt said:**
> Where do I change the settings so I get the wide scale display as seen in screenshot and screenshot1?

Its more than the size of the desktop icons. See in shot1 and 3 the way the browser is seen. 

Normally I get the display seen in shot2 and 3, and I cant see the whole browser window  :(

But the display changes by itself sometimes, and today I snapped these shots in hopes I can figure this out.

Then rebooted, and back to as seen in 2 and 3.

Seems to happen when I unplug the VGA cable, and reconnect.

Thanks

Jim
Mini 9 32gb ssd
Acer LCD model x183h
Ubuntu 10.04
Hi, have you went into additional drivers to see if there is a driver there for your video card if so activate it, then restart,if that is not the problem we need to know what your system specs are the hardware you have and the version of ubuntu you are using. You can use this command to find the hardware the post the results by clicking on # and pasting between the two code tags.

---

### Post by johngreth on 2011-06-01
What command? :0

---

### Post by sunwatt on 2011-06-01
> **wildmanne39 said:**
> Hi, have you went into additional drivers to see if there is a driver there for your video card if so activate it, then restart,if that is not the problem we need to know what your system specs are the hardware you have and the version of ubuntu you are using. You can use this command to find the hardware the post the results by clicking on # and pasting between the two code tags.


Yes, please whats the command I put in terminal?

---

### Post by sunwatt on 2011-06-01
> **johngreth said:**
> Preferences -> Monitors -> Resolution

Although it should auto detect the proper settings. I'm not sure why it doesn't...

Under Preferences, Monitors, resolution I am offered 800x600 or 640x480

---

### Post by corncob on 2011-06-01
> **sunwatt said:**
> Yes, please whats the command I put in terminal?

He probably has something like
```
sudo lshw
```
in mind.

---

### Post by sunwatt on 2011-06-01
> **corncob said:**
> He probably has something like
```
sudo lshw
```in mind.
jim@jim-laptop:~$ sudo lshw
[sudo] password for jim: 
jim-laptop                
    description: Portable Computer
    product: Inspiron 910
    vendor: Dell Inc.
    version: A05
    serial: D9TCHJ1
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific chassis=portable cpus=1 uuid=44454C4C-3900-1054-8043-C4C04F484A31
  *-core
       description: Motherboard
       product: CN0J14
       vendor: Dell Inc.
       physical id: 0
       version: A05
       serial: .D9TCHJ1.ppppppppppppppd
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 1
          version: A05 (03/05/2009)
          size: 100KiB
          capacity: 1984KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: U1
          size: 1600MHz
          capacity: 2048MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 512KiB
             capacity: 4MiB
             capabilities: burst external write-back
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
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank
             description: SODIMM DDR2 Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f007ffff ioport:1800(size=8) memory:d0000000-dfffffff(prefetchable) memory:f0300000-f033ffff
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
             resources: memory:f0080000-f00fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f0540000-f0543fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:f0100000-f01fffff memory:40000000-401fffff(prefetchable)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f0100000-f01000ff memory:40000000-4000ffff(prefetchable)
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f0100400-f01004ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:f0100800-f01008ff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:f0200000-f02fffff memory:40200000-403fffff(prefetchable)
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth3
                version: 01
                serial: 00:23:08:6e:ad:4c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.2.2 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:f0200000-f0203fff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:40400000-407fffff ioport:f0600000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth2
                version: 02
                serial: 00:24:e8:91:e3:79
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0544000-f05443ff
        *-pci:3
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
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-disk
                description: ATA Disk
                product: Flash Module
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sda
                version: Ver2
                serial: 25190799110101006045
                size: 28GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009304b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: cab968c1-c439-4c42-af06-956251fe62a6
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-29 19:36:00 filesystem=ext4 lastmountpoint=/&#65533;&#65533;B%&#65533;T&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;E&#65533; &#65533;&#65533;&#65533;0#&#65533;&#65533;/&#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B%&#65533;&#65533;~&#65533;&#65533;&#65533;~&#65533;&#65533; modified=2011-05-25 09:38:55 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-01 15:41:47 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sda2
                   size: 1258MiB
                   capacity: 1258MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1258MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)
  *-battery
       product: Dell
       vendor: Dell
       physical id: 1
       slot: Rear
       capacity: 32560mWh
       configuration: voltage=14.8V

---

### Post by wildmanne39 on 2011-06-01
> **sunwatt said:**
> jim@jim-laptop:~$ sudo lshw
[sudo] password for jim: 
jim-laptop                
    description: Portable Computer
    product: Inspiron 910
    vendor: Dell Inc.
    version: A05
    serial: D9TCHJ1
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific chassis=portable cpus=1 uuid=44454C4C-3900-1054-8043-C4C04F484A31
  *-core
       description: Motherboard
       product: CN0J14
       vendor: Dell Inc.
       physical id: 0
       version: A05
       serial: .D9TCHJ1.ppppppppppppppd
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 1
          version: A05 (03/05/2009)
          size: 100KiB
          capacity: 1984KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: U1
          size: 1600MHz
          capacity: 2048MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 512KiB
             capacity: 4MiB
             capabilities: burst external write-back
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
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank
             description: SODIMM DDR2 Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f007ffff ioport:1800(size=8) memory:d0000000-dfffffff(prefetchable) memory:f0300000-f033ffff
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
             resources: memory:f0080000-f00fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f0540000-f0543fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:f0100000-f01fffff memory:40000000-401fffff(prefetchable)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f0100000-f01000ff memory:40000000-4000ffff(prefetchable)
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f0100400-f01004ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:f0100800-f01008ff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:f0200000-f02fffff memory:40200000-403fffff(prefetchable)
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth3
                version: 01
                serial: 00:23:08:6e:ad:4c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.2.2 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:f0200000-f0203fff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:40400000-407fffff ioport:f0600000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth2
                version: 02
                serial: 00:24:e8:91:e3:79
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0544000-f05443ff
        *-pci:3
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
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-disk
                description: ATA Disk
                product: Flash Module
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sda
                version: Ver2
                serial: 25190799110101006045
                size: 28GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009304b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: cab968c1-c439-4c42-af06-956251fe62a6
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-29 19:36:00 filesystem=ext4 lastmountpoint=/&#65533;&#65533;B%&#65533;T&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;E&#65533; &#65533;&#65533;&#65533;0#&#65533;&#65533;/&#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B%&#65533;&#65533;~&#65533;&#65533;&#65533;~&#65533;&#65533; modified=2011-05-25 09:38:55 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-01 15:41:47 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sda2
                   size: 1258MiB
                   capacity: 1258MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1258MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)
  *-battery
       product: Dell
       vendor: Dell
       physical id: 1
       slot: Rear
       capacity: 32560mWh
       configuration: voltage=14.8V
Hi, I am sorry about missing the command I had an emergency while I was typing to you and I had to leave, so I rushed to finish the message and I left it out.
Since you are using 10.10 if there is a driver for your video card it would be under restricted drivers, get to it from your menu go to administration click on restricted drivers after you activate it restart the system, I looked in synaptic, I put in intel and it show the x server there and it has support for your card if you do not have the driver in the restricted section go to synaptic and install the file x server for your card the 945. It should be in restricted though, but you have to be connected to the internet to get it.

---

### Post by sunwatt on 2011-06-01
Sorry abt the emergency, and hope the crisis has passed.

Im using 10.04 and didnt see restricted drivers in admin or anywhere... where do I look?

---

### Post by wildmanne39 on 2011-06-01
> **sunwatt said:**
> Sorry abt the emergency, and hope the crisis has passed.

Im using 10.04 and didnt see restricted drivers in admin or anywhere... where do I look?Hi, I am running 11.04 so I can not look it up, you may not have any for your system that might be why you do not see the restricted drivers.
Do the second thing I said in my last post and see if x server for intel is installed. Go to administration click on synaptic package manager. I think I remember restricted drivers for 10.10 in preferences look for it there.

---

### Post by sunwatt on 2011-06-01
I went ahead and installed the intel-dbg and looked again in preferences and admin. Dont see any restricted drivers, only the hardware drivers showing the wifi.

I will reboot in the morning, maybe it will appear.

thanks

---

### Post by wildmanne39 on 2011-06-02
> **sunwatt said:**
> I went ahead and installed the intel-dbg and looked again in preferences and admin. Dont see any restricted drivers, only the hardware drivers showing the wifi.

I will reboot in the morning, maybe it will appear.

thanksHi, make sure the one that says x server for intel is installed it is seen when you type intel in the search box in synaptic.

---

### Post by sunwatt on 2011-06-02
OK, all the xserver xorg stuff is installed.

---

### Post by wildmanne39 on 2011-06-02
> **sunwatt said:**
> OK, all the xserver xorg stuff is installed.Hi, is this problem only in firefox? If so did you install an add-on for zooming in or making the page larger? Aslo in preference you can change the font size add that might help.

---

### Post by wildmanne39 on 2011-06-02
> **sunwatt said:**
> OK, all the xserver xorg stuff is installed.

Hi, looked at the screen shots three more times and that is what is happening in fire fox your page is larger in the screen shots, and that is making it go off the page and yes that will happen if display settings are not correct or if firefox is making the page larger itself.

---

### Post by sunwatt on 2011-06-02
Look at the shot of my desktop.. the difference in these displays is a puzzle to me

Thats interesting about Firefox, you could be right.  Thiunderbird also doesnt fit my screen very well. This is my only computer so I have nothing to compair to.

Here is openshot, see how the left side is cut off?  I've tried to adjust the size and fit, and have yet to solve this. 

Somehow by hooking up an the external monitor, the computer changes to the better scale, scratchin my head.

thanks

---

### Post by wildmanne39 on 2011-06-02
> **sunwatt said:**
> Look at the shot of my desktop.. the difference in these displays is a puzzle to me

Thats interesting about Firefox, you could be right.  Thiunderbird also doesnt fit my screen very well. This is my only computer so I have nothing to compair to.

Here is openshot, see how the left side is cut off?  I've tried to adjust the size and fit, and have yet to solve this. 

Somehow by hooking up an the external monitor, the computer changes to the better scale, scratchin my head.

thanksHi, it sounds like you need to manually set your resolution up, I had to a few months ago but I do not remember the exact way to do it. The settings are in the x server config file and you can us this command to look at your settings and see what it is capable of.
```
xrandr
```I think that is the command I do not have access to my files at the moment to look it up.

---

### Post by sunwatt on 2011-06-02
jim@jim-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       59.8 +
   1024x768       75.1     72.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3*    56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 800x600+0+0 (normal left inverted right x axis y axis) 195mm x 113mm
   1024x600       60.0 +
   800x600        60.3* 
   640x480        59.9  
jim@jim-laptop:~$

---

### Post by wildmanne39 on 2011-06-03
> **sunwatt said:**
> jim@jim-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       59.8 +
   1024x768       75.1     72.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3*    56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 800x600+0+0 (normal left inverted right x axis y axis) 195mm x 113mm
   1024x600       60.0 +
   800x600        60.3* 
   640x480        59.9  
jim@jim-laptop:~$
Hi, here is a guide to use to set your resolution manually, after you set it make sure you go to the next step below that one, you have to make it where it will save the changes permanently. If you do not do the last step it will reset when you turn your system off. Follow the guide carefully I know it look scary if you are not use to seeing the command line out put.
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by sunwatt on 2011-06-03
Thanks, I'll give it a try.

Last nite I downloaded 11.04 iso and made a live usb to try.

Not sure I did it right, or maybe on the live version there isnt any access to System, Admin to look around for video drivers you mentioned early in this thread. On the live usb stick Firefox had the usual problem of not fitting.


I have an extra ssd so will install 11.04 on that and keep trying solutions. 

I appreciate your help.

---

