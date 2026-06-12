---
title: "Ubuntu server can access Internet but cannot access LAN Machines"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by kannuruser on 2014-08-08
Hi, I have 2 ethernet interface eth0 with IP 192.168.1.11 and eth1 with IP 192.168.1.12 and i have modem/router as 192.168.1.1. 

I can access internet from this server machine, but cannot access any other system from this server within the LAN.

Here is the outputs i have. 

**knr@kannur:~$ ifconfig -a**

**eth0 **     Link encap:Ethernet  HWaddr 00:27:0e:2f:83:60  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::227:eff:fe2f:8360/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7203014 (7.2 MB)  TX bytes:2382269 (2.3 MB)

**eth1**      Link encap:Ethernet  HWaddr 00:90:27:77:29:ad  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:27ff:fe77:29ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7797 errors:0 dropped:9 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:609078 (609.0 KB)  TX bytes:25460 (25.4 KB)

**knr@kannur:~$ netstat -rn**

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0                  192.168.1.1     0.0.0.0         UG        0 0          0 eth0
169.254.0.0        0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.1.0        0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0        0.0.0.0         255.255.255.0   U         0 0          0 eth1

**knr@kannur:~$ route**

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default        192.168.1.1     0.0.0.0         UG    0      0        0 eth0
link-local               *                    255.255.0.0     U     1000   0        0 eth0
192.168.1.0           *                  255.255.255.0   U     0      0        0 eth0
192.168.1.0           *                  255.255.255.0   U     0      0        0 eth1

What could be the problem ?

---

### Post by varunendra on 2014-08-08
Hi kannuruser,

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature. Then edit your above post to wrap the output part in 'Code' tags now.

Onto the problem -

Looking at your [other thread]("http://ubuntuforums.org/showthread.php?t=2238208"), it seems eth0 is connected to the modem, while eth1 is connected to the local network via a network switch. The eth0 interface, in this setup, is ONLY connected to the modem and NOT connected to the local network. Is that right?

If yes, then the problem is your current routing table -
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
[B][COLOR="#0000FF"]192.168.1.0[/COLOR]     *               255.255.255.0   U     0      0        0 [COLOR="#FF0000"]eth0[/COLOR]
[COLOR="#0000FF"]192.168.1.0[/COLOR]     *               255.255.255.0   U     0      0        0 eth1[/B]
```
The bottom two routes are the same routes using different interfaces. Since the routes are same, the system prefers the higher one - that is, the one using eth0. As such, you are able to connect to internet (because eth0 is connected to the modem), but not to the local network (because the local network is connected to eth1, but the traffic is being routed through eth0).

The solution is - either keep eth0 and eth1 on different network segments (e.g., **192.168.[COLOR="#008000"]0[/COLOR].xx** and **192.168.[COLOR="#FF0000"]1[/COLOR].xx**), or manually modify the routing table.

I don't know if different networks idea fits into your 'Ubuntu as Gateway' plan, so I'd explain the routing table solution here.

To be able to connect to the local network, you need to delete the route using eth0, so the route using eth1 is used for reaching network 192.168.1.0. But then you won't be able to connect to internet since eth1 is not connected to the modem (the gateway). To be able to connect to internet, a path to reach the gateway must be defined - means there must exist a route via eth0 to reach the gateway.

So, considering the above conditions, following should solve the problem -
```
sudo route add -host 192.168.1.1 eth0
sudo route del -net 192.168.1.0 netmask 255.255.255.0 eth0
```
What we did is, we added a route specific to the gateway (your modem) via eth0, since eth0 is the one connected to it.
Then, we deleted the route to the network that was using eth0, so that now eth1 can be used to reach the same network (your LAN).

Since the route specific to the gateway still uses eth0 (because of the route we just defined with the first command), any traffic to the gateway will be routed through eth0. So both the LAN and Internet should start working.

The final routing table should look like this -
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
[B][COLOR="#008000"]192.168.1.1[/COLOR]     *               255.255.255.255 UH    0      0        0 [COLOR="#FF0000"]eth0[/COLOR]
[COLOR="#0000FF"]192.168.1.0[/COLOR]     *               255.255.255.0   U     0      0        0 eth1[/B]
```

---

### Post by kannuruser on 2014-08-10
Hi, Varun, thank you for your reply and suggestions. I am a newbie here... I solved the problem by providing eth0 an Ip address 192.168.1.10 and eth0 with 192.168.2.10 and added ip forwarding ..now everything is fine, and when i wrote the iptables, I got the internet connection as well.

---

### Post by varunendra on 2014-08-11
Glad you got it sorted. :)

Please mark the thread as **[SOLVED]** using "Thread Tools" link above the top post. It helps others by indicating that the thread contains a possible solution to the problem mentioned in the Title. Thanks!

---

