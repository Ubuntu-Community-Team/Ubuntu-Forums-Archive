---
title: "linux games fail?"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by lolman on 2009-10-06
OK, I have new problem. i have linux mint and it works great, cant say ive ever had a more flashy version of ubuntu. anyways. the games WARSOW, and SAUBRATEN, won't work. all i get of SAUBRATEN is a blue cube to show up and WARSOW won't so much as start up without crashing my computer... help please!!

---

### Post by Terl on 2009-10-06
> **lolman said:**
> OK, I have new problem. i have linux mint and it works great, cant say ive ever had a more flashy version of ubuntu. anyways. the games WARSOW, and SAUBRATEN, won't work. all i get of SAUBRATEN is a blue cube to show up and WARSOW won't so much as start up without crashing my computer... help please!!

If you have desktop effects turned on, try turning them off and running the game.  Some 3d games don't work well with the effects.

Do you have your graphics drivers installed?

---

### Post by nwadams on 2009-10-06
what specs are your computer? and have they worked before?

---

### Post by lolman on 2009-10-07
actually my computer is a piece of junk but yes they have worked before

---

### Post by lavinog on 2009-10-07
What has changed since they last worked? was there a major update?
what are the system specs...video card...etc

---

### Post by running_rabbit07 on 2009-10-07
> **Terl said:**
> If you have desktop effects turned on, try turning them off and running the game.  Some 3d games don't work well with the effects.

Do you have your graphics drivers installed?

+1 I have to turn off effects every time I start VBox or it will lock up the graphics.

---

### Post by lolman on 2009-10-07
i have no ide what my specs are but the desktop efects did have a new thing that i added on... that might be it

---

### Post by lavinog on 2009-10-07
if you open a terminal, you can use lshw to display your system specs
post it here if you would like.

---

### Post by Thelasko on 2009-10-07
Try running the programs for the terminal and post the output.  It may be something as simple as lacking MIDI playback support.  A software MIDI synthesizer is available with the "timidity" package.

---

### Post by lolman on 2009-10-20
ok here are my specs

minty-fresh               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1002MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          size: 18EHz
          width: 32 bits
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
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
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82915G/P/GV/GL/PL/910GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G71 [GeForce 7950 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:30:1b:b6:91:84
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.24a ip=192.168.1.101 latency=0 module=tg3 multicast=yes
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
        *-usb:3
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
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: a
                bus info: pci@0000:03:0a.0
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
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
             configuration: latency=0
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
        *-ide:1
             description: IDE interface
             product: 82801FR/FRW (ICH6R/ICH6RW) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
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
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: a6:ee:49:72:44:fc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes:confused:

---

### Post by lavinog on 2009-10-20
```
*-display
description: VGA compatible controller
product: G71 [GeForce 7950 GT]
vendor: nVidia Corporation
```

do you have the nvidia proprietary driver installed?

---

### Post by lolman on 2009-10-29
I dunno

---

### Post by lavinog on 2009-10-29
goto system>administration>hardware drivers
and see if there is a driver for your card, if so enable it.

---

### Post by lolman on 2009-10-29
oh ok. ill try that

---

### Post by Ijtaba on 2009-10-29
Lolman your system is 5 years "Newer" than mine and you dont know what youve got :@

---

### Post by lolman on 2009-11-03
heh, that is funny... of course, i've never really payed attention to any aspect of my computer that was complex. i just get it working, and play my games... and sometimes watch movies:popcorn:

---

