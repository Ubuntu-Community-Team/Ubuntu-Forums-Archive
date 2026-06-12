---
title: "Why is the port not forwarding?"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by stealth17 on 2007-08-13
I have a box setup as a router with Ubuntu and I'm using IPtables for NAT and firewall. I'm trying to forward port 6464 and 21 to ip address 192.168.1.103 which is on eth0. For some reason it won't forward the port(s)...

Here is the output of iptables -L
```
stealth17@stealth17-server:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  dns-cac-lb-01.ohiordc.rr.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns-cac-lb-01.ohiordc.rr.com  anywhere            
ACCEPT     tcp  --  dns-cac-lb-02.ohiordc.rr.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns-cac-lb-02.ohiordc.rr.com  anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
INBOUND    0    --  anywhere             192.168.1.1         
INBOUND    0    --  anywhere             cpe-66-61-40-229.neo.res.rr.com 
INBOUND    0    --  anywhere             192.168.1.255       
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
ACCEPT     tcp  --  anywhere             stealth17-desktop   tcp dpt:12197 
ACCEPT     udp  --  anywhere             stealth17-desktop   udp dpt:12197 
ACCEPT     tcp  --  anywhere             stealth17-desktop   tcp dpt:6464 
ACCEPT     udp  --  anywhere             stealth17-desktop   udp dpt:6464 
ACCEPT     tcp  --  anywhere             stealth17-desktop   tcp dpt:ftp 
ACCEPT     udp  --  anywhere             stealth17-desktop   udp dpt:fsp 
OUTBOUND   0    --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             192.168.1.0/24      state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             192.168.1.0/24      state RELATED,ESTABLISHED 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  cpe-66-61-40-229.neo.res.rr.com  dns-cac-lb-01.ohiordc.rr.com tcp dpt:domain 
ACCEPT     udp  --  cpe-66-61-40-229.neo.res.rr.com  dns-cac-lb-01.ohiordc.rr.com udp dpt:domain 
ACCEPT     tcp  --  cpe-66-61-40-229.neo.res.rr.com  dns-cac-lb-02.ohiordc.rr.com tcp dpt:domain 
ACCEPT     udp  --  cpe-66-61-40-229.neo.res.rr.com  dns-cac-lb-02.ohiordc.rr.com udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  stealth17-desktop    anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpt:domain 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpt:domain 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpt:netbios-ns 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpt:netbios-ns 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpt:netbios-dgm 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpt:netbios-dgm 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webmin 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5900 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            

```Have I made a mistake somewhere?

---

### Post by noob12 on 2007-08-13
You need both a prerouting rule in the nat table and a rule on the forward chain in the default (filter) table.  You haven't shown us the nat table.

Google "iptables port forwarding" and you'll see examples.

---

### Post by stealth17 on 2007-08-13
Opps, here is the NAT table:

> Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       tcp  --  anywhere             anywhere            tcp dpt:12197 to:192.168.1.103:12197 
DNAT       udp  --  anywhere             anywhere            udp dpt:12197 to:192.168.1.103:12197 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:ftp to:192.168.1.103:21 
DNAT       udp  --  anywhere             anywhere            udp dpt:fsp to:192.168.1.103:21 
DNAT       udp  --  anywhere             anywhere            udp dpt:6464 to:192.168.1.103:6464 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:6464 to:192.168.1.103:6464 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

It will forward the ports if you are on a WAN ip, but I cannot get to it from a LAN ip :-k

---

### Post by noob12 on 2007-08-13
> 
It will forward the ports if you are on a WAN ip, but I cannot get to it from a LAN ip


This last statement threw me for a loop.  Isn't 192.168.1.103:6464 the side on your LAN?  So you are trying to go from the inner interface to the public interface and back?  Is this because of the hostname resolving to the outer interface?

Haven't tried dealing with that in this way before.  Better dealing with it on the inbound side directly or in host resolution on the internal net (resolve the name to the internal interface).

---

### Post by stealth17 on 2007-08-13
> **noob12 said:**
> This last statement threw me for a loop.  Isn't 192.168.1.103:6464 the side on your LAN?  So you are trying to go from the inner interface to the public interface and back?  Is this because of the hostname resolving to the outer interface?

Haven't tried dealing with that in this way before.  Better dealing with it on the inbound side directly or in host resolution on the internal net (resolve the name to the internal interface).

Yeah. It's apache which is listening on 6464. So if I goto [http://192.168.1.103:6464](http://192.168.1.103:6464) on my computer (which is on the LAN side) it works. But if I goto [http://my.wan.ip:6464](http://my.wan.ip:6464) on my computer it sits for a while and then gives 404. But if I use a proxy so I'm coming from the WAN side, it works perfectly.

---

### Post by noob12 on 2007-08-13
> 
computer it sits for a while and then gives 404


HTTP 404?  or the browser times out connecting?  If you're getting a 404, that means the request is getting to the Apache server, which suggests a different kind of issue in the configuration of that server.

---

### Post by stealth17 on 2007-08-13
> **noob12 said:**
> HTTP 404?  or the browser times out connecting?  If you're getting a 404, that means the request is getting to the Apache server, which suggests a different kind of issue in the configuration of that server.

browser times out, sorry

---

### Post by noob12 on 2007-08-13
> 
Yeah. It's apache which is listening on 6464. So if I goto [http://192.168.1.103:6464](http://192.168.1.103:6464) on my computer (which is on the LAN side) it works. But if I goto [http://my.wan.ip:6464](http://my.wan.ip:6464) on my computer it sits for a while and then gives 404. But if I use a proxy so I'm coming from the WAN side, it works perfectly.


Basically this sounds like the port forwarding is working, but you want a rule that keeps inbound traffic received on the 192.168.1.103 interface and destined for your.wan.ip:6464 from traversing all of the forwarding, nat, and masquerading and just go to 192.168.1.103:6464.

I am not near a box where I can test out my own suggestion right now, but you might try just adding a rule to the POSTROUTING chain that says if the incoming interface is the 192.168.1.103 interface and (after the PREROUTING) where the destination is 192.168.1.103:6464 to jump off with an ACCEPT before reaching your MASQUERADE rule.

---

### Post by stealth17 on 2007-08-13
> **noob12 said:**
> Basically this sounds like the port forwarding is working, but you want a rule that keeps inbound traffic received on the 192.168.1.103 interface and destined for your.wan.ip:6464 from traversing all of the forwarding, nat, and masquerading and just go to 192.168.1.103:6464.

I am not near a box where I can test out my own suggestion right now, but you might try just adding a rule to the POSTROUTING chain that says if the incoming interface is the 192.168.1.103 interface and (after the PREROUTING) where the destination is 192.168.1.103:6464 to jump off with an ACCEPT before reaching your MASQUERADE rule.

ahh I got it working. Had to write a snat rule :)

```
sudo iptables -t nat -A POSTROUTING -p tcp --dst 192.168.1.103 --dport 6464 -s 192.168.1.1/255.255.255.0 -j SNAT --to-source 192.168.1.1
```

thanks for the help :)

---

