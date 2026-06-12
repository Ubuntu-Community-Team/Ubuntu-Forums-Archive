---
title: "Tips on fail-proof presentation using Ubuntu? a.k.a. VGA out issues"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by andresmh on 2009-01-26
I have been burned in the past when trying to do a presentation from my laptop using Ubuntu. With only a few minutes and people waiting I have sometimes resorted to having to boot in Windows because I couldn't get the projector to work immediately. I know if I have all the time of the world and with the help of the Ubuntu forums I could probably have figured out what the problem was with those projectors, but I am just wondering if there are any tips on things to disable/enable/install as I prepare for a presentation? Should I disable compiz? Should I configure Xorg in certain way?

Please enlight me! I don't want to have to use Windows!

---

### Post by sarath_it on 2009-01-26
I Generally try to keep it simple. My default user profile all the soopers! I dont do presentations but watch a lot of movies (on projector too sometimes). While whatching a 3 hour movie, even on just the lappy, you would not want to have compiz and all the baggage. I created a diff user profile for this and login to that when needed. and once the settings are in, you dont need to worry, it just works from thre.

---

### Post by MacKai on 2009-01-26
I'm having similar problems. I travel to different locations to do presentations, using various projectors and had no problems Ubuntu 8.40, but as soon as I installed 8.10  I would lock up when I connected to the same projectors that I used fine with 8.40. I had this problem originally with a clean install. I have now installed Compiz.... I have to use Windows to do my presentations...hate it

---

### Post by andresmh on 2009-01-26
[QUOTE=sarath_it;6620724you would not want to have compiz and all the baggage.[/QUOTE]

What else would you consider baggage?

---

### Post by sarath_it on 2009-01-26
conky, compiz, remote desktop, metacity (I use open box for the slim user prof), bluetooth, pretty much disable everything in session and only add pulse audio.. thats me :)

---

### Post by Martje_001 on 2009-01-26
What hardware do you have (if unsure: run lshw)? How do you connect the projector?

---

### Post by andresmh on 2009-01-26
I am connecting using a standard VGA cable, nothing fancy.  Unfortunately, I do not often have access to the room before a presentation. I come to a place and I have to present in between other people, so thereis not much time to prep. 


Here's my hardware:

```

$ lshw 
WARNING: you should run this program as super-user.
ibex300                   
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3030MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     L7100  @ 1.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 1201MHz
          capacity: 1201MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida cpufreq
          configuration: id=1
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
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:1c:25:ba:ba:fe
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.3-0 latency=0 module=e1000e multicast=yes
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 61
                serial: 00:21:5c:03:44:a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.1.102 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HBM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-844
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RC02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

---

### Post by Martje_001 on 2009-01-26
Could you also give the output of 'xrandr'? For what I've seen now, you've a good change that your hardware is supported.

---

### Post by mister_pink on 2009-01-26
I tend to find all I need to do to get an external screen to work is log out and in again.

---

### Post by andresmh on 2009-01-26
I have been successful at connecting to projectors in the past, but about 40% of the time something goes wrong. 

Here's xrandr

```

$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 2880 x 900
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 287mm x 180mm
   1440x900       60.0*+   59.9     50.0  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  

```

---

### Post by MacKai on 2009-01-26
I'm using a Dell 1330 with an Nvidia video card. I'm connecting with a VGA. i also rarely have more than 15min to set up. i have tried logging out and back on with no success. i get a signal to the projector it jut locks/ gets real slow so i can't advance to the next slide.

---

