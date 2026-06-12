---
title: "unable to connect to home wireless via command line using Linksys Wireless-G WPC54GS"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by rockerphil on 2009-11-08
ok, the title pretty well says it all but here's a quick rundown. i recently got my hands on an older IBM Thinkpad that's running 128 MB of RAM and (i think) a 850 MHz Intel Pentium III processor. since the resources are pretty limited i did what i normally do with a machine this old and built the OS from the command line up using the Ubuntu 8.04 minimal iso then using Fluxbox as the WM, idesk and feh for desktop icon rendering and several other lightweight apps to round off the OS. now down to the task at hand. the laptop doesn't come with an internal wireless card so i put an old Linksys Wireless-G  WPC54GS bus card i had in it. both lights on the card light up, and it shows up when i run an lspci.

```
gerald@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
07:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

as Broadcom Corporation BCM4306. and it shows up when i run an ifconfig

```
gerald@ubuntu:~$ sudo ifconfig
[sudo] password for gerald: 
eth0      Link encap:Ethernet  HWaddr 00:d0:59:33:df:31  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe33:df31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19667106 (18.7 MB)  TX bytes:1448962 (1.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10708 (10.4 KB)  TX bytes:10708 (10.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:20:2a:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-20-2A-46-00-00-00-00-00-00-00-00-00
-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

 
since the system resources are pretty limited i'm using this tutorial

[http://blog.tplus1.com/index.php/2008/06/13/how-to-connect-to-a-wireless-network-from-the-ubuntu-command-line/](http://blog.tplus1.com/index.php/2008/06/13/how-to-connect-to-a-wireless-network-from-the-ubuntu-command-line/)

to try and connect to my home wireless network. i can successfully get the interface up using ```
sudo ifconfig wlan0 up
``` and i get no error messages when i run ```
sudo iwconfig wlan0 Phillip
``` and of course punching in my network pass phrase. but when i try to obtain an IP from the router using dhclient this is what i get

```
gerald@ubuntu:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5959
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:20:2a:46
Sending on   LPF/wlan0/00:12:17:20:2a:46
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

i can't seem to figure out what to do from here even after googling it for several hours, so i'm kicking it over to you guys. if any more information is needed please feel free to ask. any help is greatly appreciated, and much thanks in advance,

Phil

---

### Post by rockerphil on 2009-11-08
anyone?

---

### Post by cariboo on 2009-11-08
Is the proper driver loaded? Open a terminal and type:

```
sudo lshw -C network
```

Please paste the output in your next post.

---

### Post by rockerphil on 2009-11-08
thanks for the response cariboo, and here's the output of the command you requested. everything seems to be in order, but i could be wrong.

```
gerald@ubuntu:~$ sudo lshw -C network
[sudo] password for gerald: 
  *-network               
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 1
       resources: irq:11
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 41
       serial: 00:d0:59:33:df:31
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-f
d 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion
=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=66 link=yes max
latency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:07:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:20:2a:46
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

---

### Post by rockerphil on 2009-11-08
still lookin for some help here. much thanks to everyone that helps

---

### Post by rockerphil on 2009-11-08
anyone? i'm still pounding my head against a wall in between Google searches

---

### Post by Rayve on 2009-11-08
(Going from 9.04 netbook experience here) Do you see the blue bars at the top where the network icon is?  I was trying to connect to a wifi hotspot today and it "sudo dhclient wlan0" would only work once the blue had stopped swirling and turned into bars.  I had to be sure that "enable for all users" was on, and turn off the "automatically connect" option for my regular Home network.  once I got the bars, I was able to "sudo dhclient wlan0" successfully, before that, all I got were the gateway DHCPDISCOVER lines.

Good luck!

---

### Post by rockerphil on 2009-11-09
Rayve, i appreciate the help for a normal DE, but i'm running a Desktop Environment that's custom built from the command line up, so i have no type of graphical network manager. my network interfaces are either auto-configured or manually configured via the command line, there is no in between. but if anyone else is reading this i appreciate any other help. much thanks in advance,

Phil

---

### Post by Rayve on 2009-11-09
> **rockerphil said:**
> Rayve, i appreciate the help for a normal DE, but i'm running a Desktop Environment that's custom built from the command line up, so i have no type of graphical network manager. my network interfaces are either auto-configured or manually configured via the command line, there is no in between. but if anyone else is reading this i appreciate any other help. much thanks in advance,

Phil

Ohh, I see!  Sorry about that.  I don't have anything first-hand then, but I can't sleep so thought I'd try some research.  I'm sure you've googled away already, but maybe something here can help? 

Here is a(n extensive) troubleshooter that says it's command line only, no gui, and seems to have steps for whatever security conditions you may have on your router - [http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

A very old forum post suggests dmesg may show an issue with ipv4 vs ipv6 - [http://ubuntuforums.org/archive/index.php/t-222010.html](http://ubuntuforums.org/archive/index.php/t-222010.html)

For Broadcom (on Hardy, but looks like others have used it too, mainly involves ndiswrapper but is all command line) [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Apologies if you've seen this already, I'll step back and let someone more expert than I reply.  :)

---

