---
title: "slow graphics"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by dondecap on 2011-05-31
hi,
 I have ubuntu 10, in a 64gig partiton with 6gig swap partition
and 2gig memory,
but if I do heavey graphic work it is very slow....normal work ie click to open folder etc super fast.
is there something simple to do ...............like designate memory for graphics or perhaps too big a swap file?
regards
don

---

### Post by Joe of loath on 2011-05-31
Firstly, your swap partition is about 3 times too large :p

Secondly, what processor do you have?

---

### Post by wildmanne39 on 2011-05-31
> **dondecap said:**
> hi,
 I have ubuntu 10, in a 64gig partiton with 6gig swap partition
and 2gig memory,
but if I do heavey graphic work it is very slow....normal work ie click to open folder etc super fast.
is there something simple to do ...............like designate memory for graphics or perhaps too big a swap file?
regards
don
Hi, give us the specs on your system,are you using the cube,or any other effects?
If you do not know the hardware you have put this command in a terminal and post back here.
```
lspci
```Is this a laptop or desktop, and how old is it. What do you call heavy graphic work.

---

### Post by dondecap on 2011-06-01
HI people here is what came up in terminal
don@don-OEM ~ $ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
what I was trying to do was convert 209 page pdf to jpeg with gimp....displayed as image.
displayed as layer was quicker but more aukward to wiork with.
I think its a duel processor. its a desk top machine
screen dulls when it gets near the end of this and also when it is using software manager to instal programs
regards
don
I will reduce the swap file to 2gig.

---

### Post by wildmanne39 on 2011-06-01
> **dondecap said:**
> HI people here is what came up in terminal
don@don-OEM ~ $ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
what I was trying to do was convert 209 page pdf to jpeg with gimp....displayed as image.
displayed as layer was quicker but more aukward to wiork with.
I think its a duel processor. its a desk top machine
screen dulls when it gets near the end of this and also when it is using software manager to instal programs
regards
don
I will reduce the swap file to 2gig.

Hi, yes the first thing is reduce swap to 2 gigs, Are you running the cube or desktop effects? Also post the out come of this command. 
```
sudo lshw
``` click on new reply and click # and paste the information between the brackets. You can use system monitor to see what is using up your memory and cpu when you are doing that work, that is a good way to know what is happening to your system.

---

### Post by dondecap on 2011-06-01
#don@don-OEM ~ $ sudo lshw
[sudo] password for don: 
don-oem                   
    description: Desktop Computer
    product: OEM
    vendor: OEM
    version: OEM
    serial: OEM
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=A929B73F-1DDB-6981-CB2C-001FE25F16F3
  *-core
       description: Motherboard
       product: G31MX Series
       vendor: Foxconn
       physical id: 0
       serial: UY30832067636
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/30/2008)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Socket 775
          size: 2GHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
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
          physical id: 24
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM Synchronous 50410 MHz (0.0 ns)
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 3165MHz (0.3ns)
        *-bank:1
             description: DIMM Synchronous 50410 MHz (0.0 ns)
             physical id: 1
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 3165MHz (0.3ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 2GHz
          capacity: 2GHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:fdf00000-fdf7ffff ioport:ff00(size=8) memory:d0000000-dfffffff memory:fda00000-fdafffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:44 memory:fdff8000-fdffbfff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:1f:e2:5f:16:f3
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:42 ioport:ee00(size=256) memory:fdcff000-fdcfffff memory:fdb00000-fdb1ffff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fe00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fd00(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fc00(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fb00(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdfff000-fdfff3ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f900(size=8) ioport:f800(size=4) ioport:f700(size=8) ioport:f600(size=4) ioport:f500(size=16)
           *-disk
                description: ATA Disk
                product: ExcelStor Techno
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: P22O
                serial: PVF904Q4C28L7B
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00011e8a
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 4ff98657-3fad-4ced-8a11-2642f1d71b15
                   size: 61GiB
                   capacity: 61GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-05-06 12:59:29 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;P"&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;l!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1819;&#65533; &#65533;4&#65533;&#65533;&#65533;yo!&#65533;&#65533;d modified=2011-05-19 08:35:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-01 08:55:23 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 5999MiB
                   capacity: 5999MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2000MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /media/safe
                      capacity: 3992MiB
                      configuration: mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,barrier=1,data=ordered state=mounted
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /media/store
                   version: 1.0
                   serial: 9bf49829-0dd8-4101-9524-ea84846ed8fa
                   size: 58GiB
                   capacity: 58GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-05-07 20:22:11 filesystem=ext4 label=store lastmountpoint=/media/storeZ`c?dy&#65533;h&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;l!&#65533;h&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#548;&#65533;&#65533;dy modified=2011-06-02 00:56:46 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,barrier=1,data=ordered mounted=2011-06-02 00:56:46 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: iHAS120   6
                vendor: ATAPI
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/Camera Manual
                version: 7L04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/Camera Manual
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
     *-scsi
          physical id: 2
          bus info: usb@1:5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
don@don-OEM ~ $ 
wow thats a lot of info :-)

---

### Post by dondecap on 2011-06-01
hi not running cube as far as I know
sys moniter shows everything 'sleeping' except gimp
I NOTICED IT SAID 64 BIT
I am running all 32 bit is that ok?
regards
don

---

### Post by wildmanne39 on 2011-06-01
> **dondecap said:**
> hi not running cube as far as I know
sys moniter shows everything 'sleeping' except gimp
I NOTICED IT SAID 64 BIT
I am running all 32 bit is that ok?
regards
donHi, yes that is ok, 64 bit will run a little faster,but not a lot. I looked through everything and your system is ok but it is not a powerful system so it does not have a lot of resources I suspect that is slower your system down some,run some graphic stuff like you mentioned and look at the system monitor while you are running it and see of it maxes out your cpu's or memory, it should help lower swap, be careful if your swap is in the wrong place on your drive and you have to move it or one of your other partitions it will make your system unbootable and you will have to reinstall grub. To resize swap you will have to unmount it.

---

### Post by dondecap on 2011-06-02
hi, the swap is at the 'end' of disk.
when I fire up web browser it send 1 cpu to 50% and the other to 75%swap stays respectivly still in the moniter. so looks like just a cheap system even though we had extra memory.
many thanks
regards
don
could some one mark as 'solved' ?
 :-)

---

### Post by mastablasta on 2011-06-02
an upgrade of graphics card would make it run much faster. 
 
aside from the fact that your graphics chip is not so well supported in Linux (as in Windows) it is also a "crappy" one. no offense. it is good enoguh for office work though. A 30 USD or EUR dedicated graphcis card would solve the problem.

---

### Post by wildmanne39 on 2011-06-02
> **dondecap said:**
> hi, the swap is at the 'end' of disk.
when I fire up web browser it send 1 cpu to 50% and the other to 75%swap stays respectivly still in the moniter. so looks like just a cheap system even though we had extra memory.
many thanks
regards
don
could some one mark as 'solved' ?
 :-)
Hi, I think only you can mark the thread as solved because you started it. Go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so

---

