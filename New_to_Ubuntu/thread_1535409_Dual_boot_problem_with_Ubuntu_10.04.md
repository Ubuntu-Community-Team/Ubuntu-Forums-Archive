---
title: "Dual boot problem with Ubuntu 10.04"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by Milind on 2010-07-20
I have an Ubuntu 10.04 (Gnome 2.30.2)- Win XP dual boot system. Things were going smoothly till recently when the following problem has arisen : 
When I start my computer the BIOS flash screen is seen first as usual, succeeded by the GRUB menu,the latest Ubuntu version on top. When I select Ubuntu the grub screen disappears, to be replaced by a dark screen with a flashing cursor in the top left corner. After flashing for a while the cursor vanishes, leaving a black screen, and the display light on the front of the monitor starts flickering. Nothing further happens unless I switch off the computer's power supply at the mains (merely pressing the Reset button or Power button on the computer does not work), wait till the display light goes off, and then restart the computer. Initially the computer would boot after doing this once but, increasingly, I have to do this twice for the computer to boot. 
This problem seems to happen only when trying to boot into Ubuntu. If I choose Win XP at the grub screen, the computer boots as usual.
I'd appreciate any help/suggestions.

---

### Post by friv_livs on 2010-07-20
Post the output of
```
lshw -C graphics
```

and the brand/model number of your PSU.

Sounds like graphics BSOD or power issue.

---

### Post by Milind on 2010-07-21
> **friv_livs said:**
> Post the output of
```
lshw -C graphics
```

and the brand/model number of your PSU.

Sounds like graphics BSOD or power issue.

The output of the above code is PCI (sysfs) . (See screenshot.)
[IMG]http://www.fileden.com/files/2006/5/1/10557//sc1.png[/IMG]

I haven't understood what you meant by PSU. :( But assuming you want to know about the motherboard and chip, here goes : Intel DG31PR board, Intel Core 2 Duo chip.

---

### Post by warfacegod on 2010-07-21
PSU is Power Supply Unit. Assuming you are on a Desktop, open the case (ground yourself first). The big "box" where all the wires come out of should have a label with brand and model info on it.

---

### Post by friv_livs on 2010-07-21
Milind:

Did you let lshw run for at least 2 minutes? Looks like you screenshot at the first output of the command.

---

### Post by Milind on 2010-07-21
> **friv_livs said:**
> Milind:

Did you let lshw run for at least 2 minutes? Looks like you screenshot at the first output of the command.

friv_livs :
If I run that command, that's all I get, and that too for less than a second.I then get the command prompt again. I tried many a time, but the result was the same. Finally, I just ran the command sudo lshw and got the following output. Perhaps it contains what you're looking for:

