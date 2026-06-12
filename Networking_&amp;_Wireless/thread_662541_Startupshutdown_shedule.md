---
title: "Startup/shutdown shedule"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by Reeva on 2008-01-09
Hello,

I've made a little server here, and now I want a little shedule for this server regarding startup and shutdown times.

For example, startup at 08:00am and shutdown 16:00pm.

Is that possible to do? Or how can I do it?

Thank you very much

---

### Post by Reeva on 2008-01-09
I manged to get it starting each day at a certain hour using my bios.

But I didn't find how I can shutdown it each day at a certain hour?

I installed gnome-schedule .. But this doesn't really work. When I use the command " shutdown now -h" I need to use root.

So " sudo shutdown now -h" does require user interaction?

Thank you

---

### Post by jords on 2008-01-09
Hi

Cron should do this fine.

Here is a cron howto: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

In this case you want to add a shutdown -h now to the root crontab, so:
```
sudo crontab -e
```

Then add the following line to the bottom of the file:
```
00 16 * * * /sbin/shutdown -h now
```
and save the file.

That should work.:popcorn:

Jords

---

### Post by Reeva on 2008-01-09
Thank you very much, this works fine for me ;)

---

