---
title: "Power saving and the Terminal"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by onamattuphere on 2010-01-16
I currently am living in Nepal for my studies. This means we currently have regulated power cuts 8 hours every day!
So I want to squeeze every single second out of my laptop battery.

I am getting more familiar with the terminal and can do everything I need for my studies within the terminal. My thought was that I would get more time on battery power if I run in terminal mode only, but this doesn't seem to be the case. It actually seems to be the opposite; that I get more time when running in Gnome.

I am running some power saving scripts that I found on this forum.
Does my power saving scripts get "unactivated" when I press Ctrl+ALt+F2 and do:
```
killall gdm
```

I also am running powertop and disable as much as possible; i.e hald, Apache and NetworkManager.

Please help a total n00b with increasing my love for the Terminal and making Ubuntu work for my specific needs.

(All power saving tips are also welcome)

---

### Post by warfacegod on 2010-01-16
I can't help you with the Terminal in the way you are looking to use it. I do, however, suggest that you check your BIOS for a CPU setting to throttle back your CPU.

---

### Post by MarkC502 on 2010-01-16
I am not sure with that info but I am thinking maybe when you are shutting down gdm it turning off something else that is actually helping ( like acpi functionality or cpu throttling ). Unfortunately while I love Linux and use it almost exclusivly for my personal computing I have found that it is generally not as good at power management on laptops as XP but you can tweak it quite a bit if you want to spend the time. Last time I messed with it I made  a power saving startup script for my laptop in Ubuntu Gutsy and had it dimming the screen backlight and spinng down hard disk etc and got 25% more run time but with less bright screen and laptop that started going to sleep a few minutes after you stopped touching it so it was a tradeoff.

Tough luck on the electricity shutdowns that is no good. I also must say a spare battery would be the best bet as it always is with laptops, although expensive. Another option I have used here during a bad ice storm when everyone lost power I used a $20 DC-TO-AC converter that you plug into a cars cigarette lighter to charge my laptop so we could all watch movies for like 3 days so if you or a friend have a car then that might be a way to try and get power when needed.

Good luck with your studies.

---

### Post by lukeiamyourfather on 2010-01-17
Agreed that using hardware power saving features like running the CPU at a lower clock speed will have the greatest affect on battery life. Not sure what your budget is like but there are alternatives too.

