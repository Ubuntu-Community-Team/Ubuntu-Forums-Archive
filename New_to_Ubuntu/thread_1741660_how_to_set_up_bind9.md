---
title: "how to set up bind9"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by node2network on 2011-04-28
If my English is not polite, please forgive me.

I installed bind9 on Ubuntu10.04.
My question is about my configuration below.

dns server => 192.168.0.15
simulation server => 192.168.0.201

/etc/bind/hoge.net
```


$TTL    86400

@       IN      SOA     dns.hoge.net. root.hoge.net. (
                                2011042802      ; Serial
                                10000           ; Refresh
                                7200            ; Retry
                                604800          ; Expire
                                10000 )         ; Minimum
;
@       IN      NS      dns.
        IN      PTR     dns.hoge.net.
201     IN      PTR     sim01.hoge.net.



```

/etc/bind/0.168.192.in-addr.arpa
```


$TTL    86400

@       IN      SOA     dns.hoge.net. root.hoge.net. (
                                2011042802      ; Serial
                                10000           ; Refresh
                                7200            ; Retry
                                604800          ; Expire
                                10000 )         ; Minimum
;
@       IN      NS      dns.
        IN      PTR     dns.hoge.net.
201     IN      PTR     sim01.hoge.net.



```

/etc/bind/named.conf
```


include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

zone "hoge.net" {
        type master;
        file "/etc/bind/hoge.net";
};

zone "0.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/0.168.192.in-addr.arpa";
};


```

result below.

```


$ nslookup sim01.hoge.net
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	sim01.hoge.net
Address: 192.168.0.201

$ nslookup www.hoge.net  
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
www.hoge.net	canonical name = dns.hoge.net.
Name:	dns.hoge.net
Address: 192.168.0.15


```

I can access www sim01.hoge.net by using ssh.
But I cannot access ttp://www.hoge.net. Web Browser shows "This Page Cannot Be Displayed".

How do I fix it?

---

### Post by lreyes6 on 2011-04-28
Hi,

Can you post your apache configuration for that domain?

---

### Post by node2network on 2011-04-28
oops!

I don't know that apache configuration is needed.

---

### Post by lreyes6 on 2011-04-28
You need to resolve your domain with bind9 and then tell apache to serve the website. If you are gonna have more than one domain look for Apache and Virtual domains

---

### Post by node2network on 2011-04-28
I added "ServerName www.hoge.net" on /etc/apache/sites-available/default.

But I cannot access....

---

