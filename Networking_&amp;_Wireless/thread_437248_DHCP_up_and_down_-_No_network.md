---
title: "DHCP up and down - No network"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by guiyou65 on 2007-05-08
Hello somebody !

I've just tried Ubuntu 7.04 and it's great !

I put it on a workstation in my personal LAN, no problem.
Then I put it on my (old) laptop IBM Thinkpad A20m with a PCMCIA Xircom 10/100 ethernet card and I can't imagine what's going on !

During the install, with Alternate CD, the internet autoconfig detect and configure the connection.
After reboot, it is very weird :
The ethernet port is detected (eth0)
My Netgear router "see" the laptop for a while because I can see it in the "Attached devices" list with the right address. 
The lights on the card are flashing during the dialog.
And Ubuntu must have been connected for a while because I get the notifications for new updates and for a wired connection established.

And after that, no more connection !

The connection properties gives all values to 00 (no adress, no gateway, no dns, nothing)

How is it possible ? 

I tried with Windows, and even Fedora, without any problem.
But it is Ubuntu the system I like and I want !
I am (french) beginner with linux (even I am not bad with Windows !), so I really need help.

Below some complementaries (translate from french menu, sorry):

System/Administration/Network gives :
Wired connection with DHCP
DNS with right router adress (192.168.1.1)

System/Administration/Network tools gives :
Device: Interface ethernet eth0
	IP information window : nothing (empty)
	interface information  : everything at unknown
Device: Interface ethernet eth0:avahi
	IP information window : ipv4	169.254.6.107	255.255.0.0	169.254.255.255
	interface information : 
		hardware adress OK (MAC adress of PCMCIA card)
		Multicast activated.


But when I try to click on the Configure button, the answer is : interface does not exist !


I list following commands :

~:~$ ifconfig -v
eth0      Lien encap:Ethernet  HWaddr 00:80:C7:A1:0C:75  
          adr inet6: fe80::280:c7ff:fea1:c75/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:17241 (16.8 KiB)
          Interruption:3 Adresse de base:0x300 

eth0:avah Lien encap:Ethernet  HWaddr 00:80:C7:A1:0C:75  
          inet adr:169.254.6.107  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interruption:3 Adresse de base:0x300 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hote
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:46 erreurs:0 :0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:3973 (3.8 KiB) Octets transmis:3973 (3.8 KiB)

~:~$ 
~:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 5620
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:80:c7:a1:0c:75
Sending on   LPF/eth0/00:80:c7:a1:0c:75
Sending on   Socket/fallback
~:~$ 
~:~$ ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
~:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:80:c7:a1:0c:75
Sending on   LPF/eth0/00:80:c7:a1:0c:75
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
~:~$ 

At this time I get the notification popup : You are now connected to a wired network

Then I try again :

~:~$ ifconfig -v
eth0      Lien encap:Ethernet  HWaddr 00:80:C7:A1:0C:75  
          adr inet6: fe80::280:c7ff:fea1:c75/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:24600 (24.0 KiB)
          Interruption:3 Adresse de base:0x300 

eth0:avah Lien encap:Ethernet  HWaddr 00:80:C7:A1:0C:75  
          inet adr:169.254.6.107  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interruption:3 Adresse de base:0x300 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hote
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:54 erreurs:0 :0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:4650 (4.5 KiB) Octets transmis:4650 (4.5 KiB)

Please help me !

---

### Post by spd106 on 2007-05-10
For some reason DHCP is not working, this means that avahi-autoip is kicking in and confusing the issue.

All I can say is perhaps try disabling roaming mode and set a static address configuration instead.

Could you please post the some information about the network card, the output of these commands would be useful.
```
lspci
```
```
sudo lshw -class network
```

---

### Post by guiyou65 on 2007-05-26
Well, problem solved with 25 &#8364; for a new ethernet card !
The problem was :
no connection after boot, but if you are patient, a few hours later, the connection is active !
I gave up and buy a recent model pcmcia card, and it is OK.
I tested a lot of distros, and the problem is the same with all distros and kernel upper than 2.6.18.

---

