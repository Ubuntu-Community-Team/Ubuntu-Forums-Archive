---
title: "Frequent packet loss, frequent connection failure on Ubuntu 12.04 and WiFi"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by nmayer1994 on 2013-12-30
Hey all,

I frequently experience high packet loss(anywhere from 10% to 70%) for extended periods of time, and I am frequently unable to access websites at all. It I am fairly certain that this is not a hardware problem, as my Windows boot on the same machine can access the internet quickly and reliably. I have done research and tried to fix it, but I can't seem to have any lasting success. I will post a few things which I have seen requested in other threads. Thanks in advance for whatever help you can give, I'm pretty lost.

1) Ping website (internet is working right now)
```

$ping -c4 google.com
PING google.com (74.125.239.33) 56(84) bytes of data.
64 bytes from nuq04s19-in-f1.1e100.net (74.125.239.33): icmp_req=1 ttl=53 time=101 ms
64 bytes from nuq04s19-in-f1.1e100.net (74.125.239.33): icmp_req=2 ttl=53 time=54.8 ms
64 bytes from nuq04s19-in-f1.1e100.net (74.125.239.33): icmp_req=3 ttl=53 time=49.7 ms
64 bytes from nuq04s19-in-f1.1e100.net (74.125.239.33): icmp_req=4 ttl=53 time=49.0 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 49.064/63.881/101.848/22.032 ms

```

2) Ping WiFi Router
```

$ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_req=1 ttl=255 time=33.5 ms
64 bytes from 192.168.1.254: icmp_req=2 ttl=255 time=18.5 ms
64 bytes from 192.168.1.254: icmp_req=3 ttl=255 time=52.5 ms
^C
--- 192.168.1.254 ping statistics ---
5 packets transmitted, 3 received, 40% packet loss, time 4011ms
rtt min/avg/max/mdev = 18.504/34.885/52.575/13.941 ms

```

3) ifconfig output
```

$ifconfig
eth0      Link encap:Ethernet  HWaddr 64:31:50:5c:d8:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104301 (104.3 KB)  TX bytes:104301 (104.3 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:84:11:1d  
          inet addr:192.168.1.76  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe84:111d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7093370 (7.0 MB)  TX bytes:1764435 (1.7 MB)

```

---

### Post by Bucky Ball on 2013-12-30
Welcome. What have you done to try and fix it?

Please give the output of this:

```
sudo lshw -C network
```

Have you compared the details in your wireless config in Network Manager with the details of the wireless config in Windows? Are they exactly the same details? No anomalies?

---

### Post by nmayer1994 on 2013-12-31
To try and fix it, I mostly tested a lot of things. I tried to see if there was some network protocol error (IPv4 vs IPv6), I tried to see if my IP address wasn't correct for the address of my router. I actually changed the IP address on my computer, which fixed some of my problems. If I ever lose connection entirely, forgetting the network and relogging in usually fixes it temporarily. Here is the output you wanted:

```
 
 *-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:84:11:1d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.5.0-44-generic firmware=N/A ip=192.168.1.76 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:93500000-93503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 64:31:50:5c:d8:a7
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:91410000-91410fff memory:91400000-9140ffff memory:91420000-9142ffff

```

Thanks for the quick reply!

---

### Post by Bucky Ball on 2013-12-31
So you are using a static IP address now? Are you using one in Windows? In Network Manager, in the IPv6 tab, do you have that set to 'Ignore'? Is 'Available to all users' and 'Automatically Connect' enabled in there?

---

### Post by nmayer1994 on 2013-12-31
I apologize for my complete lack of networking or IT knowledge. I suppose I must be using a static IP in Ubuntu, as I set it manually. I have no idea how to find that out in Windows, but I haven't meddled with anything in there so whichever is standard is probably the current setting. And as for the other two questions, I seem to be having difficulty finding a "Network Manager." I tried the "Network" tab in "System Settings," and I tried "Network Tools," but I can't find anything which has the IPv6 tab which you referenced. Sorry again for my ignorance.

---

### Post by Bucky Ball on 2013-12-31
If you right click on the network icon you should get to option to 'Edit Connections'.

I have checked and you appear to be using the right driver for that card so all good there. Must be something else stalling things. :-k

How did you set the static IP in Ubuntu manually if not through network manager? If you set it on the router, unset it so the router is set to serve an IP via its DHCP server (which is what is happening for Windows if you haven't set up a static IP there).

---

