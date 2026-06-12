---
title: "Problem with iptables"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by IdealVithVodka on 2007-02-07
Hi there,


I'v started using linux some time ago. I'm managed to set up a wifi network based on 3 computers 1 : man server (old laptop) with 2 pcmcia cards (one is a modem and the second one is the wifi card). The remaining 2 are the clients. I have my iptables firewall scripts here :

#!/bin/sh

iptables -F
iptables -X
iptables -t nat -X
iptables -t nat -F
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

echo "1" > /proc/sys/net/ipv4/ip_forward

iptables -A INPUT -j ACCEPT -m state --state ESTABLISHED,RELATED
iptables -A FORWARD -j ACCEPT -m state --state ESTABLISHED,RELATED

iptables -t nat -A POSTROUTING -s 192.168.0.2 -d 0/0 -j MASQUERADE
iptables -A INPUT -s 192.168.0.2 -m mac --mac-source 00:0E:21:B3:B0:50 -j ACCEPT
iptables -A FORWARD -m mac --mac-source 00:0E:21:B3:B0:50 -j ACCEPT


I know this is a really simple firewall (maybe it shouldn't be even called that way) but it works. Ohhh... the 192.168.0.2 is the ip address of the client (written that just in case) The problem is when I want to set up any restrictions like for example :
I would like 192.168.0.2  to have access only to WWW. I have to unlock port 80 so I delete this line : 
iptables -A INPUT -s 192.168.0.2 -m mac --mac-source 00:0E:21:B3:B0:50 -j ACCEPT

and replace it with something like this :

iptables -A INPUT -s 192.168.0.2 -p tcp --destination-port 80 -m mac --mac-source 00:0E:21:B3:B0:50 -j ACCEPT


and it still passes all the protocols (MSN, yahoo etc etc) ;(  Maybe I doing something wrong (well for sure).

I would be greatfull for your help.


--regards
IdealVithVodka

---

### Post by koenn on 2007-02-07
It could be that the protocols you meantion are capable of using port 80  (+the RELATED traffic on your FORWARD chain) if that's the only available option (Skype does that, don't know about MSN etc). 

Also, you don know you have to** run** the script for changes to be effective, don't you ?

However, I'm not sure I actually understand your script - I'd expect the 'allow port 80" rule on the FORWARD chain, not INPUT - except if you use  a proxy. This firewall is implemented on the laptop, right ?

---

### Post by TheWizzard on 2007-02-07
you can use gui iptable-editors like firestarter!

---

### Post by IdealVithVodka on 2007-02-07
First off all - thank you for a reply

> **koenn said:**
> It could be that the protocols you meantion are capable of using port 80  (+the RELATED traffic on your FORWARD chain) if that's the only available option (Skype does that, don't know about MSN etc). 

Hmmm... So any idea how to make a better firewall ? Any good ready to use (and learn) scripts ? Maybe you have your own idea/solution.

> **koenn said:**
> 
Also, you don know you have to** run** the script for changes to be effective, don't you ?


I know , I erase all the rules each time I want to make changes.



> **koenn said:**
> 
However, I'm not sure I actually understand your script - I'd expect the 'allow port 80" rule on the FORWARD chain, not INPUT - except if you use  a proxy. This firewall is implemented on the laptop, right ?

Ohhh... so the thing should be placed on the FORWARD... Hmmm... But I do forward :

iptables -A FORWARD -m mac --mac-source 00:0E:21:B3:B0:50 -j ACCEPT

and I know its not the port forwarded. And yes its on an old laptop that is my wifi server and ISP :) its a 133 Mhz 32 MB ram and 2 GB hdd - so a good use for old hardware.


--regards
IdealVithVodka

---

### Post by koenn on 2007-02-07
> So any idea how to make a better firewall
if you mean a firewall that blocks IM's ? If they indeed use port 80 or encapsulate in http, iptables is, AFAIK, not able to block them. Using port 80 is the workaround some apps (such as skype, maybe IM's too) use to make things 'just work' even if the user happens yo be behind a firewall, proxy server, etc.port 80 / http is usually allowed.

