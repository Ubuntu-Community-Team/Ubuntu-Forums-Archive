---
title: "New install -- No wifi drivers, no wifi icon, anything"
date: 2021-10-13
forum: Networking &amp; Wireless
---

### Post by completelymadeup on 2021-10-13
Hi!

I just installed Ubuntu (for the first time) on a brand new Lenovo Yoga 6, with a Ryzen 5 AMD chip. Ubuntu 20.04.3, Gnome 3.36.8.

Everything installed perfectly, **except** there is no wireless, at all. I looked at some forums and ran some commands, and basically confirmed this. 

I am only able to get it to connect via phone tethering (because it has no ethernet port). Can't seem to find appropriate drivers to install.

I don't have the terminal history (having restarted the computer and tried some BIOS boot stuff several times) and can't find the articles I followed, but I tried a number of commands that would ideally have unearthed some drivers, with no luck. Happy to try anything again. 

Thanks!

PS, some debugging attempts:

Some debugging attempts:

**lspci**
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Renoir IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe GPP Bridge
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe GPP Bridge
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 51)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 7
01:00.0 Non-Volatile memory controller: Sandisk Corp Device 5008 (rev 01)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8852
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 164c (rev c2)
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1637
03:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
03:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir USB 3.1
03:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir USB 3.1
03:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 01)
03:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
04:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 81)
04:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 81)

**sudo service network-manager restart**
(no effect)

[B]sudo lshw -C network
[/B]```
 *-network UNCLAIMED       
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:c0700000-c07fffff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@1:1
       logical name: usb0
       serial: 0a:85:f9:a1:25:d3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=5.11.0-27-generic firmware=RNDIS device ip=192.168.79.33 link=yes multicast=yes
```

