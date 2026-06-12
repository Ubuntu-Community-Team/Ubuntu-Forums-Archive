---
title: "[BIND9] Error in my zone file"
date: 2014-11-14
forum: Networking &amp; Wireless
---

### Post by didi2 on 2014-11-14
Hi! :)

I apology if my english is not perfect, I'm doing my best. :)

I want to create a local DNS architecture (3 servers: '_._'  '_com._' and '_example.com._').
I created the root DNS server, running Ubuntu 14.04 Server LTS.

On my root DNS server:
I changed the zone type from hints to master, and i wrote my own db.root file:
```
$TTL 1w
$ORIGIN .
.         IN   SOA   ns.   admin.   ( 2014111401 1d 2h 4w 1h )
.         IN   NS    ns
.         IN   A     192.168.1.2
ns        IN   A     192.168.1.2
com       IN   NS    ns.com
ns.com    IN   A     192.168.1.3
```

But when I want to test my configuration, I got an error:
```
$ named-checkzone . /etc/bind/db.root
zone ./IN: com/NS 'ns.com' (out of zone) has no addresses records (A or AAAA)
zone ./IN: loaded serial 2014111401
OK
```

I don't understand why it doesn't see my A RR for ns.com.
Can somebody help me?
Thanks.


[B]EDIT: The error has disappeared by itself (?).
I haven't changed anything but it started to work.[/B]

---

