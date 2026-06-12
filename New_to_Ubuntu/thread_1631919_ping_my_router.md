---
title: "ping my router?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by slwx on 2010-11-27
Hi,
I have a small networking question. 
I've just been trying to ping the router I'm connected to wireless, and the other computers in my network. 

*How do i find my routers ip adress?

My ipadres is 192.168.1.101, but when I ping 192.168.1.1 I get no response..

thanks,
Mathi

---

### Post by speedofdark on 2010-11-27
Open up a terminal and do;

```

ifconfig

```

The gateway (GW) address is your ip address from your router.

---

### Post by slwx on 2010-11-27
mathias@mathias:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:46:fe:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:d2:ef:59  
          inet addr:**192.168.1.101**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fed2:ef59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10576160 (10.5 MB)  TX bytes:9021138 (9.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-D2-EF-59-64-32-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by MrWES on 2010-11-27
Did you try 192.168.0.1 ?

[http://www.techspot.com/guides/287-default-router-ip-addresses/]("http://www.techspot.com/guides/287-default-router-ip-addresses/")

~Bill

---

### Post by speedofdark on 2010-11-27
> **slwx said:**
> mathias@mathias:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:46:fe:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          .............


Doesn't show up indeed.... 

```

route -n

```

Look for the UG flag.

---

### Post by Elfy on 2010-11-27
Networking not being something I get involved in much would it not be the wlan connection as the OP is using wireless anf would it not be also worth pinging 192.168.1.101

Possibly wrong - but heyho :)

---

### Post by uRock on 2010-11-27
**netstat -r** will show the default gateway, which is what you are looking for.

Example:
```
rabbit@rabbit-desktop:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.251.0   *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
[COLOR="Red"]default         192.168.251.254[/COLOR] 0.0.0.0         UG        0 0          0 eth0
```

---

### Post by matt_symes on 2010-11-27
Hi

> *How do i find my routers ip adress?192.168.1.101 is your internal  (routers) IP address. (If that is your internal IP)

You can use 

[http://www.whatsmyip.org/](http://www.whatsmyip.org/)

to get you external ip. A little OT i know.

Kind regards

---

### Post by chili555 on 2010-11-27
> wlan0 Link encap:Ethernet HWaddr 00:1d:e0:d2:ef:59
inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0192.168.1.101 is your computer's address and not the router. If you ping that address, you are pinging yourself. You might as well send yourself an email to ask if you are there. You know you are!

As has been suggested, the router's IP address is the same as the gateway in:```
route -n
```Here is mine, as an example:```
 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         [COLOR="Red"]192.168.1.254[/COLOR]   0.0.0.0         UG    100    0        0 wlan0
```If I want to ping the router, I do:```
ping -c3 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_req=1 ttl=255 time=0.980 ms
64 bytes from 192.168.1.254: icmp_req=2 ttl=255 time=1.02 ms
64 bytes from 192.168.1.254: icmp_req=3 ttl=255 time=1.07 ms

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.980/1.028/1.078/0.054 ms
```The modifier -c3 means ping for a count of three. Without a modifier, it will ping forever, or until you press Ctrl+c.

---

### Post by slwx on 2010-11-27
hmm very strange
mathias@mathias:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 wlan0
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

and now I can ping 192.168.1.1 .. 

sory for trouble guys, must have been the router.

thanks,
Mathi

---

