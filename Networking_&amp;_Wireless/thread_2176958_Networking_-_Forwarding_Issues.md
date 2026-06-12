---
title: "Networking - Forwarding Issues"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by Peter_Lewis on 2013-09-26
I have a 13.04 server with 2 interfaces.

servers eth0
eth0 (wan) 172.20.1.17/24  - This interface is connected to a router that will be used as our internet gateway.  The router has an interface that the server is connected to with address 172.20.1.1/24(routers ip).

Example of the routers routing table...
0.0.0.0/0   ->     gateway = it's public gateway(works not a part of this question)
172.20.1.0/24 -> gateway = Lan Interface that our server is connected to. (all other hosts on this network are working fine and the server has internet access)
10.17.17.0/25 -> gateway = 172.20.1.17 (pointed at the ip of our server)

This all works fine... lets move on.
 
servers eth1
eth1 (Lan) 10.17.17.1/25

I have a couple computers connected to a switch on the servers LAN interface.  The computers have static ip's on the 10.17.17.0/25 network.

The servers routing table...

default         172.20.1.1     0.0.0.0         UG    0      0        0 eth0
10.17.17.0      *               255.255.255.128 U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
172.20.1.0      *               255.255.255.0   U     0      0        0 eth0

ifconfig output from the server.

eth0      Link encap:Ethernet  HWaddr 00:25:90:d4:43:3f  
          inet addr:172.20.1.17  Bcast:172.20.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fed4:433f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74034 errors:0 dropped:23 overruns:0 frame:0
          TX packets:110451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13584832 (13.5 MB)  TX bytes:10578014 (10.5 MB)
          Memory:ee400000-ee480000 


eth1      Link encap:Ethernet  HWaddr 00:25:90:d4:43:3e  
          inet addr:10.17.17.1  Bcast:10.17.17.127  Mask:255.255.255.128
          inet6 addr: fe80::225:90ff:fed4:433e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7758 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:655301 (655.3 KB)  TX bytes:324797 (324.7 KB)
          Interrupt:20 Memory:ee800000-ee820000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:19832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19832 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2015396 (2.0 MB)  TX bytes:2015396 (2.0 MB)


I set the server to allow forwarding.

cat /proc/sys/net/ipv4/ip_forward 
1

a look at the network interface config...

cat /etc/network/interfaces 
auto lo
iface lo inet loopback
pre-up iptables-restore < /etc/iptables/iptables.conf


auto eth0
iface eth0 inet static
network 172.20.1.0
address 172.20.1.17
netmask 255.255.255.0
broadcast 172.20.1.255
gateway 172.20.1.1
dns-nameservers 8.8.8.8 8.8.4.4


auto eth1
iface eth1 inet static
network 10.17.17.0
address 10.17.17.1
netmask 255.255.255.128
broadcast 10.17.17.127

I disabled my firewall for now...
iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


ping tests from server

ping 172.20.1.1
PING 172.20.1.1 (172.20.1.1) 56(84) bytes of data.
64 bytes from 172.20.1.1: icmp_req=1 ttl=64 time=0.263 ms
64 bytes from 172.20.1.1: icmp_req=2 ttl=64 time=0.245 ms
^C
ping 10.17.17.3
PING 10.17.17.3 (10.17.17.3) 56(84) bytes of data.
64 bytes from 10.17.17.3: icmp_req=1 ttl=64 time=0.272 ms
64 bytes from 10.17.17.3: icmp_req=2 ttl=64 time=0.256 ms
^C

Pings from any host on 172.20.1.0/24 to any host on 10.17.17.0/25 or vice versa fails.





So to sum up the situation the Ubuntu server has two interfaces a wan and a LAN.  The LAN computers are statically assigned so no need for any dhcp services on the lan.  The server is statically assigned on its wan so no need for a dhcp client.  The upstream router has a route for the servers lan and will be handling nat translation at its wan interface so no need for NAT in iptables on the server.  For the ease of troubleshooting I have set iptables to accept all (input, forward and output) firewall chains. The server can see both networks and can ping hosts on both networks.  

The problem is that hosts on both networks can not forward(ping) traffic though the Ubuntu server.  Trace routes from any host on ether network trying to communicate with the opposite network will hit the first hop successfully(ubuntu server) and timeout never reaching the second hop which should be the host on the other network(host on the other side of the server).

I have rebooted multiple times.

Thanks for your help in advance. 

Any idea what is wrong or what I can do to troubleshoot further?

Let me know if any additional information is needed.

Thanks Pete

---

### Post by 7182818 on 2013-09-26
Man, this is a tough one.  Everything seems right from the information you've provided.  I would try running tcpdump on the interfaces along the path to try and isolate where the packets actually stop being sent at.  For example, one thing you could verify is that the server is actually forwarding the packets correctly.  For that, try pinging from one of your 10.17.17.0/25 hosts and running tcpdump on the server's eth0 to see if you can see the outgoing packets.  If you can, then check to see if you see the ICMP responses.

---

### Post by SeijiSensei on 2013-09-27
I found it a bit hard to determine what the problem might be, but it sounds like you don't have "masquerading" enabled on the gateway box.  Try adding this line to your iptables ruleset:

```
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 172.20.1.17
```

---

