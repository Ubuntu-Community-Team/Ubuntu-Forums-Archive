---
title: "another bcm 4318 thread...."
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by namsiuH on 2007-07-06
Yes I know there are tons of threads about this, but most of them are (as far as I can tell) outdated, or I just end up feeling dumb. 

After the hard drive of my dear laptop (acer aspire 3003LMi) named Sophia failed and I had to buy a new one, I decided I would like to try out linux. I knew someone who used linux and I asked which distro he recommended and here I am. Since I had to wait for my new hard drive to arrive I used the live-boot for a while. I was quite disappointed to find out that the wireless network didn't work. When the drive arrived I installed Ubuntu (feisty) and everything went fine. I decided to check the ubuntu-site + forums + google for help with my wireless. And soon I found out that my wireless card was well...pretty hopeless. 

I followed the steps in the _[Wireless Troubleshooting Guide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)_  and when I used the " sudo lswh"  I got :

> =192
             resources: iomemory:38020000-38020fff irq:16
          *-network:1 DISABLED
             description: Wireless interface
             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: b
             bus info: pci@00:0b.0
             logical name: eth1
             version: 02
             serial: 00:14:a4:6f:b6:83
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:e2000000-e2001fff irq:22


The guide told me to check out the laptoptestingteam, google or the forums. The first two only got me an owner of the same laptop with the same problem without solution so I decided to hit the forums.  Now my only hope is the community....

Any help would be nice; links to places, instructions, etc etc. As you might have guessed I'm a pretty big n00b when it comes to linux. So step-by-step instructions would be really appreciated. 

additional information that I saw some people post in their threads:

iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwlist
> Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event


lspci
>  00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


signed, namsiuH

---

### Post by Antonio44 on 2007-07-06
Try this it worked for me.


[http://doc.gwos.org/index.php/BradcommBCM4318](http://doc.gwos.org/index.php/BradcommBCM4318)


A.

---

### Post by namsiuH on 2007-07-06
You're awesome!! That was freaking easy. I'll e-mail the guy with the same laptop right away.

Thanks!!!! 

Now I'm going to watch some vampires get slain.

Signed, namsiuH

---

### Post by ksieg on 2007-07-06
> **Antonio44 said:**
> Try this it worked for me.


[http://doc.gwos.org/index.php/BradcommBCM4318](http://doc.gwos.org/index.php/BradcommBCM4318)


A.This link doesn't work for me.  Takes me to a page with a redirect link.  Any suggestions?

---

### Post by namsiuH on 2007-07-07
It was working just fine last night, but it appears someone edited the page. If you go to history (same place as in wikipedia) you can compare 2 versions. Just take the upper 2 and compare. On the left you'll see the page as it's supposed to be. I'm not sure whether you can make it work with that way but you could give it a try. And maybe someone can change it back the was it's supposed to be. 

Signed, namsiuH

EDIT:
This should work even better: [http://doc.gwos.org/index.php?title=BradcommBCM4318&oldid=16972](http://doc.gwos.org/index.php?title=BradcommBCM4318&oldid=16972)

---

