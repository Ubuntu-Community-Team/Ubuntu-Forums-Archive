---
title: "Can't Connect To The Internet"
date: 2016-09-11
forum: Networking &amp; Wireless
---

### Post by uzzo23 on 2016-09-11
Hi folks, I'm having an issue with my Linunx box. I not to long ago bought a Dell refurb a whole lot cheaper than I could put a new MOBO and CPU in my original Linux box. It's been working great up until last week. It won't connect to the internet for some reason. Since I can't post anything from that machine. I opened a terminal and ran lspci. I then copied and pasted it on a notepad and then scanned it to a file. I uploaded it as an attachment here from my windows machine. I was hoping someone could point me in the right direction on it.


[ATTACH=CONFIG]271076[/ATTACH]

---

### Post by howefield on 2016-09-11
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by ajgreeny on 2016-09-11
Can we assume that you are trying to use a cable ethernet connection here?

There is no wifi adapter showing in your image so I presume you are cable connected, and it is unusual for that to not work out of the box.

More info please.

---

### Post by mörgæs on 2016-09-11
Yes, more info is welcome.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and copy lshw.txt to the Windows computer. From here post the file in CODE tags (better than screenshots).

---

### Post by uzzo23 on 2016-09-11
> **mörgæs said:**
> Yes, more info is welcome.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and copy lshw.txt to the Windows computer. From here post the file in CODE tags (better than screenshots).
Yes, it is a hardwired connection. I tried running that code. When I hit enter I get a brief PCI (sysfs), and it then returns to phillip@phillip- desktop

---

### Post by howefield on 2016-09-12
> **uzzo23 said:**
> Yes, it is a hardwired connection. I tried running that code. When I hit enter I get a brief PCI (sysfs), and it then returns to phillip@phillip- desktop

Running that terminal command will put a text file in to the folder that you ran it from.. by default into your /home folder. Perhaps you can get it from there to your Windows machine ?

---

### Post by uzzo23 on 2016-09-12
> **howefield said:**
> Running that terminal command will put a text file in to the folder that you ran it from.. by default into your /home folder. Perhaps you can get it from there to your Windows machine ?

Ah, sorry about that. You would think that 8 or so years of using Linux I wouldn't be so Linux retarded:D

```
computer
    description: Mini Tower Computer
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=2 power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0T656F
       vendor: Winbond Electronics
       physical id: 0
       version: A02
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A02
          date: 07/02/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.7.10
          serial: [REMOVED]
          slot: CPU
          size: 2933MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 3MiB
             capacity: 3MiB
             capabilities: internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: HYMP125U64CP8-S6
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: HYMP125U64CP8-S6
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: [REMOVED]
          size: 2950MHz
          capabilities: vmx ht
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
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0a
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:dfc00000-dfcfffff
        *-display:0
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:dfe00000-dfe7ffff ioport:ecd8(size=8) memory:c0000000-cfffffff memory:dff00000-dfffffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:dfe80000-dfefffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:dfdfc000-dfdfffff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:dfb00000-dfbfffff ioport:d0000000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetLink BCM5784M Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 10
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb v2.19 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:44 memory:dfbf0000-dfbfffff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff20(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:ff980800-ff980bff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
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
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fec0(size=16)
           *-disk
                description: ATA Disk
                product: ST3500630AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: [REMOVED]
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00036e01
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: [REMOVED]
                   size: 5721MiB
                   capacity: 5721MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2014-02-25 16:17:45 filesystem=ext4 lastmountpoint=/ modified=2016-04-05 10:39:00 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2016-09-11 15:49:12 state=mounted
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: [REMOVED]
                   size: 432GiB
                   capacity: 432GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-11-07 06:33:20 filesystem=ext4 lastmountpoint=/media/7f810a10-87ae-4f36-83cd-16c680b3c83e modified=2016-05-10 21:24:29 mounted=2016-05-10 19:31:13 state=clean
           *-cdrom:0
                description: DVD-RAM writer
                product: DVDRW LH-20A1S
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/cdrom3
                logical name: /dev/cdrw3
                logical name: /dev/dvd3
                logical name: /dev/dvdrw3
                logical name: /dev/sr0
                version: 9L08
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD-RAM writer
                product: DVD+-RW GH50N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom2
                logical name: /dev/cdrw2
                logical name: /dev/dvd2
                logical name: /dev/dvdrw2
                logical name: /dev/sr1
                version: B101
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:ece0(size=32)
     *-scsi
          physical id: 2
          bus info: usb@1:5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Storage
             vendor: EPSON
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.00
             size: 3724MiB (3904MB)
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 3724MiB (3904MB)
                capabilities: partitioned partitioned:dos
              *-volume
                   description: Windows FAT volume
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /media/usb0
                   version: FAT32
                   serial: [REMOVED]
                   size: 3712MiB
                   capacity: 3720MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=ro,sync,nodev,noexec,noatime,nodiratime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted

```

