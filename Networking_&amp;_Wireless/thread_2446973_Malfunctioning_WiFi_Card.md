---
title: "Malfunctioning WiFi Card?"
date: 2020-07-10
forum: Networking &amp; Wireless
---

### Post by webmanoffesto on 2020-07-10
Recently I my WiFi just stopped. This is on an HP ProBook which until  recently would have WiFi for a few hours, or a couple of days, then the  WiFi would stop. But restarting the computer brought back the WiFi. Now  restarting the computer does not bring back WiFi. Pleases look at the  below output and tell me what you think the problem could be.

```


$ sudo iwconfig
lo        no wireless extensions.
enp2s0    no wireless extensions.

sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: 98:e7:f4:5e:1f:3a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.8 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:16 ioport:4000(size=256) memory:e2104000-e2104fff memory:e2100000-e2103fff

$ sudo lshw
ubuntu                    
    description: Notebook
    product: HP ProBook 450 G3 (Y6E48UT#ABA)
    vendor: HP
    serial: 5CD63927Q3
    width: 32 bits
    capabilities: smbios-2.7 dmi-2.7 smp
     configuration: administrator_password=disabled boot=normal  chassis=notebook family=103C_5336AN G=N L=BUS B=HP S=PRO  frontpanel_password=disabled keyboard_password=disabled  power-on_password=disabled sku=Y6E48UT#ABA  uuid=2441BB6B-CB85-E611-A34F-72ACB9008055
  *-core
       description: Motherboard
       product: 8101
       vendor: HP
       physical id: 0
       version: KBC Version 40.72
       serial: PFXJK028J442IO
     *-cache:0
          description: L1 cache
          physical id: 0
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: 1
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          physical id: 2
          slot: L2 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          physical id: 3
          slot: L3 Cache
          size: 3MiB
          capacity: 3MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.3
          serial: 0004-06E3-0000-0000-0000-0000
          slot: U3E1
          size: 1866MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse  sse2 ss ht tm pbe nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs  bts xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq  dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm sse4_1  sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand  lahf_lm abm 3dnowprefetch cpuid_fault epb ssbd ibrs ibpb stibp  tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep  bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt  xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify  hwp_act_window hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 id=3 threads=4
        *-logicalcpu:0
             description: Logical CPU
             physical id: 3.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 3.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 3.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 3.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 3.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 3.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 3.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 3.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 3.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 3.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 3.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 3.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 3.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 3.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 3.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 3.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 5
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM Synchronous 2133 MHz (0.5 ns)
             product: CT8G4SFS8213.M8FB
             vendor: Unknown - [0x9B85]
             physical id: 0
             serial: E01F3AF0
             slot: Bottom-Slot 1(top)
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: SODIMM Synchronous 2133 MHz (0.5 ns)
             product: M471A1K43BB0-CPB
             vendor: Samsung
             physical id: 1
             serial: 16A6F838
             slot: Bottom-Slot 2(under)
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
     *-firmware
          description: BIOS
          vendor: HP
          physical id: b
          version: N78 Ver. 01.39
          date: 04/16/2019
          size: 64KiB
          capacity: 15MiB
           capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd  int5printscreen int9keyboard int14serial int17printer acpi usb  smartbattery biosbootspecification netboot uefi
     *-pci
          description: Host bridge
          product: Sky Lake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Sky Lake Integrated Graphics
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:127 memory:e1000000-e1ffffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:123 memory:e2300000-e230ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.15.0-29-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: Cruzer
                   vendor: SanDisk
                   physical id: 4
                   bus info: usb@1:4
                   logical name: scsi3
                   version: 1.02
                   serial: 200607752113C0F0A48B
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@3:0.0.0
                      logical name: /dev/sdb
                      size: 29GiB (32GB)
                      capabilities: partitioned partitioned:dos
                      configuration: logicalsectorsize=512 sectorsize=512 signature=686a6515
                    *-volume:0
                         description: Windows FAT volume
                         vendor: SYSLINUX
                         physical id: 1
                         bus info: scsi@3:0.0.0,1
                         logical name: /dev/sdb1
                         logical name: /isodevice
                         version: FAT32
                         serial: 7f5d-e59c
                         size: 28GiB
                         capacity: 28GiB
                         capabilities: primary bootable fat initialized
                          configuration: FATs=2 filesystem=fat label=MULTISYSTEM  mount.fstype=vfat  mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro  state=mounted
                    *-volume:1
                         description: EXT4 volume
                         vendor: Linux
                         physical id: 2
                         bus info: scsi@3:0.0.0,2
                         logical name: /dev/sdb2
                         logical name: /media/ubuntu/Tom
                         version: 1.0
                         serial: eb47bc29-aa23-4b83-a52e-543930de014c
                         size: 1023MiB
                         capacity: 1023MiB
                          capabilities: primary journaled extended_attributes large_files  huge_files dir_nlink recover extents ext4 ext2 initialized
                          configuration: created=2018-11-16 18:10:05 filesystem=ext4 label=Tom  modified=2020-07-09 21:22:14 mount.fstype=ext4  mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2020-07-09  21:22:14 state=mounted
              *-usb:1
                   description: Video
                   product: HP HD Camera
                   vendor: DETNR019I39196
                   physical id: 6
                   bus info: usb@1:6
                   version: 0.09
                   serial: 200901010001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.15.0-29-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:e232a000-e232afff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:129 memory:e232b000-e232bfff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
              resources: irq:125 memory:e2328000-e2329fff memory:e232e000-e232e0ff  ioport:5080(size=8) ioport:5088(size=4) ioport:5040(size=32)  memory:e232c000-e232c7ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:120 ioport:3000(size=4096) memory:e2000000-e20fffff ioport:d0000000(size=270532608)
           *-display
                description: Display controller
                product: Topaz XT [Radeon R7 M260/M265]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 83
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=amdgpu latency=0
                 resources: irq:128 memory:d0000000-dfffffff memory:e0000000-e01fffff  ioport:3000(size=256) memory:e2000000-e203ffff memory:e2040000-e205ffff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:121 ioport:4000(size=4096) memory:e2100000-e21fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 15
                serial: 98:e7:f4:5e:1f:3a
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                 capabilities: pm msi pciexpress msix bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
                configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half  firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes  port=MII speed=10Mbit/s
                resources: irq:16 ioport:4000(size=256) memory:e2104000-e2104fff memory:e2100000-e2103fff
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:6000(size=4096) memory:e2200000-e22fffff ioport:be900000(size=2097152)
           *-generic
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:124 memory:e2200000-e2200fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:e2320000-e2323fff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:130 memory:e2324000-e2327fff memory:e2310000-e231ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e232d000-e232d0ff ioport:efa0(size=32)
     *-scsi:0
          physical id: 6
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 850
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2B6Q
             serial: S2RENXAH302583Z
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=0002d4c2
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: d1dc2540-fc44-47dc-a749-88e08be90b00
                size: 19GiB
                capacity: 19GiB
                 capabilities: primary bootable journaled extended_attributes  large_files huge_files dir_nlink extents ext4 ext2 initialized
                 configuration: created=2018-01-09 18:04:17 filesystem=ext4  lastmountpoint=/ modified=2020-07-09 21:21:32 mounted=2020-07-09  21:21:32 state=clean
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1.0
                serial: 670d08f8-498c-4ac5-ad0b-eddf64dc8534
                size: 880GiB
                capacity: 880GiB
                 capabilities: primary journaled extended_attributes large_files  huge_files dir_nlink extents ext4 ext2 initialized
                 configuration: created=2018-01-09 18:04:17 filesystem=ext4  lastmountpoint=/home modified=2020-07-09 21:21:32 mounted=2020-07-09  21:21:32 state=clean
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: f2c26c25-ac0d-46c7-af3a-21fafebb01ff
                size: 31GiB
                capacity: 31GiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
     *-scsi:1
          physical id: 7
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW  DU8A6SH
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: DH61
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: RI04041
       vendor: 13-54
       physical id: 1
       slot: Primary
       capacity: 34560mWh
       configuration: voltage=14.4V


ubuntu@ubuntu:~/Documents$ lspci
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1d.0 PCI bridge: Intel Corporation Device 9d18 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] (rev 83)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)



```

---

### Post by TheFu on 2020-07-10
It's dead, Jim.

Either 
[LIST=1]
[*]use the wired connection (free)
[*]get a replacement from HP (perhaps $50-$100) - hopefully just a few screws to replace, or
[*]buy a cheap usb wifi dongle ($10-$20) that is well-supported by linux out of the box.
[/LIST]

---

