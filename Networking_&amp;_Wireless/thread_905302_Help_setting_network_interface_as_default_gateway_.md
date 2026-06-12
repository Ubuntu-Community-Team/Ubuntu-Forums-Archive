---
title: "Help setting network interface as default gateway to the internet?"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by sputty01 on 2008-08-30
Hi fellow ubuntuians! i go on vacation to the US tomorrow so im wanting to use my mobile phone as a modem to get some net access while im out there (yes i sad and cant live 2 weeks without it :razz:), ive got it set up and connected ok with kppp (i had issues with gnome ppp not playing nicely with my phone) but my laptop doesnt seem to recognise its connected and wont let me use the connection to talk to the outside world.

My wireless connection works fine when thats connected and my ethernet also works fine.. but it refuses to use the ppp connection for the internet for some reason. Ive tried to add as much info as i can below and anyone who could lend a hand would be a life saver :) 


Below is my ifconfig output if thats any help :)
```
sputty01@mintydoom ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:6e:66:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x2020 Memory:e0600000-e0620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9688 (9.4 KB)  TX bytes:9688 (9.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.106.61.210  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:118 (118.0 B)  TX bytes:157 (157.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.224.1  Bcast:172.16.224.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.118.1  Bcast:172.16.118.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:0c:43:e4  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:233544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:287898643 (274.5 MB)  TX bytes:18427969 (17.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-0C-43-E4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

The interface im wanting it to use is the ppp0 one.. but i dont get a response from my pings and firefox wont show pages. Thanks in advance :)

---

### Post by solar george on 2008-08-30
Please post the results of ```
route -n
```
Try ```
sudo route add default ppp0
```

---

### Post by sputty01 on 2008-08-30
Hi again, i gave it a try but it didn't seem to work. One thing i did notice which was unusual was that i had 2 ppp0 interfaces in the routing table.. could that be causing issues?

```
sputty01@mintydoom ~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
172.16.224.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.16.118.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
sputty01@mintydoom ~ $ sudo route add default ppp0
sudo: unable to resolve host mintydoom
[sudo] password for sputty01: 
SIOCADDRT: File exists
sputty01@mintydoom ~ $ ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.

--- google.com ping statistics ---
13 packets transmitted, 0 received, 100% packet loss, time 12008ms

sputty01@mintydoom ~ $ sudo route -n
sudo: unable to resolve host mintydoom
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
172.16.224.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.16.118.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

---

