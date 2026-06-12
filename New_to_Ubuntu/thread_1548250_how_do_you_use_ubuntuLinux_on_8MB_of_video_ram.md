---
title: "how do you use ubuntu/Linux on 8MB of video ram"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by zer010 on 2010-08-08
My Dad wants to try out Ubuntu. The computer is something like: 3 GHz AMD; onboard graphics @ 8MB; .75 GB Ram. When I install Ubuntu, the resolution is something like 460x320(?) which ends up cutting off parts of some GUI panels. Is there a fix for this or is there another Linux solution besides a straight CLI?
He's not ready to buy a graphics card yet, no matter what my urging.

---

### Post by cascade9 on 2010-08-08
It wont be a 3HGz AMD atthat age. Probably a 3000+, but as fro which version, I dont know (there are lots of 3000+ AMD CPUs)

The onboard graphics would be the problem. It shouldn't be the video memory, 8MB should go to at least 1600x1200, but you could try looking in the BIOS to see if you can allocate more video RAM. I would guess that it is some VIA video chipset, but without knowing what video chip it is using, its hard to know if there will be an easy solution.

If you can run the command "sudo lshw" and post the output here (in 'code' or 'quote' brackets) that would go a long way to figuring out what is going wrong.  Or, if yuo can only work with windows (I know I cant deal with 460x320) the the output from a windows tool would help (tools like belarc advisor, everest, etc). 

BTW, I dont know about where you live, but I can get 2nd hand nViida AGP cards for virtually northing (less than $10 US). That would work much better than any VIA video, and its a very cheap upgrade.

---

### Post by halj32 on 2010-08-08
You could always try Puppy Linux, it's based on Ubuntu
take a look here
[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

---

### Post by dodle on 2010-08-08
**Edit:** halj32 was right, the new version of Puppy IS based on Ubuntu. :)

