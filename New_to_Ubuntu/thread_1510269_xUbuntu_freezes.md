---
title: "xUbuntu freezes"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by cio_1812 on 2010-06-15
i have xUbuntu 10.4 on my old laptop, an e-machines M5310 (new installation)

the problem is that in freezes after a random time, sometimes works fine for hours

when it freezes I get a black screen, I can see the mouse pointer but it's inactive

and the CapsLock just keeps blinking

---

### Post by NCLI on 2010-06-15
The blinking CapsLock light means that the system has encountered a serious error, a so-called [Kernel Panic]("http://en.wikipedia.org/wiki/Kernel_panic"). This is usually caused by failed or failing hardware, often the harddisk.

Please post the output of the command "lshw" This command has to be entered into a terminal, found under Application->Accesories->Terminal.

---

### Post by mapes12 on 2010-06-15
Xubuntu uses a different GUI compared to Ubuntu so that low end hardware can run it. I would have a go with Ubuntu and see if the machine can handle it. Failing that Puppy Linux has always worked for me on old machines.

---

### Post by halitech on 2010-06-15
a quick google search shows a lot of people with that machine and an overheating problem. Does the palm rest or the bottom feel overly warm to the touch? If it does, time for a good cleaning.

the specs look like it should handle Ubuntu easily.
```
Specs: 1.8-GHz Athlon XP-M 2400+, 
512MB DDR SDRAM, 
40GB hard drive, 
DVD/CD-RW drive, 
three USB 2.0 and one FireWire port, 
15.4-inch WXGA display, 
802.11g, 
6.6 lbs. system weight 
```

---

### Post by achase79 on 2010-06-15
using the powernowd package (installable from synaptic package manager) will help scale the processor and will reduce the heat.  This won't help in processor intensive instances though.

---

### Post by cio_1812 on 2010-06-15
hello, thank you for your replies
here's the result from lshw

```
ionut-laptop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 434MiB
     *-cpu
          product: Mobile AMD Athlon(tm) XP 2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 1788MHz
          capacity: 1788MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up cpufreq
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
          product: AGP Bridge [IGP 320M]
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 13
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64
          resources: irq:0 memory:d4000000-d7ffffff(prefetchable) memory:d0400000-d0400fff(prefetchable) ioport:8090(size=4)
        *-pci
             description: PCI bridge
             product: PCI Bridge [IGP 320M]
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=4096) memory:d0100000-d01fffff memory:e0000000-efffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: Radeon Mobility U1
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:10 memory:e0000000-efffffff(prefetchable) ioport:9000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff(prefetchable)
        *-isa
             description: ISA bridge
             product: M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2
             resources: irq:11 ioport:8400(size=256) memory:d0008000-d0008fff
        *-communication UNCLAIMED
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ALi Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=64
             resources: memory:d0009000-d0009fff ioport:8800(size=256)
        *-pcmcia
             description: CardBus bridge
             product: PCI4410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:10 memory:ffbfe000-ffbfefff ioport:1000(size=256) ioport:1400(size=256) memory:1c000000-1fffffff(prefetchable) memory:20000000-23ffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: PCI4410 FireWire Controller
             vendor: Texas Instruments
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3
             resources: irq:10 memory:d000c000-d000c7ff memory:d0000000-d0003fff
        *-network:0
             description: Network controller
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=b43-pci-bridge latency=64
             resources: irq:10 memory:d0004000-d0005fff
        *-usb:0
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
             resources: irq:11 memory:d000a000-d000afff
        *-usb:1
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: d.1
             bus info: pci@0000:00:0d.1
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
             resources: irq:11 memory:d000b000-d000bfff
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: d.2
             bus info: pci@0000:00:0d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=132 maxlatency=34 mingnt=16
             resources: irq:11 memory:d000c800-d000c8ff
        *-network:1
             description: Ethernet interface
             product: BCM4401 100Base-T
             vendor: Broadcom Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             logical name: eth0
             version: 01
             serial: 00:03:25:08:97:39
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom ethernet physical
             configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
             resources: irq:11 memory:d0006000-d0007fff memory:24000000-2401ffff(prefetchable)
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_ali latency=64 maxlatency=4 mingnt=2
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8080(size=16)
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus latency=0
             resources: irq:0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:61:f0:bd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11bg

```

---

### Post by cio_1812 on 2010-06-15
i have just cleaned the fan and proc radiator
before the cleaning the fan often went crazy and the system overheated, eventually shutting down (with XP os)
but afterwards I did not notice this kind of symptoms. I mean the fan revs are constant, only the black screen with the inactive mouse pointer and flickering CapsLock (with xUbuntu)

but it still might be a heat problem

---

### Post by achase79 on 2010-06-15
Is this problem happening while tring to return from a suspend?  
Are you able to get to a terminal using ctrl+alt+F1

If you are able to get to a terminal you may want to log in and run "top" to see if something is hanging or to restart the x-server.

---

