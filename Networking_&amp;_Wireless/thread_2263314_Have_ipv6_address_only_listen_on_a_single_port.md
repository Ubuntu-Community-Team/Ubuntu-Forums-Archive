---
title: "Have ipv6 address only listen on a single port"
date: 2015-01-31
forum: Networking &amp; Wireless
---

### Post by badarsenewb on 2015-01-31
Hi all, first time poster and still new to linux (but lots of experience networking). I'm running Ubuntu 14 and have set my network to use both ipv4 and ipv6. I'm going to be hosting a couple of different services off of my server and I'd like to be able to have each of the ipv6 addresses I assign to my server only listen to a single port. To help illuminate the situation for those who are wondering why I would do that, I'm going to be (among other things) hosting a minecraft server and a MUD. While these use different ports for listeners, I don't want the ipv6 address I'm going to use for the minecraft server to serve out the MUD service if the traffic comes in on the minecraft address but MUD port, and vice versa. This is mostly a security measure so that if someone sees the ip address for my minecraft server, they won't be able to scan the address and see all of the other ports the server is listening on. I've looked around but come up short on how to do this. Any suggestions?

---

### Post by SeijiSensei on 2015-01-31
Use iptables to permit traffic to that port and block everything else.  I don't use IPv6, so I can't help with the iptables syntax.  On an IPv4 system, you'd have a set of rules like this:
```

/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A INPUT -p tcp -i eth0 --dport 12345 -j ACCEPT
/sbin/iptables -A INPUT -j REJECT

```
This permits all traffic to localhost and TCP connections to port 12345 on eth0.  Everything else is rejected.  The second rule allows the machine to accept packets sent in response to requests it makes.

---

