---
title: "Firestarter policies"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by sputnik2012 on 2007-01-20
Hi all.

I've installed firestarter and it's running fine.  I can turn it on in whitelisting (restrictive) mode and all ports are blocked.

I've set the outbound policies to include HTTP DNS and IMAP on their respective ports. thing is I can't see a page unlessI put it's url in the incoming section.  I tried entering 255.255.255.255, makes no difference, what am I doing wrong.

Ps I think I need to edit my kernel, but it's loading up fine at the moment.

---

### Post by JamieC on 2007-01-20
Can you please open a new terminal and post the output of the following command:
```

sudo iptables -L

```

---

### Post by sputnik2012 on 2007-01-20
> Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.0.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.0.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.103        192.168.0.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.0.103        192.168.0.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (1 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
DROP       all  --  anywhere             anywhere            

Chain LSO (1 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  192.168.0.103        anywhere            tcp dpt:domain 
ACCEPT     udp  --  192.168.0.103        anywhere            udp dpt:domain 
ACCEPT     tcp  --  192.168.0.103        anywhere            tcp dpt:www 
ACCEPT     udp  --  192.168.0.103        anywhere            udp dpt:www 
ACCEPT     tcp  --  192.168.0.103        anywhere            tcp dpt:imap2 
ACCEPT     udp  --  192.168.0.103        anywhere            udp dpt:imap2 
LSO        all  --  anywhere             anywhere            


EDIT: I have a feeling I need to compile my kernel under network packet filter to recognisse the HTTP protocol. Would that be right?

Thanks,
       Rob

---

### Post by JamieC on 2007-01-20
Could you post your iptables log (if you've set it up) or otherwise take a screen shot of the blocked connections under the 'Events' tab.

---

### Post by mips on 2007-01-20
Use the app called Firewall Builder to setup you policies.

---

