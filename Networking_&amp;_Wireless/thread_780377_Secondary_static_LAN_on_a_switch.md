---
title: "Secondary static LAN on a switch"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by chowdah45416 on 2008-05-03
I have been searching all over for an answer to this question, which I thought was common, but I haven't found it yet.  I have a set of 5 servers connected through a switch somewhere, and it all works fine.  However, I only can get a slow connection this way, so I wanted to add a second network for just these 5 machines with a gigabit switch.  I tried setting them up with static IPs in the same subnet (10.0.0.0/24), but they can't seem to ping each other.  There is no gateway that is set, but I didn't think that would matter in this situation.  Does anyone have any other ideas on what I am missing?  Thanks.

---

### Post by mips on 2008-05-03
Look into nick bonding or configure the secondary adapters for a different subnet.

---

### Post by chowdah45416 on 2008-05-03
By the same subnet I meant the second network for all the servers is the same.  It is a different subnet for the primary connection.  I want to keep the two networks separate from each other.  The secondary network would only come into play if the servers were to try and connect to something on 10.0.0.0/24.

---

### Post by mips on 2008-05-03
Give a server config example please. also output of route -n

---

### Post by chowdah45416 on 2008-05-03
My interfaces file looks like this:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.204.106.132
netmask 255.255.255.240
gateway 192.204.106.129


# Gigabit
auto eth1
iface eth1 inet static
address 10.0.0.2
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1

```

I've tried this with and without the gateway, network, and broadcast specified.

My routing table is:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.204.106.128 0.0.0.0         255.255.255.240 U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.204.106.129 0.0.0.0         UG    100    0        0 eth0

```

---

### Post by chowdah45416 on 2008-05-09
I'm not sure if this adds anything, but I am also not able to ping a local machine at it's 10.0.0.0/24 IP address.

---

### Post by koenn on 2008-05-09
> **chowdah45416 said:**
> I'm not sure if this adds anything, but I am also not able to ping a local machine at it's 10.0.0.0/24 IP address.

ar both interfaces up ? show output of ```
ifconfig
```

---

### Post by chowdah45416 on 2008-05-09
Yes, they're both up just fine.  Note that eth1 (which is the secondary network) is transmitting but not receiving.  The other two machines I have up so far are neither transmitting or receiving, and they don't show "RUNNING", even though they are all configured identically.

```
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:96:F9:D9  
          inet addr:192.204.106.132  Bcast:192.204.106.143  Mask:255.255.255.240
          inet6 addr: fe80::21d:7dff:fe96:f9d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:695897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:796938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61775501 (58.9 MB)  TX bytes:75949903 (72.4 MB)
          Interrupt:23 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:1B:21:18:7B:7D  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fe18:7b7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:527000 (514.6 KB)
          Base address:0xcf00 Memory:fdcc0000-fdce0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17768701 (16.9 MB)  TX bytes:17768701 (16.9 MB)

```

---

### Post by mips on 2008-05-10
Your configs look fine to me.

What happens if you do traceroutes from one device to another device in the 10 & 192 networks in both directions? 10.->10. 10.->192. 192.->10. 192.->192. Use source and destination addresses, traceroute allows for this and post the output here.

Do you have any weird iptables setups on your servers?

What brand and model are the new 10. LAN adapters?

---

### Post by chowdah45416 on 2008-05-10
```

$ traceroute -s 10.0.0.2 10.0.0.5
traceroute to 10.0.0.5 (10.0.0.5), 30 hops max, 40 byte packets
 1  10.0.0.2 (10.0.0.2)  3008.766 ms !H  3008.764 ms !H  3008.759 ms !H

$ traceroute -s 10.0.0.2 192.204.106.135
traceroute to 192.204.106.135 (192.204.106.135), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *

$ traceroute -s 192.204.106.132 10.0.0.5
traceroute to 10.0.0.5 (10.0.0.5), 30 hops max, 40 byte packets
 1  apollo.ucacm.org (192.204.106.132)  3017.165 ms !H  3017.161 ms !H  3017.155 ms !H

$ traceroute -s 192.204.106.132 192.204.106.135
traceroute to 192.204.106.135 (192.204.106.135), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *

```

I hadn't thought about my iptables, but I made the change and it that didn't make a difference.  lspci gives me "Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)."

The problem must have something to do with the other computers.  I have one that seems to be transmitting, but the other two don't seem to be working yet.  I get "link is not ready" messages in the system log, and it definitely doesn't seem to be running from the `ifconfig`.  Any idea on what else I might need to do to get them working?

---

### Post by chowdah45416 on 2008-05-25
Just as a final update, the problem turned out to be with the card working properly on the server.  I had the kernel 2.6.15 installed on the server where the card didn't work right, and 2.6.22 was installed on the server where the card worked.  After upgrading the kernel, everything worked fine.  Thanks for all the help.

---

