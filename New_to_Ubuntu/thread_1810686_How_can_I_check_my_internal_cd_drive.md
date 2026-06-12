---
title: "How can I check my internal cd drive?"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by zangler on 2011-07-23
I have an old Acer TravelMate 2410 laptop with internal DVD-RW, with latest version of Edubuntu installed.  When I boot, I can hear sound.  When I put in a CD to listen to some music, I can't find the CD/DVD drive in order to play the music.  This has got to be something so simple, so I'm sorry to trouble the many advanced users with a trivial question.  Why doesn't the CD automatically play and why can't I find the audio files?

Thanks in advance.

---

### Post by relay_man on 2011-07-23
I'm not at all familiar with Edubuntu, but I have read at the Edubuntu website that the current version of Edubuntu ships with the same Gnome desktop system as Ubuntu.
Assuming that is correct, click on the Applications menu in the upper left corner of your screen. In the box that drops down, do you have "Sound and Video" as one of your choices?

---

### Post by zangler on 2011-07-24
Hi relay_man

Yes, I've got an Applications menu and within that I have a Sound and Video menu with the following applications:

Banshee Media Player
Brasero Disk Burner
Hydrogen Drum Machine
Movie Player
PiTiVi Video Editor
Rhythmbox Music Player
Sound Recorder
TiMidity++ MIDI Sequencer
TuxGuitar

I had a look using Banshee and Rhythmbox to see if I could find the audio CD I had placed in the DVD/CD Drive, but couldn't find anything.  Is it possible that the DVD/CD Drive isn't recognised by the Operating System?

---

### Post by relay_man on 2011-07-24
Hi zangler

Yes, it is possible that the cd player isn't recognized and that is what we should check for first.
An easy way to check is to do the following:

Open a terminal session and at the prompt enter

sudo lshw

(Broken down, the ls means list or show and hw means hardware)

You will be prompted to enter your password. This should be the same password you use to 
log in at startup.

It is likely there will be a rather lengthy listing of all the hardware that the OS can find. Take your time and look carefully for information about your cd player.  

Below is an example from my machine of what you are looking for. (yours won't be exactly the same, but should be similar. I've included only the portion showing my cd player info.  There is typically a LARGE quantity of info)

```

*-cdrom
                description: DVD-RAM writer
                product: DVD Writer 1060d
                vendor: HP
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KH23
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
```

If you cannot find any info concerning your cd player, then the OS isn't recognizing it.  That may indicate one of a few possible issues but chances are the cd player is recognized.  

At any rate, list the output of the lshw command here and we will proceed from that point.

---

### Post by zangler on 2011-07-24
Thanks for your support relay_man.  Here's the output from the sudo lshw command.  I couldn't find any reference to a CD or DVD drive.  Thanks too for explaining what the command means!

description: Notebook
    version: 0100
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=normal chassis=notebook uuid=7AC48040-895E-11DA-A8DD-B2BD019FE8F7
  *-core
       description: Motherboard
       product: Morar
       vendor: Acer
       physical id: 0
       version: Rev
       serial: lxtac051955400311aks00
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V1.09
          date: 02/07/2006
          size: 104KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 2GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 Synchronous
             physical id: 1
             slot: M2
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:b0000000-b003ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:84000000-8407ffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:b0040000-b00403ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:3000(size=4096) memory:b0100000-b01fffff ioport:80000000(size=67108864)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:06:07.0
                logical name: eth0
                version: 10
                serial: 00:0a:e4:f1:60:8c
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.13 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:20 ioport:3000(size=256) memory:b0100000-b01000ff
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 9
                bus info: pci@0000:06:09.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:22 memory:b0101000-b0101fff ioport:3400(size=256) ioport:3800(size=256) memory:80000000-83ffffff memory:88000000-8bffffff
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
             configuration: driver=Intel ICH latency=0
             resources: irq:21 ioport:1c00(size=256) ioport:18c0(size=64) memory:b0040800-b00409ff memory:b0040400-b00404ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
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
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-disk
                description: ATA Disk
                product: HTS424040M9AT00
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MA2O
                serial: MPA248Q2JETJ6E
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0005fee6
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: aa542f3d-1432-4fe1-95f8-fca693c75594
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-11-29 22:12:37 filesystem=ext4 lastmountpoint=/ modified=2011-07-19 16:06:46 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-07-24 13:30:47 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1610MiB
                   capacity: 1610MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1610MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:20a0(size=32)

---

### Post by relay_man on 2011-07-24
OK zangler

It appears that your system has not recognized the cd player.
My next suggestion would be to restart your machine.
Interrupt the startup and examine the bios settings.  I would
go through all of the bios settings carefully to see
if your cd player has been disabled in any way.
It is also very important to see if there is a setting which will
allow the machine to boot from the cd drive.  (boot order?)
Make sure that the cd drive is included in the boot order list.

The boot order for my older HP laptop is:

CD ROM
USB
HDD  (hard drive)
NETWORK BOOT

If you cannot find anything in the bios settings that look improper,
I would try to boot your laptop with the Ubuntu live disc.
(Don't install, just "run Ubuntu without changing your system"
This will test your cd drive and determine if it can function at all.)

It would be VERY unusual to find a cd drive that is not compatible with
GNU/Linux.  I'm sure we will find the problem soon.

---

### Post by zangler on 2011-07-24
Wierd!  Checked the BIOS, boot list almost same as yours, but includes reference to a floppy drive (there isn't a floppy on the laptop!) instead of the USB drive - CD/DVD, Floppy, HDD and Network Boot, in that order.  Put a Ubuntu live disc in and rebooted, was offered the opportunity to install.  Removed disc and rebooted to desktop, put in an Audio CD and the icon appeared and I was offered choice of applications.

Problem solved - no idea how!

Thank you for taking the time to help me.

---

### Post by relay_man on 2011-07-24
If the problem appears again, It might be well to remove the floppy drive from the boot list.

Glad you are up and running!

---

