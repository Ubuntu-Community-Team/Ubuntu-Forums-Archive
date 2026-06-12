---
title: "Dont like UBUNTU"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by Patrikf on 2009-10-07
I ran WinXP for 3yrs and pretty much had it down, no spy-ware, no viruses, no crashes, no problems and it was fast when browsing, playing games etc.
Switched to UBUNTU very recently and i gotta say i dont like it......I LOVE IT!  Nothing works (for me) and its super slow wont even play DVDs lol, but am i having fun trying to solve all my problems, not done this much reading since leaving school (many many years ago) ,is it just me or does every answer found in ubuntu lead to a ton more questions, i got like 50 firefox pages open.
Its kind of like playing a point and click adventure game, and i have to reach the end. GREAT!

I have had great help from reading posts and the nice ppl that have gave me pointers and while not wanting to be spoon fed (coz im literally gonna be soon, very very old) i need an answer to the question of whether i will be able to complete this "game"

Is it possible to speed ubuntu up to the same lvl as xp?
will i be able to play MOH and WOW?
Is my old laptop not good enough?
will there be support for i915g gfx?
will i have to build my own kernel?
learn programming lang?

I aint never goin back to windows its sooooooooooooo boring
I got a DVD player and my son got 360 and ps3 psp etc so movies and 3D games are covered

Thankyou UBUNTU for reignighting my love of PC tinkering again

---

### Post by scorp123 on 2009-10-07
Must be your PC. On my systems any Linux works out of the box. All that I need to do in the case of Ubuntu is to add the multimedia codecs they can't ship with for legal reasons but that's about it.

While you're at it ... please read this:

"Linux is not Windows"
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by sandyd on 2009-10-07
> **Patrikf said:**
> 
--snip--

Is it possible to speed ubuntu up to the same lvl as xp?
will i be able to play MOH and WOW?
Is my old laptop not good enough?
will there be support for i915g gfx?
will i have to build my own kernel?
learn programming lang?

--snip--
1. its probably because you haven't installed your graphics drivers yet.
since i see you have the intel cards, ill point you to 
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

2. WOW, YES, you need to install WINE
```

sudo apt-get install wine cabextract
cd /usr/bin
wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks

```
that will install WINE (and winetricks)
you then wanna see here
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421)

for the howto

3. i made a pentium 3 500mhz run ubuntu. yours is definately good enough

4. see 1.

5 & 6 no to both, unless you want to create your own programs or do kernel modifications (which you don't need to do)

have a great time using ubuntu ;)

---

### Post by Patrikf on 2009-10-07
I already read this but think you answered my question anyway.
PC runs super fast on windows and as ubuntu is at least comparable to XP i think maybe its the user.

---

