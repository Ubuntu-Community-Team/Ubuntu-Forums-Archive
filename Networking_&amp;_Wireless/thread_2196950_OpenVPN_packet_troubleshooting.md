---
title: "OpenVPN packet troubleshooting"
date: 2014-01-01
forum: Networking &amp; Wireless
---

### Post by brandon-bilbo on 2014-01-01
I have Ubuntu Server 12.04 with 2 nics as a gateway/firewall for my lan and now also running openvpn server. There are several windows PCs on the LAN. The vpn client can connect and interact with the server just fine. What is weird to me is that it also can ping just ONE windows PC on the LAN, browse its network shares, do traceroute, ping etc everything works fine with just this one PC and the server.... but not with the other PCs. There isnt anything different on the windows PCs they are all fresh windows 8 installs and connected to the same switch.

Using tcpdump and wireshark when I ping either direction they are getting the requests just not responding to them. This goes for all other types of traffic too, it seems as if the packets are making it to the destination...

openvpn server config:
```

port 1194
proto udp
dev tun
ca ca.crt
cert provizon.org.crt
key provizon.org.key  # This file should be kept secret
dh dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.0.0 255.255.255.0"
keepalive 10 120
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3

```

routes:
```


Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         98.196.114.1    0.0.0.0         UG        0 0          0 WAN
10.8.0.0        10.8.0.2        255.255.255.0   UG        0 0          0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
98.196.114.0    0.0.0.0         255.255.254.0   U         0 0          0 WAN
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 LAN

```

---

### Post by SeijiSensei on 2014-01-01
May we see the results of 

```

sudo iptables -L -nv
sudo iptables -t nat -L -nv

```

I suspect that some traffic is being blocked.  In particular, do you have a pair of forwarding rules like

```

iptables -A FORWARD -s 10.8.0.0/24 -d 192.168.0.0/24 -j ACCEPT
iptables -A FORWARD -d 10.8.0.0/24 -s 192.168.0.0/24 -j ACCEPT

```

That should prevent the traffic between the LAN and the OpenVPN clients from being masqueraded which can often muck routing up.

---

### Post by brandon-bilbo on 2014-01-01
would doubt that its my firewall since I can "see" the packets at the destination... but here goes 

sudo iptables -L -nv
```

Chain INPUT (policy DROP 30348 packets, 2377K bytes)
 pkts bytes target     prot opt in     out     source               destination
 9912 1357K ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0
53441   14M ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
2272K  128M ACCEPT     all  --  LAN    *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  tun0   *       0.0.0.0/0            0.0.0.0/0
16976 2738K ACCEPT     all  --  WAN    *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
  116  6844 ACCEPT     tcp  --  WAN    *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
   40  2260 ACCEPT     tcp  --  WAN    *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
   10   766 ACCEPT     udp  --  WAN    *       0.0.0.0/0            0.0.0.0/0            udp dpt:1194
 3616 1329K ACCEPT     udp  --  WAN    *       73.0.0.0/8           0.0.0.0/0            udp spts:67:68 dpts:67:68
 2920  207K LOG        tcp  --  WAN    *       0.0.0.0/0            0.0.0.0/0            tcp limit: avg 30/sec burst 5 LOG flags 0 level 7 prefix "DROPPED_IN:"


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
8867K   11G ACCEPT     all  --  LAN    WAN     0.0.0.0/0            0.0.0.0/0
6122K  927M ACCEPT     all  --  WAN    LAN     0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000
 6297  331K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:56666
49087 6542K ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:56666
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpts:8001:8003
    0     0 ACCEPT     all  --  tun0   *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  *      tun0    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 7 prefix "DROPPED_FORWARD:"


Chain OUTPUT (policy ACCEPT 1196K packets, 19G bytes)
 pkts bytes target     prot opt in     out     source               destination

```

sudo iptables -t nat -L -nv
```

Chain PREROUTING (policy ACCEPT 281K packets, 23M bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DNAT       tcp  --  WAN    *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000 to:192.168.0.30:8000
 6624  348K DNAT       tcp  --  WAN    *       0.0.0.0/0            0.0.0.0/0            tcp dpt:56666 to:192.168.0.30:56666
51573 6958K DNAT       udp  --  WAN    *       0.0.0.0/0            0.0.0.0/0            udp dpt:56666 to:192.168.0.30:56666
    0     0 DNAT       udp  --  WAN    *       0.0.0.0/0            0.0.0.0/0            udp dpt:8001 to:192.168.0.40:8001


Chain INPUT (policy ACCEPT 4185 packets, 817K bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 16568 packets, 1269K bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 63607 packets, 7738K bytes)
 pkts bytes target     prot opt in     out     source               destination
 269K   21M MASQUERADE  all  --  *      WAN     0.0.0.0/0            0.0.0.0/0

```

---

### Post by brandon-bilbo on 2014-01-01
I believe these 2 lines do what you're referring too
    0     0 ACCEPT     all  --  tun0   *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  -  *      tun0    0.0.0.0/0            0.0.0.0/0

---

### Post by brandon-bilbo on 2014-01-01
My openvpn logs are full of this.. FULL

RWed Jan  1 16:32:24 2014 us=437286 client1/166.147.67.222:55548 MULTI: bad source address from client [fe80::11fc:a45b:4878:297a], packet dropped
RWed Jan  1 16:32:24 2014 us=786114 client1/166.147.67.222:55548 MULTI: bad source address from client [fe80::11fc:a45b:4878:297a], packet dropped

---

### Post by brandon-bilbo on 2014-01-02
turns out it was windows firewall ****ing everything up. Although I was disappointed by the lack of responses/suggestions received here, I am glad it's working now. thanks!

---

