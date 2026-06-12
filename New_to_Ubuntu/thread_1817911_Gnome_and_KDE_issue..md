---
title: "Gnome and KDE issue."
date: 2011-08-03
forum: New to Ubuntu
---

### Post by peska on 2011-08-03
Hi. I have this problem with the Gnome 2.3 version (the one available in Ubuntu 11.04) and with the last one of KDE Desktop. It's a little hard to explain but the thing is that when I open some menu or window, this one appears and disappear constantly, like a blinking. It's also change depending on the mouse location. 
If I log in Gnome with no effects, this doesn't happen but I could run the previous version of Gnome with all the effects.
Also, once I have installed Mandriva One in my PC and the same thing happened unless I would run it in Safe Mode.
So, that's it. Thank you very much for your answer.

---

### Post by Alwimo on 2011-08-03
Have you installed the video card drivers? You can do so in Ubuntu by looking for "additional drivers".
 
Installing them may fix it. Alternatively, uninstalling them may fix it. :)

---

### Post by peska on 2011-08-03
"No propietary drivers are in use on this system"

=/

---

### Post by Foobarz on 2011-08-03
What video card are you using?

---

### Post by wildmanne39 on 2011-08-03
Hi, run these commands in the terminal please:
```
sudo lshw
```
```
lspci | grep VGA
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by peska on 2011-08-04
Here it is.

```
agustin-desktop           
    description: Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=5B098116-8531-11D7-BDE5-0060B0F998F3
  *-core
       description: Motherboard
       product: D865GBF
       vendor: Intel Corporation
       physical id: 0
       version: AAC25827-402
       serial: ABBF32019319
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: BF86510A.86A.0077.P25.0508040031
          date: 08/04/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: J2E1
          size: 2400MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
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
          physical id: 39
          slot: System board or motherboard
          size: 768MiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: J6G1
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: SerNum2
             slot: J6G2
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:2
             description: DIMM DDR Synchronous 266 MHz (3.8 ns) [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 2
             serial: SerNum3
             slot: J6H1
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:3
             description: DIMM DDR Synchronous 266 MHz (3.8 ns) [empty]
             product: PartNum4
             vendor: Manufacturer4
             physical id: 3
             serial: SerNum4
             slot: J6H2
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff memory:ffa80000-ffafffff ioport:ec00(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:cc00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d000(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d400(size=32)
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ffa7fc00-ffa7ffff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: memory:ff800000-ff8fffff
           *-network
                description: Wireless interface
                product: Atheros AR5001X+ Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 3
                bus info: pci@0000:01:03.0
                logical name: wlan0
                version: 01
                serial: 00:25:86:d3:95:3f
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.1.100 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:19 memory:ff8f0000-ff8fffff
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:30000000-300003ff
           *-disk
                description: ATA Disk
                product: Maxtor 6Y060L0
                vendor: Maxtor
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y2MP72GE
                size: 57GiB (61GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1a4e2558
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: ce098b22-5753-7942-baae-66aa8f1986ae
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-07-19 18:50:31 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 26GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1210MiB
                      capabilities: nofs
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-R/RW SW-252B
                vendor: SAMSUNG
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: R700
                serial: [
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:e800(size=8) ioport:e400(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d800(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:c400(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 memory:ffa7f800-ffa7f9ff memory:ffa7f400-ffa7f4ff
agustin@agustin-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

```

---

### Post by wildmanne39 on 2011-08-04
Hi, I am sorry at this time there is no support for your card in unity, it is probably not going to be supported in any newer releases either.

You will have to run classic with no effects of downgrade to a previous release.
[http://ubuntuforums.org/showthread.php?t=1745151&highlight=82865G+Integrated+Graphics](http://ubuntuforums.org/showthread.php?t=1745151&highlight=82865G+Integrated+Graphics)

---

### Post by peska on 2011-08-04
Unity? I'm talking about KDE and Gnome.

---

### Post by wildmanne39 on 2011-08-04
Hi,I should have said in 11.04.

---

### Post by peska on 2011-08-04
Anyway, my video card is no longer supported for them also, right?

---

### Post by wildmanne39 on 2011-08-04
Hi, only in classic with no effects.

---