**cat /etc/netplan/*.yaml**
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

[B]sudo lshw
[/B]```
me-yoga-6-13alc6            
    description: Convertible
    product: 82ND (LENOVO_MT_82ND_BU_idea_FM_Yoga 6 13ALC6)
    vendor: LENOVO
    version: Yoga 6 13ALC6
    serial: MP22XVJN
    width: 64 bits
    capabilities: smbios-3.3.0 dmi-3.3.0 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=convertible family=Yoga 6 13ALC6 frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=LENOVO_MT_82ND_BU_idea_FM_Yoga 6 13ALC6 uuid=4F89BBE6-7E0C-EC11-810C-7C8AE19C5DFB
  *-core
       description: Motherboard
       product: LNVNB161216
       vendor: LENOVO
       physical id: 0
       version: SDK0T76465 WIN
       serial: MP22XVJN
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: H6CN11WW(V1.04)
          date: 07/07/2021
          size: 128KiB
          capacity: 16MiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: AMD Ryzen 5 5500U with Radeon Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Ryzen 5 5500U with Radeon Graphics
          serial: Unknown
          slot: FP6
          size: 1568MHz
          capacity: 4056MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate ssbd mba ibrs ibpb stibp vmmcall fsgsbase bmi1 avx2 smep bmi2 cqm rdt_a rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local clzero irperf xsaveerptr rdpru wbnoinvd arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif umip rdpid overflow_recov succor smca cpufreq
          configuration: cores=6 enabledcores=6 threads=12
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 - Cache
             size: 384KiB
             capacity: 384KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 - Cache
             size: 3MiB
             capacity: 3MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 - Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: Row of chips DDR4 Synchronous Unbuffered (Unregistered) 3200 MHz (0.3 ns)
             product: HMA851S6DJR6N-XN
             vendor: Hynix
             physical id: 0
             serial: 00000000
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 3200MHz (0.3ns)
        *-bank:1
             description: Row of chips DDR4 Synchronous Unbuffered (Unregistered) 3200 MHz (0.3 ns)
             product: HMA851S6DJR6N-XN
             vendor: Hynix
             physical id: 1
             serial: 00000000
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 3200MHz (0.3ns)
     *-pci:0
          description: Host bridge
          product: Renoir Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: Renoir IOMMU
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: Renoir PCIe GPP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:34 memory:c0800000-c08fffff
           *-storage
                description: Non-Volatile memory controller
                product: Sandisk Corp
                vendor: Sandisk Corp
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi msix pciexpress nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:53 memory:c0800000-c0803fff memory:c0804000-c08040ff
              *-nvme0
                   description: NVMe device
                   product: WDC PC SN530 SDBPMPZ-256G-1101
                   physical id: 0
                   logical name: /dev/nvme0
                   version: 21160001
                   serial: 21225A807227
                   configuration: nqn=nqn.2018-01.com.wdc:guid:E8238FA6BF53-0001-001B448B414E4893 state=live
                 *-namespace
                      description: NVMe namespace
                      physical id: 1
                      logical name: /dev/nvme0n1
                      size: 238GiB (256GB)
                      capabilities: gpt-1.00 partitioned partitioned:gpt
                      configuration: guid=bc5180af-adbc-4978-b0f6-76fca9a6018c logicalsectorsize=512 sectorsize=512
                    *-volume:0 UNCLAIMED
                         description: Windows FAT volume
                         vendor: mkfs.fat
                         physical id: 1
                         version: FAT32
                         serial: 95e4-25bc
                         size: 510MiB
                         capacity: 511MiB
                         capabilities: boot fat initialized
                         configuration: FATs=2 filesystem=fat name=EFI System Partition
                    *-volume:1
                         description: EXT4 volume
                         vendor: Linux
                         physical id: 2
                         logical name: /dev/nvme0n1p2
                         logical name: /
                         version: 1.0
                         serial: fe9033e2-7195-43d8-a4f9-7e5045eda1a9
                         size: 237GiB
                         capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                         configuration: created=2021-10-12 17:21:45 filesystem=ext4 lastmountpoint=/ modified=2021-10-12 17:46:41 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2021-10-12 17:46:42 state=mounted
        *-pci:1
             description: PCI bridge
             product: Renoir PCIe GPP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.4
             bus info: pci@0000:00:02.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:35 ioport:2000(size=4096) memory:c0700000-c07fffff
           *-network UNCLAIMED
                description: Network controller
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: ioport:2000(size=256) memory:c0700000-c07fffff
        *-pci:2
             description: PCI bridge
             product: Renoir Internal PCIe GPP Bridge to Bus
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:36 ioport:1000(size=4096) memory:c0300000-c06fffff ioport:b0000000(size=270532608)
           *-display
                description: VGA compatible controller
                product: Advanced Micro Devices, Inc. [AMD/ATI]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:03:00.0
                version: c2
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix vga_controller bus_master cap_list rom
                configuration: driver=amdgpu latency=0
                resources: irq:56 memory:b0000000-bfffffff memory:c0000000-c01fffff ioport:1000(size=256) memory:c0600000-c067ffff memory:c0000-dffff
           *-multimedia:0
                description: Audio device
                product: Advanced Micro Devices, Inc. [AMD/ATI]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:89 memory:c06c8000-c06cbfff
           *-generic
                description: Encryption controller
                product: Family 17h (Models 10h-1fh) Platform Security Processor
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:03:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list
                configuration: driver=ccp latency=0
                resources: irq:53 memory:c0500000-c05fffff memory:c06cc000-c06cdfff
           *-usb:0
                description: USB controller
                product: Renoir USB 3.1
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:03:00.3
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:41 memory:c0300000-c03fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.11.0-27-generic xhci-hcd
                   physical id: 0
                   bus info: usb@1
                   logical name: usb1
                   version: 5.11
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Wireless interface
                      product: Pixel 3a
                      vendor: Google
                      physical id: 1
                      bus info: usb@1:1
                      version: 4.40
                      serial: 937AY07PZP
                      capabilities: usb-2.00
                      configuration: driver=rndis_host maxpower=500mA speed=480Mbit/s
                 *-usb:1
                      description: Video
                      product: Integrated Camera
                      vendor: Chicony Electronics Co.,Ltd.
                      physical id: 3
                      bus info: usb@1:3
                      version: 26.83
                      serial: 0001
                      capabilities: usb-2.01
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.11.0-27-generic xhci-hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 5.11
                   capabilities: usb-3.10
                   configuration: driver=hub slots=2 speed=10000Mbit/s
           *-usb:1
                description: USB controller
                product: Renoir USB 3.1
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.4
                bus info: pci@0000:03:00.4
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:56 memory:c0400000-c04fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.11.0-27-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 5.11
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Mass storage device
                      product: Infinitive
                      vendor: Walgreens
                      physical id: 2
                      bus info: usb@3:2
                      version: 1.00
                      serial: 03027224052521073511
                      capabilities: usb-2.00 scsi
                      configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-usb:1 UNCLAIMED
                      description: Generic USB device
                      product: Goodix FingerPrint Device
                      vendor: Generic
                      physical id: 3
                      bus info: usb@3:3
                      version: 1.00
                      capabilities: usb-2.00
                      configuration: maxpower=100mA speed=480Mbit/s
                 *-usb:2
                      description: Bluetooth wireless interface
                      product: Bluetooth Radio
                      vendor: Realtek
                      physical id: 4
                      bus info: usb@3:4
                      version: 0.00
                      serial: 00e04c000001
                      capabilities: bluetooth usb-1.00
                      configuration: driver=btusb maxpower=500mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.11.0-27-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 5.11
                   capabilities: usb-3.10
                   configuration: driver=hub slots=2 speed=10000Mbit/s
           *-multimedia:1
                description: Multimedia controller
                product: Raven/Raven2/FireFlight/Renoir Audio Processor
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.5
                bus info: pci@0000:03:00.5
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_rn_pci_acp3x latency=0
                resources: irq:84 memory:c0680000-c06bffff
           *-multimedia:2
                description: Audio device
                product: Family 17h (Models 10h-1fh) HD Audio Controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.6
                bus info: pci@0000:03:00.6
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:55 memory:c06c0000-c06c7fff
        *-pci:3
             description: PCI bridge
             product: Renoir Internal PCIe GPP Bridge to Bus
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:37 memory:c0200000-c02fffff
           *-sata:0
                description: SATA controller
                product: FCH SATA Controller [AHCI mode]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 81
                width: 32 bits
                clock: 33MHz
                capabilities: sata pm pciexpress msi ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:51 memory:c0201000-c02017ff
           *-sata:1
                description: SATA controller
                product: FCH SATA Controller [AHCI mode]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: 81
                width: 32 bits
                clock: 33MHz
                capabilities: sata pm pciexpress msi ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:54 memory:c0200000-c02007ff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 51
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 51
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Renoir PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Renoir PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Renoir PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:08.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Renoir Device 24: Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Renoir Device 24: Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Renoir Device 24: Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Renoir Device 24: Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Renoir Device 24: Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Renoir Device 24: Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Renoir Device 24: Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10a
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Renoir Device 24: Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10b
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pnp00:00
          product: PnP device PNP0c02
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0b00
          physical id: 2
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:02
          product: PnP device FUJ7401
          physical id: 3
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 5
          capabilities: pnp
          configuration: driver=system
     *-pnp00:04
          product: PnP device PNP0c01
          physical id: 6
          capabilities: pnp
          configuration: driver=system
     *-scsi
          physical id: 7
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Infinitive
             vendor: Walgreen
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 1.00
             serial: 03027224052521073511
             size: 28GiB (30GB)
             capabilities: removable
             configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sda
                size: 28GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=000358c0
              *-volume
                   description: Windows FAT volume
                   vendor: SYSLINUX
                   physical id: 1
                   logical name: /dev/sda1
                   logical name: /media/me/UBUNTU 20_0
                   version: FAT32
                   serial: 7cd7-cb58
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=UBUNTU 20_0 mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-battery
       description: Zinc Air Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 08/08/2010
       serial: Battery 0
       slot: Fake
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@1:1
       logical name: usb0
       serial: 0a:85:f9:a1:25:d3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=5.11.0-27-generic firmware=RNDIS device ip=192.168.79.33 link=yes multicast=yes
```

---

### Post by TheFu on 2021-10-14
Really new hardware seldom has great support by any Linux when first released.  I try to buy 1-2 yr old laptops and check out the actual chips used for the key components to be 100% certain they are supported in the kernel, without any drivers to be manually added, downloaded, or maintained.  I learned this over decades.

New is the enemy of "supported."

Did you look up the exact wifi chip used?

I don't use wifi much - actually in my laptop, I only use it outside the house. Inside the house, I have $20 USB3-to-GigE adapter that "just works".  That adapter adds 3 more USB3 ports in addition to the GigE adapter.

To get the wifi chip used can be a challenge. Try these commands:
[LIST]
[*]lspci -vk |egrep --after-context=8 'Ethernet|Network'
[*]lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
[*]sudo lsusb -v  |egrep 'Ether|Network'
[*]lsmod |grep usbnet
[*]inxi -Nxx
[*]sudo lshw -sanitize -C network
[/LIST]

One of those should work.

```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8852
```
Based on some of the other output, it appears the driver isn't shipped [https://askubuntu.com/questions/1336379/network-driver-for-realtek-8852-20-10](https://askubuntu.com/questions/1336379/network-driver-for-realtek-8852-20-10) has some steps for a solution. Seems you'll need to narrow down the exact version of this wifi adapter to manually pick the correct driver, since Realtek makes a few different versions of the 8852.

Good luck.  I try to only get Intel network adapters ... wifi or wired. This avoids most issues, I've found, assuming the NIC isn't too new.

---

