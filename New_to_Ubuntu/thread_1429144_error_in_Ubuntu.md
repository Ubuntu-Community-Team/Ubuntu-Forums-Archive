---
title: "error in Ubuntu"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by Trandre on 2010-03-13
I am a fresh ubuntu user, and have som trouble using ubuntu. It is running slow in the browser, does not work with citrix(and cisco vpn) and movies and so on. 

So I followes a post where I deleted all my files in home. This repeared the cpu problem on running browser, but recieved other issues on updating and innstalling features. So I read a new post and run: sudo apt-get install --fix-broken to do a repair. but i recieved the following message: 
sudo apt-get install --fix-broken
Leser pakkelister ... Feil
E: Problem parsing dependency Conflicts
E: Feil oppsto under behandling av xserver-xorg-video-cirrus (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: Pakkelista eller tilstandsfila kunne ikke fortolkes eller åpnes.

How can I repair this?

Trandre

---

### Post by Trandre on 2010-03-13
My environment:
    


description: Desktop Computer
    product: 00000000000000000000000
    vendor: Packard Bell NEC
    version: PB13312591
    serial: 045752720216
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=883C31B6-F1CC-D911-8000-4E45435F4349
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 2.0e (12/06/2004)
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 478
          size: 2800MHz
          capacity: 4GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: synchronous external write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 478
          size: 2800MHz
          capacity: 4GHz
          clock: 133MHz
          capabilities: ht
          configuration: id=0
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR 333 MHz (3.0 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 651 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:e0000000-e7ffffff
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:e8000000-eaffffff memory:d0000000-dfffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: G73 [GeForce 7600 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:e8000000-e8ffffff memory:d0000000-dfffffff(prefetchable) memory:e9000000-e9ffffff memory:ea000000-ea01ffff(prefetchable)
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:1400(size=32)
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-disk
                description: ATA Disk
                product: ST380011A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.01
                serial: 5JVN9WJB
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ace22e9e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: bcf39b08-f108-4d83-b750-b052dbb13ee5
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-01-31 19:54:50 filesystem=ext4 lastmountpoint=/#D:&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;:&#65533;&#65533;&#65533;&#65533;&#65533;]&#65533;&#65533;Y&#65533;&#65533;&#65533;Y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#60990;&#65533;U`&#65533;&#65533;&#65533;`&#65533;%&#65533; modified=2010-02-28 07:44:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-03-13 23:13:59 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2933MiB
                   capacity: 2933MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2933MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD_RW ND-3530A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 2.01
                serial: [_NEC    DVD_RW ND-3530A 2.0105011100
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:d800(size=256) ioport:dc00(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:20 memory:eb000000-eb000fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:eb001000-eb001fff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:eb002000-eb002fff
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 10
             bus info: pci@0000:00:10.0
             logical name: eth0
             version: 10
             serial: 00:0f:ea:c8:58:47
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.6 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
             resources: irq:17 ioport:e000(size=256) memory:eb003000-eb0030ff
     *-scsi
          physical id: 1
          bus info: usb@2:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: photosmart 7700
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdb

---

### Post by The Real Dave on 2010-03-13
> **Trandre said:**
> I am a fresh ubuntu user, and have som trouble using ubuntu. It is running slow in the browser, does not work with citrix(and cisco vpn) and movies and so on. 

So I followes a post where I deleted all my files in home. This repeared the cpu problem on running browser, but recieved other issues on updating and innstalling features. So I read a new post and run: sudo apt-get install --fix-broken to do a repair. but i recieved the following message: 
sudo apt-get install --fix-broken
Leser pakkelister ... Feil
E: Problem parsing dependency Conflicts
E: Feil oppsto under behandling av xserver-xorg-video-cirrus (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: Pakkelista eller tilstandsfila kunne ikke fortolkes eller åpnes.

How can I repair this?

Trandre

To playback movies, you'll need to install the required codecs. Go to Applications>Software Centre and search for Ubuntu Restricted Extras. Install them, and you should be able to watch your movies fine :)

---

### Post by Trandre on 2010-03-14
Thanks, for your answer The real Dave. When I tried to activate Ubuntu Restricted Extras, I found out that I have removed all installed programs(which was what I have tried to do, but also wiped out the entire contents of the softwarecenter [IMG]file:///home/famfem/Skrivebord/Skjermdump-Ubuntus%20programvaresenter.png[/IMG]

Further I have a red stop sign i the top right corner as seen here: [IMG]file:///home/famfem/Skrivebord/Skjermdump.png[/IMG] 
When I press it i get this message

---

### Post by Trandre on 2010-03-14
Didnt understand the insert picture function here so I uploaded the pictures, And tried to insert them with the uploaded adress. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150067&stc=1&d=1268554559[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150068&stc=1&d=1268554559[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150069&stc=1&d=1268554559[/IMG]

---

### Post by Trandre on 2010-03-14
This is what I have deleted, I know I could restore it, but the cpu of the computer is running more smoothly, exept for the above mentioned issues. Could anyone tell me which of these files disabled the contents of the Program center?

Trandre

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150071&stc=1&d=1268556258[/IMG]

---

### Post by Trandre on 2010-03-14
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150091&stc=1&d=1268578977[/IMG]

---

### Post by Trandre on 2010-03-14
When i am reading other threads I see information I can get up to solve my issue. So here is some more info on my computer :-)

famfem@famfem-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe #Added by software-properties

---

### Post by The Real Dave on 2010-03-14
All the started after you deleted some files? Where exactly were these deleted from? 

Could you post the output of 

```
sudo apt-get update
```

Type this into a terminal (Applications>Accessories>Terminal), hit enter, give it a password, and enter again. Should let us know if it's something to do with your software repositrity.

You can also try opening Synaptic, and seeing you can install the restricted extras from there. Just type restricted extras into the search box, right click the correct one and mark for installation. Then press Apply. 

Your sources.list looks fine, you just seem to be using a local (Norway?) server.

---

### Post by Trandre on 2010-03-14
Hi and thanks again for your help. I tried to roll back my Ubuntu to install, because I had a problem with the cpu using steadily 60-70 % of my capacity. So I followed a thread wich said I could delete all files in home cause they all where user config(at least thats how I understood it). So I did, the files i deleted is on the screenshot above from the trashbin. Wich actually fixed my cpu problem, but gave me some new :-)[img]http://ubuntuforums.org/attachment.php?attachmentid=150071&d=1268556258 [/img]

I ran the command you posted in terminal and washed the result through google transelate, you where right I think it is a norwegian server I hoocked up since it has the ".no" in it. (Does this limit my program options?, in that case, can I switch?)   

famfem @ famfem-desktop: ~ $ sudo apt-get update
[sudo] password for famfem:
Sorry, try again.
[sudo] password for famfem:
Ign cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release.gpg
Ign cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic / main Translation-nb
Ign cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic / restricted Translation-nb
Ign cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release
Ign cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic / main Packages
Ign cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic / restricted Packages
Ign cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic / main Packages
Ign cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic / restricted Packages
Error cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic / main Packages
  Use "apt-cdrom" to make this cd available for APT. You can not use "apt-get update" to add new CDs.
Error cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic / restricted Packages
  Use "apt-cdrom" to make this cd available for APT. You can not use "apt-get update" to add new CDs.
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic Release.gpg
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / main Translation-nb
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / restricted Translation-nb
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / universe Translation-nb
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / multiverse Translation-nb
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/main Translation-nb
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/restricted Translation-nb
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/universe Translation-nb
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/multiverse Translation-nb
Found [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic / partner Translation-nb
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg [189B]
Found [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-nb
Extract: 2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed Release.gpg
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/restricted Translation-nb
Found [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release [65.9 KB]
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/main Translation-nb
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/multiverse Translation-nb
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-nb
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-nb
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-nb
Found [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / free Translation-nb
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / non-free Translation-nb
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/universe Translation-nb
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic Release
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates Release
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed Release
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Found [http://archive.canonical.com](http://archive.canonical.com) karmic / partner Packages
Found [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / main Packages
Found [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / restricted Packages
Get: 5 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / restricted Sources [3 270B]
Get: 6 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / main Sources [640KB]
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [23.3 kB]
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [577B]
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [6 767B]
Found [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Found [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / free Packages
Get: 10 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic / main Sources [640KB]
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / non-free Packages
Extract: 11 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / multiverse Sources [116KB]
Extract: 12 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / universe Sources [2 795kB]
Get: 13 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic / restricted Sources [3 270B]
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / universe Packages
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic / multiverse Packages
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/main Packages
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/restricted Packages
Extract: 14 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/restricted Sources [14B]
Extract: 15 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/main Sources [55.2 kB]
Extract: 16 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/multiverse Sources [4 025B]
Extract: 17 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/universe Sources [26.9 kB]
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/universe Packages
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/multiverse Packages
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/restricted Packages
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/main Packages
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/multiverse Packages
Found [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/universe Packages
Extract: 18 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/restricted Sources [14B]
Extract: 19 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/main Sources [28.7 kB]
Extract: 20 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/multiverse Sources [14B]
Extract: 21 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-proposed/universe Sources [6 447B]
Ign [http://dl.google.com](http://dl.google.com) stable / non-free Translation-nb
Ign [http://dl.google.com](http://dl.google.com) stable / main Translation-nb
Extract: 22 [http://dl.google.com](http://dl.google.com) stable Release [2 540B]
Extract: 23 [http://dl.google.com](http://dl.google.com) stable / non-free Packages [1 010B]
Extract: 24 [http://dl.google.com](http://dl.google.com) stable / main Packages [922B]
Retrieved 4 420kB in 2min 0s (36.6 kb / s)
W: Could not find cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) / dists/karmic/main/binary-i386/Packages.gz Use 'apt-cdrom "to make this cd available for APT . You can not use "apt-get update" to add new CDs.

W: Could not find cdrom: / / Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) / dists/karmic/restricted/binary-i386/Packages.gz Use 'apt-cdrom "to make this cd available for APT . You can not use "apt-get update" to add new CDs.

E: Could not download all the files list. They were ignored, or old were used instead.

---

### Post by Trandre on 2010-03-14
Synaptic gave this result when attempting to open it(washed through google transelate):

E: Problem parsing dependency Conflicts
E: Error occurred during processing of Xserve xorg-video-cirrus (NewVersion1)
E: Problem with MergeList / var / lib / dpkg / status
E: The package lists or statusfil could be read or opened.
E: _cache-> open () failed, please report.

W: Duplicate sources.list entry [http://dl.google.com](http://dl.google.com) stable / main Packages (/ var/lib/apt/lists/dl.google.com_linux_deb_dists_stable_main_binary-i386_Packages)

---

### Post by Trandre on 2010-03-14
I read in another thread that I should post this command aswell:

famfem @ famfem-desktop: ~ $ software center 
Trace Back (most recent call last): 
  File "/ usr / share / software-center / software center / apt / aptcache.py", line 118, in open 
    self._cache = apt.Cache (GtkMainIterationProgress ()) 
  File "/ usr/lib/python2.6/dist-packages/apt/cache.py", line 72, in __init__ 
    self.open (progress) 
  File "/ usr/lib/python2.6/dist-packages/apt/cache.py", line 108, in open 
    self._cache = apt_pkg.GetCache (progress) 
System Error: E: Problem parsing dependency Conflicts, E: Error occurred during processing of Xserve xorg-video-cirrus (NewVersion1), E: Problem with MergeList / var / lib / dpkg / status, E: Package list or state file could not be interpreted or opens. 
famfem @ famfem-desktop: ~ $ ubuntu-bug software center 
Trace Back (most recent call last): 
  File "/ usr / share / apport / apport-gtk", line 348, in <Module> 
    app.run_argv () 
  File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 435, in run_argv 
    return self.run_report_bug () 
  File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 345, in run_report_bug 
    self.collect_info (symptom_script) 
  File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 601, in collect_info 
    icthread.exc_raise () 
  File "/ usr/lib/python2.6/dist-packages/apport/REThread.py", line 36, in run 
    self._retval = self.__target (* self.__args, ** self.__kwargs) 
  File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 65, in thread_collect_info 
    report.add_package_info (package) 
  File "/ usr/lib/python2.6/dist-packages/apport/report.py", line 186, in add_package_info 
    version = packaging.get_version (package) 
  File "/ usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 65, in get_version 
    pkg = self._apt_pkg (package) 
  File "/ usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 58, in _apt_pkg 
    return self._cache () [package] 
  File "/ usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 49, in _cache 
    self._apt_cache = apt.Cache () 
  File "/ usr/lib/python2.6/dist-packages/apt/cache.py", line 72, in __init__ 
    self.open (progress) 
  File "/ usr/lib/python2.6/dist-packages/apt/cache.py", line 108, in open 
    self._cache = apt_pkg.GetCache (progress) 
System Error: E: Problem parsing dependency Conflicts, E: Error occurred during processing of Xserve xorg-video-cirrus (NewVersion1), E: Problem with MergeList / var / lib / dpkg / status, E: Package list or state file could not be interpreted or opens.

---

### Post by The Real Dave on 2010-03-15
It seems to be complaning that there is a duplicate source in your sources.list file. Try removing this line

```
deb http://dl.google.com/linux/deb/  stable non-free main
```

and running 

```
sudo apt-get update
```

again. 

You can just put a # in front of it and it'll act as if it doesn't exist. 

You also seem to have a CD listed as a repo, which is ok, but causing that error when you run sudo apt-get update. It's nothing to worry about though. 

As for the Norway server, nope, doesn't limit your software choices, its a perfect mirror of the main server.

Software centre seems to be unable to resolve dependancies, but as to what's causing that, I've no idea.  :(

---

### Post by Trandre on 2010-03-15
How do I access this file in order to edit it with the #? 
I found the file but it was locked and not editable.

Trandre

Nevermind, i found the solution in a thread :-) Googl Ubuntu makes the thread search easier

---

### Post by Trandre on 2010-03-15
We are closing in on the issue, because The red stop sign is now gone. :-) But i still cannot see contents in software center and Synaptics returns the following error before closing. 


E: Problem parsing dependency Conflicts
E: Error occurred during processing of Xserve xorg-video-cirrus (NewVersion1)
E: Problem with MergeList / var / lib / dpkg / status
E: The package lists or statusfil could be read or opened.
E: _cache-> open () failed, please report.

---

### Post by Trandre on 2010-03-15
I deleted the google string
I took cdrom away from repository search
And I Manually searched for the optimal mirror. 

Wich gives me these results on the sudo apt-get update:

amfem @ famfem-desktop: ~ $ sudo apt-get update
[sudo] password for famfem:
Found [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic / partner Translation-nb
Found [http://ftp.port80.se](http://ftp.port80.se) karmic Release.gpg
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / free Translation-nb
Found [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / main Translation-nb
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / non-free Translation-nb
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Found [http://archive.canonical.com](http://archive.canonical.com) karmic / partner Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / restricted Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic / universe Translation-nb
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / free Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / multiverse Translation-nb
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-updates Release.gpg
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/main Translation-nb
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / non-free Packages
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/restricted Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/universe Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/multiverse Translation-nb
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-security Release.gpg
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-security/main Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-security/restricted Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-security/universe Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-security/multiverse Translation-nb
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed Release.gpg
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/restricted Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/main Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/multiverse Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/universe Translation-nb
Found [http://ftp.port80.se](http://ftp.port80.se) karmic Release
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-updates Release
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-security Release
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed Release
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / main Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / restricted Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / universe Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / multiverse Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/main Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/restricted Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/universe Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/multiverse Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-security/main Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-security/restricted Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-security/universe Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-security/multiverse Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/restricted Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/main Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/multiverse Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/universe Packages
Ign [http://dl.google.com](http://dl.google.com) stable / main Translation-nb
Extract: 2 [http://dl.google.com](http://dl.google.com) stable Release [2 540B]
Get: 3 [http://dl.google.com](http://dl.google.com) stable / main Packages [922B]
Retrieved 3 651B at 2min 0s (30B / s)
Reading package lists ... Wrong
E: Problem parsing dependency Conflicts
E: Error occurred during processing of Xserve xorg-video-cirrus (NewVersion1)
E: Problem with MergeList / var / lib / dpkg / status
E: Package list or state file could not be interpreted or open.

---

### Post by Trandre on 2010-03-15
Ran the command ubuntu-bug service center and recieved this output:


famfem @ famfem-desktop: ~ $ ubuntu-bug service center 
Trace Back (most recent call last): 
  File "/ usr / share / apport / apport-gtk", line 348, in <Module> 
    app.run_argv () 
  File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 435, in run_argv 
    return self.run_report_bug () 
  File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 345, in run_report_bug 
    self.collect_info (symptom_script) 
  File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 601, in collect_info 
    icthread.exc_raise () 
  File "/ usr/lib/python2.6/dist-packages/apport/REThread.py", line 36, in run 
    self._retval = self.__target (* self.__args, ** self.__kwargs) 
  File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 65, in thread_collect_info 
    report.add_package_info (package) 
  File "/ usr/lib/python2.6/dist-packages/apport/report.py", line 186, in add_package_info 
    version = packaging.get_version (package) 
  File "/ usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 65, in get_version 
    pkg = self._apt_pkg (package) 
  File "/ usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 58, in _apt_pkg 
    return self._cache () [package] 
  File "/ usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 49, in _cache 
    self._apt_cache = apt.Cache () 
  File "/ usr/lib/python2.6/dist-packages/apt/cache.py", line 72, in __init__ 
    self.open (progress) 
  File "/ usr/lib/python2.6/dist-packages/apt/cache.py", line 108, in open 
    self._cache = apt_pkg.GetCache (progress) 
System Error: E: Problem parsing dependency Conflicts, E: Error occurred during processing of Xserve xorg-video-cirrus (NewVersion1), E: Problem with MergeList / var / lib / dpkg / status, E: Package list or state file could not be interpreted or opens

---

### Post by The Real Dave on 2010-03-15
Again, it seems like there's a problem resolving dependancies. As to what's causing that, or how to solve it, I havn't a clue. Sorry I can't be of more help :(

---

### Post by Trandre on 2010-03-15
Thanks, Dave. You have allready helped a lot. Now that you have singeled out what the problem is, it is a short way to solve it. 

Thanks again

Trandre

I think I'll close this link and post a more spesific one

---

### Post by Trandre on 2010-03-20
Solved in this thread:

[http://ubuntuforums.org/showthread.php?t=1430660](http://ubuntuforums.org/showthread.php?t=1430660)

Trandre

---

