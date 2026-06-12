---
title: "Joining a UDP multicast through a machine on the other side of a tunnel"
date: 2016-04-16
forum: Networking &amp; Wireless
---

### Post by Yoshi9143 on 2016-04-16
Hi All,

Been a lurker here and posted this question on serverfault with no answers yet. Hoping you all will be able to help as I'm a bit of a networking newb, but have been reading everything I can to solve this problem. I think I am now hitting the case of things I don't know I don't know. If you all could point me in the right direction it would help me so much. 

I drew a diagram if it's helpful!

So a company publishes a multicast UDP feed (company A) and another company connects to it (Company B). I have a point-to-point tunnel to Company B.

How can I get my machine to join the multicast group Company A is publishing via company B's machine?

I can ping company B's machine just fine from the terminal if we do

```
    ping 192.168.255.1
```

But given the Python script below, I am not getting any data back. My guess is because I am not routing packets from 192.168.255.2 (my machine) to 192.168.255.1 (company B's machine)
Any idea on how to do this in the best manner?  And if so, how could I implement this?


Diagram:
[IMG]http://i.stack.imgur.com/tqbvj.png[/IMG]


Here is the socket code I am using (Python):
```


    import socket
    import struct
    
    MCAST_GRP = '233.xxx.xxx.xxx'
    MCAST_PORT = 18000
    host = '192.168.255.2'
    sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM, socket.IPPROTO_UDP)
    sock.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
    sock.bind((MCAST_GRP, MCAST_PORT))
    sock.setsockopt(socket.SOL_IP, socket.IP_ADD_MEMBERSHIP,
                         socket.inet_aton(MCAST_GRP) + socket.inet_aton(host))
    
    while True:
        print sock.recv(1024)

```

Here is the config:


```
    tunnel    Link encap:UNSPEC  HWaddr xx-xx-xx-xx-xx-xx-xx-xx-00-00-00-00-00-00-00-00
              inet addr:192.168.255.2  P-t-P:192.168.255.2  Mask:255.255.255.252
              inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Link
              UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1476  Metric:1
              RX packets:53 errors:0 dropped:0 overruns:0 frame:0
              TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0
              RX bytes:6872 (6.8 KB)  TX bytes:17522 (17.5 KB)



```

---