### Post by antony.s on 2009-10-07
For DVDs, please read [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Patrikf on 2009-10-07
I got wine up and running but games are very slow as are ubuntu games ive tested (scorched earth) etc.
great to know you got ubuntu working on a lower spec system, gonna go follow your links many thanks again.
 OH and DVDs but very choppy and slow.

---

### Post by halitech on 2009-10-07
you don't really specify what the specs are of your machine so its hard to say how well it should run. Can you provide the model or the output of
```
lshw
```

if its not installed, run this
```
sudo apt-get install lshw
```

---

### Post by MegaJim on 2009-10-07
I remember that feeling! Free software is awesome.

---

### Post by Patrikf on 2009-10-07
```
laptop@laptop-laptop:~$ sudo lshw
laptop-laptop             
    description: Notebook
    product: VGN-FS415B
    vendor: Sony Corporation
    version: C3LLXA5J
    serial: 28196850-5004631
    width: 32 bits
    capabilities: smbios-2.34 dmi-2.34
    configuration: boot=normal chassis=notebook uuid=5A7D2E00-8B1A-11DA-824E-00014AF04514
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0090J1 (10/25/2005)
          size: 111KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.73GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 6.13.8
          slot: N/A
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back data
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 6
             slot: L3 Cache
             capabilities: burst data
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM DDR 533 MHz (1.9 ns)
             product: N/A
             vendor: N/A
             physical id: 0
             serial: N/A
             slot: SODIMM1
             size: 512MiB
             width: 32 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: SODIMM DDR 533 MHz (1.9 ns)
             product: N/A
             vendor: N/A
             physical id: 1
             serial: N/A
             slot: SODIMM2
             size: 512MiB
             width: 32 bits
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
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
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
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
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
        *-usb:3Jessica
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
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
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCI7420 CardBus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:06:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
                vendor: Texas Instruments
                physical id: 3.2
                bus info: pci@0000:06:03.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3 module=ohci1394
           *-storage
                description: Mass storage controller
                product: PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
                vendor: Texas Instruments
                physical id: 3.3
                bus info: pci@0000:06:03.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:06:04.0
                logical name: eth1
                version: 05
                serial: 00:16:6f:22:63:0e
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.2.7 latency=32 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
           *-network:1
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:06:08.0
                logical name: eth0
                version: 03
                serial: 00:01:4a:f0:45:14
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
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
                product: SAMSUNG MP0402H
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: UC20
                serial: S03WJ10YB89969
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ac46ac46
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: cb04b3b7-bbbe-4ff1-b354-b892fafc9cbe
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-10-02 19:52:04 filesystem=ext3 modified=2009-10-07 15:09:02 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-10-07 11:42:10 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1608MiB
                   capacity: 1608MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1608MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: COMBO LSC-24082K
                vendor: Slimtype
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: JWK2
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
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
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:22:d3:4f:0e:c5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
laptop@laptop-laptop:~$
```

---

### Post by halitech on 2009-10-07
ok, definately should have no issues with running Ubuntu on this machine. Its a Pentium M 1.73ghz with a gig of ram. Only downside I see is the Intel 915 video card which is being a real pain in 9.04 right now. I don't have one but I've seen alot of issues lately. See here for more details and a resolution: 

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by jmszr on 2009-10-07
patrikf,


Welcome aboard!


You will need to install:

```
sudo apt-get install ubuntu-restricted-extras
```

Also, you should install the Medibuntu repository: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

As part of installing medibuntu, be sure that you install:

```
sudo apt-get install w32codecs
```

and:

```
sudo apt-get install libdvdcss2
```

That should deal with your DVD issues.

Also, I suggest that you install the VLC media player:

```
sudo apt-get install vlc
```

It is kinda fun, isn't it?

---

### Post by Patrikf on 2009-10-07
Thanks i got em all already...I really have read every guide lol.
appears ive finally broken it though getting error:[B] E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read[/B]. whenever i try my CLI commands.
Had to happen eventually.
Oh and the compiz stuff was really fun.

Scratch that, works fine if i dont use the drivers source code address in the repos.

---

### Post by tom66 on 2009-10-07
Can you run:

```

sudo cat /etc/apt/sources.list

```

and paste it here so we can see where the problem is in your sources file.

---

### Post by Patrikf on 2009-10-07
laptop@laptop-laptop:~$ sudo cat /etc/apt/sources.list
[sudo] password for laptop: 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) jaunty main
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu) hardy main
deb [http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu) hardy main


# deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty
laptop@laptop-laptop:~$

---

### Post by ConXtionS on 2009-10-07
I admit that I am not a ubuntu CONVERT yet.... 
 
However I agree it is great fun learning all of this "stuff"  I just wish it wasnt SOOOOO overwhelming...
 
Anyhow.. ,from one noob to another I wish you the best
 
Jim

---

### Post by CatKiller on 2009-10-07
> **Patrikf said:**
> getting error:[B] E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read[/B]. whenever i try my CLI commands.

> **Patrikf said:**
> 
```
 # deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty
```
laptop@laptop-laptop:~$

As you've already found, this is line 60. The problem is that although you've defined the distribution (*jaunty* in this case) you haven't defined the section which, for this repository, would be one, some, or all, of *main*, *restricted*, *universe*, or *multiverse*.

You've probably already discovered the distinctions between these sections from your other adventures in adding software sources.

Good luck with your continued explorations, and welcome to the community.

---

