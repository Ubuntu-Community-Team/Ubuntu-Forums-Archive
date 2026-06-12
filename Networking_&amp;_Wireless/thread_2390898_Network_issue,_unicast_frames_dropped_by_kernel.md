---
title: "Network issue, unicast frames dropped by kernel?"
date: 2018-05-03
forum: Networking &amp; Wireless
---

### Post by marcus-dahlberg on 2018-05-03
I have a weird problem. 2 days ago, I installed Ubuntu server 18.04 with DNS server selected by mistake in tasksel. After that, no internet on any Ubuntu machine connected to this network. Tried 16.04, 17.10 and 18.04. Tried on 3 different hardware.
Funny thing is, running Windows 10 and 7 on the same machine works! Taking the same setup (xUbuntu 17.10) to my neighbor next door works perfectly. So it is just the combination xUbuntu/Ubuntu and specifically my physical ISP port that stopped working.

Anyone have a clue of what is going on?





xubuntu@xubuntu:~$ ifconfig
eno1      Link encap:Ethernet  HWaddr 4c:cc:6a:23:0b:a5  
          inet addr:x.y.z.42  Bcast:x.y.z.255  Mask:255.255.255.0
          inet6 addr: aaaa::bbbb:ccc:dddd:eee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5794 (5.7 KB)  TX bytes:46175 (46.1 KB)
          Interrupt:20 Memory:fb400000-fb420000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48138 (48.1 KB)  TX bytes:48138 (48.1 KB)


xubuntu@xubuntu:~$ sudo ping x.y.z.1
PING x.y.z.1 (x.y.z.1) 56(84) bytes of data.
From x.y.z.42 icmp_seq=23 Destination Host Unreachable
From x.y.z.42 icmp_seq=24 Destination Host Unreachable
From x.y.z.42 icmp_seq=25 Destination Host Unreachable
^C
--- x.y.z.1 ping statistics ---
26 packets transmitted, 0 received, +3 errors, 100% packet loss, time 25600ms
pipe 4


xubuntu@xubuntu:~/Desktop$ sudo tcpdump
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eno1, link-type EN10MB (Ethernet), capture size 262144 bytes
19:34:06.107137 IP x.y.z.42 > x.y.z.1: ICMP echo request, id 2565, seq 10, length 64
19:34:06.117316 IP x.y.z.42.33677 > 83.233.79.37.domain: 32178+ PTR? 1.y.z.89.in-addr.arpa. (42)
19:34:06.117326 IP x.y.z.42.33677 > 83.233.79.36.domain: 32178+ PTR? 1.y.z.89.in-addr.arpa. (42)
19:34:06.203088 ARP, Request who-has x.y.z.1 tell x.y.z.42, length 28
19:34:07.131131 IP x.y.z.42 > x.y.z.1: ICMP echo request, id 2565, seq 11, length 64
19:34:07.227112 ARP, Request who-has x.y.z.1 tell x.y.z.42, length 28
19:34:07.748986 IP x.y.z.42.33677 > 83.233.79.37.domain: 60544+ A? ntp.ubuntu.com. (32)
19:34:26.137801 ARP, Request who-has x.y.z.1 tell x.y.z.42, length 28
19:34:36.148076 ARP, Request who-has x.y.z.1 tell x.y.z.42, length 28
19:34:47.790332 ARP, Request who-has x.y.z.1 tell x.y.z.42, length 28
19:34:48.795092 ARP, Request who-has x.y.z.1 tell x.y.z.42, length 28
19:34:49.819117 ARP, Request who-has x.y.z.1 tell x.y.z.42, length 28
^C
12 packets captured
89 packets received by filter
77 packets dropped by kernel


xubuntu@xubuntu:~$ ip route get x.y.z.1
x.y.z.1 dev eno1  src x.y.z.42 
    cache 
    
xubuntu@xubuntu:~$ netstat -r -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         x.y.z.1     0.0.0.0         UG        0 0          0 eno1
x.y.z.0     0.0.0.0         255.255.255.0   U         0 0          0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eno1


