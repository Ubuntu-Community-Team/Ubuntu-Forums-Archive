---
title: "Broadcom BCM4306 Rev 2 Wifi Finally WORKING!!!"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by Joe2Shoe on 2008-11-22
Wow!  I can't believe it!
I have the internal Broadcom BCM4306 rev 02 wireless wifi card in my laptop.  Never could get it working.  So, I installed a D-Link DWL-G650 AirPlus ExtremeG 802.11g Wireless PCMCIA CardBus Type II Card and Ubuntu v8.10 recognized the card and I'm online.  Great!
Under System/Administration/Hardware Drivers, I activated the listed "Broadcom B43legacy Wireless Driver", but afterwards removing the D-Link card, the Broadcom wireless would not work.
I did all the current updates as recommended, using the D-Link card.
Today, I turn the laptop back on using the D-Link card and now my "audio/speaker" icon in the top-right of the screen has turned blue and a different icon.  The "switch users or shutdown" icon has turned into a 'green man running' icon, and the "help" icon in the top-left of the screen has turned into a 'red & white life preserver" icon.
So, I went back to System/Administration/Hardware Drivers and activated the "Broadcom B43legacy Wireless Drivers" again, and then my connection showed 2 connections to my newtork SSID; one with the Broadcom card and the other with the D-Link card.
So, I remove the D-Link card, and I'm still online.
I restart the laptop and I'm still online using the internal Broadcom BCM4306 wifi card.
I can't believe it.  It finally worked.
Thanks to the Ubuntu developers for this wonderful day!
Hoorraaayyyyyyyyy!!!!!!!!!!!!!

---

### Post by Ayuthia on 2008-11-22
> **Joe2Shoe said:**
> Wow!  I can't believe it!
I have the internal Broadcom BCM4306 rev 02 wireless wifi card in my laptop.  Never could get it working.  So, I installed a D-Link DWL-G650 AirPlus ExtremeG 802.11g Wireless PCMCIA CardBus Type II Card and Ubuntu v8.10 recognized the card and I'm online.  Great!
Under System/Administration/Hardware Drivers, I activated the listed "Broadcom B43legacy Wireless Driver", but afterwards removing the D-Link card, the Broadcom wireless would not work.
I did all the current updates as recommended, using the D-Link card.
Today, I turn the laptop back on using the D-Link card and now my "audio/speaker" icon in the top-right of the screen has turned blue and a different icon.  The "switch users or shutdown" icon has turned into a 'green man running' icon, and the "help" icon in the top-left of the screen has turned into a 'red & white life preserver" icon.
So, I went back to System/Administration/Hardware Drivers and activated the "Broadcom B43legacy Wireless Drivers" again, and then my connection showed 2 connections to my newtork SSID; one with the Broadcom card and the other with the D-Link card.
So, I remove the D-Link card, and I'm still online.
I restart the laptop and I'm still online using the internal Broadcom BCM4306 wifi card.
I can't believe it.  It finally worked.
Thanks to the Ubuntu developers for this wonderful day!
Hoorraaayyyyyyyyy!!!!!!!!!!!!!

That is great to hear!  Can you provide your kernel information so that we can tell which kernel your card is using:
```
uname -a
```Thanks!

---

### Post by Joe2Shoe on 2008-11-22
kernel info

yoyo@dojo:~$ uname -a
Linux dojo 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux
yoyo@dojo:~$

---

### Post by Joe2Shoe on 2008-11-22
Strange.  The previously mentioned icons have reverted back to their original designs after rebooting.  Does Ubuntu v8.10 change icons on a regular basis?  Or was that just a reboot booger?
My Broadcom BCM4306 rev 02 is still working fine.
And my D-Link (Atheros AR5001X+) AirPlus ExtremeG Wireless PCMCIA CardBus Type-II Card is still working, also.
Good news.
Joe2Shoe.

---

### Post by Joe2Shoe on 2008-11-22
Network Adapters Info

yoyo@dojo:~$ lspci | grep Atheros
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

yoyo@dojo:~$ sudo lshw -C network
[sudo] password for yoyo: 
  *-network               
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:17
  
*-network:0
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  
*-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:67:8d:3d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  
*-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:15:e9:d8:7e:a7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  
*-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:67:45:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.11.6 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 56:e7:0e:8d:e7:b4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
yoyo@dojo:~$ 

yoyo@dojo:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
yoyo@dojo:~$

---

### Post by Joe2Shoe on 2008-11-22
I took me over a year to figure how to get my wireless working.

THIS is the most IMPORTANT step!!!!!!!!!!!!!!!

If you are using Ubuntu v8.10, you must enable all the repositories to be able to download the needed drivers.
Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

AFTER doing this, the drivers for my Broadcom BCM4306 rev. 02 wifi card were downloaded/installed, and now works!

Good luck.
Joe2Shoe.

---

### Post by greybeagle on 2008-12-19
thanks, was so excited to find your post, but somehow it still doesn't work for me. I wonder if the difference is that I also need another wifi card to "trick the system" into working...

---

### Post by bmach on 2008-12-28
> **Joe2Shoe said:**
> I took me over a year to figure how to get my wireless working.

THIS is the most IMPORTANT step!!!!!!!!!!!!!!!

If you are using Ubuntu v8.10, you must enable all the repositories to be able to download the needed drivers.
Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

AFTER doing this, the drivers for my Broadcom BCM4306 rev. 02 wifi card were downloaded/installed, and now works!

Good luck.
Joe2Shoe.

Just wanted to say a big thank you for this post. As a linux newbie I was so close to giving up and going back to Windows when I found this post. I've now got wireless working on my Asus A2800S laptop. Seriously stoked! The steps you outlined worked to a T. I downloaded all package updates before restarting at which point it picked up the driver update. But I don't think that was required.

Thanks again :popcorn:

---

### Post by hockeyshifter on 2009-11-15
[FONT="Tahoma"]***here is the lshw command*** [/FONT]

jose@jose-laptop:~$ lshw
WARNING: you should run this program as super-user.
jose-laptop               
    description: Computer
    width: 32 bitsj
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 446MiB
     *-cpu
          product: mobile AMD Athlon(tm) XP2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 1788MHz
          capacity: 1788MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up cpufreq
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
          configuration: driver=agpgart-ati latency=32 module=ati_agp
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
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon Mobility U1
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=66 mingnt=8
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2 module=snd_ali5451
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
        *-communication UNCLAIMED
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=64
        *-network:0
             description: Network controller
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=b43-pci-bridge latency=64 module=ssb
        *-pcmcia
             description: CardBus bridge
             product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
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
             configuration: driver=pata_ali latency=32 maxlatency=4 mingnt=2 module=pata_ali
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
             configuration: driver=ali1535_smbus latency=0 module=i2c_ali1535
        *-network:1
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 00
             serial: 00:0b:cd:e8:1f:49
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:cd:75:5b:69
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.106 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:c8:5a:b4:86:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
jose@jose-laptop:~$ 


[FONT="Tahoma"]***here is the Kernel ver***.[/FONT]

Linux jose-laptop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux


hope this helps 
it is working on a hp compaq pavilion ze4400 with an amd

---