### Post by starcannon on 2009-10-07
> **Patrikf said:**
> I ran WinXP for 3yrs and pretty much had it down, no spy-ware, no viruses, no crashes, no problems and it was fast when browsing, playing games etc.
Switched to UBUNTU very recently and i gotta say i dont like it......I LOVE IT!  Nothing works (for me) and its super slow wont even play DVDs lol, but am i having fun trying to solve all my problems, not done this much reading since leaving school (many many years ago) ,is it just me or does every answer found in ubuntu lead to a ton more questions, i got like 50 firefox pages open.
Its kind of like playing a point and click adventure game, and i have to reach the end. GREAT!
You sir have a geeks heart!
Okay, be sure to check out [Medibuntu]("http://www.medibuntu.org/") for getting your multimedia needs up to snuff. Tip install libdvdcss, and ubuntu-restricted-extras.
As far as reaching the end; well, in this game *You* decide when you've reached the end, there is no limit to what you can do with your computer when you start playing with an OS that lets you have a full access pass. 
> 
I have had great help from reading posts and the nice ppl that have gave me pointers and while not wanting to be spoon fed (coz im literally gonna be soon, very very old) i need an answer to the question of whether i will be able to complete this "game"
By the sounds of your appetite for learning, I think you'll need a bigger spoon, perhaps "shovel fed" would be more appropriate :)
> 

[LIST=1]
[*] Is it possible to speed ubuntu up to the same lvl as xp?
[*] will i be able to play MOH and WOW?
[*] Is my old laptop not good enough?
[*] will there be support for i915g gfx?
[*] will i have to build my own kernel?
[*] learn programming lang?
[/LIST]
1) For me, outta the box, Ubuntu is faster than XP, perhaps you need some modules/drivers that are missing. Beyond that, you can whittle down the kernel, and the processes that happen at boot, until you get a very lean and mean machine. There are people that like to challenge themselves by finding out how fast they can make their Linux based operating system boot; perhaps after you've cut your teeth on the basics, you may find that to be an interesting "game".

2) I have played WoW on my Ubuntu Linux install using both the Wine and the Cedega method; I prefer Cedega, but your geeky enough at heart to possibly prefer Wine. Not that you have to be a super geek to use Wine, but I do find Cedega easier. I don't know what MOH is, so you'd need to head over to [http://www.winehq.org/](http://www.winehq.org/) and dig around to see if and how well that game is supported.

3) Most likely yes, but attaching the output of ```
sudo lshw > ~/Desktop/hardware.doc
``` would help us to help you better determine what if any hardware problems you may be facing.

4) I will have to allow someone else to better answer this question, I have had no problems with intel gpu chipsets, but on those machines that use them, I have not tried to do any 3D gaming.

5) No, you don't "have to", but considering your interests, you might "want to".

6) No need to learn a programming language, but it is fun, and you could find a great deal of satisfaction from the fruits of doing so, but most never bother. May I recommend [Python]("http://wiki.python.org/moin/BeginnersGuide")?
> 
I aint never goin back to windows its sooooooooooooo boring
I got a DVD player and my son got 360 and ps3 psp etc so movies and 3D games are covered
That's certainly one way of considering things; the other way of considering things, is that it does not have to be an either or situation. You can have both. Windows for those things that won't work properly in Linux, and Linux for everything else. May I suggest a dual boot scenario, where you get to choose which OS to boot into from the Grub Menu? If you decide to do this, and if you are going to be required to do full reinstalls to pull it off, perhaps find out how to set up [Ubuntu with its own seperate /home partition]("http://www.psychocats.net/ubuntu/installseparatehome"); it makes recovering from experimentation gone wrong so much more tolerable. If you'd like to set an existing Ubuntu install up with a separate /home partition without being troubled to reinstall, [check out this guide]("http://www.psychocats.net/ubuntu/separatehome").
> 
Thankyou UBUNTU for reignighting my love of PC tinkering again
I know how you feel, when you first get into Linux, it's a lot like getting your first shiny new computer again for the first time. Enjoy the journey.

---

