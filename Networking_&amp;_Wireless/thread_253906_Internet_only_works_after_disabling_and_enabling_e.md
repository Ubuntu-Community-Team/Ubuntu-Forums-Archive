---
title: "Internet only works after disabling and enabling eth0"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by grilkip on 2006-09-09
using 6.06LTS

When I boot into Ubuntu lately, I am not able to access the internet. When I go to System>Administration>Networking eth0 appears active. But when I simply deactivate it and then activate it again, the internet is back.

?????

Any ideas?

---

### Post by MrHorus on 2006-09-09
> **grilkip said:**
> using 6.06LTS

When I boot into Ubuntu lately, I am not able to access the internet. When I go to System>Administration>Networking eth0 appears active. But when I simply deactivate it and then activate it again, the internet is back.

?????

Any ideas?

Possibly not getting an ip address.

Rather than doing that, if you go to the console and try dhclient does it work?

---

### Post by grilkip on 2006-09-09
```
duuser@uuser-desktop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:11:d8:82:99:b4
Sending on   LPF/eth1/00:11:d8:82:99:b4
Listening on LPF/eth0/00:11:d8:82:ae:24
Sending on   LPF/eth0/00:11:d8:82:ae:24
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.138
bound to 10.0.0.1 -- renewal in 3347 seconds.
```Is what I get.

After that the internet suddenly started working (I noticed gaim was signing on)

What does this mean and how do I fix it?

---

### Post by linuxusr50 on 2006-09-09
What you are seeing is a lease renewel on the IP your eth0 adapter is getting.

let us see the results of the following when is failed state:
```
ifconfig
```
```
less /etc/network/interfaces 
```


When in the failed state try running the following and see if it revives the connection.
```
sudo dhclient
```

---

### Post by borissjroetskov on 2007-04-09
hello,

I have the same problem and i still didn't find a solution.
'sudo dhclient' revives my connection, but only for the current session. The nex time i boot, the problem persists.
ifconfig in failed state:
> eth0      Link encap:Ethernet  HWaddr 00:50:04:34:78:E0
          inet addr:192.168.2.107  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fe34:78e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:130440 (127.3 KiB)  TX bytes:14201 (13.8 KiB)
          Interrupt:177 Base address:0x6f80

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

ifconfig after sudo dhclient:
> eth0      Link encap:Ethernet  HWaddr 00:50:04:34:78:E0
          inet addr:10.91.4.167  Bcast:10.91.7.255  Mask:255.255.248.0
          inet6 addr: fe80::250:4ff:fe34:78e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:311525 (304.2 KiB)  TX bytes:39689 (38.7 KiB)
          Interrupt:177 Base address:0x6f80

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3084 (3.0 KiB)  TX bytes:3084 (3.0 KiB)


can someone pls help me, this really is a small but annoying problem

---

### Post by itsmeagain on 2007-04-09
Hello 
You are not alone, I have the same problem.  The only way I can get my wireless card to work after I boot my machine is to go to System > Administraton > Network.  Here I can see that wlan0 is active. I must disable it, close Network, open Network and then activate wlan0, and then and only then it works as soon as I have closed Network.
I am running Ubuntu 6.06.1 desktop with a linksys card using ndiswrapper and the windows driver wmp11v27.  In Xandros Linux this driver works fine with ndiswrapper and I never had this problem.
I notice your wireless is on eth0, mine was the same but I changed some text on a few files and now it is on wlan0, however the probem was the same for me when I was using eth0.
Should you wish to change from eth0 to wlan0 and do not know how, I can post how I did mine.
Hopefully somebody with more experiance than I have will comes up with a solution to this annoying problem.  I am just wondering how many other users have had this problem

---

### Post by borissjroetskov on 2007-04-09
I am not talking about a wireless card, but about a wired connection. I guess that wireless is a bit more complicated because of the drivers you have to install. My connection works fine without installing any drivers, except that one flaw.
I hope someone can help me/us...

---

