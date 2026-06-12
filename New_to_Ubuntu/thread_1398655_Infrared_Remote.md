---
title: "Infrared Remote?"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2010-02-04
Hi all, 

I have a question that may or may not help me plan out a weekend project.

How do I determine if my computer (Dell Inspiron 1521) has a usable IR receiver? It appears to have one on the front chassis, underneath where the touchpad and music buttons are, but I have never been able to see if it works.


How do I find out if it works, and if it does; how do I set it up? I have an unused apple remote here, as well as a universal remote- would either of them work?

---

### Post by audiomick on 2010-02-04
Should turn up in
```
lspci
```
shouldn't it?

---

### Post by tom.swartz07 on 2010-02-04
> **audiomick said:**
> Should turn up in
```
lspci
```
shouldn't it?

Thats what I thought, but I dont know what it would be listed as.


Now the obligatory terminal scrape:

```
tom@karmic-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

```
tom@karmic-laptop:~$ lshw
WARNING: you should run this program as super-user.
karmic-laptop             
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 4608MiB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-56
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: ioport:e000(size=4096) memory:fe900000-feafffff ioport:e0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: memory:e0000000-efffffff(prefetchable) memory:fe9f0000-fe9fffff ioport:ee00(size=256) memory:fea00000-feafffff
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 memory:fe800000-fe8fffff
           *-network
                description: Wireless interface
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: eth1
                version: 01
                serial: 00:1c:26:0f:25:7c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.254.56 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:fe8fc000-fe8fffff
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:d000(size=4096) memory:fe600000-fe7fffff ioport:f0000000(size=2097152)
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=16) memory:fec01000-fec013ff
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:ffb00000-ffb00fff
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:ffb01000-ffb01fff
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:ffb02000-ffb02fff
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:ffb03000-ffb03fff
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:ffb04000-ffb04fff
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:20 memory:ffa80000-ffa800ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:10c0(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:febfc000-febfffff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:fe500000-fe5fffff
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:19:b9:84:59:33
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
                resources: irq:21 memory:fe5fe000-fe5fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:23 memory:fe5fd800-fe5fdfff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:20 memory:fe5fd500-fe5fd5ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: memory:fe5fd600-fe5fd6ff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: memory:fe5fd700-fe5fd7ff
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
          configuration: driver=k8temp
          resources: irq:0
  *-scsi:0
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@7
       logical name: scsi7
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
tom@karmic-laptop:~$ 

```


Anyone see anything that would be like an IR device?

---

### Post by audiomick on 2010-02-04
Nothing jumps out at me...

---

### Post by drzoo2 on 2010-02-04
> **audiomick said:**
> Nothing jumps out at me...

IR ports run on the serial bus so this may be it.

```
*-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:10c0(size=16)

```

---

### Post by tom.swartz07 on 2010-02-05
> **drzoo2 said:**
> IR ports run on the serial bus so this may be it.

```
*-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:10c0(size=16)

```

Alrighty, supposing that it is connected here, how would I use it/see if its working?

---

### Post by tom.swartz07 on 2010-02-05
bumpity bump

---

### Post by audiomick on 2010-02-05
Hi Tom.
Just so you don't feel deserted: sorry, now idea how to get it started.;)
Out of interest, have you searched for specs on the machine to see if it claims to have IR or not, or are you just going on the fact that it looks like a receiver and it is a fair assumption that a laptop would have it?

edit:
Hmmm, the laptop is listed in the Ubuntu Hardware support list, but the infra red is untested....

---

### Post by fatality_uk on 2010-02-05
[https://help.ubuntu.com/community/IrdaHowto](https://help.ubuntu.com/community/IrdaHowto)

---

### Post by warfacegod on 2010-02-05
Aarrghghg! Where's the gorilla and the shark!!!?

---

### Post by audiomick on 2010-02-05
> **warfacegod said:**
> Aarrghghg! Where's the gorilla and the shark!!!?
Thought it had changed. Looks like Tom's got crabs...

---

### Post by warfacegod on 2010-02-05
> **audiomick said:**
> Thought it had changed. Looks like Tom's got crabs...

Let's get his Crabby Patties!

---

### Post by tom.swartz07 on 2010-02-05
> **warfacegod said:**
> Let's get his Crabby Patties!

HAHAHA! Quab!


Ill check that link here now and let you guys know what comes of it

---

### Post by tom.swartz07 on 2010-02-05
I couldnt make heads or tails of that doc that was posted. I tried all of it, but it seems that its pretty much outdated. It was last updated for Breezy and later for 8.10.


I mean, its not a big deal if I cant get it running, although it would be really nice to have a remote to go with it.

---

### Post by audiomick on 2010-02-05
Well the packages that the guide says to install are still available. I am able to search them and find them in synaptic package manager. I guess files get created when the packages are there. The files aren't there on my machine, at least.

---

### Post by tom.swartz07 on 2010-02-05
> **audiomick said:**
> Well the packages that the guide says to install are still available. I am able to search them and find them in synaptic package manager. I guess files get created when the packages are there. The files aren't there on my machine, at least.

Yeah, the packages are there, but the config files that the guide points to arent. I guess they updated and changed (similar to grub) in recent times...

---

### Post by audiomick on 2010-02-05
> **tom.swartz07 said:**
> Yeah, the packages are there, but the config files that the guide points to arent. I guess they updated and changed (similar to grub) in recent times...
Maybe, or maybe they just don't get created until the drivers or whatever are on the computer?

---

### Post by warfacegod on 2010-02-05
Install them and see if they work. If not, remove them. It's not like this is Windows and installing one app will give you 15 minutes of registry cleaning.

---

### Post by mhgsys on 2010-02-11
@tom.swartz07

Your Dell Inspiron 1521 seems to have a Consumer IR sensor compatible with Philips RC6 (receive
            only)

(You should be able to enable it in BIOS, When the DELL logo appears, press <F2> immediately.


[http://support.dell.com/support/edocs/systems/ins1521/en/om_en/pdf/RT722A02MR.pdf](http://support.dell.com/support/edocs/systems/ins1521/en/om_en/pdf/RT722A02MR.pdf).
(page 182/183)

Just dropping a alternative way though.

(I'm gonna build this myself when I finally find the time)

[http://www.instructables.com/id/RS-232-Infrared-Receiver-in-a-Serial-Connector-LI/](http://www.instructables.com/id/RS-232-Infrared-Receiver-in-a-Serial-Connector-LI/)

and make it work with lirc  [http://lnx.manoweb.com/lirc/?partType=section&partName=lirc](http://lnx.manoweb.com/lirc/?partType=section&partName=lirc)

or MythUbuntu

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

---

### Post by tom.swartz07 on 2010-02-11
> **mhgsys said:**
> @tom.swartz07

Your Dell Inspiron 1521 seems to have a Consumer IR sensor compatible with Philips RC6 (receive
            only)

(You should be able to enable it in BIOS, When the DELL logo appears, press <F2> immediately.


[http://support.dell.com/support/edocs/systems/ins1521/en/om_en/pdf/RT722A02MR.pdf](http://support.dell.com/support/edocs/systems/ins1521/en/om_en/pdf/RT722A02MR.pdf).
(page 182/183)

Just dropping a alternative way though.

(I'm gonna build this myself when I finally find the time)

[http://www.instructables.com/id/RS-232-Infrared-Receiver-in-a-Serial-Connector-LI/](http://www.instructables.com/id/RS-232-Infrared-Receiver-in-a-Serial-Connector-LI/)

and make it work with lirc  [http://lnx.manoweb.com/lirc/?partType=section&partName=lirc](http://lnx.manoweb.com/lirc/?partType=section&partName=lirc)

or MythUbuntu

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

WOW! thanks for all of that sweet info!

Ill def look into it.

---

