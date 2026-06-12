---
title: "Unstable two ISP traffic redirection"
date: 2015-07-03
forum: Networking &amp; Wireless
---

### Post by morfi2 on 2015-07-03
I have a gateway with two ISP connected to eth0 and eth2. There is also a eth1 with local network. I'm trying to group some services in one interface and some in the second:


```
incoming traffic
1    eth0: 22 sshd, 80 http, 8080 http
2    eth2: 22 sshd


outgoing traffic 
3    eth2: 22 ssh, 25 smtp, 80 http, 110 pop3, 443 https, 587 smtp
4    eth0: the rest of the ports

```I managed to reroute the traffic in points 1,3,4 using iptable, iproute2 with fwmark. Here is interface setup:


```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
        address aaa.aaa.aaa.90
        netmask 255.255.255.248
        gateway aaa.aaa.aaa.89


auto eth2
iface eth2 inet static
        address bbb.bbb.bbb.137
        netmask 255.255.255.192
        pre-up /usr/local/bin/firewall.sh


auto br0
iface br0 inet static
        address 192.168.1.1
        netmask 255.255.0.0
        bridge-ports eth1
        post-up ifconfig eth1 0.0.0.0 promisc up

```Here is ip route and ip rules:


```
ip route show table main
aaa.aaa.aaa.88/29 dev eth0  proto kernel  scope link  src aaa.aaa.aaa.90
bbb.bbb.bbb.128/26 dev eth2  proto kernel  scope link  src bbb.bbb.bbb.137
192.168.0.0/16 dev br0  proto kernel  scope link  src 192.168.1.1
default via aaa.aaa.aaa.89 dev eth0


ip route show table 4
aaa.aaa.aaa.88/29 dev eth0  proto kernel  scope link  src aaa.aaa.aaa.90
bbb.bbb.bbb.128/26 dev eth2  proto kernel  scope link  src bbb.bbb.bbb.137
192.168.0.0/16 dev br0  proto kernel  scope link  src 192.168.1.1
default via bbb.bbb.bbb.129 dev eth2


0:      from all lookup 255
32765:  from all fwmark 0x4 lookup 4
32766:  from all lookup main
32767:  from all lookup default

```And iptables:
```


    iptables -F
    iptables -t nat -F
    iptables -t mangle -F
    iptables -P INPUT DROP




    iptables -A INPUT -i lo -j ACCEPT
    iptables -A INPUT -p udp --sport 68 --dport 67 -m physdev --physdev-in tap1 -j DROP
    iptables -A INPUT -i eth1 -j ACCEPT
    iptables -A INPUT -i eth2 -j ACCEPT
    iptables -A INPUT -i br0 -j ACCEPT
    iptables -A INPUT -p icmp -j ACCEPT
    iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
    iptables -A INPUT -p tcp --dport 22 -s 0/0 -j ACCEPT
    iptables -t mangle -A PREROUTING -p tcp --dport 22 -d bbb.bbb.bbb.137 -j MARK --set-mark 4
    iptables -t mangle -A PREROUTING -p tcp --dport 25 -s 192.168.0.0/16 -j MARK --set-mark 4
    iptables -t mangle -A PREROUTING -p tcp --dport 80 -s 192.168.0.0/16 -j MARK --set-mark 4
    iptables -t mangle -A PREROUTING -p tcp --dport 8080 -s 192.168.0.0/16 -j MARK --set-mark 4
    iptables -t mangle -A PREROUTING -p tcp --dport 110 -s 192.168.0.0/16 -j MARK --set-mark 4
    iptables -t mangle -A PREROUTING -p tcp --dport 443 -s 192.168.0.0/16 -j MARK --set-mark 4
    iptables -t mangle -A PREROUTING -p tcp --dport 587 -s 192.168.0.0/16 -j MARK --set-mark 4
    iptables -t nat -A PREROUTING -p tcp -d aaa.aaa.aaa.90 --dport 80 -j DNAT --to-destination 192.168.1.252:80


    iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source aaa.aaa.aaa.90
    iptables -t nat -A POSTROUTING -o eth2 -j SNAT --to-source bbb.bbb.bbb.137


    iptables -t nat -A POSTROUTING -s 192.168.1.0/16 -j MASQUERADE
```
I cannot access eth2 bbb.bbb.bbb.137:22 from outside even when I listen to all interfaces:


```
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     3111/sshd
```
Does anyone issued any instability in performance using fwmark iproute2? eth2 provider is much faster then eth0 but using eth2 I experienced some choking - like there were some ISP problems but there is no problem with internet service provider - checked with second router at the same time? Could some one please point me in right direction. 
THX

---

### Post by tgalati4 on 2015-07-03
Welcome to the forums.  Perhaps explain what you are trying to accomplish.  Perhaps a simple bonding between the two interfaces will give you a better load balance than trying to establish a hard policy for each interface, which can lead to strange network latent behavior.

---

### Post by morfi2 on 2015-07-04
Hi,
in the beginning I had only one ISP(1). All the outgoing traffic was provided by this ISP(1) and incoming services like ssh - 22, http -80, 8080.
Now I added a second ISP(2) and I'd like to use it for outgoing traffic especially smtp, pop3 and http(s). The incoming services would be intact and still provided by the first ISP(1).
My plan was to use ISP(1) as a default gateway, but in case of outgoing traffic I 'd use the ISP(2).
Regards

---