### Post by Doug S on 2013-09-27
@Seiji: I thought that also at first, but the OP seems to want the final router to do the NAT stuff for both network sub-nets. Then is the issue possibly that eth0 and eth1 should be bridged? Regardless, I agree that implementing NAT at the server would be the easiest.

---

### Post by Peter_Lewis on 2013-09-27
I haven't been able to put much time into this yet today but I will in a couple hours.  I had a quick look at a tcpdump and the traffic did not seem to be forwarding but I will take a closer look at it in a bit and post some of the output.

On the NAT subject...  The hosts on the lan side of the server (eth1) need to be routable with hosts on the servers wan interface(eth0).   For that reason the server can't nat the traffic.  The router attached to eth0 does all the NAT for public bound traffic.  The servers firewall is simply accepting all traffic while I'm troubleshooting this issue.

I don't think I would want to bridge the two interfaces.  The server should route that traffic in this situation.  If you wanted to share the same subnet across both interfaces like a layer two switch does, bridging would make sense.  I haven't used servers to route traffic before though so please let me know if I'm looking at this wrong.

---

### Post by s-bodet on 2013-09-29
Hi,

that should work, no need to enable NAT onto your Ubuntu server.

What are the hosts onto the LAN ?  What's their routing table ?

Steve

---

### Post by Peter_Lewis on 2013-09-30
Here is the server:

pete@skdwdt:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:90:d4:43:3f  
          inet addr:172.20.1.17  Bcast:172.20.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fed4:433f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:579922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:285059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:453247020 (453.2 MB)  TX bytes:43066956 (43.0 MB)
          Memory:ee400000-ee480000 


eth1      Link encap:Ethernet  HWaddr 00:25:90:d4:43:3e  
          inet addr:10.17.17.1  Bcast:10.17.17.127  Mask:255.255.255.128
          inet6 addr: fe80::225:90ff:fed4:433e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:518874 (518.8 KB)  TX bytes:17342721 (17.3 MB)
          Interrupt:20 Memory:ee800000-ee820000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7908 (7.9 KB)  TX bytes:7908 (7.9 KB)



pete@skdwdt:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         172.20.1.1     0.0.0.0         UG    0      0        0 eth0
10.17.17.0      *               255.255.255.128 U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
172.20.1.0      *               255.255.255.0   U     0      0        0 eth0


pete@skdwdt:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
skdwlt.local             ether   b8:70:f4:64:b0:76   C                     eth1
172.20.1.1 ether   00:60:e0:4d:73:30   C                     eth0


pete@skdwdt:~$ ping skdwlt.local
PING skdwlt.local (10.17.17.3) 56(84) bytes of data.
64 bytes from skdwlt.local (10.17.17.3): icmp_req=1 ttl=64 time=0.502 ms
64 bytes from skdwlt.local (10.17.17.3): icmp_req=2 ttl=64 time=0.453 ms


#####################################################
Here is the host on the LAN Interface:

pete@skdwlt:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:70:f4:64:b0:76  
          inet addr:10.17.17.3  Bcast:10.17.17.127  Mask:255.255.255.128
          inet6 addr: fe80::ba70:f4ff:fe64:b076/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73922 errors:0 dropped:25 overruns:0 frame:0
          TX packets:6741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12811520 (12.8 MB)  TX bytes:663474 (663.4 KB)
          Interrupt:48 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:784898 (784.8 KB)  TX bytes:784898 (784.8 KB)


wmx0      Link encap:Ethernet  HWaddr 64:d4:da:03:e5:d1  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



pete@skdwlt:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         skdwdt.local    0.0.0.0         UG    0      0        0 eth0
10.17.17.0      *               255.255.255.128 U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0


pete@skdwlt:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
10.17.17.2               ether   d4:ca:6d:43:98:d6   C                     eth0
skdwdt.local             ether   00:25:90:d4:43:3e   C                     eth0


pete@skdwlt:~$ ping skdwdt.local
PING skdwdt.local (10.17.17.1) 56(84) bytes of data.
64 bytes from skdwdt.local (10.17.17.1): icmp_req=1 ttl=64 time=0.339 ms
64 bytes from skdwdt.local (10.17.17.1): icmp_req=2 ttl=64 time=0.345 ms

pete@skdwlt:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

...
no response what so ever...
same as when I try to ping 172.20.1.1 From the LAN Host

####################################################
Here is a tcpdump of the server while the LAN host is trying to ping 8.8.8.8 from the LAN:

