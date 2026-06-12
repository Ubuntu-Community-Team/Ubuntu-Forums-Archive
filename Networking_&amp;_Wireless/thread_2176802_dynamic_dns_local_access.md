---
title: "dynamic dns local access"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by biervat2 on 2013-09-26
hi

I have a server which is accessible from outside my network with a dynamic dns address (no-ip.biz). I want to use the same address to access my server locally but my router does not support NAT loopback.
After doing some research I installed bind9 dns server. I've added 2 opendns server in named.conf.options as forwarders and a zone in named.conf.local:

        zone "mydomain.zapto.org" {
             type master;
             file "/etc/bind/db.mydomain.zapto.org";
        };

Now I don't know what I have to do with the db.mydomain.zapto.org file. I've tried some tutorials but none of them work. The file now looks like this:

> ;; BIND data file for local loopback interface
;
$TTL    604800
$ORIGIN zapto.org
@       IN      SOA     ns.zapto.org. root.gmail.com. (
                     2013092639         ; Serial
                             3H         ; Refresh
                             15         ; Retry
                             1w         ; Expire
                             3h )       ; Negative Cache TTL
;
@       IN      NS      ns.zapto.org.
ns      IN      A       192.168.1.100


;also list other computers
mydomain    IN      A       192.168.1.100

---

