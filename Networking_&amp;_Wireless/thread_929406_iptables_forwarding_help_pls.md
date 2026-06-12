---
title: "iptables forwarding help pls"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Shwick2 on 2008-09-25
I successfully set up my home network with ip forwarding and masquerading, internet <<>> ubuntu gateway <<>> local machines.

 Now i'm trying to forward a port from my ubuntu gateway to one of the machines on my lan.

 Specifically I need to forward port 6112 so that I can host warcraft games.  These two rules don't seem to be working.

#set DNAT
iptables -A PREROUTING -t nat -p tcp --dport 6112 -i eth0 -j DNAT --to 192.168.0.100:6112
iptables -A PREROUTING -t nat -p udp --dport 6112 -i eth0 -j DNAT --to 192.168.0.100:6112


 These were some other rules I already had.


#setup MASQUERADING for nat
iptables -A POSTROUTING -t nat -j MASQUERADE

# Setup port forwarding
iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT


 I set up a log after the DNAT and it gets triggered b/c I can see it in syslog, but no one can join my games.
 I also set up a log after MASQUERADE but that one didn't appear in syslog.

 Maybe it has something to do with state in the DNAT rules?  I attached my startup script.  I dunno whats going on.

---

### Post by Shwick2 on 2008-09-25
Stupid Windows SP3 didn't ask me if I wanted to allow War3 through my firewall.  I added it manually and now my windows machine can host through the gateway.  The packets were being forwarded properly all along I was just so focused on the gateway being the problem.  Next time I'll install wireshark.

---

