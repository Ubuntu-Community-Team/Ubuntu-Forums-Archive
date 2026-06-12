---
title: "DNS woes - SERVFAIL and reverse lookup fail"
date: 2015-01-07
forum: Networking &amp; Wireless
---

### Post by abasel on 2015-01-07
Set up my first DNS. Can resolve external urls but not local machines

named.conf.local
```
zone "accounting.org.nz" {
        type master;
        file "/etc/bind/zones/db.accounting.org.nz";
};

zone "0.129.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/zones/db.0.129.168.192";
};

```

db.accounting.org.nz
```
$TTL    604800
@       IN      SOA     s-networking-02.accounting.org.nz. (
                        2010052001      ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800)         ; Negative Cache TTL
;
@       IN      NS      s-networking-02.accounting.org.nz.
@       IN      A       127.0.0.1
@       IN      AAA     ::1

s-networking-02 IN      A       192.168.129.10


```

0.129.168.192.in-addr.arpa
```
@       IN      SOA     s-networking-02.accounting.org.nz. (
                        2010052001      ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800)         ; Negative Cache TTL
;
@       IN      NS      s-networking-02.accounting.org.nz.
10      IN      PTR     s-networking-02.accounting.org.nz.

```

When I try NSLOOKUP on 2-networking-02 I get 
> > s-networking-02
Server:         192.168.129.10
Address:        192.168.129.10#53

** server can't find s-networking-02.accounting.org.nz: SERVFAIL


When I try with 192.168.129.10 I get
> > 192.168.129.10
Server:         192.168.129.10
Address:        192.168.129.10#53

** server can't find 10.129.168.192.in-addr.arpa: NXDOMAIN


Looking at the server logs I get the following errors reading the zone files: unexpected end of input

---

### Post by abasel on 2015-01-07
Got nslookup s-networking-02 to work by using the following for


db.accounting.org.nz
```
$ORIGIN .
$TTL 86400      ; 1 day
accounting.org.nz IN SOA 202.126.207.10. server.accounting.org.nz. (
                                2012041141 ; serial
                                28800      ; refresh (8 hours)
                                7200       ; retry (2 hours)
                                864000     ; expire (1 week 3 days)
                                86400      ; minimum (1 day)
                                )
                        NS      124.150.167.93.
$ORIGIN accounting.org.nz.
s-networking-02            A       192.168.129.10
ns                         A       192.168.129.10

```

Still fighting with the reverse lookups

---

### Post by Doug S on 2015-01-08
Yes, your files have multiple issues.
I would recommend [the Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/dns.html") as a reference and use [named-checkzone]("https://help.ubuntu.com/lts/serverguide/dns-troubleshooting.html") to test things first.
Example:```
doug@doug-64:~/config/bind/templ$ cat db.129.168.192
[COLOR=#ff0000]$TTL    604800[/COLOR]
@       IN      SOA     s-networking-02.accounting.org.nz. [COLOR=#ff0000]bla.accounting.org.nz.[/COLOR](
                        2015010701      ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800)         ; Negative Cache TTL
;
@       IN      NS      s-networking-02.accounting.org.nz.
10      IN      PTR     s-networking-02.accounting.org.nz.
``````
doug@doug-64:~/config/bind/templ$ [COLOR=#ff0000]named-checkzone 129.168.192.in-addr.arpa db.129.168.192[/COLOR]
zone 129.168.192.in-addr.arpa/IN: loaded serial 2015010701
[COLOR=#ff0000]OK[/COLOR]
```

---

### Post by abasel on 2015-01-08
Many thanks; the light is slowly coming on :-)  

That all worked.

---

### Post by abasel on 2015-01-08
Just want to ask one more question: Can you point me in the right direction to do the following:

When DHCP issues and IP this DNS is not updated to reflect this. How do I get this to happen automatically?

---

### Post by abasel on 2015-01-08
To answer my own question I found the following: [http://lani78.com/2012/07/23/make-your-dhcp-server-dynamically-update-your-dns-records-on-ubuntu-12-04-precise-pangolin/](http://lani78.com/2012/07/23/make-your-dhcp-server-dynamically-update-your-dns-records-on-ubuntu-12-04-precise-pangolin/)

---

