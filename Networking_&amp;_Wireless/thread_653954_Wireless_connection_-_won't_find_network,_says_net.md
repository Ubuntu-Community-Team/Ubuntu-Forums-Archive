---
title: "Wireless connection - won't find network, says network disabled"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by usone123 on 2007-12-30
OK I'm about to throw my computer out the window :).  I just loaded Ubuntu 7.10 last night on this computer and I am trying to get my Belkin wireless G USB network adapter to work.  Mod # F5D7050 version 3002

The driver is installed.  It will not find any wireless networks and you'll by my pasting below now it's saying the network is disabled.  I haven been troubleshooting this myself and with some other online forums to help me and I can't even remember half the stuff I've tried..  my network though is not the issue.  I tested that 50 different ways and it is fine and my windows laptop is connected to it 2 feet away - tried both leaving security on and off my linksys access point and talked ot linksys tech support.  its definitely not the linksys.

i intially installed the driver using ndiswrapper but i also have the windows wireless drivers in my administration menu and I know I did something to install that but can't remember what...  its been a long 2 days at this...  the network driver shows up and says the device is installed.....

a few times the network manager has shown the radio frequency bars with a 0 signal.  usually it just sits there saying no wireless networks, and when i try to connect to my network it will either time out after trying or just ask for the password everytime it wants to time out (thats while security was enabled),....

below are what i got in the terminal app.  please help.... thanks in advance

rae@LT-Destop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 90
       serial: 00:07:95:c3:d1:e5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:85:17:7e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
rae@LT-Destop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:11.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)
rae@LT-Destop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:95:C3:D1:E5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

rae@LT-Destop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rae@LT-Destop:~$

---

### Post by nizaam on 2008-01-03
I had the exact same issue, same wireless device aswell (belkin).  Oddly enough the wireless works fine on the live cd but not in the installed version.  Checked lsmod when running the livecd and installed and they pretty much matched up, same modules loaded.. etc.

This post isnt very much help for your problem other than I would like to mention that xubuntu works fine with wireless installed, i had to give up on trying to install ubuntu as I could not figure out what was causing the wireless interface to be disabled.

=T

Nick.

---

