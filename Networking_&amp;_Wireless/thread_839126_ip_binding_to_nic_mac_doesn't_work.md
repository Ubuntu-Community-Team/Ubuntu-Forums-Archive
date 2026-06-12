---
title: "ip binding to nic mac doesn't work"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by orennu on 2008-06-24
hello all
i'm having a strange issue.
I have a cisco 831 router configured to bind ip with mac address
I have 2 computers 1's a desktop connected to lan the other is laptop connected through AP that's connected to the router.
I'm connected to the network on both computers but i'm not getting the ip I assigned in the router.
the strange thing is that in same pc's i also have vista running and i'm getting the ip i assigned.
i'm adding the output of the cisco ,the linux output i'll add later
:
ip dhcp pool PC-LAN
   host 192.168.10.10 255.255.255.0
   client-identifier 0100.1d7d.045a.ce
   default-router 192.168.10.254
   lease infinite
!
ip dhcp pool NOTEBOOK-LAN
   host 192.168.10.20 255.255.255.0
   client-identifier 0100.19d2.25a6.10
   default-router 192.168.10.254
   lease infinite

---

### Post by orennu on 2008-06-26
here's my ifconfig output :

oren@oren-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet _ HWaddr 00:19:d2:25:a6:10  _
          inet addr:_[U]192.168.10.1_[/U]  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe25:a610/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1592 (1.5 KB)  TX bytes:7218 (7.0 KB)


as you can see i should be getting 192.168.10.20

anyone?

---

