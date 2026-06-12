---
title: "iptables and port forwarding issue"
date: 2015-10-01
forum: Networking &amp; Wireless
---

### Post by graeme3 on 2015-10-01
Hi, I'm hoping someone can help me on my port forwarding issue.

I have a dual homed Ubuntu 14.04 server machine on my work LAN (eth0), and a private LAN (eth1).  All I'm trying to do is simply port forward port 8000 to a Windows RDP port on 3389.

My work lan is 10.150.20.0/24 the Ubuntu server is 10.150.20.177, while the destination Windows machine is at 192.168.192.128.

```
root@ubu1404srv01:/usr/local/bin# **cat /proc/sys/net/ipv4/ip_forward**1
root@ubu1404srv01:/usr/local/bin# **uname -a**
Linux ubu1404srv01.sec.nwl 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
root@ubu1404srv01:/usr/local/bin#
root@ubu1404srv01:/usr/local/bin# **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:0c:29:2c:31:ef
          inet addr:10.150.20.177  Bcast:10.150.20.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe2c:31ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:258388 (258.3 KB)  TX bytes:260415 (260.4 KB)


eth1      Link encap:Ethernet  HWaddr 00:0c:29:2c:31:f9
          inet addr:192.168.192.142  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe2c:31f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11826 errors:0 dropped:4187 overruns:0 frame:0
          TX packets:321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4898150 (4.8 MB)  TX bytes:29615 (29.6 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:944 (944.0 B)  TX bytes:944 (944.0 B)



```

Routing table looks like this...

```
root@ubu1404srv01:/usr/local/bin# **netstat -nr**Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.150.20.1     0.0.0.0         UG        0 0          0 eth0
10.150.20.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.192.0   0.0.0.0         255.255.255.0   U         0 0          0 eth1



```


I have set the default filter policy to accept all traffic, but have set the PREROUTING policy to forward the port.

```
root@ubu1404srv01:/usr/local/bin# **iptables -L -v -n**Chain INPUT (policy ACCEPT 1092 packets, 89076 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain FORWARD (policy ACCEPT 2 packets, 88 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 828 packets, 92587 bytes)
 pkts bytes target     prot opt in     out     source               destination
root@ubu1404srv01:/usr/local/bin#
root@ubu1404srv01:/usr/local/bin#
root@ubu1404srv01:/usr/local/bin# iptables -L -vt nat
Chain PREROUTING (policy ACCEPT 197 packets, 17803 bytes)
 pkts bytes target     prot opt in     out     source               destination
**    2    88 DNAT       tcp  --  eth0   any     anywhere             anywhere             tcp dpt:8000 to:192.168.192.128:3189**


Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 2 packets, 88 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 4 packets, 176 bytes)
 pkts bytes target     prot opt in     out     source               destination



```


I can confirm from the ubuntu server that the windows port is open and listening...

```
root@ubu1404srv01:/usr/local/bin# nmap -sS -p 3389 192.168.192.128

Starting Nmap 6.40 ( http://nmap.org ) at 2015-10-01 14:08 BST
Nmap scan report for win2012dom01.sec.nwl (192.168.192.128)
Host is up (0.00016s latency).
PORT     STATE SERVICE
3389/tcp open  ms-wbt-server
MAC Address: 00:0C:29:9B:25:56 (VMware)


Nmap done: 1 IP address (1 host up) scanned in 0.48 seconds
```



However when I scan from my work VLAN the port is showing up as filtered...

```
# nmap -sS -PN -p 8000 10.150.20.177

Starting Nmap 4.76 ( http://nmap.org ) at 2015-10-01 14:08 BST
Interesting ports on 10.150.20.177:
PORT     STATE    SERVICE
8000/tcp filtered http-alt


Nmap done: 1 IP address (1 host up) scanned in 2.09 seconds
```

I've made sure port forwarding is on and I now can't see where I'm going wrong...

Any help or pointers would really be appreciated.

Thanks,
Graeme

---

### Post by SeijiSensei on 2015-10-01
A typo perhaps?

```
tcp dpt:8000 to:192.168.192.128:**3189**
```

Should be 3**3**89, no?

---

### Post by graeme3 on 2015-10-01
Ahhh nice spot, but even after correcting this I still run into the same problem.

```
root@ubu1404srv01:/usr/local/bin# iptables -L -vt natChain PREROUTING (policy ACCEPT 95 packets, 8516 bytes)
 pkts bytes target     prot opt in     out     source               destination
    2    88 DNAT       tcp  --  eth0   any     anywhere             anywhere             tcp dpt:8000 to:192.168.192.128:3389


Chain INPUT (policy ACCEPT 4 packets, 208 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 5 packets, 313 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 7 packets, 401 bytes)
 pkts bytes target     prot opt in     out     source               destination



```


```
lxwasuse02:/tmp/jerry # nmap -sS -PN -p 8000 10.150.20.177

Starting Nmap 4.76 ( http://nmap.org ) at 2015-10-01 15:15 BST
Interesting ports on 10.150.20.177:
PORT     STATE    SERVICE
8000/tcp filtered http-alt


Nmap done: 1 IP address (1 host up) scanned in 2.07 seconds
```

---

### Post by Doug S on 2015-10-01
I don't see a POSTROUTING rule, needed to perform nat between your 192.168.192.0 sub-net and the main 10.150.20.0 sub-net.

---

