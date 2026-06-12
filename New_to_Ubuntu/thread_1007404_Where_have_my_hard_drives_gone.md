---
title: "Where have my hard drives gone?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Spaff on 2008-12-10
OK, so I jumped on board the Linux bandwagon a few weeks back, desperate to do away with Windows and start educating myself as to the ins and outs of Ubuntu.

However my initial installation was a failure. Despite doing my research, scouring the forums, preparing my PC for the install and partitioning my drive I just couldn't get Ubuntu to initialise after the installation. The live CD showed me what life would be like with Ubuntu as my OS and I liked what I saw so I was desperate to get it working.

Many IRC sessions and forum posts later I had tried all sorts but without success. My Ubuntu simply refused to welcome me to its beautiful GUI and repeatedly dumped me into the sobering Busybox prompt each time I tried to boot it up. I uninstalled and reinstalled, I downloaded a fresh image, I tried 32-bit and 64-bit versions but it still wouldn't work.

I then did a bit of editing in the terminal, believing my hard drive setup to be the root of the problems but this didn't help and eventually after exhausting all the avenues I could think of I was resigned to simply not being able to enjoy Ubuntu... UNTIL I remembered you can install it under Windows, albeit with reduced disk performance.

So here I am, with an Ubuntu that now boots up after I select it from my Windows boot menu. And isn't it lovely...

EXCEPT that it really struggles with my hard drives. Every time I try and search for files and folders it gets unresponsive and slow. Sometimes it will let me browse folders for a bit before suddenly losing them and other time it simply gives up on even trying to access my disks and I don't get it.

I've got 4 SATA drives which have never given me any grief under Windoze and yet Ubuntu does NOT like them one bit and for what reason I just don't know.

Has anyone any suggestions as to why Ubuntu struggles with my drives AND is the problem I'm suffering here symptomatic of my original installation failure?

Any advice would be mucho appreciated.

Cheers

---

### Post by Therion on 2008-12-10
Well I have a some questions since it sounds like most of your issues stem from a bad install disc...

1. Could you give us the basic specs of your system, please?  Nothing too detailed, just hit the high points (CPU, Memory, Video, the biggies).

2. When you burned your LiveCD or DVD, did you burn it as an IMAGE file -- meaning a bootable .iso?  

3. Did you burn the install media slooooooowly?  You need *accuracy* for this particular job, not speed.

4. Did you download the install media via a Torrent, or was it a regular HTTP download (i.e. right-click, "Save as")?

5. What version of Ubuntu are you trying to install:  version 8.04 (Hardy Heron) or 8.10 (Intrepid Ibex) or something else?

---

### Post by Michael.Godawski on 2008-12-10
hey Spaff, 
glad to see you do not lose heart...

Can you give us more info about your system?
Open the terminal and run this command, then post the output here:
```

sudo lshw
```

---

### Post by Spaff on 2008-12-10
Hi guys,

right I've got my spec print out from the terminal but I must warn you it is huge so I hope nobody gets angry with me for spunking the whole lot up here for your viewing pleasure (see below).

