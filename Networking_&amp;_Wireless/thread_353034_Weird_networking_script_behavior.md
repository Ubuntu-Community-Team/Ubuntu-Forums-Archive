---
title: "Weird networking script behavior"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by OtonVM on 2007-02-04
Hello!

I just got ubuntu 6.10 installed and I managed to configure almost everything (I was really impressed actually) except networking that works but not as expected.
The problem is that even if /etc/init.d/networking is set as a system runlevel process and that it starts at boot, internet does not work (using pppoe configured with pppoeconf). I always have to restart networking with sudo from a terminal. Another thing is the speed of the process. I takes one minute to get everything up and I'm used to be online with pppoe and dhcp in 2sec at most on my old gentoo system... It's sort of annoying...
Anyway:
/etc/inid.d/networking restart:
```

Password:
 * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.eth0.pid with pid 3439
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:ea:31:73:e2
Sending on   LPF/eth0/00:0f:ea:31:73:e2
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:ea:31:73:e2
Sending on   LPF/eth0/00:0f:ea:31:73:e2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.4 -- renewal in 1794 seconds.    <----- This hangs for almost 1 min, also on boot
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Plugin rp-pppoe.so loaded.              <----- This also hangs for some time
                                                                         [ ok ]

```

/etc/ppp/peers/dsl-provider:
```

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "xxxxxxx"

```

/var/log/messages:
```

Feb  4 10:47:19 ubuntu-linux pppd[3530]: Connection terminated.
Feb  4 10:47:19 ubuntu-linux pppd[3530]: Terminating on signal 15
Feb  4 10:47:19 ubuntu-linux pppd[3530]: Exit.
Feb  4 10:48:05 ubuntu-linux pppd[4955]: Plugin rp-pppoe.so loaded.
Feb  4 10:48:05 ubuntu-linux pppd[4959]: pppd 2.4.4 started by root, uid 0
Feb  4 10:48:05 ubuntu-linux pppd[4959]: PPP session is 5487
Feb  4 10:48:05 ubuntu-linux pppd[4959]: Using interface ppp0
Feb  4 10:48:05 ubuntu-linux pppd[4959]: Connect: ppp0 <--> eth0
Feb  4 10:48:05 ubuntu-linux pppd[4959]: CHAP authentication succeeded
Feb  4 10:48:05 ubuntu-linux pppd[4959]: CHAP authentication succeeded
Feb  4 10:48:05 ubuntu-linux pppd[4959]: peer from calling number 00:90:1A:40:90:A7 authorized
Feb  4 10:48:05 ubuntu-linux pppd[4959]: replacing old default route to eth0 [192.168.1.1]
Feb  4 10:48:05 ubuntu-linux pppd[4959]: local  IP address 193.xxx.xxx.110
Feb  4 10:48:05 ubuntu-linux pppd[4959]: remote IP address 213.xxx.xxx.90
Feb  4 10:48:05 ubuntu-linux pppd[4959]: primary   DNS address 193.xxx.xxx.23
Feb  4 10:48:05 ubuntu-linux pppd[4959]: secondary DNS address 193.xxx.xxx.13

```

Any help will be appreciated.

Byebye!

---

### Post by gradedcheese on 2007-02-04
what does your /etc/network/interfaces look like? (edit out the pppoe password, if it's in there)

---

### Post by OtonVM on 2007-02-04
cat /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```

hmmm, suppose I can delete out all except lo, eth0 and dsl...
I also noticed something else. In the networking restart output there is mentioned a renewal of the dhcp IP. This happened some minutes ago and it took the default route over so I had to restart pppoe again. Why renewal of the IP? It's not like I removed the lan cable or something... What about another dhcp daemon? Before I always used dhcpd.

---

### Post by gradedcheese on 2007-02-04
Yeah, I would remove (comment out by putting a # in front of) the extra interfaces.  You can ensure that all dhclients are killed with:

sudo killall dhclient

before restarting networking.  My guess is that, due to the other interfaces, another dhclient runs by the time dhclient is run for eth0.  That's just a guess though.  So give this a shot: remove the extra interfaces, do the killall, and then /etc/init.d/networking restart

---

### Post by OtonVM on 2007-02-04
Ok I did that. 
The behavior of the script was similar however without other interfaces as predicted.
The killall command didn't find any process, though... Then I discovered that the command invoked is dhclient3 but there was only one and is stopped and started normally. The entire connecting thing is faster.
Now I'll first wait until the IP renewal to see if it takes the default route over and then restart to see if it connects at boot. I'll post back later.

Thank you for the help!

---

### Post by OtonVM on 2007-02-04
Ufff no change... IP was renewed and the net stopped working:
```
Feb  4 13:43:43 ubuntu-linux dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Feb  4 13:43:43 ubuntu-linux dhclient: DHCPACK from 192.168.1.1
Feb  4 13:43:43 ubuntu-linux dhclient: bound to 192.168.1.4 -- renewal in 1580 seconds.
Feb  4 14:10:03 ubuntu-linux dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
```

route -n gave me no output and if I tried to add a default route (sudo route add default ppp0):
```
SIOCADDRT: File exists
```

After restart of networking route -n gives me:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.250.19.90   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

and now I guess the story will repeat itself.

I should mention that I don't use any iptables configuration because I have a router as firewall.

Now, I searched the forum for any solution but found nothing. What needs to be done is stopping dhcpd3 from renewing the IP over and over (because it remains the same anyway) and finding a way of adding and/or setting ppp0 as default route and making that static (or I can make a script to be run on startup). I'll search google but in the mean time, if someone has any ideas...

Bye!

---

### Post by OtonVM on 2007-02-04
I found nothing. For now I made eth0 IP static so the net keeps it's default route status.
Still on boot pppd starts but I have to do ifdown ppp0 and then ifup ppp0 to be able to access the net.

I just don't get it!:mad:  I read every man on the topic and every config file for dhcp or ppp. Everything seems ok and as it was when I used ither gentoo or fedora. But it just doesn't work...

I leave this open. I'll try and make a startup script for restarting the net just before gdm starts but that's just a workaround not a real solution.

---

