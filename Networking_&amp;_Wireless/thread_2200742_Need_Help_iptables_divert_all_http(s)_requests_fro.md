---
title: "Need Help: iptables divert all http(s) requests from specific ip block to youtube.com"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by xpd777 on 2014-01-20
Hello, i'd like to ask if this syntax would work on my objective:

iptables -A INPUT --source 192.168.1.0/24 -p tcp -j DNAT --to youtu.be

I'm using a tomato router with two VLANs. 192.168.1.0/24 for guests and i'd like all guests to access only youtube.com.

---

### Post by SeijiSensei on 2014-01-21
Youtu.be resolves to a number of server addresses using "round-robin" DNS:
```

Seiji@GhostWorld:~$ host youtu.be
youtu.be has address 173.194.43.39
youtu.be has address 173.194.43.40
youtu.be has address 173.194.43.41
youtu.be has address 173.194.43.46
youtu.be has address 173.194.43.32
youtu.be has address 173.194.43.33
youtu.be has address 173.194.43.34
youtu.be has address 173.194.43.35
youtu.be has address 173.194.43.36
youtu.be has address 173.194.43.37
youtu.be has address 173.194.43.38
youtu.be has IPv6 address 2607:f8b0:400d:c04::be

```
You could redirect traffic to one of those.  But if you just want to restrict users on the 192.168.1.0/24 subnet, use INPUT rules instead like this:

```

/sbin/iptables -A INPUT -s 192.168.1.0/24 -d 173.194.43.32 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.0/24 -d 173.194.43.33 -j ACCEPT
[...]
/sbin/iptables -A INPUT -s 192.168.1.0/24 -d 173.194.43.41 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.0/24 -d 173.194.43.46 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j REJECT --reject-with icmp-host-prohibited

```

That allows traffic to the YouTube servers and blocks everything else.  I'd probably choose simplicity over specificity and write a single rule with the target 173.194.43.0/24, which are all addresses controlled by Google:
```

/sbin/iptables -A INPUT -s 192.168.1.0/24 -d 173.194.43.0/24 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j REJECT --reject-with icmp-host-prohibited

```

---

### Post by xpd777 on 2014-01-23
thanks will try this tomorrow on my office router.

---

