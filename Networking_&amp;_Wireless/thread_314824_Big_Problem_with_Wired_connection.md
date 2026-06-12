---
title: "Big Problem with Wired connection"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by SebbeJohan on 2006-12-08
I guess this is the right thread.

Hi,

I really need some help to fix my connection!!!!!!! Super newbie here!

I have this problem with my wired connection (eth0). This connection disappears often and I can't seem to be able to connect. This occurs every time I go to Uni and connect on the Wifi. As soon as I get home and plug my wired connection, nothing happens. The green light is not even blinking. I tried on the laptop on a friend and it works perfectly After a couple of hours, I plug in my cable, the green light blinks and Internet begin to work. However it usually doesnt last long, and the connection disappear again...
I have installed network-manager but it didn't seem to help so I uninstalled it for network selector, which doesn't help either.
Is there a conflict somewhere? I really don't know what to do.

My /etc/network/interfaces looks like that:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


My ifconfig gives the following (I'm on the Wifi at Uni)

eth0 Link encap:Ethernet HWaddr 00:C0:9F:50B:2E
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:6

eth1 Link encap:Ethernet HWaddr 00:0E:35:29:60:68
inet addr:130.236.66.50 Bcast:130.236.67.255 Mask:255.255.254.0
inet6 addr: fe80::20e:35ff:fe29:6068/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:74655 errors:0 dropped:0 overruns:0 frame:0
TX packets:8469 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:15063194 (14.3 MiB) TX bytes:1096025 (1.0 MiB)
Interrupt:10 Base address:0x6000 Memory:d0208000-d0208fff

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2443 errors:0 dropped:0 overruns:0 frame:0
TX packets:2443 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:157198 (153.5 KiB) TX bytes:157198 (153.5 KiB)


Can someone help me with this? What other information is needed? My connection is a 100mb with no modem (or at leat I can't see it, I plug in my cable directly into a small box in the wall)

Thanks in advance

---

### Post by endersshadow on 2006-12-08
When you plug it back in, do:

```
sudo ifdown eth0
sudo ifup eth0
```

If that doesn't connect:
```
sudo dhclient
```

Should work after that.

---

### Post by SebbeJohan on 2006-12-08
Thanks for your reply!

It still doesn't work though :( 
I'm on my friend's laptop at this very moment and this is what I got from my computer when I followed your advice:

```

sebastian@(none):~$ sudo ifdown eth0
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 3170
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:c0:9f:50:db:2e
Sending on   LPF/eth0/00:c0:9f:50:db:2e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 172.21.249.166 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

```

```

sebastian@(none):~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:c0:9f:50:db:2e
Sending on   LPF/eth0/00:c0:9f:50:db:2e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

```

sebastian@(none):~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:35:29:60:68
Sending on   LPF/eth1/00:0e:35:29:60:68
Listening on LPF/eth0/00:c0:9f:50:db:2e
Sending on   LPF/eth0/00:c0:9f:50:db:2e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sebastian@(none):~$ 

```

Help please!!!! What should I do now?

---

### Post by SebbeJohan on 2006-12-09
Anyone? I'm desperate here ](*,)

---

### Post by endersshadow on 2006-12-09
When you go to System > Administration > Networking, and select eth0 and then properties, are you set up for a DHCP connection?

---

### Post by SebbeJohan on 2006-12-09
I managed to fix it :D 

It seemed that "auto eth0" was missing in my /etc/network/interfaces. Also there was two other lines about ppp or something like that (don't remember nanymore) that I've deleted. Works like a charm now!!!

Thanks endersshadow for the assistance though!

---

### Post by endersshadow on 2006-12-09
Cool, glad you got it working.  That solution will go into the memory bank for future reference :-D

---

### Post by SebbeJohan on 2006-12-11
I'm back! and so is my problem ](*,) 
I'm begining to think that the bogeyman is living  in my laptop...
Everything was working correctly until yesterday: I went to Uni, connected to the Wifi there without any problem. I got home a few hours later, tried to connect to my wired connection without any success. I tried to boot in safe-gnome, safe-terminal,... impossible to connect... I tried again a few hours after hoping the bogeyman would take a break, and it worked... but only a few minutes...
I'm getting crazy!!! I don't understand why this is happening. As told mentionned before I'm a new to ubuntu and I don't really know what to do? How can I fix this problem?
It seems that my computer can't detect my connection, possibly a conflict somewhere.
sudo ifdown eth0 gives the following:
```
There is already a pid file /var/run/dhclient.eth0.pid with pid 4725
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:c0:9f:50:db:2e
Sending on   LPF/eth0/00:c0:9f:50:db:2e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 172.21.249.166 port 67

```

sudo ifup eth0 gives the following:
```
There is already a pid file /var/run/dhclient.eth0.pid with pid 4725
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:c0:9f:50:db:2e
Sending on   LPF/eth0/00:c0:9f:50:db:2e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 172.21.249.166 port 67
sebastian@sebastian:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:c0:9f:50:db:2e
Sending on   LPF/eth0/00:c0:9f:50:db:2e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

A weired thing is that my username in the terminal used to be different like sebastian@laptop or something like that. Now it's sebastian@sebastian:~$ and a few days ago it was sebastian@(none):~$ 
I don't know maybe there is a correlation here?

Please help!!!! I really need to have this connection working. I'm currently working on my thesis and need to access the library database when I'm home.

---

### Post by SebbeJohan on 2007-01-04
Hi

I still can't connect. It really drives me crazy, I have reinstalled edgy but nothing seems to do the trick...
Please I would really appreciate some help, Ive read some other thread but nothing helped since I don't understand much :-(
HELPPPPPPPP

---

