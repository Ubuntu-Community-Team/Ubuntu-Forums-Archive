---
title: "internet doesnt work ubuntu 7.04"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by sumedhamahajan on 2008-06-19
hi, i am a new user. my internet connection is broadband with an external modem. the internet used to work initially when i installed all the updates and then i moved my laptop to my school and changed the ip and settings accordingly to the lan connection there. and now i am back home, again switched the settings but now it doesnt work.

---

### Post by argail1980 on 2008-06-19
what kind of connection dou you have? cable? DSL?

then: open a terminal (Applications > Accesoires > Terminal)

and post the output of when you enter

```
ifconfig
```

---

### Post by sumedhamahajan on 2008-06-19
eth0      Link encap:Ethernet  HWaddr 00:15:00:4A:FC:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc000 Memory:b8006000-b8006fff 

eth1      Link encap:Ethernet  HWaddr 00:0F:B0:D8:85:10  
          inet addr:192.168.1.5  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:b0ff:fed8:8510/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1802 (1.7 KiB)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:15:00:4A:FC:39  
          inet addr:169.254.6.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xc000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6718 (6.5 KiB)  TX bytes:6718 (6.5 KiB)



thanks.. this is what i get

---

### Post by argail1980 on 2008-06-19
hmm... 
go 
System > Administration > Network
mark "eth0" and click properties. Uncheck the "activate roaming mode". Then close all network windows and post the output of ifconfig again.

(sorry if the menu names are not exact, mine are in german :-) )

maybe then your internet already works again.
If not, you should also enter in a terminal ```
sudo /etc/init.d/networking restart
```

If not, again, what kind of connection do you have? PPPoE (dsl)?, cable modem?

---

### Post by superprash2003 on 2008-06-19
also type ping google.com in your terminal and post output..

---

### Post by sumedhamahajan on 2008-06-19
i tried unchecking the enable roamin mode box but it gets automatically enabled when i again open that window, dont kno why is that happening. also when i did  sudo /etc/init.d/networking restart,  it gave me
* Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5049
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:00:4a:fc:39
Sending on   LPF/eth0/00:15:00:4a:fc:39
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:00:4a:fc:39
Sending on   LPF/eth0/00:15:00:4a:fc:39
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


and while pinging google.com , i got an unknown host

---

### Post by superprash2003 on 2008-06-19
try ping 192.168.1.1 and post output

---

### Post by ettercap on 2008-06-19
hey

try this -- it worked for me i hav broadband connection

sudo pppoeconf

enter ur username and passsword

it will work

---

### Post by argail1980 on 2008-06-20
this is only if sumedhamahajan has a pppoE connection, (one of the things I've been asking for since his first post..)

When it is i.e. a cable connection, pppoEconf will do no good!

His last post looks like a dhclient got stuck

> There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416

it also looks like the dhcclient is not able to get an IP address from the... router? modem?

> No DHCPOFFERS received.


btw: can anyone see where these additional devices come from? eth2 and wlan0 were not listed by ifconfig.. are both of them wlan devices?

---

### Post by sumedhamahajan on 2008-06-20
i have dsl connection with ppp0e.
i tried pinging 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.90 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.872 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.845 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.877 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.873 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.821 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.832 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.826 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.851 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.853 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=0.819 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=0.862 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=0.864 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=0.860 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=0.859 ms
64 bytes from 192.168.1.1: icmp_seq=16 

this is wat i get

---

### Post by sumedhamahajan on 2008-06-20
and when i did sudo pppoeconf,
it scanned eth0 and while scannin eth1, it stopped dere on 100%, displaying  Looking for PPPoE Access Concentrator on eth1
and then it stayed like that and nothing happened, the display became stagnant

---

### Post by superprash2003 on 2008-06-20
in the terminal type ping 64.233.167.99 and post output

---

### Post by sumedhamahajan on 2008-06-22
on pingin 64.22.167.99, i got

PING 64.233.167.99 (64.233.167.99) 56(84) bytes of data.
From 192.168.1.5 icmp_seq=2 Destination Host Unreachable
From 192.168.1.5 icmp_seq=3 Destination Host Unreachable
From 192.168.1.5 icmp_seq=4 Destination Host Unreachable
From 192.168.1.5 icmp_seq=6 Destination Host Unreachable
From 192.168.1.5 icmp_seq=7 Destination Host Unreachable
From 192.168.1.5 icmp_seq=8 Destination Host Unreachable
From 192.168.1.5 icmp_seq=10 Destination Host Unreachable
From 192.168.1.5 icmp_seq=11 Destination Host Unreachable
From 192.168.1.5 icmp_seq=12 Destination Host Unreachable
From 192.168.1.5 icmp_seq=14 Destination Host Unreachable
From 192.168.1.5 icmp_seq=15 Destination Host Unreachable
From 192.168.1.5 icmp_seq=16 Destination Host Unreachable
From 192.168.1.5 icmp_seq=18 Destination Host Unreachable


dont know wat the prob is, my net is still not working!!

---

### Post by superprash2003 on 2008-06-22
are other pcs on your network able to connect? like a windows pc? do you connect to the  internet using a dialer? or internet works as soon as you switch on modem?

---

### Post by sumedhamahajan on 2008-06-23
ya, i presently use windows on it. it works fine wit it. n no, i dnt use a dialer, internet works as soon as i switch on my modem..

---

### Post by Midwest-Linux on 2008-06-23
> **sumedhamahajan said:**
> hi, i am a new user. my internet connection is broadband with an external modem. the internet used to work initially when i installed all the updates and then i moved my laptop to my school and changed the ip and settings accordingly to the lan connection there. and now i am back home, again switched the settings but now it doesnt work.

 Did you do any recent updates before you tried to access the internet again? 

(Only reason why I am asking, is that there seems to be a pattern of updates of the kernel causing problems from Grub, to wireless, to add/remove.)

---

### Post by .chaos on 2008-06-23
> **Midwest-Linux said:**
> Did you do any recent updates before you tried to access the internet again? 

(Only reason why I am asking, is that there seems to be a pattern of updates of the kernel causing problems from Grub, to wireless, to add/remove.)i did a massive update (190 items) and i'm having similar issues with my cable connection.  dhcclient issues and such.

---

### Post by sumedhamahajan on 2008-06-23
hi! wel, i did the basic updates available on the update manager!! nothin except dat! the media set ups and all! it did used to work after the updates! its jus not workin after i got it bak home frm college! i had to change my ip settings in college and now wen i am changing it bak to the ones at home, it doesnt work! maybe i am missing something!

---

### Post by superprash2003 on 2008-06-23
have you tried DHCP for your network card under system->administration->network ..??strange thing is you are able to ping your modem.. so that connection looks good.. your sure that in windows you didnt require a dialer right? could you mention your modem model no?

---

