---
title: "can't ping on local network, but can ping Internet - 2 network cards 16.04LTS"
date: 2018-07-06
forum: Networking &amp; Wireless
---

### Post by markt92 on 2018-07-06
Ubuntu 16.04.3 LTS

I can ping the Internet on eno2, but can't ping local ip addresses 192.168.1.x

Other machines on 192.168.1. can ping me, but I can't ping them

192.168.1.100 is a valid machine on the local net

I think we ran these commands after boot up to get the Internet working:
    route delete default gw 192.168.1.122 eno1
    sudo route add default gw 192.168.12.1 eno2



What should I check for or how do I get both networks to work?




# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.12.1    0.0.0.0         UG    0      0        0 eno2
192.168.1.0     *               255.255.255.0   U     0      0        0 eno1
192.168.12.0    *               255.255.255.0   U     0      0        0 eno2

root@ADAMS5:~# ping 192.167.1.110
PING 192.167.1.110 (192.167.1.110) 56(84) bytes of data.
^C
--- 192.167.1.110 ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 7999ms


root@ADAMS5:~# ping google.com
PING google.com (172.217.5.14) 56(84) bytes of data.
64 bytes from lga15s49-in-f14.1e100.net (172.217.5.14): icmp_seq=1 ttl=52 time=36.7 ms


# ifconfig
eno1      Link encap:Ethernet  HWaddr d4:ae:52:ad:0a:76
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d6ae:52ff:fead:a76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94004012 errors:0 dropped:573 overruns:0 frame:0
          TX packets:14721883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9570529803 (9.5 GB)  TX bytes:12815714330 (12.8 GB)


eno2      Link encap:Ethernet  HWaddr d4:ae:52:ad:0a:77
          inet addr:192.168.12.115  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::d6ae:52ff:fead:a77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:363051409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306902234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:79608533168 (79.6 GB)  TX bytes:66873934975 (66.8 GB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:43599264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43599264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:12298010856 (12.2 GB)  TX bytes:12298010856 (12.2 GB)

---

### Post by markt92 on 2018-07-06
Silly me.  [COLOR=#000000]192.167.1.110 should have been 192.168.1.110

was working correctly the whole time[/COLOR]

---

