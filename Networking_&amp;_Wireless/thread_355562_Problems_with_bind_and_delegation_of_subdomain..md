---
title: "Problems with bind and delegation of subdomain."
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by thequestion on 2007-02-07
Hi I got the tip earlier this week by someone here how to have different DNS server for the domain and a subdomain. through delegation

I have a problem though here are my configs:

```

#resolv.conf
nameserver 130.98.431.* #I can ping www.google.com etc.. so DNS server is up and runnig

```

master.test.domain.com.zone
```

$TTL 2d ; zone default of 2 days
$ORIGIN         test.domain.com.
                IN      SOA     ns1.test.domain.com. root.test.domain.com. (
                        2007020711              ; serial number
                        2h                      ; refresh = 2 hours
                        15m                     ; update retry = 15 minutes
                        3w12h                   ; expiry = 3 weeks + 12 hours
                        2h20m                   ; minimum = 2 hours + 20 minutes
                        )
        test.domain.com.             IN NS   ns1.test.domain.com.
        ns1.test.domain.com.         IN A    130.98.431.*  ;* actually not * here
        www1.test.domain.com.        IN A    130.98.431.*
        www2.test.domain.com.        IN A    130.98.431.*
        www3.test.domain.com.        IN A    130.98.431.*


```
named.conf.local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "test.domain.com" in{
type master;
file "/etc/bind/master.test.domain.com.zone";
};

```

rndc status
```

debian:/etc/bind# rndc status
number of zones: 7
debug level: 0
xfers running: 0
xfers deferred: 0
soa queries in progress: 0
query logging is OFF
server is up and running

```

I can ping google and this site for example but when I try to ping test.domain.com I get "ping: unknown host test.domain.com" Can anyone see what the problem is or if I have forgotten something?

Thanks in advance!

---

### Post by koenn on 2007-02-07
> I can ping google and this site for example but when I try to ping test.domain.com I get "ping: unknown host test.domain.com" Can anyone see what the problem is or if I have forgotten something?

What i think the problem is, is that -
- you do have a name server for  test.domain.com (i.c. ns1.test.... ) and a SOA, but nobody knows, and the only way for other computers to find out is by asking ... ns1, whose address can be found from ... ns1. 

I think what you need is some reference to your subdomain in the parent domain's zone file, like saying : this is domain.com, but any queries about test.domain.com should go to (ip address of) ns1.test.domain.com.
I'm not sure how to do that - could be a SOA or NS record, or an A record like
```
test.domain.com. in A 193....
```

not 100% sure though. Google with DNS subdomain delegation
or have a look at this 
[http://www.zytrax.com/books/dns/ch9/delegate.html](http://www.zytrax.com/books/dns/ch9/delegate.html)

---

