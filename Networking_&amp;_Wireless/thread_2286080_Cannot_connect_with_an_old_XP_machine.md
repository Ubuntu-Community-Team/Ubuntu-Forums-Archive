---
title: "Cannot connect with an old XP machine"
date: 2015-07-09
forum: Networking &amp; Wireless
---

### Post by chris398 on 2015-07-09
Hello,
I'm new to this community and to Linux.
I have successfully installed Lubuntu to an old XP machine, but I am unable to get the machine to connect to the internet. I tried installing other distros, and had the same outcome.

When I try to run inxi -N it says no network card detected.


Here's the machine specs:
Compaq Presario SR1151NX
Intel Pentium 4
512mb of DDR1 RAM
I took the case off and found this on the ethernet port:
P35-157-11Z9
When I Google that number, it only comes up with ancient drivers for older window builds.
How can I get a driver for this network adapter to work on Lubuntu? And once I get the driver, is it as simple as insert a USB and click?
Thank you in advance for any help.

---

### Post by CharlesA on 2015-07-09
Run this from a terminal please:

```
sudo lshw -class network
```

```
sudo lspci | egrep -i --color 'network|ethernet'
```

And post the results in code tags.

---

### Post by Bucky Ball on 2015-07-09
> **CharlesA said:**
> And post the results in code tags.

... and see the last link in my signature if you don't know how to do that. Also, please use default fonts and point sizes when posting, thanks. Good luck. :)

---

### Post by chris398 on 2015-07-09
Got it. I'll put up the results in a bit. I'm at work right now.

Can you tell me how to put the line that is straight up and down in the command terminal, i tried to do that earlier today, and couldn't figure it out.

---

### Post by CharlesA on 2015-07-09
> **chris398 said:**
> Can you tell me how to put the line that is straight up and down in the command terminal, i tried to do that earlier today, and couldn't figure it out.

