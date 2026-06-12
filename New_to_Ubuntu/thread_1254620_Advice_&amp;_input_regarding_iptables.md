---
title: "Advice &amp; input regarding iptables"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-08-31
Hello, I trying to set up my firewall the hard way using iptables instead of ufw, firestarter and those, I have manadge to create atlest a little with help from this guide [http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661) even if it's more then 3 years old I didn't figure out the script part tho.

I would be grateful if someone more advanced in iptables would take a look at my iptables setup and advice on errors, since they are sure to be there ;) and also tell if the layout is good or totally wrong and will cause major security risk.

There are a few questions in the layout, also can both tcp and udp be specified in a single command or is two needed?

```
#Drop all incoming, outgoing and forwarded connections
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

#loopback allowed, it's needed?
iptables -A OUTPUT -o lo -j ACCEPT

#VPN!
#drop all connections except 10.123.452.36 (can dns be used instead?)
#/*you might wonder why, I using a VPN and don't know how else to make sure 
#that the computer only uses the VPN*/
iptables -A OUTPUT -d ! 10.123.452.36 -j DROP
iptables -A INPUT -s ! 10.123.452.36 -j DROP
#pptp (both incoming & outgoing needed?)
iptables -A OUTPUT -o eth0 -p tcp udp --dport 1723 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp udp --sport 1723 -m state --state NEW,ESTABLISHED -j ACCEPT

#Get Internet working for http, https (outgoing only, does it work?) is udp needed?
iptables -A OUTPUT -o eth0 -p tcp udp -m tcp udp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp udp -m tcp udp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT

#Outgoing FTP, SSH
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp udp -m tcp udp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT

#MSN working (is incoming needed?)
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 1863 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -i etho -p tcp -m tcp --sport 1863 -m state --state NEW,ESTABLISHED -j ACCEPT

#Stream media
iptables -A OUTPUT -o eth0 -p tcp udp -m tcp udp --dport 1755 -m state --state NEW,ESTABLISHED -j ACCEPT

#mail POP3S, SMTP
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 955 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 25 -m state --state NEW,ESTABLISHED -j ACCEPT



```

---

