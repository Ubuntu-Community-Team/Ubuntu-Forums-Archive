---
title: "Teamviewer Block Problem"
date: 2015-03-03
forum: Networking &amp; Wireless
---

### Post by secoonder on 2015-03-03
Hello 
 I am using iptables  in a linux gateway (ubuntu server 12.04) and   all works good. I configured a transparent squid proxy and works too. 
i want to block Teamviewer.
 i added a deny rule "teamviewer.com" at squid.
teamviewer uses 80,443,5938 port.
i blocked 5938-5939 port by iptables.
But,when the users opened the teamviewer, The teamviewer still produced password.
What can i do ? (i can not block 80,443  port.Because ,this ports(80,443) normally is used other web sites)
Thak you very Much For your Help

---

### Post by chili555 on 2015-03-03
I'm sure it's not an elegant solution, but consider an entry in /etc/hosts something like:```
127.0.0.1       localhost
127.0.1.1       my_computer

[COLOR="#FF0000"]0.0.0.0         teamviewer.com[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by secoonder on 2015-03-04
Hello
i tried it,but it was not still blocked it

---

### Post by secoonder on 2015-07-31
Our Dns Server created zone.
teamviewer.com  returned 127.0.0.1
the problem is solved.

---

