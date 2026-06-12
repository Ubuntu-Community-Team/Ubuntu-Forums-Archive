---
title: "network congestion or something else?"
date: 2016-03-20
forum: Networking &amp; Wireless
---

### Post by dgermann on 2016-03-20
Friends--

Not sure if this is "network congestion" or something else.

_Symptoms:_

1. Access by client wind to server torus: when I ssh to wind from another client and do an ls -alh on the mount point, it takes 10-15 seconds to simply list out the directories on screen. (On my machine and another remote machine these same directories come up instantly with no delay.) Worker on this machine says the gui is slow in accessing files, such as via nautilus.

     A. This problem exists whether or not the ufw firewall on wind is enabled or disabled.

2. lightdm keeps freezing the computer (this may not be related, wanted to include what all is going on)

_System:_
All clients mentioned here are 12.04 lts. Server torus is 14.04 lts.
The files are served up via samba.
Production environment.

_Network:_
6 workstations internally connecting
via ethernet to

server torus

connecting via openvpn through
cloud
to two remote clients, wind and air

air does not have the problem wind is having.
wind is a machine about 9 months old, and has had these problems from day 1.

_Testing done so far:_
Following [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting#.Vux6RSbHTb8]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting#.Vux6RSbHTb8")  I have run these tests via a script on both wind and torus (this is the version on wind):
```
ifconfig -a
route
ethtool eth0
ethtool tun2
netstat -ian
ping -c 5 torus
mtr -r -c 5 torus
sudo tcpdump -i tun2 -c 5

```

Here are the current results on wind, the client:
```
=====ifconfig -a=====
eth0      Link encap:Ethernet  HWaddr [blanked]
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::feaa:14ff:fea7:61a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:757005 (757.0 KB)  TX bytes:402044 (402.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10864 (10.8 KB)  TX bytes:10864 (10.8 KB)

tun2      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.20.13  P-t-P:10.8.20.14  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:202967 (202.9 KB)  TX bytes:225265 (225.2 KB)

=====route=====
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.8.20.0       10.8.20.14      255.255.255.0   UG    0      0        0 tun2
10.8.20.14      *               255.255.255.255 UH    0      0        0 tun2
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
=====ethtool eth0=====
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
=====ethtool tun2=====
Settings for tun2:
	Supported ports: [ ]
	Supported link modes:   Not reported
	Supported pause frame use: No
	Supports auto-negotiation: No
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 10Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0xffffffa1 (-95)
			       drv ifup tx_err tx_queued intr tx_done rx_status pktdata hw wol 0xffff8000
	Link detected: yes
=====netstat -ian=====
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0      3259      0      0 0          2022      0      0      0 BMRU
lo        65536 0       150      0      0 0           150      0      0      0 LRU
tun2       1500 0      1579      0      0 0          1429      0      0      0 MOPRU
=====ping -c 5 torus=====
PING torus (10.8.20.1) 56(84) bytes of data.
64 bytes from torus (10.8.20.1): icmp_req=1 ttl=64 time=122 ms
64 bytes from torus (10.8.20.1): icmp_req=2 ttl=64 time=59.6 ms
64 bytes from torus (10.8.20.1): icmp_req=3 ttl=64 time=70.2 ms
64 bytes from torus (10.8.20.1): icmp_req=4 ttl=64 time=60.5 ms
64 bytes from torus (10.8.20.1): icmp_req=5 ttl=64 time=60.3 ms

--- torus ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 59.667/74.730/122.936/24.416 ms
=====mtr -r -c 5 torus=====
HOST: wind                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- torus                      0.0%     5   61.0  62.5  60.3  69.1   3.8
=====sudo tcpdump -i tun2 -c 5=====
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on tun2, link-type RAW (Raw IP), capture size 65535 bytes
21:17:57.385994 IP 10.8.20.13.ssh > fire.59294: Flags [P.], seq 753291173:753291365, ack 4051980439, win 332, options [nop,nop,TS val 394127 ecr 85571991], length 192
21:17:57.403563 IP fire.59294 > 10.8.20.13.ssh: Flags [.], ack 4294967104, win 331, options [nop,nop,TS val 85573166 ecr 394116], length 0
21:17:57.408641 IP fire.59294 > 10.8.20.13.ssh: Flags [.], ack 4294967216, win 331, options [nop,nop,TS val 85573168 ecr 394116], length 0
21:17:57.413094 IP fire.59294 > 10.8.20.13.ssh: Flags [.], ack 0, win 331, options [nop,nop,TS val 85573168 ecr 394116], length 0
21:17:57.449333 IP fire.59294 > 10.8.20.13.ssh: Flags [.], ack 192, win 331, options [nop,nop,TS val 85573178 ecr 394127], length 0
5 packets captured
14 packets received by filter
0 packets dropped by kernel
```

And here are the current results on torus, the server:
```
=====ifconfig -a=====
eth0      Link encap:Ethernet  HWaddr  [blanked]  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:b1a20000-b1a3ffff 

eth1      Link encap:Ethernet  HWaddr  [blanked]  
          inet addr:192.168.0.203  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:17ff:feb9:eec5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33620172 errors:0 dropped:11170 overruns:0 frame:0
          TX packets:48820825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17097116346 (17.0 GB)  TX bytes:63704752579 (63.7 GB)
          Memory:b1a00000-b1a1ffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:496 (496.0 B)  TX bytes:496 (496.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.20.1  P-t-P:10.8.20.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:64673 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5628941 (5.6 MB)  TX bytes:5992696 (5.9 MB)

=====route=====
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         router          0.0.0.0         UG    0      0        0 eth1
10.8.20.0       10.8.20.2       255.255.255.0   UG    0      0        0 tun0
10.8.20.2       *               255.255.255.255 UH    0      0        0 tun0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
=====ethtool eth1=====
Settings for eth1:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: Symmetric
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: on (auto)
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes
=====ethtool tun0=====
Settings for tun0:
	Supported ports: [ ]
	Supported link modes:   Not reported
	Supported pause frame use: No
	Supports auto-negotiation: No
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 10Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0xffffffa1 (-95)
			       drv ifup tx_err tx_queued intr tx_done rx_status pktdata hw wol 0xffff8000
	Link detected: yes
=====netstat -ian=====
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BM
eth1       1500 0  33620186      0  11170 0      48820840      0      0      0 BMRU
lo        65536 0         8      0      0 0             8      0      0      0 LRU
tun0       1500 0     64673      0      0 0         45129      0      0      0 MOPRU
=====ping -c 5 torus=====
PING wind (10.8.20.13) 56(84) bytes of data.
64 bytes from wind (10.8.20.13): icmp_seq=1 ttl=64 time=59.3 ms
64 bytes from wind (10.8.20.13): icmp_seq=2 ttl=64 time=71.8 ms
64 bytes from wind (10.8.20.13): icmp_seq=3 ttl=64 time=59.3 ms
64 bytes from wind (10.8.20.13): icmp_seq=4 ttl=64 time=60.1 ms
64 bytes from wind (10.8.20.13): icmp_seq=5 ttl=64 time=63.5 ms

--- wind ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 59.340/62.835/71.862/4.770 ms
=====mtr -r -c 5 torus=====
Start: Sun Mar 20 21:18:06 2016
HOST: torus                       Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- wind                       0.0%     5   60.0  62.9  59.2  67.4   4.0
=====sudo tcpdump -i tun0 -c 5=====
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on tun0, link-type RAW (Raw IP), capture size 65535 bytes
21:18:54.663582 IP 10.8.20.21.39784 > 10.8.20.1.microsoft-ds: Flags [P.], seq 2479283087:2479283129, ack 2857922074, win 296, options [nop,nop,TS val 129788032 ecr 86638613], length 42SMB PACKET: SMBecho (REQUEST)

21:18:54.663713 IP 10.8.20.1.microsoft-ds > 10.8.20.21.39784: Flags [P.], seq 1:43, ack 42, win 235, options [nop,nop,TS val 86653651 ecr 129788032], length 42SMB PACKET: SMBecho (REPLY)

21:18:54.669378 IP 10.8.20.21.39785 > 10.8.20.1.microsoft-ds: Flags [P.], seq 2903102360:2903102402, ack 953249692, win 296, options [nop,nop,TS val 129788032 ecr 86638614], length 42SMB PACKET: SMBecho (REQUEST)

21:18:54.669518 IP 10.8.20.1.microsoft-ds > 10.8.20.21.39785: Flags [P.], seq 1:43, ack 42, win 235, options [nop,nop,TS val 86653653 ecr 129788032], length 42SMB PACKET: SMBecho (REPLY)

21:18:54.683799 IP 10.8.20.21.39784 > 10.8.20.1.microsoft-ds: Flags [.], ack 43, win 296, options [nop,nop,TS val 129788037 ecr 86653651], length 0
5 packets captured
6 packets received by filter
0 packets dropped by kernel
```

So can you see something here that could be causing this slowness? Other troubleshooting I should be doing?

Thanks for your help!

---

### Post by bab1 on 2016-03-21
This is far to confusing to follow.  Let's start with a simple direct explanation what is going on.

Are you connecting by VPN in both scenarios?  This means by both the client that has the lag and the one that performs correctly?  Can I assume that you are hopping from the VPN server to the other server (torus)?  This means that the user logs in froma remote network (WAN) in both cases.

Why do you need a VPN connection when using SSH?  That is using an encrypted connection in an encrypted tunnel.  What happens if you shut the VPN off and ssh directly (to the server torus)?

It is always better to compare what is working correctly to the one that isn't.  Just the working client to the non working client. Everything else is the same, correct??? 

FWIW,  One of the best classes I ever took was "Technical Writing".  It taught me to be direct and succinct.

---

### Post by dgermann on 2016-03-21
bab1--

Thank you for helping me.

Perhaps it will help to attach a drawing of the network. [ATTACH=CONFIG]267920[/ATTACH]

There is only one server: torus is the file server and the vpn server, using a tun (not tap) interface. torus.conf has client-to-client.

Both clients mentioned here, wind and air, log in via vpn. Each sits behind a separate router (people are working from home). There are other computers also behind their individual routers, but they do not connect with these clients.

I don't know a way for either client to ssh to torus, or for torus to ssh to the clients, without going through the vpn. I do not even know their ipaddresses, nor have access to their routers to forward the traffic to these clients. These clients establish connection via vpn and a ddns, and then I can "see" them.

As far as I know, everything else is the same on these two clients: the openvpn conf files are the same; the os is the same; the file structure is the same.

Additional symptoms: Just this weekend the person using wind told me these symptoms: She was able to get logged in to the computer and brought up nautilus. The bookmarks she had had there were missing, and she could not see the directories within client and apps. They had zero items in them. She was able to see only /client/ and /apps/. (File structure is this: two shares, client and apps, are shared via samba; they are mounted directly to the mount point on the client.) When I ssh to wind, I can ls -alh these directories and all directories and files within them. She fixed it by rebooting the machine exactly 15 times.

Slow loading of files: to be specific, I ssh to wind and do an ls -alh /mountpoint/*. It takes an average of about 15 seconds for the listing of /apps/ to show up, then another 15 seconds for the listing of /client/ to show up--the second listing always takes longer. When I do the same to air, the times are about 3 seconds each.

PS: I am at a station within the lan, call it client1.

---

### Post by bab1 on 2016-03-21
> **dgermann said:**
> bab1--

Thank you for helping me.

Perhaps it will help to attach a drawing of the network. [ATTACH=CONFIG]267920[/ATTACH]

There is only one server: torus is the file server and the vpn server, using a tun (not tap) interface. torus.conf has client-to-client.

Both clients mentioned here, wind and air, log in via vpn. Each sits behind a separate router (people are working from home). There are other computers also behind their individual routers, but they do not connect with these clients.

I don't know a way for either client to ssh to torus, or for torus to ssh to the clients, without going through the vpn. I do not even know their ipaddresses, nor have access to their routers to forward the traffic to these clients. These clients establish connection via vpn and a ddns, and then I can "see" them.

As far as I know, everything else is the same on these two clients: the openvpn conf files are the same; the os is the same; the file structure is the same.

Additional symptoms: Just this weekend the person using wind told me these symptoms: She was able to get logged in to the computer and brought up nautilus. The bookmarks she had had there were missing, and she could not see the directories within client and apps. They had zero items in them. She was able to see only client and apps. (File structure is this: two shares, client and apps, are shared via samba; they are mounted directly to the mount point on the client.) When I ssh to wind, I can ls -alh these directories and all directories and files within them. She fixed it by rebooting the machine exactly 15 times.

Slow loading of files: to be specific, I ssh to wind and do an ls -alh /mountpoint/*. It takes an average of about 15 seconds for the listing of apps to show up, then another 15 seconds for the listing of client to show up--the second listing always takes longer. When I do the same to air, the times are about 3 seconds each.

Restating the above:
There is only one host of both the VPN and Samba server.  Its host name is *_torus_*.  There are 2 clients.  They are *_wind_* and *_air_*.  Both clients are on foreign networks (not under your control).  Both clients connect via the VPN to *torus* using DDNS for name resolution.

My *opinion* along with a BIG caveat that I'm *not* an OpenVPN user at all is this:   You should not need to both create a VPN and use SSH for the client to connect to the server.  Since the service (Samba file sharing) is a LAN service only, you should just use the VPN itself.  You also have an added point of failure with the DDNS service included in the name services.  

Never the less, I think you will find differences between wind and air in the conf files,  I would start by comparing the statistics of **air to torus/torus to air ** and **wind to torus/torus to wind**.

My ignorance forces me to ask:  Why are you using Point to Point connections with OpenVPN?

---

### Post by dgermann on 2016-03-21
bab1--

My neophyte's view is that I have always been able to connect to each of these clients via ssh over the vpn, so I am guessing the vpn (and the intermediate ddns service) is not the issue. I have been wrong before.

You have restated things accurately and clearly.

The clients do not use ssh to connect to the server. They use only the vpn connection. I use ssh to do updates and such on these two clients, and to trouble shoot. That's all ssh is used for.

Client to client is what allows me to ssh directly to these two clients, without having to ssh to the server first, if I recall at least one reason it was set up that way.

So which statistics should I be checking and how do I check those? Are those the ones I posted in my first post or something else?

---

### Post by bab1 on 2016-03-21
> **dgermann said:**
> bab1--

My neophyte's view is that I have always been able to connect to each of these clients via ssh over the vpn, so I am guessing the vpn (and the intermediate ddns service) is not the issue. I have been wrong before.

You have restated things accurately and clearly.

The clients do not use ssh to connect to the server. They use only the vpn connection. I use ssh to do updates and such on these two clients, and to trouble shoot. That's all ssh is used for.

Client to client is what allows me to ssh directly to these two clients, without having to ssh to the server first, if I recall at least one reason it was set up that way.

So which statistics should I be checking and how do I check those? Are those the ones I posted in my first post or something else?

I think that **ping **(in both directions), **route **, **ifconfig -a** and the configuration files for both clients will be enough to start.

---

### Post by dgermann on 2016-03-22
bab1--

Thank you. Here you go:

From torus, the server:
```
doug@torus:~$ ping -c 10 wind
PING wind (10.8.20.13) 56(84) bytes of data.
64 bytes from wind (10.8.20.13): icmp_seq=1 ttl=64 time=63.7 ms
64 bytes from wind (10.8.20.13): icmp_seq=2 ttl=64 time=61.9 ms
64 bytes from wind (10.8.20.13): icmp_seq=3 ttl=64 time=64.7 ms
64 bytes from wind (10.8.20.13): icmp_seq=4 ttl=64 time=63.1 ms
64 bytes from wind (10.8.20.13): icmp_seq=5 ttl=64 time=62.6 ms
64 bytes from wind (10.8.20.13): icmp_seq=6 ttl=64 time=61.9 ms
64 bytes from wind (10.8.20.13): icmp_seq=7 ttl=64 time=61.9 ms
64 bytes from wind (10.8.20.13): icmp_seq=8 ttl=64 time=63.3 ms
64 bytes from wind (10.8.20.13): icmp_seq=9 ttl=64 time=62.0 ms
64 bytes from wind (10.8.20.13): icmp_seq=10 ttl=64 time=62.6 ms

--- wind ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 61.953/62.813/64.746/0.934 ms

doug@torus:~$ ping -c 10 air
PING air (10.8.20.21) 56(84) bytes of data.
64 bytes from air (10.8.20.21): icmp_seq=1 ttl=64 time=24.5 ms
64 bytes from air (10.8.20.21): icmp_seq=2 ttl=64 time=28.0 ms
64 bytes from air (10.8.20.21): icmp_seq=3 ttl=64 time=25.3 ms
64 bytes from air (10.8.20.21): icmp_seq=4 ttl=64 time=25.3 ms
64 bytes from air (10.8.20.21): icmp_seq=5 ttl=64 time=23.5 ms
64 bytes from air (10.8.20.21): icmp_seq=6 ttl=64 time=41.7 ms
64 bytes from air (10.8.20.21): icmp_seq=7 ttl=64 time=23.7 ms
64 bytes from air (10.8.20.21): icmp_seq=8 ttl=64 time=27.1 ms
64 bytes from air (10.8.20.21): icmp_seq=9 ttl=64 time=26.8 ms
64 bytes from air (10.8.20.21): icmp_seq=10 ttl=64 time=37.7 ms

--- air ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9015ms
rtt min/avg/max/mdev = 23.588/28.405/41.760/5.904 ms
doug@torus:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         router          0.0.0.0         UG    0      0        0 eth1
10.8.20.0       10.8.20.2       255.255.255.0   UG    0      0        0 tun0
10.8.20.2       *               255.255.255.255 UH    0      0        0 tun0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
doug@torus:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr [blanked]  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:b1a20000-b1a3ffff 

eth1      Link encap:Ethernet  HWaddr  [blanked]  
          inet addr:192.168.0.203  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:17ff:feb9:eec5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50281238 errors:0 dropped:11182 overruns:0 frame:0
          TX packets:78139221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20530985750 (20.5 GB)  TX bytes:105378873187 (105.3 GB)
          Memory:b1a00000-b1a1ffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:496 (496.0 B)  TX bytes:496 (496.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.20.1  P-t-P:10.8.20.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:88189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:7467228 (7.4 MB)  TX bytes:7502963 (7.5 MB)

doug@torus:~$ 
```

From wind, the problem client:
```
doug@wind:~$ ping -c 10 torus
PING torus (10.8.20.1) 56(84) bytes of data.
64 bytes from torus (10.8.20.1): icmp_req=1 ttl=64 time=70.7 ms
64 bytes from torus (10.8.20.1): icmp_req=2 ttl=64 time=69.6 ms
64 bytes from torus (10.8.20.1): icmp_req=3 ttl=64 time=61.4 ms
64 bytes from torus (10.8.20.1): icmp_req=4 ttl=64 time=71.9 ms
64 bytes from torus (10.8.20.1): icmp_req=5 ttl=64 time=62.2 ms
64 bytes from torus (10.8.20.1): icmp_req=6 ttl=64 time=62.3 ms
64 bytes from torus (10.8.20.1): icmp_req=7 ttl=64 time=61.4 ms
64 bytes from torus (10.8.20.1): icmp_req=8 ttl=64 time=62.0 ms
64 bytes from torus (10.8.20.1): icmp_req=9 ttl=64 time=62.8 ms
64 bytes from torus (10.8.20.1): icmp_req=10 ttl=64 time=62.3 ms

--- torus ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 61.431/64.697/71.976/4.040 ms
doug@wind:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.8.20.0       10.8.20.14      255.255.255.0   UG    0      0        0 tun2
10.8.20.14      *               255.255.255.255 UH    0      0        0 tun2
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
doug@wind:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr  [blanked]  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::feaa:14ff:fea7:61a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49163895 (49.1 MB)  TX bytes:4955051 (4.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22676 (22.6 KB)  TX bytes:22676 (22.6 KB)

tun2      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.20.13  P-t-P:10.8.20.14  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1048521 (1.0 MB)  TX bytes:1231423 (1.2 MB)

doug@wind:~$ cat /etc/openvpn/torus.conf 
client
dev tun2
proto udp
remote  [blanked]
resolv-retry infinite
nobind
persist-key
persist-tun
dh dh4096torus.pem
ca /etc/openvpn/caontorus.crt
cert /etc/openvpn/windontorus.crt
key /etc/openvpn/windontorus.key
remote-cert-tls server
comp-lzo
verb 3
tls-auth /etc/openvpn/taontorus.key 1


doug@wind:~$ 
```

From air, the client working ok:
```
doug@air:~$ ping -c 10 torus
PING torus (10.8.20.1) 56(84) bytes of data.
64 bytes from torus (10.8.20.1): icmp_req=1 ttl=64 time=16.9 ms
64 bytes from torus (10.8.20.1): icmp_req=2 ttl=64 time=17.5 ms
64 bytes from torus (10.8.20.1): icmp_req=3 ttl=64 time=17.6 ms
64 bytes from torus (10.8.20.1): icmp_req=4 ttl=64 time=16.8 ms
64 bytes from torus (10.8.20.1): icmp_req=5 ttl=64 time=15.9 ms
64 bytes from torus (10.8.20.1): icmp_req=6 ttl=64 time=21.2 ms
64 bytes from torus (10.8.20.1): icmp_req=7 ttl=64 time=17.4 ms
64 bytes from torus (10.8.20.1): icmp_req=8 ttl=64 time=16.6 ms
64 bytes from torus (10.8.20.1): icmp_req=9 ttl=64 time=16.3 ms
64 bytes from torus (10.8.20.1): icmp_req=10 ttl=64 time=17.2 ms

--- torus ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 15.904/17.373/21.255/1.400 ms
doug@air:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
10.0.0.1        *               255.255.255.255 UH    0      0        0 eth0
10.8.20.0       10.8.20.22      255.255.255.0   UG    0      0        0 tun2
10.8.20.22      *               255.255.255.255 UH    0      0        0 tun2
link-local      *               255.255.0.0     U     1000   0        0 eth0
doug@air:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr  [blanked]  
          inet addr:10.0.0.240  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:245:c600:cb17:4847:1f3f:a1a8:ab6f/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17:813c:7b18:d860:1584/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17:fd60:ae92:1323:2eba/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17:a0ed:63af:e715:fe94/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17:c925:2781:31be:a8a6/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17:216:76ff:fe20:f6f6/64 Scope:Global
          inet6 addr: fe80::216:76ff:fe20:f6f6/64 Scope:Link
          inet6 addr: 2601:245:c600:cb17:5935:7996:fa74:5093/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17::cbca/128 Scope:Global
          inet6 addr: 2601:245:c600:cb17:6da6:e282:7070:5ae8/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:626259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:266242440 (266.2 MB)  TX bytes:26454964 (26.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:866 errors:0 dropped:0 overruns:0 frame:0
          TX packets:866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63634 (63.6 KB)  TX bytes:63634 (63.6 KB)

tun2      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.20.21  P-t-P:10.8.20.22  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:36480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3473555 (3.4 MB)  TX bytes:4648707 (4.6 MB)

doug@air:~$ cat /etc/openvpn/torus.conf 
client
dev tun2
proto udp
remote  [blanked]
resolv-retry infinite
nobind
persist-key
persist-tun
dh dh4096torus.pem
ca /etc/openvpn/caontorus.crt
cert /etc/openvpn/airontorus.crt
key /etc/openvpn/airontorus.key
remote-cert-tls server
comp-lzo
verb 3
tls-auth taontorus.key 1



doug@air:~$ 
```

---

### Post by bab1 on 2016-03-22
> **dgermann said:**
> bab1--

Thank you. Here you go:

From torus, the server:
```
doug@torus:~$ ping -c 10 wind
PING wind (10.8.20.13) 56(84) bytes of data.
64 bytes from wind (10.8.20.13): icmp_seq=1 ttl=64 time=63.7 ms
64 bytes from wind (10.8.20.13): icmp_seq=2 ttl=64 time=61.9 ms
64 bytes from wind (10.8.20.13): icmp_seq=3 ttl=64 time=64.7 ms
64 bytes from wind (10.8.20.13): icmp_seq=4 ttl=64 time=63.1 ms
64 bytes from wind (10.8.20.13): icmp_seq=5 ttl=64 time=62.6 ms
64 bytes from wind (10.8.20.13): icmp_seq=6 ttl=64 time=61.9 ms
64 bytes from wind (10.8.20.13): icmp_seq=7 ttl=64 time=61.9 ms
64 bytes from wind (10.8.20.13): icmp_seq=8 ttl=64 time=63.3 ms
64 bytes from wind (10.8.20.13): icmp_seq=9 ttl=64 time=62.0 ms
64 bytes from wind (10.8.20.13): icmp_seq=10 ttl=64 time=62.6 ms

--- wind ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 61.953/62.813/64.746/0.934 ms

doug@torus:~$ ping -c 10 air
PING air (10.8.20.21) 56(84) bytes of data.
64 bytes from air (10.8.20.21): icmp_seq=1 ttl=64 time=24.5 ms
64 bytes from air (10.8.20.21): icmp_seq=2 ttl=64 time=28.0 ms
64 bytes from air (10.8.20.21): icmp_seq=3 ttl=64 time=25.3 ms
64 bytes from air (10.8.20.21): icmp_seq=4 ttl=64 time=25.3 ms
64 bytes from air (10.8.20.21): icmp_seq=5 ttl=64 time=23.5 ms
64 bytes from air (10.8.20.21): icmp_seq=6 ttl=64 time=41.7 ms
64 bytes from air (10.8.20.21): icmp_seq=7 ttl=64 time=23.7 ms
64 bytes from air (10.8.20.21): icmp_seq=8 ttl=64 time=27.1 ms
64 bytes from air (10.8.20.21): icmp_seq=9 ttl=64 time=26.8 ms
64 bytes from air (10.8.20.21): icmp_seq=10 ttl=64 time=37.7 ms

--- air ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9015ms
rtt min/avg/max/mdev = 23.588/28.405/41.760/5.904 ms
doug@torus:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         router          0.0.0.0         UG    0      0        0 eth1
10.8.20.0       10.8.20.2       255.255.255.0   UG    0      0        0 tun0
10.8.20.2       *               255.255.255.255 UH    0      0        0 tun0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
doug@torus:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr [blanked]  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:b1a20000-b1a3ffff 

eth1      Link encap:Ethernet  HWaddr  [blanked]  
          inet addr:192.168.0.203  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:17ff:feb9:eec5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50281238 errors:0 dropped:11182 overruns:0 frame:0
          TX packets:78139221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20530985750 (20.5 GB)  TX bytes:105378873187 (105.3 GB)
          Memory:b1a00000-b1a1ffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:496 (496.0 B)  TX bytes:496 (496.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.20.1  P-t-P:10.8.20.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:88189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:7467228 (7.4 MB)  TX bytes:7502963 (7.5 MB)

doug@torus:~$ 
```

From wind, the problem client:
```
doug@wind:~$ ping -c 10 torus
PING torus (10.8.20.1) 56(84) bytes of data.
64 bytes from torus (10.8.20.1): icmp_req=1 ttl=64 time=70.7 ms
64 bytes from torus (10.8.20.1): icmp_req=2 ttl=64 time=69.6 ms
64 bytes from torus (10.8.20.1): icmp_req=3 ttl=64 time=61.4 ms
64 bytes from torus (10.8.20.1): icmp_req=4 ttl=64 time=71.9 ms
64 bytes from torus (10.8.20.1): icmp_req=5 ttl=64 time=62.2 ms
64 bytes from torus (10.8.20.1): icmp_req=6 ttl=64 time=62.3 ms
64 bytes from torus (10.8.20.1): icmp_req=7 ttl=64 time=61.4 ms
64 bytes from torus (10.8.20.1): icmp_req=8 ttl=64 time=62.0 ms
64 bytes from torus (10.8.20.1): icmp_req=9 ttl=64 time=62.8 ms
64 bytes from torus (10.8.20.1): icmp_req=10 ttl=64 time=62.3 ms

--- torus ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 61.431/64.697/71.976/4.040 ms
doug@wind:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.8.20.0       10.8.20.14      255.255.255.0   UG    0      0        0 tun2
10.8.20.14      *               255.255.255.255 UH    0      0        0 tun2
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
doug@wind:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr  [blanked]  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::feaa:14ff:fea7:61a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49163895 (49.1 MB)  TX bytes:4955051 (4.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22676 (22.6 KB)  TX bytes:22676 (22.6 KB)

tun2      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.20.13  P-t-P:10.8.20.14  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1048521 (1.0 MB)  TX bytes:1231423 (1.2 MB)

doug@wind:~$ cat /etc/openvpn/torus.conf 
client
dev tun2
proto udp
remote  [blanked]
resolv-retry infinite
nobind
persist-key
persist-tun
dh dh4096torus.pem
ca /etc/openvpn/caontorus.crt
cert /etc/openvpn/windontorus.crt
key /etc/openvpn/windontorus.key
remote-cert-tls server
comp-lzo
verb 3
tls-auth /etc/openvpn/taontorus.key 1


doug@wind:~$ 
```

From air, the client working ok:
```
doug@air:~$ ping -c 10 torus
PING torus (10.8.20.1) 56(84) bytes of data.
64 bytes from torus (10.8.20.1): icmp_req=1 ttl=64 time=16.9 ms
64 bytes from torus (10.8.20.1): icmp_req=2 ttl=64 time=17.5 ms
64 bytes from torus (10.8.20.1): icmp_req=3 ttl=64 time=17.6 ms
64 bytes from torus (10.8.20.1): icmp_req=4 ttl=64 time=16.8 ms
64 bytes from torus (10.8.20.1): icmp_req=5 ttl=64 time=15.9 ms
64 bytes from torus (10.8.20.1): icmp_req=6 ttl=64 time=21.2 ms
64 bytes from torus (10.8.20.1): icmp_req=7 ttl=64 time=17.4 ms
64 bytes from torus (10.8.20.1): icmp_req=8 ttl=64 time=16.6 ms
64 bytes from torus (10.8.20.1): icmp_req=9 ttl=64 time=16.3 ms
64 bytes from torus (10.8.20.1): icmp_req=10 ttl=64 time=17.2 ms

--- torus ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 15.904/17.373/21.255/1.400 ms
doug@air:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
10.0.0.1        *               255.255.255.255 UH    0      0        0 eth0
10.8.20.0       10.8.20.22      255.255.255.0   UG    0      0        0 tun2
10.8.20.22      *               255.255.255.255 UH    0      0        0 tun2
link-local      *               255.255.0.0     U     1000   0        0 eth0
doug@air:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr  [blanked]  
          inet addr:10.0.0.240  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:245:c600:cb17:4847:1f3f:a1a8:ab6f/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17:813c:7b18:d860:1584/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17:fd60:ae92:1323:2eba/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17:a0ed:63af:e715:fe94/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17:c925:2781:31be:a8a6/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17:216:76ff:fe20:f6f6/64 Scope:Global
          inet6 addr: fe80::216:76ff:fe20:f6f6/64 Scope:Link
          inet6 addr: 2601:245:c600:cb17:5935:7996:fa74:5093/64 Scope:Global
          inet6 addr: 2601:245:c600:cb17::cbca/128 Scope:Global
          inet6 addr: 2601:245:c600:cb17:6da6:e282:7070:5ae8/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:626259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:266242440 (266.2 MB)  TX bytes:26454964 (26.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:866 errors:0 dropped:0 overruns:0 frame:0
          TX packets:866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63634 (63.6 KB)  TX bytes:63634 (63.6 KB)

tun2      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.20.21  P-t-P:10.8.20.22  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:36480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3473555 (3.4 MB)  TX bytes:4648707 (4.6 MB)

doug@air:~$ cat /etc/openvpn/torus.conf 
client
dev tun2
proto udp
remote  [blanked]
resolv-retry infinite
nobind
persist-key
persist-tun
dh dh4096torus.pem
ca /etc/openvpn/caontorus.crt
cert /etc/openvpn/airontorus.crt
key /etc/openvpn/airontorus.key
remote-cert-tls server
comp-lzo
verb 3
tls-auth taontorus.key 1



doug@air:~$ 
```
I don't see any differences between the 2 clients.  In fact I don't see a network problem at all.  Although there are ttl time differences, they are not out of the norm.   What do you when you use this command from both clients to the server (also, how long does it take for a reply)```
smbtree
```

---

### Post by dgermann on 2016-03-23
bab1--

On both machines I get:
```
doug@air:~$ smbtree
Enter doug's password: 
doug@air:~$ 

```

In other words, nothing. 

Running as sudo, does not do anything differently. (It asks for root's password; there is none.)

Trying this:
```

doug@air:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=2601:245:c600:cb17::cbca bcast=2601:245:c600:cb17::cbca netmask=ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
added interface eth0 ip=2601:245:c600:cb17:216:76ff:fe20:f6f6 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:4847:1f3f:a1a8:ab6f bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:5935:7996:fa74:5093 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:6da6:e282:7070:5ae8 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:704e:31ac:a1aa:1704 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:a0ed:63af:e715:fe94 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:c925:2781:31be:a8a6 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:fd60:ae92:1323:2eba bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=fe80::216:76ff:fe20:f6f6%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=10.0.0.240 bcast=10.0.0.255 netmask=255.255.255.0
Enter doug's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
doug@air:~$ 

doug@wind:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::feaa:14ff:fea7:61a%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.102 bcast=192.168.1.255 netmask=255.255.255.0
Enter doug's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
doug@wind:~$ 

```

I think it is looking the wrong place.

Responses are pretty much instantaneous.

Thanks!

---

### Post by bab1 on 2016-03-23
> **dgermann said:**
> bab1--

On both machines I get:
```
doug@air:~$ smbtree
Enter doug's password: 
doug@air:~$ 

```

In other words, nothing. 


I think it is looking the wrong place.

Responses are pretty much instantaneous.

Thanks!
It sure does, but this only means that you can't browse the shares from the clients.  FWIW, you should not need to do any diagnosis as root (root) with Samba clients.

To check whether the client can see a share on the specific server you can try this> smbclient -d3 L torus

---

### Post by dgermann on 2016-03-24
bab1--

Did this:
```
doug@wind:~$ smbclient -d3 -L torus
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::feaa:14ff:fea7:61a%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.102 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.6.3).
Enter doug's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name torus<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name torus<0x20>
resolve_wins: Attempting wins lookup for name torus<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name torus<0x20>
Connecting to 10.8.20.1 at port 445
Connecting to 10.8.20.1 at port 139
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[EVERYONE] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (torus server (Samba, Ubuntu))
	client          Disk      
	apps            Disk      
resolve_lmhosts: Attempting lmhosts lookup for name torus<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name torus<0x20>
resolve_wins: Attempting wins lookup for name torus<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name torus<0x20>
Connecting to 10.8.20.1 at port 139
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[EVERYONE] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	EARTH                earth server (Samba, Ubuntu)
	SHARON2              sharon2
	TORUS                torus server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	EVERYONE             TORUS
	WORKGROUP            BAK
doug@wind:~$ 


```

And air:
```
doug@air:~$ smbclient -d3 -L torus
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=2601:245:c600:cb17::cbca bcast=2601:245:c600:cb17::cbca netmask=ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
added interface eth0 ip=2601:245:c600:cb17:216:76ff:fe20:f6f6 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:4847:1f3f:a1a8:ab6f bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:5935:7996:fa74:5093 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:6da6:e282:7070:5ae8 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:704e:31ac:a1aa:1704 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:a0ed:63af:e715:fe94 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:c925:2781:31be:a8a6 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2601:245:c600:cb17:f44b:ccd4:aa01:9265 bcast=2601:245:c600:cb17:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=fe80::216:76ff:fe20:f6f6%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=10.0.0.240 bcast=10.0.0.255 netmask=255.255.255.0
Client started (version 3.6.3).
Enter doug's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name torus<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name torus<0x20>
resolve_wins: Attempting wins lookup for name torus<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name torus<0x20>
Connecting to 10.8.20.1 at port 445
Connecting to 10.8.20.1 at port 139
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[EVERYONE] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (torus server (Samba, Ubuntu))
	client          Disk      
	apps            Disk      
resolve_lmhosts: Attempting lmhosts lookup for name torus<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name torus<0x20>
resolve_wins: Attempting wins lookup for name torus<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name torus<0x20>
Connecting to 10.8.20.1 at port 139
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[EVERYONE] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	EARTH                earth server (Samba, Ubuntu)
	SHARON2              sharon2
	TORUS                torus server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	EVERYONE             TORUS
	WORKGROUP            BAK
doug@air:~$ 

```


Do these tell us anything useful?

---

### Post by bab1 on 2016-03-24
> **dgermann said:**
> bab1--
Do these tell us anything useful?
I need some context here.  How long did it take to get the returned info?  I see the shares?

I think you should unmount the share you have set in fstab and see if you cam mount the same share manually with something simple such as```

 sudo mount -t cifs //torus/data /media/<temp_mount_point> -o user=<your_user_name>
```...use your network variables for the <temp_mount_point> and <your_user_name>.

You can confirm the mount is successful with this ```
mount
```...the mounted share should be at the bottom of the screen.  If you can mount the share; how long did it take and can you see the data in the share using the file manager?

---

### Post by dgermann on 2016-03-24
bab1--

Many thanks!

Forgot to say: the info you see came up instantly: then entered password requested and its results showed up instantly too.

As you suggested, on wind I umounted and then cli mounted the shares; after the mount command I get:
```
//torus/apps on /sam/apps type cifs (rw)
//torus/client on /sam/client type cifs (rw)
```

From cli I issue ls -alh at :00 on the clock; /apps comes up at :13 seconds, and /client at :30; so no improvement in speed. My person is not there so I cannot tell you what the nautilus results would be.

Remounted using fstab and got these times: :11 and :25. To me those are about the same as the others. For comparison, on air at the moment I am getting: :04 and :07.

Some other way to test the file manager without a person sitting at the monitor? Perhaps using top?

---

### Post by bab1 on 2016-03-24
> **dgermann said:**
> bab1--

Many thanks!

Forgot to say: the info you see came up instantly: then entered password requested and its results showed up instantly too.

As you suggested, on wind I umounted and then cli mounted the shares; after the mount command I get:
```
//torus/apps on /sam/apps type cifs (rw)
//torus/client on /sam/client type cifs (rw)
```

From cli I issue ls -alh at :00 on the clock; /apps comes up at :13 seconds, and /client at :30; so no improvement in speed. My person is not there so I cannot tell you what the nautilus results would be.

Remounted using fstab and got these times: :11 and :25. To me those are about the same as the others. For comparison, on air at the moment I am getting: :04 and :07.

Some other way to test the file manager without a person sitting at the monitor? Perhaps using top?
There is no way to test Nautilus remotely.  On the other hand I don't see much to test.  There doesn't appear to be a name service problem, nor is there a problem with share definitions.  The VPN seems to work correctly.  I have to assume that torus is a relatively modern machine with reasonable I/O stats for the HDD's.

This leaves you with a WAN problem.  Any testing of this will have to originate from the client itself.  I'm not the one to advise on your WAN problems.  I've always had the luxury of having a network admin on staff.  So I just started a ticket and waited for the results.  In your case this means talking to the ISP that your remote client uses.  [**Here**]("https://www.google.com/search?client=ubuntu&channel=fs&q=wan+speed+testing+ubuntu&ie=utf-8&oe=utf-8") is a Google search that should provide you with some info to use when talking to the ISP rep.  I have no more ideas.

---

### Post by dgermann on 2016-03-24
bab1--

Thank you for all the wonderful help you have been!

I will check out those speed tests you have pointed me to. You've given me an idea: perhaps the problem is the isp at the other end. I think wind, air, and I may in fact be on three different isps.

[INDENT]So I did test these and found air and I are on one isp, wind is on another. Speeds on wind d/l 2.17 and 2.42 Mbit/s; up 0.25 & 0.30; on air d/l 72.10 and 63.77, and up 9.89 and 11.41. So this might account for it.[/INDENT]

Yes, torus is a machine new in the last 6 months, designed as a server and all solid state drives, so I think it is quite fast. At least much more expensive!

In between our posts I was checking out other things to test speed: pv and mc. pv just showed me things were slow. mc opened the directories in a half second or so each; on my local machine it was instantaneous.

OTOH, does the fact that nautilus sometimes does not list the files at all suggest this might be more than a speed issue? (It is almost as if it sees the mount point, but the files are invisible to nautilus.) Thoughts about that?

Thank you very very much, bab1!

---

### Post by bab1 on 2016-03-24
> **dgermann said:**
> 
OTOH, does the fact that nautilus sometimes does not list the files at all suggest this might be more than a speed issue? (It is almost as if it sees the mount point, but the files are invisible to nautilus.) Thoughts about that?

The data displayed does not come to the machine in one chunk.  It comes in small packets and is reassembled.  If enough data arrives that the display can start it will do that.  You need to speak to the ISP from here on.

---

### Post by dgermann on 2016-03-24
Will do!

Many thanks. See above edits for speed test results.

---

