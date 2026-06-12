---
title: "HELP. No more video out via VGA on Ubuntu 9.10. ATI problem?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Major_Rager on 2010-02-11
Hey there. Been using Linux Ubuntu for over 2 years now, but this will be my first post.

I just recently got a new laptop notebook. An HP Pavilion dv-2-1028CA, to be exact.

My old one was a Toshiba Satellite, but it died and I had to purchase another computer last minute. Both laptops have ATI Radeon graphics cards.

When i was using the Satellite, I was using Ubuntu 8.10 and had no problem getting video out to my TV via S-Video. Now, since I have a superior laptop (I think), I decided to install Ubuntu 9.10 on my HP and I love it. Very little setup was required, unlike past distros.

However, I cannot get video out via VGA on my HP now. I am assuming this has to do with maybe no ATI Radeon support on later versions of Ubuntu?

Is there anyway to make this work? I've even tried downloading ATI Catalyst Control center but it tells me it cannot find any ATI drivers, and none are available on the HardWare Drivers downloader via System. Am I sh*t outta luck?

Here are my specs:
```
description: Notebook
    product: HP Pavilion dv2 Notebook PC
    vendor: Hewlett-Packard
    version: F.08
    serial: CNC92421HK
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=oem-specific chassis=notebook uuid=7E41316A-F468-C05E-7BBD-0021CC3ABE04
  *-core
       description: Motherboard
       product: 3054
       vendor: Flextronics
       physical id: 0
       version: 17.23
       serial: 0123456789012345
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.08 (04/22/2009)
          size: 112KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Neo Processor MV-40
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) Neo Processor MV-40
          slot: Socket M2/S1G1
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: H0 L1 Cache
             size: 128KiB
             capacity: 128KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 512KiB
             capacity: 512KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GiB
        *-bank
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             physical id: 0
             slot: S1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:9000(size=4096) memory:cfd00000-cfefffff ioport:d0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=64
                resources: memory:d0000000-dfffffff(prefetchable) memory:cfdf0000-cfdfffff ioport:9000(size=256) memory:cfe00000-cfefffff
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 memory:f0200000-f02fffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:25:56:0b:e1:c7
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.2.10 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 memory:f0200000-f020ffff
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:a000(size=4096) memory:80000000-800fffff ioport:f0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 02
                serial: 00:21:cc:3a:be:04
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:26 ioport:a000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:21 ioport:8440(size=8) ioport:8434(size=4) ioport:8438(size=8) ioport:8430(size=4) ioport:8400(size=16) memory:f0309000-f03093ff
           *-disk
                description: ATA Disk
                product: ST9250315AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0003
                serial: 5VC1X8YQ
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d2a2e519
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: b140b690-0d99-419d-9a22-7a04e9097afe
                   size: 227GiB
                   capacity: 227GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-01-23 20:39:55 filesystem=ext3 modified=2010-02-07 19:51:18 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback mounted=2010-02-09 13:47:19 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5506MiB
                   capacity: 5506MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5506MiB
                      capabilities: nofs
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
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f0304000-f0304fff
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
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f0305000-f0305fff
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
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f0306000-f0306fff
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
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f0307000-f0307fff
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
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f0308000-f0308fff
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
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f0309400-f03094ff
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
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16)
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
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
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
             resources: irq:16 memory:f0300000-f0303fff
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
             capabilities: pci bus_master
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
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 1
          bus info: usb@1:10
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb

```

---