### Post by sandyd on 2009-10-07
type in
```

gksudo gedit /etc/apt/sources.list

```
replace everything inside with
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://deb.playonlinux.com/ jaunty main
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu hardy main
deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu hardy main
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
```

---

### Post by Patrikf on 2009-10-07
I can also remember a time when windows was overwhelming.  thanks Jim NOOBS ROCK!

Aha a clue, thanks CatKiller.

Hey Starcannon thanks for advice taken onboard. Cedega is on the todo list but i fear Python (tried it a long time ago after hearing a guy wrote the entire program for that two wheeled stand on scooter thingy in a couple of hours) just seem to get lost in the loop inside a loop inside a loop, end up writing very very long programs that could be done by an expert in twenty lines of code, but good to know i chose a good one in the first place. Think i like learning languages in nibbles lol.
As for windows, i was dual booting to start and felt like i had a safety net, bit like not playing wow on a PVP server took a little of the excitment away if you know what i mean.

I redone my sources list carlee and updates working fine, however think i got wrong drivers as performance it worse than ever after trying the bleeding edge method (mouse feels like its dragging) noticed there was a touch pad update so ill try this first then revert back to the driver i was most successful with. maybe i got here at the wrong time with all the probs with intel drivers?.....then again maybe its the right time....more fun lol.

Sorry for long post ill leave you all alone now and thanks again for the welcome, the advice and encouragement.

---

### Post by guriinii on 2009-10-07
Ubuntu is a massive learning curve and scary as hell, but really, really fun. I've broke it so many times!

Have a look at this Terminal guide, it helped me loads:
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

Happy Terminalling!

---

### Post by sandyd on 2009-10-07
> **Patrikf said:**
> I can also remember a time when windows was overwhelming.  thanks Jim NOOBS ROCK!

Aha a clue, thanks CatKiller.

Hey Starcannon thanks for advice taken onboard. Cedega is on the todo list but i fear Python (tried it a long time ago after hearing a guy wrote the entire program for that two wheeled stand on scooter thingy in a couple of hours) just seem to get lost in the loop inside a loop inside a loop, end up writing very very long programs that could be done by an expert in twenty lines of code, but good to know i chose a good one in the first place. Think i like learning languages in nibbles lol.
As for windows, i was dual booting to start and felt like i had a safety net, bit like not playing wow on a PVP server took a little of the excitment away if you know what i mean.

I redone my sources list carlee and updates working fine, however think i got wrong drivers as performance it worse than ever after trying the bleeding edge method (mouse feels like its dragging) noticed there was a touch pad update so ill try this first then revert back to the driver i was most successful with. maybe i got here at the wrong time with all the probs with intel drivers?.....then again maybe its the right time....more fun lol.

Sorry for long post ill leave you all alone now and thanks again for the welcome, the advice and encouragement.
acccccccckkkkkkkkkk........
intel drivers on jaunty were always a bit buggy to begin with.
I never had an intel card myself, so i can't say for everybody, but perhaps they will improve with the release of Karmic

---

### Post by sandyd on 2009-10-07
hmm....
lets try something different.....
```

sudo gedit /etc/apt/sources.list 
```
[/code]
add this to the bottom 
```

deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main 
```

then run
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [AF1CDFA9               ]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9&op=index")               
sudo apt-get update
sudo apt-get install                 xserver-xorg-video-intel

```

---

### Post by Cresho on 2009-10-07
ITS OKAY!  stay with your windows xp.  It's an os made for children.  my 3 year old who reads uses it just fine!  He cant use ubuntu yet but he is getting there.

---

### Post by praveesh on 2009-10-07
Did you try installing windows xp . Could you get your dvd working in it without installing any drivers and third party applications? You may want to try KUBUNTU , A sister operating system of Ubuntu . If you have  good graphics , KUBUNTU will be faster than xp. I would like to recommend you installing the upcoming version of KUBUNTU (9.10) . It is more faster.

---

### Post by thiebaude on 2009-10-07
I just noticed the last 2 lines in his sources list.He has 2 hardy entries.He is mix matching them.

---

### Post by crjackson on 2009-10-07
> **Patrikf said:**
> ```
laptop@laptop-laptop:~$ sudo lshw
laptop-laptop             
    description: Notebook
    product: VGN-FS415B
    vendor: Sony Corporation
    version: C3LLXA5J
    serial: 28196850-5004631
    width: 32 bits
    capabilities: smbios-2.34 dmi-2.34
    configuration: boot=normal chassis=notebook uuid=5A7D2E00-8B1A-11DA-824E-00014AF04514
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0090J1 (10/25/2005)
          size: 111KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.73GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 6.13.8
          slot: N/A
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back data
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 6
             slot: L3 Cache
             capabilities: burst data
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM DDR 533 MHz (1.9 ns)
             product: N/A
             vendor: N/A
             physical id: 0
             serial: N/A
             slot: SODIMM1
             size: 512MiB
             width: 32 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: SODIMM DDR 533 MHz (1.9 ns)
             product: N/A
             vendor: N/A
             physical id: 1
             serial: N/A
             slot: SODIMM2
             size: 512MiB
             width: 32 bits
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
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
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
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
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
        *-usb:3Jessica
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
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
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCI7420 CardBus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:06:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
                vendor: Texas Instruments
                physical id: 3.2
                bus info: pci@0000:06:03.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3 module=ohci1394
           *-storage
                description: Mass storage controller
                product: PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
                vendor: Texas Instruments
                physical id: 3.3
                bus info: pci@0000:06:03.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:06:04.0
                logical name: eth1
                version: 05
                serial: 00:16:6f:22:63:0e
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.2.7 latency=32 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
           *-network:1
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:06:08.0
                logical name: eth0
                version: 03
                serial: 00:01:4a:f0:45:14
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
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
                product: SAMSUNG MP0402H
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: UC20
                serial: S03WJ10YB89969
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ac46ac46
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: cb04b3b7-bbbe-4ff1-b354-b892fafc9cbe
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-10-02 19:52:04 filesystem=ext3 modified=2009-10-07 15:09:02 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-10-07 11:42:10 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1608MiB
                   capacity: 1608MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1608MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: COMBO LSC-24082K
                vendor: Slimtype
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: JWK2
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
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
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:22:d3:4f:0e:c5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
laptop@laptop-laptop:~$
```

