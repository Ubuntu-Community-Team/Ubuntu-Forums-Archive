---
title: "Cannot connect to colocation's fiber network"
date: 2016-03-21
forum: Networking &amp; Wireless
---

### Post by evan.lyall on 2016-03-21
I moved my Ubuntu fileserver offsite to a colocation service and cannot connect to their fiber network. It recognizes the connection (via: cat /sys/class/net/p5p2/carrier), it seems to record packets being transferred (via: ifconfig p5p2), and the lights on the NIC seem to flash nominally, but it can't successfully ping the default gateway. Cumulatively, I've now spent WAY too many hour trying to debug it, and I'm in over my head.

OS: Ubuntu Server 14.04
NIC: [AOC-STGN-i2S]("http://www.amazon.com/gp/product/B005OK1GEK/")
Optical Transceiver: [Supermicro AOC-E10GSFPSR 10Gb Ethernet SFP plus]("http://www.amazon.com/Supermicro-AOC-E10GSFPSR-10Gb-Ethernet-Transceiver/dp/B008STP2TE/")

Network configuration provided by the colocation service:
IPv4: xxx.xxx.xxx.150
Subnet: xxx.xxx.xxx.128/25
Gateway: xxx.xxx.xxx.129
Subnet Mask: 255.255.255.128
Fully-Qualified Domain Name: aaa.bbb.ccc.com
DNS Nameserver1: X
DNS Nameserver2: Y
DNS Nameserver3: Z

```
$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:354419 (354.4 KB)  TX bytes:354419 (354.4 KB)


p5p2      Link encap:Ethernet  HWaddr 00:25:90:c0:bf:f3  
          inet addr:xxx.xxx.xxx.150  Bcast:xxx.xxx.xxx.255  Mask:255.255.255.128
          inet6 addr: xxxx::xxx:xxxx:xxxx:bff3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1134798 (1.1 MB)  TX bytes:73221 (73.2 KB)
``` 
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         xxx.xxx.xxx.129 0.0.0.0         UG    0      0        0 p5p2
xxx.xxx.xxx.128 0.0.0.0         255.255.255.128 U     0      0        0 p5p2
``` 
```
$ iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
```
$ hostname
aaa
```
```
$ ping xxx.xxx.xxx.129
PING xxx.xxx.xxx.129 (xxx.xxx.xxx.129) 56(84) bytes of data.
From xxx.xxx.xxx.150 icmp_seq=1 Destination Host Unreachable
From xxx.xxx.xxx.150 icmp_seq=2 Destination Host Unreachable
From xxx.xxx.xxx.150 icmp_seq=3 Destination Host Unreachable
^C
--- xxx.xxx.xxx.129 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4024ms
pipe 3
``` 
```
$ arp -an
? (xxx.xxx.xxx.129) at <incomplete> on p5p2
``` 
```
$ sudo nmap localhost
Starting Nmap 6.40 ( http://nmap.org ) at 2016-03-21 11:51 PDT
mass_dns: warning: Unable to determine any DNS servers. Reverse DNS is disabled. Try using --system-dns or specify valid servers with --dns-servers
Nmap scan report for aaa.bbb.ccc.com (xxx.xxx.xxx.150)
Host is up (0.000035s latency).
Not shown: 997 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
```

If I try to 'nmap' the gateway, it says the gateway is down. However I can set up a temporary internet connection where I route my laptop's wifi to 'em2' on the motherboard. Then ping works fine, and 'nmap' returns:
```
nmap xxx.xxx.xxx.129

Starting Nmap 6.40 ( http://nmap.org ) at 2016-03-22 11:52 PDT
Nmap scan report for xxx.yyy.ccc.com (xxx.xxx.xxx.129)
Host is up (0.0034s latency).
Not shown: 998 filtered ports
PORT   STATE  SERVICE
21/tcp open   ftp
80/tcp closed http


Nmap done: 1 IP address (1 host up) scanned in 5.77 seconds
```


What am I doing wrong with the fiber network configuration? The colocation service says the fiber cable is fine, and that the switch is forwarding packets correctly.

---

### Post by evan.lyall on 2016-03-22
Adding interface configuration information:

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto p5p2
iface p5p2 inet static
    address xxx.xxx.xxx.150
    gateway xxx.xxx.xxx.129
    netmask 255.255.255.128
    network xxx.xxx.xxx.128/25
    broadcast xxx.xxx.xxx.255
    dns-domain ccc.com
    dns-search ccc.com bbb.ccc.com
    dns-nameservers X Y Z
```

```
$ cat /etc/hosts
127.0.0.1   localhost
127.0.1.1   localhost
xxx.xxx.xxx.150 aaa.bbb.ccc.com aaa
```

---

