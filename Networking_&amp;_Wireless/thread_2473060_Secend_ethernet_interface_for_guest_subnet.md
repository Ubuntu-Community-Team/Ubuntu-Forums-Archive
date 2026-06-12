---
title: "Secend ethernet interface for guest subnet"
date: 2022-03-22
forum: Networking &amp; Wireless
---

### Post by peterstoss on 2022-03-22
Hey,
my configuration
192.168.0.x enp2s0f2 (192.168.0.1) is primary subnet - router is 192.168.0.1
192.168.2.x enx00e04c025f69 (192.168.15.1) should be guest network -> all traffic has to be forwared to 192.168.0.1, access to 192.168.0.x must be denied.

Two questions:
1) I have an USB eth-Adapter for the guest network. IP should be 192.168.15.1 - but netplan doesn't set the ip. This is my yaml (netplan apply done; no error).
I always have to set the ip by myself with: ifconfig enx00e04c025f69 192.168.15.1
Whats wrong?
Here is my yaml:

root@guest4cam:/home/henning# cat /etc/netplan/00-installer-config.yaml
# This is the network config written by 'subiquity'
network:
  version: 2
  ethernets:
    enp2s0f2:
      addresses: [192.168.2.60/24]
      gateway4: 192.168.2.100
      nameservers:
        addresses: [192.168.2.100,1.1.1.1]
        search: []
    enx00e04c025f69:
      addresses: [192.168.15.1/24]


ifconfig:

enp2s0f2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.60  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::82ee:73ff:febd:c840  prefixlen 64  scopeid 0x20<link>
        ether 80:ee:73:bd:c8:40  txqueuelen 1000  (Ethernet)
        RX packets 701  bytes 65360 (65.3 KB)
        RX errors 0  dropped 281  overruns 0  frame 0
        TX packets 273  bytes 38750 (38.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enx00e04c025f69: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:e0:4c:02:5f:69  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 92  bytes 7036 (7.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 92  bytes 7036 (7.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

2) I already installed iptables. Can you help me to setup the rules for the guest-subnet? net.ipv4.ip_forward=1 in sysctl.conf is already set.

Thanks!
Peter

---

### Post by Andrew_Welham on 2022-03-31
did you get anywhere with this issue ?

Also did you do a  
netplan generate -debug  

 first ?

---

