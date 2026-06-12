---
title: "pptp client huge packets TX ???"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by kkfok1 on 2008-09-07
Hi,

[B]The following happening is puzzling me :

What will cause such huge number packets being sent within such short time ? 
And
What are these packets contain ?

Packets captured : 2964470
Between first and last packet : 107.120 sec
Avg packet per sec : 27674.344
Avg packet size : 373.261
Bytes : 1106520024
Avg bytes per sec : 10329743.866
Avg Mbit/s : 82.638

Any help is much appreciated[/B]

 linux-generic 2.6.24.19.21
 ppp 2.4.4rel-9ubuntu2
 pptp-linux 1.7.0-2ubuntu2

I have connected to a VPN server 10.24.0.1 via pptp by using KVpnc (0.9.0) GUI. However, when I tried to change to route traffic to this VPN tunnel, I starting to see the TX bytes count of the ppp0 is increasing exponentially which cause the VPN server drop the connection. Am I doing something wrong or it is a ppp0 or pptp bug ?

You can see within 5 sec, the TX increase from 116byte to 11.1MB, and another 5 sec from 11.1MB to 71.9MB, another 5 sec from 71.9MB to 134.8MB and within 1 minute 15 sec the TX byte count from 116bytes to 807.6MB ???

A side note is the ping [www.google.com](www.google.com) just hang (no reply) after I switch the route.

Following is the capture I have which shows ifconfig ppp0 and route -n with a time stamp :

Sun Sep 7 17:30:52 MYT 2008
ppp0 Link encap:Point-to-Point Protocol
          inet addr:10.24.51.150 P-t-P:10.24.0.1 Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1488 Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:122 (122.0 B) TX bytes:116 (116.0 B)

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
10.24.0.1 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
192.168.2.0 0.0.0.0 255.255.255.0 U 0 0 0 wlan0
0.0.0.0 192.168.2.1 0.0.0.0 UG 0 0 0 wlan0
********************
Sun Sep 7 17:30:57 MYT 2008
ppp0 Link encap:Point-to-Point Protocol
          inet addr:10.24.51.150 P-t-P:10.24.0.1 Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1488 Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:122 (122.0 B) TX bytes:116 (116.0 B)

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
10.24.0.1 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
192.168.2.0 0.0.0.0 255.255.255.0 U 0 0 0 wlan0
0.0.0.0 192.168.2.1 0.0.0.0 UG 0 0 0 wlan0
********************
Sun Sep 7 17:31:02 MYT 2008
ppp0 Link encap:Point-to-Point Protocol
          inet addr:10.24.51.150 P-t-P:10.24.0.1 Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1488 Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:238 (238.0 B) TX bytes:11642203 (11.1 MB)

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
10.24.0.1 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
192.168.2.0 0.0.0.0 255.255.255.0 U 0 0 0 wlan0
0.0.0.0 10.24.0.1 0.0.0.0 UG 0 0 0 ppp0
********************
Sun Sep 7 17:31:07 MYT 2008
ppp0 Link encap:Point-to-Point Protocol
          inet addr:10.24.51.150 P-t-P:10.24.0.1 Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1488 Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:238 (238.0 B) TX bytes:75469044 (71.9 MB)

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
10.24.0.1 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
192.168.2.0 0.0.0.0 255.255.255.0 U 0 0 0 wlan0
0.0.0.0 10.24.0.1 0.0.0.0 UG 0 0 0 ppp0


I have tried to confirm if there is really such huge data being TX so I use tcpdump and I found the below statistics.

From the tcpdump using wireshark for the summary is as below :

Packets captured : 2964470
Between first and last packet : 107.120 sec
Avg packet per sec : 27674.344
Avg packet size : 373.261
Bytes : 1106520024
Avg bytes per sec : 10329743.866
Avg Mbit/s : 82.638

Almost all are packet like below :
3 0.000014 192.168.2.2 61.238.150.146 PPP Comp Compressed data

I am no expert in using wireshark. If you need the dump, please let me know I can send to you but it is really big. May be you can advise me how to export just a few packets.

I am very interesting to know what are these packets and how could they being sent out (if it is true, as I still cannot believe this)

Any help is much appreciated.

---

### Post by mantissacoder on 2009-09-25
Hi there,

Were you able to eventually figure out what the issue was? 

I'm encountering the same..

---

### Post by mantissacoder on 2009-09-26
> **mantissacoder said:**
> Hi there,

Were you able to eventually figure out what the issue was? 

I'm encountering the same..

Nevermind, the following pretty much addressed it:

[http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lots_of_data](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lots_of_data)

---

