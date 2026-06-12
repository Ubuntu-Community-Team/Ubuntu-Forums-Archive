---
title: "user's crontab versus root's crontab"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by SBFree on 2009-01-30
I still need help making a crontab file. The command I want to run is a perl script owned by user www-data. The user is Apache2 from what I understand. I have learned there are seperate crontab files for each user but do not know where any are expect for the one for root. Can I run a command for this script from root's crontab or do I have to make one for this user? If I have to make one for this user where should it be placed? Thanks.

---

### Post by hyper_ch on 2009-01-30
why not run it from www-data's crontab?

(1) make a text file (www-cron.txt) with the cron entry e.g.
```

30 23 * * * /path/to/script

```

(2) add it to www-data cron
```

sudo crontab -u www-data www-data.txt

```

(3) check if it was added:
```

sudo crontab -l -u www-data

```

---

