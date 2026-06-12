---
title: "Internet connection sharing"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by stealintv on 2008-06-06
Hello all. I am interested in setting up a network to share an internet connection. This is the setup:

HP nc6000 laptop running Ubuntu 7.10
- eth0 (built on network card)
- eth2 (pcmcia wireless card)

There is a rogue access point in my area (ssid = linksys) with a very fast internet connection I would like to share with my desktops. I have a linksys router and some cables.

I installed firestarter with "apt-get" and went through the setup wizard. Upon running the command
```
sudo firestarter
```

I get an error message saying "the device eth0 is not ready please check your settings and make sure your internet connection is active."

Because I am typing this post using the active internet connection, I know that it is working.

output of ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:08:02:E0:DD:08
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8496 (8.2 KB)  TX bytes:7051 (6.8 KB)
          Interrupt:11

eth2      Link encap:Ethernet  HWaddr 00:60:1D:F2:E2:DC
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260:1dff:fef2:e2dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2610 errors:20 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2455905 (2.3 MB)  TX bytes:546158 (533.3 KB)
          Interrupt:3 Base address:0x4100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:352 (352.0 b)  TX bytes:352 (352.0 b)

```

uname -a

```
Linux stealintv215-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC2008 i686 GNU/Linux
```

Any ideas would be appreciated.

Thanks in advance,
Andy

---

### Post by SpaceTeddy on 2008-06-06
first - it is neither legal nor "nice" to use other peoples internet without telling them ! 

here is a [[COLOR="Blue"]tutorial[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") on how to setup internet sharing for ubuntu (i don't use firestarter - i write my iptables rules myself... if you want to use firestarter, then you will need to find the apropriate buttons in it that resemble my commands)

if any questions remain, just ask.

hope it helps :)

---

### Post by stealintv on 2008-06-07
Thanks for the speedy response. We will say that the rogue access point is in my test lab. 

I followed the tutorial changing only the internet connected device to eth2.

I got a '1' response after entering:
```
sudo sysctl -w net.ipv4.ip_forward=1
``` so I didn't need the dirty hack.

I have the network cable plugged directly into the back of a Winxp machine to test before I setup the router. I can ping the XP machine from Ubuntu and vice versa. The Ubunutu machine is also connected to the internet, but the XP machine won't connect to the internet. 

I have the XP firewall turned off. Here is the XP info:

```
IP         10.8.16.2
subnet     255.255.255.0
gateway    10.8.16.1
dns        10.8.16.1
```

and the ubuntu laptop's:

```
eth0      Link encap:Ethernet  HWaddr 00:0d:9d:8d:76:0f
          inet addr:10.8.16.1  Bcast:10.8.16.0  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe8d:760f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2606 (2.5 KB)  TX bytes:6513 (6.3 KB)
          Interrupt:11

eth2      Link encap:Ethernet  HWaddr 00:60:1d:f2:e2:dc
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260:1dff:fef2:e2dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29422 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:71606890 (68.2 MB)  TX bytes:3756461 (3.5 MB)
          Interrupt:3 Base address:0x180



lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:106000 (103.5 KB)  TX bytes:106000 (103.5 KB)
```

Any ideas?
Thanks again for the help!
Andy

---

### Post by superprash2003 on 2008-06-07
in your windows pc type ping google.com and post output

---

### Post by stealintv on 2008-06-07
OK so I fugured it out.
The DNS needed to be 192,168.0.1 on the XP machine.
Just thought I'd post in case anyone else was following this. 

Another tip, read the tutorial twice.

Thanks for all the help. I may have another question once I start setting up the router, but that will be later. I have some work to do now!!!

Andy

---

