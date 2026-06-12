---
title: "System Freezes and Then Odd Boot"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by JustJ9 on 2010-05-17
Installed 9.10 on my brothers computer. Every hour or so it freezes and he has to shut the power. When it boots sometimes it shows a blank screen and when restarted again it gives a choice of booting a Linux generic image 14 with an additional recovery mode PLUS the option of choosing Linux generic image 21 with its own recovery mode. If you choose the latter it won't boot. So the former is chosen and it loads. An hour later it freezes again. 

I'm a nOOb as is my brother but we are both committed to Ubuntu. Any help is appreciated.

---

### Post by sydbat on 2010-05-17
Sounds like a hardware problem, most likely overheating. Have you checked the fans to make sure they are a) running and b) not caked with dust?

Also, what type of computer is it? A desktop? Laptop?

The more information you can give us, the easier it will be to help you.

---

### Post by JustJ9 on 2010-05-17
It's a desktop. It was recently cleaned and the fans are running.

---

### Post by sydbat on 2010-05-17
Can you provide any more info? Like - 

CPU?
Graphics card?
RAM?
Hard drive specs?

If you are unsure of any of these, when in Ubuntu open a terminal (Applications > Accessories > Terminal) and run this```
sudo lshw
```and post the results here (please use the [code] tags).

---

### Post by JustJ9 on 2010-05-17
> **sydbat said:**
> Can you provide any more info? Like - 

CPU?
Graphics card?
RAM?
Hard drive specs?

