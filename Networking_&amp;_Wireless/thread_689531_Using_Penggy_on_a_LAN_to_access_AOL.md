---
title: "Using Penggy on a LAN to access AOL"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by switlikbob on 2008-02-06
Ok, first I'm sure you want to know why I would want to use AOL when I already have an internet connection via my LAN connection.  Let's just say that I need AOL to circumvent certain "security measures" put in place here at the office.

So, I have penggy installed and configured.  Here's the output when I start up penggy:
______________________________
Resolving AmericaOnline.aol.com...
Connecting to 64.12.9.61:5190 ...
Loging into provider as 'username_not_shown'
IP address: 172.163.245.7
DNS server: 205.188.146.145
MTU: 1500
Hostname: client-245-7.aol.com
Domain: aol.com
IP tunnel is working.
_______________________________

However, once this tunnel is established, I can't ping any IP address, not on the internet or intranet.  The only address I can ping is my loopback address (127.0.0.1).  Does this mean that the tun0 device is bound to my loopback adapter and not eth0?

---

