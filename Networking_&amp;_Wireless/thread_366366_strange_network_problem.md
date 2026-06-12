---
title: "strange network problem"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by byronical on 2007-02-20
Last week my network connection just stopped working on one particular network. I´ve verified that I´m still able to connect to another network (using DHCP).

I´ve tried both DHCP and STATIC IP addresses on the network that I can´t connect to as well as the same IP configuration from another M$ W2000 laptop that can connect.

I´m also unable to ping my gateway - the w2000 is able to ping the gateway.

Below is information about my network configuration and HW configuration

```
byronical:[net] ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:3F:CF:60:40  
          inet addr:10.200.6.154  Bcast:10.200.6.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fecf:6040/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2 txqueuelen:1000 
          RX bytes:79116185 (75.4 MiB)  TX bytes:602604 (588.4 KiB)
          Interrupt:225 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:967114 (944.4 KiB)  TX bytes:967114 (944.4 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I can ping others Node on my sub network and my local loopback IP Address but cannot ping my gateway

```

byronical:[net] ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.089 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.069 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.057 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.053 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3007ms
rtt min/avg/max/mdev = 0.053/0.067/0.089/0.014 ms
byronical:[net] ping -c 4 10.200.6.155
PING 10.200.6.155 (10.200.6.155) 56(84) bytes of data.
64 bytes from 10.200.6.155: icmp_seq=1 ttl=128 time=8.03 ms
64 bytes from 10.200.6.155: icmp_seq=2 ttl=128 time=0.174 ms
64 bytes from 10.200.6.155: icmp_seq=3 ttl=128 time=0.180 ms
64 bytes from 10.200.6.155: icmp_seq=4 ttl=128 time=0.198 ms

--- 10.200.6.155 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3008ms
rtt min/avg/max/mdev = 0.174/2.145/8.031/3.398 ms
byronical:[net] 

byronical:[net] ping -c 4 10.200.6.1
PING 10.200.6.1 (10.200.6.1) 56(84) bytes of data.

--- 10.200.6.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3001ms

```

HW Information

```
byronical:[net] sudo mii-tool -v eth0tool eth0
SIOCGMIIPHY on 'eth0tool' failed: No such device
eth0: 100 Mbit, full duplex, link ok
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   100 Mbit, full duplex
  basic status: link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
byronical:[net] sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes

byronical:[net] sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:cf:60:40
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=off broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=10.200.6.154 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:3000-30ff iomemory:e0200800-e02008ff irq:225

```


and my routing information

```


byronical:[net] route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.200.6.0      *               255.255.255.0   U     0      0        0 eth0
default         10.200.6.1      0.0.0.0         UG    0      0        0 eth0

byronical:[net] ip neigh
10.200.6.1 dev eth0 INCOMPLETE


```

Could IP Tables be causing packets to be dropped??

```


byronical:[net] sudo iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.9.198.11         anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.9.198.11         anywhere            
ACCEPT     tcp  --  192.9.198.13         anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.9.198.13         anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             10.200.6.255        
DROP       all  --  224.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.0/8         
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  10.200.6.154         192.9.198.11        tcp dpt:domain 
ACCEPT     udp  --  10.200.6.154         192.9.198.11        udp dpt:domain 
ACCEPT     tcp  --  10.200.6.154         192.9.198.13        tcp dpt:domain 
ACCEPT     udp  --  10.200.6.154         192.9.198.13        udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  224.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.0/8         
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:x11 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:x11 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:fsp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere

```

I´ve been hitting my head against a brick wall for a couple of days now and am starting to become very frustrated since I´d rather be working with Linux than using a spare W2000 node.

Does anyone have any ideas what could be causing this problem?

Thanks
Byron

---

### Post by Yfrwlf on 2007-02-20
Reinstall?  J/k ;)  Since I'm pretty noobish I'd recommend using Firestarter to configure your iptables.  Using Firestarter you could "turn off" the firewall so that you can make sure it's not causing a problem, though anything that runs into the firewall should appear in the event section of Firestarter so you will know it stopped something.

I'd disable the firewall and then turn on DHCP and you can do a ```
/etc/init.d/network restart
```and see if that fixes it?

These are just random ideas cause I'm noobish keep in mind. ^^  Also posting the contents of /etc/network/interfaces might be of some use to someone in helping you perhaps.

---

### Post by decrepit on 2007-02-21
I'm fairly inexperienced as well, but most of what you have looks fine to me. except the last bit.
Mine's working fine and I get this.

mike@ubu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        *               255.255.255.0   U     0      0        0 eth0
default         10.1.1.1        0.0.0.0         UG    0      0        0 eth0
mike@ubu:~$ ip neigh
10.1.1.1 dev eth0 lladdr 00:13:a3:6e:6e:ec STALE
mike@ubu:~$ 

If you can figure out what lladdr is that might help, I don't think it's the MAC address of the NIC.
May be you have a problem with the NIC, can you swap the connections around to eliminate that possibility?

---

### Post by byronical on 2007-02-21
Hi

I know it seems crazy but when I connected today to the network that I was having problems with, it just worked and now I'm back in business..... not sure what was the problem was since I hadn't changed any configuration from yesterday.

I 'm now able to ping my reach my gateway so I wonder what was preventing me in the first place??

```

byronical:[~] ip neigh
10.200.6.1 dev eth0 lladdr 00:00:0c:07:ac:01 REACHABLE
byronical:[~] 

```

The mystery continues but at least I'm up and working again.

I'd previously verified that my Ubuntu box was able to connect to another network (using DCHP) without problems so maybe it was the clients network causing the problem but then Windows nodes didn't have any problems connecting to that particular network that I was having problems with. (any ideas?)

I'm still anxious that this problem might reoccur but I'll see how things go.

Thanks
Byron

---

### Post by dmizer on 2007-02-21
you are/were suffering from dns problems.  you can try two things.

1) blacklist ipv6 by adding:
blacklist ipv6
to the end of /etc/modprobe.d/blacklist

as well as by following the rest of the directions in this thread: [http://www.ubuntuforums.org/showthread.php?t=282034](http://www.ubuntuforums.org/showthread.php?t=282034)

this should prevent you from experiencing the problem again unless your actual dns servers go down.

---

