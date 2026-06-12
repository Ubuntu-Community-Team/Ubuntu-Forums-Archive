---
title: "graphics issue? horizontal lines zipping across screen"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by eagle416 on 2010-05-03
I have installed ubuntu netbook edition on my friend's Gateway ZA8. We put 9.10 on initially, but then tried to upgrade. someone unplugged the computer while it was upgrading and it wouldn't start when it was finished, so I did a fresh install from USB.

So right now I am using ubuntu netbook edition 10.04 lucid

Anyway, now I have horizontal bars of greyish white pixels flashing at seemingly random heights and times. I can still use the computer, but it is really annoying. What can be done to configure my graphics system so that it will stop? lspci is listed below, but I don't know what do do with the info.

Eagle416

```
jonai@jonai-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
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
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by conradin on 2010-05-03
Does this video issue persist when your in the terminal? (alt+F2) to find out. 
I will guess your graphics card driver is corrupt. I dont see your graphics controller in the list you included, try lshw, to find out what it is.

Try booting into recovery mode and repairing your packages.

---

### Post by eagle416 on 2010-05-03
in gnome terminal the problem persists, and it even persists when I hit CTRL ALT F8 and start a CLI session.

I shall try repairing the packages. when i boot into recovery mode how should I go from there?

lshw listed below

```
buntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 433MiB
     *-cpu
          product: AMD Athlon(tm) Processor L110
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.12.2
          size: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
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
             resources: ioport:9000(size=4096) memory:f0000000-f01fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:27 memory:d0000000-dfffffff(prefetchable) memory:f0100000-f010ffff ioport:9000(size=256) memory:f0000000-f00fffff
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
             configuration: driver=pcieport
             resources: irq:24 ioport:a000(size=4096) memory:20000000-200fffff ioport:cfd00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 02
                serial: 00:26:9e:67:c1:97
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
                resources: irq:26 ioport:a000(size=256) memory:cfdef000-cfdeffff(prefetchable) memory:cfdf0000-cfdfffff(prefetchable) memory:cfd00000-cfd0ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:f0200000-f02fffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: 0c:ee:e6:da:05:e6
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=10.204.2.49 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 memory:f0200000-f020ffff
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
             resources: irq:22 ioport:8440(size=8) ioport:8434(size=4) ioport:8438(size=8) ioport:8430(size=4) ioport:8400(size=16) memory:f0508000-f05083ff
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
             resources: irq:16 memory:f0504000-f0504fff
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
             resources: irq:17 memory:f0505000-f0505fff
        *-usb:2
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
             resources: irq:17 memory:f0506000-f0506fff
        *-usb:3
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
             resources: irq:18 memory:f0507000-f0507fff
        *-usb:4
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
             resources: irq:19 memory:f0508400-f05084ff
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
             resources: irq:0 ioport:8410(size=16)
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
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
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
             resources: irq:16 memory:f0500000-f0503fff
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
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage

```

---

### Post by Subespaciovectorial on 2010-07-15
The same problem, man. I have a packard bell and the horizontal lines appears randomly on the screen on every tty.

I tried with 'ubuntu 10.04' and 'ubuntu 10.04 netbook' and the problem persist. This doesn't happen on windows when I run it from the grub. The big problem is that, after a while, the horizontal lines get wider and stationary on the top, so I can hardly see the top of the screen, and then all the characters on the windows get distorted...

I would appreciate a lot if someone fixed the problem, I don't want to use windows.

---

### Post by Pablo Alonso on 2011-04-25
Hey man, I am experiencing something similar even trying now the latest beta of ubuntu natty narwhal 11.04......

have anyone found a solution to this problem ???
ubuntu in this machine is totally unusable. the weird part is that booting from an usb stick the graphics seems to work right... when the system got finally installed the problem in my case shows up!
 :confused:

thanks
regards,
Pablo

---

