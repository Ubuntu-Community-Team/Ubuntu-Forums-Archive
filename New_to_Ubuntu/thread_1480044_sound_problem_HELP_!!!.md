---
title: "sound problem HELP !!!"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by grobar87 on 2010-05-11
When i turn on my equalizer on every music player sound start to be very very bad:confused:...in system->preferences->multimedia system selector i try with all plugins (ALSA,PulseAudio....) but sound is still very bad...please help!

---

### Post by grobar87 on 2010-05-11
anyone...ok...just tell me what plugin to use for sound?..:confused:

---

### Post by tom.swartz07 on 2010-05-11
Could you give some information about your system and hardware?

Post the output of sudo lshw
Dont forget to use code tags so the output stays to a reasonable size in your post

---

### Post by grobar87 on 2010-05-11
dejan@dejan-laptop:~$ sudo lshw
[sudo] password for dejan: 
dejan-laptop              
    description: Portable Computer
    product: Vostro A860
    vendor: Dell Inc.
    serial: 565W6H1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-3600-1035-8057-B5C04F364831
  *-core
       description: Motherboard
       product: 0Y487G
       vendor: Dell Inc.
       physical id: 0
       serial: .565W6H1.CN486438B41956.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A02 (09/18/2008)
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2410  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Microprocessor
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: HYMP112S64CP6-S6
             vendor: AD00000000000000
             physical id: 0
             serial: 04004293
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR Synchronous [empty]
             physical id: 1
             slot: DIMM_B
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:f6e00000-f6efffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f6f00000-f6ffffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f60(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f80(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:21 memory:f6dfc000-f6dfffff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:44000000-441fffff memory:44200000-443fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:f6c00000-f6cfffff memory:44400000-445fffff(prefetchable)
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 01
                serial: 00:17:c4:4e:8e:26
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k ip=192.168.1.64 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:f6cf0000-f6cfffff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) memory:f6a00000-f6bfffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:21:70:8e:d5:3c
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:27 ioport:de00(size=256) memory:f6aff000-f6afffff memory:f0000000-f000ffff(prefetchable) memory:f0020000-f003ffff(prefetchable)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f00(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f20(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6f40(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:4000(size=4096) memory:f6900000-f69fffff memory:40000000-43ffffff(prefetchable)
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00704030-b0070402f irq:16 memory:f6900000-f6900fff ioport:4000(size=256) ioport:4400(size=256) memory:40000000-43ffffff(prefetchable) memory:48000000-4bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:18 memory:f69ff800-f69fffff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:17 memory:f69ff600-f69ff6ff
           *-generic:1
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: driver=ricoh-mmc latency=255 maxlatency=255 mingnt=255
                resources: irq:10 memory:f69ff700-f69ff7ff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:6e70(size=8) ioport:6e78(size=4) ioport:6e80(size=8) ioport:6e88(size=4) ioport:6ea0(size=16) ioport:eff0(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK1252GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LV01
                serial: X8IITDG1T
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00032fe9
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: a83b887d-4118-4ac4-95a4-4dcd9f0d9e59
                   size: 1906MiB
                   capacity: 1906MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: 92f0d3f4-e384-41f7-945a-b30bd2be9ea0
                   size: 10GiB
                   capacity: 10GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-04 18:17:37 filesystem=ext4 lastmountpoint=/nM&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;{&#65533;&#65533;&#65533;>3&#65533;u^ &#65533;U/&#65533;&#65533;>3&#65533;~!&#65533;`F&#65533;&#65533;`F&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;>3&#65533;>3&#65533;a modified=2010-05-04 18:00:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-11 14:10:25 state=mounted
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: d21d1a05-df6a-486c-98c3-c2b6e963f87e
                   size: 99GiB
                   capacity: 99GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-04 18:17:44 filesystem=ext4 lastmountpoint=/homeZP&#65533;&#768;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;&#65533;&#65533; &#65533;u^ &#65533;&#65533;&#65533; &#65533;&#65533; &#65533;&#65533;b&#65533;p&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533; modified=2010-05-11 14:10:26 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2010-05-11 14:10:26 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW TS-L633A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D300
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6dfbf00-f6dfbfff ioport:10c0(size=32)
  *-battery
       product: DELL F286H89
       vendor: SMP
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 44000mWh
       configuration: voltage=11.1V
dejan@dejan-laptop:~$

---

### Post by grobar87 on 2010-05-11
sorry for this :P i dont know how to use code tags...:confused:

---

### Post by VastOne on 2010-05-11
> **grobar87 said:**
> anyone...ok...just tell me what plugin to use for sound?..:confused:

Searching Google with the following Ubuntu + ICH8 Family + Audio

[_[COLOR="Green"]Here[/COLOR]_]("http://www.google.com/search?q=Ubuntu+%2B+ICH8+Family+%2B+Audio&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

results in a massive amount of info about your sound issues, you may want to check these out

---

### Post by grobar87 on 2010-05-11
ok thanks for your posts

---

