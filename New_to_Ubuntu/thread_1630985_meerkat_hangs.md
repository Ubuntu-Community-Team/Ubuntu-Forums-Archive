---
title: "meerkat hangs"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by navaneethan on 2010-11-26
In my ubuntu (meerkat) i get hang often ,i don't know why? is it a bug? do feel the similar thing? whenever i do some operations like browsing or playing some videos which it gets hang? may i know the reason please? and suggest me?

---

### Post by madjr on 2010-11-26
were other versions working fine?

did you upgraded directly? or installed in a new partition?

does the live-cd/usb hangs also?

---

### Post by sikander3786 on 2010-11-26
In addition to the queries in above post, we need to know about your Hardware. Which graphics card is there? Did you install the proprietary drivers? And how much RAM?

That is not a bug. I am using Maverick at the moment and it runs smooth.

Is it desktop or netbook edition?

---

### Post by navaneethan on 2010-11-26
```
 vendor: Dell Inc.
          physical id: 0
          version: A02 (09/17/2009)
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T6570  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Microprocessor
          size: 2101MHz
          capacity: 2101MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 128KiB
             capacity: 128KiB
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
          physical id: 1000
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: NT2GT64U8HD0BN-AD
             vendor: 7F7F7F0B00000000
             physical id: 0
             serial: FBAB2C27
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             vendor: 7F7F7F7FCB000000
             physical id: 1
             serial: 00002880
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: QUOTVGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:efe8(size=8)
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
             resources: memory:f6b00000-f6bfffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f60(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f80(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6fa0(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:48 memory:f6afc000-f6afffff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:c0000000-c01fffff ioport:c0200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f6900000-f69fffff ioport:c0400000(size=2097152)
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 01
                serial: 20:7c:8f:08:5e:19
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.0.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f69f0000-f69fffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:f6600000-f68fffff ioport:f0000000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:4000(size=4096) memory:f6500000-f65fffff ioport:c0600000(size=2097152)
           *-generic:0
                description: SD Host controller
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:0f:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f65ff600-f65ff6ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:0f:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f65ff700-f65ff7ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 0.3
                bus info: pci@0000:0f:00.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:19 memory:f65ff800-f65fffff
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:c000(size=4096) memory:f6400000-f64fffff ioport:f0200000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 03
                serial: b8:ac:6f:73:f0:c2
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:45 ioport:ce00(size=256) memory:f0204000-f0204fff memory:f0200000-f0203fff memory:f0220000-f023ffff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f00(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f20(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6f40(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
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
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:6e70(size=8) ioport:6e78(size=4) ioport:6e80(size=8) ioport:6e88(size=4) ioport:6ea0(size=32) memory:fed1c800-fed1cfff
           *-disk
                description: ATA Disk
                product: WDC WD5000BEVT-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX21A50Y6886
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=14e3524f
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 2a45d674-bbf6-764c-a0ce-828a1fbeb878
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-08-28 00:06:32 filesystem=ntfs label=Windows state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 392GiB
                   capacity: 392GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 78GiB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 78GiB
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 78GiB
                 *-logicalvolume:3
                      description: HPFS/NTFS partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 79GiB
                 *-logicalvolume:4
                      description: Linux filesystem partition
                      physical id: 9
                      logical name: /dev/sda9
                      logical name: /
                      capacity: 14GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:5
                      description: Linux swap / Solaris partition
                      physical id: a
                      logical name: /dev/sda10
                      capacity: 3992MiB
                      capabilities: nofs
                 *-logicalvolume:6
                      description: Linux filesystem partition
                      physical id: b
                      logical name: /dev/sda11
                      logical name: /boot
                      capacity: 1137MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,commit=5,barrier=0,data=ordered state=mounted
                 *-logicalvolume:7
                      description: HPFS/NTFS partition
                      physical id: c
                      logical name: /dev/sda12
                      capacity: 58GiB
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW TS-L633C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DW50
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
             resources: memory:f6afbf00-f6afbfff ioport:1100(size=32)
  *-battery
       product: DELL X612G05
       vendor: LG
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 44000mWh
       configuration: voltage=11.1V
navanee@navanee-Vostro-1015:~$ 

```this is my sys info

---

### Post by madjr on 2010-11-26
ok, is a dell. but you havent answered my first comment

---

### Post by navaneethan on 2010-11-28
ya i have win7 working good ;-)

---

