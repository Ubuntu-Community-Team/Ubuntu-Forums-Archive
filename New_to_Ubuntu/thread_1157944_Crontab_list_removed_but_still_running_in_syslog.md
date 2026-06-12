---
title: "Crontab list removed but still running in syslog"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by televisi on 2009-05-13
Hi All,
I'm using Ubuntu Server edition.

I've removed crontab list from a user 'jo'
```
[jo@TESTING:~] crontab -l
no crontab for jo

```

I also checked there is no 'jo' cron user file in /var/spool/cron/crontabs folder
```
[root@TESTING:/var/spool/cron/crontabs] l
total 12
drwx-wx--T 2 root   crontab 4096 May 13 22:01 .
drwxr-xr-x 5 daemon daemon  4096 Jan  2  2000 ..
-rw------- 1 root   crontab  317 May 13 21:59 root

```

but it keeps appearing in /var/log/syslog:
```
**May 13 22:19:01 TESTING /USR/SBIN/CRON[4742]: (jo) CMD (/testing/script.sh)**
May 13 22:19:01 TESTING /USR/SBIN/CRON[4744]: (root) CMD (/home/anotherscript.sh)

```

I've restarted the Ubuntu, this cron job from user 'jo' keeps appearing, did I miss something here?

Thanks

---

### Post by televisi on 2009-05-13
Ah... thanks to mprince, I found it, apparently it is listed in /etc/crontab

silly me ;)

---

