---
title: "Setting Bind server to forward DNS requests that it can't resolve"
date: 2019-02-13
forum: Networking &amp; Wireless
---

### Post by wontontwelve on 2019-02-13
I'm working in an environment where we have two pre-existing Windows Server DNS servers, but need to frequently change the IP addresses associated with certain static internal URLs. What I'm trying to do is set up a Bind server which resolves those specific development URLs when requested, but which use our existing DNS servers to resolve any requests which it cannot resolve itself.
 
Details on the environment [SIZE=1](please note that radstuff.com is used as a placeholder for a real domain)[/SIZE]:
dev-dns01 is the Ubuntu virtual machine running Ubuntu 16.04.5 LTA and Bind
[www.radstuff.com]("http://www.radstuff.com") is our domain name
10.0.0.82 is the IP address of dev-dns01
10.0.0.6 is one of our pre-existing DNS servers
10.0.0.7 is our other pre-existing DNS server

Currently, dev-dns01 is properly resolving items specified in its forward lookup zone as desired, including translating our static development URLs into the desired IP addresses. However, when I request that dev-dns01 resolve any URL outside of radstuff.com, I get a "query refused" error (while using Windows Command Prompt). I thought that I had this server set up so that 10.0.0.7 and 10.0.0.6 would act as forwarders, but apparently not. These servers are able to ping each other. If anyone has any suggestions, I'd really appreciate it.

Here are the contents of named.conf.local:
```
zone "radstuff.com" {
        type master;
        file "/etc/bind/zones/db.radstuff.com";       # zone file path
        allow-transfer { any; };                        # allow transfers from $


};


zone "0.0.10.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/db.0.0.10";
        allow-transfer { any; };


};


zone "25.0.10.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/db.25.0.10";
        allow-transfer { any; };


};


zone "8.0.10.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/db.8.0.10";
        allow-transfer { any; };


};

```

Here are the contents of named.conf.options:
```
options {
        directory "/var/cache/bind";


        recursion yes;                   #enables recursive queries
        listen-on { 10.0.0.82; };       #listens here only
        allow-transfer { any; };        #enable zone transfers by default


        forwarders {
                10.0.0.7;
                10.0.0.6;
        };


        dnssec-validation auto;


        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

Here is the content of db.radstuff.com:
```
;
; BIND data file for local loopback interface
;
$TTL    300
@       IN      SOA     dev-dns01.radstuff.com. admin.radstuff.com. (
                              2         ; Serial
                         604800         ; Refresh
                          180           ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;


; name servers - NS records
                IN      NS      dev-dns01


; name servers - A records
dev-dns01       IN      A       10.0.0.82


; 10.0.5.0/24 - A records
test            IN      A       10.0.5.5


; 10.0.0.0/24 - A records
apps                            IN      A       10.0.0.122

```
And finally, here are the contents of the reverse lookup table for 10.0.0.x, db.10.0.0:
```
;
; BIND reverse data file for local loopback interface
;
$TTL    300
@       IN      SOA     dev-dns01.radstuff.com. admin.radstuff.com. (
                              1         ; Serial
                         604800         ; Refresh
                          180           ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
; name servers
        IN      NS      dev-dns01.radstuff.com.


; PTR records
82      IN      PTR     dev-dns01.radstuff.com.       ;10.0.0.82







```

---

### Post by wontontwelve on 2019-02-14
I've solved this, and wanted to put the relevant information here in case anyone finds this in the future.

In named.conf.options, under "options {" I had to add the following*:

allow-recursion { any; };
allow-query { any; }
allow-query-cache { any; };


*Please note that these settings are only recommended if the Bind9 server is protected from outside traffic. In this case, only a few devices can use this server as a name server.

---