I am running Lubuntu on an old AMD Sempron laptop with a terrible graphics chipset, and it runs nice and smooth.  Much better than when I was running Ubuntu.  I had the same problem of being unable to see the entire screen.  The solution was to re-configure the xserver.  Here is the thread for the problem:  [http://ubuntuforums.org/showthread.php?t=1544285](http://ubuntuforums.org/showthread.php?t=1544285).  Maybe it can help you.

Another distro that I tried recently was [SliTaz](http://www.slitaz.org/).  It was extremely fast, the boot up seemed to be almost instant, and the display was configured correctly.  But because I wanted a Debian/Ubuntu based system I switched to Lubuntu.

**Edit:** If you do decide to use Lubuntu, don't judge Ubuntu by it.  The LXDE Desktop, which Lubuntu uses, is not as far along in development stages as the GNOME desktop, which Ubuntu uses.

---

### Post by cascade9 on 2010-08-08
> **halj32 said:**
> You could always try Puppy Linux, it's based on Ubuntu
take a look here
[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

I wouldnt say 'based on'. As of version 5.0 it does use ubuntu binaries, but puppy still uses PET package mangament, not debian apt-get etc..   

I have no idea why anybody would recommend puppy, or other 'light' distros for an AMD 3000+/768MB setup anyway.

---

### Post by robert shearer on 2010-08-08
> **cascade9 said:**
> 
I have no idea why anybody would recommend puppy, or other 'light' distros for an AMD 3000+/768MB setup anyway.

Agreed !.
 I am running Ubuntu 10.04 on an AMD2600+ with 768 Mb ram and it runs well.

---

### Post by khelben1979 on 2010-08-08
> **robert shearer said:**
> Agreed !.
 I am running Ubuntu 10.04 on an AMD2600+ with 768 Mb ram and it runs well.

By using [XFCE4]("http://en.wikipedia.org/wiki/Xfce4") instead of [Gnome]("http://en.wikipedia.org/wiki/Gnome_%28software%29") and [KDE]("http://en.wikipedia.org/wiki/KDE") the speed increase gets even better! I'm not sure if an Ubuntu installation can accept to not install Gnome though, Debian does accept it. Anyone who knows?

---

### Post by da burger on 2010-08-08
> **khelben1979 said:**
> By using [XFCE4]("http://en.wikipedia.org/wiki/Xfce4") instead of [Gnome]("http://en.wikipedia.org/wiki/Gnome_%28software%29") and [KDE]("http://en.wikipedia.org/wiki/KDE") the speed increase gets even better! I'm not sure if an Ubuntu installation can accept to not install Gnome though, Debian does accept it. Anyone who knows?

You can. Either by installing Xubuntu (or Kubuntu if you want KDE) or installing xubuntu-desktop once the system is installed. However I seem to remember reading somewhere that Xubuntu ins't actually that much lighter than Ubuntu.

---

### Post by cascade9 on 2010-08-08
> **da burger said:**
> You can. Either by installing Xubuntu (or Kubuntu if you want KDE) or installing xubuntu-desktop once the system is installed. However I seem to remember reading somewhere that Xubuntu ins't actually that much lighter than Ubuntu.

Xubuntu isnt that much lighter than ubuntu. 

Better of doing a minimal install of Xfce, rather than getting xubuntu-desktop.

---

### Post by kwacka on 2010-08-08
Check out the installation/low memory systems help page [HERE]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by scratman on 2010-08-08
I'm not sure how you can be having too many problems running Ubuntu with that system spec to be honest.  I'm using Ubuntu Netbook Edition on an Acer Aspire One Z5, which has a dual core 1.6Ghz processor, 512 Mb RAM and 8Mb Video graphics.  Things work fine for me currently.  I'll grant you, the resolution is not high, 1024x600, but that is due to the screen on my netbook, it will cheerfully output fullscreen video at 1280x1024 resolution on my external monitor.  HD video is a different story, but I'm not worried about that at all frankly.  I can actually get the Desktop Effects working, but I've no need or desire for them.

Honestly, I don't see any major reason why Ubuntu should have problems running on a higher spec machine than mine.

---

### Post by zer010 on 2010-08-10
Firstly, thank you all for your help!   I know for a fact that his mobo has no AGP slot, but has a lot of PCI slots. I will have to double check to be sure it doesn't have a PCI-E slot. 
I will have to do a little more research on his hardware. Next time I go  over to his house I will run "sudo lshw" and post the results here.

---

### Post by sandyd on 2010-08-10
[Lubuntu (LXDE)]("http://www.facebook.com/nixiepixel"). [Crunchbang (OpenBox)]("http://crunchbanglinux.org/")
much lighter, less graphiccy. both based on ubuntu.

---

### Post by uRock on 2010-08-10
One thing to check if you haven't already is whether or not there are any drivers offered in the menu under System> Administration> Hardware Drivers.

From what I can see your specs aren't much lower than mine and we should be able to get Ubuntu 10.04 working.

Cheers,
uRock

---

### Post by zer010 on 2010-10-11
Ok, it's been awhile, but I now have the machine in question here. I ran a Live session and got a lshw output (and I was WAY off of my original estimate on the specs!):
ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Desktop Computer
    product: VT8361
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 8361-686B
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (02/22/2002)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.4.2
          slot: Socket A
          size: 1333MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 1280MiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 1GiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: BANK_1
             size: 256MiB
     *-pci
          description: Host bridge
          product: VT8361 [KLE133] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e0000000-e3ffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: VT8361 [KLE133] AGP Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: memory:e4000000-e6ffffff memory:28000000-280fffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CyberBlade/i1
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-1.0 pm bus_master cap_list
                configuration: latency=32
                resources: memory:e5800000-e5ffffff memory:e6000000-e601ffff memory:e5000000-e57fffff memory:28000000-2800ffff(prefetchable)
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: driver=parport_pc latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:d000(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG SP0411N
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: TW10
                serial: S01JJ30WA14634
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=55555555
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 9ea0952a-1094-d84c-9dc1-e9b75f7fcd99
                   size: 23GiB
                   capacity: 23GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2004-10-04 18:49:53 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: d46a1c6e-0fe6-594f-844e-8839caae24a2
                   size: 13GiB
                   capacity: 14GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-11-05 15:32:17 filesystem=ntfs state=clean
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM GD-5000
                vendor: HITACHI
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 0213
                capabilities: removable audio dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: LTR-52327S
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: QS09
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:12 ioport:d400(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:12 ioport:d800(size=32)
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:11 ioport:dc00(size=256) ioport:e000(size=4) ioport:e400(size=4)
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth0
             version: 10
             serial: 00:30:1b:0f:0c:df
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
             resources: irq:11 ioport:e800(size=256) memory:e8000000-e80000ff memory:28100000-2810ffff(prefetchable)
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: SanDisk Cruzer
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 8.02
             serial: u
             size: 3863MiB (4051MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 3863MiB (4051MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=0001f83b
              *-volume
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /media/sndsk4gb
                   version: FAT32
                   serial: e62e-bb77
                   size: 3863MiB
                   capacity: 3863MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=sndsk4gb mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted

---

### Post by zer010 on 2010-10-11
I find this output particularly interesting:
*-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 1280MiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 1GiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: BANK_1
             size: 256MiB
It says that there is a 1GiB module installed, but when checking memory in System Monitor, it says the total RAM is 615.4MiB. It tells about the same in WinXP. I wonder why this is so...

---

### Post by vlaar on 2010-10-11
> *-display UNCLAIMED
description: VGA compatible controller

You don't have a driver installed. 
If you try to install that. The errors might disappear.

---

