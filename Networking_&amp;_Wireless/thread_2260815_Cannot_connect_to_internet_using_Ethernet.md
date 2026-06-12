---
title: "Cannot connect to internet using Ethernet"
date: 2015-01-14
forum: Networking &amp; Wireless
---

### Post by Carloscgp on 2015-01-14
Hello all,

I just built my first computer and installed Linux 14.04 Trusty Tahr on it without any problems. When I tried to connect to the internet using an Ethernet cable it failed. Network Manager keeps trying to connect but it fails and disconnect over and over again. 

Here is the first ifconfig result:

[COLOR=#141823][FONT=Helvetica]eth0 Link encap:Ethernet HWaddr fc:aa:14:09:73:95 [/FONT][/COLOR][COLOR=#141823][FONT=Helvetica]
inet6 addr: fe80::feaa:14ff:fe09:7395/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:373 errors:0 dropped:7 overruns:0 frame:0
TX packets:33 errors:0 dropped:3085 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:54159 (54.1 KB) TX bytes:3158 (3.1 KB)

eth0: avahi Link encap:Ethernet HWaddr fc:aa:14:09:73:95 
inet addr:169.254.6.163 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:2613 errors:0 dropped:0 overruns:0 frame:0
TX packets:2613 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:214923 (214.9 KB) TX bytes:214923 (214.9 KB)

After that I tried setting up the network manually and I managed to connect to it, but there's no internet connection.

ifconfig after setting up mannually:
eth0 Link encap:Ethernet HWaddr fc:aa:14:09:73:95 
inet addr:192.168.1.12 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::feaa:14ff:fe09:7395/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:419 errors:0 dropped:7 overruns:0 frame:0
TX packets:39 errors:0 dropped:3837 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:58019 (58.0 KB) TX bytes:4181 (4.1 KB)

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:2901 errors:0 dropped:0 overruns:0 frame:0
TX packets:2901 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:238193 (238.1 KB) TX bytes:238193 (238.1 KB)

and route results: 

Destination Gateway Genmask Flags Metric Ref Use Iface
default         192.168.1.1 0.0.0.0 UG    0         0     0     eth0
192.168.1.0 *             255.255.255.0 U 1         0    0     eth0

Tried connect my laptop using the ethernet cable and it worked fine. Anyone has any ideas on how to solve this? Thank you in advance.[/FONT][/COLOR]

---

### Post by mikewhatever on 2015-01-14
What makes you think that it failed? It got an IP in both cases, which should be considered a success.

---

### Post by Carloscgp on 2015-01-14
Well, yes, but I still can't connect to the Internet.

---

### Post by Bashing-om on 2015-01-14
Carloscgp; Hello ....

Can you talk to your router (gateway) ?
```

ping -c3 192.168.1.1

```
[my default address is 192.168.0.1]

Yes , Then can you get out of house ?
```

ping -c3 8.8.8.8

```
Yes ? .. Then we looking at a DNS issue .. 

[INDENT][INDENT]to be continued
[/INDENT][/INDENT]

---

### Post by Carloscgp on 2015-01-15
I have tried pinging my router but got 'Destination Host Unreachable'. Tried using linux from the usb stick, and I still had the same problem, so I don't think it is a installation fault.

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.From 192.168.1.12 icmp_seq=1 Destination Host Unreachable
From 192.168.1.12 icmp_seq=2 Destination Host Unreachable
From 192.168.1.12 icmp_seq=3 Destination Host Unreachable



```

---

### Post by Carloscgp on 2015-01-15
Also tried using a live USB with Ubuntu 12.04.5 and got the same problem.

---

### Post by Sally_Joshua on 2015-01-15
[h=2]Configure your connection settings in NetworkManager[/h]

---

### Post by Bashing-om on 2015-01-15
Carloscgp; Humm ...

Something is not configured ... OR we have our wires crossed.
Consider:
> 
After that I tried setting up the network manually and I managed to connect to it, but there's no internet connection.

ifconfig after setting up mannually:
eth0 Link encap:Ethernet HWaddr fc:aa:14:09:73:95 
inet addr:[color=red]192.168.1.12[/color]

but you say the 'default' gateway is:
> 
Destination Gateway Genmask Flags Metric Ref Use Iface
default [color=red]192.168.1.1[/color]


So yeah. let's continue and see about setting up a manual internet connection:

Is the card good ?
```

ping -c3 127.0.0.1

```
Is Network Manager disabled - such that we will use our config files  ?
```

cat /etc/NetworkManager/NetworkManager.conf

```

And now what is in the 'manual' config ?
```

cat /etc/network/interfaces

```

Try and find out what is not going on .

[INDENT][INDENT]IF you can not talk to your router,
[INDENT][INDENT][INDENT][INDENT]can not talk to anyone 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

