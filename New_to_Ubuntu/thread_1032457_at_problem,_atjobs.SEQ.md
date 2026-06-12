---
title: "at problem, atjobs/.SEQ"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by pixelmuerto on 2009-01-06
hi, 
I try execute the at command and show me this message
at 12:00 friday
warning: commands will be executed using /bin/sh
Cannot open lockfile /var/spool/cron/atjobs/.SEQ: No such file or directory

in the directory 
ls -a /var/spool/cron/atjobs/
. ..

and the daemon is running 
ps aux| grep atd
daemon 12222 0.0 0.0 1984 424 ? Ss 14:15 0:00 /usr/sbin/atd


any idea ? 
thanks.

---

