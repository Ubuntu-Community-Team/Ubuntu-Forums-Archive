---
title: "Wireless Problems with a D620 / Broadcom BCM4311"
date: 2013-12-22
forum: Networking &amp; Wireless
---

### Post by disintergrator on 2013-12-22
Hi, 
As stated, I am having trouble getting wifi to work on a Latitude D620. I have tried installing the newer versions of Linux Mint, Ubuntu Studio, Ubuntu, Kubuntu, and now I am on Xubuntu. I have tried a few different walkthroughs for this particular problem (like using sudo apt-get install linux-firmware-nonfree & 
sudo apt-get install firmware-b43-installer), 
but so far, none have worked. Here is what is displayed when I run lshw in Terminal. 

lshw:
```
 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2006MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow cpufreq
          configuration: id=0
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
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:eff00000-eff7ffff ioport:eff8(size=8) memory:d0000000-dfffffff memory:efec0000-efefffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:eff80000-efffffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:efebc000-efebffff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:8c000000-8c1fffff ioport:8c200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:efd00000-efdfffff ioport:8c400000(size=2097152)
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=wl latency=0
                resources: irq:17 memory:efdfc000-efdfffff
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:efc00000-efcfffff ioport:8c600000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:1c:23:07:06:cc
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 duplex=full firmware=5752-v3.19 ip=192.168.1.72 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:44 memory:efcf0000-efcfffff
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
             resources: irq:20 ioport:bf80(size=32)
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
             resources: irq:21 ioport:bf60(size=32)
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
             resources: irq:22 ioport:bf40(size=32)
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
             resources: irq:23 ioport:bf20(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:ffa80000-ffa803ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:80000000-87ffffff ioport:88000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 40
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: irq:18 memory:80000000-80000fff ioport:5000(size=256) ioport:5400(size=256) memory:88000000-8bffffff memory:84000000-87ffffff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
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
             resources: ioport:10c0(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
 
```

I also read somewhere that this command may be of help:
lspci -vnn -d 14e4:
```
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
    Subsystem: Dell Latitude D620 [1028:01c2]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at efcf0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at efdfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl

```

Any suggestions would be greatly appreciated. Thank you in advance.

---

### Post by chili555 on 2013-12-22
Here is my suggestion. Please hook up the ethernet temporarily. Open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and let us hear the result.

---

### Post by disintergrator on 2013-12-22
That last command, I think I have done before. Anyway, I did the first command and it seemed to complete normally, but after doing the second command, this is what it prompted me with:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

PS
About to reboot, unplug ether, and see if it will work. I will let you know. 
And thanks again, especially for the speedy reply.

---

### Post by disintergrator on 2013-12-22
Ok. Wifi is working great now, Thank you so much. Upon rebooting, it did say something about some number (i.e. 2435782) kvm disabled by BIOS, but it flashed so quickly I did not get what the number was. But I assume this is ok. 
Will this procedure also work on other flavors of Linux (Linux Mint, Kubuntu, Zorin, Bodhi, etc.) with this laptop? And if so, would you have a reccomendation on a version that is user-friendly for a senior (my dad) coming from the Windows XP environment, but also one with respect of being used on a 2-4 year old dual core laptop? Again, thank you so much.

---

### Post by chili555 on 2013-12-22
The procedure will work perfectly in kubuntu, which I recommend. You needn't do the first step if you resist the urge to allow Additional Drivers to install the wrong driver for your 4311 device; all you need is the firmware piece.

I don't know much about the other variants, Mint, et al.

By the way, I am a senior, too; a great-grandfather. My wife uses and loves kubuntu. Anything new has a short learning curve. I'm confident Dad will grow to like it.

---

### Post by disintergrator on 2013-12-23
Thank you for the advice. I think we will leave Xubuntu on it for the moment, since my wife just told me she liked it and was already getting used to it. But if I ever dual-boot it, and I do have another laptop I am now thinking of putting Kubuntu on. Question of curiousity: When talking about older laptops as well as desktops, is there ever a reason to NOT use the newest (12.10, now, I think) version of Ubuntu? Or should you pretty much always grab the latest version, whether your pc was made 8 years ago, or 8 weeks ago? 

Congrads on the children and grand(s). I think Dad will like this too.

By the way, I notice it said you are from SC. We are too, and we live in Anderson. Just thought it was a pleasant coincident.

---

### Post by chili555 on 2013-12-24
The latest version is 13.10. I am a latest and greatest kinda guy. I think any machine will run the latest kernel well; the the graphical environment, Unity, Gnome, KDE, Xfce, etc., is another matter. Unity is pretty resource hungry but that's no problem for multi-core processors, capable video cards and tons of RAM. On the other end of the scale is Xfce. Just about anything that still runs should be able to run Xfce, the lightweight desktop environment in xubuntu.

Of course, the nice thing is that you can try the live DVD; if it runs well enough there, it will run even a bit better after it's fully installed!

---

