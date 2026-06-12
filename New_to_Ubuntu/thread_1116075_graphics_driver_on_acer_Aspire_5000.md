---
title: "graphics driver on acer Aspire 5000"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Bel-Mondo on 2009-04-04
I noticed that no graphics driver is set, in System--> Administration --> Hardware Drivers. Could this be why e.g. Celestia runs really badly?
If so, how do I get a graphics driver?

---

### Post by roger_1960 on 2009-04-04
Hi

Can you post the output from
> lshw
so we can tell what hardware you have?

Do this by typing the command into the terminal - found at applications-accessories-terminal

---

### Post by overdrank on 2009-04-04
Hi and welcome the command lspci may be better as it is a lot less info for them to copy and paste. :) You can look for VGA and this will be the graphics card.
The terminal is located under applications, accessories.

---

### Post by Bel-Mondo on 2009-04-04
> **roger_1960 said:**
> Hi

Can you post the output from

so we can tell what hardware you have?

Do this by typing the command into the terminal - found at applications-accessories-terminal

```
runi@kommunistiska-propagandamaskinan:~$ lshw
WARNING: you should run this program as super-user.
kommunistiska-propagandamaskinan
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 946MiB
     *-cpu
          product: AMD Turion(tm) 64 Mobile Technology ML-34
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.4.2
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-pci:0
          description: Host bridge
          product: 760/M760 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=64 module=amd64_agp
        *-pci
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128 module=pata_sis
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=173 maxlatency=11 mingnt=52
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
             configuration: driver=Intel ICH latency=173 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80 module=ehci_hcd
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:16:36:5e:06:f0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.10.155 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
        *-pcmcia
             description: CardBus bridge
             product: PCI1510 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-network:1
             description: Network controller
             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=b43-pci-bridge latency=64 module=ssb
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:cf:06:30:75
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
runi@kommunistiska-propagandamaskinan:~$ 

```


> **overdrank said:**
> Hi and welcome the command lspci may be better as it is a lot less info for them to copy and paste. :) You can look for VGA and this will be the graphics card.
The terminal is located under applications, accessories.

Thank you very much.

```
runi@kommunistiska-propagandamaskinan:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
runi@kommunistiska-propagandamaskinan:~$ 

```

---

### Post by roger_1960 on 2009-04-04
Hi

Sadly, you may be out of luck - see the thread below.  (Unless anyone knows better of course)

[http://ubuntuforums.org/showthread.php?t=1085347](http://ubuntuforums.org/showthread.php?t=1085347)

---

### Post by overdrank on 2009-04-04
Hi and I have very little experience with the 
VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
But is should not have a driver listed. If you are looking for the 3d support I do not believe you will be able to achieve this.

---

### Post by Bel-Mondo on 2009-04-04
> **overdrank said:**
> Hi and I have very little experience with the 
VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
But is should not have a driver listed. If you are looking for the 3d support I do not believe you will be able to achieve this.

Thank you for your help overdrank and roger.
I was merely speculating that this might be why celestia is working so badly. I would really love to use celestia to explore the universe ;)
But well.. yes, it looks like I am out of luck.
Thank you.

---

