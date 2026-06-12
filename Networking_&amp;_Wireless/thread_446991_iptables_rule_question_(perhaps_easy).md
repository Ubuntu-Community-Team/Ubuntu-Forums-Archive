---
title: "iptables rule question (perhaps easy)"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by jcpunk on 2007-05-17
I just inherited a the firewall system at work and was trying to unify it under one easy to maintain script (with toggle values for various stuff like smtp and http)

The previous system had the line here with a comment about detecting scans

```
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j $ACTION
```


A different box had this line with the same comment (verbatim)
```
$IPTABLES -A INPUT -p tcp ! --syn -m conntrack --ctstate INVALID -j $ACTION
```


What is the difference?  They look to be about the same but....

Is one better than the other?

---

### Post by jcpunk on 2007-05-18
Seems I have answered it myself

The first detects nmap -sA myhost while the second detects nmap -sM myhost

they also find others, but this is a quick reference for myself and others now.

---