pete@skdwdt:~$ sudo tcpdump 
[sudo] password for pete: 
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
18:06:40.920121 IP skdwlt.local > google-public-dns-a.google.com: ICMP echo request, id 3805, seq 17, length 64
18:06:40.920871 IP skdwdt.gtekadmin.com.40182 > gtekadmin.com.domain: 31779+ PTR? 8.8.8.8.in-addr.arpa. (38)
18:06:40.921293 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.40182: 31779 Refused- 0/0/0 (38)
18:06:40.921399 IP skdwdt.gtekadmin.com.58504 > 172.20.1.1.domain: 31779+ PTR? 8.8.8.8.in-addr.arpa. (38)
18:06:40.962343 IP 172.20.1.22.17500 > 255.255.255.255.17500: UDP, length 136
18:06:40.963943 IP 172.20.1.22.17500 > 172.20.1.255.17500: UDP, length 136
18:06:40.985102 IP 172.20.1.1.domain > skdwdt.gtekadmin.com.58504: 31779 1/13/0 PTR google-public-dns-a.google.com. (293)
18:06:40.985793 IP skdwdt.gtekadmin.com.44705 > gtekadmin.com.domain: 40127+ PTR? 1.0.168.192.in-addr.arpa. (42)
18:06:40.986149 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.44705: 40127*- 1/1/1 PTR gtekadmin.com. (103)
18:06:40.986947 IP skdwdt.gtekadmin.com.52532 > gtekadmin.com.domain: 14660+ PTR? 1.1.20.172.in-addr.arpa. (42)
18:06:40.987256 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.52532: 14660 Refused- 0/0/0 (42)
18:06:40.987345 IP skdwdt.gtekadmin.com.36187 > 172.20.1.1.domain: 14660+ PTR? 1.1.20.172.in-addr.arpa. (42)
18:06:41.022988 IP 172.20.1.1.domain > skdwdt.gtekadmin.com.36187: 14660 NXDomain 0/0/0 (42)
18:06:41.123901 IP6 fe80::225:90ff:fed4:433f.mdns > ff02::fb.mdns: 0 PTR (QM)? 1.1.20.172.in-addr.arpa. (42)
18:06:41.123939 IP skdwdt.gtekadmin.com.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.1.20.172.in-addr.arpa. (42)
18:06:41.237838 ARP, Request who-has 172.20.1.224 tell 172.20.1.22, length 46
18:06:41.324475 IP 172.20.1.216.netbios-ns > 172.20.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
18:06:41.332745 IP 172.20.1.22.netbios-ns > 172.20.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
18:06:41.722550 ARP, Request who-has 172.20.1.224 tell 172.20.1.21, length 46
18:06:41.722563 ARP, Request who-has 172.20.1.229 tell 172.20.1.21, length 46
18:06:41.928056 IP skdwlt.local > google-public-dns-a.google.com: ICMP echo request, id 3805, seq 18, length 64
18:06:42.074648 IP 172.20.1.216.netbios-ns > 172.20.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
18:06:42.083462 IP 172.20.1.22.netbios-ns > 172.20.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
18:06:42.125640 IP6 fe80::225:90ff:fed4:433f.mdns > ff02::fb.mdns: 0 PTR (QM)? 1.1.20.172.in-addr.arpa. (42)
18:06:42.125679 IP skdwdt.gtekadmin.com.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.1.20.172.in-addr.arpa. (42)
18:06:42.127400 IP skdwlt.local.21634 > gtekadmin.com.domain: 39398+ A? daisy.ubuntu.com. (34)
18:06:42.127409 IP skdwlt.local.21634 > 172.20.1.1.domain: 39398+ A? daisy.ubuntu.com. (34)
18:06:42.127414 IP skdwlt.local.21634 > google-public-dns-a.google.com.domain: 39398+ A? daisy.ubuntu.com. (34)
18:06:42.237850 ARP, Request who-has 172.20.1.224 tell 172.20.1.22, length 46
18:06:42.859641 IP 172.20.1.223.netbios-ns > 172.20.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
18:06:42.935999 IP skdwlt.local > google-public-dns-a.google.com: ICMP echo request, id 3805, seq 19, length 64
18:06:42.958145 ARP, Request who-has 172.20.1.1 tell 172.20.1.227, length 46
18:06:42.960243 ARP, Reply 172.20.1.227 is-at 08:00:37:41:62:5f (oui Unknown), length 46
^C18:06:43.248765 IP 172.20.1.239.58543 > 239.255.255.250.1900: UDP, length 133


34 packets captured
780 packets received by filter
716 packets dropped by kernel

---

### Post by The Cog on 2013-09-30
So we can see echo requests on eth0 addressed to google. eth0 is the wan port, so the server is forwarding the ping request.

Please can you try and ping both 172.20.1.17 and 172.20.1.1 from the LAN host skdwdt.

---

### Post by Peter_Lewis on 2013-10-01
ya sure.  This is a tcpdump from the server(172.20.1.17) while the Host(10.17.17.3) on the LAN is pinging 172.20.1.1 and 172.20.1.17.

The Host on the LAN skdwlt can ping the server 172.20.1.17 but not the gateway 172.20.1.1.

Server:

