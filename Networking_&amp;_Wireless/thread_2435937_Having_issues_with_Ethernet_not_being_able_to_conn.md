---
title: "Having issues with Ethernet not being able to connect to the internet."
date: 2020-01-28
forum: Networking &amp; Wireless
---

### Post by mariofanboy-21 on 2020-01-28
Hello everyone. As of late, I have been having issues wih my Lubuntu installation (18.04.03) being able to connect to the internet. DO you guys know how I can fix this issue?

---

### Post by guiverc on 2020-01-28
I have an old dell optiplex 755 that stopped being my primary system because on occasion it'd power up without the NIC (network interface card) working, ie. no ethernet.  In my case it occurs on any OS, be it 'live' media, an old windows or Lubuntu 18.04 LTS, or even the BIOS doesn't detect it - ie. it's failing hardware.  A reboot usually fixes it.

If I boot Lubuntu 18.04 LTS on it, I can go to terminal and enter the command

`ip link`, ie. 

```
guiverc@d960-ubu2:~$   ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 00:26:b9:78:23:96 brd ff:ff:ff:ff:ff:ff
```

In this case I know I have ethernet (it worked, yeah!) as I see the `enp0s25` device which is my ethernet.  (*the **lo** device is loopback and I ignore that*)

Next I'd enter 'ip addr` to see my ip address 

```
guiverc@d960-ubu2:~$   ip addr
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:26:b9:78:23:96 brd ff:ff:ff:ff:ff:ff
    inet 192.168.15.138/24 brd 192.168.15.255 scope global noprefixroute enp0s25
       valid_lft forever preferred_lft forever
    inet6 fe80::eed5:5ae0:44d5:9810/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```
This shows I have an IP address which to me makes sense, ie. 192.168.15.138

Note: I've edited the results, to reduce info, simplify - plus these are copy/pasted from my replacement pc anyway as it was logged into ubuntuforums)

Next I'd run a `ip route` to see where my data gets routed

```
guiverc@d960-ubu2:~$   ip route
default via 192.168.15.16 dev enp0s25 proto static metric 100 
169.254.0.0/16 dev enp0s25 scope link metric 1000 
192.168.15.0/24 dev enp0s25 proto kernel scope link src 192.168.15.138 metric 100 

```

showing my external traffic (default) gets routed ti 192.168.15.16 which I know is a valid routed correctly.

I can ping that router, ie.

```
guiverc@d960-ubu2:~$   ping -c 1 192.168.15.16
PING 192.168.15.16 (192.168.15.16) 56(84) bytes of data.
64 bytes from 192.168.15.16: icmp_seq=1 ttl=64 time=0.796 ms


--- 192.168.15.16 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.796/0.796/0.796/0.000 ms

```
Next I'll ping an easy external address; oogle's DNS

```
guiverc@d960-ubu2:~$   ping -c 1 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=54 time=26.2 ms


--- 8.8.8.8 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 26.157/26.157/26.157/0.000 ms

```
Finally I'll ping using DNS, ie. human names

```
guiverc@d960-ubu2:~$   ping -c 1 dns.google.com
PING dns.google.com (8.8.8.8) 56(84) bytes of data.
64 bytes from dns.google (8.8.8.8): icmp_seq=1 ttl=54 time=22.6 ms


--- dns.google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 22.646/22.646/22.646/0.000 ms

```


which shows my system is good.  Do you get valid results for all these steps? or any are markedly different to what I did?

---

