---
title: "Ubuntu MATE - No Ethernet Adapter - Acer Aspire 6930."
date: 2017-08-05
forum: Networking &amp; Wireless
---

### Post by computer0freek on 2017-08-05
Hey Guys,

I've had Ubuntu Mate installed for a while now on my Acer Aspire 6940. I had Ubuntu MATE 16.10 (I believe) and I upgraded to Ubuntu MATE 17.04. The ethernet adapter did not work in either version. I've used Ubuntu pre 16.10 on this laptop with no issue with the Ethernet or wireless adapters. The wireless adapter works fine but I'm unable to control the Ethernet within "Network Connections". 

**IFCONFIG Output:**

```
root@Freek:~# ifconfig -a
enp9s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 00:23:8b:a2:b9:d1  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1930  bytes 127731 (127.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1930  bytes 127731 (127.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp7s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.1.116  netmask 255.255.255.0  broadcast 10.0.1.255
        inet6 fe80::e43e:d385:62de:8bf3  prefixlen 64  scopeid 0x20<link>
        ether 00:22:fa:04:be:a2  txqueuelen 1000  (Ethernet)
        RX packets 368491  bytes 477806226 (477.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 127248  bytes 15611245 (15.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

[B]
sudo lshw output[/B]

```
freek
    description: Computer
    product: Aspire 6930G
    vendor: Acer
    version: Not Applicable
    serial: LXABL0X013915010952500
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 smp vsyscall32
    configuration: administrator_password=disabled boot=normal frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=40957AC0-27B2-DC11-B0F7-00238BA2B9D1
  *-core
       description: Motherboard
       product: Makalu
       vendor: Acer
       physical id: 0
       version: Not Applicable
       serial: 913CSFMBQTF002D6
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: v0.3236
          date: 03/10/2009
          size: 108KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: CPU Version
          slot: U2E1
          size: 2801MHz
          capacity: 2801MHz
          width: 64 bits
          clock: 266MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority dtherm ida cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 6MiB
             capabilities: burst internal write-back unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:cc000000-ceffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G96M [GeForce 9600M GS]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:30 memory:ce000000-ceffffff memory:d0000000-dfffffff memory:cc000000-cdffffff ioport:2000(size=128) memory:c0000-dffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-30-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1820(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-30-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: Bluetooth wireless interface
                   product: BCM2046 Bluetooth Device
                   vendor: Broadcom Corp
                   physical id: 1
                   bus info: usb@4:1
                   version: 8.56
                   serial: 00265E9BD969
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: Fingerprint Sensor
                   vendor: TouchStrip
                   physical id: 2
                   bus info: usb@4:2
                   version: 0.33
                   capabilities: usb-1.00
                   configuration: maxpower=100mA speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-30-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:f0404000-f04043ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.10.0-30-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.10
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: USB2.0-CRW
                   vendor: Generic
                   physical id: 2
                   bus info: usb@1:2
                   logical name: scsi4
                   version: 58.87
                   serial: 20071114173400000
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=ums-realtek maxpower=500mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Multi-Card
                      vendor: Generic-
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/sdc
                      version: 1.00
                      capabilities: removable
                      configuration: logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sdc
              *-usb:1
                   description: Video
                   product: Acer Crystal Eye webcam
                   vendor: SuYin
                   physical id: 6
                   bus info: usb@1:6
                   version: 1.00
                   serial: CN0314-SN30-OV03-VA-R02.03.02
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
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
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:f0400000-f0403fff
        *-pci:1
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
             resources: irq:25 ioport:3000(size=4096) memory:c0000000-c01fffff ioport:c0200000(size=2097152)
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
             resources: irq:26 ioport:4000(size=4096) memory:c0400000-c06fffff ioport:c0700000(size=2097152)
           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlp7s0
                version: 00
                serial: 00:22:fa:04:be:a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-30-generic firmware=8.83.5.1 build 33692 ip=10.0.1.116 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:28 memory:c0400000-c0401fff
        *-pci:3
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
             resources: irq:27 ioport:5000(size=4096) memory:c0900000-c0bfffff ioport:c0c00000(size=2097152)
           *-network DISABLED
                description: Ethernet interface
                product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: enp9s0
                version: b0
                serial: 00:23:8b:a2:b9:d1
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
                resources: irq:17 memory:c0900000-c093ffff ioport:5000(size=128)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-30-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-30-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18a0(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-30-generic uhci_hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f0404400-f04047ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.10.0-30-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.10
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
        *-pci:4
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
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:18f0(size=8) ioport:18e4(size=4) ioport:18e8(size=8) ioport:18e0(size=4) ioport:18d0(size=16) ioport:18c0(size=16)
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
             resources: memory:c0e00000-c0e000ff ioport:1c00(size=32)
        *-ide:1
             description: IDE interface
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1c48(size=8) ioport:18fc(size=4) ioport:1c40(size=8) ioport:18f8(size=4) ioport:1c30(size=16) ioport:1c20(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA-TL100
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 10.1
             serial: Y6QB30OSKKEU
             size: 223GiB (240GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=eef4ec01
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: b13d8f2a-aee0-4f95-8ef6-6081a36208d7
                size: 219GiB
                capacity: 219GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2017-07-15 22:41:11 filesystem=ext4 lastmountpoint=/ modified=2017-08-05 19:09:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-08-04 14:26:08 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 4060MiB
                capacity: 4060MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap volume
                   physical id: 5
                   logical name: /dev/sda5
                   version: 1
                   serial: 0d44f203-67e0-4a86-b5b3-06ef483dfb89
                   size: 4060MiB
                   capacity: 4060MiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT32N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: AS01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000LM024 HN-M
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 0003
             serial: S2RUJ9KD305045
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=38999fc9
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /home/data
                version: 1.0
                serial: b2251406-07dd-47b6-92d7-4a1df8410a32
                size: 931GiB
                capacity: 931GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2017-07-15 23:20:06 filesystem=ext4 lastmountpoint=/home/data modified=2017-08-05 19:09:35 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2017-08-05 19:09:35 state=mounted
  *-battery
       description: Lithium Ion Battery
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1
       slot: Rear
       capacity: 1000mWh
       configuration: voltage=0.0V
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 2
       capabilities: outbound
```

[B]Also see screen shot of the network connections.
[/B][ATTACH=CONFIG]276271[/ATTACH]

Thank you guys in advance in regards to helping me get my network adapter working. I'm kind of at a loss at the moment. 

Kyle

---

### Post by cariboo on 2017-08-05
Try:

```
sudo lshw -C network
```

as your ifconfig does show an Ethernet adaptor /dev/enp9s0

---

### Post by computer0freek on 2017-08-05
RUH-ROH - 

> root@Freek:~# lshw -C networks
root@Freek:~# lshw -C networks
root@Freek:~# exit          
exit
kyle@Freek:~$ sudo lshw -C networks
[sudo] password for kyle: 
kyle@Freek:~$ sudo lshw -c networks
kyle@Freek:~$ sudo lshw -C Networks
kyle@Freek:~$     


So according to that - I don't have any network adapters :)

---

### Post by praseodym on 2017-08-06
You have:
> 
```
           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlp7s0
                version: 00
                serial: 00:22:fa:04:be:a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-30-generic firmware=8.83.5.1 build 33692 ip=10.0.1.116 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:28 memory:c0400000-c0401fff
...
           *-network DISABLED
                description: Ethernet interface
                product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: enp9s0
                version: b0
                serial: 00:23:8b:a2:b9:d1
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
                resources: irq:17 memory:c0900000-c093ffff ioport:5000(size=128)
```

Please show:

There is a bug in 17.04. Please run these 2 commands and reboot

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by cariboo on 2017-08-06
> **computer0freek said:**
> RUH-ROH - 



So according to that - I don't have any network adapters :)

sorry about that, there was a spelling error in my post, the command should be:

```
sudo lshw -C network
```

**Note:** You don't need to use sudo if you are running as root.

---

### Post by computer0freek on 2017-08-11
> **praseodym said:**
> You have:


Please show:

There is a bug in 17.04. Please run these 2 commands and reboot

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```


Thanks Praseodym and cariboo for the responses. Sorry it has taken me so long to get back with you guys. I've been really really busy! 

Please see below for the output within the terminal. After the reboot - no change with Ethernet Adapter. 

```
kyle@Freek:~$ echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
[sudo] password for kyle: 

[device]
wifi.scan-rand-mac-address=no
kyle@Freek:~$ sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
kyle@Freek:~$ sudo lshw -C network
  *-network                 
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: 00
       serial: 00:22:fa:04:be:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-30-generic firmware=8.83.5.1 build 33692 ip=192.168.200.150 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:28 memory:c0400000-c0401fff
  *-network DISABLED
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: enp9s0
       version: b0
       serial: 00:23:8b:a2:b9:d1
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:c0900000-c093ffff ioport:5000(size=128)
kyle@Freek:~$ 


```
Kyle

---

### Post by praseodym on 2017-08-11
Driver is loaded?
```

sudo modprobe -v atl1e
```

---

### Post by chili555 on 2017-08-11
> *-network DISABLED
                description: Ethernet interface
                product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
                vendor: Qualcomm Atheros[I]Disabled? 
[/I]
Please run and post:```
dmesg | grep -e atl -e enp
```

---

### Post by computer0freek on 2017-08-14
Thanks Guys: 

See below results: 

> kyle@Freek:~$ sudo modprobe -v atl1e
kyle@Freek:~$ sudo modprobe -v atl1e
kyle@Freek:~$ dmesg | grep -e atl -e enp
[    1.612940] ATL1E 0000:09:00.0 enp9s0: renamed from eth0

Thanks,
Kyle

---

### Post by computer0freek on 2017-08-16
Bump :)

---

### Post by computer0freek on 2017-08-30
I tried a reinstall of Ubuntu with the same problem. I reverted back to my Windows 10 image - no problem. Reinstalled Ubuntu Mate and the problem still remains.

---

### Post by chili555 on 2017-08-30
I am still quite mystified as to why and how an ethernet interface can be disabled:> *-network [COLOR="#FF0000"]DISABLED[/COLOR]
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: enp9s0
       version: b0
       serial: 00:23:8b:a2:b9:d1
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
<snip>Let's see if there is any clue by looking at the log concerning the pci bus:```
dmesg | grep 09:00
```Will you please try setting the BIOS to defaults?

I'm puzzled.

---

### Post by computer0freek on 2018-05-02
Forgot this thread was open. I ended up installing the older version of Ubuntu Mate and the installing updates. After all updates were installed - i then upgraded the os to the lastest. Closing Ticket.

---

