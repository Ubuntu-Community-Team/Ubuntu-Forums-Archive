---
title: "[SOLVED] Bind DNS problem"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by gkaragoulis on 2008-08-25
I'm trying to setup a secondary DNS server for my company's existing Windows 2003 AD domain, but I keep running into problems.  Every time i do:
```
nslookup  <computer>
```
it says NXDOMAIN, and when I do:
```
nslookup  <computer>.mydomain.com
```
it says it couldn't find "<computer>.mydomain.com.mydomain.com".  So it's putting an extra suffix on the zone and it can't find it (SERVFAIL).

How do I make it search for <computer>.mydomain.com, and not <computer> or <computer>.mydomain.com.mydomain.com ?  I have already checked and doubled checked my 'resolv.conf' so that I know the default search domain is 'mydomain.com'

---

### Post by gkaragoulis on 2008-08-26
K I figured out what went wrong.  In the how-to I read they told me to declare the zone like so:
```
zone "example.com"{
...
};
```
When really I should have made it look like:
```
zone "*.example.com" {
...
};
```
Stupid syntax error...

---

