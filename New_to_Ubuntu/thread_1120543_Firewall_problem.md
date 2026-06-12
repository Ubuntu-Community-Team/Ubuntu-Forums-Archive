---
title: "Firewall problem"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by EgilCPH on 2009-04-09
Hi!

I'm having network problems this morning.
When i boot my Ubunto server, the firewall (well, actually the iptables) have reverted to the highest security setting, causing my server not to be recognized on the LAN.
```
sudo iptables --list
[sudo] password for egil: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
RH-Lokkit-0-50-INPUT  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
RH-Lokkit-0-50-INPUT  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain RH-Lokkit-0-50-INPUT (2 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
REJECT     tcp  --  anywhere             anywhere            tcp dpts:0:1023 flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:nfs flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp dpts:0:1023 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp dpt:nfs reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpts:x11:6009 flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:font-service flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable
```

I then reduce the security level
```
sudo lokkit --medium
```

and the setting is reduced:
```
sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain RH-Lokkit-0-50-INPUT (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  ns3.inet.tele.dk     anywhere            udp spt:domain 
ACCEPT     udp  --  ns3.tele.dk          anywhere            udp spt:domain 
REJECT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp reject-with icmp-port-unreachable
``` 
Now my server is visible on the network and I can mount the shares and use the services.

Quite frankly, I don't understand what is going on here. How can I make shure the settings don't change between boots?

Rgds.
Egil

---

### Post by Michael.Godawski on 2009-04-09
hi EgilCPH, 

perhaps you have to add your iptables rules to the init.d script as described in this guide by frodon:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[/LIST]
It's point 3.3 if you do not want to read all the great info.

---

### Post by EgilCPH on 2009-04-09
Thank you very much Michael.Godawski.

I'll do as directed.
:grin:

---