One thing  you can do is find out the IP addresses of the MSN / Yahoo / etc servers and block those addresses (or even ranges)  as "destination". It's not 100% waterproof : these servers sometimes change address, new servers are added that you don't block untill you find out, etc. 

```
Ohhh... so the thing should be placed on the FORWARD... Hmmm... But I do forward :
```
To avoid misonderstanding : this is not about port forwarding. 
iptables uses 3 CHAINS, each with a separate rule set.

INPUT is for connections TO the router/fw itself. eg if youu want to do remote maintenance from another machine. What counts is *where* the connection is initiated. So if the router sends you back a web page/shell/remote desktop in reply to a connectioon initiated from an other PC, in'ts still governed by the INPUT rules (under "ESTABLISHED and/or RELATED"

OUTPUT is for connections initiated from the router (laptop) itself, like when you let the laptop ping a computer to check connectivity. The replies to that ping (coming from that outer computer) are "ESTABLISHED" or "RELATED" to the ping and are still governed by OUTPUT rules, even though the come towards the laptop. 

FORWARD is for traffic passing through the router, i.e. it does not have the laptop/router's IP address as source or destination address. So when you route and filter traffic from other PC's through the router/laptop to the internet (or in fact, any other network), the rules of the FORWARD chain apply. 

I never used MAC addresses in iptables (I use ip addresses and sometimes interface names like eth0, eth1, ...) but I gather that
iptables -A FORWARD -m mac --mac-source 00:0E:21:B3:B0:50 -j ACCEPT
means : if it's coming from MAC address 00:0E:... , allow it to pass through to somewhere else. 
So you're not blocking anything here - as long as it's coming from the PC with that MAC address. Everything else (passing through) will be blocked by the default policy (FORWARD -> DROP)

---

### Post by IdealVithVodka on 2007-02-08
> **koenn said:**
> if you mean a firewall that blocks IM's ? If they indeed use port 80 or encapsulate in http, iptables is, AFAIK, not able to block them. Using port 80 is the workaround some apps (such as skype, maybe IM's too) use to make things 'just work' even if the user happens yo be behind a firewall, proxy server, etc.port 80 / http is usually allowed.


Well, I gave the port 80 example becouse I tried to block myself (testing & learning how to use iptables). My reall goal is to have just few ports open on my network : 25,80,443,8074
The rest I would like to keep closed for the world.

> **koenn said:**
> 
One thing  you can do is find out the IP addresses of the MSN / Yahoo / etc servers and block those addresses (or even ranges)  as "destination". It's not 100% waterproof : these servers sometimes change address, new servers are added that you don't block untill you find out, etc. 


In fact MSN was just an example IM, instead of msn I wanted to block Gadu-Gadu (a polish IM). And I think I have a good solution. According to the protocol specification to connect to the GG network you need first to connect to they're server : appmsg.gadu-gadu.pl 9port 80) So if I block that IP it should do. Also I can block all of the servers that are used by that IM - only 12.



> **koenn said:**
> 
To avoid misonderstanding : this is not about port forwarding. 
iptables uses 3 CHAINS, each with a separate rule set.

INPUT is for connections TO the router/fw itself. eg if youu want to do remote maintenance from another machine. What counts is *where* the connection is initiated. So if the router sends you back a web page/shell/remote desktop in reply to a connectioon initiated from an other PC, in'ts still governed by the INPUT rules (under "ESTABLISHED and/or RELATED"

OUTPUT is for connections initiated from the router (laptop) itself, like when you let the laptop ping a computer to check connectivity. The replies to that ping (coming from that outer computer) are "ESTABLISHED" or "RELATED" to the ping and are still governed by OUTPUT rules, even though the come towards the laptop. 

