---
title: "[SOLVED] Bind Help"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by Deicist on 2008-07-22
I'm currently in the process of moving my Web / Mail / DNS server from an aging Windows 2003 box to an Ubuntu based system.

I currently have the Web and Email servers transferred over, however I'm having problems with setting up DNS.  

I'm behind a NAT device, my external IP is 87.194.103.105

Here's what I have so far:

/etc/bind/named.conf.local

```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name
zone "comicsearch.co.uk" {
        type master;
        file "/etc/bind/zones/comicsearch.co.uk.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "66.10.10.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.66.10.10.in-addr.arpa";
};
```

/etc/bind/zones/comicsearch.co.uk.db

```

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
comicsearch.co.uk.      IN      SOA     WebServer.comicsearch.co.uk. admin.comicsearch.co.uk. (
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
comicsearch.co.uk.      IN      NS              WebServer.comicsearch.co.uk.
comicsearch.co.uk.      IN      MX     10       MailServer.comicsearch.co.uk.

// Replace the IP address with the right IP addresses.
www              IN      A       87.194.103.105
MailServer              IN      A       87.194.103.105
WebServer              IN      A       87.194.103.105

```

 /etc/bind/zones/rev.66.10.10.in-addr.arpa

```


@ IN SOA webserver.comicsearch.co.uk. admin.comicsearch.co.uk. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     WebServer.comicsearch.co.uk.
15                   IN    PTR    comicsearch.co.uk

```


/etc/resolv.conf

```

search comicsearch.co.uk
nameserver 10.10.66.15

```

Help?

---

### Post by Bachstelze on 2008-07-22
Whoever wrote those example files was **wrong**! You **must** edit the serial line of your zone file so that it reflects the last time it was modified. Change this

```
2006081401;
```

into this :

```
2008072201;
```

---

### Post by Deicist on 2008-07-22
Okay, done that.

no change :(

---

### Post by Bachstelze on 2008-07-22
Well, what *is* the problem you're having, anyway?

---

### Post by Deicist on 2008-07-22
> **HymnToLife said:**
> Well, what *is* the problem you're having, anyway?

Okay, the problem is that I'm try to migrate from a windows server to an ubuntu server for my DNS.

I've setup the Ubuntu server as above, but I now can't resolve [www.comicsearch.co.uk](www.comicsearch.co.uk) (my website, hosted on the same server) from any machine using the Ubuntu server as DNS.

Thanks for the quick response by the way, much appreciated.

---

### Post by kpatz on 2008-07-22
Try this format for your comicsearch.co.uk.db (I based this on the .db files I have on my box).

```
$TTL 14400
@       IN      SOA     localhost.      root.comicsearch.co.uk. (
                                                2008072201
                                                28800
                                                3600
                                                604800
                                                38400 )

comicsearch.co.uk.   14400   IN      NS      ns1.comicsearch.co.uk.
comicsearch.co.uk.   14400   IN      MX     10       mail.comicsearch.co.uk.

www     14400          IN      A       87.194.103.105
mail    14400          IN      A       87.194.103.105
ns1     14400          IN      A       87.194.103.105

```
Did you register comicsearch.co.uk?  Do you have the DNS pointing to your server?

---

### Post by Deicist on 2008-07-22
> **kpatz said:**
> Try this format for your comicsearch.co.uk.db (I based this on the .db files I have on my box).

```
$TTL 14400
@       IN      SOA     localhost.      root.comicsearch.co.uk. (
                                                2008072201
                                                28800
                                                3600
                                                604800
                                                38400 )

comicsearch.co.uk.   14400   IN      NS      ns1.comicsearch.co.uk.
comicsearch.co.uk.   14400   IN      MX     10       mail.comicsearch.co.uk.

*     14400          IN      A       87.194.103.105


```


I altered it slightly based on the fact I want everything to resolve to the same IP.

Works a treat, thank you so much.

the only problem now is that [http://comicsearch.co.uk](http://comicsearch.co.uk) doesn't resolve... any ideas?

edit: strangley I can resolve comicsearch.co.uk (no 'www') from the localhost, but not from another machine uising it as it's DNS.  strange.

---

### Post by kpatz on 2008-07-23
> **Deicist said:**
> the only problem now is that [http://comicsearch.co.uk](http://comicsearch.co.uk) doesn't resolve... any ideas?
Add an A record for comicsearch.co.uk as follows:```
comicsearch.co.uk.     14400          IN      A       87.194.103.105
```

---

