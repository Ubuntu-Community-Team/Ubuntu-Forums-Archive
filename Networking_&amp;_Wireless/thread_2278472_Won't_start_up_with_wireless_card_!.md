---
title: "Won't start up with wireless card !"
date: 2015-05-16
forum: Networking &amp; Wireless
---

### Post by xicoperola on 2015-05-16
Hello everyone,
I just installed Lubuntu 14.04 in an old computer i had around here, but the problem is that if i connect the Wireless PCI adapter (TL-WN353GD) the computer won't start up, it just freezes in a black screen. While it works normally without it. Also during the installation i had to remove the adapter to manage to install, otherwise the installation would freeze after i choose "Install Lubuntu". Does anyone know how to fix this ?

Thanks

---

### Post by mörgæs on 2015-05-17
Let's see more of the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by xicoperola on 2015-05-17
Thanks for your reply, bellow is the result:

```
computer
    description: Desktop Computer
    product: Presario 6233EA
    vendor: Compaq
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0804h
       vendor: Compaq
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 1
          version: 686O2 v3.13
          date: 12/16/2002
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.4
          slot: XU1 PROCESSOR
          size: 2400MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: burst internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 512KiB
             capacity: 4MiB
             capabilities: burst internal write-back data
     *-memory:0
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3,8 ns)
             product: HYMD232 646A8-H
             vendor: JEDEC ID:AD 00 00 00 00 00 00 00
             physical id: 0
             serial: [REMOVED]
             slot: DIMM1
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3,8 ns)
             product: HYMD232 646A8-H
             vendor: JEDEC ID:AD 00 00 00 00 00 00 00
             physical id: 1
             serial: [REMOVED]
             slot: DIMM2
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 25
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f4000000-f7ffffff
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:f1000000-f21fffff memory:e0000000-f01fffff
           *-display
                description: VGA compatible controller
                product: NV31 [GeForce FX 5600]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
                resources: irq:18 memory:f1000000-f1ffffff memory:e0000000-efffffff memory:f0000000-f001ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:2440(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:2460(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:2480(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f0500000-f05003ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:1000(size=4096) memory:f0200000-f04fffff
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:05:08.0
                logical name: eth0
                version: 81
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:f0400000-f0400fff ioport:1000(size=64)
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:24c0(size=16) memory:20100000-201003ff
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
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:2000(size=256) ioport:2400(size=64) memory:f0500400-f05005ff memory:f0500600-f05006ff
     *-scsi:0
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST360020A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.64
             serial: [REMOVED]
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0009e04e
           *-volume:0
                description: Linux swap volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1
                serial: [REMOVED]
                size: 3905MiB
                capacity: 3905MiB
                capabilities: primary bootable nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 52GiB
                capacity: 52GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 52GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 4
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM SD-616T
             vendor: SAMSUNG
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: F307
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc


```

---

### Post by mörgæs on 2015-05-18
You have the latest BIOS. Good, else I would suggest upgrading. 

I don't know this wifi card but a brief googling shows that it's only 802.11 b/g. Are you sure it's worth the effort to fight with it? You could also see what a used card capable of 802.11 n costs.

---

### Post by xicoperola on 2015-05-18
You're right, it probably doesn't worth, I had never noticed about that limitation... I will get a new one then.
Thanks for your help.

---

### Post by tgalati4 on 2015-05-18
Does the card work in Windows on another computer?  I've had bad wireless cards that would freeze up a laptop.  Sometimes the chips wear out.  Put your finger on it.  If it's hot, then it's probably shot.

---

