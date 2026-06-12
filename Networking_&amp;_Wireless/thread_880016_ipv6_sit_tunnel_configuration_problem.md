---
title: "ipv6 sit tunnel configuration problem"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by baritono on 2008-08-04
Hi!

I'm using Ubuntu 8.04 on my desktop computer. (kernel 2.6.24-18-generic) I want to access IPv6 through a tunnel broker server. Here's what I've got so far:

# iptunnel add sit1 mode sit remote <server IPv4 addr> local <my IPv4 addr> ttl 30
# ifconfig sit1 up
# ifconfig sit1 inet6 add <my IPv6 addr>/128
# route -A inet6 add ::/0 sit1
# echo 1 > /proc/sys/net/ipv6/conf/all/forwarding
# ping6 <server IPv6 addr>
PING <server IPv6 addr>(<server IPv6 addr>) 56 data bytes
ping: sendmsg: [COLOR="Red"]Operation not permitted[/COLOR]
ping: sendmsg: [COLOR="Red"]Operation not permitted[/COLOR]

--- <server IPv6 addr> ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms

everything looks fine until I tried to ping the tunnel broker server, when I got the "Operation not permitted" error.

Am I doing anything wrong? How can I diagnose this problem? Would anybody please help me! Thanks!

---

### Post by elventear on 2009-04-29
Did you ever find a cause of the problem? I am experiencing the same issue and I am unable to find the cause.

---

### Post by m1lkman on 2010-07-16
Know this is old but, for anybody searching.

Try using ping6

Ping won't work with ip6 addresses.

---