pete@skdwdt:~$ sudo tcpdump
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
07:41:12.513595 IP gtekNas1.local.netbios-ns > 172.20.1.255.netbios-ns: NBT UDP PACKET(137): REGISTRATION; REQUEST; BROADCAST
07:41:12.514363 IP skdwdt.gtekadmin.com.52674 > gtekadmin.com.domain: 12432+ PTR? 255.1.20.172.in-addr.arpa. (43)
07:41:12.514635 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.52674: 12432 Refused- 0/0/0 (43)
07:41:12.514697 IP gtekNas1.local.netbios-ns > 172.20.1.255.netbios-ns: NBT UDP PACKET(137): REGISTRATION; REQUEST; BROADCAST
07:41:12.514711 IP skdwdt.gtekadmin.com.58179 > 172.20.1.1.domain: 12432+ PTR? 255.1.20.172.in-addr.arpa. (43)
07:41:12.526323 ARP, Request who-has 172.20.1.250 tell Tracy-PC.local, length 46
07:41:12.528540 IP 172.20.1.245.netbios-dgm > 172.20.1.255.netbios-dgm: NBT UDP PACKET(138)
07:41:12.541270 ARP, Request who-has 172.20.1.224 tell Tracy-PC.local, length 46
07:41:12.550070 IP 172.20.1.1.domain > skdwdt.gtekadmin.com.58179: 12432 NXDomain 0/0/0 (43)
07:41:12.650999 IP6 fe80::225:90ff:fed4:433f.mdns > ff02::fb.mdns: 0 PTR (QM)? 255.1.20.172.in-addr.arpa. (43)
07:41:12.651038 IP skdwdt.gtekadmin.com.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.20.172.in-addr.arpa. (43)
07:41:12.739883 IP 172.20.1.231.17500 > 255.255.255.255.17500: UDP, length 112
07:41:12.741247 IP 172.20.1.231.17500 > 172.20.1.255.17500: UDP, length 112
07:41:12.884691 IP6 fe80::1946:dccf:f01:d0f4.dhcpv6-client > ff02::1:2.dhcpv6-server: dhcp6 solicit
07:41:12.970430 ARP, Request who-has 172.20.1.224 tell 172.20.1.21, length 46
07:41:12.970443 ARP, Request who-has 172.20.1.229 tell 172.20.1.21, length 46
07:41:13.040500 ARP, Request who-has 172.20.1.250 tell Tracy-PC.local, length 46
07:41:13.227249 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 4818, seq 58, length 64
07:41:13.539674 ARP, Request who-has 172.20.1.224 tell Tracy-PC.local, length 46
07:41:13.652787 IP6 fe80::225:90ff:fed4:433f.mdns > ff02::fb.mdns: 0 PTR (QM)? 255.1.20.172.in-addr.arpa. (43)
07:41:13.652823 IP skdwdt.gtekadmin.com.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.20.172.in-addr.arpa. (43)
07:41:13.654302 IP skdwlt.local.42576 > gtekadmin.com.domain: 33380+ A? daisy.ubuntu.com. (34)
07:41:13.654314 IP skdwlt.local.42576 > 172.20.1.1.domain: 33380+ A? daisy.ubuntu.com. (34)
07:41:13.654319 IP skdwlt.local.42576 > google-public-dns-a.google.com.domain: 33380+ A? daisy.ubuntu.com. (34)
07:41:14.038930 ARP, Request who-has 172.20.1.250 tell Tracy-PC.local, length 46
07:41:14.227166 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 4818, seq 59, length 64
07:41:14.461548 ARP, Request who-has 172.20.1.224 tell 172.20.1.221, length 46
07:41:14.471500 ARP, Request who-has 172.20.1.229 tell 172.20.1.239, length 46
07:41:14.906795 IP 172.20.1.216.63265 > 239.255.255.250.1900: UDP, length 133
07:41:14.970582 ARP, Request who-has 172.20.1.229 tell 172.20.1.239, length 46
07:41:15.227076 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 4818, seq 60, length 64
07:41:22.699083 IP skdwdt.gtekadmin.com.56242 > gtekadmin.com.domain: 34626+ PTR? 1.0.168.192.in-addr.arpa. (42)
07:41:22.699727 IP skdwdt.gtekadmin.com.53237 > gtekadmin.com.domain: 15873+ PTR? 1.1.20.172.in-addr.arpa. (42)
07:41:22.700033 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.53237: 15873 Refused- 0/0/0 (42)
07:41:22.700117 IP skdwdt.gtekadmin.com.49229 > 172.20.1.1.domain: 15873+ PTR? 1.1.20.172.in-addr.arpa. (42)
07:41:27.737929 IP skdwdt.gtekadmin.com.56322 > gtekadmin.com.domain: 7339+ PTR? 250.1.20.172.in-addr.arpa. (43)
07:41:32.910921 IP skdwdt.gtekadmin.com.57604 > gtekadmin.com.domain: 57381+ PTR? 245.1.20.172.in-addr.arpa. (43)
07:41:37.948990 IP skdwdt.gtekadmin.com.40341 > gtekadmin.com.domain: 49288+ PTR? 224.1.20.172.in-addr.arpa. (43)
07:41:42.985540 IP skdwdt.gtekadmin.com.56628 > gtekadmin.com.domain: 27194+ PTR? b.f.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.2.0.f.f.ip6.arpa. (90)
07:41:42.986005 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.56628: 27194 Refused- 0/0/0 (90)
07:41:43.021571 IP skdwdt.gtekadmin.com.54410 > gtekadmin.com.domain: 51742+ PTR? 251.0.0.224.in-addr.arpa. (42)
07:41:48.059028 IP skdwdt.gtekadmin.com.43350 > gtekadmin.com.domain: 7207+ PTR? 255.255.255.255.in-addr.arpa. (46)
07:41:58.104108 IP skdwdt.gtekadmin.com.53552 > gtekadmin.com.domain: 12282+ PTR? 2.0.0.0.1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.2.0.f.f.ip6.arpa. (90)
07:41:58.104640 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.53552: 12282 Refused- 0/0/0 (90)
07:41:58.140877 IP skdwdt.gtekadmin.com.54163 > gtekadmin.com.domain: 44236+ PTR? 21.1.20.172.in-addr.arpa. (42)
07:42:03.179200 IP skdwdt.gtekadmin.com.45501 > gtekadmin.com.domain: 31637+ PTR? 229.1.20.172.in-addr.arpa. (43)
07:42:08.217487 IP skdwdt.gtekadmin.com.42555 > gtekadmin.com.domain: 19567+ PTR? 3.17.17.10.in-addr.arpa. (41)
07:42:08.217990 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.42555: 19567 Refused- 0/0/0 (41)
07:42:08.353874 IP skdwdt.gtekadmin.com.44440 > gtekadmin.com.domain: 37577+ PTR? 8.8.8.8.in-addr.arpa. (38)
07:42:08.354212 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.44440: 37577 Refused- 0/0/0 (38)
07:42:08.354304 IP skdwdt.gtekadmin.com.50053 > 172.20.1.1.domain: 37577+ PTR? 8.8.8.8.in-addr.arpa. (38)
07:42:08.388585 IP 172.20.1.1.domain > skdwdt.gtekadmin.com.50053: 37577 1/0/0 PTR google-public-dns-a.google.com. (82)
07:42:08.388863 IP skdwdt.gtekadmin.com.48758 > gtekadmin.com.domain: 38252+ PTR? 221.1.20.172.in-addr.arpa. (43)
07:42:08.389170 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.48758: 38252 Refused- 0/0/0 (43)
07:42:08.389255 IP skdwdt.gtekadmin.com.38862 > 172.20.1.1.domain: 38252+ PTR? 221.1.20.172.in-addr.arpa. (43)
07:42:08.423769 IP 172.20.1.1.domain > skdwdt.gtekadmin.com.38862: 38252 NXDomain 0/0/0 (43)
07:42:08.524670 IP6 fe80::225:90ff:fed4:433f.mdns > ff02::fb.mdns: 0 PTR (QM)? 221.1.20.172.in-addr.arpa. (43)
07:42:13.427142 IP skdwdt.gtekadmin.com.49009 > gtekadmin.com.domain: 27130+ PTR? 239.1.20.172.in-addr.arpa. (43)
07:42:18.464694 IP skdwdt.gtekadmin.com.53516 > gtekadmin.com.domain: 26482+ PTR? 250.255.255.239.in-addr.arpa. (46)
07:42:28.571086 ARP, Request who-has 172.20.1.229 tell 172.20.1.239, length 46
07:42:28.673409 ARP, Request who-has 172.20.1.224 tell 172.20.1.22, length 46
07:42:28.673669 IP skdwdt.gtekadmin.com.47148 > gtekadmin.com.domain: 8910+ PTR? 22.1.20.172.in-addr.arpa. (42)
07:42:28.674200 IP gtekadmin.com.domain > skdwdt.gtekadmin.com.47148: 8910 Refused- 0/0/0 (42)
07:42:28.674337 IP skdwdt.gtekadmin.com.48914 > 172.20.1.1.domain: 8910+ PTR? 22.1.20.172.in-addr.arpa. (42)
07:42:28.709542 IP 172.20.1.1.domain > skdwdt.gtekadmin.com.48914: 8910 NXDomain 0/0/0 (42)
07:42:28.810306 IP6 fe80::225:90ff:fed4:433f.mdns > ff02::fb.mdns: 0 PTR (QM)? 22.1.20.172.in-addr.arpa. (42)
07:42:28.810354 IP skdwdt.gtekadmin.com.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 22.1.20.172.in-addr.arpa. (42)
07:42:28.884799 IP dfw06s40-in-f3.1e100.net.https > skdwdt.gtekadmin.com.54425: Flags [P.], seq 2703655064:2703655125, ack 1124956803, win 1002, options [nop,nop,TS val 2835381370 ecr 19846883], length 61
07:42:28.884830 IP dfw06s40-in-f3.1e100.net.https > skdwdt.gtekadmin.com.54425: Flags [P.], seq 61:102, ack 1, win 1002, options [nop,nop,TS val 2835381370 ecr 19846883], length 41
07:42:28.884837 IP dfw06s40-in-f3.1e100.net.https > skdwdt.gtekadmin.com.54425: Flags [F.], seq 102, ack 1, win 1002, options [nop,nop,TS val 2835381370 ecr 19846883], length 0
07:42:28.884909 IP skdwdt.gtekadmin.com.54425 > dfw06s40-in-f3.1e100.net.https: Flags [.], ack 103, win 247, options [nop,nop,TS val 19906885 ecr 2835381370], length 0
07:42:28.885298 IP skdwdt.gtekadmin.com.54425 > dfw06s40-in-f3.1e100.net.https: Flags [F.], seq 1, ack 103, win 247, options [nop,nop,TS val 19906885 ecr 2835381370], length 0
07:42:28.912206 IP dfw06s40-in-f3.1e100.net.https > skdwdt.gtekadmin.com.54425: Flags [.], ack 2, win 1002, options [nop,nop,TS val 2835381398 ecr 19906885], length 0
07:42:29.029751 IP 172.20.1.216.netbios-ns > 172.20.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
07:42:29.119466 IP dfw06s33-in-f7.1e100.net.https > skdwdt.gtekadmin.com.60178: Flags [P.], seq 1160896380:1160896441, ack 3010063531, win 661, options [nop,nop,TS val 612679855 ecr 19846953], length 61
07:42:29.119507 IP skdwdt.gtekadmin.com.60178 > dfw06s33-in-f7.1e100.net.https: Flags [.], ack 61, win 331, options [nop,nop,TS val 19906944 ecr 612679855], length 0
07:42:29.119514 IP dfw06s33-in-f7.1e100.net.https > skdwdt.gtekadmin.com.60178: Flags [P.], seq 61:102, ack 1, win 661, options [nop,nop,TS val 612679855 ecr 19846953], length 41
07:42:29.119520 IP skdwdt.gtekadmin.com.60178 > dfw06s33-in-f7.1e100.net.https: Flags [.], ack 102, win 331, options [nop,nop,TS val 19906944 ecr 612679855], length 0
07:42:29.119524 IP dfw06s33-in-f7.1e100.net.https > skdwdt.gtekadmin.com.60178: Flags [F.], seq 102, ack 1, win 661, options [nop,nop,TS val 612679855 ecr 19846953], length 0
07:42:29.119974 IP skdwdt.gtekadmin.com.60178 > dfw06s33-in-f7.1e100.net.https: Flags [F.], seq 1, ack 103, win 331, options [nop,nop,TS val 19906944 ecr 612679855], length 0
^C07:42:29.136807 IP 172.20.1.182.netbios-ns > 172.20.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
81 packets captured
1213 packets received by filter
1102 packets dropped by kernel

