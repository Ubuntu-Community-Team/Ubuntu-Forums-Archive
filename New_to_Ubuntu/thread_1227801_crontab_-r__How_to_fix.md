---
title: "crontab -r ? How to fix????"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by lcnrj on 2009-07-31
:confused:
I always used crontab
unintentionally gave a crontab -r and sudo crontab-r  What can I do now?
Appears orphan error and 6067 bad username. :oops::oops:

---

### Post by credobyte on 2009-07-31
```
crontab -e

```

Save it and ..
```
crontab -l
```

Doesn't help ?

---

### Post by lcnrj on 2009-07-31
yes, I do that but now appears in cron.log:

"Jul 31 15:42:01 don cron[6038]: Error: bad username; while reading /etc/crontab"
"Jul 31 15:42:01 don /usr/sbin/cron[6038]: (sillas~) ORPHAN (no passwd entry)"

---

### Post by lcnrj on 2009-08-01
resolved:
I don't know how, but that error disappeared: 
"Jul 31 15:42:01 don cron[6038]: Error: bad username; while reading /etc/crontab"
 
and I run the jobs even though state "Jul 31 15:42:01 don /usr/sbin/cron[6038]: (sillas~) ORPHAN (no passwd entry)" 

:D

---

