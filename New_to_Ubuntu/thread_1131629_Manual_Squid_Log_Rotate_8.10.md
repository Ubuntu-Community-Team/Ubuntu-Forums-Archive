---
title: "Manual Squid Log Rotate 8.10"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by hutsy on 2009-04-21
ok, I thought I'd post this here as it seems like a noob question.

I am using Ubuntu Server 8.10, I have installed squid and have setup and it's working fine. What I want to do is use cron to rotate the log (instead of logrotate), the reason for this is I can't find any info on when the monthly / weekly / etc are run. I have tried testing by changing my system date to 3 minutes before the logrotate (both on last day of the month and the first day of the month) is executed by cron (currently 06:25 daily) and my monthly squid file rotate doesn't work.

When I run the following command manually (logged on as root) nothing happens:
/usr/sbin/squid -f /etc/squid/squid.conf -k rotate

I have also tried varients:
squid -k rotate
/usr/sbin/squid -k rotate

Is this because ubuntu has logrotate installed and it's not letting squid rotate manually?

Also when I had squid set-up using logrotate monthly I could use the 'Rotate Now' button in Webmin 1.470.


I hope this makes sense, basically I just want to remove squid from logrotate (have done this using webmin) and manually rotate the squid log file (I know how the add to cron later).

Thanks!

---

### Post by vor_lord on 2009-06-21
I am having exactly the same problem.

Examining cache.log shows that it appears to think it is working:

```

2009/06/21 19:34:55| storeDirWriteCleanLogs: Starting...
2009/06/21 19:34:55|   Finished.  Wrote 4363 entries.
2009/06/21 19:34:55|   Took 0.0 seconds (598162.9 entries/sec).
2009/06/21 19:34:55| logfileRotate: /var/log/squid/store.log
2009/06/21 19:34:55| logfileRotate (stdio): /var/log/squid/store.log
2009/06/21 19:34:55| logfileRotate: /var/log/squid/access.log
2009/06/21 19:34:55| logfileRotate (stdio): /var/log/squid/access.log

```

However, I do see some warnings like this periodically in cache.log:
```

2009/06/20 12:37:25| WARNING: Disk space over limit: 105600 KB > 102400 KB

```

I thought is was possible that the cache_dir variable was causing this somehow, so I increased the size of the cache_directory:
```

#Default:
# cache_dir ufs /var/spool/squid 100 16 256
cache_dir ufs /var/spool/squid 1000 16 256

```

but that didn't work -- squid -k rotate doesn't do anything.  I could set it up in logrotate but that is annoying since I also use sarg and want to generate reports right before a rotation is performed.

I'm not sure this belongs in Absolute Beginner Talk...

---

### Post by iponeverything on 2009-06-21
> However, I do see some warnings like this periodically in cache.log:

```

2009/06/20 12:37:25| WARNING: Disk space over limit: 105600 KB > 102400 KB


```

Looks like you partition is about to fill up. Increasing the cachedir var is not going to make your disk bigger ;)

What is the "df -h" tell you. And Why are running a squid server with a tiny 1 gig cache. (was a 100 megs??).

---

### Post by juancarlospaco on 2009-06-21
...OMG!, Beginner Talks are not so Beginner, LOL.
:)

---

### Post by vor_lord on 2009-06-22
> **iponeverything said:**
> Looks like you partition is about to fill up. Increasing the cachedir var is not going to make your disk bigger ;)
What is the "df -h" tell you. 

```

> df -h .
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              24G  2.5G   20G  11% /

```

The partition is not about to fill up.  The warning in cache.log is indicating that the cache itself has hit the limit configured in the cache_dir variable.  I can see how you were confused since it does say "disk space".

> And Why are running a squid server with a tiny 1 gig cache. (was a 100 megs??).

100 megs is the default setting, actually.  My squid server is intended to provide reporting of usage for my home network, not performance.  100 meg does the job just fine, as does the server (which is a small VirtualBox server).

---

### Post by iponeverything on 2009-06-22
> **vor_lord said:**
> ```

> df -h .
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              24G  2.5G   20G  11% /

```

The partition is not about to fill up.  The warning in cache.log is indicating that the cache itself has hit the limit configured in the cache_dir variable.  I can see how you were confused since it does say "disk space".



100 megs is the default setting, actually.  My squid server is intended to provide reporting of usage for my home network, not performance.  100 meg does the job just fine, as does the server (which is a small VirtualBox server).

My apologies. Squid serves very well in that role.

---

