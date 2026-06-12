---
title: "No wifi after pppoeconf"
date: 2014-11-22
forum: Networking &amp; Wireless
---

### Post by hariks0 on 2014-11-22
Hi,

I was using BSNL Wimax internet with a Dlink modem-cum-router DSL2730U. I connect the Wimax modem cable to one of the output [yes,output as it can be used both as input and output] ports of the router and use Internet in the PC over lan cable as well as in mobiles/tablet over wifi. Since the connection was very slow, I took a new FTTH connection. As the FTTH was provided as PPPOE, I configured the connection by ```
sudo pppoeconf
``` The FTTH modem was connected to the DLink modem-cum-router as earlier. 
[LIST]
[*]Now the PC can connect to Internet over lan cable but the wifi does not connect.
[*]The PC also has the network icon disabled even though it is connected to Internet.
[*]The same configuration still works well for BSNL wimax for both lan cable and wifi.
[*]I cannot access the modem with 192.168.1.1 in browser
[/LIST]


The contents of /etc/ppp/peers/dsl-provider
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
user "userid"
usepeerdns
```

The original file does not have the last 3 lines. The network configuration details are :```
hari@Indira:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:d1:a7:15:66  
          inet6 addr: fe80::219:d1ff:fea7:1566/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5757 errors:0 dropped:19 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:556280 (556.2 KB)  TX bytes:13371 (13.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:15449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1211595 (1.2 MB)  TX bytes:1211595 (1.2 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.24.118  P-t-P:192.168.22.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1480  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:8980 (8.9 KB)  TX bytes:5922 (5.9 KB)

```

What is to be done for using net over lan as well as wifi? Thanks in advance !

---

