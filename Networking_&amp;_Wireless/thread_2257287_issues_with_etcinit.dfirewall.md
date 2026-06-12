---
title: "issues with /etc/init.d/firewall"
date: 2014-12-18
forum: Networking &amp; Wireless
---

### Post by pixel2 on 2014-12-18
hey all,

Ive set up my firewall as to be more safe while browsing net. Ive done these steps:

1. Created file called firewall (for now in homedir),
2. Wrote some iptables rules into it,
3. Made it executable and copied to /etc/init.d.
4. Updated rc.d in order for firewall to be started at boot time,
5. Started firewall as a service.

It works as it should but when I restart my box, the internet is gone. I cannot browse any webpage, ping, nothing. I have to stop firewall (service) manually - once I do it, internet is back.
I checked iptable rules all-over again and its all ok with them. I even copied them onto Debian 7.4 (another box) and internet is there (regardless the state (started/stopped)).

Whats wrong that makes my rules fail under Ubuntu?

---

### Post by Lars Noodén on 2014-12-18
Can you post the contents of /etc/init.d/firewall so we can see what it does?

---

### Post by pixel2 on 2014-12-18
> **Lars Noodén said:**
> Can you post the contents of /etc/init.d/firewall so we can see what it does?
sure I can.....
```
#!/bin/bash
#CLEANING OLD FILTERS
iptables -F
iptables -X
iptables -F -t nat
iptables -X -t nat
iptables -F -t filter
iptables -X -t filter
 
# USAGE POLICY
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
iptables -A INPUT -i lo -j ACCEPT
# iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# iptables -A INPUT -p icmp --icmp-type echo-request -j REJECT --reject-with icmp-host-unreachable
 
# SECURE FROM ACK SCANNING
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --tcp-flags SYN,RST,ACK,FIN,URG,PSH ACK -j LOG --log-prefix "ACK scan: "
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --tcp-flags SYN,RST,ACK,FIN,URG,PSH ACK -j DROP
 
# SECURE FROM FIN SCANNING
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --tcp-flags SYN,RST,ACK,FIN,URG,PSH FIN -j LOG --log-prefix "FIN scan: "
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --tcp-flags SYN,RST,ACK,FIN,URG,PSH FIN -j DROP
 
# SECURE FROM XMAS TREE SCAN
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --tcp-flags SYN,RST,ACK,FIN,URG,PSH PSH -j LOG --log-prefix "Xmas scan: "
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --tcp-flags SYN,RST,ACK,FIN,URG,PSH FIN,URG,PSH -j DROP
 
# SECURE FROM NULL SCAN
iptables -A INPUT -m conntrack --ctstate INVALID -p tcp ! --tcp-flags SYN,RST,ACK,FIN,PSH,URG SYN,RST,ACK,FIN,PSH,URG -j LOG --log-prefix "Null scan: "
 
# SECURE FROM DDOS
iptables -A INPUT -m conntrack --ctstate INVALID -p tcp ! --tcp-flags SYN,RST,ACK,FIN,PSH,URG SYN,RST
iptables -N syn-flood
iptables -A INPUT -p tcp --syn -j syn-flood
iptables -A syn-flood -m limit --limit 1/s --limit-burst 4 -j RETURN
iptables -A syn-flood -m limit --limit 1/s --limit-burst 4 -j LOG --log-prefix "SYN-flood: "
iptables -A syn-flood -j DROP
 
# SECURE FROM PING OF DEATH 
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j LOG --log-prefix "Ping: "
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
 
# PING LOCK
iptables -A INPUT -p icmp --icmp-type echo-request -j REJECT --reject-with icmp-host-unreachable
 
# TELNET LOCK
# iptables -A OUTPUT -p tcp --dport telnet -j REJECT
iptables -A INPUT -p tcp --dport telnet -j REJECT
 
# LOGGING INTO /var/log/messages
iptables -N LOGGING
iptables -A INPUT -j LOGGING
iptables -A LOGGING -m limit --limit 2/min -j LOG --log-prefix "IPTables-Dropped: " --log-level 4
iptables -A LOGGING -j DROP
```

---

### Post by kpatz on 2014-12-18
Uncomment this line by removing the # at the beginning:

From:
```

# iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

```

To:
```

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

```

---

### Post by pixel2 on 2014-12-19
@kpatz: many thanks. Is working now :)

---

