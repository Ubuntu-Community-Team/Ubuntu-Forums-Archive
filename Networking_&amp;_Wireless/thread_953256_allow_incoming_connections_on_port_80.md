---
title: "allow incoming connections on port 80"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by TreeFinger on 2008-10-20
I am trying to configure iptables to allow incoming connections for my http server but I am not having any success. Here is what I try concerning iptables..

```

First we flush our current rules
# iptables -F
# iptables -t nat -F

Setup default policies to handle unmatched traffic
# iptables -P INPUT ACCEPT
# iptables -P OUTPUT ACCEPT
# iptables -P FORWARD DROP

Copy and paste these examples ...
# export LAN=eth1
# export WAN=eth0

Then we lock our services so they only work from the LAN
# iptables -I INPUT 1 -i ${LAN} -j ACCEPT
# iptables -I INPUT 1 -i lo -j ACCEPT
# iptables -A INPUT -p UDP --dport bootps -i ! ${LAN} -j REJECT
# iptables -A INPUT -p UDP --dport domain -i ! ${LAN} -j REJECT

(Optional) Allow access to our http server from the WAN
# iptables -A INPUT -p TCP --dport 80 -i ${WAN} -j ACCEPT

Drop TCP / UDP packets to privileged ports
# iptables -A INPUT -p TCP -i ! ${LAN} -d 0/0 --dport 0:1023 -j DROP
# iptables -A INPUT -p UDP -i ! ${LAN} -d 0/0 --dport 0:1023 -j DROP

Finally we add the rules for NAT
# iptables -I FORWARD -i ${LAN} -d 192.168.0.0/255.255.0.0 -j DROP
# iptables -A FORWARD -i ${LAN} -s 192.168.0.0/255.255.0.0 -j ACCEPT
# iptables -A FORWARD -i ${WAN} -d 192.168.0.0/255.255.0.0 -j ACCEPT
# iptables -t nat -A POSTROUTING -o ${WAN} -j MASQUERADE


HTTP forwarding to an internal host
iptables -t nat -A PREROUTING -p tcp --dport 80 -i ${WAN} -j DNAT --to-destination 192.168.0.2

```

can anyone offer any advice? I have been trying all day :/

---

