---
title: "Ubuntu 9.10 Empathy issues"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by maxmouse24 on 2010-04-28
I have two computers with Ubuntu 9.10 installed.

My GF and I use Empathy to video chat. (she is in another state)

Problems are that her CPU maxes out almost, every time we start a video chat.

Also the audio and video is majorly cutting out. 

She is on a 5Mb/sec connection (IN)
I am on a 3Mb/sec connection (OK)

any ideas. it is aggravating.

---

### Post by spydeyrch on 2010-04-28
Do you know what her computer specs are? That would be helpful to start things off.  :)

Also, what other programs does she typically have running in the background while she is running empathy?

-Spydey :lolflag:

---

### Post by maxmouse24 on 2010-04-28
tell me the command to type in and I will ssh in and get the info. all she ever runs is empathy when we chat

---

### Post by skyeric on 2010-04-28
```
 sudo lshw 
``` will give you a very detailed system spec

---

### Post by LowSky on 2010-04-28
Have you tried Skype?

---

### Post by maxmouse24 on 2010-04-28
how do I have that put it in a text document?

---

### Post by maxmouse24 on 2010-04-28
skype is worse

---

### Post by LowSky on 2010-04-28
> **maxmouse24 said:**
> how do I have that put it in a text document?

copy the data, open gedit, paste


or just copy the info to here and use [CODE] tags

---

### Post by maxmouse24 on 2010-04-28
This is the output from my system I will include hers in a couple of hours. (I blanked my IP)


```
    

    description: Desktop Computer
    product: PCV-RS520(UC)
    vendor: Sony Corporation
    version: 28005431
    serial: 3005320
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=E0321B4D-3944-D811-A4F7-000EA65979BD
  *-core
       description: Motherboard
       product: P4SD-VL
       vendor: ASUSTek Computer Inc.
       physical id: 0
       version: To be filled by O.E.M.
       serial: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1002 (01/28/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.3
          serial: 0000-0F33-0000-0000-0000-0000
          slot: CPU 1
          size: 3GHz
          capacity: 3GHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid
          configuration: id=1
        *-cache
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 2a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 512MiB
             width: 64 bits
        *-bank:3
             description: DIMM SDRAM Synchronous
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:8000(size=4096) memory:fe900000-fe9fffff memory:d7f00000-f7efffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RV280 [Radeon 9200]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: memory:e0000000-efffffff(prefetchable) ioport:8800(size=256) memory:fe9f0000-fe9fffff memory:fe9c0000-fe9dffff(prefetchable)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e000(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e400(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ec00(size=32)
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:febffc00-febfffff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=8192) memory:fea00000-feafffff memory:80000000-800fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 02
                serial: 00:0e:a6:59:79:bd
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=xxx.xxx.xxx.xxx latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:20 memory:feaff000-feafffff ioport:ac00(size=64)
           *-storage
                description: Mass storage controller
                product: HPT366/368/370/370A/372/372N
                vendor: HighPoint Technologies, Inc.
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: scsi2
                logical name: scsi3
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list rom emulated
                configuration: driver=pata_hpt37x latency=120 maxlatency=8 mingnt=8
                resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=256) memory:80000000-8001ffff(prefetchable)
              *-disk:0
                   description: ATA Disk
                   product: Maxtor 6Y250P0
                   vendor: Maxtor
                   physical id: 0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/sdb
                   version: YAR4
                   serial: Y62F3KFE
                   size: 233GiB (251GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=048fac46
                 *-volume
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: scsi@2:0.0.0,1
                      logical name: /dev/sdb1
                      capacity: 467GiB
                      capabilities: primary
              *-disk:1
                   description: ATA Disk
                   product: Maxtor 6Y250P0
                   vendor: Maxtor
                   physical id: 1
                   bus info: scsi@3:0.0.0
                   logical name: /dev/sdc
                   version: YAR4
                   serial: Y62DHZVE
                   size: 233GiB (251GB)
                   configuration: ansiversion=5
           *-firewire
                description: FireWire (IEEE 1394)
                product: uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr
                vendor: NEC Corporation
                physical id: e
                bus info: pci@0000:02:0e.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=44 mingnt=20
                resources: irq:18 memory:feafd000-feafdfff
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16) memory:80100000-801003ff
           *-disk
                description: ATA Disk
                product: WDC WD1600BB-98D
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 15.0
                serial: WD-WMAEK2251334
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b854d39b
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 64378df0-d562-d743-9220-7d0c252721c9
                   size: 6149MiB
                   capacity: 6149MiB
                   capabilities: primary boot ntfs initialized
                   configuration: clustersize=2048 created=2003-10-22 19:44:35 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 86b5043f-4da6-0440-af80-7dec24cd9d52
                   size: 39GiB
                   capacity: 40GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2003-12-01 18:24:37 filesystem=ntfs state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 103GiB
                   capacity: 103GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 9538MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 93GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
           *-cdrom:0
                description: DVD-RAM writer
                product: DVD-RAM GSA-H55N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                serial: [HL-DT-STDVD-RAM GSA-H55N1.0307/08/17 7U02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM GDR8162B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 0015
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:d400(size=256) ioport:d000(size=64) memory:febff800-febff9ff memory:febff400-febff4ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:d800(size=256) ioport:dc00(size=128)

```