xubuntu@xubuntu:~$ ip route show table local
broadcast x.y.z.0 dev eno1  proto kernel  scope link  src x.y.z.42 
local x.y.z.42 dev eno1  proto kernel  scope host  src x.y.z.42 
broadcast x.y.z.255 dev eno1  proto kernel  scope link  src x.y.z.42 
broadcast 127.0.0.0 dev lo  proto kernel  scope link  src 127.0.0.1 
local 127.0.0.0/8 dev lo  proto kernel  scope host  src 127.0.0.1 
local 127.0.0.1 dev lo  proto kernel  scope host  src 127.0.0.1 
broadcast 127.255.255.255 dev lo  proto kernel  scope link  src 127.0.0.1 


xubuntu@xubuntu:~$ ip rule show
0:    from all lookup local 
32766:    from all lookup main 
32767:    from all lookup default 


xubuntu@xubuntu:~$ arp -a
? (x.y.z.40) at <incomplete> on eno1
? (x.y.z.1) at <incomplete> on eno1


xubuntu@xubuntu:~$ sudo arp -s x.y.z.1 00:18:74:14:CD:00


xubuntu@xubuntu:~$ arp -a
? (x.y.z.40) at <incomplete> on eno1
? (x.y.z.1) at 00:18:74:14:cd:00 [ether] PERM on eno1


xubuntu@xubuntu:~$ sudo ping x.y.z.1
PING x.y.z.1 (x.y.z.1) 56(84) bytes of data.
^C
--- x.y.z.1 ping statistics ---
44 packets transmitted, 0 received, 100% packet loss, time 44020ms


xubuntu@xubuntu:~$ sudo ping -b x.y.z.255
WARNING: pinging broadcast address
PING x.y.z.255 (x.y.z.255) 56(84) bytes of data.
^C
--- x.y.z.255 ping statistics ---
45 packets transmitted, 0 received, 100% packet loss, time 45051ms


xubuntu@xubuntu:~/Desktop$ sudo tcpdump
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eno1, link-type EN10MB (Ethernet), capture size 262144 bytes
19:41:02.811146 IP x.y.z.42 > x.y.z.255: ICMP echo request, id 2596, seq 15, length 64
19:41:02.811890 IP x.y.z.42.33677 > 83.233.79.37.domain: 26674+ PTR? 255.y.z.89.in-addr.arpa. (44)
^C
19:41:02.811901 IP x.y.z.42.33677 > 83.233.79.36.domain: 26674+ PTR? 255.y.z.89.in-addr.arpa. (44)


3 packets captured
93 packets received by filter
84 packets dropped by kernel


xubuntu@xubuntu:~$ sudo ethtool eno1
Settings for eno1:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on (auto)
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes


WINDOS 10:
C:\>ipconfig


Windows IP Configuration




Ethernet adapter Ethernet:


   Connection-specific DNS Suffix  . : cust.abcdefgh.com
   IPv4 Address. . . . . . . . . . . : x.y.z.250
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : x.y.z.1


C:\>arp -a


Interface: x.y.z.250 --- 0xf
  Internet Address      Physical Address      Type
  x.y.z.1           00-18-74-14-cd-00     dynamic
  224.0.0.22            01-00-5e-00-00-16     static
  255.255.255.255       ff-ff-ff-ff-ff-ff     static
  
C:\>ping x.y.z.1


Pinging x.y.z.1 with 32 bytes of data:
Reply from x.y.z.1: bytes=32 time<1ms TTL=255
Reply from x.y.z.1: bytes=32 time<1ms TTL=255
Reply from x.y.z.1: bytes=32 time<1ms TTL=255
Reply from x.y.z.1: bytes=32 time<1ms TTL=255


Ping statistics for x.y.z.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

---

### Post by marcus-dahlberg on 2018-05-04
This was solved by ISP. Reset of my interface I guess.

---

