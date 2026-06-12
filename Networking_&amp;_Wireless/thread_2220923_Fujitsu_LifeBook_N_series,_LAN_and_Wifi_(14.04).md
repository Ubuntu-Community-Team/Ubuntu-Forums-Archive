---
title: "Fujitsu LifeBook N series, LAN and Wifi (14.04)"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by drjoeross on 2014-04-29
Greetings I have a Fujitsu lifebook N series in great shape with pentium 4   3 gighertz proccessor and 2 gigs of ram.  I have installed Ubuntu 32 bit but it does NOT recognize the Lan card (realTek) or the wireless Card (Atheros).  There are also reported System Errors to be reported but of course cannot. This is my first ever failure with any version of Ubuntu.  I even tried Debian and Xubuntu, these did not work either so I guess the issues is common with linux installs and this notebook. 

On boot up,  I have seen a message about IRQ Conflict?  I think... it came across the screen once on boot up but very fast. The only other message I have seen what was odd, was that the Radeon (900?)  hardware acceleration was turned off....something like that as Ubuntu started to boot.

.  I re-installed win xp and it is fine everything works but I don't want xp.  
 Any suggestions?
Thanks,
Joe

---

### Post by Ubi_one_2014 on 2014-04-29
type i a console lshw[enter]
and post the outpur here,

---

### Post by drjoeross on 2014-04-30
Greetings thanks for you offer of assistance.  I Re-Installed Ubuntu,  but it still does not connect to either the plugged in EtherNet or the available wireless.  Here are the results you asked for run as lshw  and  afterwards  sudo lshw
thanks,
Joe


TERMINAL LSHW COMMAND AS SUDO
-----------------------------------------
```
drjoeross@JoeUbuntuLT:~$ sudo lshw
[sudo] password for drjoeross: 
joeubuntult               
    description: Notebook
    product: FPC06017AK
    vendor: FUJITSU
    serial: R4208760
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.3 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1 uuid=00000000-0000-0000-0000-000B5D2C1A7C
  *-core
       description: Motherboard
       product: CYGNUS
       vendor: FUJITSU
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix/FUJITSU
          physical id: 0
          version: 1.24
          date: 02/06/2004
          size: 121KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: On Board
          size: 3GHz
          capacity: 3060MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: pipeline-burst synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst synchronous internal write-back unified
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
          physical id: d
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM SDRAM
             physical id: 0
             slot: DIMM1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM
             physical id: 1
             slot: DIMM2
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 645xx
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 51
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=64
          resources: irq:0 memory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:a000(size=4096) memory:ec100000-ec1fffff memory:f0000000-f7ffffff
           *-display
                description: VGA compatible controller
                product: RV350/M10 [Mobility Radeon 9600 PRO Turbo]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:0 memory:f0000000-f7ffffff ioport:a000(size=256) memory:ec100000-ec10ffff memory:ec120000-ec13ffff
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2/3 SMBus controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:9000(size=32)
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1000(size=16)
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=173 maxlatency=11 mingnt=52
             resources: ioport:1400(size=256) ioport:1080(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=173 maxlatency=11 mingnt=52
             resources: irq:18 ioport:1c00(size=256) ioport:1800(size=128)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:20 memory:ec000000-ec000fff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:21 memory:ec001000-ec001fff
        *-usb:2
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64 maxlatency=80
             resources: irq:23 memory:ec002000-ec002fff
        *-network:0 DISABLED
             description: Ethernet interface
             product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 7
             bus info: pci@0000:00:07.0
             logical name: eth0
             version: 10
             serial: 00:0b:5d:2c:1a:7c
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
             resources: irq:0 ioport:2000(size=256) memory:ec003000-ec0030ff memory:80010000-8001ffff
        *-pcmcia:0
             description: CardBus bridge
             product: PCI7420 CardBus Controller
             vendor: Texas Instruments
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:16 memory:80000000-80000fff ioport:2400(size=256) ioport:2800(size=256) memory:84000000-87ffffff memory:88000000-8bffffff
        *-pcmcia:1
             description: CardBus bridge
             product: PCI7420 CardBus Controller
             vendor: Texas Instruments
             physical id: 9.1
             bus info: pci@0000:00:09.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:17 memory:8c000000-8c000fff ioport:2c00(size=256) ioport:3000(size=256) memory:90000000-93ffffff memory:94000000-97ffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
             vendor: Texas Instruments
             physical id: 9.2
             bus info: pci@0000:00:09.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:18 memory:ec003800-ec003fff memory:ec004000-ec007fff
        *-storage UNCLAIMED
             description: Mass storage controller
             product: PCI7420/7620 SD/MS-Pro Controller
             vendor: Texas Instruments
             physical id: 9.3
             bus info: pci@0000:00:09.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm cap_list
             configuration: latency=64 maxlatency=4 mingnt=7
             resources: memory:ec008000-ec008fff
        *-network:1
             description: Wireless interface
             product: AR5212/AR5213 Wireless Network Adapter
             vendor: Qualcomm Atheros
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: wlan0
             version: 01
             serial: 00:90:96:77:d4:81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=3.13.0-24-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11abg
             resources: irq:18 memory:ec010000-ec01ffff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600BEVE-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WXC708980084
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000c564f
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: 9342f16a-223f-4060-bebe-a750c3665984
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/target/boot modified=2014-04-30 01:18:27 mount.fstype=ext2 mount.options=rw,relatime mounted=2014-04-30 01:18:27 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 148GiB
                capacity: 148GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: rW1V0j-WhAu-rwEw-rsjB-jtk6-2RyA-HHJBSt
                   size: 148GiB
                   capacity: 148GiB
                   capabilities: multi lvm2
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD-ROM SDR6112F
             vendor: TOSHIBA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1F32
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 2001MiB (2098MB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=000736cc
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                version: FAT16
                serial: 1c9a-c85d
                size: 1999MiB
                capacity: 2000MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat
  *-battery
       description: Lithium Ion Battery
       product: CP178680-01
       vendor: Fujitsu
       physical id: 1
       serial: Not Supported
       slot: Internal Battery
       capacity: 66000mWh
       configuration: voltage=14.8V
drjoeross@JoeUbuntuLT:~$
```

---

### Post by drjoeross on 2014-04-30
UPDATE:    When I re-installed Ubuntu 14.04  this time the Wireless Does Work but the Lan Card (RealTek) still does not appear to be working.  I guess the first install was defective for some reason.  This is Better but still no Lan Card, which is lots faster and would be nice. 
Joe

---

### Post by drjoeross on 2014-04-30
Just noticed in the settings details overview: why the graphics are SO S L O W.....  Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)

Can anyone help here? I have a Radon 9600 card in my laptop and it is usually fast. 

Joe

---

### Post by mörgæs on 2014-05-01
With this graphics card I suggest a fresh install of X/Lubuntu.

---

