---
title: "[SOLVED] How can I block or redirect SSL for certain users?"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by KIAaze on 2008-10-06
I've managed to filter https sites using squid, but I currently have to configure browsers manually to use the proxy instead of a direct connection.


My attempts at blocking or redirecting all SSL connections not coming from the proxy have failed so far.
I'm using firehol.

This works to redirect http traffic to the proxy:
```
iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 80 -j REDIRECT --to-port 3128

```
This does NOT work for https traffic:
```
iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 443 -j REDIRECT --to-port 3128

```
How can I block or redirect SSL for all user IDs, except proxy (user under which squid runs)?

---

### Post by KIAaze on 2008-10-08
Solved.
I thought I tried this already, but I don't understand why it works now (before, it just seemed to drop all SSL connections, even the ones going through the proxy). :confused:

Anyway, here's the cleaned up firehol.conf file that currently works for me:
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

#Log SSL traffic for debugging. (use "dmesg" to see the logs) (replace "foobar" with some username other than yours to log everything)
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 443 -m owner ! --uid-owner foobar -j LOG --log-prefix "[PORT 443]" --log-uid --log-tcp-sequence --log-tcp-options --log-ip-options
iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner foobar --dport 443 -j LOG --log-prefix "[NAT PORT 443]" --log-uid --log-tcp-sequence --log-tcp-options --log-ip-options

#drop all SSL traffic not going through the proxy
iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 443 -j DROP
#redirect all http traffic not going through the proxy
iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 80 -j REDIRECT --to-port 8080

#additional stuff to have a secure firewall
interface any world
policy drop
protection strong
client all accept
server cups accept

```

---

