---
title: "Help me I think I did something wrong"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by orangeschoolbus on 2010-03-21
After installing the latest version of Kubuntu, I was unable to connect to anything....I decided to create a manual connection instead of using auto eth0....It now seems that I am connected to the router (both the router and Kubuntu show connections) however I still cannot get online or access the other computer on the network...

Did I do something wrong or is there a setting I need to change to make everything work properly?


PS I'm a complete noob to both Ubuntu and Kubuntu so any advice is appreciated

---

### Post by HermanAB on 2010-03-21
Howdy,

Just run the network wizard again...

You need a number of things for networking to work:
IP address
Network mask
Router address
Default route

It is usually the default route that stays forgotten.  So you could do something like this manually (substitute your values of course):
$ sudo ifconfig eth0 192.168.1.100 netmask 255.255.255.0 up
$ sudo route add default gw 192.168.1.1

Or you could also do this:
$ sudo dhclient eth0

to let DHCP sort it out for you.

---

### Post by orangeschoolbus on 2010-03-22
I'm assume when you say default route you're talking about the default gateway? If so then I did have that entered.....

I also ran $ sudo dhclient eth0 here are the results:
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/removed for privacy
Sending on   LPF/eth0/removed for privacy
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.*



I also ran ifconfig because I figured it might be relevant, although to be honest I don't understand what most of the results mean :) but here it is

eth0      Link encap:Ethernet  HWaddr removed for privacy
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:fe26:7735/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xb400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2702 (2.7 KB)  TX bytes:2702 (2.7 KB)

---

### Post by dineshs on 2010-03-22
You can confirm def gateway by running this command
```
route -n
```
Also try to ping the router IP(default gateway obtained via this command)
```
ping 192.168.0.1
```
Assuming the default gateway is 192.168.0.1

---

### Post by orangeschoolbus on 2010-03-22
I couldn't ping the router. I ran route -n and like I said before I don't know what any of it means, but I'm learning....anyways here you go


   Kernel IP routing table
  Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
  192.168.0.0     0.0.0.0         255.255.255.0      U     1           0        0     eth0
  169.254.0.0     0.0.0.0         255.255.0.0         U     1000      0        0     eth0
  0.0.0.0         192.168.0.1     0.0.0.0                  UG    0         0        0     eth0

---

### Post by dineshs on 2010-03-22
Is your ethernet cable proper? Do you have any other Operating system ,If so what is the condition?

---

### Post by orangeschoolbus on 2010-03-22
I just switched the ethernet cable with one from one of my other machines that I'm certain was working....same results

Kubuntu is the only OS on this machine....

---

### Post by sinhanikhil.5 on 2010-03-22
> **orangeschoolbus said:**
> After installing the latest version of Kubuntu, I was unable to connect to anything....I decided to create a manual connection instead of using auto eth0....It now seems that I am connected to the router (both the router and Kubuntu show connections) however I still cannot get online or access the other computer on the network...

Did I do something wrong or is there a setting I need to change to make everything work properly?


PS I'm a complete noob to both Ubuntu and Kubuntu so any advice is appreciated
Well please dont cry, I cant help u as I am new too but I am sure ull get it done right. 
 
 
 
 
.

---

### Post by dineshs on 2010-03-22
This link may be useful
[http://ubuntuforums.org/showpost.php?p=8275776&postcount=6](http://ubuntuforums.org/showpost.php?p=8275776&postcount=6)

---

### Post by dineshs on 2010-03-22
pl read this also if you are manually setting IP
[http://ubuntuforums.org/showthread.php?p=8975701#post8975701](http://ubuntuforums.org/showthread.php?p=8975701#post8975701)

---

### Post by orangeschoolbus on 2010-03-22
> **dineshs said:**
> This link may be useful
[http://ubuntuforums.org/showpost.php?p=8275776&postcount=6](http://ubuntuforums.org/showpost.php?p=8275776&postcount=6)


I can't run the commands from that thread. When I try to run the commands gk sudu it tells me I need to install, then it says it couldn't find the package

---

### Post by dineshs on 2010-03-22
Sorry you are using KDE pl try kdesudo

---

### Post by dineshs on 2010-03-22
you may also refer kubuntuguide
[http://kubuntuguide.org/Karmic#Networking](http://kubuntuguide.org/Karmic#Networking)

---

### Post by orangeschoolbus on 2010-03-22
I appreciate all the help, I decided to wubi install Kubuntu on my Windows machine and everything is working fine. Since I'm doing this as a "pet project" I will play with it on that machine until I feel more comfortable with it and the new version comes in a month or so....

I will (obviously) still be here regularly looking for help, but for now I have solved (avoided) my network problems and am now ready to 'get to know' the OS....

---

