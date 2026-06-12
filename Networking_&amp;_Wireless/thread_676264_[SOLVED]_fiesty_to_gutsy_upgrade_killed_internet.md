---
title: "[SOLVED] fiesty to gutsy upgrade killed internet"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by netsplit on 2008-01-23
Okay so posting this from windows. Hoping I have all the needed info to troubleshoot this in this post, if there's more data you need, be happy to restart and oblige.

I have no internet access from linux.  I upgraded from feisty to gutsy using the upgrade tool. Everything seems to go okay except for my internet died. I connect with pppd using a 3g cellular internet card (seirra wireless aircard 875U, using the guide from [here](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607) ). The driver is already in the kernal. It was working before so I think that is okay. Basically it connects but linux refuses to access ppp0.


okay here's the output from trying to ping the remote gateway, ifconfig, and route -n (10.192.0.1 is the remote gateway on the NAT)

```

link@owner-pc:~$ ping 10.192.0.1
PING 10.192.0.1 (10.192.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 10.192.0.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3003ms

link@owner-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:92:2F:FB:47
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe2f:fb47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:14785 (14.4 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12085 (11.8 KB)  TX bytes:12085 (11.8 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:10.192.9.25  P-t-P:10.192.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:138 (138.0 b)  TX bytes:207 (207.0 b)

link@owner-pc:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.192.0.1      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.192.0.1      0.0.0.0         UG    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
link@owner-pc:~$

```

The
0.0.0.0         10.192.0.1      0.0.0.0         UG    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
wasn't there before but I tried a

 route add default gw  10.192.0.1 

or something close to that while trying to figure it out.

Any help would be much appreciated.

---

### Post by netsplit on 2008-01-23
Okay so I hooked another computer up and used it for the net. eth0 is having the same trouble! Well sorta. DNS works. It just can't connect to any sites, but it can look up their ip address just fine.

I read a missconfigured IP tables could do that, but I can't see anything that would do that in my tables

```

link@owner-pc:~$ sudo iptables -L -n -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
  281 27405 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0
    0     0 LOG        0    --  !lo    *       127.0.0.0/8          0.0.0.0/0           LOG flags 0 level 4
    0     0 DROP       0    --  !lo    *       127.0.0.0/8          0.0.0.0/0
    4  1338 ACCEPT     0    --  eth0   *       0.0.0.0/0            255.255.255.255
82040   82M ACCEPT     0    --  eth0   *       192.168.0.0/24       0.0.0.0/0
    0     0 ACCEPT    !tcp  --  eth0   *       0.0.0.0/0            224.0.0.0/4
    0     0 DROP       0    --  *      *       0.0.0.0/0            224.0.0.1
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       0    --  *      *       0.0.0.0/0            224.0.0.1
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
  281 27405 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     0    --  *      eth0    0.0.0.0/0            255.255.255.255
57924 3232K ACCEPT     0    --  *      eth0    0.0.0.0/0            192.168.0.0/24
  313 46410 ACCEPT    !tcp  --  *      eth0    0.0.0.0/0            224.0.0.0/4
    0     0 DROP       0    --  *      *       0.0.0.0/0            224.0.0.1
  827 59808 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4
  827 59808 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0

```

Any ideas?

---

### Post by netsplit on 2008-01-23
btw network still works as I'm vncing to a computer on the network for net.

---

### Post by netsplit on 2008-01-25
okay so got it fixed on the off chance anyone else has this trouble. After a bunch of messing around and general wtfness noticed ipmasq was installed, which I needed for sharing the internet. Uninstalled that and it works fine. Now to try reinstalling it...

---

