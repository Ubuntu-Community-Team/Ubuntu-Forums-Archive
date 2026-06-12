---
title: "Vpn server Problem"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by delma on 2008-12-01
GRE: read(fd=6,buffer=8058660,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs


Can anyone help me pls?

i have pppoe conection home with a router wrt54gl with forwading port 1723,49 and 47.
But when i telnet from localhost on port 47 or 49 the result is conection refused
my server ip is 192.168.2.199
my router wrt54gl is 192.168.2.1
my pptpd.conf is 
localip 192.168.2.199
remoteip 192.168.2.234-245

and pptpd-options

  GNU nano 2.0.7                         File: /etc/ppp/pptpd-options

name *
lock
mtu 1450
mru 1450
proxyarp
auth
ipcp-accept-local
ipcp-accept-remote
lcp-echo-failure 3
lcp-echo-interval 5
deflate 0

# Handshake Auth Method
+chap
+mschap-v2

# Data Encryption Methods
mppe required

---

