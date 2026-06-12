---
title: "Drivers"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by fidelandche on 2009-07-30
I have just checked my drivers and found that they are all proprietary drivers, is this going to cause me a problem in the long term? or do I need to change the drivers over for long term stability of Ubuntu? If I do need to change over the drivers, how do I do it? 

           Many thanks

---

### Post by RomeReactor on 2009-07-30
Hi. Do you mean the drivers for your video card or wireless card? Sometimes proprietary drivers are needed due to the lack of some functionality in the open source ones. It's a matter of choice, though: you're free to use proprietary or open-source drivers as you see fit.

---

### Post by fidelandche on 2009-07-30
Both really, I  know that proprietary drivers are not updated that much and as not using windows ever again, I just want to make sure my system is as stably as possible. I think it is more down to the wireless driver because I have noticed lots of posts about the slow internet and some people are posting that it might be down to the wireless driver(?) I am also having problems with streaming video when in full screen. So I thought that if I change the driver(?) it might make a difference?

        Many thanks

---

### Post by RomeReactor on 2009-07-30
Can you be more specific regarding the fullscreen video problem? What video card do you have? How did you install the proprietary drivers for it--downloaded from their website, or through one of the package managers (Synaptic, Add/Remove, Apt-Get, etc)?

---

### Post by DanFoxDavies on 2009-07-30
> **fidelandche said:**
> Both really, I  know that proprietary drivers are not updated that much and as not using windows ever again, I just want to make sure my system is as stably as possible. I think it is more down to the wireless driver because I have noticed lots of posts about the slow internet and some people are posting that it might be down to the wireless driver(?) I am also having problems with streaming video when in full screen. So I thought that if I change the driver(?) it might make a difference?

        Many thanks
I sometmes have issues with fullscreen video too. I found that disabling Compiz when watching them helps a lot. Also, Ubuntu Netbook Remix seems to have a more general issue with fullscreen-ing on my partner's Dell Mini10 (with a fresh Ubuntu 9.04NR on it rather than Dell's messed-up version)

---

### Post by fidelandche on 2009-07-30
When I installed Ubuntu 9.04 I removed all of windows so I could use Ubuntu as my only OS. All is going well until I stream movies from the Internet. It is fine in a small screen, but once I go full screen the picture goes 'choppy' and the play back sticks for a second or two. The sound is fine but the picture sticks. I have the the same problem with you tube.

  The video card is in built and it is 
File Description: Video Driver
Version: Intel 7.14.10.1147
Operating System: Microsoft(r) Windows(r) Vista 
Part Number: D20041-002-001
Date: 01/23/2007

  As for drivers they are the ones that came with the laptop when I bought it 
as a windows machine. I have only updated them when windows released updates.
I am having a problem with Internet connection as well, this appears to be an
issue that lots of people appear to be having, as there has been lots of
posts on this forum about the same subject.

      Many thanks

---

### Post by CatKiller on 2009-07-30
> **fidelandche said:**
> I have just checked my drivers and found that they are all proprietary drivers

Just as an FYI, the Hardware Drivers tool **only** lists proprietary drivers. There's no reason to list the many many free drivers that are included in the kernel, as kernel modules, or as libraries.

At some point the company that made the proprietary driver will drop support for whatever widget you're using. When that day comes you either hope that enough people have been testing the free drivers so that they will work with whatever widget you're using, or you'll have to get a new widget. And in the meantime you'd best hope that the company that made the proprietary driver has kept on top of things with regard to compatibility, stability and security, because no one else can do a thing about it.

---

### Post by starcannon on 2009-07-30
Boot your computer from the LiveCD, take Ubuntu for a nice safe test drive in that fashion; don't worry, nothing is installed or changed. 
What works? What doesn't work? Can you post some output of a terminal to help us better see your entire hardware list?

Running from the LiveCD, go to Applications>Accessories>Terminal and report back here the output of:
```

sudo lshw

```

