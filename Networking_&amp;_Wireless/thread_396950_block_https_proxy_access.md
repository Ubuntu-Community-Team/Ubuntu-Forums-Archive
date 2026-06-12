---
title: "block https proxy access"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2007-03-30
Hi I have big problems in little china town,

I am running a transparent proxy and content filter and all was well however there is one site I just cannot seem to block

even though I followed MrC's advice in blocking the ip of hidebehind.net

what must I do to block hidebehind.net it seems to give alot of problems for many people


any suggestions 


oh please please it's driving me crazy because it basically defeats the purpose of having a content filter :confused:

---

### Post by andytof47 on 2007-04-03
O.K. bump please

The thing is this is my main firewall.....My Ubuntu firewall/AP/Everything

hidebehind.net is certainly blocked in my blacklists, and sure enough typing [www.hidebehind.net](www.hidebehind.net) produces the desired result of blocking the page

however typing [https://hidebehind.net](https://hidebehind.net) lets me go straight through and browse the page.... and call up all the pron one could want (highlighting the problem)

how may I block this - I already have the site blocked by IP and I am at wits end......

I have a development box and quickly checked Clark Connect and it certainly does block the site and any access...

however I do note two things ----- content filter was not on, it was blocked using the firewall in clark connect (iptables I assume), and it was certainly in transparent proxy mode the same as what I am using on my Ubuntu box now ---yet it still managed to block for my network...



please can someone post me some help ------ I think it is going to come down to an alternative to using DansGuardian and more than likely it will be an iptables solution.....


Please someone help


Cheers

---

### Post by josephus on 2007-04-03
I don't completely understand the question, and don't have much experience with firewalls/transparent proxies. but isn't it sufficient to use:

sudo iptables -A OUTPUT -d 69.80.225.122 -j REJECT

---

### Post by andytof47 on 2007-04-03
> iptables -A OUTPUT -d 69.80.225.122 -j REJECT

sadly if it did I would already have implemented it.............


So the question is to recap and clarify....... How can I block access to this site with my firewall?

I have attached a sample of captures from my network if it is helpful

ip's
69.80.225.122
69.80.225.119

here is my iptable -L
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:sip 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:33000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:33000 
DROP       all  --  abel.hidebehind.com  anywhere            
DROP       all  --  hosted.by.alphared.com  anywhere            
DROP       all  --  bp                   anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state NEW 
REJECT     all  --  anywhere             192.168.1.4         reject-with icmp-port-unreachable 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
REJECT     all  --  anywhere             abel.hidebehind.com reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             hosted.by.alphared.com reject-with icmp-port-unreachable 
root@andy1-desktop:/home/mel1# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   tcp  --  anywhere             anywhere            tcp dpt:www redir ports 8080 
REDIRECT   tcp  --  anywhere             anywhere            tcp dpt:www redir ports 8080 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webcache OWNER UID match squid 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www OWNER UID match squid 
REDIRECT   tcp  --  anywhere             anywhere            tcp dpt:www redir ports 8080 

```

yet it still manages to get through:confused: 

help

---

### Post by andytof47 on 2007-04-03
bump.......


please ------- very desperate:confused:

---

