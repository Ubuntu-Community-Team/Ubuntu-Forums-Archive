---
title: "Can't do &quot;sudo apt-get update&quot;"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by yikesy on 2010-06-02
I'm trying to install MySQL.

"sudo apt-get install mysql" fails (trying to install version 5.1) so I thought I'd do "sudo apt-get update" and I get lots of 400 Bad Requests:

```
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic/universe/source/Sources.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic/multiverse/source/Sources.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-updates/main/source/Sources.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-updates/universe/source/Sources.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-security/main/source/Sources.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-security/restricted/source/Sources.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-security/universe/source/Sources.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz  400  Bad Request
W: Failed to fetch http://astromirror.uchicago.edu/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  400  Bad Request
```

I even tried switching the software source.
If I paste one of these URLs in Firefox I can download the file just fine, so it isn't my internet connectivity.

I'm using 9.10. I dare not use "Update Manager" given that if it dies in the middle it can ruin my install.

Any advice? Thanks!

---

### Post by zkriesse on 2010-06-02
Do you have the Multiverse repositories installed? Just a thought..

---

### Post by yikesy on 2010-06-02
Thanks for the pointer, Zach!

I went into System->Administration->Software Sources->Other Software

and checked both of them. I ran apt-get install mysql a couple more times, eventually trying "--fix-missing" and it finally worked.

What utter nonsense.
:)

---

### Post by Bachstelze on 2010-06-02
It was probably just a temporary problem on the mirror.

---