Keep in mind that the LiveCD will be a bit slow, its running off the CD and so of course will not be anywhere near as fast as it is when installed on a HDD.

GL

---

### Post by fidelandche on 2009-08-02
Ok I have run the live CD and it is just the same with streaming videos, when in full screen the video is choppy and sticks. Here is the output from the terminal,

 description: Portable Computer
    product: ML6226B
    vendor: Gateway
    version: 3408386R
    serial: T3C7371009473
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=portable cpus=1 uuid=406A605C-EA1D-B211-8000-A0829907F10E
  *-core
       description: Motherboard
       vendor: Gateway
       physical id: 0
       version: 77.10
       serial: QTFGJJ71218112
       slot: &#65533;
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 77.10 (03/06/2007)
          size: 105KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: uFCPGA2
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 512MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 0
             serial: 05006C7C
             slot: DIMM 1
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 1
             serial: 05006CA2
             slot: DIMM 2
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
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
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8038 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 14
                serial: 00:e0:b8:c6:19:25
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:03:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 9.1
                bus info: pci@0000:03:09.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:03:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7 module=tifm_7xx1
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
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
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7530A
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: EX32
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: ST980811AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AL
                serial: 5LY3H5AE
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9a71cf53
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 1dcea6fe-557b-45ec-9aea-87e97aa66bd9
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-06-28 19:55:15 filesystem=ext3 modified=2009-08-01 18:10:20 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-08-01 17:44:37 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1427MiB
                   capacity: 1427MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1427MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-battery
       description: Lithium Ion Battery
       product: MAL32b
       vendor: SMP-PAN24
       physical id: 1
       version: 2007/03/24
       serial: 5989
       slot: In the Back side
       capacity: 4800mWh
       configuration: voltage=11.1V
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:e0:94:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.79 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 76:8e:08:c8:6e:39
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by RomeReactor on 2009-08-02
> **fidelandche said:**
> 
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        

Your video chipset is Intel, and their drivers are open source: as far as I know, there are no proprietary Intel video drivers for Linux. Not sure about your wireless, though, but it's possible it's also Intel, which would mean open drivers as well. In any case, according to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/370231") there seems to be a performance regression in Jaunty regarding the driver for your Intel video chip. One of the posts there reads:
> (Needs kernel 2.6.30) Unbearably slow full-screen video playback, Compiz
disabled, extremely slow and jumpy backward scrolling in FireFox
presumably due to absents of proprietary drivers for Intel Corporation
Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
This particular problem is related to the kernel, and is fixed for version 2.6.30, available in Karmic (Ubuntu 9.10). If this is indeed the same issue as yours, you'll have to wait until the kernel gets backported to Jaunty, or until Karmic is released. *Or* you could try to install the 2.6.30 kernel downloading the following packages:

[LIST]
[*][Linux Headers 2.6.30, All]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb")
[*][Linux Headers 2.6.30, 32-bit](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb)
[*][Linux Image 2.6.30, 32-bit]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")
[/LIST]
You can then install them by double-clicking on them. Note that this will install a new kernel, which will be used by default on your next boot.

---

### Post by fidelandche on 2009-08-03
So in your opinion would install the kernel?? or just wait for 9.10? and on the subject of 9.10 release do I have to order it when it is released or will it be posted out to me on release? or can I pre-order?

               Many thanks

---

### Post by RomeReactor on 2009-08-03
> **fidelandche said:**
> So in your opinion would install the kernel?? or just wait for 9.10?
It depends on how important these video issues are to you. Are you willing to wait a couple of months until 9.10 is released?
> and on the subject of 9.10 release do I have to order it when it is released or will it be posted out to me on release? or can I pre-order
When 9.10 comes out the update manager will inform you that a new release is available, and ask you if you want to upgrade. The beta releases have been available for a while, but I wouldn't recommend you install it just yet.

---

