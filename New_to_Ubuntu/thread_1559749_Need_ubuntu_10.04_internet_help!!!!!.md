---
title: "Need ubuntu 10.04 internet help!!!!!"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by 11rohrbacherk on 2010-08-23
I just downloaded ubunutu for the first time and cannot find a way to connect to the internet at all. First of all no networks can even be found, so i used my brother's cisco linksys flash drive thing and it found my wireless network. I click connect and it starts to try to connect for a minute then just says "Disconnected - You are now offline." My Modem and router is on and fully functioning with my other computers in the house, and i have tried all the troubleshooting guides. SOMEONE PLEASE HELP!

---

### Post by JBAlaska on 2010-08-23
Is it a laptop? If so please post Make and Model.

Please post the output of these commands:
```
lspci
```
```
lsusb
```
```
iwconfig
```
Thanks.

---

### Post by silbak04 on 2010-08-23
try installing the driver for it in linux....type this in the terminal ```
$ lshw 
``` or ```
$ lspci 
``` to see what kind of network adapter you have, and then go look for the driver

---

### Post by 11rohrbacherk on 2010-08-23
Yes it is an Acer Aspire 5610Z i typed in those in the terminal and this is what i got:
 
 
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1737:0071 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11abgn  ESSID:";pd$\x11\x9E\x09\xDC\xAA\xD4\xAC\xF2\x1B\x10\xAF;3\xCD\xE3PHG\x15\\xBBo"\x19\xBA\x9B}\xF5"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=5 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL]

---