---

### Post by mörgæs on 2016-09-12
The output shows that you have a standard net card which is [known to work well]("http://www.ubuntu.com/certification/catalog/component/pci/14e4%3A1698/") on Buntu.

It also shows that the installation was done in 2011. I suggest that you begin from a clean slate and do a fresh install of 16.04.1, erasing the old system in the process. More unpleasant surprises might hide here and there in such an old install.

---

### Post by uzzo23 on 2016-09-12
> **mörgæs said:**
> The output shows that you have a standard net card which is [known to work well]("http://www.ubuntu.com/certification/catalog/component/pci/14e4%3A1698/") on Buntu.

It also shows that the installation was done in 2011. I suggest that you begin from a clean slate and do a fresh install of 16.04.1, erasing the old system in the process. More unpleasant surprises might hide here and there in such an old install.

Thank ya'll so much for the advice. It's been working fine up until about a week ago. I was worried that it may be a bad ethernet jack. I did download ubuntu 10.04 yesterday and tried to run it as a live CD since that was the last best version of ubuntu IMHO. I had the same problem trying to run it from the CD, no internet connection. I may actually give Lubuntu a try this time around. I'll have to find a larger disk though. They won't fit on a standard CD anymore.

---

### Post by wildmanne39 on 2016-09-12
That release is to old no point installing it, you can not even update it so it is at risk if you use it on the internet.

Ubuntu Mate 16.04 is made to look like 10.04 and it is working great on my computer and I love it.

---

### Post by mörgæs on 2016-09-13
> **uzzo23 said:**
> I'll have to find a larger disk though. They won't fit on a standard CD anymore.

