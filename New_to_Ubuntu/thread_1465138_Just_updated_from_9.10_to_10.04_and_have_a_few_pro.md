---
title: "Just updated from 9.10 to 10.04 and have a few problems"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by chrisxuk on 2010-04-29
Hi there,

updated to 10.04 this morning and have stumbled across a few problems. The first being that i've lost what seems, wireless internet capabilities. When I was on 9.10 my wireless adapter worked straight away. Any ideas how I can fix this?

Secondly I currently dual boot Ubuntu with Windows XP. After updating to 10.04 I can't boot into XP :(

I click on XP on the GRUB menu, and a black screen just pops up with a blinking hyphon in the top left hand corner. Left it like this for a few minutes and nothing else happened! Any way of fixing this?

Thanks.

---

### Post by D3jan on 2010-04-29
you need some live programs for reparing boot  , something like "Acronis director" or "EasyBCD" on live CD , if you brick linux you can , recoveru XP and then backup your data and install clean 10.04

---

### Post by chrisxuk on 2010-04-29
Right, i've connected via ethernet but this can only be a temporary connection. Anything I can do to get my wireless adapter to work? Booting into XP isn't as important.

---

### Post by Calash on 2010-04-29
We will need to know what type of hardware you have.  If you can post the output of the following it will help.


```

lspci

```

Post the output using the code tag and it will be easier for us to read.  The code tag is the "#" looking button at the top of the "Reply to Thread" area.

---

### Post by chrisxuk on 2010-04-29
Okay, i'll have that up for you later. Got to go to 6th form for a couple of hours.

---

### Post by davrosuk on 2010-04-29
XP not showing up is almost certainly linked to this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765")

Once you update (once you get your network working!) it'll be fine since that package has now been fixed.

---

### Post by chrisxuk on 2010-04-29
Just thought i'd add that to update to 10.04 I typed "update-manager -d" into Alt+F2 and installed it that way. Could this of lead to my problems at all?

---

### Post by klemes on 2010-04-29
> **chrisxuk said:**
> Just thought i'd add that to update to 10.04 I typed "update-manager -d" into Alt+F2 and installed it that way. Could this of lead to my problems at all?

No that is alright that is the standard procedure.
About your wireless did you check into Hardware Drivers from the System menu to check if there is a proprietary driver for your wireless ready to be activated?

---

### Post by bruno9779 on 2010-04-29
OP: have you tried:

```
sudo update-grub
```

to detect XP?

and, have you checked "hardware drivers" for an entry about your WiFi card?

EDIT: as someone said before it would help to know which wifi card is it.

can you post the output of :

```
lspci | grep -i net
```

---

### Post by Rushyang on 2010-04-29
Hey guys, I've heard too many these kind of issues with 10.04... & If it's really unstable then <...> I don't have enthusiasm to install it anymore.

---

### Post by Calash on 2010-04-29
>> **Rushyang said:**
> Hey guys, I've heard too many these kind of issues with 10.04... & If it's really unstable then <...> I don't have enthusiasm to install it anymore.

I would not call it unstable.  I have three systems that have been running it, one since beta1 and two since RC.

These are the natural problems when deploying to a varied and random environment.  There are so many different types of hardware that can be combined into a near infinite number of combination along with lack of maintaining the hardware.  This creates differences in the results.

I will not even get into issues surrounding human interaction.


So far I have not seen many more issues than any other release, outside of the min/max/close button positioning issues that we all know and love/hate :)

---

### Post by coolbrook on 2010-04-29
> **Rushyang said:**
> Hey guys, I've heard too many these kind of issues with 10.04.

I decided to wait til the final release is available (for upgrading.)  The RC errata stated that there could be problems with grub and the partitions for dual booting.

---

### Post by chrisxuk on 2010-04-29
Thanks for all the replies. I'm currently connected via Ethernet, but this cannot be a permanent connection unfortunately.

The output to lspci is:
```

chris@chris-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
02:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
02:00.1 Audio device: ATI Technologies Inc HD48x0 audio
chris@chris-desktop:~$ 

```

And the output to lspci | grep -i net is:
```

chris@chris-desktop:~$ lspci | grep -i net
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
chris@chris-desktop:~$ 

```