It is a pipe. It should be right above the enter key on the keyboard and looks like this:
[http://kb.mailchimp.com/merge-tags/using/where-to-find-the-pipe-key](http://kb.mailchimp.com/merge-tags/using/where-to-find-the-pipe-key)

---

### Post by chris398 on 2015-07-10
Thanks for the pipe key info, i can say I've truly never used it before today.

I entered the code above and then the terminal asked me for a password. I enter the password, and it cycled through bunch of items that looked like parts of the PC (usb,cpu..etc) after that the regular command line comes up. I then tried to enter the 2nd code you gave me, but nothing happens. It just comes up blank.

---

### Post by CharlesA on 2015-07-10
> **chris398 said:**
> Thanks for the pipe key info, i can say I've truly never used it before today.

I entered the code above and then the terminal asked me for a password. I enter the password, and it cycled through bunch of items that looked like parts of the PC (usb,cpu..etc) after that the regular command line comes up. I then tried to enter the 2nd code you gave me, but nothing happens. It just comes up blank.

Huh. You can try redirecting the output to a file and then copying to a thumb drive so you can post it:

```
sudo lshw -class network > ~/Documents/lshw.txt
```

It should have looked something like this, though:

```
charles@Mars:~$ **sudo lshw -class network**
  *-network
       description: Ethernet controller
       product: Virtio network device
       vendor: Red Hat, Inc
       physical id: 12
       bus info: pci@0000:00:12.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: msix bus_master cap_list rom
       configuration: driver=virtio-pci latency=0
       resources: irq:10 ioport:c080(size=32) memory:febf2000-febf2fff memory:febe0000-febeffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: ba:58:73:65:ff:a3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=virtio_net ip=192.168.1.200 link=yes multicast=yes

```

```
charles@Mars:~$ **sudo lspci | egrep -i --color 'network|ethernet'**
00:12.0 Ethernet controller: Red Hat, Inc Virtio network device

```

The output you get should be similar to those, but it won't say Virtio, as I ran them a virtual machine.

---

### Post by chris398 on 2015-07-10
Ok, So i was able to run that code in terminal. It did the same thing, cycled through components and brought up a refreshed command line. I then went to documents to find the .txt file. It was blank.

I'm trying to make a video of what's happening to give you a visual.

So here's a visual.


[gfycat.com/MeatyOrnateLangur]("http://gfycat.com/MeatyOrnateLangur")

---

### Post by CharlesA on 2015-07-10
Interesting. It doesn't show any network card there.

Can you run this without specifiying anything then post the text document.

```
sudo lshw > ~/Documents/lshw.txt
```

---

### Post by chris398 on 2015-07-10
GOT SOMETHING!!!  A wall of text that i know a couple of words of

```
compaq    description: Computer
    product: Piranha
    vendor: INTEL
    width: 32 bits
    capabilities: smbios-2.4 smp-1.4 smp
    configuration: cpus=1
  *-core
       description: Motherboard
       physical id: 0
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          size: 2800MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System memory
          physical id: 1
          size: 2006MiB
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cff80000-cfffffff ioport:c800(size=8) memory:d0000000-dfffffff memory:cff40000-cff7ffff
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
             configuration: driver=snd_hda_intel latency=0
             resources: irq:25 memory:cff38000-cff3bfff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:80000000-801fffff ioport:0(size=2097152)
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:b400(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-15-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-15-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: USB hub
                   product: Dell Multimedia Pro Keyboard Hub
                   vendor: Dell
                   physical id: 1
                   bus info: usb@3:1
                   version: 59.00
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=3 speed=12Mbit/s
                 *-usb
                      description: Keyboard
                      product: Dell Multimedia Pro Keyboard
                      vendor: Dell
                      physical id: 1
                      bus info: usb@3:1.1
                      version: 59.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=90mA speed=2Mbit/s
              *-usb:1
                   description: Mouse
                   product: Gaming Mouse G502
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@3:2
                   version: 88.02
                   serial: 0C87335C3731
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=300mA speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c000(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-15-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c400(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-15-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Mass storage device
                   product: USB Reader
                   physical id: 1
                   bus info: usb@5:1
                   logical name: scsi5
                   version: 1.00
                   serial: 9205291
                   capabilities: usb-1.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12Mbit/s
                 *-disk:0
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@5:0.0.0
                      logical name: /dev/sdc
                      configuration: logicalsectorsize=512 sectorsize=512
                 *-disk:1
                      description: SCSI Disk
                      physical id: 0.0.1
                      bus info: scsi@5:0.0.1
                      logical name: /dev/sdd
                      configuration: logicalsectorsize=512 sectorsize=512
                 *-disk:2
                      description: SCSI Disk
                      physical id: 0.0.2
                      bus info: scsi@5:0.0.2
                      logical name: /dev/sde
                      configuration: logicalsectorsize=512 sectorsize=512
                 *-disk:3
                      description: SCSI Disk
                      physical id: 0.0.3
                      bus info: scsi@5:0.0.3
                      logical name: /dev/sdf
                      configuration: logicalsectorsize=512 sectorsize=512
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:cff37c00-cff37fff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-15-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   description: Mass storage device
                   product: Cruzer Facet
                   vendor: SanDisk
                   physical id: 1
                   bus info: usb@1:1
                   logical name: scsi6
                   version: 1.26
                   serial: 4C532000050427108101
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sdb
                      size: 7633MiB (8004MB)
                      capabilities: partitioned partitioned:dos
                      configuration: logicalsectorsize=512 sectorsize=512
                    *-volume
                         description: Windows FAT volume
                         physical id: 1
                         bus info: scsi@6:0.0.0,1
                         logical name: /dev/sdb1
                         logical name: /media/pjsingh/MELS PINKY
                         version: FAT32
                         serial: 0e37-e108
                         size: 7633MiB
                         capacity: 7633MiB
                         capabilities: primary fat initialized
                         configuration: FATs=2 filesystem=fat label=MELS PINKY mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096)
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:b000(size=8) ioport:a800(size=4) ioport:a400(size=8) ioport:a000(size=4) ioport:9800(size=16)
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
             resources: ioport:400(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom:0
             description: DVD reader
             product: DVD+RW SOHW-802S
             vendor: LITE-ON
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: UPP6
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: SCSI CD-ROM
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr1
             capabilities: audio
             configuration: status=nodisc
     *-scsi:1
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG SP1614C
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 0-30
             serial: S01XJ10X663737
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=000b1535
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/pjsingh/ad97b4d8-7251-4d63-99ec-ad8ad1eadccb
                version: 1.0
                serial: ad97b4d8-7251-4d63-99ec-ad8ad1eadccb
                size: 75GiB
                capacity: 75GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-07-24 23:39:06 filesystem=ext4 lastmountpoint=/ modified=2015-07-25 23:03:09 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2015-07-25 23:03:09 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 73GiB
                capacity: 73GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1270MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 72GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted



```

Ok,

Also here is the attachment as you requested.

---

### Post by mörgæs on 2015-07-10
Is networking enabled in Bios?

---

### Post by chris398 on 2015-07-10
That sounds like good reasoning. I'm going to buzz home on my  lunchbreak and give it a try.

I've never enabled/disabled a network interface in the BIOS, so wish me luck.  UEFI has me spoiled these days.

---

### Post by CharlesA on 2015-07-10
It sounds kinda weird, but it is worth a shot to make sure it is enabled in the BIOS. Good luck.

---

### Post by chris398 on 2015-07-10
Well guess what...I can't access the BIOS on this box. It's password protected.  I almost chucked it out the window. The owner of this computer doesn't remember the password that he put on it 8 years ago. It actually was my whole reasoning for putting Linux on the computer. He couldn't remember the password he put into Windows XP, and he hasn't accessed it in like 3 years due to not knowing the password. I suggested to install Linux, since XP is done, and the computer is still decent. I owe this guy money, so this was supposed to be my payment.

 Anybody know how to bypass a password protected BIOS?  Any other ideas besides the BIOS?

---

### Post by Bucky Ball on 2015-07-10
Desktop? Locate and take out the CMOS battery for about two minutes. You'll find it in there somewhere. It is a small round one. 

Pop it back in and that should have cleared the BIOS (and any manual settings you have tweaked in there, so be warned). If not, take it out for five minutes.

No idea with a laptop.

---

### Post by chris398 on 2015-07-10
Yes it is a desktop. I've seen the CMOS battery in there. I wasn't sure if pulling it would wipe the Password. I'll give it a try in a bit. Thank you.

---

### Post by chris398 on 2015-07-11
Well, I was able to reset the BIOS password by pulling the battery. LAN was enabled. I am still unable to see the network card when running [ Sudo lshw -class network] in terminal.

I went back into the BIOS and tried to disable and then re-enable, still no success.  I spoke to the person who owns the computer, he said it always connected to the internet w/out issues. 

Any other strains of spaghetti we can throw at the wall here? I'm open for anything.

---

### Post by CharlesA on 2015-07-11
If you boot into Windows, does the network card entry show the type of network card? I'm out of ideas since it seems the card that machine has needs a driver but it isn't seen by the OS for some reason.

---

### Post by Bucky Ball on 2015-07-11
This might be have been done and sounds obvious, but ...

Have you plugged in an ethernet cable, if that is possible, booted into Ubuntu and in a terminal:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

... or updated via the Software Centre? Might pick something up. You could then perhaps look in Additional Drivers. 

This all might make no difference as the install doesn't even see the thing to start, identified or not. 

Apologies if this was tried but the thread's getting pretty lengthy. :)

---

### Post by chris398 on 2015-07-11
I'm at work right now, So I'll try these 2 things when I get home.

First I'll try Buckyball's comment. I'll try running the update command in terminal. I don't believe I have tried that yet.

Second move will be what Charles A said, I'll re-install windows, and see if windows recognizes the network card. I don't have a WinXP install disc handy, but I do have a Win7 disc.Typically when I do a fresh install of windows, I have to get the drivers for the network card. We'll see where I stand after that.

Thanks again for the awesome help. I'm starting to believe the network card is toast. I think I have an old discreet Belkin network card somewhere in my dungeon, I may dig for that thing and try it for a last ditch.

---

### Post by Bucky Ball on 2015-07-11
Yea, chuck it in. It may just work 'out of the box' and you would be able to get to the bottom of it with more ease if you could get online.

---

