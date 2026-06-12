---
title: "firewall problem"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by carl on 2006-12-09
Hey

I have just installed the 6.10 server version and made a firewall. It looks like this


iptables -A INPUT -i eth0 -s 10.0.0.2 -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A INPUT -i eth0 -s 10.0.0.3 -p tcp -m tcp --dport 22 -j ACCEPT

iptables -A INPUT -i eth0 -s 10.0.0.2 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A INPUT -i eth0 -s 10.0.0.3 -p tcp -m tcp --dport 80 -j ACCEPT

iptables -A INPUT -i eth0 -s 10.0.0.2 -p tcp -m tcp --dport 443 -j ACCEPT
iptables -A INPUT -i eth0 -s 10.0.0.3 -p tcp -m tcp --dport 443 -j ACCEPT

iptables -A INPUT -i eth0 -s 10.0.0.2 -p tcp -m tcp --dport 5432 -j ACCEPT
iptables -A INPUT -i eth0 -s 10.0.0.3 -p tcp -m tcp --dport 5432 -j ACCEPT

iptables -A INPUT -j DROP

iptables -A INPUT -i lo -j ACCEPT

I have to stop firewall if I want to install a package from the ubuntu archives

At the same time I have to say yes if I want to collect the package without verification, how to I combine a iptabels rule with the firewall so that I can get rid of this problem

Carl

---

### Post by handy on 2006-12-12
Perhaps this can help you:

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by carl on 2006-12-13
I tryed as it is mention in the HOWTO
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

But still the same problem:confused: 

Carl

---

### Post by koenn on 2006-12-13
the 2nd set of rules only applies to ftp. If your access the repositories with http, these rules will block them. 

in your first set of rules, you have rules for http
```
iptables -A INPUT -i eth0 -s 10.0.0.2 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A INPUT -i eth0 -s 10.0.0.3 -p tcp -m tcp --dport 80 -j ACCEPT
```
but they allow **incoming** connections coming from 10.0.0.2  to (any address), tcp port 80. 
That should be OUTPUT (from your machine to port 80 on a ubuntu mirror)
+ accept related, established INPUT from any server, port 80 to your computer. I think. Maybe.

---

### Post by handy on 2006-12-14
See if Frodon, ( the moderator that wrote the how-to ) in his associated thread, or someone else there can help you:

[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)

---

