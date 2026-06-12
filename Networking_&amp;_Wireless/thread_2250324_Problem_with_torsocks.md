---
title: "Problem with torsocks"
date: 2014-10-28
forum: Networking &amp; Wireless
---

### Post by Farinet on 2014-10-28
When i try to start 

```
torsocks fetchmail -c
```

i'm getting this error msg:

```
 ERROR torsocks[2627]: Unable to resolve. Status reply: 4 (in socks5_recv_resolve_reply() at socks5.c:657)gethostbyname fehlgeschlagen für <hostname>
Nicht-behebbarer Fehler in der NamensauflösungKann meinen eigenen Rechnernamen nicht in der Hosts-Datenbank finden und nicht qualifizieren!
Versuche, mit unqualifiziertem Rechnernamen weiterzuarbeiten.

```
 
(I - try to - translate: gethostname failed for <hostname> 
Unsolveable error in DNS resolution. Unable to find my own hostname in host database and to qualify it).

In the following the above error msg tells me to repair my /etc/hosts, DNS NIS or LDAP. For what i was able to check i looked into my  /etc/hosts and it looks like this:

```
 
127.0.0.1    localhost
127.0.0.1    <hostname>


# Below lines are for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

And /etc/resolv.conf looks like this:

```

nameserver <wlan ip address here)
search (name of wlan router here)

```

Thanks in advance for any suggestion!

---

