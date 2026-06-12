---
title: "Network printer found, but cannot connect to it"
date: 2013-10-15
forum: Networking &amp; Wireless
---

### Post by Gabriele_Magi on 2013-10-15
Hello everyone :)

As indicated in the thread title, I cannot connect to the network printer here at the office .

This is how my PC is configured:

partition 1 :
Ubuntu 12.04
2 user accounts
Installed Printers :
Brother MFC ... (ip 10.31.0.xx )
Samsung ML2850 (ip 10.0.0.xx )

partition 2 :
Lubuntu LXLE
printer:
Brother MFC ... (ip 10.31.0.xx )

I can use both printers with the account of the partition 1.

A few days ago I decided to install LXLE on a new partition
(I needed a DE that would require fewer resources for my pc, and wanted
to have a fresh installation of the OS).
When I tried to configure the printer Samsung , I failed in any way.
I've tried everything: restarting CUPS, changed address ipp ://... , socket ://...,
used the same dnssd:// address of the other user accounts, installed the PPD driver...

If I install the printer and try to print a test page I get this message: "The printer is not responding" .
If I try to change the address, I get the message " CUPS : client error not possible ." 
If I enter 10.0.0.xx on Firefox (accounts partition 1 ), I have access to the configuration page of the printer.
On the other partition, I get an error: "Request timeout".

I am pretty sure that something is not configured in the right way, but I can not figure out where the problem is. :(

If you need more information, feel free to ask me.
Thank you in advance for your help ;)

---

### Post by ronniew on 2013-10-15
Direct connection to the printer or network printer?

If network printer, you may want to check the firewall, in system tools.

---

### Post by Gabriele_Magi on 2013-10-16
Hi ronniew,

Thank you for answering.
Actually it is a network printer.
I checked the firewall, and it's disabled.

I also tried to ping the address, but I don't get any reply from that IP... :-?

---

### Post by houstonbofh on 2013-10-16
I noticed the printers are on different class c type subnets.  You likely have a routing problem.  If this is not enough to help we will need you network config and routing table. (From both systems)

---

### Post by Gabriele_Magi on 2013-10-16
> **houstonbofh said:**
> I noticed the printers are on different class c type subnets.  You likely have a routing problem.  If this is not enough to help we will need you network config and routing table. (From both systems)

Thank you houstonbofh! 

Since I don't know how to solve routing problems, please tell me exactly which information you need.

- About the routing table, you need the data I get from ```
sudo route -n
```
, is that right?
- About the network config, are the data from settings/network connections enough?

---

### Post by houstonbofh on 2013-10-16
No need for sudo. Just ifconfig and route -n.

This is mine.  However, note that I have KVM installed, so ignore the .122 range. :)

```
lee@dev01:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:94:9b:b2  
          inet addr:192.168.64.194  Bcast:192.168.64.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fe94:9bb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68598238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84557794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26516926333 (26.5 GB)  TX bytes:59198707631 (59.1 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:115798046 (115.7 MB)  TX bytes:115798046 (115.7 MB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:25:10:b1  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66902043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57044262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55354113542 (55.3 GB)  TX bytes:16435946275 (16.4 GB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:25:10:b1  
          inet6 addr: fe80::fc54:ff:fe25:10b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66902043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57604551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:56290742144 (56.2 GB)  TX bytes:16465102808 (16.4 GB)

lee@dev01:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.64.1    0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.64.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
lee@dev01:~$ 

```

---

### Post by Gabriele_Magi on 2013-10-17
Ok, so here you are the ifconfig and the route -n of the first partition
(the one that is "working")
```

gabri@gabriele-HP-Compaq-dx2400-Microtower:~$ sudo ifconfig
[sudo] password for gabri: 
eth0      Link encap:Ethernet  IndirizzoHW 00:1e:0b:a9:b7:4e  
          indirizzo inet:10.31.0.8  Bcast:10.255.255.255  Maschera:255.0.0.0
          indirizzo inet6: fe80::21e:bff:fea9:b74e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8125 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:8008696 (8.0 MB)  Byte TX:1296919 (1.2 MB)
          Interrupt:43 Indirizzo base:0x8000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:299 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:17081 (17.0 KB)  Byte TX:17081 (17.0 KB)

gabri@gabriele-HP-Compaq-dx2400-Microtower:~$ sudo route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.31.0.1       0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

```

These are, instead, the ifconfig and route -n of the other system:
```
gabriele@gabriele-pc:~$ ifconfig
eth0      Link encap:Ethernet  IndirizzoHW 00:1e:0b:a9:b7:4e  
          indirizzo inet:10.31.0.45  Bcast:10.31.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::21e:bff:fea9:b74e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10320 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:10750986 (10.7 MB)  Byte TX:1659877 (1.6 MB)
          Interrupt:43 Indirizzo base:0x4000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:3384 (3.3 KB)  Byte TX:3384 (3.3 KB)

gabriele@gabriele-pc:~$ route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.31.0.1       0.0.0.0         UG    0      0        0 eth0
10.31.0.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

I think that I have to modify the routing table (especially the second row),
but I do not know how to do it correctly... :)

---

### Post by houstonbofh on 2013-10-17
It is your subnet mask.  You have a /24 on one and a /8 on the other.  You need a /8 on both.  Ignore the 169...  That is a autoconfig address.

---

### Post by Gabriele_Magi on 2013-10-17
Ok, thanks.
I am not in the office right now, but I guess I have to delete the line with /24
and add a line with /8, using ```
route del -net ... 
``` and then ```
route add -net ...
```

---

### Post by houstonbofh on 2013-10-17
Not route.  Your subnet mask.  Assuming you have a static IP address, it will be in /etc/network/interfaces and you will change a "mask 255.155.155.0" to "mask 255.0.0.0" and reboot or restart networking.

---

### Post by Gabriele_Magi on 2013-10-18
Eventually I get the printer to work!

My /etc/network/interfaces file was almost empty.

So I found another solution:

I ran ```
sudo ifconfig eth0 netmask 255.0.0.0
```
then
```
sudo route add -net 0.0.0.0 gw 10.31.0.1
```
and now the printer is working like it should! :D
Thank you so much for your precious help :)

By the way, I noticed that I lose this setting on reboot...
Did I have to add them to /etc/network/interfaces to load them at 
startup?

---

### Post by houstonbofh on 2013-10-18
Compare the /etc/network/interfaces on each machine.  That is the boot config, so yes, fixing it there fixes it for good.

---

