---
title: "Need help getting Belkin internet connection working"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by tahitiwibble on 2008-03-04
I have tried everything that my limited knowledge will allow me.

A couple of days ago the man from the Post Office came to check my internet connection. He proved to me that they really are providing a line with true 256/128 capacity. For the past two years, using all kinds of computers (Windows, Mac & Linux) here at home, I have never seen better than 18.1kbs while downloading big files and once had a log running for 9 months which gave me an average download rate of 1.9kbs. He was running an old laptop with Windows 98 to show me test results which easily met the 256kbs ceiling.

I have a Belkin ADSL modem with Router and the little Belkin USB wireless adapter. Yesterday I was on the cabled connection from my computer to the modem and still got the same lousy results.

Should I just throw away this modem? and get a new one?

If anyone can suggest what to do, this may help:

dad@dad-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"myfirsteverwifi"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:50:7F:34:E6   
          Bit Rate=11 Mb/s   
          Link Quality=100/100  Signal level=50/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dad@dad-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 7c
       serial: 00:e0:4d:44:04:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 latency=32 maxlatency=8 mingnt=3 multicast=yes
       resources: ioport:d000-d0ff iomemory:fdffe000-fdffe0ff irq:21
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:11:50:b1:7c:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.3 multicast=yes wireless=IEEE 802.11b/g
dad@dad-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:50:7F:34:E6
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    Extra: Last beacon: 48ms ago

dad@dad-desktop:~$ Isusb
bash: Isusb: command not found
dad@dad-desktop:~$ lsusb
Bus 005 Device 006: ID 0bda:0151 Realtek Semiconductor Corp. 
Bus 005 Device 005: ID 050d:705c Belkin Components 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0d62:a100 Darfon Electronics Corp. Benq Mouse
Bus 002 Device 003: ID 046d:c30a Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:0a01 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
dad@dad-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"myfirsteverwifi"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:50:7F:34:E6   
          Bit Rate=11 Mb/s   
          Link Quality=100/100  Signal level=47/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dad@dad-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"myfirsteverwifi"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:50:7F:34:E6   
          Bit Rate=11 Mb/s   
          Link Quality=99/100  Signal level=48/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dad@dad-desktop:~$ 

I pay $100 a month for this connection and it really hurts not to get what I pay for.

Thanks for the reading this anyway.

---

### Post by rustybronco on 2008-03-04
> **tahitiwibble said:**
> I have tried everything that my limited knowledge will allow me.

Thanks for the reading this anyway.Well with my limited knowledge just maybe we will equal 100%

[http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html](http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html)

