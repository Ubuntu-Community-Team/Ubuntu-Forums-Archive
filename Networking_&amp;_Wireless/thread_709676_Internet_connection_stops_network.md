---
title: "Internet connection stops network"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by geoffrymoose on 2008-02-27
Hi there,

I have two i386 Ubuntu 7.10 machines running happily (Lets call them pc1 and pc2). They are networked with a hub between them and can see each other fine (Pink OK).

pc1 can connect to the internet through a USB Modem. I have two methods of making a connection: either a script in terminal or a GUI launcher "driver", both work fine and there are no problems.

**However:** If i connect pc1 to the internet with the USB Modem (using either method), I can no longer get the machines to see each other (no longer Ping). I'm trying to share the internet connection but seem to have a situation where i can *either* have a LAN connection or an internet connection not both. If I stop the modem connection the machines will happily Ping away but if I start the modem up again, they stop.

Any thoughts/ideas would be greatly appreciated.

---

### Post by lloyd_b on 2008-02-27
> **geoffrymoose said:**
> Hi there,

I have two i386 Ubuntu 7.10 machines running happily (Lets call them pc1 and pc2). They are networked with a hub between them and can see each other fine (Pink OK).

pc1 can connect to the internet through a USB Modem. I have two methods of making a connection: either a script in terminal or a GUI launcher "driver", both work fine and there are no problems.

**However:** If i connect pc1 to the internet with the USB Modem (using either method), I can no longer get the machines to see each other (no longer Ping). I'm trying to share the internet connection but seem to have a situation where i can *either* have a LAN connection or an internet connection not both. If I stop the modem connection the machines will happily Ping away but if I start the modem up again, they stop.

Any thoughts/ideas would be greatly appreciated.

Could you post the output from the following terminal commands (twice please - once with just the LAN, and again with the internet connection active):
```
ifconfig 
route -n
```

I suspect that when the internet connection comes up, it's changing the routes so that the computer no longer knows it needs to use the ethernet device to reach the other PC.  Hopefully, the output of the above commands will provide a possible explanation for why (my guess at this point is that both are using the same subnet, but that's just a guess based on insufficient information).

Lloyd B.

---

### Post by Iowan on 2008-02-27
I wonder if there's an addressing issue - **ifconfig** and/or contents of **/etc/network/interfaces** file should help (per lloyd_b's suggestion)

---

### Post by geoffrymoose on 2008-02-27
Hi there and thank you for the response.

Output below:

**ifconfig from pc1 with no internet connection**:

geoffry@Moose:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:F1:42:F0  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fef1:42f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4212 (4.1 KB)  TX bytes:6367 (6.2 KB)
          Interrupt:18 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8640 (8.4 KB)  TX bytes:8640 (8.4 KB)

**ifconfig from pc1 with internet connection:**

geoffry@Moose:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:F1:42:F0  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fef1:42f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7625 (7.4 KB)  TX bytes:7090 (6.9 KB)
          Interrupt:18 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9792 (9.5 KB)  TX bytes:9792 (9.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:121.90.86.83  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:304 (304.0 b)  TX bytes:239 (239.0 b)

**route -n from pc1 with no internet connection:**

geoffry@Moose:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

**route -n from pc1 with internet connection:**

geoffry@Moose:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

**Info from pc2 (JIC is useful):**

little@Little:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:0A:3E:A3  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe0a:3ea3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4093 (3.9 KB)  TX bytes:14138 (13.8 KB)
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1867 (1.8 KB)  TX bytes:1867 (1.8 KB)

little@Little:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
little@Little:~$

---

### Post by geoffrymoose on 2008-02-28
and contents of etc/network/interfaces:

auto lo
iface lo inet loopback



iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0



auto eth1

iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0

auto eth0

The eth1 card is currently disabled in BIOS. The problem is the same regardless of eth1's state.

---

### Post by lloyd_b on 2008-02-28
Okay, my first guess was wrong (not too unusual, btw).

The only thing that jumps out at me is that the default route that's added after you start PPP (the one starting "0.0.0.0") doesn't specify a gateway, which is different from what I expected.  But then it's been many years since I used PPP, so I can't say that it's wrong...

Experiment - after bringing up PPP:
```
sudo route del default
ping 192.168.1.3
```
and see if that works.

Also - could you post the contents of the script you run to start up the modem?

Lloyd B.

---

### Post by Talks_44 on 2008-02-28
I think it is about ISP.. this problem is often meet to more internet users..ISP is being caused by their bag connection...

---

### Post by geoffrymoose on 2008-02-28
Hi there,

Um... not sure how to say this but it was the firewall Firestarter (has option "Allow internet connection sharing" switched off as default).

Up till now i had been using the Ping function of network Tools as it was easier to just keep that window open on the second desktop and swap to it when I wanted to test. When I read the reply above I tried Ping in the terminal as suggested and got an error : "ping: sendmsg: Operation not permitted".

Not permitted is alot different from simply doesn't work and from there I realized something was stopping it deliberately and from there i thought of the firewall.

Thank you so much for your time and responses, I've learned alot about subnets and routing and, of course, to properly investigate a fault by looking for simple causes first!

Geoffry

---

