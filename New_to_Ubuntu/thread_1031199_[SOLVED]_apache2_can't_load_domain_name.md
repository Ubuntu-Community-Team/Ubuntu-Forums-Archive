---
title: "[SOLVED] apache2 can't load domain name"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by gerreth on 2009-01-05
Hi, i have fully configured bind9 and ldap.

I created the domain gerreth.intern (a domain, on my computer only, so im not in a real network)

While attempting to configure horde3 is noticed while restarting apache2. He gives this error:
"apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName"

I've checked every apache config file, and all setting seem to be ok.

When i try

```
www.gerreth.intern
```
He says "It works"
```
www.gerreth.intern/ldapadmin
```
works aswell =/

Any ideas?


Thx!

---

### Post by gerreth on 2009-01-05
Problem solved by using this site: [http://languor.us/apache2-could-not-determine-servers-fully-qualified-domain-name-using-127-0-1-1-servername](http://languor.us/apache2-could-not-determine-servers-fully-qualified-domain-name-using-127-0-1-1-servername)

---

