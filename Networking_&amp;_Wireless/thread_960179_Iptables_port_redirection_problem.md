---
title: "Iptables port redirection problem"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by AussieGuy69 on 2008-10-27
I have a custom built service that id like to be accessible on 10 ports. I'm testing this script, to allow connections to apache on port 8080.

Note im only using apache as a test.

This script works locally (firefox and telnet can go to localhost:8080)
But not remotely from another internet address (elinks over ssh on another ip, can only get to port 80 and not 8080).

This also fails when I modify the script to forward to my own custom service instead, and again works locally fine.

How can I get this to accept remote connections on the extra ports and not just local ones?

#!/bin/bash
/sbin/iptables --flush
/sbin/iptables -t nat --flush
/sbin/iptables -t mangle --flush
/sbin/iptables --policy INPUT ACCEPT
/sbin/iptables --policy OUTPUT ACCEPT
/sbin/iptables --policy FORWARD ACCEPT
/sbin/iptables -t nat --policy PREROUTING ACCEPT
/sbin/iptables -t nat --policy OUTPUT ACCEPT
/sbin/iptables -t nat --policy POSTROUTING ACCEPT
/sbin/iptables -t mangle --policy PREROUTING ACCEPT
/sbin/iptables -t mangle --policy OUTPUT ACCEPT
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT


#apache remote test
iptables -t nat -A OUTPUT -o eth0 -p tcp --dport 8080 -j REDIRECT --to-port 80

#local apache test
iptables -t nat -A OUTPUT -o lo -p tcp --dport 8080 -j REDIRECT --to-port 80

---

