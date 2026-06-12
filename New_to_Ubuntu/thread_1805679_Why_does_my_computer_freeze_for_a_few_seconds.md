---
title: "Why does my computer freeze for a few seconds?"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by jerrard on 2011-07-16
Hi Forum!

Another Noob question here.

I have now installed Ubuntu 10.04 a few times for various reasons. i had some problems getting it up and running in the first instance but got some help here.

However, while i have been until this moment happy to have it running, i have always seem to had a problem. The problem is that my computer just pauses/freeze's/hangs for about 5-10 secs and the carries on as usual. 

This happens while on the interwebs and watching films (mainly). There appears to be no trigger to make this happen and it does not happen at regular intervals. System monitor doesn't show any increased usage for anything or any major spikes. It really becomes annoying the third or fourth time into a film.

My graphic card is nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2) and i have used the recommended driver.

Please can someone point me in the right direction? All similar threads or post state that the system stops working and has to be rebooted, while mine does not.

Please let me know if you need any more info.

Kind regards,

J

---

### Post by rickytikki on 2011-07-16
is it a laptop or pc because sometimes laptops get tooo hot cause interuptions like that. also list complete system specs.

---

### Post by jerrard on 2011-07-16
Hi,

Its a desktop.

I also forgot to add that its the entire computer that freeze's and not just a program. I can't move the mouse etc

Many Thanks

---

### Post by jerrard on 2011-07-16
System Specs are:
description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: N68PV-GS
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.70 (08/03/2009)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.11.2
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 1GHz
          capacity: 2700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP67 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1f00(size=256)
     *-serial
          description: SMBus
          product: MCP67 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:dc00(size=64) ioport:1d00(size=64) ioport:1e00(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP67 Co-processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:fde80000-fdefffff
     *-usb:0
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fde7f000-fde7ffff
     *-usb:1
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fde7ec00-fde7ecff
     *-usb:2
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fde7d000-fde7dfff
     *-usb:3
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fde7e800-fde7e8ff
     *-ide:0
          description: IDE interface
          product: MCP67 IDE Controller
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:fde78000-fde7bfff
     *-pci:0
          description: PCI bridge
          product: MCP67 PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
          resources: ioport:e000(size=4096) memory:fdf00000-fdffffff
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 8
             bus info: pci@0000:01:08.0
             version: 61
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:18 ioport:ec00(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 8.1
             bus info: pci@0000:01:08.1
             version: 61
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:17 ioport:e880(size=32)
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 8.2
             bus info: pci@0000:01:08.2
             version: 63
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:19 memory:fdfffc00-fdfffcff
        *-network
             description: Network controller
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: a
             bus info: pci@0000:01:0a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=b43-pci-bridge latency=32
             resources: irq:19 memory:fdffc000-fdffdfff
     *-ide:1
          description: IDE interface
          product: MCP67 AHCI Controller
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi4
          logical name: scsi5
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:f80(size=8) ioport:f00(size=4) ioport:e80(size=8) ioport:e00(size=4) ioport:cc00(size=16) memory:fde76000-fde77fff
        *-cdrom
             description: DVD-RAM writer
             product: DRW-24B3LT
             vendor: ASUS
             physical id: 0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: Hitachi HCP72503
             vendor: Hitachi
             physical id: 1
             bus info: scsi@5:0.0.0
             logical name: /dev/sda
             version: GM3O
             serial: GEK033RG16R7HE
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00098f12
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 00cee9b3-e7d1-490d-9fb0-668322dae961
                size: 293GiB
                capacity: 293GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2011-06-21 22:04:01 filesystem=ext4 lastmountpoint=/:C&#65533;4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^]&#65533; &#65533;&#65533;&#65533;/&#65533;&#65533;^]&#65533;~1!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^]&#65533;^]&#65533;-&#65533; modified=2011-06-21 22:20:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2011-07-16 14:42:11 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@5:0.0.0,2
                logical name: /dev/sda2
                size: 5155MiB
                capacity: 5155MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5155MiB
                   capabilities: nofs
     *-network
          description: Ethernet interface
          product: MCP67 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:19:66:96:25:a7
          size: 100MB/s
          capacity: 1GB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.84 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:31 memory:fde7c000-fde7cfff ioport:c880(size=8) memory:fde7e400-fde7e4ff memory:fde7e000-fde7e00f
     *-pci:1
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24
     *-pci:2
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-pci:4
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:0e.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:27
     *-pci:5
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:28
     *-pci:6
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:29
     *-pci:7
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 11
          bus info: pci@0000:00:11.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:30
     *-display
          description: VGA compatible controller
          product: C68 [GeForce 7050 PV / nForce 630a]
          vendor: nVidia Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:21 memory:fc000000-fcffffff memory:d0000000-dfffffff(prefetchable) memory:fb000000-fbffffff memory:fde40000-fde5ffff(prefetchable)
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:11
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

---

### Post by rickytikki on 2011-07-16
look at the end of this forum it has what you need. [http://ubuntuforums.org/showthread.php?t=1478787&page=180](http://ubuntuforums.org/showthread.php?t=1478787&page=180)

---

### Post by jerrard on 2011-07-16
Many Thanks!

Peeps here are so helpful! Keep up the good work please guys and girls!

---

### Post by idoitprone on 2011-07-19
> description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)

You do have slow and small memory stick. Get better memory, in fact my 3 year old netbook has faster memory than yours.  It a netbook for crying out loud. Next time it freezes, post the results of ```
free -m
``` and
```
top
```You are probably swapping

if not then your cpu is straved for data

---

