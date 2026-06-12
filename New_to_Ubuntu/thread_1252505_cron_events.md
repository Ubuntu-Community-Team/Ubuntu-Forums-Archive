---
title: "cron events"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by expatCM on 2009-08-28
I read that cron has a range events set up with a normal desktop install.

I also read that cron has the default setting to run these events at 04:00.

In common with many other users, my desktop is always shut down at that time.  Should I do something about the cron standard execution time?  

I can see some events in the various /etc/cron.time directories but I cannot see where the time is scheduled.  Where is this setting to be found please?

---

### Post by ptn107 on 2009-08-28
The times for each of those folders are set in /etc/crontab.

---

### Post by expatCM on 2009-08-29
Ah ... crontab ....  yes, just taken a look and I do see the times that the events run.  Nothing is a problem for my system there.  Thanks for pointing me in this direction.

But ...  one thing I do not quite grasp now ... I just installed a program called Gnome Schedule which I thought was a gui for cron.  I have set up an event there and expected it would appear in the crontab list but it does not.  Is there another file I should be looking at?

---

