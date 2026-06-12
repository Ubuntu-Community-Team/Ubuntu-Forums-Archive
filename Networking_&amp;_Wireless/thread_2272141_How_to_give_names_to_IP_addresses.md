---
title: "How to give names to IP addresses"
date: 2015-04-04
forum: Networking &amp; Wireless
---

### Post by kepar2 on 2015-04-04
Hello,

I have been trying to figure out how to give "names" to IP addresses that is assigned by my DHCP server.
I want to do it dynamically. I have done it before statically by adding one by one in my DNS-zones files.

Then it was something like this:

```

/etc/bind/db.local.example.com
 
$TTL    604800
@       IN      SOA     local.example.com. hostmaster.example.com. (
                        1503281         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.local.example.com.
ns1     IN      A       192.168.0.1
;
; Local computers / name comes here::
comp1   IN      A       192.168.0.101 
comp2   IN      A       192.168.0.102 
comp3   IN      A       192.168.0.103

```

with names I mean comp1, comp2, comp3...comp200, etc.

thanks

---