eth1

pete@skdwdt:~$ sudo tcpdump -i eth1
[sudo] password for pete: 
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
08:21:24.441708 IP skdwlt.local > skdwdt.gtekadmin.com: ICMP echo request, id 4982, seq 36, length 64
08:21:24.441749 IP skdwdt.gtekadmin.com > skdwlt.local: ICMP echo reply, id 4982, seq 36, length 64
08:21:24.453594 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 5038, seq 25, length 64
08:21:24.564379 IP6 fe80::225:90ff:fed4:433e.mdns > ff02::fb.mdns: 0 PTR (QM)? 3.17.17.10.in-addr.arpa. (41)
08:21:24.564467 IP skdwdt.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 3.17.17.10.in-addr.arpa. (41)
08:21:24.565163 IP skdwlt.local.mdns > 224.0.0.251.mdns: 0*- [0q] 1/0/0 (Cache flush) PTR skdwlt.local. (61)
08:21:24.687611 IP6 fe80::225:90ff:fed4:433e.mdns > ff02::fb.mdns: 0 PTR (QM)? 1.1.20.172.in-addr.arpa. (42)
08:21:24.687721 IP skdwdt.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.1.20.172.in-addr.arpa. (42)
08:21:25.362063 IP skdwdt.local.24800 > skdwlt.local.48229: Flags [P.], seq 2068570348:2068570356, ack 3139055560, win 330, options [nop,nop,TS val 20491004 ecr 19941448], length 8
08:21:25.363369 IP skdwlt.local.48229 > skdwdt.local.24800: Flags [P.], seq 1:17, ack 8, win 331, options [nop,nop,TS val 19942205 ecr 20491004], length 16
08:21:25.363394 IP skdwdt.local.24800 > skdwlt.local.48229: Flags [.], ack 17, win 330, options [nop,nop,TS val 20491005 ecr 19942205], length 0
08:21:25.441645 IP skdwlt.local > skdwdt.gtekadmin.com: ICMP echo request, id 4982, seq 37, length 64
08:21:25.441677 IP skdwdt.gtekadmin.com > skdwlt.local: ICMP echo reply, id 4982, seq 37, length 64
08:21:25.453480 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 5038, seq 26, length 64
08:21:25.567766 IP skdwlt.local.43861 > gtekadmin.com.domain: 25358+ A? daisy.ubuntu.com. (34)
08:21:25.567787 IP skdwlt.local.43861 > 172.20.1.1.domain: 25358+ A? daisy.ubuntu.com. (34)
08:21:25.567792 IP skdwlt.local.43861 > google-public-dns-a.google.com.domain: 25358+ A? daisy.ubuntu.com. (34)
08:21:25.688479 IP6 fe80::225:90ff:fed4:433e.mdns > ff02::fb.mdns: 0 PTR (QM)? 1.1.20.172.in-addr.arpa. (42)
08:21:25.688555 IP skdwdt.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.1.20.172.in-addr.arpa. (42)
08:21:26.441596 IP skdwlt.local > skdwdt.gtekadmin.com: ICMP echo request, id 4982, seq 38, length 64
08:21:26.441631 IP skdwdt.gtekadmin.com > skdwlt.local: ICMP echo reply, id 4982, seq 38, length 64
08:21:26.453376 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 5038, seq 27, length 64
08:21:27.441558 IP skdwlt.local > skdwdt.gtekadmin.com: ICMP echo request, id 4982, seq 39, length 64
08:21:27.441591 IP skdwdt.gtekadmin.com > skdwlt.local: ICMP echo reply, id 4982, seq 39, length 64
08:21:27.453351 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 5038, seq 28, length 64
08:21:27.691146 IP6 fe80::225:90ff:fed4:433e.mdns > ff02::fb.mdns: 0 PTR (QM)? 1.1.20.172.in-addr.arpa. (42)
08:21:27.691248 IP skdwdt.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.1.20.172.in-addr.arpa. (42)
08:21:28.396523 IP skdwdt.local.24800 > skdwlt.local.48229: Flags [P.], seq 8:16, ack 17, win 330, options [nop,nop,TS val 20491763 ecr 19942205], length 8
08:21:28.397839 IP skdwlt.local.48229 > skdwdt.local.24800: Flags [P.], seq 17:33, ack 16, win 331, options [nop,nop,TS val 19942964 ecr 20491763], length 16
08:21:28.397864 IP skdwdt.local.24800 > skdwlt.local.48229: Flags [.], ack 33, win 330, options [nop,nop,TS val 20491763 ecr 19942964], length 0
08:21:28.441326 IP skdwlt.local > skdwdt.gtekadmin.com: ICMP echo request, id 4982, seq 40, length 64
08:21:28.441358 IP skdwdt.gtekadmin.com > skdwlt.local: ICMP echo reply, id 4982, seq 40, length 64
08:21:28.453200 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 5038, seq 29, length 64
08:21:34.830928 IP6 fe80::225:90ff:fed4:433e.mdns > ff02::fb.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
08:21:34.831007 IP skdwdt.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
08:21:40.440507 IP skdwlt.local > skdwdt.gtekadmin.com: ICMP echo request, id 4982, seq 52, length 64
08:21:40.440545 IP skdwdt.gtekadmin.com > skdwlt.local: ICMP echo reply, id 4982, seq 52, length 64
08:21:40.452289 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 5038, seq 41, length 64
08:21:40.460582 IP skdwdt.local.24800 > skdwlt.local.48229: Flags [P.], seq 40:48, ack 81, win 330, options [nop,nop,TS val 20494779 ecr 19945226], length 8
08:21:40.461906 IP skdwlt.local.48229 > skdwdt.local.24800: Flags [P.], seq 81:97, ack 48, win 331, options [nop,nop,TS val 19945980 ecr 20494779], length 16
08:21:40.461935 IP skdwdt.local.24800 > skdwlt.local.48229: Flags [.], ack 97, win 330, options [nop,nop,TS val 20494779 ecr 19945980], length 0
08:21:40.582517 IP skdwlt.local.32857 > gtekadmin.com.domain: 24996+ A? daisy.ubuntu.com.gtekadmin.com. (48)
08:21:40.582551 IP skdwlt.local.32857 > 172.20.1.1.domain: 24996+ A? daisy.ubuntu.com.gtekadmin.com. (48)
08:21:40.582556 IP skdwlt.local.32857 > google-public-dns-a.google.com.domain: 24996+ A? daisy.ubuntu.com.gtekadmin.com. (48)
08:21:41.440401 IP skdwlt.local > skdwdt.gtekadmin.com: ICMP echo request, id 4982, seq 53, length 64
08:21:41.440439 IP skdwdt.gtekadmin.com > skdwlt.local: ICMP echo reply, id 4982, seq 53, length 64
08:21:41.452234 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 5038, seq 42, length 64
08:21:42.440310 IP skdwlt.local > skdwdt.gtekadmin.com: ICMP echo request, id 4982, seq 54, length 64
08:21:42.440354 IP skdwdt.gtekadmin.com > skdwlt.local: ICMP echo reply, id 4982, seq 54, length 64
08:21:42.452197 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 5038, seq 43, length 64
08:21:43.440238 IP skdwlt.local > skdwdt.gtekadmin.com: ICMP echo request, id 4982, seq 55, length 64
08:21:43.440276 IP skdwdt.gtekadmin.com > skdwlt.local: ICMP echo reply, id 4982, seq 55, length 64
08:21:43.452150 IP skdwlt.local > 172.20.1.1: ICMP echo request, id 5038, seq 44, length 64
08:21:43.465739 IP skdwlt.local.22843 > gtekadmin.com.domain: 339+ A? videosearch.ubuntu.com. (40)
08:21:43.465774 IP skdwlt.local.22843 > 172.20.1.1.domain: 339+ A? videosearch.ubuntu.com. (40)
08:21:43.465780 IP skdwlt.local.22843 > google-public-dns-a.google.com.domain: 339+ A? videosearch.ubuntu.com. (40)
08:21:43.476387 IP skdwdt.local.24800 > skdwlt.local.48229: Flags [P.], seq 48:56, ack 97, win 330, options [nop,nop,TS val 20495533 ecr 19945980], length 8
08:21:43.489937 IP skdwlt.local.48229 > skdwdt.local.24800: Flags [P.], seq 97:113, ack 56, win 331, options [nop,nop,TS val 19946737 ecr 20495533], length 16
08:21:43.489969 IP skdwdt.local.24800 > skdwlt.local.48229: Flags [.], ack 113, win 330, options [nop,nop,TS val 20495536 ecr 19946737], length 0
08:21:43.540965 IP skdwlt.local.44997 > gtekadmin.com.domain: 23860+ A? security.ubuntu.com. (37)
08:21:43.540998 IP skdwlt.local.44997 > 172.20.1.1.domain: 23860+ A? security.ubuntu.com. (37)
08:21:43.541006 IP skdwlt.local.44997 > google-public-dns-a.google.com.domain: 23860+ A? security.ubuntu.com. (37)
08:21:43.692068 IP skdwlt.local.29854 > gtekadmin.com.domain: 32674+ A? us.archive.ubuntu.com. (39)
08:21:43.692099 IP skdwlt.local.29854 > 172.20.1.1.domain: 32674+ A? us.archive.ubuntu.com. (39)
08:21:43.692106 IP skdwlt.local.29854 > google-public-dns-a.google.com.domain: 32674+ A? us.archive.ubuntu.com. (39)
^C
65 packets captured
143 packets received by filter
78 packets dropped by kernel
...

