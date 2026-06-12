---
title: "[SOLVED] IP change results in partial network connectivity"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by SimonC78 on 2008-03-25
Hi all,

I recently changed my network ip address to allow me to connect to a couple of different VPN's without conflict from anything else. Old network was 192.168.0.x, new is 10.100.1.x. I've made the necessary changes in /etc/network/interfaces, and now I don't have any connectivity with the outside world. I can ping all the machines/routers/etc inside the network, including the gateway, however i can't get out via the web, nslookup, ping, etc.

Any idea's would be greatly appreciated. Am running 7.10 server.

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 10.100.1.11
        netmask 255.255.255.0
        network 10.100.1.0
        broadcast 10.100.1.255
        gateway 10.100.1.1
        dns-nameservers 10.100.1.1

```

ifconfig -a:
```

eth0      Link encap:Ethernet  HWaddr 00:0D:9D:4A:A3:42
          inet addr:10.100.1.11  Bcast:10.100.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:35736 (34.8 KB)  TX bytes:38969 (38.0 KB)
          Interrupt:20

```

route:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.100.1.0      *               255.255.255.0   U     0      0        0 eth0
default         10.100.1.1      0.0.0.0         UG    100    0        0 eth0

```

---

### Post by SimonC78 on 2008-03-25
Solved. DNS needed to be updated in /etc/resolv.conf.

Sorry for the lame Q!

---

### Post by beatbros on 2008-03-25
Hi,
if you can ping & browse by using IP Address below the problem is name resolution.
I've seen that in your network configuration you set up :dns-nameservers 10.100.1.1 
Is it your router/gateway set up to forward DNS Queries to real DNS servers?


Name:	[www.l.google.com](www.l.google.com)
 Address: 209.85.135.99
 Name:	[www.l.google.com](www.l.google.com)
 Address: 209.85.135.103
 Name:	[www.l.google.com](www.l.google.com)
 Address: 209.85.135.104
 Name:	[www.l.google.com](www.l.google.com)
 Address: 209.85.135.147

---

### Post by beatbros on 2008-03-25
Ah ok...

simple ! :=)

bye

---

