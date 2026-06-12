---
title: "windows to ubuntu DNS replication. Is is possible to do?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by curtriley on 2009-06-16
Is there a way to get ubuntu DNS to pull domains and all domain info from a windows DNS server to populate the ubuntu DNS data?

---

### Post by HermanAB on 2009-06-16
Howdy,

Windows DNS is an old copy of BSD BIND8.  So you can simply copy the configuration files from Windows to Linux.  The named.conf file and zone files are hiding in there somewhere - some searching will find them.  I found them once, just can't remember where.

---

### Post by curtriley on 2009-06-17
Once I find the files, how can I automate this process?

---

