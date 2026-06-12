---
title: "iptables on LTS 6.06 Dapper and Frontpage"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by elbeano on 2007-05-16
I want to use Frontpage via FTP, but when I try to load remote site using FTP I receive the error: "500 Illegal PORT command"

When I substitute my DLink router for my Linux Gateway/Webserver, this works fine. Details follow on the gateway:

Dapper Drake LTS 6.06
Iptables setup:

 -t nat -A POSTROUTING -o eth0 -j MASQUERADE
 -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
 -A FORWARD -i eth1 -o eth0 -j ACCEPT

I am guessing I need to add something to my iptables setup to make this work, but I'm not sure what.

---

### Post by elbeano on 2007-07-29
Yes, I figured this out. I simply needed to specify passive FTP when accessing my sites.

---

