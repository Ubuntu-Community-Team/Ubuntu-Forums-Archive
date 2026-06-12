---
title: "Oracle 10 g Connection Issue with Oracle 8i Server"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by Yogesh Upadhyay on 2011-02-18
HI,

We are here in our company migrating from Windows to Ubuntu Desktop. Our development team is having a very serious issue with ubuntu.
The thing is We are having one Oracle8i Database, and we need to configure Oracle client for above said server. Since Oracle 8i 's EOL has reached and Oracle is not providing any Support regarding this.
We have to use Oracle 10 g Client for our 8i database. It shows some "Connection Error" while trying to connect to Datbase. 

Is it really possible to configure Oracle 10g Client to work with Oracle 8i...Any other version which might work in above scenario.

Any Little help would be appriciable.


Thanks in Advance.

---

### Post by Sef on 2011-02-18
Moved to absolute beginner talk.

---

### Post by davidmohammed on 2011-02-18
the only way to connect an oracle 10g client to an oracle 8i database is to ensure the oracle 8i database is patched to either 8.1.7.3 or 8.1.7.4.  You'll need to have a valid oracle metalink account to download this patch-set.

---

