---
title: "ethernet not connecting to router"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by godwine on 2008-10-17
I'm new to Linux and I really need some help after two frustrating weeks (50+ hours) of trying to get Ubuntu 8.04 to connect to the internet. My dual-boot PC connects to the internet on broadband in Windows XP OK and Ubuntu lights my BT Voyager 220v Ethernet LED for 15 seconds during boot-up - so there's nothing wrong with the hardware. I've re-installed Ubuntu for the third time and this time I've left everything in default mode; the router has DHCP enabled and Network Settings are in roaming mode.

Please check out what I think are the relevant listings and put me right if you can.


lspci -nn
00:07.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)


lshw -C network
 *-network               
       description: Ethernet interface
       product: DECchip 21142/43
       vendor: Digital Equipment Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: 41
       serial: 00:10:83:f7:b3:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical

       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=40 mingnt=20 module=tulip multicast=yes

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:83:f7:b3:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc800 

eth0:avahi Link encap:Ethernet  HWaddr 00:10:83:f7:b3:f7  
          inet addr:169.254.11.155  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82400 (80.4 KB)  TX bytes:82400 (80.4 KB)


cat /etc/network/interfaces
auto lo
iface lo inet loopback


dmesg
[   17.854297] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   17.854376] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 18 (level, low) -> IRQ 16
[   17.870152] tulip0:  EEPROM default media type Autosense.
[   17.870156] tulip0:  Index #0 - Media MII (#11) described by a 21142 MII PHY (3) block.
[   17.870159] tulip0:  Index #1 - Media 10base2 (#1) described by a 21142 Serial PHY (2) block.
[   17.870162] tulip0:  Index #2 - Media AUI (#2) described by a 21142 Serial PHY (2) block.
[   17.872174] tulip0:  MII transceiver #1 config 3100 status 7849 advertising 0101.
[   17.872176] tulip0:  Advertising 01e1 on PHY 1, previously advertising 0101.
[   17.941856] SCSI subsystem initialized
[   17.957629] eth0: Digital DS21142/43 Tulip rev 65 at Port 0xc800, 00:10:83:f7:b3:f7, IRQ 16.


cat /etc/resolv.conf
(nothing)

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

sudo ethtool eth0
Settings for eth0:
No data available

sudo dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:10:83:f7:b3:f7
Sending on   LPF/eth0/00:10:83:f7:b3:f7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6




If anything else is needed just let me know - I'll be most grateful.

---

### Post by fwre01 on 2008-10-17
I'v read other posts of people experiencing problems with this chipset. Maybe try using a different distro on a live CD, see if the nic works and then see what driver version its using? I can see at the moment you are using "driver=tulip driverversion=1.1.15"

---

### Post by godwine on 2008-10-17
Thanks fwre01, I installed openSUSE 11.0 last week because I understood that it configures networks more easily. I played around with SUSE Network Manager for a short while after the automatic installation stage without any luck. So I'll go back and use the live-CD and try out your suggestion.

My network card is actually an HP Ethernet card with an Adaptec ANA-6911A chip posing as a DEC 21142/3; a Tulip driver is used - no wonder its confused!

---

### Post by godwine on 2008-10-18
I give up.

I'm a newbie to Linux and I've spent over 50 hours simply trying hook my PC AMD XP3200+ via USB or by ethernet through a ANA-6911 (DEC21142/3) chip to a BT Voyager 220v BCM6348 chip.

When I first installed Ubuntu 8.04 and couldn't connect to the net I was first misled by eth0:avahi in Network Tools then by dynamic/static IP and DHCP, tried pppoeconf (but we're pppoa in UK), manual network configuration, checked over my /var/log/syslog, then I came across a possible NM bug and installed WICD, tried different distros and re-installation of an older Ubuntu, tried a manual USB networking configuration - and so on. When I ended up trying download ANA6911A/DEC21142/3 chip drivers for ethernet and BCM6348KPBG driver for USB and reading SourceForge pages on Linux kernels I realised I've spent too much time to justify the benefits. After all, this hardware has run my Windows XP for 5 years and never bothered me.....

I think the problem lies with the current Ubuntu 8.04 driver for the DEC21142/3 and I couldn't install an old_tulip driver. When I took the USB route I couldn't find the VID1/2 PID1/2 settings for the BCM6348 in order to do a sudo /usr/bin/eciadsl-config-tk.

I give up.

---

### Post by Rocktman2 on 2008-10-18
This isn't exactly like your problem, but you never know what triggers a resolution. I dual-boot Window$ & Ubuntu. I had originally installed 6.06LTS then through on-line upgrades was at 7.10. At that time, I installed a second NIC while in Window$. One for the Internet, one for the internal network.

In Window$, both NICs worked perfectly; when I booted in Ubuntu, neither NIC worked. I was able to manually get them to work.

Then when 8.04 was offered as an on-line upgrade, I did the upgrade to 8.04(.1?) hoping the NICs would be resolved. Upon the restart, neither NIC was working. They had to have been working with 7.10 otherwise I wouldn't have been able to do the on-line upgrade (& yes, they work upon booting into Windoze).

One NIC is an Intel Pro/100 VE onboard NIC; the other is a Sohoware 10/100 PCI NIC. The Intel was my original NIC when I installed 6.06 LTS from CD. 

After several weeks of mulling over the situation, I ordered the 8.04 CD to try it live to see if my NICs would work. At least 1 did, so for the time being, that was good enough.

I decided to bite the bullet & do a clean install since Ubuntu is installed on a separate disk from my Window$. I thought I would just be able to pop in the CD & click install, but even that didn't work. The 8.04 install failed. Since I didn't have anything on the Ubuntu disk I needed, I deleted all the partitions & started over. This time the install went smoothly.

When all was said & done, both NICs appear installed & working. 

A reply I got to my post on another forum about this issue was,
"Well, there appears to be some sort of issue with 8.04 and NICs. I have two computers that have the same NIC, only one runs 32 bit and the other 64 bit. For some reason, the 64 bit came out alright but the 32 bit does not seem to be capable of handling the NIC. I ended up compiling the driver from source... I did a fresh install instead of an upgrade, by the way."

Again, not exactly the same as you, but...

Sorry I couldn't be of more help.

---

### Post by godwine on 2008-10-26
PROBLEM RESOLVED

I purchased a new PC and, rather than use the pre-installed Vista, I've installed Ubuntu64. It recognized the ethernet card and hooked up to the net straightaway. However it took three resets to recognize my LG 22" monitor but I am prepared to get to grips with the various aspects of Ubuntu and will give it a lengthy tryout. I look forward to exploring the new world of Ubuntu. Thanks.

---

### Post by godwine on 2008-10-30
My experience with Ubuntu started exactly one month ago. I think I've given it a fair try but after failing to get my ethernet card installed on my old PC and having videocard driver glitches, video-to-DVD difficulties and TV setup failures on my new PC I have succumbed to Vista. 

I'll probably have another go with Linux sometime; but not now.

---

