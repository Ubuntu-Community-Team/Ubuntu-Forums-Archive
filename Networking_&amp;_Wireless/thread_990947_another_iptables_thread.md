---
title: "another iptables thread"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by sveri on 2008-11-23
Hi all,

first of all the situation.
I have a lan with several clients (192.168.15.x)
and one of them is an Exchange Server.

As an Router i am trying to setup ubuntu server.
Which works in some disciplines but not in others.
I got an dhcp and internet routing working 
for the lan clients.

But i cannot access the internal exchange server
from the outside. So what i need is a routing to
port 80, 443 and 25 from the ubuntu server to the
exchange client.

I tried several iptable scripts, but nothing did help.

Here are the relevant parts of the script:
iptables -A FORWARD -p tcp -m multiport --dports 20,21,80 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -m tcp --dport 80 -j DNAT --to      -destination 192.168.15.1:80

iptables -t nat -A PREROUTING -p tcp -m tcp --dport 443 -j DNAT --to-destination 192.168.15.1:443

#iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to-destination 192.168.15.1

#iptables -A FORWARD -i eth1 -m state --state NEW -p tcp -d 192.168.15.1 --dport 80 -j ACCEPT

#iptables -t nat -A POSTROUTING -o eth2 -p tcp --dport 80 -j SNAT --to-source $LAN_IP

As you can see i tried every combination i found on the
internet and it seems to work a bit.
When i try to access my lan with my external ip
it always takes ages until i get the page load error.
I just cannot figure out what is exactly wrong.


Some advice would be great.

I attached the whole script just if somebody
needs it


Thanks in Advance
Sven

---