start with pinging your router address (something like 192.168.1.1) and check the latency.
also check the you have the proper dns server addresses in your router which is used to resolve the name you type to an i.p. address (if you don't latency goes way up)  if you are using dhcp.
if you are using a static i.p. let me know.

***edit*** also available in gui form. system>administration>network tools

---

### Post by tahitiwibble on 2008-03-04
rustybronco,

I'm on it man ................ I'm on it. Please just give an old fella a little time to exhaust his own, following your tips,  resourcefulness.

You're a champ! Thanks.

I'll be back.

---

### Post by tahitiwibble on 2008-03-04
> **rustybronco said:**
> Well with my limited knowledge just maybe we will equal 100%

[http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html](http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html)

start with pinging your router address (something like 192.168.1.1) and check the latency.
also check the you have the proper dns server addresses in your router which is used to resolve the name you type to an i.p. address (if you don't latency goes way up)  if you are using dhcp.
if you are using a static i.p. let me know.

task - start with pinging your router address (something like 192.168.1.1) and check the latency.
result - PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=1.51 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=1.46 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=1.37 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=1.29 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=1.46 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=1.44 ms

--- 192.168.2.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 1.297/1.428/1.517/0.071 ms

task - check the you have the proper dns server addresses in your router which is used to resolve the name you type to an i.p. address (if you don't latency goes way up)  if you are using dhcp.
result - My DNS is automatically assigned by the ISP Primary address is 202.3.225.115, secondary is 202.3.225.125, DHCP Server Function is ON by default

I'm lost, but learning.

---

### Post by rustybronco on 2008-03-04
> **tahitiwibble said:**
> task - start with pinging your router address (something like 192.168.1.1) and check the latency.
result - PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=1.51 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=1.46 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=1.37 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=1.29 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=1.46 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=1.44 ms

--- 192.168.2.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 1.297/1.428/1.517/0.071 ms
ping times are high to your router. ? **5006ms.***edit*** I guess not, here is mine.**

> dale@hardy-laptop:~$ ping -c 6 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=47.8 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=34.3 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=26.2 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=50.3 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=3.79 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=28.2 ms

--- 192.168.2.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time **5001ms**
rtt min/avg/max/mdev = 3.796/31.815/50.347/15.462 ms

---

### Post by tahitiwibble on 2008-03-04
fyi:

traceroute: Warning: google.com has multiple addresses; using 64.233.187.99
traceroute to google.com (64.233.187.99), 30 hops max, 40 byte packets
 1   (192.168.2.1)  1.266 ms  1.299 ms  1.218 ms
 2  123.50.80.1 (123.50.80.1)  24.188 ms  24.544 ms  26.557 ms
 3  202.3.241.179 (202.3.241.179)  24.542 ms  21.292 ms  23.085 ms
 4  if-0-0.core1.mana.pf (202.3.241.3)  23.464 ms  22.778 ms  23.200 ms
 5  80.255.53.1 (80.255.53.1)  549.741 ms  550.295 ms  550.110 ms
 6  rvs-rt001.ge-0-3-0.3.globalconnex.net (80.255.37.113)  549.479 ms  548.768 ms  550.031 ms
 7  66.36.192.161 (66.36.192.161)  609.482 ms  611.187 ms  606.057 ms
 8  ge-6-8.car2.Washington1.Level3.net (4.79.17.53)  609.311 ms  615.308 ms  626.140 ms
 9  ae-3-89.edge1.Washington1.Level3.net (4.68.17.144)  612.582 ms  605.498 ms  605.964 ms
10  GOOGLE-INC.edge1.Washington1.Level3.net (4.79.228.38)  619.572 ms  618.731 ms GOOGLE-INC.edge1.Washington1.Level3.net (4.79.231.6)  619.481 ms
11  72.14.238.136 (72.14.238.136)  625.383 ms  621.806 ms  619.178 ms
12  72.14.236.15 (72.14.236.15)  626.206 ms  622.880 ms  622.701 ms
13  216.239.49.222 (216.239.49.222)  629.202 ms  625.390 ms 216.239.43.249 (216.239.43.249)  626.211 ms
14  google.com (64.233.187.99)  627.061 ms  620.658 ms  622.687 ms


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:4D:44:04:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xd000 

eth1      Link encap:Ethernet  HWaddr 00:11:50:B1:7C:1B  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:feb1:7c1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40331 errors:0 dropped:109 overruns:0 frame:0
          TX packets:22308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11923230 (11.3 MiB)  TX bytes:3212641 (3.0 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81023 (79.1 KiB)  TX bytes:81023 (79.1 KiB)



route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1

---

### Post by rustybronco on 2008-03-04
> **tahitiwibble said:**
> fyi:

traceroute: Warning: google.com has multiple addresses; using 64.233.187.99
traceroute to google.com (64.233.187.99), 30 hops max, 40 byte packets
 1   (192.168.2.1)  1.266 ms  1.299 ms  1.218 ms
 2  123.50.80.1 (123.50.80.1)  24.188 ms  24.544 ms  26.557 ms
 3  202.3.241.179 (202.3.241.179)  24.542 ms  21.292 ms  23.085 ms
 4  if-0-0.core1.mana.pf (202.3.241.3)  23.464 ms  22.778 ms  23.200 ms
 5  80.255.53.1 (80.255.53.1)  **549.741 ms  550.295 ms  550.110 ms**
 6  rvs-rt001.ge-0-3-0.3.globalconnex.net (80.255.37.113) **549.479 ms  548.768 ms  550.031 ms**
 7  66.36.192.161 (66.36.192.161) ** 609.482 ms  611.187 ms  606.057 ms**
 8  ge-6-8.car2.Washington1.Level3.net (4.79.17.53)  **609.311 ms  615.308 ms  626.140 ms**
 9  ae-3-89.edge1.Washington1.Level3.net (4.68.17.144) ** 612.582 ms  605.498 ms  605.964 ms**
10  GOOGLE-INC.edge1.Washington1.Level3.net (4.79.228.38) ** 619.572 ms  618.731 ms GOOGLE-INC.edge1.Washington1.Level3.net (4.79.231.6)  [b]619.481 ms**
11  72.14.238.136 (72.14.238.136)  **625.383 ms  621.806 ms  619.178 ms**
12  72.14.236.15 (72.14.236.15)  **626.206 ms  622.880 ms  622.701 ms**
13  216.239.49.222 (216.239.49.222)  **629.202 ms  625.390 ms 216.239.43.249 (216.239.43.249)  626.211 ms**
14  google.com (64.233.187.99)  **627.061 ms  620.658 ms  622.687 ms**

whats up with the high ping times?
```
traceroute to google.com (64.233.187.99), 30 hops max, 40 byte packets
 1    19.962 ms  20.073 ms  20.242 ms
 2    26.450 ms  26.655 ms  26.807 ms
 3    26.948 ms  28.184 ms  28.452 ms
 4    31.905 ms  32.057 ms  32.182 ms
 5   32.546 ms  32.696 ms  32.901 ms
 6   37.801 ms  10.254 ms  28.622 ms
 7  te-0-6-0-1-ar01.taylor.mi.michigan.comcast.net (68.86.90.110)  32.181 ms  32.316 ms  32.892 ms
 8  pos-0-3-0-0-cr01.cleveland.oh.ibone.comcast.net (68.86.85.37)  41.662 ms  41.861 ms  42.802 ms
 9  pos-0-7-0-0-cr01.pittsburgh.pa.ibone.comcast.net (68.86.85.46)  48.279 ms  48.349 ms  48.523 ms
10  COMCAST-IP.edge1.Washington1.Level3.net (4.79.231.14)  51.579 ms  51.774 ms  51.865 ms
11  xe-11-2-0.edge1.Washington1.Level3.net (4.79.231.13)  48.784 ms  48.930 ms  53.621 ms
12  GOOGLE-INC.edge1.Washington1.Level3.net (4.79.228.38)  29.139 ms  25.605 ms GOOGLE-INC.edge1.Washington1.Level3.net (4.79.231.6)  41.233 ms
13  72.14.238.136 (72.14.238.136)  57.343 ms  57.520 ms  61.442 ms
14  72.14.236.15 (72.14.236.15)  63.154 ms  63.355 ms  65.572 ms
15  216.239.43.249 (216.239.43.249)  68.666 ms  68.378 ms  68.775 ms
16  jc-in-f99.google.com (64.233.187.99)  66.012 ms  65.576 ms  66.337 ms
```

---

### Post by tahitiwibble on 2008-03-04
Heaven only knows :-( I don't, that's for sure!

Are those really ping times or is it how long it takes to be lead up the garden path by the staff at this country's only ISP (a subsidiary of the Post Office) who spend 24/24 downloading films on a shaky satellite's insufficient bandwidth?

---

### Post by rustybronco on 2008-03-04
I guess we will have to investigate.
search posts/google for high ping times.
80.255.53.1 is intelsat...
check the i.p address before it, with whois in network tools the delay seems to be between those two.

I've got to spend time with the family now, but I will help all I can until it's resolved. (bet on it )
you put up with it for 9 months,a little more time won't matter.

***edit*** who did the post office ping? your neighbor?

***2nd edit*** i'd call you isp and ask ** whats up with that?** if it isn't  a problem with "4 if-0-0.core1.mana.pf (202.3.241.3) 23.464 ms 22.778 ms 23.200 ms" to intelesat
> % [whois.apnic.net node-1]
% Whois data copyright terms    [http://www.apnic.net/db/dbcopyright.html](http://www.apnic.net/db/dbcopyright.html)

inetnum:      202.3.224.0 - 202.3.255.255
netname:      MANA
country:      PF
descr:        MANA S.A.
descr:        IAP/ISP of Tahiti and her Islands
admin-c:      RA57-AP
tech-c:       TT136-AP
status:       ALLOCATED PORTABLE
mnt-by:       APNIC-HM
mnt-lower:    MAINT-PF-TT
changed:      [email]hm-changed@apnic.net[/email] 20070806
source:       APNIC 

---

### Post by tahitiwibble on 2008-03-04
2 years my friend! Please don't let me detract from family time, it's the most important thing you can do. I have 5 kids and know a little about that particular subject. .......................... and THANKS. 

I'll carry on myself with your suggestions and see what comes up.

---

### Post by tahitiwibble on 2008-03-04
> **rustybronco said:**
> 
***edit*** who did the post office ping? your neighbor?

:lolflag::lolflag::lolflag:, please see my last edit that I was writing at the same time as your reply.

---

### Post by rustybronco on 2008-03-04
my guess, It's gotta be with your isp.

 [http://ezinearticles.com/?Top-10-Questions-To-Ask-Your-Satellite-Internet-Service-Provider&id=645143](http://ezinearticles.com/?Top-10-Questions-To-Ask-Your-Satellite-Internet-Service-Provider&id=645143)
> For a ping to make its round trip it must travel up to the satellite, back to earth to the server, up to the satellite again and back to the origination point. This is a round trip is approximately 88,892 miles. When calculated with the speed of light, in a perfect world the round trip will take about 448 milliseconds. When you add in coding delays and processing delays you can increase that figure by 100 to 250 milliseconds. On an efficient system, a round trip ping should take between 550 and 700 milliseconds (225 ms one way in each direction).
> 8) What will be my actual measured speeds?

The service providers will sell you a specific rate plan that will have an uplink or return data rate, and a downlink or forward data rate. This will usually be expressed in a manner such as &#8220;128/512&#8221; or sometimes &#8220;512/128&#8221;. The larger number will always be the forward channel which is your downlink as a user. Most providers will not tell you that the speeds include IP overhead. Every internet system whether its satellite or terrestrial uses IP protocols that require a certain amount of bandwidth to process the IP traffic. Because of the overhead you can expect that your actual measured payload speeds will be around 20% lower than what you are paying for. Actual speeds can be measured by running a speed test from a PC over the satellite link.
who or to where did they do their speed test?  speedtest.net?

---

### Post by tahitiwibble on 2008-03-06
> **rustybronco said:**
> my guess, It's gotta be with your isp.

 [http://ezinearticles.com/?Top-10-Questions-To-Ask-Your-Satellite-Internet-Service-Provider&id=645143](http://ezinearticles.com/?Top-10-Questions-To-Ask-Your-Satellite-Internet-Service-Provider&id=645143)


who or to where did they do their speed test?  speedtest.net?

Rustybronco,

Forgive me for not getting back to you sooner, I thought that the forum notified me of new posts, I'll have to check that.

We know that my outbound ping to google.com shows lousy results. I wonder if you could ping me please, obviously in the opposite direction,  with traceroute in the Terminal for comparison's sake.

The guy from the Post Office first of all tested with their own proprietary system. The strange thing was that when I used his laptop to use some of the classic internet speed testing sites, I got the same very good results ( a full 256/128 ) that he did while downloading from local (Tahiti) sites. It's confusing! Is my system just not up to it? Is it the modem/router? I know that Windows 98 is leaner and meaner than the rubbish coming from Microsoft since then, but I think that Linux should be able to do as well as Windows 98.

Funnily enough it **was** speedtest.net that I used on his computer which obtained a very good 230 something download rate???? I just did the speedtest.net test and got 106/zero because it stalled on the upload test!????

We're definitely getting fleeced by the govt. operated monopolised ISP, but how can you explain the good results on the PO man's laptop?

Thanks for the ezine article, very very interesting.

---

### Post by rustybronco on 2008-03-06
> **tahitiwibble said:**
> Rustybronco,

Forgive me for not getting back to you sooner, I thought that the forum notified me of new posts, I'll have to check that.

We know that my outbound ping to google.com shows lousy results. I wonder if you could ping me please, obviously in the opposite direction,  with traceroute in the Terminal for comparison's sake.

The guy from the Post Office first of all tested with their own proprietary system. The strange thing was that when I used his laptop to use some of the classic internet speed testing sites, I got the same very good results ( a full 256/128 ) that he did while downloading from local (Tahiti) sites. It's confusing! Is my system just not up to it? Is it the modem/router? I know that Windows 98 is leaner and meaner than the rubbish coming from Microsoft since then, but I think that Linux should be able to do as well as Windows 98.

Funnily enough it **was** speedtest.net that I used on his computer which obtained a very good 230 something download rate???? I just did the speedtest.net test and got 106/zero because it stalled on the upload test!????

We're definitely getting fleeced by the govt. operated monopolised ISP, but how can you explain the good results on the PO man's laptop?

Thanks for the ezine article, very very interesting.Well the question I have is, where did he connect his equipment up to? also was it connected through a cable or wireless? let's eliminate what we can from the equation.
another thought, why does each hop have to be a satellite hop that adds 500ms?  

in answer to your question yes I will  ping you but I can't until late tonight my time (michigan usa) 
but I know I won't have the issue of a multiple hop satellite relay.

> but how can you explain the good results on the PO man's laptop?
after we have the facts of how and where to, we aim to find out...

---

### Post by tahitiwibble on 2008-03-06
> **rustybronco said:**
> Well the question I have is, where did he connect his equipment up to? also was it connected through a cable or wireless? let's eliminate what we can from the equation.
another thought, why does each hop have to be a satellite hop that adds 500ms?  

in answer to your question yes I will  ping you but I can't until late tonight my time (michigan usa) 
but I know I won't have the issue of a multiple hop satellite relay.

The PO man used their own proprietary cable modem rather than my Belkin to test the line. He was cabled and not wireless. Stupid me should have thought to tell him to connect to my modem/router :oops: but didn't. I was so shocked to see the guy after a year of waiting. He also had a nice looking piece of equipment with him that was a line speed tester.

As soon as he left the house I disabled my wireless and hard wired my PC to the modem: still the same miserable results.

I imagine that you will do the satellite hopping because for now, that's the only way to connect with Tahiti. Trans-oceanic cable is to be laid next year from Hawaii.

I think it's my hardware, because despite the satellite factor, I should be getting the same as the PO man's results when hard wired.

It's got to be chilly up there in Michigan! I worked with a bunch of guys from Ann Arbor for a couple of years. Nice people.

edit - PS I got the same hard-wired, poor results when downloading from local (same island) site.

---

### Post by rustybronco on 2008-03-06
> **tahitiwibble said:**
> 
I imagine that you will do the satellite hopping because for now, that's the only way to connect with Tahiti. Trans-oceanic cable is to be laid next year from Hawaii.

I think it's my hardware, because despite the satellite factor, I should be getting the same as the PO man's results when hard wired.

edit - PS I got the same hard-wired, poor results when downloading from local (same island) site.yes but I will have a lot less satellite hops than you.
does sound like hardware (possibly). can you get someone with a different o.s. to come and connect at your place and see what speed they get?

I need to think about this some more...

---

### Post by tahitiwibble on 2008-03-06
rustybronco,

I have had a Windows desktop (XP Pro), 2 Windows laptops (XP Pro), an Apple notebook (latest OS) and now my newish Ubuntu desktop all connected to the Belkin modem/router within the past two years and have tested wireless, wireless/cabled & cabled on all the different machines. With what you have helped me to learn about pinging and tracing I have to come to the conclusion that the Belkin is a piece of rubbish. The service that our ISP offers is as bad as you can get and I am going to go see the general manager of the place tomorrow for a refund for having charged me a lot of money for a service they just don't provide (stalls, disconnections and slowness are an all day, everyday fact of life).
The fact is that they seem to have contracted for a bottom dollar satellite connection and they charge us poor suckers top dollar for the same service. Profit margin must be astronomical!

I just checked again with my daughter's Apple notebook on a cabled/wireless disabled speedtest.net and got exactly the same results as ever.

It's the Belkin, it has to be. I'm wondering if it's not all part of the PO's disgusting monopoly situation where they more or less oblige you to buy their proprietary ADSL modem which is probably somehow tied into their hardware or something?

Anyway Squire, I'm going to try and borrow another modem and see what happens - unless you think there's a way to unbridle the Belkin?

---

### Post by rustybronco on 2008-03-07
The only thing I can think of other than a bad cable modem? router? (heat issues) is if the cable modem was tied to a mac address and your isp is throttling your service because of it.
I'm glad (not in a sadistic way) to see the problem has occurred with the other os's in the past, the question is now did it ever work correctly? if it did, is the initial card/pc used with install happen to be around some place?
Dale.

---

### Post by HereInOz on 2008-03-07
I would replace the modem/router with something like a Billion 7300G.  I have had a couple of Belkins look for all the world like they were working, but just didn't.  Replacement with a loaned modem/router fixed it.  If you can borrow something for testing, I would have a go at that before buying something.

When you think about it, the only common factor is the modem/router.  Everything else has been eliminated.

---

### Post by rustybronco on 2008-03-07
> **tahitiwibble said:**
> I'm going to try and borrow another modem and see what happens - unless you think there's a way to unbridle the Belkin?You can breathe new life into the device! when the wind starts to blow, put it to work as a paper weight!

---

### Post by tahitiwibble on 2008-03-07
> **HereInOz said:**
> I would replace the modem/router with something like a Billion 7300G.  I have had a couple of Belkins look for all the world like they were working, but just didn't.  Replacement with a loaned modem/router fixed it.  If you can borrow something for testing, I would have a go at that before buying something.

When you think about it, the only common factor is the modem/router.  Everything else has been eliminated.

You're right mate! That's the only common factor. I was hoping for a tweak or a re-config, or something: but it boils down to the Belkin one way or another. Fair's fair though, it's the first one of their products I've been disappointed with.

---

### Post by tahitiwibble on 2008-03-07
> **rustybronco said:**
> You can breathe new life into the device! when the wind starts to blow, put it to work as a paper weight!

A thousand thanks for your help Dale, I learnt quite a bit thanks to you.

Sentencing has been pronounced following our diagnostics and HereInOz's helpful comment. Execution shall take place at the earliest. I'll give it to someone with a 128kbs subscription.

---

