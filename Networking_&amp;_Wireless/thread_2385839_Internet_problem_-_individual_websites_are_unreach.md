---
title: "Internet problem - individual websites are unreachable"
date: 2018-02-25
forum: Networking &amp; Wireless
---

### Post by bart.paszkiewicz on 2018-02-25
Hello Everyone!
I'm new here, so please forgive me if I did something wrong :)

I've encountered a problem in Xubuntu LTS that I can't overcome.

Generally the internet connection is established and works ok. Sites like Google are reachable. 
The problem occurs with for example the homepage of my ISP ([www.netia.pl]("http://www.netia.pl")). Everytime I try to load this page, the connection is timed out.
I use latest Firefox. The connection is using PPPoE. The DNS is by default 127.0.1.1. 

ping -c3 netia.pl:
```

PING netia.pl (87.204.19.8) 56(84) bytes of data.


--- netia.pl ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2043ms
 

```

lshw
```

  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 01
       serial: 00:17:31:ee:cb:b0
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:27 ioport:c800(size=256) memory:ddeff000-ddefffff memory:ddee0000-ddeeffff 

```

ifconfig
```

enp2s0    Link encap:Ethernet  HWaddr 00:17:31:ee:cb:b0  
          inet6 addr: fe80::82eb:7b74:37c5:8ab9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24127 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32879809 (32.8 MB)  TX bytes:4153783 (4.1 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:308839 (308.8 KB)  TX bytes:308839 (308.8 KB)


ppp0      Link encap:Point-to-Point Protocol  
          inet addr:77.253.120.29  P-t-P:83.238.252.81  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:32130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:32165437 (32.1 MB)  TX bytes:3619225 (3.6 MB)
 

```

traceroute -I netia.pl
```

traceroute to www.netia.pl (87.204.19.8), 30 hops max, 60 byte packets
 1  83.238.252.81 (83.238.252.81)  29.445 ms  29.431 ms  32.543 ms
 2  83.238.113.44 (83.238.113.44)  34.990 ms  42.875 ms  42.901 ms
 3  WarsH002RT22-WarsH002SW30.inetia.pl (213.241.2.222)  40.162 ms  42.628 ms  45.275 ms
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * * 

```

In addition:

edit: /etc/NetworkManager/NetworkManager.conf 
```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false 

```

edit: /var/lib/NetworkManager/NetworkManager.state 
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true 

```

edit: /etc/network/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback 

```


Thanks in advance for your help. Please have in mind that I don't have 24/7 access to the computer this problem is related to. If any additional logs are required I'll try to provide them asap, but it'll probably take a while. 
Have a nice day!

---

### Post by gordintoronto on 2018-02-25
What command produced the response which included dnsmasq?  

Is your wireless ipv4 set to DHCP?

---

### Post by bart.paszkiewicz on 2018-02-26
> **gordintoronto said:**
> What command produced the response which included dnsmasq? [COLOR=#000000]
[/COLOR]
I've edited the first post and included the sources of information. 

> **gordintoronto said:**
> 
Is your wireless ipv4 set to DHCP?
 I don't know whether the wireless ipv4 is set to DHCP or not, I don't know how to check it. Please give me a hint.

In addition I installed the same xubuntu on a VM on a different PC (Windows 10 as a host) and despite Windows having no problems with the internet connection, on the VM xubuntu there is exactly the same problem as on the computer mentioned in the first post.
edit: on the VM firefox is able to open [www.netia.pl]("http://www.netia.pl"), but ping -c3 netia.pl still gives exactly the same result as in the main case.

---