Lan Host:

pete@skdwlt:~$ ping 172.20.1.17
PING 172.20.1.17 (172.20.1.17) 56(84) bytes of data.
64 bytes from 172.20.1.17: icmp_req=1 ttl=64 time=0.378 ms
64 bytes from 172.20.1.17: icmp_req=2 ttl=64 time=0.430 ms
64 bytes from 172.20.1.17: icmp_req=3 ttl=64 time=0.546 ms
...
64 bytes from 172.20.1.17: icmp_req=282 ttl=64 time=0.436 ms
64 bytes from 172.20.1.17: icmp_req=283 ttl=64 time=0.520 ms
64 bytes from 172.20.1.17: icmp_req=284 ttl=64 time=0.531 ms
^C
--- 172.20.1.17 ping statistics ---
284 packets transmitted, 284 received, 0% packet loss, time 282997ms
rtt min/avg/max/mdev = 0.219/0.446/0.571/0.103 ms





pete@skdwlt:~$ ping 172.20.1.1
PING 172.20.1.1 (172.20.1.1) 56(84) bytes of data.
^C
--- 172.20.1.1 ping statistics ---
853 packets transmitted, 0 received, 100% packet loss, time 852051ms

---

### Post by Peter_Lewis on 2013-10-01
It seems like there is something filtering or something on the router that I need to look into.  

