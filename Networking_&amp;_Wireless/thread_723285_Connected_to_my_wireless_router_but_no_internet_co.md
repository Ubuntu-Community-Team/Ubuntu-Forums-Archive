---
title: "Connected to my wireless router but no internet connection"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by bluecrimson21 on 2008-03-13
ok, heres my setup. recently upgraded from feisty to gusty and  been having problems with my wireless adapter. first using NM now switched to WICD. I have RTL8180 chipset 
with ndiswrapper driver. and here's some command and screen shots...

```
bluecrimson@myfirstlinuxstation:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.199
netmask 255.255.255.0
gateway 192.168.1.3

auto wlan0
iface wlan0 inet static
address 192.168.1.253
netmask 255.255.255.0
gateway 192.168.1.3
```

```
bluecrimson@myfirstlinuxstation:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:37:FB:5C  
          inet6 addr: fe80::206:5bff:fe37:fb5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3969 errors:0 dropped:0 overruns:0 carrier:9
          collisions:0 txqueuelen:1000 
          RX bytes:3425520 (3.2 MB)  TX bytes:574840 (561.3 KB)
          Interrupt:11 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10542 (10.2 KB)  TX bytes:10542 (10.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:40:F4:94:60:C6  
          inet addr:192.168.1.253  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe94:60c6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:713 errors:0 dropped:21 overruns:0 frame:0
          TX packets:1002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:218128 (213.0 KB)  TX bytes:73901 (72.1 KB)
          Interrupt:11 Memory:d092a000-d092a100 

```

```
bluecrimson@myfirstlinuxstation:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b linked  ESSID:"crimson"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:F8:EA:61:3B   
          Bit Rate=11 Mb/s   Sensitivity=80/85  
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-35 dBm  Noise level=-254 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
bluecrimson@myfirstlinuxstation:~$ sudo iwlist wlan0 scanning
[sudo] password for bluecrimson:
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:EA:61:3B
                    ESSID:"crimson"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:205  Signal level:0  Noise level:92
                    Extra: Last beacon: 31ms ago

```

```
bluecrimson@myfirstlinuxstation:~$ cat /etc/resolv.conf
nameserver 58.71.1.37
nameserver 58.71.2.7

```

```
bluecrimson@myfirstlinuxstation:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.1.3     0.0.0.0         UG    0      0        0 wlan0

```

```
bluecrimson@myfirstlinuxstation:~$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
From 192.168.1.253 icmp_seq=1 Destination Host Unreachable
From 192.168.1.253 icmp_seq=2 Destination Host Unreachable
From 192.168.1.253 icmp_seq=3 Destination Host Unreachable
From 192.168.1.253 icmp_seq=6 Destination Host Unreachable
From 192.168.1.253 icmp_seq=7 Destination Host Unreachable
From 192.168.1.253 icmp_seq=10 Destination Host Unreachable
From 192.168.1.253 icmp_seq=11 Destination Host Unreachable

```
-this the result when I ping my router, and of course to any other computer connected to my router. wait till I do the command below

```
bluecrimson@myfirstlinuxstation:~$ sudo service networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
SIOCDELRT: No such process
RTNETLINK answers: No such process
SIOCDELRT: No such process
                                                                         [ OK ]
bluecrimson@myfirstlinuxstation:~$ sudo service networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
                                                                         [ OK ]
```

```
bluecrimson@myfirstlinuxstation:~$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=64 time=1.43 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=64 time=1.23 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=64 time=1.19 ms
64 bytes from 192.168.1.3: icmp_seq=4 ttl=64 time=1.17 ms
64 bytes from 192.168.1.3: icmp_seq=5 ttl=64 time=1.33 ms
64 bytes from 192.168.1.3: icmp_seq=6 ttl=64 time=1.18 ms
64 bytes from 192.168.1.3: icmp_seq=7 ttl=64 time=1.15 ms
64 bytes from 192.168.1.3: icmp_seq=8 ttl=64 time=1.19 ms
64 bytes from 192.168.1.3: icmp_seq=9 ttl=64 time=1.12 ms
64 bytes from 192.168.1.3: icmp_seq=10 ttl=64 time=1.31 ms
64 bytes from 192.168.1.3: icmp_seq=11 ttl=64 time=1.16 ms
64 bytes from 192.168.1.3: icmp_seq=12 ttl=64 time=1.24 ms
64 bytes from 192.168.1.3: icmp_seq=13 ttl=64 time=1.18 ms
64 bytes from 192.168.1.3: icmp_seq=14 ttl=64 time=1.19 ms
64 bytes from 192.168.1.3: icmp_seq=15 ttl=64 time=1.45 ms

--- 192.168.1.3 ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 13997ms
rtt min/avg/max/mdev = 1.125/1.239/1.452/0.101 ms


```
-and thats the result when I ping my router again. I dunno if this is about WICD, if I switched from wired to my wireless, I need to restart networking TWICE or more. oh well anyways once I restart networking I can now access my router (go to the built-in web page of linksys WRT54G). I can access other computer connected to the network, I can use samba but I can't go anywhere beyond my router, I can't access the internet. 

Screen shot of WICD connected to my router.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=62476&stc=1&d=1205422575[/IMG]

Sorry, been trying to solve this for the last 3 days now, and I dunno where else can I find some help but here. Thanks

---

### Post by Paris Heng on 2008-03-13
Everything seen fine. All the IPs are correct. Try using traceroute to check from your PC to the router outgoing interface (outgoing to Internet). Can other PC in the network using the router to connect to the Internet?

---

### Post by bluecrimson21 on 2008-03-14
yeah. there are 4 other machine connected to the router, via ethernet(not wireless) connection though, and they can access the internet with no sweat (All of them are windows XP). 

traceroute result:
```
bluecrimson@myfirstlinuxstation:~$ sudo traceroute www.yahoo.com
traceroute: unknown host www.yahoo.com

```

it seems like there is a problem with my wireless connection not getting any DNS. i remember there is an issue about this in the wiki page of WICD, already tried the instruction given but still not getting any result. 

thanks. so now I think the problem here is WICD

---

### Post by handydan918 on 2008-03-14
> **bluecrimson21 said:**
> yeah. there are 4 other machine connected to the router, via ethernet(not wireless) connection though, and they can access the internet with no sweat (All of them are windows XP). 

traceroute result:
```
bluecrimson@myfirstlinuxstation:~$ sudo traceroute www.yahoo.com
traceroute: unknown host www.yahoo.com

```

it seems like there is a problem with my wireless connection not getting any DNS. i remember there is an issue about this in the wiki page of WICD, already tried the instruction given but still not getting any result. 

thanks. so now I think the problem here is WICD

To verify, can you ping an external server by ip address? 
I.e., ping 74.125.19.104  (google)

---

