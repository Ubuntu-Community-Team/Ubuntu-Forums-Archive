---
title: "Ubuntu 7.1 won't connect to internet through router"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by Nubers on 2008-02-12
Hi All,

I am so lost and could really use some expert help.  I have two machines, one running xp sp2 and another running ubuntu 7.1.  I want both to connect to the internet through my dsl modem and bought a new D-link router.  The XP machine connects to the internet with no problems.  The ubuntu machine does not.  

If I log in to the router it sees the ubuntu machine and assigns an ip, but the ubuntu machine just doesn't connect.

I tried the pppoeconf command from the ubuntu howto and received an error stating that there was no connection.

I cannot find any answer to what might seem like a simple problem.  I have now wasted three evenings scouring the net, this forum and any resources available to find a solution.  I do not understand networking *at all*, have grown extremely frustrated and any help would be truly truly truly appreciated.

Thanks!

Dave

---

### Post by thebof1993 on 2008-02-13
Hi,

I have the same problem and have also spend many days trying to fix it. Although my problem is different by Ubuntu and XP being on the same PC and the D-Link router able to access the internet on XP bu not Ubuntu.

Any help would be greatly apriciated!

Gra

Sorry about spelling! lol

---

### Post by gimfred on 2008-02-13
I am working through this problem too. Here is what I have done to get internet (sort of).
My setup.

[LIST=1]
[*]A NB1300+4 dsl modem router. (ip=192.168.1.1)
[*]A DLink DI-624 wireless router.(ip=192.168.0.1
[*]An integrated ethernet card. (DHCP)
[*]A DLink DWL-G520 wireless card. (DHCP)
[/LIST]

I can connect via the NB1300 wired connection flawlessly. If I connected the DI-624 to the NB1300, I could reach the DI via wireless, I could ping 192.168.1.1 but no internet.

I turned off the DI's DHCP server, and set NB's ip to be the gateway (gateway = 192.168.1.1) I changed the DI's ip to 192.168.1.2 and in put my ISP's DNS ips as my primary and secondary DNS. I rebooted everything.

I could now reach 192.168.1.1 and made sure it had a DHCP server running. 

I changed all my ips to my own designations but essentially the internet is working. The wireless drops out constantly but it is working.

---

### Post by thebof1993 on 2008-02-14
My PC is conecting to my D-Link router via a on-board ethernet cable and I can also ping my router but not any internet sites. My router has some features that you can test connectivity on  and the last three of them:
[LIST]
[*]Testing ATM OAM segment ping
[*]Testing ATM OAM end to end ping
[*]Ping Primary Domain Names Server
[/LIST]
All fail when I run them on Ubuntu but when I do the same tests on XP only the first 2 of those:
[LIST]
[*]Testing ATM OAM segment ping
[*]Testing ATM OAM end to end ping
[/LIST]
will fail. I don't knwo what these mean either apart from the last one so I am completley confussled:?

---

### Post by thebof1993 on 2008-02-15
Sorry I hate to double post but I found the solution to my problem with my router!!! All I had to do was to go onto the D-Link website and update my router drivers but typing in [http://192.168.1.1](http://192.168.1.1) and then go onto settings and firmware!!! Good luck!!

---

### Post by Webdragun on 2008-03-21
Hello All, I actually have a similar problem with a linksys router, the card sees the wireless networks but just will not connect. the driver seems to be fine, I tried an update to the router's firmware to no avail... I also noticed that the freq was defaulted to the equivalent of channel one in the config file, i even trid setting my router to channel 1 rather than 6 or 11.. still nothing.. my xp partition connects fine... just cannot get a connection in ubuntu.   please help!!  I'm pretty new at this and have been wracking my brains for almost a week now!

any assistance would be greatly appreciated.

---

### Post by Eiríkr on 2008-03-21
Let's start with some basic info gathering.  :)  Please post the results of all the following commands.
```
ifconfig
iwconfig
cat /etc/network/interfaces
sudo /etc/init.d/networking restart
```

Cheers,

Eiríkr

---

### Post by nschmitz06 on 2008-03-28
im having the same problem, i have my router firmware updated to newest available, linksys. but still no connection, my configuration is <laptop> === <router>===== <modem> here is what i get when i do those commands in terminal.

nmschm2@nmschm2-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:A0:D1:33:E3:76  
          inet addr:192.168.1.6  Bcast:192.168.15.255  Mask:255.255.240.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19494 (19.0 KB)  TX bytes:19494 (19.0 KB)

nmschm2@nmschm2-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

nmschm2@nmschm2-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth1 inet static
address 192.168.1.6
netmask 255.255.240.0
gateway 192.168.1.1

auto eth1

iface eth0 inet dhcp
wireless-essid NETGEAR

auto eth0
nmschm2@nmschm2-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
eth0: ERROR while getting interface flags: No such device
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; No such device.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
                                                                         [ OK ]
nmschm2@nmschm2-laptop:~$

---

### Post by chili555 on 2008-03-28
@Nubers> I tried the pppoeconf command from the ubuntu howto and received an error stating that there was no connection.I think you set up the router to do the PPPoE stuff, at least in my Linksys. Have you tried that? Then your Ubuntu and Windows machines should connect with no special steps.

---

