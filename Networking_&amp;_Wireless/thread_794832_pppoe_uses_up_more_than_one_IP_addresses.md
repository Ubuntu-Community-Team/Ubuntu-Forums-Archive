---
title: "pppoe uses up more than one IP addresses"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by sistoviejo on 2008-05-15
I have a little home server running Ubuntu Hardy Heron. It's also running dhcpd3 and a bind name server. Also it does NAT for the rest of the computers on my home network and dials pppoe to my adsl provider. So basically it works as a router.
My ISP gives me up to two connections on the same modem with two different dynamic IP addresses. 
[COLOR="DarkRed"]My problem is that sometimes this server dials twice and has two different public IP addresses.
[/COLOR]When this happens, all the computers that access the Internet through the server, have no Internet access.

I need to connect another computer directly to the Internet, so that this one connects only once. Sometimes this other computer is switched off. Is it possible to make it dial only once without the need of a second computer directly connected to the Internet?

Note: 
I am also using PPP Tray Icon 0.2 on this computer.

Here's an example of what it does:
```

silvio@xxxxx:~$ ifconfig
eth0      Link encap:Ethernet  
          inet addr:192.168.x.x  Bcast:192.168.x.x  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3814692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3809380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:115829 txqueuelen:1000 
          RX bytes:2359011231 (2.1 GB)  TX bytes:2341651768 (2.1 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:224844 (219.5 KB)  TX bytes:224844 (219.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:190.135.x.x  P-t-P:190.64.x.x  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3073 (3.0 KB)  TX bytes:4102 (4.0 KB)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:190.135.x.x  P-t-P:190.64.x.x  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2382 (2.3 KB)  TX bytes:887 (887.0 B)

Note: IPv6 addresses were removed and IPv4 addresses are masked with "x"s.
```

Here's the contents of my /etc/ppp/peers/dsl-provider file:
```

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth0
usepeerdns
user "****@****"

Note: Username was masked with "*"s.
```

Any help will be appreciated!!
Thank you.

---

### Post by sistoviejo on 2008-05-25
anyone?

---