It looks like traffic is forwarding though the server just fine right?

---

### Post by Peter_Lewis on 2013-10-01
yep got it.

Thanks Allot for all your help.

The issue was not with the routing on the server or its attached Lan.  I had a couple issues with the router.  A hidden layer two filter was in the way.

The server is forwarding traffic so that all the local networks are routable now.  Using nat at the router instead of the server is all working fine now as well.


Thanks for all your help :). -Pete

---

### Post by Doug S on 2013-10-01
Thanks for reporting back and letting us know. Glad you got it sorted out. Myself, I was very interested in this thread.

---

### Post by The Cog on 2013-10-01
I have no idea. I don't see anything that will allow me to work out who is sending what. 
When you use tcpdump, please use -n to prevent it converting IP addresses to names. 
I can't even do a search and replace on that trace because I can't see the required DNS lookups.

---

### Post by Doug S on 2013-10-01
> **The Cog said:**
> I have no idea. I don't see anything that will allow me to work out who is sending what. 
When you use tcpdump, please use -n to prevent it converting IP addresses to names. 
I can't even do a search and replace on that trace because I can't see the required DNS lookups.Actually, good point. And there are also a great many packets being dropped, I assume due to so many lookups going on. I had meant to suggest:```
sudo tcpdump -n -nn -tttt -i eth0
```

