---
title: "can't get bind9 wildcard domain to work"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by jdaum on 2008-09-26
Hi,

I'm not completely new to Linux, but this is the first time in 6 years I have it on a laptop again. I have some experience with managing a Debian based web server though.

I want to use this computer for web development and have in the past used my windows host file to setup local development domain names.

I'd like to automate that now by setting up a wildcard domain with bind. I'm sure I must be missing a setp though, as it doesn't work.

My /etc/bind/named.conf.local:
```
zone "example.com" IN {
        type master;
        file "data/master-example.com";
        allow-update { none; };
};

```

data/master-example.com:

```
example.com. 86400     IN      SOA     example.com. hostmaster.example.com. (
                                        2005100804      ; Serial YYYYMMDDXX
                                        10800           ; Refresh
                                        3600            ; Retry
                                        3600000         ; Expire
                                        86400 )         ; minimum
                        IN      NS      ns1.example.com.
                        IN      NS      ns2.example.com.
                        IN      MX      10      mail.example.com.
                        IN      A       127.0.0.1
mail                    IN      A       127.0.0.1
ns1                     IN      A       127.0.0.1
ns2                     IN      A       127.0.0.1
*.example.com.		IN      CNAME   example.com

;
```

I've restarted bind, but get domain not found when I ping example.com or test.example.com

/etc/resolv.conf shows

```
nameserver 127.0.0.1
```

I'm not sure what is missing. Any help appreciated.

Kind regards,

Jochen

---

