---
title: "[SOLVED] Problem Uadating Hardy in India"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Andavane on 2008-12-14
Am staying in India about 200 km from Chennai.
When updating ubuntu (from the kolkata server) I get the following message:

> Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/main/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/restricted/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/universe/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/main/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

anyone know this problem and how to fix?

regards

John

---

### Post by nhasian on 2008-12-14
go to System -> Administration -> Software sources

change the *download from* to *other* then select best server.  now give it a try.

---

### Post by Andavane on 2008-12-15
> **nhasian said:**
> go to System -> Administration -> Software sources

change the *download from* to *other* then select best server.  now give it a try.
Thanks, funnily enough when I next logged in, it said I had two other update (or something) which I clicked to update. After it had done that, the remaining 'problem' updates seem to have vanished.
Not sure what happened there.
Will certainly select 'other' should the problem recur.
Regards
John

---