If you use the [minimal install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") then you can still use a CD.

---

### Post by uzzo23 on 2016-09-13
Well I tried, when it got to the DHCP configuration I got a Network autoconfiguration failed error. Just for kicks, I swapped places. I put my windows box where the Linux box usually sits. I wanted to rule out the cable and/or the port from the switch. It works just fine in the same spot. I posted this with it in the same spot as  my Linux machine usually sits. So it's either got to be a problem with the ethernet jack on that machine or something with the OS itself. Hopefully someone smarter than me can figure it out.

---

### Post by mörgæs on 2016-09-14
You just need to do some more experimenting. 

Does the minimal ISO work of you use a fixed IP address and not DHCP?
Can you boot the full ISO from a USB stick?

Did you remember to use 16.04.1 and not 16.04.0?

---

### Post by uzzo23 on 2016-09-14
> **mörgæs said:**
> You just need to do some more experimenting. 

Does the minimal ISO work of you use a fixed IP address and not DHCP?
Can you boot the full ISO from a USB stick?

Did you remember to use 16.04.1 and not 16.04.0?
I still can't get it to work. I tried entering my IP address and netmask manually. It gets to the archive mirror and tries to download and I get a "bad archive mirror" error. One of the reasons for that it says below is a unreliable network connection. I don't know what version I downloaded to be honest. I followed the link you gave me.

archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/mini.iso

---

### Post by mörgæs on 2016-09-15
You just need to do some more experimenting. You don't have to wait for people to get back to the thread. 

What if you choose a mirror in a neighbour country?
Can you boot the full ISO from a USB stick?

---

### Post by uzzo23 on 2016-09-15
I really don't know what else I can do my friend. I can build one, but when it has a problem, I don't know enough about them to do the troubleshooting. I tried a mirror from the UK and got the same thing. I don't have a USB stick, so I can't try that. Is there a way to test the ethernet jack to see if it's working properly?

---

### Post by mörgæs on 2016-09-16
The thread now has lasted four days, and maybe your problem has even longer. 

A USB stick is cheap around here. I don't know where you live but I guess it applies worldwide. 

Considering time versus money I suggest that you buy a USB stick and try that approach.

---

### Post by uzzo23 on 2016-09-16
> **mörgæs said:**
> The thread now has lasted four days, and maybe your problem has even longer. 

A USB stick is cheap around here. I don't know where you live but I guess it applies worldwide. 

Considering time versus money I suggest that you buy a USB stick and try that approach.

Well, I took your advice and purchased a 32 GB USB stick today. I downloaded the latest lubuntu ISO(16.04.1) image onto it from my windows machine. I put it in my Linux machine and changed the boot sequence to boot from (USB Device) and I get nothing but a flashing cursor. I can go back into BIOS and change the boot sequence back to the HD and the current version I have installed boots up. It's recognizing the stick and the ISO file on it. But it won't boot up from there for some reason, very frustrating. As a side note though. It's amazing to me how much storage space that they can fit into such a small device these days.

---

### Post by mörgæs on 2016-09-17
> **uzzo23 said:**
> It's amazing to me how much storage space that they can fit into such a small device these days.

Yes, development is going fast. I believe I still have one of my first 256 MB USB stick lying around somewhere. 

For how long time did you wait with the flashing cursor?

---

### Post by uzzo23 on 2016-09-17
> **mörgæs said:**
> Yes, development is going fast. I believe I still have one of my first 256 MB USB stick lying around somewhere. 

For how long time did you wait with the flashing cursor?

I left it on all night and it's still blinking as I type this reply.

---

### Post by mörgæs on 2016-09-17
You might be wondering why this is taking so many efforts when other people's install problems are solved within a few posts. 

The reason is that your Intel 82G33/G31 graphics controller is known to cause trouble (maybe you have already googled it). It does not mean 'impossible', just 'difficult'.

Is your computer a Dell Optiplex 360 or a close relative? 

When the install process from USB boot is hanging, does anything happen if you press Ctrl+Alt+F1?

---

### Post by uzzo23 on 2016-09-17
> **mörgæs said:**
> You might be wondering why this is taking so many efforts when other people's install problems are solved within a few posts. 

The reason is that your Intel 82G33/G31 graphics controller is known to cause trouble (maybe you have already googled it). It does not mean 'impossible', just 'difficult'.

Is your computer a Dell Optiplex 360 or a close relative? 

When the install process from USB boot is hanging, does anything happen if you press Ctrl+Alt+F1?
Nah, it's just a little frustrating when things don't work like they're supposed to. As long as one of my machines is working I'm in good shape. But I don't trust windows 7 either. But yes, you are correct. It is a Dell Optiplex 360. The only thing that happens when I press Ctrl+Alt+F1 is I hear a beeping noise coming from inside the box. Thank you for your patience with me and trying to help.

---

### Post by wildmanne39 on 2016-09-17
Hi, I really only work with wireless issues but from your first post with the screenshot I could not see a driver loaded for your device and I just want to make sure it is loaded would you please run:
```
lspci -nnk | grep -iA2 net
lsusb
```
and post the results here.
Thanks

---

### Post by uzzo23 on 2016-09-17
> **Wild Man said:**
> Hi, I really only work with wireless issues but from your first post with the screenshot I could not see a driver loaded for your device and I just want to make sure it is loaded would you please run:
```
lspci -nnk | grep -iA2 net
lsusb
```
and post the results here.
Thanks

What continues to baffle me is that it was all working fine up until a week or so ago.

> phillip@phillip-desktop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Dell Device [1028:0294]
    Kernel driver in use: tg3
phillip@phillip-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0781:5575 SanDisk Corp. 
Bus 001 Device 005: ID 04b8:088f Seiko Epson Corp. 
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
phillip@phillip-desktop:~$ 


---

### Post by wildmanne39 on 2016-09-17
It shows the driver in the first command and I am sorry I posted the wrong command for the second one please post the output of:
```
lsmod
```
That will confirm for sure if the driver is loading or not.
If it is there are a couple of people here that are good with ethernet connection issues hopefully one of them will post.

---

### Post by uzzo23 on 2016-09-17
> **Wild Man said:**
> It shows the driver in the first command and I am sorry I posted the wrong command for the second one please post the output of:
```
lsmod
```
That will confirm for sure if the driver is loading or not.
If it is there are a couple of people here that are good with ethernet connection issues hopefully one of them will post.

Not a problem my friend.

```
phillip@phillip-desktop:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39555  1 
bnep                   17830  2 
rfcomm                 38139  4 
bluetooth             158410  10 bnep,rfcomm
snd_hda_codec_analog    75395  1 
nls_iso8859_1          12617  2 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
nls_cp437              12751  2 
vfat                   17308  2 
fat                    55605  1 vfat
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
usbhid                 41937  0 
hid                    81731  1 usbhid
usblp                  17885  0 
snd_seq_midi           13132  0 
snd_rawmidi            25832  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51677  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28983  2 snd_pcm,snd_seq
i915                  432554  2 
snd                    62250  15 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_seq_device,snd_timer
mac_hid                13077  0 
ppdev                  12849  0 
psmouse                97340  0 
parport_pc             32114  1 
hwmon_vid              12723  0 
serio_raw              13027  0 
dcdbas                 14098  0 
drm_kms_helper         45466  1 i915
drm                   197676  3 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
shpchp                 32265  0 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            39646  2 
tg3                   141465  0 
phillip@phillip-desktop:~$ 

```

---

### Post by wildmanne39 on 2016-09-17
The driver is loaded, did you reset your router yet? I suggest deleting your connection from network manager and rebooting your router after it comes back up reboot your computer and let network manager find your connection if that does not help then hopefully an ethernet specialist will stop by.

---

### Post by uzzo23 on 2016-09-17
> **Wild Man said:**
> The driver is loaded, did you reset your router yet? I suggest deleting your connection from network manager and rebooting your router after it comes back up reboot your computer and let network manager find your connection if that does not help then hopefully an ethernet specialist will stop by.

I gave it a shot, it loaded up the wired connection but is still showing me disconnected.

---

### Post by wildmanne39 on 2016-09-17
You can bump the thread every 12 hours to keep it at the top of the forum so people can see it.
Good Luck

---

### Post by uzzo23 on 2016-09-17
> **Wild Man said:**
> You can bump the thread every 12 hours to keep it at the top of the forum so people can see it.
Good Luck
Okay, thank you so much for trying to help me!

---

### Post by evan8 on 2016-09-18
Same problem here. I use a thinkpad T420

Have rany many distros on sam elaptop like xuuntu etc with no issue. but the past week I can no longer connect wifi. Sometimes it will let me for some minutes or however but when i log on it's just dead.

I even ddi debian installer. added my firmware. shows my networks to connect to. would not connect. used linux on this machine for quite some time but the past week or longer it just barely works. even though it did not work. Did some ne wupdate or something mess this up? Works fine on windows and Ihad zero problem son linux a few weeks back.

LIke I said. I have ran many distros on the this same machine and other week or so all was well. I even got my network name son debian. I installed xubuntu using the wifi but now it's just dead. I'm not new to linux world so this one is just strange to me

---

### Post by wildmanne39 on 2016-09-18
> **evan8 said:**
> Same problem here. I use a thinkpad T420

Have rany many distros on sam elaptop like xuuntu etc with no issue. but the past week I can no longer connect wifi. Sometimes it will let me for some minutes or however but when i log on it's just dead.

I even ddi debian installer. added my firmware. shows my networks to connect to. would not connect. used linux on this machine for quite some time but the past week or longer it just barely works. even though it did not work. Did some ne wupdate or something mess this up? Works fine on windows an di had zero problem son linux a few weeks back.
Please start your own thread and do not hijack someone else's. Your issues are not remotely alike yours is wifi and his is ethernet.
Thanks

---

### Post by mörgæs on 2016-09-18
Could you try installing the [alternate Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") 16.04.1?

---

### Post by uzzo23 on 2016-09-18
> **mörgæs said:**
> Could you try installing the [alternate Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") 16.04.1?
I get the same thing, just a flashing cursor.

---

### Post by mörgæs on 2016-09-19
How did you install the present Ubuntu in the good old days (2011)?

---

### Post by uzzo23 on 2016-09-19
> **mörgæs said:**
> How did you install the present Ubuntu in the good old days (2011)?
  It's kind of a long story but I'll try and be brief. My first build was when 8.04 came out. Somewhere along the line something happened to the CPU and/or MOBO. It sat for a long period of time until I ran up on an old salvage box that had a MOBO with a pentium 4 processor. So I put it in not even thinking it would work. Well, it did work, it was just extremely slow, almost unresponsive. I started a thread that you actually replied to. But this was in 2014, In 2011 I probably still had the original configuration. That thread is here in case you want to look over it.

[https://ubuntuforums.org/showthread.php?t=2206785](https://ubuntuforums.org/showthread.php?t=2206785)

So, fast forward to April of this year. This Linux box had been sitting collecting dust because it was so slow it was almost unusable. So I started shopping around for a new MOBO and CPU for it. Well, I ran up on this refurb Dell on newegg for 65 bucks. It came with no OS and no software. I was going to have to spend somewhere in the neighborhood of $200.00 for decent MOBO and CPU. So I bought the Dell and took the HD out of the original box that already had 12.04 on it and stuck it in this Dell box and it fired right up and has been working fine up until about 2 weeks ago now. I have a thread on that one too if you'd like to look at it. So the version I have now was already on the HD when I put it in this Dell machine. I just took the HD  that came with it out and put mine in. What's strange to me is that I burned a 10.04 CD the other day and it booted with that. But yesterday I found a blank DVD lying around. So I put lubuntu 16.04.1 on it and tried to boot that up. It won't boot either, very strange.

[https://ubuntuforums.org/showthread.php?t=2319585](https://ubuntuforums.org/showthread.php?t=2319585)

---

### Post by mörgæs on 2016-09-19
What you did is a classic last resort: Move the hard disk to another computer, install Lubuntu 16.04.1 without any closed-source drivers and apply all updates. After that move the disk to the Dell.

Another suggestion is to update the BIOS. I have done that on other Dells with good results.

---

### Post by uzzo23 on 2016-09-19
> **mörgæs said:**
> What you did is a classic last resort: Move the hard disk to another computer, install Lubuntu 16.04.1 without any closed-source drivers and apply all updates. After that move the disk to the Dell.

Another suggestion is to update the BIOS. I have done that on other Dells with good results.

Boy what a nightmare this has turned out to be. I took the the HD out of the box I was running windows on and swapped it with the Dell machine that I was running linux on. I put the disk I had burned with Lubuntu 16.04.1 in and it didn't boot up. But, the current version I have did and with internet connection. So I thought to myself, I'll just put the HD with windows in the Dell box and leave it there since that's probably where it belongs in the first place. BIG mistake, I kept getting a boot error. So I decided to reinstall windows 7, another big mistake. It went all the way through and then gave a hardware malfunction error. "NMI: Parity check/Memory Parity error/ The system has halted". I did it 3 times and got the same thing. So now I'm showing 3 versions of windows 7 on that HD and it doesn't work. But, the HD with xubuntu 12.04 on it seems to be working fine in this other box now. As much as I like linux, there are still a few applications that I need windows for. So I really don't know where to go from here.

---

### Post by occasionalbicyclist on 2016-09-20
How are you creating the boot USB disk?

It sounds like you might be just simply copying the entire iso file onto the USB disk - without doing the special formatting that allows the disk to be booted from.

You need to make sure you use a tool like "unetbootin" or "dd" (Linux) or "Rufus" (windows) to create that boot disk..

---

### Post by mörgæs on 2016-09-20
> **uzzo23 said:**
> But, the HD with xubuntu 12.04 on it seems to be working fine in this other box now.

So far, so good. Now you can install 16.04.1 here, erasing the disk in the process.

---

