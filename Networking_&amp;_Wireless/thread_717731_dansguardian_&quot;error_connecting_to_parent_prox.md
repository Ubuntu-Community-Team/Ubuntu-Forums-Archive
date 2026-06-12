---
title: "dansguardian &quot;error connecting to parent proxy&quot;"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by elbeano on 2008-03-07
I have an Ubuntu LTS 6.06 server providing webserver, firewall (shorewall), content caching (squid) and want to add dansguardian content filtering. Squid is working fine as a transparent proxy. I add dansguardian, but it refuses to start with the error message "error connecting to parent proxy"

Relevant Shorewall rules:

[INDENT]#use squid
REDIRECT        loc     3128    tcp     80[/INDENT]

Dansguardian config:

[INDENT]# commented out UNCONFIGURED...

reportinglevel = 3
filterip = 127.0.0.1
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128
daemonuser = 'squid'
daemongroup = 'squid'[/INDENT]

I try Modify /etc/squid/squid.conf here (formerly 192.168.0.1):

[INDENT]http_port 127.0.0.1:3128[/INDENT]

This results in dansguardian starting, but there is no www access from the local network after this.

What am I missing?

---

### Post by elbeano on 2008-03-07
I've moved beyond this issue, and on to others. I suspect that the dansguardian mailing list would have been a better place to post than here. Thanks for looking....

Basically, there were lines I need to add to squid.conf to make it work:

acl localnet src 192.168.42.0/255.255.255.0
http_access allow localnet
http_access allow localhost
http_access deny all

---

