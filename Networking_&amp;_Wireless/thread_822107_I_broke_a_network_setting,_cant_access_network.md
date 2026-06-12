---
title: "I broke a network setting, cant access network"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by bzz_ on 2008-06-07
Ok, today I **finally** got around to correcting my network configuration.. which I shall try and outline to the best of my ASCII abilities.

```

                 ,
                / \  Internet
              <``X``>
               /_!_\
                 |
                 |   _______
                 |__|       | - 192.168.100.100
                    | Modem |
                    |_______|
                        |
                        |
                        |
   x2 PC & x1 XBox |||||||||||||||| - 192.168.0.1
   ----------------|              | - DHCP On
                   | Wired Router |   Range:
                   |              |   192.168.0.101 -
                   ||||||||||||||||   192.168.0.150
                              |
                              |
                              |
                         ,_,_,|,_,_,
                        (           ) - 192.168.0.254
             x2 Laptops  )  Wifi   (  - DHCP Off
             -----------(   Router  )
                         )         (
                        (,_,_,_,_,_,)

```

So here's the problem:

Basically, the networking works perfectly; if a laptop is connected to wifi, it gets an IP from the wired router, and the default gateway is acquired properly (192.168.0.1).. same for wired connections.

My laptop is unable to connect to the network while connected through the wifi router when booted into Ubuntu. If I put in my HDD with Windows XP on it, it works fine. Other Linux laptops work fine (Red Hat and Ubuntu). So obviously I must of changed or disabled something on my laptop that is preventing it from working properly. Any ideas?

*** avahi is disabled (multiple ways) could this be a problem? I started the Multicast DNS service discovery (avahi-daemon) and it didn't change anything after restarting networking, etc. ***

This may be useful.. not sure: also, other PCs can't ping my wifi router, not sure why, I think I broke the config on that (I'm on a roll!) but it does work....
> 
# ifconfig eth1

eth1      Link encap:Ethernet  HWaddr 00:04:23:92:5c:fe  
          inet addr:192.168.0.150  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe92:5cfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2024 errors:468 dropped:468 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:633628 (618.7 KB)  TX bytes:3712 (3.6 KB)
          Interrupt:11 Memory:c0210000-c0210fff 

# iptables -L INPUT

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning 
DROP       all  --  127.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.1           
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

# iptables -L OUTPUT

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  anywhere             224.0.0.1           
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

# ping 192.168.0.150
PING 192.168.0.150 (192.168.0.150) 56(84) bytes of data.
64 bytes from 192.168.0.150: icmp_seq=1 ttl=64 time=0.092 ms

# ping 192.168.0.254
PING 192.168.0.254 (192.168.0.254) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

#ping google.com
ping: unknown host google.com

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1


---

