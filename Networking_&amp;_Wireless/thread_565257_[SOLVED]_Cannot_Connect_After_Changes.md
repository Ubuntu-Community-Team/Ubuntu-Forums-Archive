---
title: "[SOLVED] Cannot Connect After Changes"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by mlissner on 2007-10-02
I can't seem to get my server to connect to the internet. It's running on CLI only, and should have a static IP associated with it. I'm utterly baffled as to why this problem has begun, as I have not changed anything to my knowledge on this computer.

I have checked that the cable going into the server works, but for some reason the computer just won't get going.

If it helps, here're some outputs:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:B0:D0:7B:82:A2  
          inet addr:192.168.1.132  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2b0:d0ff:fe7b:82a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:261800 (255.6 KiB)  TX bytes:151298 (147.7 KiB)
          Interrupt:17 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17124 (16.7 KiB)  TX bytes:17124 (16.7 KiB)

```

```
more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.1.132
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

```
 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

Does anybody see anything that might help be debug this issue? Thank you, and I apologize if you have seen my other post on this subject, but that one is out of control, and full of accidental red herrings at this point.

Thanks.

---

### Post by helgman on 2007-10-05
I've read through your other thread as well, if it's [this one](http://ubuntuforums.org/showthread.php?t=563315) you are talking about.

If I understand the problem correctly you have a servers on a LAN connected to a modem that is using NAT against Internet and the problem is that the server can't access or be accessed from "the Net".

You manually configured a static IP address on the server.

Since your computer uses a [private IP address](http://en.wikipedia.org/wiki/Private_network) it can't be accessed from the Internet without your modem doing a [port forward](http://en.wikipedia.org/wiki/Port_forwarding) to you server.

This, however, should not affect your servers ability to reach the Internet.

I find no information in your post(s) about DNS settings. Can you do a look up  of [www.google.com?](www.google.com?)
```
nslookup www.google.com
```
I saw some references to DNS in the other thread but I didn't figure out if you where running a server of your own or if it was the modem serving you.

Let me know how things work out.

Regards,
Helgman

---

### Post by mlissner on 2007-10-06
Yep, that was the thread I was referring to...good detective work. It hasn't been easy, but I have gotten this fixed. I dealt with my broadband provider and Linksys, and apparently the router needed to register the MAC address of the primary computer with the modem...as if that makes any sense.

Once that was done, everything starting working like a champ. I am so glad this is fixed.

Thanks for the help though. I am amazed anybody was able to figure this out.

---

