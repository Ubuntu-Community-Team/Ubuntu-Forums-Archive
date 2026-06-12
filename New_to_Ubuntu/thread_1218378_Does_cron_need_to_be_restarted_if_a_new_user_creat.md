---
title: "Does cron need to be restarted if a new user creates a crontab?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by RavUn on 2009-07-20
On a box, that I don't have root access to, I added a job to my crontab to run every hour.  So far it doesn't appear to be running (if it is then I'm not getting an email and I don't have root access to the logs) but the databases that my script is supposed to update has not been updated.  I don't know for sure if it's due to an error or if it's just because the cron job's not running.

My user hasn't used crontab previously and I just did today:
```
crontab -e
```
and added my job (and a MAILTO variable).

If I do ps aux | grep crond then I see:
```
root      3282  0.0  0.1 57216 1072 ?        Ss   Jul07   0:00 crond
htiadmin 20886  0.0  0.0 51092  672 pts/1    R+   15:08   0:00 grep crond

```

Can somebody tell me if I need to do something to get my own cron job running?  Does the entire cron service need to be restared, or is there something I can do with my own user?

---

### Post by slakkie on 2009-07-20
No, if you created it with the crontab command then you don't need to restart it. If you directly added a crontab file (believe /var/spool/crontabs - or is that solaris.. mmm), then you need to restart crontab.

Maybe something wrong with your script/crontab entry. Care to share?

---

