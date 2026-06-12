---
title: "Any advice on miscellaneous odd problems?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by dxgc on 2010-12-22
I have a bunch of odd problems. I'm not asking for a solution but am hoping for a suggestion or two about where I can go to do more research.

My system works well enough to use but does not work well. I have a feeling that I might have subtle cpu or memory issues, but don't know how to verify this.

I bought a ZaReason Limbo 4110 ($299 base) basically as insurance. (Since then I've had two older computers die, so it was a good bet, and now it's one of two machines I use daily.) My other box is a ZaReason 2440, and I've had no problems with it.

About two days after I got this box, I ran a routine update (on Kubuntu 9.10) and I lost video on bootup, right after the splash screen -- everything went to black.

I installed Mint7 KDE, which seemed to work OK as I remember, but didn't use the computer extensively since I didn't need it.

I'm currently using Mint9 KDE, which is about the only thing that works well enough to use.

I've tried these:
  - Kubuntu 10.04 (installed, didn't work well, I think Firefox didn't work)
  - Kubuntu 9.04 (installed, Firefox didn't work)
  - Mepis 8 (installed, Firefox didn't work unless I simultaneously used Konqueror, site by site (!))
  - Mint 10 (looks nice, works OK from the live CD, but I haven't tried installing it)
  - Mint9 XFCE (installed, worked mostly OK until it locked me out)
  - OpenSuse 11.2 (ran from live CD, but I think Firefox didn't work, even from there)
  - Ubuntu 10.10 (ran from live CD, Firefox didn't work, even from there)
  - Ubuntu 10.10 (ran under VirtualBox but Firefox didn't work, deleted it all)
  - Xubuntu 10.04 (installed, worked mostly OK until it locked me out)

My basic problems: 

- the software updater usually can't connect to the internet, though it does sometimes, on no particular schedule

- I do system updates via a script run from the command line, which *almost* always works

- Firefox and Chrome work, but every now and then my internet connection drops, sometimes degrading site by site until I have to reboot - then everything is fine for the rest of the day

- after a reboot due to loss of internet connection, Mintupdate works

- I have emacs configured so I can send email from it through Gmail, but this doesn't work until I'm forced to reboot after the internet connection fails - then it works flawlessly; it has worked without fail on my other computer (different hardware and OS)

- some odds and ends: 

- screensaver doesn't work unless I manually start its daemon

- desktop shortcuts that I set up don't work (on the other box I use Ctrl-7 to start Firefox; that works there but not on this box; I have to use the mouse)

- Mint9 XFCE worked better than Mint9 KDE, but after about two weeks it locked me out; I managed to get back in by logging on as root, but could not reset the password; I chose a new password and things were OK for a couple of days; then I was locked out again, so I tried Xubuntu 10.04

- Xubuntu 10.04 worked, but after about two days it locked me out, hard, and I could not log in at all, by any means, so I switched to Mint9 KDE

- I switched cables to my DSL modem: no change

- I put in a spare ethernet card that I had and the system sees it but I can't connect with it and I don't know how; but I don't feel like this is the problem since when the internet connection is fully working it's fully working, though it doesn't always get to that state

- I found a note about the "lshw" and "lspci" commands and ran them to generate info about the system, but don't know what to do with the info, though if anyone can make sense of it I can post it all

---

### Post by cariboo on 2010-12-22
It would probably be best if you posted the output of lspci and lshw, that way we can see what your hardware is and if the correct drivers are being loaded. Please use code tags ([noparse]```

```[/noparse]) to make the listings easier to read.

---

### Post by inkrypted on 2010-12-22
Most of your problems seem Internet related. Are you on a wired or wireless connection? WICD has a KDE client now and I would say this is the preferred method of dealing with most connections as the KDE network manager seems to be lacking in that area. As for the screen saver problem I had the same my solution was to disable the KDE screen savers and power daemon then install xscreensavers and use a script to start it at boot up. Also alot of the problems you described also sound like DNS server issues. You might try using OpenDNS or try running a local DNS server such as Unbound.

Links

WICD
[http://kde-apps.org/content/show.php/Wicd+Client+KDE?content=132366](http://kde-apps.org/content/show.php/Wicd+Client+KDE?content=132366)

OpenDNS
[http://www.opendns.com](http://www.opendns.com)

Unbound DNS
[http://www.unbound.net](http://www.unbound.net)

If you need scripts or config files I am happy to share just let me know. Best of luck;)

---

### Post by dxgc on 2010-12-22
> **cariboo907 said:**
> It would probably be best if you posted the output of lspci and lshw, that way we can see what your hardware is and if the correct drivers are being loaded. Please use code tags ([noparse]```

```[/noparse]) to make the listings easier to read.

Okie-Dokie. I realize that mine is a really vague question, but any help will be appreciated.

**lshw output:**
```

    description: Desktop Computer
    product: G41M-ES2L
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-00241DBE1130
  *-core
       description: Motherboard
       product: G41M-ES2L
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F4 (07/22/2009)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          slot: Socket 775
          size: 2GHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
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
          physical id: 19
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM 800 MHz (1.2 ns)
             physical id: 2
             slot: A2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
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
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:27 memory:e3000000-e33fffff memory:d0000000-dfffffff(prefetchable) ioport:e400(size=8)
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
             resources: irq:16 memory:e3500000-e3503fff
        *-pci:0
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
             resources: irq:24 ioport:1000(size=4096) memory:80000000-801fffff memory:80200000-803fffff(prefetchable)
        *-pci:1
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
             resources: irq:25 ioport:c000(size=4096) memory:e0000000-e0ffffff ioport:e3400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:24:1d:be:11:30
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:26 ioport:c000(size=256) memory:e3410000-e3410fff(prefetchable) memory:e3400000-e340ffff(prefetchable) memory:e3420000-e342ffff(prefetchable)
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
             resources: irq:23 ioport:e000(size=32)
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
             resources: irq:19 ioport:e100(size=32)
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
             resources: irq:18 ioport:e200(size=32)
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
             resources: irq:16 ioport:e300(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e3504000-e35043ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:d000(size=4096) memory:e1000000-e2ffffff memory:80400000-804fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 21x4x DEC-Tulip compatible 10/100 Ethernet
                vendor: Davicom Semiconductor, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 31
                serial: 00:08:a1:60:ee:90
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=dmfe driverversion=1.36.4 latency=64 link=no maxlatency=40 mingnt=20 multicast=yes
                resources: irq:20 ioport:d000(size=256) memory:e2000000-e20000ff memory:80400000-8043ffff(prefetchable)
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
        *-ide
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7240S
                vendor: Optiarc
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: ST3320613AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: CC2J
                serial: 9SZ5P0BE
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00069522
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 10ae5647-735e-4744-a138-94be872d4262
                   size: 292GiB
                   capacity: 292GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-09-26 10:16:48 filesystem=ext4 lastmountpoint=/ Š]   t      h                  p   _   u^    U/   d   _   ~!   h         h            t                _      _   a modified=2010-12-16 12:31:14 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-12-16 12:31:14 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 5796MiB
                   capacity: 5796MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5796MiB
                      capabilities: nofs
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
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
        *-disk:4
             description: SCSI Disk
             physical id: 0.0.4
             bus info: scsi@2:0.0.4
             logical name: /dev/sdf

```

**lspci output:**
```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

```

---

### Post by dxgc on 2010-12-22
> **inkrypted said:**
> Most of your problems seem Internet related. Are you on a wired or wireless connection? WICD has a KDE client now and I would say this is the preferred method of dealing with most connections as the KDE network manager seems to be lacking in that area. As for the screen saver problem I had the same my solution was to disable the KDE screen savers and power daemon then install xscreensavers and use a script to start it at boot up. Also alot of the problems you described also sound like DNS server issues. You might try using OpenDNS or try running a local DNS server such as Unbound.

Links

WICD
[http://kde-apps.org/content/show.php/Wicd+Client+KDE?content=132366](http://kde-apps.org/content/show.php/Wicd+Client+KDE?content=132366)

OpenDNS
[http://www.opendns.com](http://www.opendns.com)

Unbound DNS
[http://www.unbound.net](http://www.unbound.net)

If you need scripts or config files I am happy to share just let me know. Best of luck;)


Thanks for your response. Again, sorry for the vague collection of symptoms that isn't quite a question, but that's what I have to work with.

*** Connection:** wired, DSL

*** Screen saver:** That's where I am now too. It sort of works but aint' the right way. I threw it in with the rest just in case it might give a clue.

*** DNS server issues, etc:** I have two computers using the same connection. Usually only one is on at a time, but when both are running things are no worse or better.

At times I do have pages stalling in the middle of loading, but can live with that. I just keep kicking them until they finish.

The real issues are 

* the update manager not working and 

* the inability to send email through emacs. 

Emacs is really handy as a way to send quick notes to myself.

And as I said, some times (once a day only) I lose my internet connection and after rebooting the update manager and emacs mail work perfectly for the rest of the day.

Though many web pages are slow to load, I have NONE of these other, real problems on my other computer (slightly more expensive hardware running Kubuntu 8.04).

I'll take a look at OpenDNS, Unbound, and WICD. Thank you for the suggestions.

---

### Post by mysteriousdarren on 2010-12-22
This to me sounds like a unsupported hardware problem. Several times I had trouble using firefox amd just took it off and installed the most current and it worked. Go to a different site if its a laptop and see if its the internet, that can't hurt. What distro for sure did you want to use? I had one computer that was having trouble with the internet on every ubuntu distro until I installed Backtrack 4r2 on it and it works like a charm. Good luck with getting things fixed. I will keep an eye out and see if I can help. Sometimes its just finding the right distro that works.

---

### Post by inkrypted on 2010-12-23
I tend to agree with MysteriousDarren now it does sound like unsupported hardware. This is gonna sound bad especially posting it here but if it's a notebook I always had really good luck with OpenSUSE no matter the desktop it just seems to have better notebook support especially in the power management department. ( Forgive me Ubuntu and Kubuntu Gods );)

---

### Post by mysteriousdarren on 2010-12-23
Well I don't agree with the powermanagment part(install jupiter), but realize that you have to use what works for you even if its not *buntu.

---

### Post by dxgc on 2010-12-24
Thanks to everyone who took a look at this. It was worth a shot, but I think the problem is too vague and transient to figure out. I'll have to keep thinking about it and observing, though I suspect that some piece of hardware on my particular computer is not quite right.

-- Dave

---

