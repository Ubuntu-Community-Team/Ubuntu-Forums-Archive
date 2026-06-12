---
title: "Laptop as Router with 2 Subnet"
date: 2015-03-27
forum: Networking &amp; Wireless
---

### Post by fman2 on 2015-03-27
Hi , im still new on learning networking/subnetting with ubuntu . and now i tried to setup pc as a router with ubuntu 12.04
and i following the guide from this tutorial : [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

and any other references, but i hardly to found any tutorial that helped me with 2 subnets 1 router setup. 
so here is my setup : 

[IMG]http://i.imgur.com/ejh8rSa.png[/IMG]

1. Router is connected to my Phone with wlan0 interface, and my router has 3 interfaces :
    i. wlan0 (Internet Source)
    ii. eth0 (First subnet)
    iii. eth1 (Second subnet)

2. And i configured all the interfaces at router in /etc/network/interfaces :
    ```
# Set up the local loopback interface
              auto lo
              iface lo inet loopback

              # Set up External Interfaces
              auto wlan0
              iface wlan0 inet static
                      address 192.168.43.16
                      netmask 255.255.255.0
                      gateway 192.168.43.1
                      
              # Set up First Internal Interfaces 
              auto eth0
              iface eth0 inet static
                      address 10.10.0.1
                      network 10.10.0.0
                      netmask 255.255.255.248
                      broadcast 10.10.0.7

              # Set up Second Internal Interfaces
              auto eth1
              iface eth1 inet static
                      address 10.10.1.1
                      network 10.10.1.0
                      netmask 255.255.255.248
                      broadcast 10.10.1.7

```

3. And i enable port forward, iptables to ACCEPT , also i installed firestarter as my firewall.

4. Client 1 configured the IP manually at Network Manager with following details :

    Address : 10.10.0.2
    Netmask : 255.255.255.248
    Gateway : 10.10.0.1
    DNS Servers : 192.168.43.1

5. Client 2 details :
   
    Address : 10.10.1.2
    Netmask : 255.255.255.248
    Gateway : 10.10.1.1
    DNS Servers : 192.168.43.1
   
6. Here the setup picture : 

[IMG]http://i.imgur.com/ExLfQov.png[/IMG]


and the problem here is, only client 1(10.10.0.2)  can received the internet access and can ping to router(10.10.0.1) . While client 2(10.10.1.2) have a problem to ping to router also doesnt have internet access but client 2 can ping to client 1 without any problem. so how do i fix this ?

---

### Post by robsoles on 2015-03-27
Dunno if this will fix it but I'd swear the broadcast address needs at least the last number to be 255.


The problem, tho, is probably in your router configuration, whichever steps you took to set up ETH1 (10.10.1.1) need to be reviewed.

---

### Post by fman2 on 2015-03-27
> **robsoles said:**
> Dunno if this will fix it but I'd swear the broadcast address needs at least the last number to be 255.


The problem, tho, is probably in your router configuration, whichever steps you took to set up ETH1 (10.10.1.1) need to be reviewed.

thx man for reply.

what u mean the broadcast need to be 255? mean all the broadcast on client and router should be assigned 255.255.255.255 ?
yup , theres a problem with router conf but i dont know how to figured it out. :(

---

### Post by robsoles on 2015-03-27
no, I mean they need to be 10.10.0.255 and 10.10.1.255

---

### Post by The Cog on 2015-03-27
That IP config all looks OK to me. Unusual subnet size, but quite correct.
I am surprised that client1 can access the internet - you must have enabled ip_forwarding on the router even though your mail doesn't say so (maybe port forwarding meant ip forwarding)?

Anyway, I suspect, looking at your diagram, that your problem might be the ethernet cabling to client 2. If there is no switch and you just cable two PCs together, you have to use a "crossover" cable because switches and PCs have different pinouts to each other. You can check if the cabling is OK by looking at the **ifconfig **comand output. Look for the word RUNNING, which only shows when the adapter correctly sees signals from the device at the other end of the cable. Or the command **ip link** might show "NO-CARRIER" against eth1, which means the same thing.

Edit:
@robsoles:
They don't have to be x.x.x.255 for the broadcast address. With the unusual netmask that fman2 has chosen, 10.10.0.7 and 10.10.1.7 are the correct broadcast addresses (only 3 bits of the address are the host address on that subnet). Actually, since the broadcast addresss can be calculated from the ip adress and the netmask, you don't normally have to configure the broadcast address at all.

---

### Post by robsoles on 2015-03-27
oh, I really should have realised that, thanks very much for addressing it :)

(no, seriously no pun intended - do prefer to be told if I am posting nonsense as if it isn't, so to speak.)

---

### Post by fman2 on 2015-03-27
> **The Cog said:**
> That IP config all looks OK to me. Unusual subnet size, but quite correct.
I am surprised that client1 can access the internet - you must have enabled ip_forwarding on the router even though your mail doesn't say so (maybe port forwarding meant ip forwarding)?

Anyway, I suspect, looking at your diagram, that your problem might be the ethernet cabling to client 2. If there is no switch and you just cable two PCs together, you have to use a "crossover" cable because switches and PCs have different pinouts to each other. You can check if the cabling is OK by looking at the **ifconfig **comand output. Look for the word RUNNING, which only shows when the adapter correctly sees signals from the device at the other end of the cable. Or the command **ip link** might show "NO-CARRIER" against eth1, which means the same thing.

Edit:
@robsoles:
They don't have to be x.x.x.255 for the broadcast address. With the unusual netmask that fman2 has chosen, 10.10.0.7 and 10.10.1.7 are the correct broadcast addresses (only 3 bits of the address are the host address on that subnet). Actually, since the broadcast addresss can be calculated from the ip adress and the netmask, you don't normally have to configure the broadcast address at all.

hi, and now the situation turnover after i reset all the interfaces and iptables , i started to reconfigured back from started and client 2(10.10.1.2) now can access to internet and ping to router(10.10.1.1) but client 1(10.10.0.2) have problem with internet and cant ping to router , while the client each other can ping without problem client1(10.10.0.2) and client2(10.10.1.2).

1. here is my ifconfig and ip link and sorry my wlan0 ip is not static.

[ATTACH=CONFIG]260923[/ATTACH][ATTACH=CONFIG]260924[/ATTACH]

2. and here is my iptables :

```
allison@allison-HP-430-Notebook-PC:~$ sudo iptables -L -n
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  127.0.0.1            0.0.0.0/0            tcpflags:! 0x17/0x02
ACCEPT     udp  --  127.0.0.1            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            limit: avg 10/sec burst 5
DROP       all  --  0.0.0.0/0            255.255.255.255     
DROP       all  --  0.0.0.0/0            192.168.0.255       
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0            state INVALID
LSI        all  -f  0.0.0.0/0            0.0.0.0/0            limit: avg 10/min burst 5
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0           
INBOUND    all  --  0.0.0.0/0            10.10.1.1           
INBOUND    all  --  0.0.0.0/0            192.168.0.22        
INBOUND    all  --  0.0.0.0/0            10.10.1.7           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Input"

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            limit: avg 10/sec burst 5
TCPMSS     tcp  --  0.0.0.0/0            0.0.0.0/0            tcpflags: 0x06/0x02 TCPMSS clamp to PMTU
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            10.10.1.0/29         state RELATED,ESTABLISHED
ACCEPT     udp  --  0.0.0.0/0            10.10.1.0/29         state RELATED,ESTABLISHED
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Forward"

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.22         127.0.0.1            tcp dpt:53
ACCEPT     udp  --  192.168.0.22         127.0.0.1            udp dpt:53
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0            state INVALID
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Output"

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
LSI        all  --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x02
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x04
LOG        icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
DROP       icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix "Outbound "
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0 
```

---

### Post by robsoles on 2015-03-27
hmmm, clients pinging each other successfully with failure of internet access for one of them points my nose back at the router set up but I'm completely ready to be wrong again :)

Edit: I can't think for sure: should those clients be able to ping each other, are they not meant to be isolated from each other? (is that not the point of the setup?)

---

### Post by fman2 on 2015-03-27
> **robsoles said:**
> hmmm, clients pinging each other successfully with failure of internet access for one of them points my nose back at the router set up but I'm completely ready to be wrong again :)

i think theres only problem with the firewall at router conf , what u think ?
how to allow both port eth0 and eth2 , any ideas?

---

### Post by robsoles on 2015-03-27
any chance you can list your eth0 related firewall rules for us? any eth1 related rules too please.

I have to go to bed but you are in good hands, I am sure.

---

### Post by fman2 on 2015-03-27
> **robsoles said:**
> any chance you can list your eth0 related firewall rules for us? any eth1 related rules too please.

I have to go to bed but you are in good hands, I am sure.

what u mean by rules? i just typed this 

sudo iptables --policy INPUT ACCEPT
sudo iptables --policy OUTPUT ACCEPT
sudo iptables --policy FORWARD ACCEPT

and here is my ip tables : 

```
allison@allison-HP-430-Notebook-PC:~$ sudo iptables -L -v -n --line-numbers
Chain INPUT (policy DROP 94 packets, 8368 bytes)
num   pkts bytes target     prot opt in     out     source               destination         
1        0     0 ACCEPT     tcp  --  *      *       127.0.0.1            0.0.0.0/0            tcpflags:! 0x17/0x02
2     3541  335K ACCEPT     udp  --  *      *       127.0.0.1            0.0.0.0/0           
3       72  6884 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
4       39 14940 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 10/sec burst 5
5        2   666 DROP       all  --  wlan0  *       0.0.0.0/0            255.255.255.255     
6      407 31897 DROP       all  --  *      *       0.0.0.0/0            192.168.0.255       
7        0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
8      101  3636 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
9        0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
10       0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
11      12   480 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
12       0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 10/min burst 5
13   31427   36M INBOUND    all  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           
14       0     0 INBOUND    all  --  eth2   *       0.0.0.0/0            10.10.1.1           
15       0     0 INBOUND    all  --  eth2   *       0.0.0.0/0            192.168.0.22        
16       0     0 INBOUND    all  --  eth2   *       0.0.0.0/0            10.10.1.7           
17      94  8368 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
18      94  8368 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Input"

Chain FORWARD (policy DROP 245 packets, 15770 bytes)
num   pkts bytes target     prot opt in     out     source               destination         
1       57  3564 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 10/sec burst 5
2      631 37500 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x06/0x02 TCPMSS clamp to PMTU
3     3758  352K OUTBOUND   all  --  eth2   *       0.0.0.0/0            0.0.0.0/0           
4     4216 4295K ACCEPT     tcp  --  *      *       0.0.0.0/0            10.10.1.0/29         state RELATED,ESTABLISHED
5      169 23887 ACCEPT     udp  --  *      *       0.0.0.0/0            10.10.1.0/29         state RELATED,ESTABLISHED
6      245 15770 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
7      245 15770 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Forward"

Chain OUTPUT (policy DROP 8 packets, 528 bytes)
num   pkts bytes target     prot opt in     out     source               destination         
1        0     0 ACCEPT     tcp  --  *      *       192.168.0.22         127.0.0.1            tcp dpt:53
2        0     0 ACCEPT     udp  --  *      *       192.168.0.22         127.0.0.1            udp dpt:53
3     3613  341K ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
4        0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
5       32  2199 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
6        0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
7        0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
8        8   320 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
9    25933 4167K OUTBOUND   all  --  *      wlan0   0.0.0.0/0            0.0.0.0/0           
10       9   756 OUTBOUND   all  --  *      eth2    0.0.0.0/0            0.0.0.0/0           
11       8   528 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
12       8   528 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Output"

Chain INBOUND (4 references)
num   pkts bytes target     prot opt in     out     source               destination         
1    29888   36M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
2     1528  208K ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
3       11  6336 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
num   pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
num   pkts bytes target     prot opt in     out     source               destination         
1       11  6336 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
2        0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
3        0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x02
4        0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
5        0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x04
6        0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
7        0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
8       11  6336 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
9       11  6336 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
num   pkts bytes target     prot opt in     out     source               destination         
1        0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
2        0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix "Outbound "
3        0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain OUTBOUND (3 references)
num   pkts bytes target     prot opt in     out     source               destination         
1      109 17568 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
2    26320 4303K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
3        9   684 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
4     3262  198K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


```

---

### Post by The Cog on 2015-03-27
Try without the firewalls, to see if it's a firewall issue. 
If it is a firewall issue, please post the outout of ```
sudo iptables-save -c
```

---

### Post by SeijiSensei on 2015-03-27
Do you have IP masquerading enabled on the router?  If you open a browser on the router, can you navigate to web sites?

If not, you probably need to add this rule to the router's iptables configuration:
```
/sbin/iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```
That tells the router to rewrite the source address of outbound packets with the address of the interface that points to the upstream gateway.  If that doesn't fix it, we'll have to look more deeply into the problem.

---

### Post by fman2 on 2015-03-28
> **The Cog said:**
> Try without the firewalls, to see if it's a firewall issue. 
If it is a firewall issue, please post the outout of ```
sudo iptables-save -c
```

orait i'll try to disable firewall. 

> **SeijiSensei said:**
> Do you have IP masquerading enabled on the router?  If you open a browser on the router, can you navigate to web sites?

If not, you probably need to add this rule to the router's iptables configuration:
```
/sbin/iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```
That tells the router to rewrite the source address of outbound packets with the address of the interface that points to the upstream gateway.  If that doesn't fix it, we'll have to look more deeply into the problem.

yup i already enabled that on router, and yes i can browse anything on router pc without problem.
here is my firewall rules /etc/iptables.up.rules  :

```
# Generated by iptables-save v1.4.12 on Fri Mar 27 23:14:12 2015*nat
:PREROUTING ACCEPT [52:5929]
:INPUT ACCEPT [1:60]
:OUTPUT ACCEPT [37:2326]
:POSTROUTING ACCEPT [19:1111]
-A POSTROUTING -o wlan0 -j MASQUERADE
COMMIT
# Completed on Fri Mar 27 23:14:12 2015
# Generated by iptables-save v1.4.12 on Fri Mar 27 23:14:12 2015
*mangle
:PREROUTING ACCEPT [1841:340361]
:INPUT ACCEPT [1801:337290]
:FORWARD ACCEPT [37:2951]
:OUTPUT ACCEPT [1768:331412]
:POSTROUTING ACCEPT [1785:333135]
COMMIT
# Completed on Fri Mar 27 23:14:12 2015
# Generated by iptables-save v1.4.12 on Fri Mar 27 23:14:12 2015
*filter
:INPUT DROP [0:0]
:FORWARD DROP [7:455]
:OUTPUT DROP [5:372]
:INBOUND - [0:0]
:LOG_FILTER - [0:0]
:LSI - [0:0]
:LSO - [0:0]
:OUTBOUND - [0:0]
-A INPUT -s 127.0.0.1/32 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT
-A INPUT -s 127.0.0.1/32 -p udp -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p icmp -m limit --limit 10/sec -j ACCEPT
-A INPUT -d 255.255.255.255/32 -i wlan0 -j DROP
-A INPUT -d 192.168.0.255/32 -j DROP
-A INPUT -s 224.0.0.0/8 -j DROP
-A INPUT -d 224.0.0.0/8 -j DROP
-A INPUT -s 255.255.255.255/32 -j DROP
-A INPUT -d 0.0.0.0/32 -j DROP
-A INPUT -m state --state INVALID -j DROP
-A INPUT -f -m limit --limit 10/min -j LSI
-A INPUT -i wlan0 -j INBOUND
-A INPUT -d 10.10.1.1/32 -i eth2 -j INBOUND
-A INPUT -d 192.168.0.22/32 -i eth2 -j INBOUND
-A INPUT -d 10.10.1.7/32 -i eth2 -j INBOUND
-A INPUT -j LOG_FILTER
-A INPUT -j LOG --log-prefix "Unknown Input" --log-level 6
-A FORWARD -p icmp -m limit --limit 10/sec -j ACCEPT
-A FORWARD -p tcp -m tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
-A FORWARD -i eth2 -j OUTBOUND
-A FORWARD -d 10.10.1.0/29 -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -d 10.10.1.0/29 -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -j LOG_FILTER
-A FORWARD -j LOG --log-prefix "Unknown Forward" --log-level 6
-A OUTPUT -s 192.168.0.22/32 -d 127.0.0.1/32 -p tcp -m tcp --dport 53 -j ACCEPT
-A OUTPUT -s 192.168.0.22/32 -d 127.0.0.1/32 -p udp -m udp --dport 53 -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -s 224.0.0.0/8 -j DROP
-A OUTPUT -d 224.0.0.0/8 -j DROP
-A OUTPUT -s 255.255.255.255/32 -j DROP
-A OUTPUT -d 0.0.0.0/32 -j DROP
-A OUTPUT -m state --state INVALID -j DROP
-A OUTPUT -o wlan0 -j OUTBOUND
-A OUTPUT -o eth2 -j OUTBOUND
-A OUTPUT -j LOG_FILTER
-A OUTPUT -j LOG --log-prefix "Unknown Output" --log-level 6
-A INBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INBOUND -j LSI
-A LSI -j LOG_FILTER
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j DROP
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -j DROP
-A LSI -p icmp -m icmp --icmp-type 8 -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6
-A LSI -p icmp -m icmp --icmp-type 8 -j DROP
-A LSI -m limit --limit 5/sec -j LOG --log-prefix "Inbound " --log-level 6
-A LSI -j DROP
-A LSO -j LOG_FILTER
-A LSO -m limit --limit 5/sec -j LOG --log-prefix "Outbound " --log-level 6
-A LSO -j REJECT --reject-with icmp-port-unreachable
-A OUTBOUND -p icmp -j ACCEPT
-A OUTBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTBOUND -j ACCEPT
COMMIT
# Completed on Fri Mar 27 23:14:12 2015
```

---

### Post by fman2 on 2015-03-28
woot woot , finally evertyhing is working, the step i took: 

1. Flush the firewall rules
2. Reset interfaces and reconfigure back
3. Install webmin and configure firewall with this rules only :
    -A POSTROUTING -o wlan0 -j MASQUERADE

and voila. all client can connect to internet and ping to each other/router with fine. thanks all for help. now time for installing proxy server on eth1 and make dmz for eth1 , any ideas are incoming bcause i still learning to create simple network design.

---