---

### Post by maxmouse24 on 2010-04-28
I should clarify

the audio/video cut out is on both computers

---

### Post by maxmouse24 on 2010-04-28
here is the information for the other computer. 

```

description: Notebook
    product: HP G60 Notebook PC
    vendor: Hewlett-Packard
    version: F.33
    serial: 2CE8493YF0
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=370B8320-C7FA-11DD-9FF1-A493484883B9
  *-core
       description: Motherboard
       product: 303C
       vendor: Wistron
       physical id: 0
       version: 08.48
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.33 (12/02/2008)
          size: 102KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Turion Dual-Core RM-70
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.3.1
          slot: Socket A
          size: 500MHz
          capacity: 2GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: S1
             size: 2GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: S2
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 5
          bus info: cpu@1
          version: 15.3.1
          size: 500MHz
          capacity: 500MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1a00(size=256)
     *-serial
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP78S [GeForce 8200] Co-Processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:c0080000-c00fffff
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.4
          bus info: pci@0000:00:01.4
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0006000-c0006fff
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0007000-c00070ff
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0008000-c0008fff
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0007400-c00074ff
     *-ide:0
          description: IDE interface
          product: MCP78S [GeForce 8200] IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30c0(size=16)
     *-multimedia
          description: Audio device
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:c0000000-c0003fff
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
     *-ide:1
          description: IDE interface
          product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:25 ioport:30f0(size=8) ioport:30e4(size=4) ioport:30e8(size=8) ioport:30e0(size=4) ioport:30d0(size=16) memory:c0004000-c0005fff
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-L633L
             vendor: TSSTcorp
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 0400
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: WDC WD2500BEVT-6
             vendor: Western Digital
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 13.0
             serial: WD-WXEX08RFF080
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=fd03d783
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 37f4c39f-d26d-48eb-a2b9-cb925f665139
                size: 224GiB
                capacity: 224GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2010-04-25 21:28:13 filesystem=ext4 lastmountpoint=/ï¿½7ï¿½ï¿½ï¿½ï¿½ï¿½Bï¿½ï¿½ï¿½ï¿½ï¿½ï¿½xï¿½I^ï¿½pï¿½ï¿½ïï¿½ï¿½pï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ïï¿½ï¿½ï¿½`ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½%ï¿½ï¿½ modified=2010-04-25 21:48:02 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-04-28 06:48:04 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 8118MiB
                capacity: 8118MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8118MiB
                   capabilities: nofs
     *-network
          description: Ethernet interface
          product: MCP77 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1f:16:51:9a:fc
          capacity: 100MB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm ht bus_master cap_list
          resources: ioport:4000(size=4096) memory:c1000000-c1ffffff ioport:c4000000(size=469762048)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: C77 [GeForce 8200M G]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:c1000000-c1ffffff memory:d0000000-dfffffff(prefetchable) memory:c4000000-c5ffffff(prefetchable) ioport:4000(size=128) memory:c6000000-c601ffff(prefetchable)
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:24 memory:c2000000-c20fffff
        *-network
             description: Wireless interface
             product: AR928X Wireless Network Adapter (PCI-Express)
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wlan0
             version: 01
             serial: 00:23:4e:47:43:a8
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath9k ip=XXX.XXX.XXX.XXX latency=0 multicast=yes wireless=IEEE 802.11abgn
             resources: irq:23 memory:c2000000-c200ffff
     *-pci:3
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h [Turion X2, Athlon X2, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: d
          bus info: usb@1:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb


```

---

### Post by LowSky on 2010-04-28
After looking at both PC's parts you shouldn't have any issue running video camera's.

Heck if my Netbook with it 1.6GHz processor and nearly no graphics can use Skype without a problem. I can't see the application being an issue on either of your computers.

You did ay you useing Empathy but you didn't say with what service? Google, MSN, or something else?

I know support is somewhat flimsy on video chat at this time, MSN especially.

---

### Post by maxmouse24 on 2010-04-28
we created gtalk accounts. the video and audio cut out much like network dropout video pixalates and we have to repeat what we say quite a bit. also her cpu on the system monitor is always running 70% - 100% mine consistently runs at around 40%

---

### Post by maxmouse24 on 2010-04-28
bump

---

