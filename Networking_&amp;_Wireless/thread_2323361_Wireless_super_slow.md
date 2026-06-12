---
title: "Wireless super slow"
date: 2016-05-04
forum: Networking &amp; Wireless
---

### Post by Joo_Abrantes on 2016-05-04
Today I installed Ubuntu 16 and my wireless wasn't working (the same was happening with Ubuntu 14.04). I followed the solution presented here [http://askubuntu.com/a/543626/250716](http://askubuntu.com/a/543626/250716) and my wifi started to work but it is now super slow (way faster on Windows). What should I do?

Information about my system:

```

joao
    description: Computer
    width: 64 bits
    capabilities: smbios-2.8 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 15GiB
     *-cpu
          product: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 3276MHz
          capacity: 3500MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
     *-pci
          description: Host bridge
          product: Sky Lake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Sky Lake PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:5000(size=4096) memory:93000000-93ffffff ioport:80000000(size=301989888)
           *-display
                description: 3D controller
                product: GM107M [GeForce GTX 950M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nouveau latency=0
                resources: irq:130 memory:93000000-93ffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:5000(size=128)
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915_bpo latency=0
             resources: irq:131 memory:92000000-92ffffff memory:a0000000-afffffff ioport:6000(size=64)
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:94320000-94327fff
        *-usb
             description: USB controller
             product: Sunrise Point-H USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:126 memory:94300000-9430ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-21-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=8 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-21-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Video
                   product: HP Truevision HD
                   vendor: Generic
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.03
                   serial: DETGB01BI9E3L7
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   product: Bluetooth Radio
                   vendor: Realtek
                   physical id: 7
                   bus info: usb@1:7
                   version: 2.00
                   serial: 00e04c000001
                   capabilities: bluetooth usb-2.10
                   configuration: driver=btusb maxpower=500mA speed=12Mbit/s
        *-generic:1 UNCLAIMED
             description: Signal processing controller
             product: Sunrise Point-H Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:94332000-94332fff
        *-communication
             description: Communication controller
             product: Sunrise Point-H CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:132 memory:94333000-94333fff
        *-storage
             description: SATA controller
             product: Sunrise Point-H SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 31
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:128 memory:94330000-94331fff memory:94336000-943360ff ioport:6080(size=8) ioport:6088(size=4) ioport:6060(size=32) memory:94334000-943347ff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:7000(size=4096) memory:94200000-942fffff ioport:7c900000(size=2097152)
           *-generic
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:127 memory:94200000-94200fff
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 ioport:4000(size=4096) memory:94100000-941fffff
           *-network
                description: Wireless interface
                product: RTL8723BE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlo1
                version: 00
                serial: 18:4f:32:a1:aa:03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8723be driverversion=4.4.0-21-generic firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 ioport:4000(size=256) memory:94100000-94103fff
        *-pci:3
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 ioport:3000(size=4096) memory:94000000-940fffff
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eno1
                version: 0a
                serial: b0:5a:da:d5:2e:33
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8107e-2_0.0.2 02/26/15 ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:129 ioport:3000(size=256) memory:94004000-94004fff memory:94000000-94003fff
        *-isa
             description: ISA bridge
             product: Sunrise Point-H LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-H PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 31
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:9432c000-9432ffff
        *-multimedia
             description: Audio device
             product: Sunrise Point-H HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:133 memory:94328000-9432bfff memory:94310000-9431ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-H SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 31
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:94335000-943350ff ioport:6040(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG MZNLF128
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1H1Q
             serial: S2HUNXAG836074
             size: 119GiB (128GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=8130209d-cb2b-4427-a2cb-5f1be6d0fd2c logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: 9e5f-9cd1
                size: 255MiB
                capacity: 259MiB
                capabilities: boot precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat label=SYSTEM mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:1
                description: reserved partition
                vendor: Windows
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                serial: 31c5ba9e-05bb-4f66-810c-39eea4a14bb1
                capacity: 127MiB
                capabilities: nofs precious readonly hidden nomount
                configuration: name=Microsoft reserved partition
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: 30009556-0524-644e-a3dd-921bbc262c96
                size: 118GiB
                capacity: 118GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2015-08-29 08:34:46 filesystem=ntfs label=Windows name=Basic data partition state=clean
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: a4f8-c088
                size: 840MiB
                capacity: 862MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2016-01-10 03:42:47 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:1
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS541010A9
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: A710
             serial: JA1080SB0SVK2P
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=fd09d250-f1ab-463f-8b9d-90a9bcc9c61f logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: 4efe49d7-60b5-c24b-979a-40bab471e293
                size: 279GiB
                capacity: 279GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2015-10-01 11:18:29 filesystem=ntfs label=DATA name=Basic data partition state=clean
           *-volume:1
                description: Windows NTFS volume
                vendor: Windows
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                version: 3.1
                serial: cabde1a0-c9ea-9e44-b1ef-4f11e8bb9d28
                size: 16GiB
                capacity: 16GiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2015-10-01 11:18:34 filesystem=ntfs label=RECOVERY modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sdb3
                version: FAT32
                serial: c1d2-04f6
                size: 487MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI System Partition
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sdb4
                logical name: /
                version: 1.0
                serial: 41c00ae8-a35f-499e-8eb4-6f57e27e621b
                size: 619GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-05-03 11:23:25 filesystem=ext4 lastmountpoint=/ modified=2016-05-04 20:34:38 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-05-04 20:34:42 state=mounted
           *-volume:4
                description: Linux swap volume
                vendor: Linux
                physical id: 5
                bus info: scsi@2:0.0.0,5
                logical name: /dev/sdb5
                version: 1
                serial: 13ad6819-9463-464c-860a-704b4f929050
                size: 15GiB
                capacity: 15GiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:2
          physical id: 4
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW  SU208GB
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: HH00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc


```

---

