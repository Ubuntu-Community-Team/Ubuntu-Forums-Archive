---
title: "Bind configuration with example.com"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by arron on 2007-08-08
I have my bind dns server up and running.  It is handling requests for my registered domain.  I have entries working like mail.example.com, [www.example.com](www.example.com) and so on, but i cant figure out how to get example.com to resolve to an ip, so ping example.com will work (ping [www.,](www.,) ns, mail and so on work).

I tried a entry like:

```
example.   IN   A   123.123.123.123
```
and :

```
123   IN   A   example.
```

in the 2 zone files, and of course with the proper ip's and domain names.

That from what i read this should work, but does not.  Any ideas?

---

### Post by PaulFr on 2007-08-09
As far as I can remember, shouldnt you have ```
example.com.   IN   A   123.123.123.123
``` rather than just **example.**

---

### Post by arron on 2007-08-09
Thanks PaulFr, that did the trick!

---

