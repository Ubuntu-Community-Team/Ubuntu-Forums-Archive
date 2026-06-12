---
title: "Firefox not locating server"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by RichardSchollar on 2006-08-12
I run a dual boot PC (XP and Ubuntu) and access the internet thru an ADSL line and a Zoom X5 router (wired).  I have no problems connecting with XP.  I have an Nvidia ethernet (430 chip) which I believed was causing me problems connecting under Ubuntu (the ethernet car simply wasn't recognised at all) so I have installed a 3Com ethernet card 10/100 (not Gigabit) and at least Firefox under Ubuntu can now connect to my router.  However, it is still unable to connect to any websites.  Does anyone have any ideas what I can try next?

The following could be relevant:

 richard@RGS:~$ sudo ifconfig
Password:
eth1      Link encap:Ethernet  HWaddr 00:0A:5E:56:F9:E1
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:5eff:fe56:f9e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:1 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1404 (1.3 KiB)  TX bytes:1392 (1.3 KiB)
          Interrupt:58 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8708 (8.5 KiB)  TX bytes:8708 (8.5 KiB)

richard@RGS:~$ ping -c 5 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=1.23 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.409 ms
64 bytes from 10.0.0.2: icmp_seq=3 ttl=64 time=0.416 ms
64 bytes from 10.0.0.2: icmp_seq=4 ttl=64 time=0.408 ms
64 bytes from 10.0.0.2: icmp_seq=5 ttl=64 time=0.408 ms

--- 10.0.0.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 0.408/0.574/1.232/0.329 ms
richard@RGS:~$


The router IP address is 10.0.0.2.  When I was using my motherboard's ethernet adapter, I was unable to connect to the router thru Firefox, so it would appear that installing the network card has had some benefit.

Any help appreciated.

Richard

---

### Post by NetworkGuy on 2006-08-12
My first thought would be that your DNS entries may not be correct.   Check your /etc/resolv.conf.   If there are no entries in there, your PC does not know how to convert [www.something.com](www.something.com) to an IP address.   If there are entries in there, try pinging something using it's URL ([www.yahoo.com](www.yahoo.com) for example).

 If you can not ping [www.yahoo.com](www.yahoo.com) then the servers in the resolv.conf may be incorrect.

---

### Post by drtvasudevan on 2006-08-12
```
gksu gedit /etc/network/interfaces
```
add if it is not there
 dns-nameservers (your ISP number)

---

### Post by HolyJoe on 2006-08-12
Hi, drtvasudevan,

gksu gedit /etc/... for this problem is incorrect.


Tao-HolyJoe

---

### Post by RedBoot on 2006-08-12
NetworkGuy,
> Check your /etc/resolv.conf.Thanks, this answers a question I had lately about where this info was kept.
After changing resolv.conf, do you need to issue a command to activate it?  Would **invoke-rc.d networking restart** work?

---

### Post by NetworkGuy on 2006-08-12
I'm still learning the debian commands myself.   I personally would use 

sudo ifdown <interface>

followed by

sudo ifup <interface>

Maybe someone else can properly answer your invoke-rc.d question.

---

### Post by RichardSchollar on 2006-08-13
Guys

Thanks for all replies.

The problem was the about:config IPv6 thing.

Changed the setting to TRUE and can now surf!:D 

Richard

---

### Post by drtvasudevan on 2006-08-13
> **RichardSchollar said:**
> Guys

Thanks for all replies.

The problem was the about:config IPv6 thing.

Changed the setting to TRUE and can now surf!:D 

Richard

i am trying my best not to get mad at this ipv6 stuff.:evil: 
if the mozilla people insist on keeping it i dont know why ubuntu people will provide the environment!
the first thing most people will do is try and connect to internet soon after installation.
not being able to certainly will create a very bad impression.:confused: 
i myself came to ubuntu an year ago and gave up ubuntu precisely on this account. the ipv6 stuff was not very well known at that time i guess.
i came back to ubuntu about two month back but by this time i knew the problem.
will somone listen?
:-k

---