milind@milind-desktop:~$ sudo lshw -c graphics
milind@milind-desktop:~$ sudo lshw
milind-desktop            
    description: Desktop Computer
    product: INTEL
    vendor: DG31PR
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=DB02C56A-AAAE-11DD-9B3B-000EA68F7260
  *-core
       description: Motherboard
       product: DG31PR
       vendor: Intel Corporation
       physical id: 0
       version: AAE39516-301
       serial: BTPR84400YY7
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: PRG3110H.86A.0047.2008.0227.1745 (02/27/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU         E7400  @ 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: J3E1
          size: 2793MHz
          capacity: 4GHz
          width: 64 bits
          clock: 1066MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni monitor tm2 ssse3 lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Unknown
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
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
          physical id: 22
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: Unknown
             vendor: Unknown
             physical id: 0
             serial: Unknown
             slot: J6H1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR Synchronous 800 MHz (1.2 ns) [empty]
             product: Unknown
             vendor: Unknown
             physical id: 1
             serial: Unknown
             slot: J6H2
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 2800MHz
          capabilities: ht
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
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24
        *-display
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:ff900000-ff97ffff ioport:f140(size=8) memory:d0000000-dfffffff(prefetchable) memory:ff700000-ff7fffff
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
             resources: irq:16 memory:ff980000-ff983fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:80000000-801fffff memory:80200000-803fffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:ff800000-ff8fffff memory:80400000-805fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: 00:1c:c0:ab:44:a4
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:27 ioport:e000(size=256) memory:ff820000-ff820fff memory:ff800000-ff81ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:f080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:f060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:f040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:f020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ff984000-ff9843ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
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
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f0f0(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG SP0411N
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: TW10
                serial: 00000000000000
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ee5aee5d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: f8ce-a7eb
                   size: 10001MiB
                   capacity: 10001MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-10-06 06:40:31 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 13GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 13GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 674MiB
                      capabilities: nofs
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:f0e0(size=8) ioport:f0d0(size=4) ioport:f0c0(size=8) ioport:f0b0(size=4) ioport:f0a0(size=16)
           *-disk
                description: ATA Disk
                product: ST3360320AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 3.CH
                serial: 5QF7SB3X
                size: 335GiB (360GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ee5aee5c
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 8af33bbe-02f5-f749-8d88-5c078c8b1d05
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-02-17 00:05:55 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   size: 296GiB
                   capacity: 296GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 74GiB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 74GiB
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sdb7
                      capacity: 74GiB
                 *-logicalvolume:3
                      description: HPFS/NTFS partition
                      physical id: 8
                      logical name: /dev/sdb8
                      capacity: 74GiB
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-H663C
                vendor: TSSTcorp
                physical id: 0.1.0
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CM00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             resources: ioport:f000(size=32)
milind@milind-desktop:~$

---

### Post by Milind on 2010-07-21
> **warfacegod said:**
> PSU is Power Supply Unit. Assuming you are on a Desktop, open the case (ground yourself first). The big "box" where all the wires come out of should have a label with brand and model info on it.

Thanks, warfacegod. So far, I've never been adventurous enough to open my computer and muck about with the hardware. Let me gather my courage. If I can't, I guess I'll have to call the repairer.

---

### Post by warfacegod on 2010-07-21
> **Milind said:**
> Thanks, warfacegod. So far, I've never been adventurous enough to open my computer and muck about with the hardware. Let me gather my courage. If I can't, I guess I'll have to call the repairer.

Sure thing. Eventually, you *will* need to get brave to clean your computer of dust. I try to clean my laptop once every month or so. Any desktops in my house (they come and go like raising children) get cleaned every two months or so.

It's either that or shell out cash every time your computer needs cleaning and that should be far more often than folks usually realize.

---

### Post by friv_livs on 2010-07-22
Milind:

According to your lshw:

```
*-display
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:ff900000-ff97ffff ioport:f140(size=:cool: memory:d0000000-dfffffff(prefetchable) memory:ff700000-ff7fffff
```

You have a bug with your graphics card:

[HTML]https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/539533/[HTML]

Try the following in recovery mode:

```
cd /usr/lib/xorg/modules/drivers
cp intel_drv.so intel_drv.sobackup
rm intel_drv.so
```

To restore driver if this doesn't help, in recovery mode run:

```
cd /usr/lib/xorg/modules/drivers
cp intel_drv.sobackup intel_drv.so
rm intel_drv.sobackup
```

I'm not sure how to correct the power button not being recognized.

---

### Post by Milind on 2010-07-24
@ friv_livs : 
 
Unfortunately that didn't work. :(

---

### Post by friv_livs on 2010-07-24
Milind:

I cannot help you further on your issues due to being out of my knowledge base.

Sorry.

---

### Post by Milind on 2010-07-25
> **friv_livs said:**
> Milind:

I cannot help you further on your issues due to being out of my knowledge base.

Sorry.

friv_livs :

That's all right. Thanks for the help. My problem may not have been solved but, at least, I learnt a few things from you.

---

### Post by oldfred on 2010-07-25
I have nvidia and at the grub menu, hit e for edit and on the kernel line replace quiet splash with nomodeset.

Also try rescue mode .

See also
All drivers: nomodeset - this will disable the kernel modesetting feature and drop the user back to the old X.org infrastructure and behaviour. 
or
nouveau.modeset=1

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by Milind on 2010-08-09
@ oldfred. Thanks, but none of those solved my problem. 
Out of sheer frustratiom I reinstalled Ubuntu 10.04 from the Live CD, formatting the previous install. The problem disappeared! Unfortumately my joy was short-lived. Once Ubuntu updated to the present to 2.6.32-24 the problem reappeared. Any suggestions, anyone?

---

### Post by Elmer Fudd on 2010-08-09
> **Milind said:**
> @ oldfred. Thanks, but none of those solved my problem. 
Out of sheer frustratiom I reinstalled Ubuntu 10.04 from the Live CD, formatting the previous install. The problem disappeared! Unfortumately my joy was short-lived. Once Ubuntu updated to the present to 2.6.32-24 the problem reappeared. Any suggestions, anyone?

Does the problem re-disappear if you choose to boot (from the Grub or Burg menu)  2.6.32-23?

---

### Post by Milind on 2010-08-09
> **Elmer Fudd said:**
> Does the problem re-disappear if you choose to boot (from the Grub or Burg menu)  2.6.32-23?

No, it doesn't. It only disappears, apparently, after a clean new install from the CD, but reappears after any version update.

---

### Post by chriswillmorris on 2010-08-09
I had a Acer Aspire laptop and fixed my problem by going into the BIOS and switching hard drive config from IDE to ACHI.

---

### Post by Milind on 2010-08-10
> **chriswillmorris said:**
> I had a Acer Aspire laptop and fixed my problem by going into the BIOS and switching hard drive config from IDE to ACHI.

I couldn't find any such option in my BIOS.

---

### Post by chriswillmorris on 2010-08-12
I would look it up online.  The answer should be out there.

---

### Post by Milind on 2010-09-19
Bumping my problem up again. I still haven't found any solution. :(

---

