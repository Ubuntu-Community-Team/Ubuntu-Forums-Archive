---
title: "Newbie need help"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by websphere on 2008-04-24
Hi guys,

I'm a new ubuntu user (just switch from Microsoft) and is willing to learn. Need some help in connecting to SpeedTouch 570 (integrated adsl modem/router). I'm able to see the router but there isn't any IP assigned from the router... 

When I plug directly using Ethernet cable it obtain IP address. Please advice... Thank you. Below shows some of response i got:

```

sk@sk-laptop:~$ iwconfig eth1
eth1      IEEE 802.11b  ESSID:"sk"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:10:C6:48:DB:CB   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sk@sk-laptop:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:04:23:7e:89:74  
          inet6 addr: fe80::204:23ff:fe7e:8974/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:111 dropped:111 overruns:0 frame:0
          TX packets:407 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:71463 (69.7 KB)
          Interrupt:11 Base address:0x8000 Memory:e0001000-e0001fff 

sk@sk-laptop:~$ dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 22480
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

```

```
sk@sk-laptop:~$ sudo killall dhclient
sk@sk-laptop:~$ sudo ifconfig eth1 up
sk@sk-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:04:23:7e:89:74
Sending on   LPF/eth1/00:04:23:7e:89:74
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by websphere on 2008-04-25
anyone?

---

### Post by dstew on 2008-04-25
You can only have one active interface at a time with Network Manager. Unplug the cable, reboot, and try again, without the cable plugged in.

---

