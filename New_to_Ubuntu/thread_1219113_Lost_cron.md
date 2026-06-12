---
title: "Lost cron"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by bzarr on 2009-07-21
I'm trying to find a failing cron job, but doing the following is returning '... Is a directory'

```
sudo cat /var/spool/cron/crontabs
```

I know there is a cron trying to run as there is new mail every 5 minutes saying it's failed!

Please help

---

### Post by llamabr on 2009-07-21
edit your cron job with this command:

```
crontab -e
```

---

### Post by amingv on 2009-07-21
That's because it *is* a directory.

Try:
```
sudo ls /var/spool/cron/crontabs/
```

or

```
sudo cat /var/spool/cron/crontabs/root #or whatever user it is you want to manage
```

---

