---
title: "Ubuntu 10.4 simply freezes on IBM T42 laptop"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by montage9 on 2010-05-22
Hi,

Sometimes immediately after starting the computer, the OS freezes, i.e, no keyboard control or mouse, the only way to recover is to hard reboot the machine. This has started happening quite frequently, I don't know whether this is a hardware or software problem. The machine previously has windows XP professional and it never once behaved in this fashion, so I am suspecting it is software problem. Pl. tell me how to troubleshoot further. Thanks.

---

### Post by -humanaut- on 2010-05-22
I'm not familiar with the T42 can you open a terminal type: sudo lshw 

and post back?

---

### Post by tgalati4 on 2010-05-22
T42's and other T-series are known for GPU delamination problems.  It's possible that putting Ubuntu on it has stressed the graphics chip to the point of freezing.  Windows drivers seem to be less stressing on the graphics chip and therefore work longer before problems begin.

Is this machine dual boot?  Did you try booting with a Live CD?

I have a T43p with a later model ATI graphics chip.  I have it monitored and it does get toasty playing neverball or anything 3D.  I'm using dynamic clocks and tpfan to crank the fan when the temperatures reach 70C.

So I think you are right, this is probably a combination of hardware and software problems.

Can you boot into recovery mode?  If so, then stay in that mode for a while to check for stability.  Also run memtest to check your ram.

---

### Post by montage9 on 2010-05-23
*-core
       description: Motherboard
       product: 23739XU
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: J1YPL53R2JJ
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 1RETDIWW (3.14 ) (01/20/2005)
          size: 144KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.80GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.13.6
          slot: None
          size: 1800MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-dfffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:3000(size=4096) memory:c0100000-c01fffff memory:e0000000-e7ffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: RV350 [Mobility Radeon 9600 M10]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:11 memory:e0000000-e7ffffff(prefetchable) ioport:3000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1820(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1840(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:c0000000-c00003ff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:4000(size=20480) memory:c0200000-cfffffff memory:e8000000-efffffff(prefetchable)
           *-pcmcia:0
                description: CardBus bridge
                product: PCI4520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:b0000000-b0000fff ioport:4000(size=256) ioport:4400(size=256) memory:e8000000-ebffffff(prefetchable) memory:c4000000-c7ffffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI4520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:b1000000-b1000fff ioport:4800(size=256) ioport:4c00(size=256) memory:ec000000-efffffff(prefetchable) memory:c8000000-cbffffff
           *-network:0
                description: Ethernet interface
                product: 82540EP Gigabit Ethernet Controller (Mobile)
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 03
                serial: 00:11:25:86:e9:05
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
                resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8000(size=64) memory:c0240000-c024ffff(prefetchable)
           *-network:1
                description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: wlan0
                version: 01
                serial: 00:05:4e:4e:b8:33
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k ip=192.168.1.4 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11abg
                resources: irq:11 memory:c0210000-c021ffff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1860(size=16) memory:80000000-800003ff
           *-disk
                description: ATA Disk
                product: FUJITSU MHT2080A
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8471
                serial: NP0KT5326Y1G
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000196f
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 289ee58f-6934-4076-9ddf-97563f2a54db
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-09 13:55:40 filesystem=ext4 lastmountpoint=/G&#65533;&#65533;Q&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;3&#65533;&#65533;&#65533;&#65533;2&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;u^ &#65533;U/&#65533;d&#65533;&#65533;&#65533;&#65533;&#65533;~!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;a modified=2010-05-22 23:20:38 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-22 23:20:38 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3152MiB
                   capacity: 3152MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3152MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: UJDA765 DVD/CDRW
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:11 ioport:1c00(size=256) ioport:18c0(size=64) memory:c0000c00-c0000dff memory:c0000800-c00008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)

---

### Post by montage9 on 2010-05-23
The freeze happens within few min of boot up, I don't play any games or heavy user of the graphics chip, just regular browser etc. No fancy applications. I had ubuntu 9.10 before and that too showed similar problems, that is why I upgraded to 10.4, but to no avail, I think I should switch back to WinXP now, atleast the computer was functional.

---

### Post by tgalati4 on 2010-05-23
Install WinXP and play any 3D game.  If the computer locks up then you know you have a GPU problem.  The open ATI radeon driver should work OK with the 9600 card.  So I don't think it's a video driver problem.

---

