---
title: "I dont have network and internet connection after installing Ubuntu"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by deansamson1985 on 2008-09-08
I just installed Ubuntu on my desktop,
having it as dual boot,
I've been searching for answers here in the forum...
will someone help me out?

---

### Post by newtubunix on 2008-09-08
Is it a wireless or wired connection?

---

### Post by regala on 2008-09-08
> **deansamson1985 said:**
> I just installed Ubuntu on my desktop,
having it as dual boot,
I've been searching for answers here in the forum...
will someone help me out?

Could you at least be more specific ?
Hardware specification, Ubuntu release you used, what is "no network" ?
People here are, obviously, willing to help anyone; but there are some things one cannot guess.

---

### Post by deansamson1985 on 2008-09-08
> **newtubunix said:**
> Is it a wireless or wired connection?

The router is wireless but I want to use wired on my desktop,

---

### Post by deansamson1985 on 2008-09-08
> **regala said:**
> Could you at least be more specific ?
Hardware specification, Ubuntu release you used, what is "no network" ?
People here are, obviously, willing to help anyone; but there are some things one cannot guess.

my interface/logical name is eth0
sis190

Ubuntu 8.04

---

### Post by deansamson1985 on 2008-09-08
*-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:16:7f:36
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full latency=0 link=no module=sis190 multicast=yes port=MII speed=100MB/s

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1e:8c:16:7f:36
Sending on   LPF/eth0/00:1e:8c:16:7f:36
Sending on   Socket/fallback

this are the details I've got....

---

### Post by tbehrens on 2008-09-09
> If you're having problems in Synaptic or Firefox, if you're a newbie like me, here's the process at it's most basic:

ipv6 is a protocol not handled by many routers. It's new and will be needed someday (which means a long time from now (like years) you're gonna have to buy a new one. In the meantime, config linux not to use it by:

1. Open a Terminal Window
2. Type sudo gedit /etc/modprobe.d/blacklist
3. In the gedit window at the end of the file, type: blacklist ipv6
4. Save the file and reboot.

To make sure you no longer have ipv6 running, open a terminal window and type:
ip a | grep inet6

Many thanks to mhael for this process!

I found this to be particularly useful when network issues plagued me.

---

### Post by deansamson1985 on 2008-09-10
I cant edit blacklist :(
even if im using sudo

---

