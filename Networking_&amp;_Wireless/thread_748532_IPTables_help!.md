---
title: "IPTables help!"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by eochs on 2008-04-07
I am trying to do port forwarding and running into some issues...  It works great when I have Port 1309 on my DMZ box forward to Port 1309 on a backend server like this:

iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.0.100
iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 1309 -j DNAT --to 192.168.0.200:1309
iptables -A FORWARD -i eth0 -o eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

nmap shows 1309 is open and I can connect just fine to 192.168.0.100:1309 (and it forwards to .200:1309 as planned)

My real problem is that I also need to change the port number... I need to connect to 192.168.0.100:9001 and have it forward to 192.168.0.200:1309... For that I've tried this:

iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.0.100
iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 9001 -j DNAT --to 192.168.0.200:1309
iptables -A FORWARD -i eth0 -o eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

nmap shows 9001 as closed, and I cannot connect to 192.168.0.100:9001...

Bottom line, works great if forwarding from Port 1 on Server A to Port 1 on Server B, but not at all if forwarding from Port 1 on Server A, to Port 2 on Server B

Any clues?

---

