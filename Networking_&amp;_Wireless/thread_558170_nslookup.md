---
title: "nslookup"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by extracted on 2007-09-23
you can not preform zone transfers with nslookup via the ls command ?

such as

nslookuo
> 192.168.1.6

set type=any
ls -d whatever.net.  


???

i always get ls is not implemented yet.

---

### Post by jrib on 2007-09-23
That seems normal according to the man page

---

### Post by JinxAu on 2007-09-23
Have you tried "dig"?

```
dig -t AXFR 192.168.1.6
```

From the manpage:
>        The -t option sets the query type to type. It can be any valid query
       type which is supported in BIND9. The default query type "A", unless
       the -x option is supplied to indicate a reverse lookup. A zone transfer
       can be requested by specifying a type of AXFR. When an incremental zone
       transfer (IXFR) is required, type is set to ixfr=N. The incremental
       zone transfer will contain the changes made to the zone since the
       serial number in the zone&#8217;s SOA record was N.


---