---

### Post by Peter_Lewis on 2013-10-01
OK sounds good I will in the future.  That makes more sense.  

I posted the arp from both the server and the host so that you could see that skdwlt.local and skdwdt.local where talking over the level 2 PDU connection associated with their host names.  Your solution would have been allot easier to view however. 
...
Your right eth0 on this server is on a crazy talkative windows network.  So much net bios it makes me wan't to scream lol.

That's actually the main reason I'm segmenting off my own private subnet.

---

### Post by The Cog on 2013-10-01
> I posted the arp from both the server and the host so that you could see that skdwlt.local and skdwdt.local where talking over the level 2 PDU connection associated with their host names
That's still not giving me IP addresses. I guess the names mean something to you, but they don't to me, and I am still not able to be sure the trace contains the IP addresses we've been talking about. The traces just makes my head spin.

Doug S: What's -nn? I don't see that in man tcpdump.

---

### Post by The Cog on 2013-10-01
> I posted the arp from both the server and the host so that you could see that skdwlt.local and skdwdt.local where talking over the level 2 PDU connection associated with their host names
That's still not giving me IP addresses. I guess the names mean something to you, but they don't to me, and I am still not able to be sure the trace contains the IP addresses we've been talking about. The traces just makes my head spin.

Doug S: What's -nn? I don't see that in man tcpdump.

---

### Post by Peter_Lewis on 2013-10-01
skdwdt = desktop = server
skdwlt = laptop = host

Server: skdwdt
eth0 = 172.20.1.17/24 gw 1.1
eth1 = 10.17.17.1/25

Host: skdwlt
eth0 = 10.17.17.3/25 gw 17.1

hope that helps.

I've already re-addressed and filtered the network so I can't do any more captures for you I'm afraid.

---

### Post by Doug S on 2013-10-01
> **The Cog said:**
> Doug S: What's -nn? I don't see that in man tcpdump.Apparently, it doesn't mean anything. I thought -n was one level of not converting things to names and -nn was a deeper level, but I seem to be wrong. Sorry for any misdirection.

@Peter: If you want to quiet down your tcpdump session then try this (the port 22 part is because I tried it via a SSH session):```
sudo tcpdump -n -tttt -i eth0 not port 137 and not port 138 and not port 139 and not port 22
```Edit: I had not seen your post 18 above when I wrote this.

---

