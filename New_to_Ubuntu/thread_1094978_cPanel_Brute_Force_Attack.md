---
title: "cPanel Brute Force Attack"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by finer recliner on 2009-03-13
what is the error message you get when trying to access cPanel from ubuntu?

---

### Post by HermanAB on 2009-03-13
When you run a public server, you should always install a rate limit rule in order to guard against brute forcers:

```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit -burst 5 -j ACCEPT
```

It will slow down continuous retries from the same source address, without affecting normal operation.

Cheers,

Herman

---

