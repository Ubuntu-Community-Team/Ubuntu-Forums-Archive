---
title: "Wieless modem"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Helaya on 2009-02-28
Hi, I recently installed Interpid Ibex on my PC with dual booting. I  cant setup my Bandluxe C120 wireless modem with it. Is any one there to help, please.:confused:

---

### Post by DevinMcElheran on 2009-03-02
What to you mean by "setup" the modem? Do you mean connect? Do you by any chance mean laptop when you say pc?

---

### Post by damis648 on 2009-03-02
If I understand correctly, you're trying to connect to wireless, right? In order to get a clearer picture of your setup, could you open terminal (Applications>Accessories) and post the output of the following command:
```
lspci
```

---

### Post by Helaya on 2009-03-03
> **DevinMcElheran said:**
> What to you mean by "setup" the modem? Do you mean connect? Do you by any chance mean laptop when you say pc?
Actualy I have a desktop pc and and I want to connect to the internet using my newly bought Bandluxe c120 wireless modem. In windows I could connect easily to the net using the modem.

---

### Post by Helaya on 2009-03-03
> **damis648 said:**
> If I understand correctly, you're trying to connect to wireless, right? In order to get a clearer picture of your setup, could you open terminal (Applications>Accessories) and post the output of the following command:
```
lspci
```
yes I wanted to connect to the net using wireless modem.Following are the outcome of the command you mentioned.

[B]roshan@Maya:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by damis648 on 2009-03-03
Note, you probably mean wireless card, not modem. :popcorn:
In any case, does this card happen to be USB? Because I can't seem to see it on the list of PCI devices. Would you mind also posting:
```
lsusb
lshw
```


> **Helaya said:**
> yes I wanted to connect to the net using wireless modem.Following are the outcome of the command you mentioned.

[B]roshan@Maya:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 
Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by manowar689 on 2009-03-03
its actually a 3g modem card yes ??? if so i would suggest switchind to hardy it has good support for these devices

---

### Post by Helaya on 2009-03-03
> **damis648 said:**
> Note, you probably mean wireless card, not modem. :popcorn:
In any case, does this card happen to be USB? Because I can't seem to see it on the list of PCI devices. Would you mind also posting:
```
lsusb
lshw
```
damis648
This is a 3G wireless modem connected through USB. Following is the outcome of the commands you mentioned.

roshan@Maya:~$ lsusb
Bus 004 Device 002: ID 1a8d:1002  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2045 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
roshan@Maya:~$ lshw
WARNING: you should run this program as super-user.
maya                      
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1263MiB
     *-cpu
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr lahf_lm
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
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
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
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-cdrom
                description: DVD-RAM writer
                product: 16X16X5X
                vendor: DVDRW
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: MTS1
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
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
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:50:8d:c3:22:05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sis latency=32 module=sata_sis
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:26:c2:f3:c4:a9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
roshan@Maya:~$ 


Thanx

P S: I found following link which describes to install modem on ubuntu 8.0, but it seems different in 8.14

[http://www.arabteam2000-forum.com/index.php?act=attach&type=post&id=73596](http://www.arabteam2000-forum.com/index.php?act=attach&type=post&id=73596)

---

### Post by damis648 on 2009-03-03
Ah, I had no idea that was a 3G wireless card. Now as far as I know many 3G cards are supported OOTB, can you set it up via right-clicking the network icon in the upper right-hand corner and clicking the 'Edit Connections' button and going to the 3G tab?

---

### Post by Helaya on 2009-03-04
Thank you for helping me damis648,
i tried that but I couldn't fix it b, cos I'm not much tech savy. In places my modem shows as cd R/W.

---

### Post by Helaya on 2009-03-04
Thank you manowar689
I found this link which explains it on 8.04 but its different in 8.14. Any suggestions please.
(by the way i'm not good with these tech things.)
[http://www.arabteam2000-forum.com/index.php?act=attach&type=post&id=73596]("http://www.arabteam2000-forum.com/index.php?act=attach&type=post&id=73596")

---

### Post by Helaya on 2009-03-05
> **manowar689 said:**
> its actually a 3g modem card yes ??? if so i would suggest switchind to hardy it has good support for these devices


Since there is setup details available for Bandluxe c120 modem on Hardy, can anyone help me to install (or downgrade to) Hardy from Interpid.

---

### Post by ddreamer on 2010-08-19
Hi, all:
I have successfully connected to the internet through BandLuxe C120 by NetworkManager in Ubuntu 10.04. Please refer to [http://swiss.ubuntuforums.org/showthread.php?p=9739114&highlight=bandluxe+c120#post9739114](http://swiss.ubuntuforums.org/showthread.php?p=9739114&highlight=bandluxe+c120#post9739114)
Good Luck...

---

