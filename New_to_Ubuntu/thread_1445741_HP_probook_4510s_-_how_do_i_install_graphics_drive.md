---
title: "HP probook 4510s - how do i install graphics driver?"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by Slyth99 on 2010-04-03
Hi

I am trying to run some games like grand theft auto 3 and they are running extremely slowly!

I have just installed Ubuntu 9.10 and i have updated the system.

I usually go to System/Administration/Hardware Drivers on the menu  after updating and installing a new system and the system is able to find the drivers I need. I have done this before on my desktop computer with no problems. Now that I have a laptop this doesn't seem to work. I have done a bit of searching on the Internet but can't seem to find the information that I need. Any help or suggestion would be appreciated. thanks!

---

### Post by Encrypted_Soldier on 2010-04-03
If it's a nvidia card go on nvidia's website and download the driver from there.  Also tell us more about the hardware you are running so we can better help you.

---

### Post by Slyth99 on 2010-04-03
I am pretty sure it is an intel graphics card - i don't know if it is nvidia or ati... :(

Anyone else got any suggestions?

---

### Post by Slyth99 on 2010-04-03
there must be a way to do it...

---

### Post by TheNerdAL on 2010-04-03
Nvidia and Intel are two different companies.

---

### Post by TheNerdAL on 2010-04-03
Give me the info:
```
lspci
```

---

### Post by Slyth99 on 2010-04-03
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by TheNerdAL on 2010-04-03
Then you have Intel.

---

### Post by Slyth99 on 2010-04-03
You still there dude?

What do i do now?

---

### Post by TheNerdAL on 2010-04-03
Yeah.

---

### Post by Slyth99 on 2010-04-03
what do i do now?

---

### Post by TheNerdAL on 2010-04-03
I don't know if your driver is supported.

---

### Post by Slyth99 on 2010-04-03
I'm still not sure what i should do to make sure the drivers are correct and updated???

---

### Post by Slyth99 on 2010-04-03
> **TheNerdAL said:**
> I don't know if your driver is supported.
can i play games on this laptop under linux then?

---

### Post by TheNerdAL on 2010-04-03
Nevermind, it is. 

Give me the info: 
```
lshw
```

---

### Post by Slyth99 on 2010-04-03
root@nickos-laptop:/home/nickos# lshw
nickos-laptop             
    description: Notebook
    product: HP ProBook 4510s
    vendor: Hewlett-Packard
    version: F.15
    serial: CNU0114RNS
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=CC20AAB1-62FC-DF11-BC6E-8A007F19E83E
  *-core
       description: Motherboard
       product: 3072
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 24.0E
       serial: CNU0114RNS
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: a
          version: 68PZI Ver. F.15 (02/23/2010)
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Intel(R) Genuine processor
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Internal Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
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
     *-cache
          description: L1 cache
          physical id: 2
          slot: Internal Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: AD73I1B1674EG
             vendor: CB01100500000000
             physical id: 0
             serial: 000000
             slot: Top
             size: 2GiB
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: AD73I1B1674EG
             vendor: CB01100500000000
             physical id: 1
             serial: 000000
             slot: Bottom
             size: 2GiB
             clock: 1067MHz (0.9ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:31 memory:d0000000-d03fffff memory:c0000000-cfffffff(prefetchable) ioport:70f0(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0400000-d04fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:70c0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:70a0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:7080(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:d8904c00-d8904fff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:17 memory:d8900000-d8903fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 memory:d8800000-d88fffff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 memory:d8700000-d87fffff
           *-network
                description: Wireless interface
                product: WiFi Link 100 Series
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 00
                serial: 00:26:c7:1d:10:08
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=10.0.0.3 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:32 memory:d8700000-d8701fff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:5000(size=8192) memory:d4700000-d86fffff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:3000(size=8192) memory:d0700000-d46fffff
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:28 ioport:2000(size=4096) memory:d0600000-d06fffff memory:d8a00000-d8afffff(prefetchable)
           *-network
                description: Ethernet interface
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:85:00.0
                logical name: eth0
                version: 10
                serial: d8:d3:85:1d:72:e7
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:30 memory:d0600000-d0603fff ioport:2000(size=256) memory:d8a00000-d8a1ffff(prefetchable)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:7060(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:7040(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:7020(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:d8904800-d8904bff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:d0500000-d05fffff
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
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:70e8(size=8) ioport:70fc(size=4) ioport:70e0(size=8) ioport:70f8(size=4) ioport:7000(size=32) memory:d8904000-d89047ff
           *-disk
                description: ATA Disk
                product: ST9500420AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0006
                serial: 5VJ4JJLN
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=aaaeeb12
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 28f3aa7f-2d5b-4989-88d0-98a2f4e9e35f
                   size: 457GiB
                   capacity: 457GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-04-04 08:59:51 filesystem=ext4 lastmountpoint=/p+&#65533;&#65533;&#65533;&#65533;x&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;I^&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533; modified=2010-04-03 14:40:14 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-04-03 14:40:14 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 8573MiB
                   capacity: 8573MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8573MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7586H
                vendor: hp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KH03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
  *-battery
       product: ZZ08063
       vendor: SMP-SO22G6F
       physical id: 1
       version: 3C2A
       serial: 077D
       slot: Primary
       capacity: 4400mWh
       configuration: voltage=14.4V

---

### Post by TheNerdAL on 2010-04-03
Go here and update your drivers: [http://www.intel.com/support/chipsets/sb/CS-029319.htm](http://www.intel.com/support/chipsets/sb/CS-029319.htm)

I can only take you this far, sorry.

---

### Post by Slyth99 on 2010-04-03
thanks man!

---

### Post by TheNerdAL on 2010-04-03
Anytime.

Mark [SOLVED] if this thread is solved. :)

---

### Post by Slyth99 on 2010-04-03
one more thing how do i know if my graphics card is GL40, GM45, GS40, GS45, PM45?

---

### Post by Slyth99 on 2010-04-03
I think i have found a good site where you can download the linux driver for this type of laptop with an intel driver...it is:

[http://edc.intel.com/Software/Downloads/IEGD/#download](http://edc.intel.com/Software/Downloads/IEGD/#download)

I hope this helps somebody I will close this off once i try it out!!!

---

### Post by Slyth99 on 2010-04-03
No that didn't work either :(

---

### Post by Slyth99 on 2010-04-03
this sucks!

---

