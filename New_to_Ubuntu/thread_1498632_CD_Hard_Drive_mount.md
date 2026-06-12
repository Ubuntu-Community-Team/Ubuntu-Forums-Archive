---
title: "CD Hard Drive mount"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Makosz on 2010-06-01
I have a cd drive that seems to be mounted but when i put in a cd and try to open it it says "unable to mount cdrom0" how can i read the cd's?
also i have a hard disk plugrd in and it either cant see it or it see's it as floppy disk because i do not have a floppy disk. how can i acess my other hard drive?

---

### Post by NUboon2Age on 2010-06-01
What is on the CD?  

When you run 

```
lshw
```

What does it say?

---

### Post by NUboon2Age on 2010-06-01
What is on the CD?  

> **Makosz said:**
> For now its just music

Hmmm... that's interesting... so its trying to mount a non-filesystem disk and isn't recognizing that its a music disk.

---

### Post by nhasian on 2010-06-01
if you don't have a floppy drive, go into your system bios and disable the floppy controller.  (sometimes its listed as FDD)

---

### Post by Makosz on 2010-06-01
For now its just music

---

### Post by NUboon2Age on 2010-06-01
If you go to a terminal and run

```
lshw

```
scroll back and copy the output and paste it into a reply here, it will give info to start trying to figure this problem out.

---

### Post by Makosz on 2010-06-01
this is it

mako@mako-desktop:~$ lshw
WARNING: you should run this program as super-user.
PCI (sysfs)  
mako-desktop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2518MiB
     *-cpu
          product: AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 1850MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 746 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis
          resources: irq:0 memory:d0000000-d3ffffff
        *-pci
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: memory:cdd00000-cfefffff memory:ada00000-cdbfffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5500]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:ce000000-ceffffff memory:b0000000-bfffffff(prefetchable) memory:cfee0000-cfefffff(prefetchable)
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
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia:0
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:c400(size=256) ioport:c000(size=128)
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
             resources: irq:20 memory:cfff8000-cfff8fff
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
             resources: irq:21 memory:cfff9000-cfff9fff
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:cfffa000-cfffafff
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
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:cfffb000-cfffbfff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:0b:6a:1e:9b:0a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=32 maxlatency=11 mingnt=52 multicast=yes
             resources: irq:19 ioport:bc00(size=256) memory:cfff7000-cfff7fff memory:a0000000-a001ffff(prefetchable)
        *-storage
             description: RAID bus controller
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=sata_sis latency=128
             resources: irq:17 ioport:dc00(size=8) ioport:d800(size=4) ioport:d400(size=8) ioport:d000(size=4) ioport:cc00(size=16) ioport:c800(size=128)
        *-multimedia:1
             description: Multimedia audio controller
             product: CM8738
             vendor: C-Media Electronics Inc
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2
             resources: irq:16 ioport:b800(size=256)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:18:39:0e:28:98
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11bg

---

