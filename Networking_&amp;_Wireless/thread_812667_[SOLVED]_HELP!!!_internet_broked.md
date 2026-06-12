---
title: "[SOLVED] HELP!!! internet broked"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by i.am.technofreak on 2008-05-30
hi
i have been playing around with dhcp servers and relays on my eee, if followed these instructions [http://ubuntuforums.org/showthread.php?t=335465](http://ubuntuforums.org/showthread.php?t=335465) and rebooted because the dhcp wouldn't start, and now my eth0 will connect to my router and get ips and all that, but i cannot ping anything and the internet isn't working.  It very bad.  im guessing it was some of that command line stuff that changed some settings but i don't know what they were in the first place!  i am running eeexubuntu 7.10.
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1E:8C:E4:65:2B  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21e:8cff:fee4:652b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:6716 (6.5 KB)  TX bytes:0 (0.0 b)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

/etc/network/interfaces:


auto lo
iface lo inet loopback

route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth0

thanks
technofreak

---

### Post by superprash2003 on 2008-05-30
are you able to ping your router?

---

### Post by i.am.technofreak on 2008-05-30
ping 10.1.1.1:
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 10.1.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3000ms

same result for sudo ping 10.1.1.1
10.1.1.1 is my router

---

### Post by i.am.technofreak on 2008-06-06
fixed it, just reinstalled me os

---

