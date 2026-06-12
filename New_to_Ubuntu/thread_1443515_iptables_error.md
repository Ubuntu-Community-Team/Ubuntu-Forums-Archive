---
title: "iptables error"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by savin on 2010-03-31
please help me..
thanks in advance....

chain INPUT (policy DROP)
target     prot opt source         destination         
ACCEPT     tcp  --  anywhere       arl-sandbox         tcp dpt:ssh 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere       arl-sandbox         tcp dpt:1050 
ACCEPT     all  --  anywhere       anywhere            
ACCEPT     all  --  anywhere       anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:http-alt 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere       anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:domain 
ACCEPT     icmp --  anywhere       anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 




Error under following conditions :

target    prot  opt   source                 destination           port

1.ACCEPT  tcp   --    192.168.2.X     arl-sandbox(204.232.200.X)   tcp dpt:1050 

2.#( by removing tis line) 
ACCEPT    tcp   --     anywhere           anywhere            tcp dpt:1050


By Default its
Doing 2. and not doin 1.      eventhough with following rules

1. DROP   tcp  --     192.168.2.X      204.232.200.X         tcp dpt:1050
2. ACCEPT tcp    --      anywhere           anywhere         tcp dpt:1050


if removing  2.     by default its blocking every connection to 1050
though allowing 

ACCEPT  tcp    --     192.168.2.X       204.232.200.X         tcp dpt:1050

---

### Post by gmargo on 2010-03-31
Sorry, but I have no idea what your question is.  And please use CODE tags to wrap your iptables info, so that a fixed width font is used to display it.

---

### Post by JKyleOKC on 2010-03-31
> **savin said:**
> please help me..
thanks in advance....

chain INPUT (policy DROP)
target     prot opt source         destination         
ACCEPT     tcp  --  anywhere       arl-sandbox         tcp dpt:ssh 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere       arl-sandbox         tcp dpt:1050 
ACCEPT     all  --  anywhere       anywhere            
ACCEPT     all  --  anywhere       anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:http-alt 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere       anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:domain 
ACCEPT     icmp --  anywhere       anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


I'm not sure either what your question is, but I do see a problem in this area of your listing:
```
chain INPUT (policy DROP)
target     prot opt source         destination         
ACCEPT     tcp  --  anywhere       arl-sandbox         tcp dpt:ssh 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere       arl-sandbox         tcp dpt:1050 
ACCEPT     all  --  anywhere       anywhere
```
Since iptables processes the rules in order, executes the first one that matches, and then does not process any more, only those first four rules will ever be tested. The fourth one always matches every packet that gets by the first three, and says to accept everything. Thus the "drop" policy never comes into play and nothing gets dropped...

---

