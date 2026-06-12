---
title: "Bittorrent port forwarding with iptables"
date: 2019-06-11
forum: Networking &amp; Wireless
---

### Post by stavros082 on 2019-06-11
I have a qBittorrent client on a device that is connected to another(which has a public ip) using OpenVPN, and I am trying to forward port 6881. The port is open(nmap shows it as open) but there is no traffic, and the client reports 0 DHT nodes. This is the map with the network interfaces.

Internet <- (venet0) host (tun0) <- (tun0) client

host venet0 ip: 193.148.69.152
host tun0 ip: 10.9.8.1
client run0 ip: 10.9.8.3

host iptables:
```
# iptables -nvL
Chain INPUT (policy ACCEPT 56 packets, 2938 bytes)
 pkts bytes target     prot opt in     out     source               destination         
21926 7250K ACCEPT     all  --  venet0 *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED

Chain FORWARD (policy ACCEPT 3 packets, 156 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    8   384 ACCEPT     tcp  --  venet0 tun0    0.0.0.0/0            10.9.8.3             tcp dpt:6881
    2    56 ACCEPT     udp  --  venet0 tun0    0.0.0.0/0            10.9.8.3             udp dpt:6881

Chain OUTPUT (policy ACCEPT 2281 packets, 188K bytes)
 pkts bytes target     prot opt in     out     source               destination

# iptables -nvL -t nat
Chain PREROUTING (policy ACCEPT 136 packets, 8452 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    8   368 DNAT       tcp  --  venet0 *       0.0.0.0/0            0.0.0.0/0            tcp dpt:6881 to:10.9.8.3
   13   364 DNAT       udp  --  venet0 *       0.0.0.0/0            0.0.0.0/0            udp dpt:6881 to:10.9.8.3

Chain POSTROUTING (policy ACCEPT 31 packets, 1999 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    6   280 SNAT       tcp  --  *      tun0    0.0.0.0/0            10.9.8.3             tcp dpt:6881 to:10.9.8.1
   15   420 SNAT       udp  --  *      tun0    0.0.0.0/0            10.9.8.3             udp dpt:6881 to:10.9.8.1

Chain OUTPUT (policy ACCEPT 31 packets, 1999 bytes)
 pkts bytes target     prot opt in     out     source               destination  
```

client iptables:
```
# iptables -nvL
Chain INPUT (policy ACCEPT 1269K packets, 1117M bytes)
 pkts bytes target     prot opt in     out     source               destination         
   58  2696 ACCEPT     tcp  --  tun0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:6881
   19   532 ACCEPT     udp  --  tun0   *       0.0.0.0/0            0.0.0.0/0            udp dpt:6881

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  26M   24G ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
83832 7218K ACCEPT     all  --  br0    *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 854K packets, 161M bytes)
 pkts bytes target     prot opt in     out     source               destination 

```

I can't figure out what's missing, since NAT is set up and the port is open.

---

### Post by stavros082 on 2019-07-01
Bump

---

### Post by SeijiSensei on 2019-07-01
Did you enable packet forwarding in /etc/sysctl.conf?  Ubuntu, like most modern distros, will not forward packets across interfaces as a security measure.  You need to uncomment the "net.ipv4.ip_forward=1" line in sysctl.conf.  Make the change, then reboot.

---

