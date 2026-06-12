---
title: "KNetworkManager won't even start"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by hydrotemplar on 2008-02-24
So I just installed Kubuntu, and I've been trying to get my internet working.  It recognizes that eth0 is connected, but nothing will work in my browser.
I think the answer may have to do with KNetworkManager, but the program won't open.  When I try to open it from the K-Menu it does nothing.  It hasn't done anything from when I first installed Kubuntu.
I've tried reinstalling, but it still does nothing.
Anybody have any clue how to get this to work?

---

### Post by sireebob on 2008-04-17
... oh! I was about to say I have the same problem, but I found out that my panel's system tray wasn't added for some reason. I actually had Mint installed previously, but I have a separate /home partition so I left that alone when I installed Kubuntu 8.04 Beta. That might have something to do with it.

Anyway, to get the system tray, right-click the panel (go to Panel Menu if necessary) and click Add Applet to Panel. Find the System Tray, and add it. Then if you need to you can move it over near the clock.

I hope that helps you.

---

### Post by cmnorton on 2008-05-06
If you enter the command sudo dhclient, does your network come back?

There is a bug for this problem: [https://bugs.launchpad.net/bugs/193964](https://bugs.launchpad.net/bugs/193964)

---

### Post by dmodmodmo@gmail.com on 2008-05-09
> **cmnorton said:**
> If you enter the command sudo dhclient, does your network come back?

There is a bug for this problem: [https://bugs.launchpad.net/bugs/193964](https://bugs.launchpad.net/bugs/193964)


Yes and here is what I get

aveo@daveo-workstation:~$ sudo dhclient
[sudo] password for daveo:
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:55:3f:19:f5
Sending on   LPF/eth0/00:02:55:3f:19:f5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 136.167.25.71 from 136.167.24.1
DHCPREQUEST of 136.167.25.71 on eth0 to 255.255.255.255 port 67
DHCPACK of 136.167.25.71 from 136.167.24.1
bound to 136.167.25.71 -- renewal in 36742 seconds.
daveo@daveo-workstation:~$

---

### Post by dmodmodmo@gmail.com on 2008-05-09
> **sireebob said:**
> ... oh! I was about to say I have the same problem, but I found out that my panel's system tray wasn't added for some reason. I actually had Mint installed previously, but I have a separate /home partition so I left that alone when I installed Kubuntu 8.04 Beta. That might have something to do with it.

Anyway, to get the system tray, right-click the panel (go to Panel Menu if necessary) and click Add Applet to Panel. Find the System Tray, and add it. Then if you need to you can move it over near the clock.

I hope that helps you.

I can add it the the system tray but when I click on it nothing happens

---

