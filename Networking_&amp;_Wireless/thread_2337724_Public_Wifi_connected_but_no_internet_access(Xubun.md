---
title: "Public Wifi connected but no internet access(Xubuntu 16.04)"
date: 2016-09-21
forum: Networking &amp; Wireless
---

### Post by andreabroka on 2016-09-21
[COLOR=#111111][FONT=Ubuntu]Let me start with the fact that the WIFI works in other networks. The notebook connects with the college wifi, after some page refresh redirects me to the login page and then no internet connections. The same pc with windows connects perfectly. My other pc with ubuntu 15.10 works perfectly at the same network. This notebook has a fresh ubuntu 16.04 installed.
[/FONT][/COLOR]
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.200.0.1      0.0.0.0         UG    600    0        0 wlp2s0
10.200.0.0      0.0.0.0         255.255.0.0     U     600    0        0 wlp2s0
andrea@andrea-Latitude-E4310:~$ ifconfig -a
eno1      Link encap:Ethernet  HWaddr 5c:26:0a:4c:d2:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f5400000-f5420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:335755 (335.7 KB)  TX bytes:335755 (335.7 KB)

wlp2s0    Link encap:Ethernet  HWaddr 18:3d:a2:37:62:5c  
          inet addr:10.200.99.21  Bcast:10.200.255.255  Mask:255.255.0.0
          inet6 addr: fe80::e04b:28ab:40a3:dc19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3419152 (3.4 MB)  TX bytes:345942 (345.9 KB)
```

[COLOR=#111111][FONT=Ubuntu]I tried:[/FONT][/COLOR]

[LIST=1]
[*]upgrade kernel
[*]set ipv6 to ignore
[*]restart nm
[*]set google dns
[*]using different browsers
[/LIST]
[COLOR=#111111][FONT=Ubuntu]no results with any of them.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Is there anything else I can try? Thank you very much

ps: this is the wifi test complete

Does any one has any idea?[/FONT][/COLOR]

---

### Post by andreabroka on 2016-09-22
I noticed that while changing dns It was possible to open only one web site and then no connections.


```
andrea@andrea-Latitude-E4310:~$ ping -c 4 google.com
PING google.com (216.58.192.142) 56(84) bytes of data.
64 bytes from ord36s01-in-f14.1e100.net (216.58.192.142): icmp_seq=1 ttl=48 time=7.60 ms
64 bytes from ord36s01-in-f14.1e100.net (216.58.192.142): icmp_seq=2 ttl=48 time=8.81 ms
64 bytes from ord36s01-in-f14.1e100.net (216.58.192.142): icmp_seq=3 ttl=48 time=8.25 ms
64 bytes from ord36s01-in-f14.1e100.net (216.58.192.142): icmp_seq=4 ttl=48 time=11.3 ms


--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 7.606/9.008/11.361/1.424 ms
andrea@andrea-Latitude-E4310:~$ ping [www.google.com]("http://www.google.com")
PING [www.google.com]("http://www.google.com") (216.58.192.132) 56(84) bytes of data.
64 bytes from ord36s01-in-f132.1e100.net (216.58.192.132): icmp_seq=1 ttl=48 time=10.1 ms
64 bytes from ord36s01-in-f132.1e100.net (216.58.192.132): icmp_seq=2 ttl=48 time=6.90 ms
64 bytes from ord36s01-in-f132.1e100.net (216.58.192.132): icmp_seq=3 ttl=48 time=12.4 ms
64 bytes from ord36s01-in-f132.1e100.net (216.58.192.132): icmp_seq=4 ttl=48 time=26.6 ms
64 bytes from ord36s01-in-f132.1e100.net (216.58.192.132): icmp_seq=5 ttl=48 time=9.62 ms
64 bytes from ord36s01-in-f132.1e100.net (216.58.192.132): icmp_seq=6 ttl=48 time=9.10 ms
64 bytes from ord36s01-in-f132.1e100.net (216.58.192.132): icmp_seq=7 ttl=48 time=12.6 ms
64 bytes from ord36s01-in-f132.1e100.net (216.58.192.132): icmp_seq=8 ttl=48 time=25.0 ms
64 bytes from ord36s01-in-f132.1e100.net (216.58.192.132): icmp_seq=9 ttl=48 time=12.9 ms






andrea@andrea-Latitude-E4310:~$ ping [www.google.com]("http://www.google.com")
ping: unknown host [www.google.com]("http://www.google.com")
andrea@andrea-Latitude-E4310:~$ ping -c 4 google.com
ping: unknown host google.com
andrea@andrea-Latitude-E4310:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=29 ttl=40 time=30.8 ms
64 bytes from 8.8.8.8: icmp_seq=30 ttl=40 time=29.6 ms
64 bytes from 8.8.8.8: icmp_seq=31 ttl=40 time=37.7 ms
64 bytes from 8.8.8.8: icmp_seq=32 ttl=40 time=48.6 ms
64 bytes from 8.8.8.8: icmp_seq=33 ttl=40 time=31.9 ms
64 bytes from 8.8.8.8: icmp_seq=34 ttl=40 time=34.0 ms
64 bytes from 8.8.8.8: icmp_seq=35 ttl=40 time=30.9 ms
64 bytes from 8.8.8.8: icmp_seq=36 ttl=40 time=44.5 ms
64 bytes from 8.8.8.8: icmp_seq=37 ttl=40 time=29.6 ms
64 bytes from 8.8.8.8: icmp_seq=38 ttl=40 time=41.7 ms
64 bytes from 8.8.8.8: icmp_seq=39 ttl=40 time=33.8 ms
64 bytes from 8.8.8.8: icmp_seq=40 ttl=40 time=31.0 ms
64 bytes from 8.8.8.8: icmp_seq=42 ttl=40 time=8263 ms
64 bytes from 8.8.8.8: icmp_seq=43 ttl=40 time=7255 ms
64 bytes from 8.8.8.8: icmp_seq=44 ttl=40 time=6257 ms
64 bytes from 8.8.8.8: icmp_seq=45 ttl=40 time=5257 ms
64 bytes from 8.8.8.8: icmp_seq=46 ttl=40 time=4257 ms
64 bytes from 8.8.8.8: icmp_seq=47 ttl=40 time=3261 ms
64 bytes from 8.8.8.8: icmp_seq=48 ttl=40 time=2261 ms
64 bytes from 8.8.8.8: icmp_seq=49 ttl=40 time=1261 ms
64 bytes from 8.8.8.8: icmp_seq=50 ttl=40 time=261 ms
64 bytes from 8.8.8.8: icmp_seq=51 ttl=40 time=300 ms
64 bytes from 8.8.8.8: icmp_seq=52 ttl=40 time=344 ms
64 bytes from 8.8.8.8: icmp_seq=54 ttl=40 time=8739 ms
64 bytes from 8.8.8.8: icmp_seq=55 ttl=40 time=8011 ms
64 bytes from 8.8.8.8: icmp_seq=56 ttl=40 time=7011 ms
64 bytes from 8.8.8.8: icmp_seq=57 ttl=40 time=6011 ms
64 bytes from 8.8.8.8: icmp_seq=58 ttl=40 time=5007 ms
64 bytes from 8.8.8.8: icmp_seq=59 ttl=40 time=4003 ms
64 bytes from 8.8.8.8: icmp_seq=60 ttl=40 time=3003 ms
```

---

### Post by andreabroka on 2016-09-22
I booted from USB , Ubuntu 15.10 and I had the same problem, only the first web page is loaded. Please is there anything else I can try?

---

### Post by hcuellart on 2016-09-22
I am in the same boat as you, though I have the problem in both scenarios, public and private. If you are having the problem in a public access only, maybe the firewall is the conflicting issue??? I am a newbie so take this as a suggestion, but I see you have not tried that...

---

### Post by andreabroka on 2016-09-22
Thank you for answering. How can I modify the firewall?

---

### Post by hcuellart on 2016-09-23
Andrea please search here in the forums for how to disable firewall if I remember correctly it's ufw in the command line, so search for that too...

---

### Post by QIII on 2016-09-23
Hello!

As a matter of safe and sane practice, please don't even consider changing/disabling your firewall to use public wifi!  That's about like using your umbrella in a light sprinkle and folding it up in a downpour.

---

### Post by jeremy31 on 2016-09-23
Before trying to connect to a network,
```
sudo iwconfig wlp2s0 power off
```
See if disabling power management helps.  It also seems that the wireless is attempting to roam between access points with the same name.  If you click on the wifi icon in the notification bar, choose edit connections, then choose the network, and select a MAC address from the dropdown box next to BSSID and hopefully that will stop the attempts to roam

---

### Post by andreabroka on 2016-09-28
Hi, I tried but nothing changed. Still the same problem.

---

### Post by andreabroka on 2016-09-29
It is very strange because I tried with an other pc ubuntu 15.10 and it works. This pc has the same problem even when booted form usb on ubuntu 15.10.

---

