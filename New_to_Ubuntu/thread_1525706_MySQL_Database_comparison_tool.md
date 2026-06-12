---
title: "MySQL Database comparison tool"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by Blagomir on 2010-07-07
Hello,

I need to compare two remote databases`s schemas. Can you recommend me a software that can do this?

---

### Post by jtarin on 2010-07-07
[[COLOR="Blue"]Perl[/COLOR]]("http://www.perlmonks.org/?node_id=381053")

---

### Post by souki on 2010-07-07
diff utils

```
mysqldymp -d db1 > db1.sql
mysqldymp -d db2 > db2.sql
diff -y --suppress-common-lines db1.sql db2.sql > diff.txt
```

---

### Post by Blagomir on 2010-07-07
suoki,

I need to compare the tables without dump them. And if it`s possible, the sotware should "produce" SQL queries which will make the second database same as the first one.

---

### Post by souki on 2010-07-08
> **Blagomir said:**
> 
I need to compare the tables without dump them. And if it`s possible, the sotware should "produce" SQL queries which will make the second database same as the first one.

I see, but do you know anything like that? I think it's not possible to do it that way (automagically), because there's too much possibilities

I'm offen confronted with complex dev/staging/production problem, and mysqldump/diff is quite good to analyse each singular problem before producing any sql patch

---