Secondly in answer to Therion's q's I burned my image files at a slow speed and definitely made sure they were burned as images (I am not new to making images and bootable CD's!). And I downloaded my .iso's from the ubuntu site, one via direct transfer and one via a torrent.

Spec follows:

```

description: Mini Tower Computer
    product: G33M03
    vendor: Foxconn
    version: 1.0
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=mini-tower uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: G33M03
       vendor: FOXCONN
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080014 (12/12/2007)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppytoshiba int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
          slot: SOCKET775 M/B
          size: 2666MHz
          capacity: 2666MHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 39
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM SDRAM Synchronous
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-ide
                description: IDE interface
                product: JMB368 IDE controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: scsi4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm pciexpress bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
              *-cdrom
                   description: DVD writer
                   product: DVD_RW ND-2500A
                   vendor: _NEC
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: 1.06
                   serial: [_NEC    DVD_RW ND-2500A 1.0603121900
                   capabilities: removable audio cd-r cd-rw dvd dvd-r
                   configuration: ansiversion=5 status=nodisc
              *-disk
                   description: ATA Disk
                   product: ST3160021A
                   vendor: Seagate
                   physical id: 0.1.0
                   bus info: scsi@4:0.1.0
                   logical name: /dev/sdd
                   version: 8.01
                   serial: 5JS2ZVQX
                   size: 149GiB (160GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=23f5b669
                 *-volume
                      description: Windows NTFS volume
                      physical id: 1
                      bus info: scsi@4:0.1.0,1
                      logical name: /dev/sdd1
                      logical name: /media/Mr Slave
                      version: 3.1
                      serial: 060573ec-f4a4-694f-b6a6-b15f29f99434
                      size: 149GiB
                      capacity: 149GiB
                      capabilities: primary bootable ntfs initialized
                      configuration: clustersize=4096 created=2005-03-08 15:44:50 filesystem=ntfs label=Mr Slave mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-communication UNCLAIMED
                description: Communication controller
                product: 536EP Data Fax Modem
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-network:0
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb
           *-network:1
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:03:02.0
                logical name: eth0
                version: 10
                serial: 00:1c:25:36:c3:80
                size: 10MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.64 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801IB (ICH9) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801IB (ICH9) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST3200822AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.01
                serial: 4LJ1AQG6
                size: 186GiB (200GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=dc17dc17
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /host
                   logical name: /boot
                   version: 3.1
                   serial: bc6e1bc9-14d1-fa41-9bfc-9c6be94b05bd
                   size: 186GiB
                   capacity: 186GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-11-18 17:55:13 filesystem=ntfs label=Eugene mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: Maxtor 6Y080M0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: YAR5
                serial: Y21JP4BE
                size: 76GiB (81GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=10e510e5
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 5098a496-88f3-994c-859c-3ed2ebdacee6
                   size: 76GiB
                   capacity: 76GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2005-10-31 15:17:54 filesystem=ntfs label=Little'un state=clean
           *-disk:1
                description: ATA Disk
                product: ST3250310AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdc
                version: 3.AA
                serial: 6RY3J1HL
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=09b309b2
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: 3a653979-2bb3-824c-8e5c-42874607441c
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-01-25 18:56:01 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:35:ff:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 76:84:ca:aa:66:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by Michael.Godawski on 2008-12-10
You can use the code brackets (#) to make large output more eye-friendly.
Perhaps this command will focus our attention more on the real thing.

```
sudo fdisk -l
```

---

### Post by Therion on 2008-12-10
Okay so the hardware looks good from what I can tell.  You're familiar with how to burn the install media which is good so I'm ruling that out.

Here's where I get confused:

> **Spaff said:**
> However my initial installation was a failure. Despite doing my research, scouring the forums, preparing my PC for the install and partitioning my drive I just couldn't get Ubuntu to initialise after the installation. 
First you say the install was a failure and then you say Ubuntu won't initialize after the installation.  So... Is the installation completing normally or is it not?

If not, what happens that prevents the installation from terminating normally?  Error message, lockup... What happens?

If the installation does complete normally what happens, specifically, when you reboot?

---

### Post by Spaff on 2008-12-10
Sorry, that was a bit confusing.

My install completes absolutely fine, all seems to be a success. It reboots and I get the GRUB menu to select Ubuntu from (I'm obviously going dual boot) then the splash screen pops up for quite a while before I'm kicked out to busybox and left wondering where to go next.

Here's my fdisk -l:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc17dc17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10e510e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09b309b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23f5b669

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19457   156288321    7  HPFS/NTFS

```

Cheers guys

---

### Post by Therion on 2008-12-10
> **Spaff said:**
> Sorry, that was a bit confusing.

My install completes absolutely fine, all seems to be a success. It reboots and I get the GRUB menu to select Ubuntu from (I'm obviously going dual boot) then the splash screen pops up for quite a while before I'm kicked out to busybox and left wondering where to go next.
Oh... Okay... Well your first post mentioned "desperate to do away with Windows" so I assumed you were doing a fresh, solo-install, of Ubuntu.  I'm sorry, but the fact that you intend to dual-boot is not obvious; this is the first mention you've made of wanting to set up dual-boot scenario and that's NOT a minor detail. 

So... Now we're making some progress.  Now that we've cleared up you need to set up dual-boot install we need to know what OS are you going to dual-boot alongside Ubuntu: Windows XP or Windows Vista?

---

### Post by Spaff on 2008-12-10
Sorry, neglected to mention that.

I'm on an XP machine. 

So at the moment I'm running Ubuntu having installed it via Windows and this is when I get my hard drive problems. Whereas when I try and install it using the proper Linux filesystem having booted from the Live CD I can't get it to load Ubuntu successfully from the Grub boot menu

---

### Post by Therion on 2008-12-10
Yeah, the problem is Windows doesn't like having another OS on the same drive but that's an easy thing to work around.  You need to have a good, working install Windows to start with so you can then install Ubuntu and let Ubuntu's GRUB take over the boot menu.  To have both OS'es on the same drive, you'll need to reformat and repartition a portion of the primary drive.

These four hard drives you mention; how are these configured in your system?  

Do you have any kind of RAID array set up or is there one bootable system drive with three additional "backup" drives, or what?

Assuming you don't have a RAID array set up you should look over this tutorial for how to set up a dual-boot installation alongside Windows XP:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Further... Assuming you do NOT have a RAID array set up with these four drives, I would suggest you physically unplug all the drives except for the one drive you intend to install on until everything is installed and up and running normally.  This advice comes from my personal experience.  Once you've got your installation up and running, once you've done all your updates and so forth, THEN you shut down the PC, reconnect the spare drives and reboot.  This last bit is up to you; it's just my personal suggestion.

---

### Post by Spaff on 2008-12-10
Well I originally installed on my master C drive, having partitioned it through the installer, but then kept having the problem where it wouldn't load up properly.

So then I tried installing on one of the other drives, which I partitioned using some software in windows before booting from the live cd to install but after the installation finished I still had the same problem where Ubuntu wouldn't load and I got dumped to Busybox.

Now this RAID malarkey you speak of leaves me with raised eyebrows because I'm afraid I'm not sure of my configuration. What's the best way to tell?

---

### Post by Therion on 2008-12-10
Simply put, if you don't know if you have a RAID array configured or not, you don't.  Let's just leave it at that.

Secondly, without being in the drivers seat, it's hard for me to visualize what you've done to your system specifically, so I'm not going to try.  No real point anyway.

In short, here's what I suggest you do.  Unplug three of your four hard drives, leaving only the drive you want to dual-boot from connected.  Then use the tutorial I gave you in my previous post to configure your system starting from the top and working your way down through the whole thing.  Follow that tutorial step-by-freaking-step.

Post back if your issues persist.

---

### Post by Spaff on 2008-12-10
The tutorial goes through it in exactly the same way as I did my installs but I will try unplugging the slave drives to see if this helps.

Must admit I thought they were causing me grief before as each time I booted my system and used the live CD to run ubuntu for diagnostics I noticed that they kept switching round so were being assigned different ID's each time I restarted.

I'll see if I have any joy with the hard drive thing and let you know how I get on.

Cheers

---

