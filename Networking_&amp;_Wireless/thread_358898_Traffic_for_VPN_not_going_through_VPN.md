---
title: "Traffic for VPN not going through VPN"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by alkaboy on 2007-02-11
Hello,

I am trying to get connected to my corporate VPN. I have tried using both vpnclient and vpnc. I can successfully connect to both. However, once the connection is fully established and up and running, my attempts to connect to, for example, my corporate website, do not succeed. Can someone by chance help me debug this issue?

Thanks!

---

### Post by spd106 on 2007-02-11
Maybe check the routing table to make sure the network packets are going to be routed through the tunnel. Use **ifconfig** for identifying the tunnel network, then **ip route** for the routing table.
You should be okay to have the default route directed out through the normal Internet connection, but it may be better to direct it through the tunnel, at least temporarily. Make sure that you have only one default route, this is a common problem and can cause instabilities in network access.

---

### Post by alkaboy on 2007-02-11
I have VMware working as well, and I have figured out that the traffic from VMware can successfully go through the VPN, but not Firefox in Ubuntu. Any idea how I can change this routing?

---

### Post by alkaboy on 2007-02-12
I have tried removing VMware (all I used it for was to connect to vpn ;) ) and I still cannot seem to have the routing issue solved. Can someone please help me set the routes correctly on my vpn? I am not familiar with using 'ip'.

Thanks

---

### Post by alkaboy on 2007-02-19
Here is the output from "ip route":

199.242.6.131 via 192.168.1.1 dev eth1 
192.168.196.0/24 dev cipsec0  proto kernel  scope link  src 192.168.196.1 
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.103 
165.177.0.0/16 via 192.168.196.1 dev cipsec0  scope link 
169.242.0.0/16 via 192.168.196.1 dev cipsec0  scope link 
172.16.0.0/13 via 192.168.196.1 dev cipsec0  scope link 
22.0.0.0/8 via 192.168.196.1 dev cipsec0  scope link 
25.0.0.0/8 via 192.168.196.1 dev cipsec0  scope link 
45.0.0.0/8 via 192.168.196.1 dev cipsec0  scope link 
default via 192.168.1.1 dev eth1 

And the output from "ifconfig":

cipsec0   Link encap:Ethernet  HWaddr 00:0B:FC:F8:01:8F  
          inet addr:192.168.196.1  Mask:255.255.255.0
          UP RUNNING NOARP  MTU:1356  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:7 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:12:0E:08:19:AD  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6538 errors:424 dropped:0 overruns:0 frame:424
          TX packets:6531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5342356 (5.0 MiB)  TX bytes:948477 (926.2 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13082 (12.7 KiB)  TX bytes:13082 (12.7 KiB)


Does anyone out there at first glance know how I need to set up my IP routes? Any help would be *greatly* appreciated. Thanks!!

---

### Post by alkaboy on 2007-02-19
As a follow-up, it looks like things might be routed properly, but no response from external vpm-server?

Running "tracepath www.google.com"
 1:  192.168.1.103 (192.168.1.103)                          0.159ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                            asymm 36   2.366ms 
 2:  192.55.2.1 (192.55.2.1)                                6.444ms 
 3:  msfc40core-206v.bfm.com (172.16.206.1)                17.126ms 
 4:  168.215.100.229 (168.215.100.229)                    asymm  5  21.420ms 
 5:  core-01-ge-0-1-1-510.nycl.twtelecom.net (66.192.253.64) asymm  6  18.587ms 
 6:  peer-02-so-0-0-0-0.nycl.twtelecom.net (66.192.240.198) asymm  7  18.627ms 

Running "tracepath <internal corporate website>":
 1:  192.168.196.1 (192.168.196.1)                          0.160ms pmtu 1390
And then it just hangs.

Anyone?

---

### Post by spd106 on 2007-02-20
It could be a DNS issue. Can you connect to the web server directly with it's IP address?

---

### Post by alkaboy on 2007-02-22
I'm not exactly sure of the web server's IP address, but when I attempt to connect to the corporate homepage (i.e. with tracepath), it knows to try to get the traffic through the tunnel

---

### Post by alkaboy on 2007-02-22
Additionally, i'm using vpnc with --udp now

---

