---
title: "How to discover if there is a firewall active"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by ildella on 2007-11-19
Hi all. 

Recently I have some networking problem. 
Every time I try to receive or send a file via Skype, it says that my connection is relayed. This happens even if person are under my same NAT, person with which I have exchanged files till a few days ago. 
If I try to install a ftp server, I cannot even connect to it through my external IP, it just works using 127.0.0.1.

Now, what could this be? My ISP has a NAT, the network arrives to my linksys WRT54GL access point that give my PC a IP with DHCP. I have the same behavior if I use a fixed IP. 

BTW, router confi did not changed lately, but I checked it: firewall is deactivated and no restrictions seems to be active. 
I did not install a firewall. 

The questio is: how could I found if there is and, if so, who is, the firewall or anything else that is blocking incoming connections? 

I am using Ubuntu Gutsy. 

Thanks.

---

### Post by LRT on 2007-11-19
i don't have much experience with skype, but if you want to see if there are any firewall rules on your machine then check your iptables

```
iptables -L
```

---

### Post by ildella on 2007-11-19
this is the output, from which I can't get any advice...

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by LRT on 2007-11-19
that shows you have no firewall rules enabled, which basically means you have no firewall installed.

> My ISP has a NAT

does this mean your ISP is assigning you a private IP? if this is the case, then you have to check with your ISP to see if they are properly forwarding the port that skype talks on and also check that your router is properly forwarding the port.. also, your router should be configured to the IP address your ISP is assigning you. If they are assigning you IP addressses via DHCP, then your router should be set to receive addresses via DHCP, and you should not manually set your router's IP to a fixed address if this is the case. if they are assigning you a fixed ip address, either private or public, then you should not change this either.

---

### Post by dmizer on 2007-11-20
you'll need to set up port forwarding.

see the skype help regarding that here: [http://www.skype.com/help/faq/technical.html](http://www.skype.com/help/faq/technical.html)
and more specifically:
> In the quest for even better voice quality, it is also advisable to open up incoming TCP and/or UDP to the specific port you see in Skype Options. This port is chosen randomly when you install Skype. In the case of firewalls, this should be easy to arrange. In some routers, however, you cannot configure incoming UDP at all (but you still can configure incoming TCP port forwarding, which you could/should do).

forwarding the tcp port shown in "skype options" will likely fix your problem.  you may also be successful by simply rebooting your modem and router.  you say you are also unable to connect to an ftp server, so if none of the above works for you, i suggest taking it up with your isp.

---

### Post by ildella on 2007-11-20
I will try, I just want to notice that everything worked perfectly till a few days ago, and I did not change my ISP. 

More than this, the relayed transfer happens with peer *inside* the same NAT, so there should not be any problem...

Anyway, I'll try. Thanks for advices.

---

### Post by dmizer on 2007-11-20
try rebooting your router (unplug the power for 30 seconds, and plug it back in).

---

