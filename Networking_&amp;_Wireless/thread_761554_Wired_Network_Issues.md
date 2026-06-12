---
title: "Wired Network Issues"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by rheywood on 2008-04-21
Hello,

I'm currently having a rather strange problem regarding connecting to the internet on Ubuntu via a wired connection. I've been running 7.10 since October without any problems, and then a few days ago it stopped working. Nothing major had occured, I'd simply gone briefly onto Windows XP, then returned. 

Last night I decided to upgrade to the latest RC of 8.04 since I presumed 7.10 had problems for it, even though I'd used it for the last 6 months. However, this does not work either, and will not load any sites. I have looked around on the forum, but nothing seems to address this issue.

The network tools is automatically selected for loopback, and yet when I try eth0 for Ethernet, it says the interface cannot be found. 

Sorry that there is no technical output - please advise as to what is needed to help on this very strange issue!

Thanks in advance!

---

### Post by timcredible on 2008-04-21
well, if it had been working ok for months, then something changed (you booted into windows), and now it doesn't work, basic troubleshooting says it's a 99% chance the thing that changed caused the problem.  you'll want to check to see what windows did while you were running it.  it seems odd that windows would mess up a nic, but i have seen times when windows sent a nic a command and the nic remembered it on next boot.

---

### Post by rheywood on 2008-04-21
The thing is, I didn't use the internet whilst I switched over. I only used printing, which I've used before and not caused a problem. Also, I have booted into Windows many times to use the net [e.g. restricted video players], and never had a problem...

---

### Post by rheywood on 2008-04-25
OK, I've been trying to fix this for a few days now. I've reinstalled my entire system, but to no avail.

Whenever I open Network Tools, two interfaces are shown: Loopback interface (lo) then Ethernet interface (eth0). I try and press 'Configure' but I am greeted with the following message:
> The interface does not exist
Check that it is correctly typed and that it is correctly supported by your system.

Here is the output of lspci:
> richard@richard-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

ifconfig:
> richard@richard-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:05:d4:39:34  
          inet addr:172.20.23.254  Bcast:172.20.23.255  Mask:255.255.255.252
          inet6 addr: fe80::230:5ff:fed4:3934/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:235126 (229.6 KB)  TX bytes:6812 (6.6 KB)
          Interrupt:16 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:960 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48000 (46.8 KB)  TX bytes:48000 (46.8 KB)


Finally, a post on the forum suggested trying
sudo ifup eth0, however I get this message:
Ignoring unknown interface eth0=eth0.

Does anybody have any idea what this could be? It's driving me crazy!

Cheers for any advice!

---

### Post by Jamie Jackson on 2008-04-26
> **rheywood said:**
> OK, I've been trying to fix this for a few days now. I've reinstalled my entire system, but to no avail.

Whenever I open Network Tools, two interfaces are shown: Loopback interface (lo) then Ethernet interface (eth0). I try and press 'Configure' but I am greeted with the following message:


Here is the output of lspci:


ifconfig:


Finally, a post on the forum suggested trying
sudo ifup eth0, however I get this message:
Ignoring unknown interface eth0=eth0.

Does anybody have any idea what this could be? It's driving me crazy!

Cheers for any advice!

This could be a total red herring, but I have heard of Windows Update updating a device's firmware, with the undesired consequence of rendering the device inoperable in Linux.

If my crazy suspicion sounds not so crazy, it might be possible to downgrade the firmware.

Again, I'm not claiming this is the problem, it's just the first thing that popped to mind when reading the clues.

---

### Post by rheywood on 2008-04-26
Cheers for the attempt - I've tried searching to change the firmware, doesn't seem as though I'm able to. The nearest I've got is rolling back to older drivers on Windows, although that hasn't made any difference.

Here are the results of ifup/ifdown for eth0 if these are of any use to somebody!

> richard@richard-desktop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 6648
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:30:05:d4:39:34
Sending on   LPF/eth0/00:30:05:d4:39:34
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 172.20.253.13 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

> richard@richard-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:30:05:d4:39:34
Sending on   LPF/eth0/00:30:05:d4:39:34
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 172.20.23.254 from 172.20.253.13
DHCPREQUEST of 172.20.23.254 on eth0 to 255.255.255.255 port 67
DHCPACK of 172.20.23.254 from 172.20.253.13
SIOCADDRT: No such process
bound to 172.20.23.254 -- renewal in 263407 seconds.

---

