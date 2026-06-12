---
title: "[SOLVED] iptables rule not working?"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by xyrer on 2007-09-20
Hi, I'm new to iptables and have a squid server, we have an application that connects  by telnet to our AIX server wich is on another subnet, the point is I don't really know if I should forward the traffic with squid or iptables, I tried iptables but no luck, this is what I typed:

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 23 -j DNAT --to-destination 192.168.1.1:23

I odn't really know what all that means, but it didn't work anyway, all documentation I've seen is hard for newbies, please someone help me.

---

### Post by Paris Heng on 2007-09-21
> **xyrer said:**
> Hi, I'm new to iptables and have a squid server, we have an application that connects  by telnet to our AIX server wich is on another subnet, the point is I don't really know if I should forward the traffic with squid or iptables, I tried iptables but no luck, this is what I typed:

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 23 -j DNAT --to-destination 192.168.1.1:23

I odn't really know what all that means, but it didn't work anyway, all documentation I've seen is hard for newbies, please someone help me.

What do u mean by not working? Can explain? Thanx

---

### Post by xyrer on 2007-09-21
Like I said, the app that must connect to the AIX server have, until now, been forwarded by wingate, in wingate it's called mapping, and the apps does telnet to the 192.168.15.5, and wingate send the telnet to the 192.168.1.1, on port 23.

I'm trying to do the same thing on linux, I have read about people redirecting http communications sent to a linux server, to a http specialized server by doing forward in iptables, I tried doing the same thing but nothing works, here is my iptables rules:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             192.168.1.1         tcp dpt:telnet 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webcache 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             192.168.1.1         tcp dpt:telnet 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 

with those rules applied, i do telnet to the linux server and nothing happens.
I hope I made myself clear, I've been trying to demostrate that Linux server and squid is better than Windows XP and wingate.

Thanks.

---

### Post by xyrer on 2007-09-21
I forgot to mention that eth0 is local ip 192.168.15.36, eth1 is public ip, and eth0:0 is local ip 192.168.1.158

---

### Post by Paris Heng on 2007-09-22
Did you save the iptables once you configure it? It might the problems i think

---

### Post by xyrer on 2007-09-22
After I made allthose rules i did:
sudo iptables-save

still, telnet to 192.168.15.36 doesn't work

---

### Post by Paris Heng on 2007-09-23
Anyway,I hope there will be an expert to assist you.

---

### Post by xyrer on 2007-09-24
I did all this on another machine, I have never touched iptables on this one:

sudo iptables -t nat -A PREROUTING -p tcp --dport 23 -j DNAT --to 192.168.1.1:23
sudo iptables -A INPUT -d 192.168.1.1 -p tcp --dport 23 -j ACCEPT
sudo iptables -A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.1.1 --dport 23 -j ACCEPT
sudo iptables-save
sudo iptables --list

and it shows me this:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             192.168.1.1         tcp dpt:telnet 
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             192.168.1.1         tcp dpt:telnet 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

this one has ip 192.168.15.9 on eth0:0, first machine has it on eth0

from another machine, i do telnet 192.168.15.9, still nothing happens.

I still can't figure out what's the deal about this.

someone please help me.

---

### Post by xyrer on 2007-09-27
ok, I solved it. As I pointed out before, I was trying to forward the telnet traffic to an alias in the same ethernet card, and iptables doesn't accept aliases, I installed another ethernet card and problem solved.

However, I read all kind of documentation and that kind of thing is not written anywhere.(or maybe I skipped it somehow) I hope someone learns from my mistake.

Thanks to everyone.

---