I've checked in hardware drivers and it only has something for my graphics card. When I just have my wireless adapter plugged in, and no Ethernet cable I get the wireless bars but in a light grey and with a line through them. Right clicking just brings up options for wired connections and to set up a VPN.

---

### Post by bkratz on 2010-04-29
If it "plugs-in" it is probably a usb device-post the output of 

lsusb

(that is LSUSB in lowercase)

---

### Post by chrisxuk on 2010-04-29
Output from lsusb

```

chris@chris-desktop:~$ lsusb
Bus 002 Device 004: ID 046d:c225 Logitech, Inc. 
Bus 002 Device 003: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 002 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 1435:0427 Wistron NeWeb 
Bus 001 Device 006: ID 050d:0255 Belkin Components 
Bus 001 Device 005: ID 04f2:a217 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chris@chris-desktop:~$ 

```

---

### Post by bkratz on 2010-04-29
This one is the wireless--but so far I haven't found anything later than 2006 on it, will still look

Bus 001 Device 008: ID 1435:0427 Wistron NeWeb

---

### Post by chrisxuk on 2010-04-29
I only installed 9.10 about a week and a half ago. My wireless adapter worked straight away, first time I ran Ubuntu. No need to install drivers or anything. This is so annoying! :(

---

### Post by dannyboy79 on 2010-04-29
post the output of 
sudo lshw -C network

---

### Post by bkratz on 2010-04-29
did find this one but not much help--still looking

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1115919](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1115919)

---

### Post by frup on 2010-04-29
I would try doing 

sudo apt-get update
sudo apt-get dist-upgrade

In the past when an upgrade hasn't worked for me it is because a package here or there has had a problem... doing this ensures that you definitely have everything as it is supposed to be. Might not solve the problem, but at least you can rule it out.

Also make sure that these commands output something similar

**$ cat /etc/issue**
Ubuntu 10.04 LTS \n \l

**~$ cat /etc/lsb-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

**$ uname -a**
Linux ursus 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

press escape on your grub menu to choose different kernel versions if available and see if the different versions allow your hardware to work. This works sometimes.

---

### Post by Sef on 2010-04-29
> And the output to lspci | grep -i net is:
 	Code:
 	chris@chris-desktop:~$ lspci | grep -i net
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
chris@chris-desktop:~$


Had you installed NVidia's proprietary drivers before you upgraded?

---

### Post by chrisxuk on 2010-04-29
Thanks for the replies.

> **dannyboy79 said:**
> post the output of 
sudo lshw -C network

There was no output really :confused:

```

chris@chris-desktop:~$ sudo lshw -C network
chris@chris-desktop:~$    

```


> **frup said:**
> I would try doing 

sudo apt-get update
sudo apt-get dist-upgrade

In the past when an upgrade hasn't worked for me it is because a package here or there has had a problem... doing this ensures that you definitely have everything as it is supposed to be. Might not solve the problem, but at least you can rule it out.

Also make sure that these commands output something similar

**$ cat /etc/issue**
Ubuntu 10.04 LTS \n \l

**~$ cat /etc/lsb-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

**$ uname -a**
Linux ursus 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

press escape on your grub menu to choose different kernel versions if available and see if the different versions allow your hardware to work. This works sometimes.

I have tried all of these commands in the terminal, and they have all come back the same as yours!

Is there a way to do something like a system restore in Windows, but on Ubuntu? Or would I be better off just downloading and burning a new .iso of 10.04? Would this fix my problems?

---

### Post by chrisxuk on 2010-04-29
> **Sef said:**
> Had you installed NVidia's proprietary drivers before you upgraded?

NVidia? My graphics card is ATI :confused: How strange, or is this normal? Sorry, i'm very new to Ubuntu!

---

### Post by dannyboy79 on 2010-04-29
you probably have a motherboard with nvidia chipsets for various controllers. did you read my message about posting output of
sudo lshw -C network

---

### Post by chrisxuk on 2010-04-29
sudo lshw - C network output 

```

chris@chris-desktop:~$ sudo lshw -C network
chris@chris-desktop:~$  

```

---

### Post by dannyboy79 on 2010-04-29
ok, this is very weird. are you sure your wifi card is even plugged in? if you're not getting anything back from 

sudo lshw -C network

