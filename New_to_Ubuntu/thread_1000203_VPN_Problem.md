---
title: "VPN Problem"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by delma on 2008-12-02
Hello everybody i have a problem with my vpn:
[COLOR="Red"]Dec  2 04:50:02 server pptpd[29816]: GRE: read(fd=6,buffer=8059540,len=8196) from PTY failed: status = -1 error = Input/output
Dec  2 04:50:02 server pptpd[29816]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Dec  2 04:50:02 server pptpd[29816]: CTRL: Reaping child PPP[29817]
[/COLOR]

I mention that i have pppoe conection from my provider of internet, the router linksys wrt54gl is my default server for internet with the ip 192.168.2.1, and i mention that my internal ip of server is 192.168.2.199 

my pptpd.conf look like this:
localip 192.168.2.199
remoteip 192.168.2.234-245

and my pptpd-options:

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


Can someone can help me pls i need it very much.I mention that the protocol GRE is not responding when i telnet from the server, how i open protocol GRE???

Thank you very much!!!

---

