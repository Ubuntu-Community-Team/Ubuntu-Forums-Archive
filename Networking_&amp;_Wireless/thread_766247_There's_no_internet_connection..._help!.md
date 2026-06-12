---
title: "There's no internet connection... help!"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by gigio6 on 2008-04-25
A week ago I installed Ubuntu for the first time. I was surprised: I had to find no drivers, all went OK. In fact I turned off the pc, but when I turned it on again, there was no connection! I've read that, if I use the ethernet port, I have nothing to do, I haven't to set anything! 
I'm speaking of Ubuntu 7.10.
Yesterday I decided to reinstall everything (also my windows partition in which I had the internet connection without problems), so I tryed to surf the net and all was Ok. Now, I haven't an internet connection again.
These are the settings now on my ubuntu:

luigi@Luigi-desktop:~$ ifconfig eth0 
eth0 Link encap:Ethernet HWaddr 00:C0:CA:34:1D:C1 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) 
Interrupt:12 Base address:0xd000 

luigi@Luigi-desktop:~$ ifconfig eth1 
eth1: error fetching interface information: Device not found 

What can I do now? Should I try to install the new version?
There's a possibility to set manually the connection?
Help!!!!

---

### Post by hessiess on 2008-04-25
Im also having a problem with wired internet not working, though in 8.04. I dont know what the problem is..

---

### Post by superprash2003 on 2008-04-25
go to system->administration->network and choose wired connection(eth0) and click on properties.then select automatic configuration(DHCP) or enter ip manually and then try

---