FORWARD is for traffic passing through the router, i.e. it does not have the laptop/router's IP address as source or destination address. So when you route and filter traffic from other PC's through the router/laptop to the internet (or in fact, any other network), the rules of the FORWARD chain apply. 



Thank you for clearing those things up. I had an idea how does that work , but now its clear for me.

> **koenn said:**
> 
I never used MAC addresses in iptables (I use ip addresses and sometimes interface names like eth0, eth1, ...) but I gather that
iptables -A FORWARD -m mac --mac-source 00:0E:21:B3:B0:50 -j ACCEPT
means : if it's coming from MAC address 00:0E:... , allow it to pass through to somewhere else. 


Yes, I know it passes everything with that mac. But atm I haven't configured the WPA or other encryption method to protect my little student made network :)
Will something like this help more :

iptables -A FORWARD -s 192.168.0.2 -m mac --mac-source 00:0E:21:B3:B0:50 -j ACCEPT

so if not - then what kind of instruction set should I use to allow port 80 for my 2 connected PC ? Maybe something like this :

iptables -A FORWARD -p tcp --destination-port 80 -m mac --mac-source 00:0E:21:B3:B0:50 -j ACCEPT

This above should work as my FORWARD politics is DROP.  According to the thing above it shoud (it should!!) forward everything on TCP on port 80 that comes from a mac address of 00:0E:21:B3:B0:50. Is it correct ? Or I'm missing something ?


Thank you in advantage


With Kind Regards
IdealVithVodka

---

### Post by IdealVithVodka on 2007-02-08
> **TheWizzard said:**
> you can use gui iptable-editors like firestarter!

Thanks for the advice, but to be honest I would like to learn how to use iptables from command line. I would like to be a NE in the future, administrating servers etc etc I would like to learn everything from the basics :)

With Kind Regards
IdealVithVodka

---

### Post by mips on 2007-02-08
To simplify iptables I would suggest you use an application called Firewall Builder as it generates the IPtables rule sets via a nice GUI.
[http://www.fwbuilder.org/](http://www.fwbuilder.org/)

-

---

### Post by TheWizzard on 2007-02-09
> **IdealVithVodka said:**
> Thanks for the advice, but to be honest I would like to learn how to use iptables from command line. I would like to be a NE in the future, administrating servers etc etc I would like to learn everything from the basics :)

With Kind Regards
IdealVithVodka

ok, good luck :KS

---

### Post by IdealVithVodka on 2007-02-09
Hi guys one more time,

With a help of my friend I have managed to do the thing I needed.

For the INPUT chain I use the following(remember my input and :
 forward politics is DROP)

iptables -A INPUT -p tcp --sport 80 -d 192.168.0.0/30 -j ACCEPT
iptables -A INPUT -p tcp --sport 443 -d 192.168.0.0/30 -j ACCEPT
iptables -A INPUT -p udp --sport 53 -d 192.168.0.0/30 -j ACCEPT


I have just 2 pc in my small network so /30 should do (2 bits = 4 cmb)
instead of my old FORWARD rule I have a diferent one now :)

iptables -A FORWARD -p tcp --sport 80 -d 192.168.0.2 -j ACCEPT
iptables -A FORWARD -p tcp --dport 80 -s 192.168.0.2 -j ACCEPT
iptables -A FORWARD -p tcp --sport 443 -d 192.168.0.2 -j ACCEPT
iptables -A FORWARD -p tcp --dport 443 -s 192.168.0.2 -j ACCEPT
iptables -A FORWARD -p udp --sport 53 -d 192.168.0.2 -j ACCEPT
iptables -A FORWARD -p udp --dport 53 -s 192.168.0.2 -j ACCEPT

For me it works as I'm not able to start my Yahoo MSN when using this. But my webpages work correctly :) I think that this could also be mixed with mac check -m mac --mac-source 00:E1....  I don't know if the thing that I have now is the best solution you can think off. I try to find out a diferent one.

---