that means you don't have any network hardware device installed in your machine! or your ubuntu is really bugered!!!

type in 
man lshw

and read what the command lshw can provide you.

---

### Post by chrisxuk on 2010-04-29
Right. I put man lshw into the terminal and it told me that I needed to run it as the super user. So I entered sudo lshw into the terminal and it has provided me with a wealth of information. There is a lot :p

```

chris@chris-desktop:~$ sudo lshw
[sudo] password for chris: 
chris-desktop             
    description: Desktop Computer
    product: M61PME-S2P
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=30303234-3144-3636-3635-4337FFFFFFFF
  *-core
       description: Motherboard
       product: M61PME-S2P
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2 (12/30/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 7850 Dual-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.2.3
          slot: Socket M2
          size: 1400MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: 4
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             physical id: 1
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 9
          bus info: cpu@1
          version: 15.2.3
          size: 1400MHz
          capacity: 1400MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:e000(size=64) ioport:1c00(size=64) ioport:c400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fa007000-fa007fff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fa006000-fa0060ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
          resources: ioport:a000(size=4096)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:fa000000-fa003fff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:24:1d:66:65:c7
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.156 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:25 memory:fa004000-fa004fff ioport:c800(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fa005000-fa005fff
        *-cdrom
             description: DVD writer
             product: DVD-RW  DVR-217F
             vendor: PIONEER
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.07
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: ST3500418AS
             vendor: Seagate
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: CC34
             serial: 9VM15FMZ
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=b2a2b2a2
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: a6799406-34cd-1147-84b1-7d6d96dd0730
                size: 339GiB
                capacity: 339GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-04-17 11:31:21 filesystem=ntfs state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 125GiB
                capacity: 125GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 125GiB
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 101
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:b000(size=4096) memory:f8000000-f9ffffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: RV770 [Radeon HD 4850]
             vendor: ATI Technologies Inc
             physical id: 0
             bus info: pci@0000:02:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:26 memory:e0000000-efffffff(prefetchable) memory:f9000000-f900ffff ioport:b000(size=256) memory:f8000000-f801ffff(prefetchable)
        *-multimedia
             description: Audio device
             product: HD48x0 audio
             vendor: ATI Technologies Inc
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:f9010000-f9013fff
     *-pci:2
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: b
          bus info: usb@1:8
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 30MiB (32MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/DV
                version: FAT12
                serial: 0000-0000
                size: 15EiB
                capabilities: primary bootable fat initialized
                configuration: FATs=1 filesystem=fat label=DV mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
chris@chris-desktop:~$ 

```

Hope this is of some use!

---

### Post by dannyboy79 on 2010-04-29
ok, this is getting kind of tiring. you need to tell us what kind of wifi card you have, is it a pci card, is it a usb one, is it built into the motherboard? i doubt it's a pci or built in based on teh output of lshw. so please post the output of 

sudo lsusb -v

---

### Post by dannyboy79 on 2010-04-29
think i finally figured out what wifi card you have based on this thread

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1115919&page=2](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1115919&page=2)

don't know what to tell you if it worked in karmic and it doesn't now in lucid. can you boot up a livecd of karmic to see what module the wifi was using?

---

### Post by chrisxuk on 2010-04-29
> **dannyboy79 said:**
> ok, this is getting kind of tiring. you need to tell us what kind of wifi card you have, is it a pci card, is it a usb one, is it built into the motherboard? i doubt it's a pci or built in based on teh output of lshw. so please post the output of 

sudo lsusb -v

Woops, sorry. One of the most important bits, and I forget. My apologies.

I have an Inventel UR540G adapter. It's plugged into a USB port, with a cable. It was supplied by my ISP, Orange.

I've swapped to my laptop now, so i'll update with the output to "sudo lsusb -v" tomorrow morning.

I'll try a live CD tomorrow as well, to find out more information for you! :)

Once again, my apologies.

---

### Post by mynameisnick on 2010-04-29
Just wanted to give a thanks. I had the same grub problem and now I don't. :)

---

### Post by jou770d on 2010-05-29
I came across this thread while trying to find a solution for a similar card so I thought I'ld post what I found here.
This did it for me:
```
sudo aptitude install linux-firmware-nonfree
```
Source:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383)

---

