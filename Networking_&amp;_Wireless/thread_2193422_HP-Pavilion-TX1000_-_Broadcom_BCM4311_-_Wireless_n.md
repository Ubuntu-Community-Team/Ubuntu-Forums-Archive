---
title: "HP-Pavilion-TX1000 - Broadcom BCM4311 - Wireless not working"
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by amjjawad on 2013-12-12
Hi,

```
lshw
hp-pavilion-tx1000
    description: Notebook
    product: HP Pavilion tx1000 Notebook PC (GF789EA#ABB)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF7214LZT
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 family=103C_5335KV sku=GF789EA#ABB uuid=434E4637-3231-344C-5A54-001B242F1736
  *-core
       description: Motherboard
       product: 30BF
       vendor: Quanta
       physical id: 0
       version: 69.26
       serial: None
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.11
          date: 04/18/2007
          size: 106KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor TK-55
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.1
          slot: Socket S1
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
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
             size: 256KiB
             capacity: 512KiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: DIMM 1
        *-bank:1
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: M4 70T6554EZ3-CE6
             vendor: EC00000000000000
             physical id: 1
             serial: 68030A17
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.8.1
          size: 1800MHz
          capacity: 1800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: NVIDIA Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: NVIDIA Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: NVIDIA Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: NVIDIA Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: NVIDIA Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: NVIDIA Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:4000(size=4096) memory:b4000000-b7ffffff ioport:d0000000(size=2097152)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 memory:b8000000-bbffffff
        [COLOR=#ff0000][B]*-network
             description: Network controller
             product: BCM4311 802.11a/b/g
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:03:00.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=wl latency=0
             resources: irq:19 memory:b8000000-b8003fff[/B][/COLOR]
     *-display
          description: VGA compatible controller
          product: C51 [GeForce Go 6150]
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:18 memory:b2000000-b2ffffff memory:c0000000-cfffffff memory:b1000000-b1ffffff memory:fe0c0000-fe0dffff
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: NVIDIA Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: NVIDIA Corporation
          physical id: a.3
          bus info: pci@0000:00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:b0040000-b007ffff
     *-usb:0
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:b0004000-b0004fff
     *-usb:1
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:b0005000-b00050ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:3080(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:30b0(size=8) ioport:30a4(size=4) ioport:30a8(size=8) ioport:30a0(size=4) ioport:3090(size=16) memory:b0006000-b0006fff
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:17 memory:d7000000-d7003fff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: NVIDIA Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:1b:24:2f:17:36
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.8 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:20 memory:b0007000-b0007fff ioport:30b8(size=8)
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 7
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-4084N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: KQ09
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 8
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: FUJITSU MHW2120B
             vendor: Fujitsu
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 8918
             serial: NZ1DT752HS6H
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000ba6ab
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 6df601ad-ded9-4c0c-9247-41e96a41458c
                size: 20GiB
                capacity: 20GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-12-13 01:27:14 filesystem=ext4 lastmountpoint=/ modified=2013-12-13 02:55:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-12-13 02:55:29 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: a07e72b9-23ce-4aef-9f1c-ea176ed70451
                size: 2GiB
                capacity: 2GiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sda3
                logical name: /home
                version: 1.0
                serial: 5c31abca-7129-4b28-b22c-66afe1fba952
                size: 89GiB
                capacity: 89GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-12-13 01:27:19 filesystem=ext4 lastmountpoint=/home modified=2013-12-13 02:55:31 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-12-13 02:55:31 state=mounted


```

I have followed: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I have insatlled the needed drivers. However, I can't see any Wireless Network just like this machine has no Wireless Adapter. Nothing at all. Yes, I have checked the "Wireless Button" on the Laptop 10 times and it is ON. 

Help is highly appreciated.

Thank you!

---

### Post by amjjawad on 2013-12-12
Sorry, forgot to add:
I have installed Crunchbang today on this very machine. Wireless worked out-of-the box like a charm. When I installed Lubuntu (this is my neighbour's machine and he is newcomer to Linux so Crunchbang won't be an easy option for him), I failed, no matter how many times I tried, to get the Wireless Up and Running. I even had to re-install Lubuntu but nothing happened.

---

### Post by chili555 on 2013-12-12
I assume you are running a later version of Ubuntu. The correct driver for 4311 is not wl. With a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and tell us if it's working.

---

### Post by amjjawad on 2013-12-13
Hello chili555 :D

> **chili555 said:**
> I assume you are running a later version of Ubuntu.
Yes, Lubuntu 13.10 i386

> The correct driver for 4311 is not wl. 
I guess I noticed that when I installed Crunchbang (Debian Based) 'before' installing Lubuntu. It worked out-of-the box but had to remove it and go for Lubuntu because the user is new to Linux.

> 
With a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and tell us if it's working.


When I rebooted, the machine was stuck on "Lubuntu Logo" with the "5 dots" Screen so had to shut it down from the power button and turn it on.

When it was ON again, I was able to connect to my Wireless :D

Ubuntu Community should be very proud and lucky to have someone with your skills around. Problem solved good Sir, thank you so much :D

I should never be worried as long as someone like you is around!

---

### Post by chili555 on 2013-12-13
> **amjjawad said:**
> Hello chili555 :D


Yes, Lubuntu 13.10 i386


I guess I noticed that when I installed Crunchbang (Debian Based) 'before' installing Lubuntu. It worked out-of-the box but had to remove it and go for Lubuntu because the user is new to Linux.



When I rebooted, the machine was stuck on "Lubuntu Logo" with the "5 dots" Screen so had to shut it down from the power button and turn it on.

When it was ON again, I was able to connect to my Wireless :D

Ubuntu Community should be very proud and lucky to have someone with your skills around. Problem solved good Sir, thank you so much :D

I should never be worried as long as someone like you is around!Very happy to help. Your very kind words are appreciated!

---

### Post by amjjawad on 2013-12-16
> **chili555 said:**
> Very happy to help.
And I am happy that someone with your skills and experience is around and help us :)


> Your very kind words are appreciated!
Those are true words :)
Thank you again for everything!

---

