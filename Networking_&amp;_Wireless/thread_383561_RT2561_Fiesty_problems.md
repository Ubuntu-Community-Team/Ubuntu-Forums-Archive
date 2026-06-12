---
title: "RT2561 Fiesty problems"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by dun4d on 2007-03-13
Hey
I'm on Feisty Herd 5 and have a RT2561 with the RT61 driver. It shows all the wireless networks but will not connect to any (open or locked). Any help?
Thanks

---

### Post by winter7 on 2007-03-13
ditto here... must be a bug somewhere.

-Dino

---

### Post by rjpilla on 2007-03-14
Loss my RT2500 on latest upgrade. Got it working by removing the network manager using synaptic.

---

### Post by sirbats on 2007-04-08
> **rjpilla said:**
> Loss my RT2500 on latest upgrade. Got it working by removing the network manager using synaptic.

Hi All,
I have the same problem. I have RT61 card and RT61 driver is installed by default on feisty-beta 7.04. but can not connect to router. My solutions as follows :

please test your RT61 card by

```
 
$ sudo dhclient ra1 (on my pc the RT61 card detected as ra1) sts@opotumon:~$ sudo dhclient ra1
Password:
Internet Software Consortium DHCP Client 2.0pl5
Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
All rights reserved.

Please contribute if you find this software useful.
For info, please visit http://www.isc.org/dhcp-contrib.html

Listening on LPF/ra1/00:16:b6:99:73:c9
Sending on   LPF/ra1/00:16:b6:99:73:c9
Sending on   Socket/fallback/fallback-net
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.1.234
DHCPREQUEST on ra1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.234
SIOCADDRT: File exists
bound to 192.168.1.109 -- renewal in 43200 seconds.
sts@opotumon:~$ 


```

then do as follows :

```
 system > administration > synaptic package manager : choose install dhclient : it's will affected to UNINTSTALL " Network manager" and "gnome Nertwork Manager" which actually native in KDE (I used gnome desktop manager" and " dhclient3 - just go ahead. 
```

then reboot : I opened browser and connected to internet. 
To have metwork monitor please do as follows :

```
 right click upper pannel > add to panel > click "Network Monitor" > add to panel = you will have Network Monitor with wireless indicator 
```

I dont make any encryption to connect router.

have a nice surfing

---

### Post by derelict888 on 2007-08-22
I have the RT2561 and Ubuntu 7.04, and followed the instructions in the previous post. It also worked for me. I ran the "sudo dhclient ra1" and then uninstalled "network monitor" and "gnome network monitor", rebooted and viola. I can't change networks very easily but by adding the network monitor panel I can still see my signal strength, etc... Thanks for the info!
:popcorn:

---

