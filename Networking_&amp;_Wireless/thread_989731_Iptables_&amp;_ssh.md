---
title: "Iptables &amp; ssh?"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2008-11-21
I am sharing a net connection through a ubuntu server. However, when I tried to connect to the servers, all my programs lock up. Everything. SMB, ssh, telnet, ping, etc. Nothing happens, and I have to control-c out. I can ssh/ping/etc out of the servers fine.

I added this rule to my /etc/network/interfaces file:
```
iptables -A INPUT -i $iface -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
```

And i rebooted the networking, and now i get a no rout to host error. Does anybody know what i am doing wrong?

---

### Post by SpaceTeddy on 2008-11-22
ok, firstly - do you want to connect to or through the server (there is a difference here in where the rules go). While we are discussing this: have you done anything else but this one rule with iptables or any other firewall software (firestarter, shorewall, ufs...)

Also, this rule is for incoming packets, and if this is the only rule, it will not work. You are allowing incoming packets, but you do not allow the replies to leave the computer. 

a generic approach to this would be these two rules
```
sudo iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -m state --state ESTABLISHED -j ACCEPT
```

and then for every port that you acctually want to open you add it like this (i'll use ssh as an example)
```
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT
```
this will accept incoming packets, and will allow the server to answer. however, you will not be able to ssh out of the server - that needs another rule. 

Lastly, can you give me the output of:
```
sudo iptables -L -vnx
ifconfig
route -n
```

cheers

---

### Post by rhcm123 on 2008-11-22
> **SpaceTeddy said:**
> ok, firstly - do you want to connect to or through the server (there is a difference here in where the rules go). While we are discussing this: have you done anything else but this one rule with iptables or any other firewall software (firestarter, shorewall, ufs...)

Also, this rule is for incoming packets, and if this is the only rule, it will not work. You are allowing incoming packets, but you do not allow the replies to leave the computer. 

a generic approach to this would be these two rules
```
sudo iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -m state --state ESTABLISHED -j ACCEPT
```

and then for every port that you acctually want to open you add it like this (i'll use ssh as an example)
```
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT
```
this will accept incoming packets, and will allow the server to answer. however, you will not be able to ssh out of the server - that needs another rule. 

Lastly, can you give me the output of:
```
sudo iptables -L -vnx
ifconfig
route -n
```

cheers

I remember you! Ok, here's what i have:
-That firestartrer gateway I was working on is the server i referred to. (protecting my boxes from the net)
I would like to be able to connect through the server to my other servers (i.e. when on the wifi in my back yard i would connect through firestarter
to the severs)

iptables -L -vnx:
```
root@USSR-FIREWALL:~# iptables -L -vnx
Chain INPUT (policy DROP 2 packets, 656 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       192.168.2.1          0.0.0.0/0           tcp flags:!0x17/0x02 
       3      228 ACCEPT     udp  --  *      *       192.168.2.1          0.0.0.0/0           
      22      924 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 
       1       48 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 limit: avg 1/sec burst 5 
       0        0 LSI        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
       0        0 LSI        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  eth0   *       0.0.0.0/0            255.255.255.255     
       8     1892 DROP       all  --  *      *       0.0.0.0/0            192.168.2.255       
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
      46     5042 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
       0        0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
      17    14370 INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
      64     5372 INBOUND    all  --  eth1   *       0.0.0.0/0            192.168.3.1         
       9      396 INBOUND    all  --  eth1   *       0.0.0.0/0            192.168.2.144       
     197    31909 INBOUND    all  --  eth1   *       0.0.0.0/0            192.168.3.255       
       2      656 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       2      656 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 limit: avg 1/sec burst 5 
       0        0 LSI        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
       0        0 LSI        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
     942    55656 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.3.134       tcp dpts:6881:6889 
       0        0 ACCEPT     udp  --  eth0   *       0.0.0.0/0            192.168.3.134       udp dpts:6881:6889 
   14927  2063319 OUTBOUND   all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           
   16380 20148690 ACCEPT     tcp  --  *      *       0.0.0.0/0            192.168.3.0/24      state RELATED,ESTABLISHED 
     249    34642 ACCEPT     udp  --  *      *       0.0.0.0/0            192.168.3.0/24      state RELATED,ESTABLISHED 
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 1 packets, 44 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       192.168.2.144        192.168.2.1         tcp dpt:53 
       3      196 ACCEPT     udp  --  *      *       192.168.2.144        192.168.2.1         udp dpt:53 
      22      924 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
      10      692 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
      18     1146 OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
      53     5780 OUTBOUND   all  --  *      eth1    0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (4 references)
    pkts      bytes target     prot opt in     out     source               destination         
      89    20078 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:80 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:443 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:137:139 
     103    12733 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:137:139 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:445 
       1       60 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:22 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:123 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:123 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:111 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:111 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:2049 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:2049 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:631 
      94    19176 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:631 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
       0        0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain LSI (6 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 reject-with icmp-port-unreachable 
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 reject-with icmp-port-unreachable 
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 REJECT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 reject-with icmp-port-unreachable 
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain LSO (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
    pkts      bytes target     prot opt in     out     source               destination         
       1       48 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
   14254  2024269 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       3      228 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
     740    45700 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

```

ifconfig:
```
root@USSR-FIREWALL:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:37:70:48  
          inet addr:192.168.2.144  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe37:7048/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15108 errors:0 dropped:0 overruns:3 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20451223 (19.5 MB)  TX bytes:2287770 (2.1 MB)
          Interrupt:20 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:09:5b:8c:68:e5  
          inet addr:192.168.3.1  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe8c:68e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2603575 (2.4 MB)  TX bytes:20456158 (19.5 MB)
          Interrupt:16 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62328 (60.8 KB)  TX bytes:62328 (60.8 KB)


```

route -n:
```
root@USSR-FIREWALL:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0

```
Thanks for the help again!!1

---

### Post by SpaceTeddy on 2008-11-22
This is a setting in firestarter... i have no idea how to configure this in firestarter - I have not even seen the program. I only know it is a frontend to iptables - and if you want to be able to do this you will need to understand firestarter. 
Also, the rules i said were for a manual iptables configuration - they don't work as firestarter will flush all manual changes away and then reload it's own configuration...

So, generically, what you need to do is allow a connection in the FORWARD chain to go from one interface to another. Again, i have no idea how this is done in firestarter - if i get the time i'll have a look, tho.

Anybody else how to manipulate the iptables FORWARD chain through firestarter ???

---

### Post by rhcm123 on 2008-11-22
ok, here is what i want to do.
I have a very good linux based router. It has some basic functionality, like ping.

My router is on the 192.168.2.x subnet.
My gateway machine is:
eth0 = 192.168.2.144
eth1 = 192.168.3.1

how do i expose the hosts behind the gateway (i.e. the ones connected to eth1) to the internet. They had little problems when they were directly connected.. so how do i open them up so that they are exposed (firestarter will be blocking the malicious services)

---

### Post by SpaceTeddy on 2008-11-25
i know what needs to be done, i just don't know how to accomplish this with firestarter. I've had a (quick) look at the program, and really don't see how this thing works, as it only seems to handle incoming and outgoing connections (or so i understand it) but does not configure pass-through connections in any way... 

also, i think your network looks something like this ?

Internet
|
router
|
switch -- AP -- Laptop
|
Ubuntu
|
Server


and you want to conection from the Laptop to the server, right ?
in this case, you also need a route to the 192.168.16.3 network on the router, or need to mask the server on the Ubuntu box and then connect to this one (port-forwarding)... 

sorry for answering late and being short.. don't have much time at the moment...

---

### Post by rhcm123 on 2008-11-25
> **SpaceTeddy said:**
> i know what needs to be done, i just don't know how to accomplish this with firestarter. I've had a (quick) look at the program, and really don't see how this thing works, as it only seems to handle incoming and outgoing connections (or so i understand it) but does not configure pass-through connections in any way... 

also, i think your network looks something like this ?

Internet
|
router
|
switch -- AP -- Laptop
|
Ubuntu
|
Server


and you want to conection from the Laptop to the server, right ?
in this case, you also need a route to the 192.168.16.3 network on the router, or need to mask the server on the Ubuntu box and then connect to this one (port-forwarding)... 

sorry for answering late and being short.. don't have much time at the moment...

There's a switch inbetween ubuntu and server in your diagram, but yeah, that's how i have my network setup.

So what your saying is i need to enable port forwarding on on the firestarter box for the server?

---

### Post by SpaceTeddy on 2008-11-26
ok... here are the (possible) solution i know of - i personally prefer 1, but i do not know if this is even possible to handle since i don't know if you can actually perform all needed tasks.

[SIZE="5"]1.) setup proper routing[/SIZE]

for this, you will need to add a route on the router (192.168.2.1) to the 192.168.3.x network. The sample command in a linux shell would look like this:

```
sudo route add -net 192.168.3.0 netmask 255.255.255.0 gw 192.168.2.144
```

once this is done, you will then need to modify the firewall on your ubuntu box to allow traffic passthrough. The easiest (and most unsecure) way to do this is:
```
sudo iptables -P FORWARD ACCEPT
```

and now you should be able to reach the Server from anywhere in your network. Of course, all these commands are temporary and do not survive a reboot. If you need to make them permanent i can tell you where to put them.
[SIZE="5"]
2.) enable port forwarding on the ubuntu box. [/SIZE]
In this case, all changes apply to the ubuntu box. What you do is you forward ports from it to another computer (the same as you would forward ports from your router to an internal computer). a sample command for this would be
```
sudo iptables -A PREROUTING --table nat -p tcp --dport **%service%** --to-destination **%server%** -j DNAT
```
The bold bits need to be changed to your needs. The service is the port that needs to be forwarded, the server is the ip where to forward this too. 

A connection then has to go to the 192.168.2.144, NOT to the server. it will be forwarded appropriately. 
There are two possible hickups here.
1.) rewriting packets does not necessarily mean that they also get accepted. You will still need something in your forward chain that does allow these packets to pass. Caution here, because in the forward chain they have already been rewritten and are no longer addressed to 192.168.2.144 but to the real host behind it. (that's because DNAT is done prerouting... )
2.) do not overlap services from the ubuntu box with the port forwarding. You can acctually lock yourself out by forwarding too much. So, beware that too much might not be what you need.

I hope you noticed that i did NOT talk about firestarter. I really have no idea how this program handles things and how to use it. I can either tell you what iptables rules are needed and you get rid of firestarer, or you will have to find some other way of working with that program. I am not touching it.

hope it helps :)

---

### Post by rhcm123 on 2008-11-29
Forget all this. Ive been reading the firestarter documentation and apparently direct traffic from the interwho cannot pass through a gateway computer.

Until i figure out how to do this (and possibly set up a DMZ) i'll just remove the middle man and have a direct internet connection.

Sorry about all the hassle.

---

