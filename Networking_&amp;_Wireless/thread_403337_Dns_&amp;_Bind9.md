---
title: "Dns &amp; Bind9"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by elementsofway on 2007-04-06
I am trying to setup my pc as mail.elementsofway.com based on this [post]("http://ubuntuforums.org/showthread.php?t=236093"), but am having difficulty.

Currently these correctly work:
[INDENT][FONT="Courier New"]ping elementsofway.com  --> 192.168.1.90
ping mail.elementsofway.com  --> 192.168.1.90
hostname  --> mail.elementsofway.com[/FONT][/INDENT]

But these don't come back the way I want:
[INDENT][FONT="Courier New"]nslookup mail.elementsofway.com  --> 216.177.89.6
dig mail.elementsofway.com  --> ns1.discountasp.net.[/FONT][/INDENT]


My PC's ip is 192.168.1.90 (mail.elementsofway.com)
My DNS server is 192.168.1.254 (launchmodem.com)


Files...

/etc/bind/named.conf.local
```
zone "elementsofway.com" {
        type master;
        file "/etc/bind/zones/elementsofway.com.db";
};

zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.1.168.192.in-addr.arpa"; 
};

```

/etc/bind/named.conf.options    includes...
```
        forwarders {
                192.168.1.254;
        };

```

/etc/bind/zones/elementsofway.com.db
```
elementsofway.com.   IN   SOA   elementsofway.com. (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
elementsofway.com.      IN      NS              elementsofway.com.
elementsofway.com.      IN      MX     10       mta.elementsofway.com.

// Replace the IP address with the right IP addresses.
mta                 IN      A       192.168.1.90
elementsofway.com     IN      A       192.168.1.90

```

/etc/bind/zones/rev.1.168.192.in-addr.arpa
```
@ IN SOA ns1.elementsofway.com. admin.elementsofway.com. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.elementsofway.com.
254                  IN    PTR    elementsofway.com

```


I think my problem is with elementsofway.com.db file, but I'm not sure.  Any help would be great.

---

### Post by bnuytten on 2007-04-21
elementsofway.com is a registered domain name. There are a few options here. If you registered the domain it is easy to solve. If you didn't you can either choose another domain name that is not in use (e.g. elementsofway.org) or adjust your DNS configuration so that it first consults your own private DNS and than another DNS. Third option is to only use your own DNS server and make it a forwarding one...

---

