---
title: "2 NIC 1 routing problem"
date: 2017-03-10
forum: Networking &amp; Wireless
---

### Post by primskovich on 2017-03-10
Hello,

I have a weird problem and I don't know where else to go, hope this place is ok and somebody can shed some light on what's going on.

I have several linux servers that act as proxy server for me. There is only SSH Daemon running and I do "ssh -D" or with putty and dynamic port forwarding.

Easy peasy, works as intended.


The thing is, in addition to eth0/enp0s3 which is on wired network and behind a router, I also have 4g USB modem. I establish 4G connection and now my server has access to internet on two network interfaces. The reason for this is, 4G has dynamic IP, which I need and incoming connections blocked, so I need to use a second NIC. So my point is to SSH into the server on NIC1 and go out on NIC2 and have external IP of a 4G connection. this works on 3 out of 5 boxes and all are on the same location. my other two, i tried on two different locations and i can't get them to work.

I set up routing table to something like this:

```

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.8.1     0.0.0.0         UG    0      0        0 enx0c5b8f279a64
192.168.1.0     *               255.255.255.0   U     0      0        0 enp0s3
192.168.8.0     *               255.255.255.0   U     0      0        0 enx0c5b8f279a64

```


```

$ ifconfig 
enp0s3    Link encap:Ethernet  HWaddr 08:00:27:dc:c9:bb  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fedc:c9bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1600719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1463227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:334581703 (334.5 MB)  TX bytes:1129958980 (1.1 GB)

enx0c5b8f279a64 Link encap:Ethernet  HWaddr 0c:5b:8f:27:9a:64  
          inet addr:192.168.8.100  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::e5b:8fff:fe27:9a64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:818375 errors:633001 dropped:0 overruns:0 frame:630834
          TX packets:886224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:544583863 (544.5 MB)  TX bytes:152213461 (152.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:216843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:21351570 (21.3 MB)  TX bytes:21351570 (21.3 MB)

```


This is working example.

The thing is, I have several of these boxes. And it works on some and not the others. These are the only things I do, install usb_modeswitch so I can use 4G modem, set up a connection and set up routing. The first two things work, the last one doesn't and I can't figure out why. There is nothing else I did on my working boxes and I don't know what else could be messing with this configuration.


things i checked:
- kernel packet forwarding ( /proc/sys/net/ipv4/ip_forward - disabled on working box, so doesn't affect non working box )
- iproute2 policy based routing ( disabled on working box, didn't mess with on non working box)
- iptables disabled on both
- these two boxes are on different location, maybe the problem is in router or ISP ?
- I did a tcpdump and i noticed on working box, packets from outside have a fqdn "ddwrt" which is my router - like it's supposed to be with NAT? and on non working box, the "name of the packet" is fqdn from where i am connecting, so not my rotuers name but my source fqdn. this is the only reason i see, my config could be dropping packets


because how i noticed it doesn't work?
on non working box ... when i enable 4g NIC and connect it online, it works, and it sets up a default route and then you have two default routes. at this point, you can SSH into the server from outside, the router correctly forwards the incoming packet to the SSH daemon on the local box. then I delete default route from NIC1 and set up a new default route to NIC2 like in CODE 1 above and it stops working. by "stops working" i mean, i can no longer connect to the box from the outside. it's like the router cannot reach local address anymore and the packets are being dropped. the server is unavailable to the outside world. but then i use a 2nd machine on the LAN and i ping the server's local address and IT WORKS. I can SSH into the box from LAN but not from the outside ... how, why? so apparently the SSH server is still listening on local address and i can connect to it from my LAN just fine, just not from outside ..... why not? what else could be the problem? and why does it work on one box and not the other (behind different router) - what could router have with all these?


i complicated this too much, i hope you guys know what i mean.

thanks for any ideas

example of tcpdump on working box
```

08:08:06.764612 IP DD-WRT.40722 > george.ssh: Flags [.], ack 31580, win 1444, options [nop,nop,TS val 60094317 ecr 106186878], length 0
08:08:06.764678 IP george.ssh > DD-WRT.40722: Flags [P.], seq 41324:41512, ack 1, win 315, options [nop,nop,TS val 106186958 ecr 60094316], length 188
08:08:06.764894 IP george.ssh > DD-WRT.40722: Flags [P.], seq 41512:41836, ack 1, win 315, options [nop,nop,TS val 106186959 ecr 60094317], length 324
08:08:06.765072 IP george.ssh > DD-WRT.40722: Flags [P.], seq 41836:42024, ack 1, win 315, options [nop,nop,TS val 106186959 ecr 60094317], length 188
08:08:06.765244 IP george.ssh > DD-WRT.40722: Flags [P.], seq 42024:42212, ack 1, win 315, options [nop,nop,TS val 106186959 ecr 60094317], length 188
08:08:06.765333 IP DD-WRT.40722 > george.ssh: Flags [.], ack 31768, win 1444, options [nop,nop,TS val 60094317 ecr 106186878], length 0

```

example of tcpdump on non working box
```

08:08:50.170258 IP 192.168.2.6.ssh > mx-ll-45.5.34-112.dynamic.verizon.com.46850: Flags [.], ack 1378, win 248, options [nop,nop,TS val 379557 ecr 60107411], length 0 
08:08:50.580217 IP mx-ll-45.5.34-112.dynamic.verizon.com.46850 > 192.168.2.6.ssh: Flags [.], ack 1018, win 244, options [nop,nop,TS val 60107524 ecr 379546], length 0 
08:08:50.581162 IP mx-ll-45.5.34-112.dynamic.verizon.com.46850 > 192.168.2.6.ssh: Flags [P.], seq 1378:1426, ack 1018, win 244, options [nop,nop,TS val 60107524 ecr 379557], length 48 

```

this is the only thing i see different and i don't know what else to check, thanks again.
i think it might be a router problem, and i would buy a new router, if i knew which feature it needs for this. or maybe ISP problem and i would call them if I knew what to ask ... - i think it might be router problem after all ... it looks like my DDWRT makes a bridged network whereas my second router only does NAT  ... i think, i don't know? so i need a bridge capable router on 2nd location and it will work?


edit; this thread is not public is it?

---

