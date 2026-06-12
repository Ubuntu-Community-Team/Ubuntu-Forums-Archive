---
title: "[SOLVED] Problem with SSH VPN"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by bludhound on 2008-06-16
I'm currently trying to set up a SSH VPN on my office network, following the instructions on [https://help.ubuntu.com/community/SSH_VPN]("https://help.ubuntu.com/community/SSH_VPN"). As clear as the instructions are, I ran into a problem at 'Configuring the Interfaces'. Everything went smoothly, except that trying to ping the server and client from each other produced the following error: 

On the client,
ping: sendmsg: Operation not permitted

On the server, nothing happened when I pinged my client until I had to end it with Ctrl-C, and then a 100% packet loss was reported.

I'd really appreciate it if anyone can offer some help here. Thanks in advance!

And here is my ifconfig output, if it helps:

On the server:

```
ath0      Link encap:Ethernet  HWaddr 00:14:6c:31:ef:9b  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe31:ef9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:192829 (188.3 KB)  TX bytes:183082 (178.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:17:31:4e:01:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xd800 Memory:cffe0000-d0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1232 (1.2 KB)  TX bytes:1232 (1.2 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.1.168.100  P-t-P:192.168.1.200  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:2184 (2.1 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-31-EF-9B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37944 errors:0 dropped:0 overruns:0 frame:2304
          TX packets:1709 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3549855 (3.3 MB)  TX bytes:240684 (235.0 KB)
          Interrupt:21 

```

And on the client,

```
eth0      Link encap:Ethernet  HWaddr 00:c0:26:71:ce:af  
          inet addr:202.178.1.100  Bcast:202.178.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:26ff:fe71:ceaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17667063 (16.8 MB)  TX bytes:2669281 (2.5 MB)
          Interrupt:18 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106208 (103.7 KB)  TX bytes:106208 (103.7 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.1.200  P-t-P:192.168.1.100  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2184 (2.1 KB)  TX bytes:0 (0.0 B)
```

My server on the network has an IP of 192.168.1.100, and the target IP of my client on the server's network is 192.168.1.200.

The SSH port is the only open port on the firewall of my server's router. On my client, all ports are blocked by the router's firewall. In addition, the server machine is protected by Firestarter, with the SSH port open to all IP addresses. I've tried turning Firestarter off, but that did not change anything.

---

### Post by kevdog on 2008-06-16
Can you list your current iptables ruleset?
sudo iptables -L

---

### Post by bludhound on 2008-06-16
> **kevdog said:**
> Can you list your current iptables ruleset?
sudo iptables -L

Here's the one on the client:

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:1900 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1900 
ACCEPT     tcp  --  home                 anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  home                 anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             202.178.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
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
ACCEPT     tcp  --  bludhound-desktop    home                tcp dpt:domain 
ACCEPT     udp  --  bludhound-desktop    home                udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
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
ACCEPT     all  --  192.168.1.18         anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:7845 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:7845 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:2869 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:2869 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:10243 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10243 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:10284 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10284 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:10283 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10283 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:10282 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10282 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:10281 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10281 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:10280 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10280 
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


And on the server:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

```

---

### Post by kevdog on 2008-06-16
If you flush your iptables on the client (may want to save the current filewall setup with iptables-save first):
sudo iptables -F

Then recheck with sudo iptables -L to make sure no rulesets exist, then will the process work?

---

### Post by bludhound on 2008-06-16
I've finally got it working by disabling every single firewall in the way. It's a firewall problem after all. Thanks for the help anyway!

---

### Post by kevdog on 2008-06-16
If you saved the file, what you can do is to save a copy, then manually start adding in each section.  It sounds like a outbound policy rather than inbound to be.  That is where I would start.

---

