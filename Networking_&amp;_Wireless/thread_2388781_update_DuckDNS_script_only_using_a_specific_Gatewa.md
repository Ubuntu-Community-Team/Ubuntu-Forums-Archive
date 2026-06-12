---
title: "update DuckDNS script only using a specific Gateway, in a multi gateway LAN setup"
date: 2018-04-07
forum: Networking &amp; Wireless
---

### Post by wowiesy2 on 2018-04-07
I use duckdns for my dynamic dns. 


Automatically updating the ip address with my duckdns domains works okay (in an Ubuntu server machine, I used a cron script). I managed to make this work on a network with a lone Gateway to the internet.  


I used the instruction from duckdns website, using this template script: 
```

echo url="https://www.duckdns.org/update?domains=jfincr&token={my_token}&ip=" | curl -k -o ~/scripts/duckdns/duck.log -K -




```

How do I make duckdns update on a multi gateway setup, but only through a specific gateway?  


In a remote office LAN, the Ubuntu server serves as a LAN DHCP and Gateway, as well as an OpenVPN Server.  


Now this LAN Gateway, is actually connected to 2 different ISPs for redundancy / fail over. (I used to have it setup for Load Balancing as well, but had to disable Load Balancing due to errors that I couldn’t trade when LAN clients connect to the HQ server applications)  


so this machine has the following network setup:


Gateway1 (to ISP1):  192.168.15.1  
Gateway2 (to ISP2):  192.168.2.1


only have dynamic IP from the 2 ISPs, and ISP2 has practically disabled port forwarding in their setup (I think I’ve setup the web console properly in the ISP provided  modem / router, but I am unable to connect).. this leaves me with ISP1, which fortunately, just now recently was able to test port forwarding recently.  So I have to specifically update duckdns, but only through Gateway1. 




IP addresses of this Ubuntu machine:
IP1: 192.168.15.254 (to GW1) interface enp1s0
IP2: 192.168.2.254  (to GW2) interface enp3s0
IP3: 192.168.111.1 ( to LAN) interface enp2s0


my routing table and routing rules are setup like this

default route:
```

kss1x@JFINCRROUTER:~$ ip route show
default via 192.168.2.1 dev enp3s0 
10.8.0.0/24 dev tun1  proto kernel  scope link  src 10.8.0.249 
10.9.0.0/24 dev tun0  proto kernel  scope link  src 10.9.0.1 
169.254.0.0/16 dev enp3s0  scope link  metric 1000 
192.168.2.0/24 dev enp3s0  proto kernel  scope link  src 192.168.2.254 
192.168.15.0/24 dev enp1s0  proto kernel  scope link  src 192.168.15.254 
192.168.100.0/24 via 10.8.0.1 dev tun1 
192.168.111.0/24 dev enp2s0  proto kernel  scope link  src 192.168.111.1 




```


since I use policy routing, here are the routing tables as well as the routing rules: 

```
routing table 1
kss1x@JFINCRROUTER:~$ ip route show table 1
default via 192.168.15.1 dev enp1s0 
10.9.0.0/24 dev enp2s0  scope link 
192.168.15.0/24 dev enp1s0  scope link  src 192.168.15.254 
192.168.111.0/24 dev enp2s0  scope link 


routing table 2
kss1x@JFINCRROUTER:~$ ip route show table 2
default via 192.168.2.1 dev enp3s0 
10.9.0.0/24 dev enp2s0  scope link 
192.168.2.0/24 dev enp3s0  scope link  src 192.168.2.254 
192.168.111.0/24 dev enp2s0  scope link 




rules table
kss1x@JFINCRROUTER:~$ ip rule list
0:	from all lookup local 
1022:	from 192.168.2.254 lookup 2 
1023:	from all iif enp3s0 lookup 2 
1024:	from all fwmark 0x1 lookup 1
1025:	from all fwmark 0x2 lookup 2 
32764:	from 192.168.15.254 lookup 1 
32765:	from all iif enp1s0 lookup 1 
32766:	from all lookup main 
32767:	from all lookup default 



```

iptables

filter: 

```
kss1x@JFINCRROUTER:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere             state NEW udp dpt:1196
ACCEPT     udp  --  anywhere             anywhere             state NEW udp dpt:1196
ACCEPT     udp  --  anywhere             anywhere             state NEW udp dpt:1196
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
SSH_ROUTER  tcp  --  anywhere             anywhere             tcp dpt:2222
DROP       all  --  anywhere             anywhere            


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


Chain SSH_ROUTER (1 references)
target     prot opt source               destination         
ACCEPT     all  --  ww.xx.yy.zz        anywhere            
ACCEPT     all  --  10.9.0.0             anywhere            
ACCEPT     all  --  10.8.0.0             anywhere            
ACCEPT     all  --  10.6.0.0             anywhere            
ACCEPT     all  --  10.6.1.0             anywhere            
ACCEPT     all  --  192.168.111.0/24     anywhere            
DROP       all  --  anywhere             anywhere  



```

nat

```
kss1x@JFINCRROUTER:~$ sudo iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
SNAT       all  --  192.168.111.0/24     anywhere             to:192.168.15.254
SNAT       all  --  192.168.111.0/24     anywhere             to:192.168.2.254
SNAT       all  --  192.168.111.0/24     anywhere             to:192.168.15.254
SNAT       all  --  192.168.111.0/24     anywhere             to:192.168.2.254
SNAT       all  --  10.9.0.0/24          anywhere             to:192.168.15.254
SNAT       all  --  10.9.0.0/24          anywhere             to:192.168.2.254
SNAT       all  --  192.168.111.0/24     anywhere             to:192.168.15.254
SNAT       all  --  192.168.111.0/24     anywhere             to:192.168.2.254
SNAT       all  --  10.9.0.0/24          anywhere             to:192.168.15.254
SNAT       all  --  10.9.0.0/24          anywhere             to:192.168.2.254



```

mangle

```
kss1x@JFINCRROUTER:~$ sudo iptables -L -t mangle
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
CONNMARK   all  --  anywhere             anywhere             CONNMARK restore
ACCEPT     all  --  anywhere             anywhere             mark match 0x1
MARK       all  --  anywhere             anywhere             state NEW mark match 0x0 MARK set 0x1
ACCEPT     all  --  anywhere             anywhere             mark match 0x2
MARK       all  --  anywhere             anywhere             state NEW mark match 0x0 MARK set 0x2
CONNMARK   all  --  anywhere             anywhere             CONNMARK save


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination   



```

---

### Post by TheFu on 2018-04-07
TL;DR

Is there a reason you don't use ddclient?  Does it not handle different interfaces? I don't know that it does, haven't been on a dynamic IP in over a decade.

BTW, the older **route -n** command is easier to read.

---

### Post by wowiesy2 on 2018-04-16
managed to use the --interface option of the curl command.... 

incidentally.. duckdns also uses curl to update...

---

### Post by TheFu on 2018-04-16
If solved, please mark the thread as "SOLVED" using the menu above.
Also, it would be helpful if you posted the final solution for complete clarity.

---

