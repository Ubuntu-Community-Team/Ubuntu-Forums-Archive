---
title: "Speakers don't turn off when headphones inserted"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by dmaxel on 2010-09-27
Hello everyone,

I have an Acer Aspire 6530 laptop, and have a couple problems with sound, although I only want to touch on one today.

Basically, in Mavierck (fully updated), whenever I plug in my headphones, the speakers don't automatically turn themselves off, so I can't listen to something privately. The same problem occurs in previous Ubuntu versions as well, but in those it may work for a while, and then finally break for reasons unknown (not from updates). I looked around on the forum, but either there were no answers or they were **extremely** old. Everything has been unmuted, and there is no headphone slider, headphone jack sense, or anything along those lines in the mixer (GNOMEmixer and alsamixer)

Running sudo lshw gives me this:
```
description: Computer
    product: Aspire 6530
    vendor: Acer, inc.
    version: Not Applicable
    serial: <snip>
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific cpus=2 uuid=A01B73AB-42B9-DC11-B13E-00238BEE5FA0
  *-core
       description: Motherboard
       product: Mantasta
       vendor: Acer, Inc.
       physical id: 0
       version: Not Applicable
       serial: <snip>
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: v0.3223 (02/18/2009)
          size: 111KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) X2 Dual-Core QL-62
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.3.1
          slot: Socket S1G2
          size: 2GHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             physical id: 0
             slot: S1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 Synchronous
             physical id: 1
             slot: S2
             size: 1GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.3.1
          size: 1GHz
          capacity: 1GHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: Acer Incorporated [ALI]
             vendor: Acer Incorporated [ALI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:cfd00000-cfefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:9000(size=256) memory:cfdf0000-cfdfffff memory:cfe00000-cfefffff
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:cfdec000-cfdeffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:c0000000-c01fffff ioport:c0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:f0400000-f04fffff
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: 01
                serial: 00:26:5e:08:42:de
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.3.20 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 memory:f0400000-f040ffff
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 4)
             vendor: Advanced Micro Devices [AMD]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:a000(size=4096) memory:f0300000-f03fffff
           *-network
                description: Ethernet interface
                product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: b0
                serial: 00:23:8b:ee:5f:a0
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
                resources: irq:43 memory:f0300000-f033ffff ioport:a000(size=128)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8430(size=8) ioport:8424(size=4) ioport:8428(size=8) ioport:8420(size=4) ioport:8400(size=16) memory:f0208000-f02083ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54322
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: FBEO
                serial: 090515FB2D06LJCN4DJC
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0004c1ce
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: b421-d900
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-07-09 02:55:43 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 117GiB
                   capabilities: primary
              *-volume:2
                   description: HPFS/NTFS partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 48GiB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 66GiB
                   capacity: 66GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 62GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 3814MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f0004000-f0004fff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f0005000-f0005fff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f0208400-f02084ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f0006000-f0006fff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f0007000-f0007fff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f0208800-f02088ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8410(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T50N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RP05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f0000000-f0003fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 11h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 2
          bus info: usb@2:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
```I also have absolutely no microphone support (both the built-in one next to the webcam, nor the actual microphone jack work) but I'll keep that for another time.

Any help is appreciated. Thank you!

---

### Post by andrewthomas on 2010-09-27
This should be posted in the maverick forum

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

