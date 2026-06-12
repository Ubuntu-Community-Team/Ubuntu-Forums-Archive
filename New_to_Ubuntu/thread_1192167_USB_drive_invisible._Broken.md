---
title: "USB drive invisible. Broken?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Halibutt on 2009-06-19
Hello there. I got a 120GB drive from a friend recently. It's old, it's loud, but it's 120GB and I have a free slot on my desktop, so...

Anyway, I put it in a USB case to see if it works at all. I plugged it into my laptop, started up my computer and... nothing, the darn thing is invisible. At times it shows up in computer:/// as a USB device, but is neither clickable nor mountable. Also gparted doesn't see the device. 

My question is: is the disk down or is it my Ubuntu? I don't care for the data on the disk, it could safely be formatted - if only I could make it work. Checked here and there and here's the output of what seems relevant:

> sudo fdisk -l
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5473    43961841    7  HPFS/NTFS
/dev/sda2            5474        7296    14643247+   5  Extended
/dev/sda5            5474        5765     2345458+  82  Linux swap / Solaris
/dev/sda6            5766        6738     7815591   83  Linux
/dev/sda7            6739        7296     4482103+  83  Linux

```

> sudo dmesg|tail
```
[ 1854.960099] usb 2-2: USB disconnect, address 9
[ 1855.216097] usb 2-2: new low speed USB device using uhci_hcd and address 10
[ 1855.384942] usb 2-2: configuration #1 chosen from 1 choice
[ 1855.469384] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input16
[ 1855.477038] generic-usb 0003:15CA:00C3.0009: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-2/input0
[ 1855.912061] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 1856.137679] usb 1-1: configuration #1 chosen from 1 choice
[ 1856.175823] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1856.178283] usb-storage: device found at 6
[ 1856.178289] usb-storage: waiting for device to settle before scanning
halibutt@halibutt-laptop:~$ 
```

> sudo lsusb
```
Bus 001 Device 006: ID 0402:5621 ALi Corp. USB 2.0 Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 010: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

> sudo lshw
```
    description: Notebook
    product: HP Compaq nx8220 (PY538ES#AKD)
    vendor: Hewlett-Packard
    version: F.14
    serial: CNU6011BWN
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=0066A55C-2B99-DB11-2B84-6D990C0E5929
  *-core
       description: Motherboard
       product: 0934
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 43.1D
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68DTV Ver. F.14 (08/18/2006)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U10
          size: 800MHz
          capacity: 1733MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back unified
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1280MiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM Synchronous 533 MHz (1.9 ns)
             product: KSBD48F-A8KE4
             vendor: 7F7F7F2500000000
             physical id: 0
             serial: 00000000
             slot: DIMM #1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: SODIMM Synchronous 533 MHz (1.9 ns)
             product: NT256T64UH4A0FN-37
             vendor: 7F7F7F0B00000000
             physical id: 1
             serial: E2750A66
             slot: DIMM #2
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 915GM/PM Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: M24 1P [Radeon Mobility X600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: eth0
                version: 11
                serial: 00:14:c2:e6:f0:1c
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5751m-v3.29a latency=0 link=no module=tg3 multicast=yes port=twisted pair
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 05
                serial: 00:15:00:4e:0b:5d
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.103 latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:02:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:02:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: SD Host controller
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
                vendor: Texas Instruments
                physical id: 6.4
                bus info: pci@0000:02:06.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7 module=sdhci_pci
           *-communication UNCLAIMED
                description: Communication controller
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
                vendor: Texas Instruments
                physical id: 6.5
                bus info: pci@0000:02:06.5
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: FUJITSU MHV2060A
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0083
                serial: NT29T5C2ERB5
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d315d315
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 7e4b50bd-7ad6-4748-ab7c-1cc98dbae037
                   size: 41GiB
                   capacity: 41GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-07-23 06:32:29 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2290MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 7632MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 4377MiB
                      configuration: mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-832S
                vendor: MATSHITA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ee:3d:a9:d9:06:8d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

BTW, Windows doesn't seem to work with the USB drive either. Any help?
Cheers

---

### Post by Terry of Astoria on 2009-06-19
I don't know much, but a noisy drive is sometimes a dead or dying drive.
Some of the USB drives are actually IDE drive inside USB case. Maybe try taking it out of USB enclosure and install in the computer, and then see what happens . .

---

### Post by Halibutt on 2009-06-20
> **Terry of Astoria said:**
> I don't know much, but a noisy drive is sometimes a dead or dying drive.
Some of the USB drives are actually IDE drive inside USB case. Maybe try taking it out of USB enclosure and install in the computer, and then see what happens . .

Yup, this one definitely is one of those. However, I'd rather not install it in my desktop right now. Firstly, my minitower is rather tightly packed inside and it would be a major pain to dismantle it, install it and then realize it's dead. Secondly, I don't have Ubuntu installed there.

Anyway, you might be right that the disk is simply a waste of time and efforts. If it's not dead yet, it probably would be soon. 
Cheers

---

### Post by LewRockwell on 2009-06-20
jumper not set correctly...perhaps?

---

### Post by Halibutt on 2009-06-21
> **LewRockwell said:**
> jumper not set correctly...perhaps?And what is jumper?

---

### Post by LewRockwell on 2009-06-21
> **Halibutt said:**
> And what is jumper?

jumpers like these:

[http://www.ehow.com/how_4966046_set-maxtor-hard-drive-slave.html](http://www.ehow.com/how_4966046_set-maxtor-hard-drive-slave.html)

The manufacturers of hard drives place legends which denote the correct positions of jumpers for a specific application. You might also find them listed on the web somewhere.

Most often there are three or four different settings(sometimes even more):

Cable Select
Master
Slave

Those three are the most common but you will also find drives that have a specific setting for:

Master WITH slave
Master with NO slave(single drive)

Then there are sometimes jumpers to limit or alter other drive parameters.

---

### Post by LewRockwell on 2009-06-21
Here is a nifty device that no technician or hobbyist should be without:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

.

---

