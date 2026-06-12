---
title: "bind9 config for subset of domain"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by cnschulz on 2008-02-26
Hi, I have bind9 running successfully on my headless gutsy server.

I use dyndns so i can have a "proper" site name that points to my *static* ip address. (actually i have two that point to the same place but thats irrelevant)

id like to use the homeip.net hostname inside my network for consistency. thats all i need the dns for.

internal dns is configured such that: xxx.homeip.net -> 192.168.1.3

however, with my current configuration, i have hijacked the whole *.homeip.net domain... so if i want to look at someone elses (aaa.homeip.net) dns will fail.

is there a way i can just override xxx.homeip.net to point to my internal network and leave the others at homeip.net to resolve on the secondary dns (my isp's dns)

cheers

c.

-----

named.conf.local:

zone "homeip.net" {
        type master;
        file "/etc/bind/zones/homeip.net.db";
        };

zone "1.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};

-----
db.192:

TTL    604800
@       IN      SOA     xxx.homeip.net. xxx.homeip.net. (
                     2008022602         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      xxx.
3       IN      PTR     xxx.homeip.net.

-------------
 homeip.net.db:

@                IN      SOA     xxx.homeip.net. xxx.local. (

                                                        2008022602
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

@                IN      NS      xxx.homeip.net.
@                IN      A       192.168.1.3
xxx         IN      A       192.168.1.3

---