[http://www.treehugger.com/files/2008/10/7-portable-solar-laptop-chargers-worth-considering.php](http://www.treehugger.com/files/2008/10/7-portable-solar-laptop-chargers-worth-considering.php)

There's many generic 12V solar systems out there that could easily charge or power a laptop from a inverter and 12V battery. Cheers!

---

### Post by warfacegod on 2010-01-17
> **lukeiamyourfather said:**
> Agreed that using hardware power saving features like running the CPU at a lower clock speed will have the greatest affect on battery life. Not sure what your budget is like but there are alternatives too.

[http://www.treehugger.com/files/2008/10/7-portable-solar-laptop-chargers-worth-considering.php](http://www.treehugger.com/files/2008/10/7-portable-solar-laptop-chargers-worth-considering.php)

There's many generic 12V solar systems out there that could easily charge or power a laptop from a inverter and 12V battery. Cheers!

Solar is an excellent idea +1.

---

### Post by onamattuphere on 2010-01-17
Thanks for all the feedback!

There are many inverters in the valley. However the problem is that overall, they raise the collective power consumption, which ultimately might contribute to increased power cuts. Until there's enough water to run the hydro-electric plants on full efficiency, we're all cursed with these cuts.

I love the solar-charging. It would be a great overall solution for many people here.

I'm on a tight budget and I've already spent money on an 8 cell battery which is supposed to arrive in two weeks. Solar charger is now on my wish list..


Thanks for the heads up on script behavior after shutting off GDM I have to work with ubuntu tweaks. All I need my computer for while it's on battery, is to grep a 20MB textfile (a dictionary).

How do I check if my scripts are running after I've killed off GDM?

How do I check if my both my cpu's are running on the lowest frequency using terminal commands?

Would also be great to learn how to have an option in GRUB where I can choose to boot straight into the terminal (with all power saving scripts running of course).

I have checked my BIOS and it's the most boring BIOS I've ever come across. Can't fiddle around with anything, save passwords and boot order.

Here's the output of my lshw in case anyone would be bothered to check it out:
```
description: Notebook
    product: Aspire 5610Z
    vendor: Acer
    version: V3.50
    serial: LXAGQ0X1777260EB851601
    width: 32 bits
    capabilities: smbios-2.33 dmi-2.33 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=01DD7525-92DB-FE4E-AA8B-001B381F37AA
  *-core
       description: Motherboard
       product: Grapevine
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXAGQ0X1777260EB851601
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V3.50 (02/13/2007)
          size: 101KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2080  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          slot: U1
          size: 1733MHz
          capacity: 1733MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr cpufreq
          configuration: id=1
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: burst internal write-back
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
          physical id: a
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: M2
             size: 1GiB
             width: 32 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 1733MHz
          capacity: 1733MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G70 [GeForce Go 7600]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
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
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1b:77:36:5b:fd
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
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
             capabilities: uhci bus_master
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
             capabilities: uhci bus_master
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
             capabilities: uhci bus_master
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
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: eth0
                version: 02
                serial: 00:1b:38:1f:37:aa
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
           *-system
                description: SD Host controller
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=sdhci latency=0 maxlatency=72 mingnt=32 module=sdhci
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
           *-memory:2
                description: FLASH memory
                product: SD/MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: driver=sdhci latency=0 maxlatency=72 mingnt=32 module=sdhci
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
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST9160821AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AL
                serial: 5MA33H4Z
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ecd1691c
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 623759fb-d9ec-f24e-a592-0450b9fef15a
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-31 18:02:55 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 137GiB
                   capacity: 137GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /media/disk
                      capacity: 122GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 13GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 666MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DS8A1P
                vendor: Slimtype
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CA11
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
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
     *-scsi
          physical id: 2
          bus info: usb@5:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: DataTravelerMini
             vendor: Kingston
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: PMAP
             size: 984MiB (1031MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 984MiB (1031MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=568e4326
              *-volume
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /media/KINGSTON
                   version: FAT32
                   serial: bc6e-a61c
                   size: 983MiB
                   capacity: 983MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8 state=mounted
```

---

### Post by lukeiamyourfather on 2010-01-17
This would make a good direct charging source (no inverter necessary). Its 18-22 volts output which is perfect for your 19 volt Acer notebook. Its half the current of the AC adapter so it would take approximately twice as long to charge compared but that's not bad for solar.

[http://www.ctsolar.com/322wbluenylonfoldingsolarpanelourmostpopularpanel.aspx](http://www.ctsolar.com/322wbluenylonfoldingsolarpanelourmostpopularpanel.aspx)

I've not changed the CPU clock in the terminal before. Normally I just use the panel utility (right click panel and select add to panel, then add the CPU frequency scaling monitor). A quick search revealed cpufreqd to automatically change the CPU clock based on user configurations. There might be other ways too. Cheers!

---

### Post by warfacegod on 2010-01-19
See post #6:

[http://ubuntuforums.org/showthread.php?t=1385331]("http://ubuntuforums.org/showthread.php?t=1385331")

---

### Post by onamattuphere on 2010-01-20
Thanks for the support so far.

I figured out how to change the cpu scaling in the terminal```
sudo echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```. (since I have two cores I also did this for the same file, but in the cpu1-folder). But I couldn't change the content of this file (both cpu0 and cpu1 folders), even though I used chmod as well as with the -s attribute; ie: chmod (path/filename) OR chmod -s (path/filename).

So I followed [this guide]("http://www.arsgeek.com/2008/01/16/cpu-scaling-ubuntu-battery-life-and-you-how-to-scale-your-cpu/").

and typed in:
```
sudo dpkg-reconfigure gnome-applets
```This finally let me get the Gnome option of scaling the cpus through the applets (one for each core), BUT when I tried to change settings or scaling the processors didn't respond.
Then I ran gconf-editor and chose powersave as the governor for battery mode.

I tried cpufreqd and powernowd, none of them did anything for me - I am currently using cpufreqd since I think that was the default one.


Then suddenly I realized I had opened pandoras box!
After a reboot I got the error message:
> 
CPU frequency scaling unsupported
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.
Before I tried all this stuff my cores were constantly running on the ondemand setting - AC or battery. Now I have an annoying error message and my cpu is on full blast all the time.
Been searching for the error message but all I've come up with so far is that people are saying that it's caused since my processor does not support scaling. I now it does since it was doing it before I started all this.
I just wanted to tweak Ubuntu to my liking and now it is acting up on me. I now that somewhere down the road I'll end up more knowledgeable, but the timing for this is not exactly perfect.

I tried cpufrequtils: but this appeared when I installed it:
```
 * CPUFreq Utilities: Setting ondemand CPUFreq governor...                       * disabled, governor not available...                                   [ OK ] 

```I cannot run or find the program.


Please help!

Edit: I reset the dpkg-reconfigure gnome-applets - turn it off, then enabled it again. Then I didn't touch the governor settings in the gconf-editor. This made the error message go away, but manual scaling is still not working. ```
sudo echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied

```Actually the automatic scaling is working, however not as aggressive as it was before I started my fiddling and certainly not as aggressive as I would ultimately like to have it.
On AC they're both on full power (with ondemand as governor). Before I started messing with things they were on constant low until it would scale up as soon as there was any work for the CPU. On Battery it would still be on ondemand governor, yet it wouldn't scale up the CPU as frequently. However it would happen during battery state - which is why I wanted to tweak the settings in the first place.

Hoping for some help to solve this; where's the location for the scripts that ubuntu uses for CPU scaling?

---

### Post by warfacegod on 2010-01-20
Have you tried changing this:

> /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

by hand with:

```
gksudo nautilus
```

You'd be browsing your files as root and I would imagine that you could modify and save any file you choose.

---

### Post by onamattuphere on 2010-01-20
When I launched nautilus as instructed i got:
```
** (nautilus:19634): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

```
I am not using nautilus by default, so maybe this is what the error is about?

Then the file turned up empty when I opened up in gedit, although when I did cat on the file it gave me *ondemand*.

I entered *powersave* in gedit and saved it. I got a message saying that a backup could not be created. I chose to 'save anyway', which gave me error message: "Could not save the file /sys/devices/system/cpu/&#8230;/cpufreq/scaling_governor." and at the same time in the terminal:
```
** (gedit:19699): WARNING **: Hit unhandled case 4 (Invalid parameters) in gedit_unrecoverable_saving_error_message_area_new.

```.
The funny thing is that it will actually change something; Even though it does not scale down the processors, the governor is changed when I check the CPU Frequency Scaling Monitor on my panel. So this is just as when I try to change the governor (or the scaling for that matter) by mouse clicking the panel applet. I make the changes and even though the settings are changed, the cpus are still working at the same percentage. Strange and very annoying.

I also flashed my BIOS to the latest version without any noticeable changes at all.

Well, at least I can tick this off in the long list of things I've tried. I know scaling works, so I guess I'm bound to find a solution at some point as long as I keep trying.

##EDIT##
Finally, I've had some progress: [http://forum.notebookreview.com/showthread.php?t=287721](http://forum.notebookreview.com/showthread.php?t=287721)
I went to the synaptic package manager and found that powernowd had an ubuntu icon infront of it. So I marked it for installation and then scaling works perfect in Gnome! Now I have full control through the CPU frequency scaling monitor-applet for my panel.
I'll see if I can change the scaling without Gnome running.

So getting closer and more optimistic. Can't wait to mark this thread as solved.

---

### Post by onamattuphere on 2010-01-23
OK - progress:

I have finally managed to change the cpu governor in the terminal. It is done with the inbuilt laptop-mode command.

To configure it and change the governor, type:
```
sudo nano /etc/laptop-mode/laptop-mode.conf
```
(I would recommend backing the file up before making any changes.)

Then to activate laptop-mode:
```
sudo /etc/init.d/laptop-mode start
```
It can be stopped or restarted, by exhanging *start* with *stop* or *restart*.

Can anyone please tell me how I can have laptop-mode activated during boot up?

---

### Post by warfacegod on 2010-01-23
You may not want to. Boot up is fairly processor intensive. If you enable laptop mode for boot up it may take so much longer that you would actually use *more* battery. You should look at some statistics first and base your decision on that and then run some tests on your laptop to see if your numbers are consistent with what you researched.

---

### Post by onamattuphere on 2010-01-27
How do I check which deamons/services/scripts are running from the terminal, and how do I enable/disable them for the boot-up sequence?

---

### Post by warfacegod on 2010-01-27
I would imagine Startup Applications.

Just a thought; have you checked Synaptic to see if you have "ubuntu-laptop-mode" installed?

---

### Post by onamattuphere on 2010-01-27
Thanks. I checked the package manager and it was not installed. However if I would install it, it would remove the following:
acpi-support
laptop-mode-tools
powermanagement-interface
ubuntu-desktop

I tried to do the apropos command for that "Startup Applications" you mentioned. Are you sure it's a command to be executed in the terminal?

I got this:
```
STARTUPMANAGER (1) [startupmanager] - change boot settings
genisoimagerc (5)    - startup configuration file for genisoimage
kdostartupconfig (1) - KDE configuration options loader
kstartupconfig (1)   - KDE configuration options loader
startupmanager (1)   - change boot settings

```

---

### Post by warfacegod on 2010-01-27
Easier to use it from your menu:

System> Preferences> Startup Applications

---

### Post by nothingspecial on 2010-01-27
> **onamattuphere said:**
> How do I check which deamons/services/scripts are running from the terminal, and how do I enable/disable them for the boot-up sequence?
```

sudo apt-get install sysv-rc-conf
```

```
man sysv-rc-conf
```

```
sudo sysv-rc-conf
```

---

### Post by onamattuphere on 2010-01-31
> **warfacegod said:**
> Easier to use it from your menu:

System> Preferences> Startup Applications

I don't have that in my menu. Neither in Preferences nor in Administration.

Thanks for the heads up on sysv-rc-conf. I googled it and found [this nice thread]("http://ubuntuforums.org/showthread.php?t=89491"). However, I would like to know which services/scripts/deamons are currently running. Since I am not sure that everything is running according to what the sysv-rc-conf is telling me.
Is there such a method within the terminal?

---

### Post by warfacegod on 2010-01-31
```
top
```

or

```
htop

sudo apt-get install htop
```

---

### Post by onamattuphere on 2010-02-01
Thanks! I love the htop program: you get the PID for processes owned by the root as well - just what I wanted.

I also stumbled over this:
```
less /proc/modules
```

However, none of these options will tell me what scripts are activated. Like for instance laptop-mode.. Or am I wrong?
I do suspect that laptop-mode is loaded at boot, but not completely sure. Would be nice to clear my doubts in order to troubleshoot in a proper manner.

Anybody know how to check which scripts are running?

---

### Post by warfacegod on 2010-02-01
Can't help you there.

---

### Post by onamattuphere on 2010-02-04
I have a new issue and it seems quite important. I've just received my new battery and it's nice to have to extra juice. At the moment I'm getting 2h 50m, using about 16-17W according to powertop.

I read [this]("http://www.lesswatts.org/tips/cpu.php") and tried this code:
```
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
```

..which of course does not work, since I cannot change these files - even as root user. As far as I can see, *laptop-mode *does not have any setting for it either.

The page says this will shave of several watts, so it would be great to get it working.

---

### Post by warfacegod on 2010-02-04
Try "sudo su".

---

### Post by onamattuphere on 2010-02-04
```
sudo su echo 1 > /sys/devices/system/cpu/sched_mc_power_savings 
bash: /sys/devices/system/cpu/sched_mc_power_savings: Permission denied
```
Does this command require a password? It didn't prompt me to type it in.

---

### Post by warfacegod on 2010-02-04
It most certainly should have.

Try this:

```
sudo su
```

Then:

```
yourcode
```

If sudo of any kind isn't asking for a password then you may have another, separate issue entirely.

---

### Post by onamattuphere on 2010-02-07
That worked! I learned a new command as well - great! But how do you get back out of root mode?

I stumbled over something interesting while doing *apropos suspend*;
```
man pm-powersave
```
Basically this is the main controller for power saving scripts on my system, and all the scripts for power saving are placed under the two locations:

/etc/pm/power.d
/usr/lib/pm-utils/power.d

Great - Light at the end of the tunnel.


I am currently working on the following:

When I boot up and run x (with the command; *startx*) and then when I loose power I do ```
killall Xorg
``` as well as killing dhcdbd and NetworkManager. I get the results I've been trying to acheive: 12-13W and 5-7 wakeups pr sec.
Problem is that when I boot up without AC, I have to run X and quit it again in order to achieve these values. If I don't run X and quit, I only get ca 17W and 15 wakups pr sec.

Anybody know what might be causing this?

---

### Post by warfacegod on 2010-02-07
> But how do you get back out of root mode?

It should just time out after a brief interval. I can't quite remember, but I think closing the Terminal will do it too.

---

### Post by onamattuphere on 2010-02-08
> **warfacegod said:**
> It should just time out after a brief interval. I can't quite remember, but I think closing the Terminal will do it too.

That's what I've been doing. Would be nice to know the command though .. that way I feel more .. well.. in command.


Anyways, great news:

When I boot up straight into the terminal on battery I do:
```
pm-powersave true
``` together with ```
sudo killall dhcdbd NetworkManager
``` - which basically solves my case.

---

### Post by warfacegod on 2010-02-08
> But how do you get back out of root mode?

Try: Ctrl+Alt+F7

---

### Post by onamattuphere on 2010-02-09
```
sudo su *"enter your username"*
```

---

