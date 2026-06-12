---
title: "DHCP is fine but static IP won't allow gateway to be added"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by ryukent on 2008-02-08
Hi all, just wandered if anyone could shed any light.

Since I've installed gutsy, I can only connect to my router via DCHP. When I I try to set a static ip address, it connects fine, but won't add the gateway.

For example I get:

sudo route -v add default gw 192.168.0.1
SIOCADDRT: No such process

So although I can connect to my router, I can't get out onto the internet. Works fine in roaming mode, but I have static routing set up on my router, so I need to fix the ip.

I'm using an intel pro wireless 3945 btw.

Any help would be much appreciated.

Cheers

---

### Post by jeffus_il on 2008-02-08
The man page of route states:
>        route add default gw mango-gw
              adds  a  default route (which will be used if no other route matches).  All packets using this route will be
              gatewayed through "mango-gw". The device which will actually be used for that route depends on  how  we  can
              reach "mango-gw" - the static route to "mango-gw" will have to be set up before.
the static route needs to be added first, using something similar to:
```
route add -net 192.56.76.0 netmask 255.255.255.0 dev eth0
```

Did you try manually setting up using the "Network" on the system menu?

---

### Post by jeffus_il on 2008-02-08
The solution is here:
[http://ubuntuforums.org/showthread.php?t=575512](http://ubuntuforums.org/showthread.php?t=575512)

---

### Post by ryukent on 2008-02-08
Thanks for your interest, but that thread doesn't have a solution. It just says use DHCP.... but I've already established it works with DHCP assigned IP. I want to set a static ip.

When I run route now I get:

[FONT="Courier New"]]ryu@ryu-laptop:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth1[/FONT]

But I can't get that gateway up with static ip on. Even though I quite clearly put it in the box under network manager, it won't add as the gateway.

any thoughts?

---

### Post by ryukent on 2008-02-08
OK, there's an update to this problem:

With my etc/network/interfaces set to:

> auto lo
iface lo inet loopback

iface eth1 inet dhcp
address 192.168.1.82
netmask 255.255.255.0
gateway 192.168.0.1
dns-sameservers 192.168.0.1
wpa-psk **************
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid ***********

auto eth1

I can restart network fine:

ryu@ryu-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 6379
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:de:80:bf:e0
Sending on   LPF/eth1/00:18:de:80:bf:e0
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.3 -- renewal in 110890 seconds.
                                                                         [ OK ]

But, when the above file reads:

iface eth1 inet static

I get:

ryu@ryu-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          SIOCADDRT: No such process
Failed to bring up eth1.
                                                                         [ OK ]

What could be causing this?

---

### Post by ryukent on 2008-02-08
Never did get this to work with the default network manager, but installing WICD seemed to solve the problem. Shame the built in network manager doesn't work.

In case anyone else is having the same problem. I've written a quick guide on installing WICD:

[https://help.ubuntu.com/community/WICD]("https://help.ubuntu.com/community/WICD")

---

### Post by jeffus_il on 2008-02-09
I did the same once and had to remove the dhcp program used by network manager "dhcdbd" and install another dhcp client,  "dhcp3-client".

---

