---
title: "No Internet on machine sharing Internet"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by fortenbt on 2007-08-27
About a week ago, I followed [_**this**_]("http://ubuntuforums.org/showthread.php?t=91370") guide to sharing my internet connection using ubuntu.

The sharing works; my laptop gets internet from my router that routes internet forwarded from my ubuntu machine.  However, sometimes (and it seems pretty random) internet does not work on the ubuntu machine.

It is directly connected to a cable modem, gets an ip address, and i can ping the gateway ip.

My iptables -L output is the following when Internet does not work.
```
Chain INPUT (policy DROP)

target     prot opt source               destination         

ACCEPT     0    --  anywhere             anywhere            

LOG        0    --  127.0.0.0/8          anywhere            LOG level warning 

DROP       0    --  127.0.0.0/8          anywhere            

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  192.168.0.0/24       anywhere            

ACCEPT    !tcp  --  anywhere             224.0.0.0/4         

LOG        0    --  192.168.0.0/24       anywhere            LOG level warning 

DROP       0    --  192.168.0.0/24       anywhere            

LOG        0    --  192.168.0.0/24       anywhere            LOG level warning 

DROP       0    --  192.168.0.0/24       anywhere            

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  anywhere             192.168.1.101       

ACCEPT     0    --  anywhere             192.168.1.255       

ACCEPT     0    --  anywhere             64.93.153.123       

ACCEPT     0    --  anywhere             64.93.155.255       

DROP       0    --  anywhere             224.0.0.1           

LOG        0    --  anywhere             anywhere            LOG level warning 

DROP       0    --  anywhere             anywhere            



Chain FORWARD (policy DROP)

target     prot opt source               destination         

ACCEPT     0    --  192.168.0.0/24       anywhere            

ACCEPT     0    --  192.168.0.0/24       anywhere            

ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 

LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 

DROP       0    --  anywhere             192.168.0.0/24      

LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 

DROP       0    --  anywhere             192.168.0.0/24      

DROP       0    --  anywhere             224.0.0.1           

LOG        0    --  anywhere             anywhere            LOG level warning 

DROP       0    --  anywhere             anywhere            



Chain OUTPUT (policy DROP)

target     prot opt source               destination         

ACCEPT     0    --  anywhere             anywhere            

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  anywhere             192.168.0.0/24      

ACCEPT    !tcp  --  anywhere             224.0.0.0/4         

LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 

DROP       0    --  anywhere             192.168.0.0/24      

LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 

DROP       0    --  anywhere             192.168.0.0/24      

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  192.168.1.101        anywhere            

ACCEPT     0    --  192.168.1.255        anywhere            

ACCEPT     0    --  64.93.153.123        anywhere            

ACCEPT     0    --  64.93.155.255        anywhere            

DROP       0    --  anywhere             224.0.0.1           

LOG        0    --  anywhere             anywhere            LOG level warning 

DROP       0    --  anywhere             anywhere 
```

When Internet does work, my iptables -L looks like this:
```
Chain INPUT (policy DROP)

target     prot opt source               destination         

ACCEPT     0    --  anywhere             anywhere            

LOG        0    --  127.0.0.0/8          anywhere            LOG level warning 

DROP       0    --  127.0.0.0/8          anywhere            

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  192.168.0.0/24       anywhere            

ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 

LOG        0    --  192.168.0.0/24       anywhere            LOG level warning 

DROP       0    --  192.168.0.0/24       anywhere            

LOG        0    --  192.168.0.0/24       anywhere            LOG level warning 

DROP       0    --  192.168.0.0/24       anywhere            

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  anywhere             192.168.1.101       

ACCEPT     0    --  anywhere             192.168.1.255       

ACCEPT     0    --  anywhere             64.93.153.123       

ACCEPT     0    --  anywhere             64.93.155.255       

DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET 

LOG        0    --  anywhere             anywhere            LOG level warning 

DROP       0    --  anywhere             anywhere            



Chain FORWARD (policy DROP)

target     prot opt source               destination         

ACCEPT     0    --  192.168.0.0/24       anywhere            

ACCEPT     0    --  192.168.0.0/24       anywhere            

ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 

LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 

DROP       0    --  anywhere             192.168.0.0/24      

LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 

DROP       0    --  anywhere             192.168.0.0/24      

DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET 

LOG        0    --  anywhere             anywhere            LOG level warning 

DROP       0    --  anywhere             anywhere            



Chain OUTPUT (policy DROP)

target     prot opt source               destination         

ACCEPT     0    --  anywhere             anywhere            

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  anywhere             192.168.0.0/24      

ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 

LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 

DROP       0    --  anywhere             192.168.0.0/24      

LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 

DROP       0    --  anywhere             192.168.0.0/24      

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  anywhere             255.255.255.255     

ACCEPT     0    --  192.168.1.101        anywhere            

ACCEPT     0    --  192.168.1.255        anywhere            

ACCEPT     0    --  64.93.153.123        anywhere            

ACCEPT     0    --  64.93.155.255        anywhere            

DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET 

LOG        0    --  anywhere             anywhere            LOG level warning 

DROP       0    --  anywhere             anywhere
```

My ifconfig -a is:
```
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:EB:1E:6C  

          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0

          inet6 addr: fe80::20f:eaff:feeb:1e6c/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:2622 errors:0 dropped:0 overruns:0 frame:0

          TX packets:3120 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:419796 (409.9 KiB)  TX bytes:2974179 (2.8 MiB)

          Interrupt:16 Base address:0x6000 



eth1      Link encap:Ethernet  HWaddr 00:A0:C9:E0:15:00  

          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::2a0:c9ff:fee0:1500/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:49439 errors:0 dropped:0 overruns:0 frame:0

          TX packets:55234 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:3563521 (3.3 MiB)  TX bytes:3595138 (3.4 MiB)



eth2      Link encap:Ethernet  HWaddr 00:0F:EA:EA:4E:DE  

          inet addr:64.93.153.123  Bcast:64.93.155.255  Mask:255.255.252.0

          inet6 addr: fe80::20f:eaff:feea:4ede/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:34789 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2823 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:9263893 (8.8 MiB)  TX bytes:448850 (438.3 KiB)

          Interrupt:19 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
```

My ethtool eth2 (the nic that is directly connected to the internet) is:
```
Settings for eth2:

        Supported ports: [ TP ]

        Supported link modes:   10baseT/Half 10baseT/Full 

                                100baseT/Half 100baseT/Full 

                                1000baseT/Half 1000baseT/Full 

        Supports auto-negotiation: Yes

        Advertised link modes:  10baseT/Half 10baseT/Full 

                                100baseT/Half 100baseT/Full 

                                1000baseT/Half 1000baseT/Full 

        Advertised auto-negotiation: Yes

        Speed: 100Mb/s

        Duplex: Full

        Port: Twisted Pair

        PHYAD: 0

        Transceiver: internal

        Auto-negotiation: on

        Supports Wake-on: g

        Wake-on: d

        Current message level: 0x00000037 (55)

        Link detected: yes
```

If there is any other information I could provide, please let me know.

---

### Post by emil.s on 2007-08-27
Hi!

Sometimes the "default gateway" has disappeared for me...

Check your default-GW with "route". You should get something like:
default         10.0.0.1        0.0.0.0         UG    0      0        0 eth0

Check it next time your connection get lost. And if the default line has disappeared, add a new default GW with:
```
sudo route add default gw 0.0.0.0
```
and replace 0.0.0.0 with your gateway IP. ;)

---