If you are unsure of any of these, when in Ubuntu open a terminal (Applications > Accessories > Terminal) and run this```
sudo lshw
```and post the results here (please use the ```
 tags).


[CODE]description: Space-saving Computer
    product: Dimension 2400
     vendor: Dell Computer Corporation
    serial: HM1V771
    width:  32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
     configuration: administrator_password=enabled boot=normal  chassis=space-saving cpus=1 power-on_password=enabled  uuid=44454C4C-4D00-1031-8056-C8C04F373731
  *-core
       description: Motherboard
       product: 0F5949
       vendor: Dell Computer Corp.
       physical id: 0
        version: A01
       serial: ..CN7082151H403U.
     *-firmware
           description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A05 (12/02/2003)
          size: 64KiB
           capacity: 448KiB
          capabilities: pci pnp apm upgrade  shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen  int9keyboard int14serial int17printer acpi usb ls120boot  biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R)  Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
           physical id: 400
          bus info: cpu@0
          version:  15.2.9
          slot: Microprocessor
          size: 2400MHz
          capacity: 3600MHz
           width: 32 bits
          clock: 400MHz
          capabilities:  boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge  mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up  pebs bts cid xtpr
          configuration: id=0
        *-cache:0
              description: L1 cache
             physical id: 700
              size: 8KiB
             capacity: 8KiB
             capabilities:  internal write-back data
        *-cache:1
             description: L2 cache
              physical id: 701
             size: 128KiB
             capacity:  128KiB
             capabilities: internal varies unified
      *-memory
          description: System Memory
          physical id: 1000
           slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
              description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_1
              size: 512MiB
             width: 64 bits
             clock:  266MHz (3.8ns)
        *-bank:1
             description: DIMM  SDRAM Synchronous 266 MHz (3.8 ns) [empty]
             physical id: 1
             slot: DIMM_2
              width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
           description: Host bridge
          product:  82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
           bus info: pci@0000:00:00.0
          version: 01
           width: 32 bits
          clock: 33MHz
          configuration:  driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff(prefetchable)
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated  Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
              width: 32 bits
             clock: 33MHz
              capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
              resources: irq:16 memory:e8000000-efffffff(prefetchable)  memory:feb80000-febfffff
        *-usb:0
             description:  USB Controller
             product: 82801DB/DBL/DBM  (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
              width: 32 bits
             clock: 33MHz
              capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
              resources: irq:16 ioport:ff80(size=32)
        *-usb:1
              description: USB Controller
             product: 82801DB/DBL/DBM  (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
              width: 32 bits
             clock: 33MHz
              capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
              resources: irq:19 ioport:ff60(size=32)
        *-usb:2
              description: USB Controller
             product: 82801DB/DBL/DBM  (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
              width: 32 bits
             clock: 33MHz
              capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
              resources: irq:18 ioport:ff40(size=32)
        *-usb:3
              description: USB Controller
             product: 82801DB/DBM  (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
              width: 32 bits
             clock: 33MHz
              capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
              resources: irq:23 memory:ffa80800-ffa80bff
        *-pci
              description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
              clock: 33MHz
             capabilities: pci bus_master
              resources: ioport:d000(size=4096) memory:fe900000-feafffff  memory:20000000-200fffff(prefetchable)
           *-communication UNCLAIMED
                description:  Communication controller
                product: HSF 56k Data/Fax  Modem
                vendor: Conexant Systems, Inc.
                 physical id: 5
                bus info: pci@0000:01:05.0
                version:  00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                 configuration: latency=64
                resources: memory:fe9f0000-fe9fffff ioport:dff8(size=8)
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor:  Broadcom Corporation
                physical id: 9
                bus info:  pci@0000:01:09.0
                logical name: eth0
                 version: 01
                serial: 00:12:3f:26:ce:38
                 size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                 clock: 33MHz
                capabilities: pm  bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt  100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes  driver=b44 driverversion=2.0 duplex=half latency=64 link=no  multicast=yes port=twisted pair speed=10MB/s
                 resources: irq:17 memory:fe9ee000-fe9effff memory:20000000-20003fff(prefetchable)
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
              configuration: latency=0
        *-ide
             description:  IDE interface
             product: 82801DB (ICH4) IDE Controller
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
              resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8)  ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff
           *-disk
                description: ATA Disk
                 product: WDC WD400BB-75JH
                vendor: Western  Digital
                physical id: 0
                bus info:  scsi@0:0.0.0
                logical name: /dev/sda
                version: 06.0
                serial: WD-WCAMC2115259
                size: 37GiB  (40GB)
                capabilities: partitioned partitioned:dos
                 configuration: ansiversion=5 signature=d0f4738c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                    logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 7ce3b22e-f928-4331-9741-cc3675056613
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled  extended_attributes large_files huge_files dir_nlink recover extents  ext4 ext2 initialized
                   configuration: created=2010-05-15 17:07:42  filesystem=ext4 lastmountpoint=/'&#65533;{&#65533;&#65533;g&&#65533;&#65533;&#65533;&#65533;&#65533;t&#1984;&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;&#65533;e&#65533;&#65533;FO&#65533;&#65533;FO&#1984;g&&#65533;&#65533;~&#65533;&#1720;~&#65533;&#65533;Eh&#65533;&#65533;g&&#1952;&&#65533;&#65533;&#65533;  modified=2010-05-17 06:36:55 mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered  mounted=2010-05-17 10:52:25 state=mounted
              *-volume:1
                   description: Extended  partition
                   physical id: 2
                   bus  info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                    size: 1451MiB
                   capacity: 1451MiB
                   capabilities:  primary extended partitioned partitioned:extended
                  *-logicalvolume
                      description: Linux swap /  Solaris partition
                      physical id: 5
                      logical  name: /dev/sda5
                      capacity: 1451MiB
                       capabilities: nofs
           *-cdrom
                 description: SCSI CD-ROM
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical  name: /dev/scd0
                logical name: /dev/sr0
                 capabilities: audio
                configuration: status=nodisc
        *-serial  UNCLAIMED
             description: SMBus
             product:  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
              vendor: Intel Corporation
             physical id: 1f.3
             bus info:  pci@0000:00:1f.3
             version: 01
             width: 32  bits
             clock: 33MHz
             configuration:  latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio  controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)  AC'97 Audio Controller
             vendor: Intel Corporation
              physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
              width: 32 bits
             clock: 33MHz
              capabilities: pm bus_master cap_list
             configuration:  driver=Intel ICH latency=0
             resources: irq:17 ioport:ee00(size=256)  ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff

```

---

### Post by JustJ9 on 2010-05-17
It just happened again. Any ideas?

---

### Post by sydbat on 2010-05-17
Could be a number of factors like age, power supply, etc.

Does it make any strange noises before it freezes and powers off?

What was on it before (Win XP I presume)? Did it have problems then too?

Also, try turning off any fancy desktop effects. I notice you only have 512MB of RAM, and it shares that with your on-board graphics, so you are likely overtaxing your system to the point it becomes unusable (freezes). If it freezes again, try this:

```
Hold down Alt and the SysRq keys and type R E I S U B. 
```

This should shut down a non-responsive Linux system. If it does nothing, there is likely a hardware problem.

---

### Post by JustJ9 on 2010-05-17
> **sydbat said:**
> Could be a number of factors like age, power supply, etc.

Does it make any strange noises before it freezes and powers off?

What was on it before (Win XP I presume)? Did it have problems then too?

Also, try turning off any fancy desktop effects. I notice you only have 512MB of RAM, and it shares that with your on-board graphics, so you are likely overtaxing your system to the point it becomes unusable (freezes). If it freezes again, try this:

```
Hold down Alt and the SysRq keys and type R E I S U B. 
```This should shut down a non-responsive Linux system. If it does nothing, there is likely a hardware problem.

It was running XP, no strange noises and I set the desktop effects to bare bones. I will try the code when it happens again. Thank you for your help. He may just need to get a new box.

---