I would recommend Ubuntu 8.04 for that machine due to the Intel Graphics controller.  9.10 will probably work okay, but it's not released.  One of my laptops has that graphics controller and I run version 8.04 for that reason.

Linux does have some decent games, but no where near the same as windows.  It will get there some day but the user base is currently small compared to windows.  If gaming is your main interest then keep windows around for that purpose.

I suspect that you slow/sluggish performance complaints will go away if you install 8.04 on this machine.

To solve your video playback problems, open a terminal and past in the following as one long chunk of text.  Hit enter, put in your password and hit enter again.  Sit back and it will take care of the rest.

```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 totem-xine xine-ui libxine1 libxinerama1 libxine1-all-plugins libxine1 libxine1-ffmpeg libdvdnav4 libdmx1 libdvdread4 gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly vlc smplayer smplayer-themes smplayer-translations && sudo /usr/share/doc/libdvdread4/install-css.sh
```

That take care of all your video files & DVD needs.

Peace

---

### Post by anewguy on 2009-10-07
You also mentioned compiz - if you are using this you may want to disable it and then try a DVD again.  Sometimes the eye candy can mess up the video playback.

I also agree on trying 8.04 on the system because of the graphics controller. 9.04, as you've probably noticed from searching the forum, doesn't do real well with your graphics controller, but the earlier version did.  I don't remember if 8.10 did as well.  If you need help locating 8.04 for download just let us know.  It should help some things quite a bit as the video can also make the system seem sluggish and "jumpy".

Dave :)

---

### Post by Kapitän Rotbart on 2009-10-08
Oh gee, please no bashing Intel graphics cards. Granted I've never got an Intel graphics card that was designed for gaming (though DirectX/OpenGL would always work, Vista Aero capable meaning Compiz flies like a kite at full blown speed)...Nvidia would always require restricted drivers and ATI had huge compatibility issues with Ubuntu...I'd say Intel graphics cards would be "playing it safe".

---

### Post by anewguy on 2009-10-08
> **Kapitän Rotbart said:**
> Oh gee, please no bashing Intel graphics cards. Granted I've never got an Intel graphics card that was designed for gaming (though DirectX/OpenGL would always work, Vista Aero capable meaning Compiz flies like a kite at full blown speed)...Nvidia would always require restricted drivers and ATI had huge compatibility issues with Ubuntu...I'd say Intel graphics cards would be "playing it safe".

We aren't bashing the adapter but rather the support for it in 9.04 that seems a little flaky.

Dave :)

---

### Post by Patrikf on 2009-10-08
Cresho, why all the hostility man. At 3 years the Park beats any OS

---

### Post by Patrikf on 2009-10-08
Tried that carlee, still no joy and thanks for the effort.
Gonna take u guys advice and install 8.04.
and amended source list #deb-src [http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu) hardy main
                                    #deb [http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu) hardy main

---

### Post by Cresho on 2009-10-09
> **Patrikf said:**
> Cresho, why all the hostility man. At 3 years the Park beats any OS

yes but he loves his xp!  It wasn't a hostile attack.  I'm just saying that xp is easier to use.  That's all.  He also spends more time at the park.

---

### Post by Patrikf on 2009-10-09
Glad to hear it, my bads.
sorry man.

---

