---
title: "Connecting to Buffalo Linkstation"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by netCDwtF on 2010-07-21
Hi

I am haveing trouble to get familiar with my storage device 
(this one : [http://www.newegg.com/Product/Product.aspx?Item=N82E16822165123](http://www.newegg.com/Product/Product.aspx?Item=N82E16822165123) ) on the linux partition (Ubuntu 9.1 (karmic)).
It is weired via Ethernet cable to my laptop (IBM Lenovo T500)



Firstly I setup it on my windows partition  and was able to acces it via NAS  navigator and also map it into My Computer. So, everything is OK in Windows.

But if I am working in Linux I have no clue how to access it. 
For mounting I need some kind of communication with the device ...

Pinging its static ip (given in Windows setup) gives no result 


anyway some threads had similar issues so i tried
[http://ubuntuforums.org/showthread.php?t=1534167](http://ubuntuforums.org/showthread.php?t=1534167)

route
```
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

```

sudo ifdown eth0
```
ifdown: interface eth0 not configured
```

sudo ifup eth0
```
Ignoring unknown interface eth0=eth0.
```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:22:68:15:9d:fe  
          inet6 addr: fe80::222:68ff:fe15:9dfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9928 (9.9 KB)  TX bytes:1836 (1.8 KB)
          Memory:fc000000-fc020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3784 (3.7 KB)  TX bytes:3784 (3.7 KB)

pan0      Link encap:Ethernet  HWaddr 72:06:4b:ab:2f:6e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:65:c5:ef:ee  
          inet addr:192.168.0.192  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fec5:efee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22451409 (22.4 MB)  TX bytes:6039264 (6.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-65-C5-EF-EE-63-35-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


sudo dhclient eth0
```
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:22:68:15:9d:fe
Sending on   LPF/eth0/00:22:68:15:9d:fe
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
```

this added 
```
eth0:avahi Link encap:Ethernet  HWaddr 00:22:68:15:9d:fe  
          inet addr:169.254.9.156  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:fc000000-fc020000 

```
to the   **ifconfig -a**  list

this ip tho isnt mountable -.-   (mount  /<ip>  sharefolder)

tired of it  and  craving for help  :/

---

### Post by cariboo on 2010-07-23
Go to Places->Network, and see if the device shows up there.

According to the output of ifconfig, wlan0 has an ip address of 192.168.0.192, is that address int he same netblock as your NAS?

To be in the same netblock the NAS ip address should be somewhere between 192.168.0.1 to 192.168.0.254. As long at it's ip address isn't the same as wlan0 you shouldn't have any problems.

---

### Post by netCDwtF on 2010-07-23
Thanks for your reply.


well i opened  my Places - >  network   and replugged the NAS  
Nothing appeared nor dissapeared (ofc i refreshed it)
 

if wlan0 stands for my wireless connections then it shouldn't be the issue at all, because the devaice is pluged to my laptop not wireless router 


In win env I assigened ip for NAS  169.254.0.1   ... should i change it some-why?

---

### Post by Malawi on 2012-07-14
Hi,

I have the exact same problem with the same storage device, on Ubuntu 12.4.
-> unable to connect the NAS via the ethernet cable.

Do you have any news for that?

Thank you

---

### Post by wildmanne39 on 2012-07-14
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

