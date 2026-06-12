---
title: "Problem resolving Domain Names"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by pkj on 2009-01-19
hi,

having a sudden and unexpected problem wherein my firefox 3 is not being able to resolve the domain names..i.e., [www.google.com](www.google.com) reaches me nowehre whereas typing the google IP takes me to the google site...

Even the links which result out of the google search are not accessible,i.e., not being resolved by the firefox...

Tried installing Opera, but no joy...

Any help/suggestions

pkj

---

### Post by hyper_ch on 2009-01-19
what's the output of
```

cat /etc/resolv.conf

```?

---

### Post by pkj on 2009-01-19
nameserver 199.100.100.1

which is my DNS

pkj

---

### Post by hyper_ch on 2009-01-19
199? That doesn't look like a private network address....

---

### Post by Bachstelze on 2009-01-19
> **hyper_ch said:**
> 199? That doesn't look like a private network address....

Why should it? Not everyone is using his own DNS server...

---

### Post by hyper_ch on 2009-01-19
well, it looks like a "router" address :)

---

### Post by pkj on 2009-01-20
yes.. Its my internal DNS.

Point to note that the address resolutions is working perfectly fine when i use a different system (another machine on ubuntu/win)..so the problem lies within this problematic machines configuration..

pkj

---

