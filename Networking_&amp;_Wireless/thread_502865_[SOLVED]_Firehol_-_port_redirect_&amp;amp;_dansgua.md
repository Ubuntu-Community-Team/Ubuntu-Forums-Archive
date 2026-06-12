---
title: "[SOLVED] Firehol - port redirect &amp;amp; dansguardian"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by ushills on 2007-07-17
I have a problem with Firehol and dansguardian.

This is my current firehol setup

```


#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5

iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

#transparent_squid 8080 "nobody root"

#transparent_squid 8080 "root root"

# Accept all client traffic on any interface
interface any world
policy drop
protection strong
client all accept
server cups accept
#server webcache accept

```

While this works and allows connection out to the internet I have to manually set Firefox to use port 8080 to have dansguardian filter web content.

I understand the command

```
transparent_squid 8080 "root root"
```

should route all http requests through port 8080 all this does in practice is prevent any http access.

Also, when I test the firewall using shields up, [HTML]http://www.grc.com[/HTML] the firewall fails as it has allowed a ping request, although all ports are stealthed.  I thought that all ping requests should be dropped with firehol.

I would also like to be able to bypass the proxy for user name "ian", how is this possible, I would imagine it would be 

```
transparent_squid 8080 "ian root"
```

although this also doesn't work.

---

### Post by ruibernardo on 2007-09-05
I found this thread while searching for firehol. It says [SOLVED], but apparently it isn't, so here are my 2 cents to who find this.

> **ushills said:**
> 
I understand the command

```
transparent_squid 8080 "root root"
```should route all http requests through port 8080 all this does in practice is prevent any http access.


This is because dansguardian is not on the proxy owned by root. That process is the main squid one. Dansguardian proxy is owned (by default) by the proxy user. To confirm this, edit the file /etc/squid/squid.conf and search for "cache_effective_user". It should be "cache_effective_user proxy". Restart the squid service.

What worked for me on firehol was:

```
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "proxy proxy"

```> **ushills said:**
> 
I would also like to be able to bypass the proxy for user name "ian", how is this possible, I would imagine it would be 

```
transparent_squid 8080 "ian root"
```although this also doesn't work.

Never done that, so I can't confirm it. Since it's the iptables -t filter line that drops the browsing, you should add a line before the existing iptables -t filter one allowing the user ian to access the proxy. This would be something like:

```
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner --uid-owner ian -j ACCEPT
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
```And restart firehol.

---

