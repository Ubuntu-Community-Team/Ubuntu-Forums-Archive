---
title: "Cannot acces Internet (inactive Ethernet port?)"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by rsgangr on 2009-05-14
**Background**
 I am new to Linux. Windows XP has been my operating system for some time and I need to keep it available. Being wary of data loss, I installed Ubuntu 8.04 LTS on a second drive, setting up a dual-boot system using Grub as boot loader. When I first booted into Ubuntu after setting up the dual-boot an “Updates available” (not sure of the exact wording) icon appeared and, when clicked, the update began and proceeded to completion. During that session I was able to access the Internet using Firefox and Evolution.
 

 **Problem**
 I have been unable to access the Internet ever since the first occasion mentioned above.
 

 **Hardware**
 1.7 GHz Celeron; 250 GB hdd (Windows XP); 30 GB hdd (Ubuntu 8.04 LTS); ADSL router (Billion). The network adaptor on the motherboard is a “Realtek RTL 8139/810x” and, although Ubuntu sees it, the Ethernet port is not being activated. On the router the port light remains OFF.
 

 **Attempts to understand what has happened**
 Under “Network Settings” I have tried “Enable Roaming Mode”, “Static IP address” and “Automatic configuration (DHCP)”.
 

 In Network Tools, the Network devices seen are: Loopback interface (lo), Ethernet interface (eth0) and Ethernet interface (eth0:avahi). Only the Loopback interface can be pinged successfully.
 

 It seems almost as if the Ethernet port needs to be “activated” in some way that I have yet to discover. The router is not at fault – from Windows XP it works normally.
 

 What am I doing wrong and/or what have I missed? Any assistance will be greatly appreciated.

---

### Post by aeiah on 2009-05-14
this isnt a proper solution, obviously, but from the terminal you can issue the command:
```

sudo ifup eth0

```

this should bring the interface up. you can see interface details on the commandline with 'ifconfig'.

if my network card has lost its marbles i re-associate it with the modem with 
```

sudo dhclient

```
you could see if that does anything, or at the very least tells you anything useful.

you can also check out dmesg to see if that holds any error information.


ps: i assume your network card works perfectly under windows?

---

### Post by beercz on 2009-05-14
Try:

Applications->Accessories->Terminal

Type: > sudo ifup eth0

If that fails, paste the output of the following (again in Terminal):

> sudo ifconfig eth0 in this forum.

---

### Post by rsgangr on 2009-05-15
Firstly, thank you to “aeiah” and “beercz” for quickly responding to my post with some suggestions and questions. I shall deal with them in order and add some comments at the end.
 

 **Code: “sudo ifup eth0” gave the following output:**
  rsg@rsg-Linux:~$ sudo ifup eth0  
  [sudo] password for rsg:  
  Ignoring unknown interface eth0=eth0.  
  rsg@rsg-Linux:~$  
 

 **Code: “sudo dhclient” gave the following output:**
  rsg@rsg-Linux:~$ sudo dhclient  
  Internet Systems Consortium DHCP Client V3.0.6  
  Copyright 2004-2007 Internet Systems Consortium.  
  All rights reserved.  
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)  
  

  Listening on LPF/eth0/00:0c:76:25:6e:70  
  Sending on   LPF/eth0/00:0c:76:25:6e:70  
  Sending on   Socket/fallback  
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5  
  DHCPOFFER of 192.168.1.100 from 192.168.1.254  
  DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67  
  DHCPACK of 192.168.1.100 from 192.168.1.254  
  bound to 192.168.1.100 -- renewal in 16298 seconds.  
  rsg@rsg-Linux:~$  
  

 **Does the network card work perfectly under Windows?**
 Yes – no problems have been experienced and I submitted my post via Windows XP.
 

 **Code: “sudo ifconfig eth0” gave the following output:**
  rsg@rsg-Linux:~$ sudo ifconfig eth0  
  eth0      Link encap:Ethernet  HWaddr 00:0c:76:25:6e:70   
            inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0  
            inet6 addr: fe80::20c:76ff:fe25:6e70/64 Scope:Link  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
            RX packets:119 errors:0 dropped:0 overruns:0 frame:0  
            TX packets:181 errors:0 dropped:0 overruns:0 carrier:0  
            collisions:0 txqueuelen:1000  
            RX bytes:72591 (70.8 KB)  TX bytes:24366 (23.7 KB)  
            Interrupt:11 Base address:0xe000  
  

  rsg@rsg-Linux:~$  
 

 **Further comments:**
 
[LIST=1]
[*]After trying all possible     sequences I have discovered that it is possible to boot into Ubuntu,     with an active Internet connection, _only_     if it is my initial menu choice. This means that if I have been     working in Windows XP I need to do a complete Shut Down _and     cut power to both computer and router_     at the wall socket. Then, after switching on the power again, I need     to select Ubuntu in the menu. In effect, a complete “cold start”     is needed.
[*]Whilst     trying the various sequences I noticed that Windows activates the     Ethernet port during boot-up and always deactivates it (the light     goes off) during a Restart or Shut Down. It seems, then, that my     Ubuntu installation is not doing this for whatever reason.
[*]I     have downloaded the “Ubuntu Pocket Guide and Reference” by Keir     Thomas and have just started reading it. Undoubtedly I shall know     more about Ubuntu when I have finished.
[/LIST]
Since I have found a "work-around" solution, albeit not ideal, to my lack of Internet access from within Ubuntu, it would be unfair to expect the experts to spend much time on this problem. However, I shall appreciate receiving any further suggestions on this topic. Thanks to all who took the trouble to read my post.

**2009-07-22 Closing Comment:**
For reasons I do not understand my problems have disappeared in the interim! Perhaps the regular running of "Update Manager" had something to do with it. In any event, I am now able move back-and-forth between Ubuntu and Windows XP and can access the Internet at will.

---