### Post by 11rohrbacherk on 2010-08-23
@ Silbak04 this is what i got:
 
 
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] $ lshw
$: command not found
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] lshw
WARNING: you should run this program as super-user.
kyle-laptop               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: Genuine Intel(R) CPU           T2060  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor est tm2 xtpr pdcm cpufreq
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
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: [EMAIL="pci@0000:00:00.0"]pci@0000:00:00.0[/EMAIL]
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
             bus info: [EMAIL="pci@0000:00:02.0"]pci@0000:00:02.0[/EMAIL]
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0100000-d017ffff ioport:5088(size=8) memory:c0000000-cfffffff(prefetchable) memory:d0200000-d023ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: [EMAIL="pci@0000:00:02.1"]pci@0000:00:02.1[/EMAIL]
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d0180000-d01fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: [EMAIL="pci@0000:00:1b.0"]pci@0000:00:1b.0[/EMAIL]
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:d0240000-d0243fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: [EMAIL="pci@0000:00:1c.0"]pci@0000:00:1c.0[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:44000000-441fffff memory:44200000-443fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: [EMAIL="pci@0000:00:1c.1"]pci@0000:00:1c.1[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:44400000-445fffff memory:44600000-447fffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: [EMAIL="pci@0000:00:1c.2"]pci@0000:00:1c.2[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:44800000-449fffff memory:44a00000-44bfffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: [EMAIL="pci@0000:00:1c.3"]pci@0000:00:1c.3[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:6000(size=4096) memory:44c00000-44dfffff memory:44e00000-44ffffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: [EMAIL="pci@0000:00:1d.0"]pci@0000:00:1d.0[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:50a0(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: [EMAIL="pci@0000:00:1d.1"]pci@0000:00:1d.1[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:50c0(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: [EMAIL="pci@0000:00:1d.2"]pci@0000:00:1d.2[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:50e0(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: [EMAIL="pci@0000:00:1d.3"]pci@0000:00:1d.3[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:5400(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: [EMAIL="pci@0000:00:1d.7"]pci@0000:00:1d.7[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0444000-d04443ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: [EMAIL="pci@0000:00:1e.0"]pci@0000:00:1e.0[/EMAIL]
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:7000(size=4096) memory:d0000000-d00fffff memory:40000000-43ffffff(prefetchable)
           *-network:0
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 1
                bus info: [EMAIL="pci@0000:06:01.0"]pci@0000:06:01.0[/EMAIL]
                logical name: eth0
                version: 02
                serial: 00:16:d4:68:ef:cc
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
                resources: irq:21 memory:d0000000-d0001fff
           *-network:1
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: [EMAIL="pci@0000:06:02.0"]pci@0000:06:02.0[/EMAIL]
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64
                resources: irq:22 memory:d0002000-d0003fff
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: [EMAIL="pci@0000:06:04.0"]pci@0000:06:04.0[/EMAIL]
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:d0004000-d0004fff ioport:7000(size=256) ioport:7400(size=256) memory:40000000-43ffffff(prefetchable) memory:48000000-4bffffff
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: [EMAIL="pci@0000:06:04.1"]pci@0000:06:04.1[/EMAIL]
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
                resources: memory:d0005000-d000507f
           *-generic
                description: SD Host controller
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: [EMAIL="pci@0000:06:04.2"]pci@0000:06:04.2[/EMAIL]
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32
                resources: irq:17 memory:d0005400-d00054ff
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: [EMAIL="pci@0000:06:04.3"]pci@0000:06:04.3[/EMAIL]
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
                resources: memory:d0005800-d000587f
           *-memory:2
                description: FLASH memory
                product: SD/MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: [EMAIL="pci@0000:06:04.4"]pci@0000:06:04.4[/EMAIL]
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32
                resources: irq:17 memory:d0005100-d00051ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: [EMAIL="pci@0000:00:1f.0"]pci@0000:00:1f.0[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: [EMAIL="pci@0000:00:1f.2"]pci@0000:00:1f.2[/EMAIL]
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:5440(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: [EMAIL="pci@0000:00:1f.3"]pci@0000:00:1f.3[/EMAIL]
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:5420(size=32)
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:20:92:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:25:9c:08:2c:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abgn
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by JBAlaska on 2010-08-23
Ok you have a Broadcom BCM4318 chipset.

Put the Ubuntu LiveCD in your drive and go to: **System, Administration, Software sources** and check the box below **"Installable from CDROM"**. 

Then open a terminal and do:
```
sudo apt-get update
```

Then:
```
sudo apt-get install bcmwl-kernel-source

```

Now reboot and select the **Broadcom STA driver**. in **System, Administration, Hardware Drivers**

---

### Post by 11rohrbacherk on 2010-08-23
Ok i downloaded ubuntu online and just burnt it to a disc so is that the same thing as a ubuntu livecd?

---

### Post by 11rohrbacherk on 2010-08-23
ok i did it and a bunch of errors popped up could not be resoloved, then some failed to fetch stuff...

---

### Post by 11rohrbacherk on 2010-08-23
Here is exactly what showed up:
 
 
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] sudo apt-get update
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done            
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Some index files failed to download, they have been ignored, or old ones used instead.
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,205kB of archives.
After this operation, 3,764kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3
  File not found
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main fakeroot 1.14.4-1ubuntu1
  File not found
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main patch 2.6-2ubuntu1
  File not found
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL]

---

### Post by JBAlaska on 2010-08-24
Are you sure the image of Ubuntu you downloaded is ok and the CD burned properly? And you checked the box below "Installable from CDROM"in the first part of my post.


[COLOR="Blue"]Edit:[/COLOR] **Did you download the x86_64 version of Ubuntu 10.04?**

Please post output of:
```
uname -a
```

---

### Post by 11rohrbacherk on 2010-08-24
Yes I'm almost positive i burned it right, and i checked the Below installable from cd-rom/dvd, which is next to:
**Cdrom with Ubuntu 10.04 'Lucid Lynx'**
Officially supported
Restricted copyright
 
 
then i clicked revert the box became unchecked so i just checked it again and typed the code and this came up:
 
 
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] sudo apt-get update
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done            
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Some index files failed to download, they have been ignored, or old ones used instead.
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,205kB of archives.
After this operation, 3,764kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3
  File not found
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main fakeroot 1.14.4-1ubuntu1
  File not found
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main patch 2.6-2ubuntu1
  File not found
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL]

---

### Post by JBAlaska on 2010-08-24
Ok:
The following NEW packages will be installed:
**bcmwl-kernel-source** dkms fakeroot patch

So now reboot and go to: **System, Administration, Hardware Drivers** and enable the Broadcom STA driver. You may need another reboot for the driver to enable.

Check with:
```
iwconfig
```

If all is well, you need to uncheck the installable from cdrom box (don't hit "revert" just close).

When your network is working, you can run:
```
sudo apt-get update
```

And it should work properly.

---

### Post by 11rohrbacherk on 2010-08-24
here's the output of uname -a:
 
 
Linux kyle-laptop 2.6.32-24-generic #39 Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

---

### Post by 11rohrbacherk on 2010-08-24
when i tried to activate broadcom B43 wireless driver i got a message saying:
 
Sorry, installation of this driver failed.
 
Please have a look at the log file for details: /var/log/jockey.log

---

### Post by Tekniloco on 2010-08-24
I have the same chipset.  I connected my laptop with my wired connection and ran the update through the wired connection.  After running the update I restarted the computer and then activated the hardware driver.  This worked.  However, this morning I started the laptop and now neither the wireless nor the wired connection works.  I am now researching alternative solutions.  None of the solutions I have seen in any of the forums have worked permanently so far.  If anyone else has had this problem with this chipset, please let us know what steps you have taken and if it worked or not.

---

### Post by JBAlaska on 2010-08-25
> **11rohrbacherk said:**
> when i tried to activate broadcom B43 wireless driver i got a message saying:
 
Sorry, installation of this driver failed.
 
Please have a look at the log file for details: /var/log/jockey.log

You need to choose the Broadcom STA driver, not the B43 driver.

---

### Post by 11rohrbacherk on 2010-08-25
When i go to Administration>Hardware Drivers      
the Broadcom B43 is the only thing that was there, but i just connected with a wire and installed it, But its still not working wirelessly, it says that my wireless network device is not ready.

---

### Post by 11rohrbacherk on 2010-08-25
i think one of the main problems is that when i try to update in the terminal it says:

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)

---

### Post by pinsky on 2010-09-20
> **11rohrbacherk said:**
> Yes I'm almost positive i burned it right, and i checked the Below installable from cd-rom/dvd, which is next to:
**Cdrom with Ubuntu 10.04 'Lucid Lynx'**
Officially supported
Restricted copyright
 
 
then i clicked revert the box became unchecked so i just checked it again and typed the code and this came up:
 
 
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] sudo apt-get update
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done            
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Some index files failed to download, they have been ignored, or old ones used instead.
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL] sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,205kB of archives.
After this operation, 3,764kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3
  File not found
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main fakeroot 1.14.4-1ubuntu1
  File not found
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main patch 2.6-2ubuntu1
  File not found
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[EMAIL="kyle@kyle-laptop:~$"]kyle@kyle-laptop:~$[/EMAIL]

I've solved it by clicking manually installing all the missing .deb packages, and after thet the driver could be activated. 

Just manually go to the location, and you'l find out thaet the file that is missing is actually there (on your ubuntu cd) :).
In the first case it is 

"/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb " 


After you manually install it, a different one will emerge and when you install them all, youll be able to activate the proprietary driver.

---

