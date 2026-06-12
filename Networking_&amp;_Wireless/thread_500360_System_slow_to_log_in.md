---
title: "System slow to log in"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by Alsvartr on 2007-07-13
Hello. Recently I deleted Network Manager from Ubuntu cause I prefer to use pon directly and after reboot when I log in the desktop starts very slowly. Then I commented lines in my /etc/network/interfaces file and reboot again. And this time all worked properly (but of course my network interfaces didn't loaded :) ). Can anyone tell me - what's the problem? Where should I dig?

---

### Post by Mr. C. on 2007-07-14
Lets see the contents of the uncommented /etc/network/interfaces.

MrC

---

### Post by Alsvartr on 2007-07-14
Here it is:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0

auto eth1
iface eth1 inet dhcp
```

---

### Post by Mr. C. on 2007-07-14
Your eth0 static entry is missing the **gateway** entries.  Add an entry:

```
gateway *gateway_IP*
```

where gateway_IP is the IP address of the gateway to use, likely your router's LAN address.

Also, show the contents of your /etc/resolv.conf

be sure you have your ISPs nameserver's listed there.

MrC

---

### Post by Alsvartr on 2007-07-14
> **Mr. C. said:**
> Your eth0 static entry is missing the **gateway** entries.  Add an entry:

```
gateway *gateway_IP*
```

where gateway_IP is the IP address of the gateway to use, likely your router's LAN address.

Also, show the contents of your /etc/resolv.conf

be sure you have your ISPs nameserver's listed there.

MrC

eth0 is the network card that connected to my notebook... So I have no gateway on it.

/etc/resolv.conf
```
search mo
nameserver 10.0.0.1
nameserver 212.152.38.198
```
Nameservers are added by me personally and they're correct. But I don't add "search mo" - it added automatically after reboot.

---

### Post by Mr. C. on 2007-07-14
Remove:

nameserver 10.0.0.1

from your resolv.conf file.  Do not use your router's poor caching DNS services.  Use reliable servers, such as your ISPs.

Show the output from

```
ifconfig -a
netstat -rn

```
MrC

---

### Post by Alsvartr on 2007-07-14
> **Mr. C. said:**
> 
Remove:

nameserver 10.0.0.1

from your resolv.conf file. Do not use your router's poor caching DNS services. Use reliable servers, such as your ISPs.
But 10.0.0.1 is my ISPs DNS...

> **Mr. C. said:**
> 
Show the output from

```
ifconfig -a
netstat -rn

```
MrC

```
alsvartr@bust:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:80:48:B5:5D:22  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:48ff:feb5:5d22/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9749 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1250787 (1.1 MiB)  TX bytes:9699630 (9.2 MiB)
          Interrupt:9 Base address:0xb800 

eth1      Link encap:Ethernet  HWaddr 00:14:78:25:4F:66  
          inet addr:192.168.28.49  Bcast:192.168.28.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:fe25:4f66/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2323846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2217433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1246059198 (1.1 GiB)  TX bytes:1739540409 (1.6 GiB)
          Interrupt:9 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1185862 (1.1 MiB)  TX bytes:1185862 (1.1 MiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.0.28.176  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:1906210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2179991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1106042720 (1.0 GiB)  TX bytes:1619676785 (1.5 GiB)

```

```

alsvartr@bust:~$ netstat -rn
Destination Gateway Genmask Flags MSS Window irtt Iface
192.168.50.1    192.168.28.1    255.255.255.255 UGH       0 0          0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.28.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0
0.0.0.0         192.168.28.1    0.0.0.0         UG        0 0          0 eth1

```

---

### Post by Mr. C. on 2007-07-14
You have two default routes:

```
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0
0.0.0.0         192.168.28.1    0.0.0.0         UG        0 0          0 eth1
```

You need to delete the one that is incorrect, probably the PPP0 route.  The default route controls where packets go that do not have a specific host or network route.

If 10.0.0.1 is your ISPs name server, and it responds, then leave it.

MrC

---

### Post by Alsvartr on 2007-07-14
> **Mr. C. said:**
> You have two default routes:

```
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0
0.0.0.0         192.168.28.1    0.0.0.0         UG        0 0          0 eth1
```

You need to delete the one that is incorrect, probably the PPP0 route.  The default route controls where packets go that do not have a specific host or network route.

I know it, but it doesn't fix my problem. When I have network manager installed (but doesn't use it - I use "pon") all worked perfectly with this settings. After I uninstall NM - I got this slow log in proccess.
P.S. ppp0 is my VPN connection... It is correct.

---

### Post by Mr. C. on 2007-07-14
Have you checked your MTU for your PPP connection?

It is very difficult to diagnose someone's problem, when only part of the information is shared each time.  We've come *long* way from your initial problem description, to your more complex setup, and this wastes a lot of diagnosis time, and guides us down the wrong path.

MrC

---

### Post by Alsvartr on 2007-07-14
> **Mr. C. said:**
> Have you checked your MTU for your PPP connection?

It is very difficult to diagnose someone's problem, when only part of the information is shared each time.  We've come *long* way from your initial problem description, to your more complex setup, and this wastes a lot of diagnosis time, and guides us down the wrong path.

MrC
The problem isn't in my internet or ethernet connection. It worked fine when NM was installed and it work fine now. BUT. After uninstalling NM I got slow log in process (nautilus and desktop starts very slow). System logs doesn't show any interesting information. I just don't know where to dig.

---

### Post by Mr. C. on 2007-07-14
How do you know it has nothing to do with the network connection?   You said you commented out your network/interfaces file, essentially disabling the network, and then everything is fine.  This, and the long delay with your desktop appearing looks very much like a network problem.

The details of your network are sketchy, there is no route in your routing table for the 127.0.0.0/8 network, and you have two default routes.  You seem to know enough about networking, but are ignoring basic configuration problems.

Tear down that network, and put it back piece by piece until you have your setup working again.

MrC

---

### Post by Alsvartr on 2007-07-14
> **Mr. C. said:**
> 
The details of your network are sketchy, there is no route in your routing table for the 127.0.0.0/8 network, and you have two default routes.  You seem to know enough about networking, but are ignoring basic configuration problems.


M, you right of course. I just wanted to say that network works fine.

> **Mr. C. said:**
> 
Tear down that network, and put it back piece by piece until you have your setup working again.

What have I done:
1. Rebooted and log in with this "slow problem". By the way, programs (such as gedit or gnome terminal or nautilus) are starting slow too.
And routing table was:
```
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.28.0    *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.28.1    0.0.0.0         UG    0      0        0 eth1
```

2. Deleted this eth1 default route:
```
sudo route -net del default
```

3. After that all delay problems with programs were fixed O_o

But what kind of route is this? I thought it is route to my ISP local network (without it I can't browse the local network). Looks like this route really is the problem. What should I do with it?

---

### Post by Mr. C. on 2007-07-14
The kernel can use one and only one default route to forward packets to networks it cannot directly reach.  Multiple default routes create problems, as you've experienced.  Some systems allow multiple default routes, and the route with the highest priority is used in such cases.  Windows allows this - when you establish a dial-up connection when an Ethernet connection is already present, Windows will simply add new default and network specific routes with higher priorities than existing routes.  They are removed when the connection is broken down.

The second route you had made no sense - the default route must represent the IP address of the router which will forward all packets which are not destined for directly connected networks.  In a point-to-point network, placing a packet "on the wire" is equivalent to addressing the other end of the wire, so a network route could be equivalent to a host route.
  
MrC

---

### Post by Alsvartr on 2007-07-15
> **Mr. C. said:**
> The kernel can use one and only one default route to forward packets to networks it cannot directly reach.  Multiple default routes create problems, as you've experienced.  Some systems allow multiple default routes, and the route with the highest priority is used in such cases.  Windows allows this - when you establish a dial-up connection when an Ethernet connection is already present, Windows will simple add new default and network specific routes with higher priorities than existing routes.  They are removed when the connection is broken down.

Wait, wait. When I'm log in to system I have **only one** default route.
```
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.28.0    *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.28.1    0.0.0.0         UG    0      0        0 eth1
```
See? And this route forward packets to my ISPs local network. 192.168.28.1 is my gateway to this network. If I remove this route I would be unable to browse local network (my ISPs local site, ftp server, DC++ and stuff). I just rebooted with my Ubuntu LiveCD to see how the routing table looks like by default. And I saw this entry:
```
default         192.168.28.1    0.0.0.0         UG    0      0        0 eth1
```

I don't understand the source of my problem.

---

### Post by Mr. C. on 2007-07-15
I'm not sure if we're on the same page, mostly due to some loose terminology you are using.  When you say "forward packets to my ISPs local network", I hope you are meaning "forward packets to the **router** directly attached to my 192.168.28.0/24 network.  You don't forward packets to some network cloud.

The route entry:

```
default         192.168.28.1    0.0.0.0         UG    0      0        0 eth1
```

is the default route you have configured.  Your system will send *all* packets (that have not matched other specific routes in the route table) to the address 192.168.28.1 via the eth1 interface.  This IP address (192.168.28.1) must be a *router* not a network, or some other non-routing piece of hardware.

This must either be YOUR router (which in turn is configured to route to your ISPs router), or your ISPs router which is on the same network as your eth1 interface.

I still don't see a route for the loopback interface - you need that!

MrC

---

### Post by Alsvartr on 2007-07-15
> **Mr. C. said:**
> 
The route entry:

```
default         192.168.28.1    0.0.0.0         UG    0      0        0 eth1
```

is the default route you have configured.  Your system will send *all* packets (that have not matched other specific routes in the route table) to the address 192.168.28.1 via the eth1 interface.  This IP address (192.168.28.1) must be a *router* not a network, or some other non-routing piece of hardware.

This must either be YOUR router (which in turn is configured to route to your ISPs router), or your ISPs router which is on the same network as your eth1 interface.

Yes, it is my ISPs router.

> **Mr. C. said:**
> I still don't see a route for the loopback interface - you need that!

Could you tell me, how can I configure one? You saw contents of my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0

auto eth1
iface eth1 inet dhcp
```
I have this loopback entry.

---

### Post by Alsvartr on 2007-07-15
Tried this:
```
sudo route add -host 127.0.0.1 lo
```
Nope. Still working slow.

When I have only this eth1 default route and no ppp0 default route - all working slow (it takes approximately half a minute to gedit or nautilus to start). When I activate ppp0 vpn connection - all working perfect.

---

### Post by Mr. C. on 2007-07-15
If I recall, you had a 10.x.x.x name server listed in your resolv.conf.  What network is this actually on ?  The VPN network ?

Since 10.x.x.x is a private network, you will have trouble if that network is not available, as your DNS will have to timeout before the next name server is checked in /etc/resolv.conf.  These timeouts are about 15 seconds / query.

MrC

---

### Post by Alsvartr on 2007-07-15
Finally.

I removed all nameservers from resolv.conf and it work - I have no delays. Now I must add the routes to this dns servers in interfaces file, is this correct?

---

### Post by Alsvartr on 2007-07-15
> **Mr. C. said:**
> If I recall, you had a 10.x.x.x name server listed in your resolv.conf.  What network is this actually on ?  The VPN network ?

Since 10.x.x.x is a private network, you will have trouble if that network is not available, as your DNS will have to timeout before the next name server is checked in /etc/resolv.conf.  These timeouts are about 15 seconds / query.

MrC

Yes, it is a private network. And this network is accessed by the ppp0 interface, I understand.
```
10.0.0.1        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
```

Then, what should I do? Start ppp connection in system startup through the "auto" stanza in interfaces file?

---

### Post by Mr. C. on 2007-07-15
I can't tell you what to do, since you've never stated your goal.  We've been working on one issue after another, and I have no idea what you are ultimately trying to do.

MrC

---

### Post by Alsvartr on 2007-07-15
Did you saw my previous post?
> I removed all nameservers from resolv.conf and it work - I have no delays.

---

### Post by Mr. C. on 2007-07-15
Yes, and you ALSO asked"...Now I must add the routes to this dns servers in interfaces file, is this correct?" and then followed up with "Then, what should I do? Start ppp connection in system startup through the "auto" stanza in interfaces file?"

That's three questions asking for advice as to what you should do.  Nobody can tell you what to do, UNTIL you make your goals clear.  I have no idea how you are trying to configure your network, nor what you require.

MrC

---

