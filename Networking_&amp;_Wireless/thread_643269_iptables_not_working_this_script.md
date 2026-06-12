---
title: "iptables not working this script"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by dapim on 2007-12-17
#open 80 for http
sudo iptables -A INPUT -p tcp -i wlan0 --dport 80 -j ACCEPT

#open 53 for dns
sudo iptables -A INPUT -p udp -i wlan0 --dport 53 -j ACCEPT

#block all
sudoiptables -A INPUT -j DROP

---

### Post by HermanAB on 2007-12-17
The order is important.  'A' adds rules to the end of the list.  'I' inserts rules at the start of the list.  So you are adding rules to the end, but another rule could be dropping the packets earlier.

Cheers,

Herman

---

### Post by samaricsm on 2008-02-08
The INPUT parameter is for protocols your machine will accept.  As written, your script is good if the machine is a DNS Web server.  If it is a user machine and you want to connect to the web, then try:

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
## Browser  80 - normal  443 - https (ssl, tls, etc)
iptables -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
iptables -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
## DNS
iptables -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
## e-mail 25 - SMTP (out)  110 POP3 (in)
iptables -A OUTPUT -p tcp --dport 25 --syn -m state --state NEW -j ACCEPT
iptables -A OUTPUT -p tcp --dport 110 --syn -m state --state NEW -j ACCEPT

---

