---
title: "Auto Shutdown for child user accounts"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by mx32 on 2011-03-01
How can I schedule a recurrent task to shutdown the computer for a user without administrative privileges? (Some times my child leaves the computer on)

I have tried gnome-schedule with the command:
/sbin/shutdown -h now

It works fine for root user, but does not work under a no administrative user. 
I have also tried running gnome-schedule with the command:
gkus gnome-schedule 
this way, it is suppose to allow me to add tasks to other users, but it only allows not recurrent tasks.

Running "gkus gnome-schedule" from my child account does not work either

So, what's the advice? I have Ubuntu 10.04 

Thanks

---

### Post by aeiah on 2011-03-01
gnome-schedule is a graphical front end for crontab, which in its self is fairly easy to use. 

normally you'd use root's crontab to issue the shutdown command, as you talk about. does this not work? or are you looking for a way to shutdown if he's logged on but not if you're logged on?

---

### Post by wizard10000 on 2011-03-01
Personal preference, but I prefer not to put systemwide tasks in anyone's crontab, not even root's - I prefer to edit /etc/crontab instead.

There are at least two ways to do this.  You can do it in /etc/crontab or you can do it in /etc/rc.local - whichever you prefer.  Either will have to be edited as root.

Let's say you wanted to power down the machine at 10pm every night.  To do it in /etc/crontab you'd do it like this -

```
* 22 * * *   root   shutdown -P now
```

If you wanted to shut the machine down at different times (say the kids have a later curfew on the weekend) /etc/crontab would be the way to do it.

In /etc/rc.local (which would be my preferred method since it's easy to cancel) you'd do it like this -

```
shutdown -P 22:00
```

If you wanted to you could cancel a scheduled shutdown called from rc.local with

```
sudo shutdown -c
```

but this wouldn't work with an immediate shutdown scheduled as a cron job.

You could also do the scheduled shutdown with "at" but that wouldn't be much fun at all and would be a little more difficult to cancel.

Hope this helps -

---

### Post by mx32 on 2011-03-02
> **aeiah said:**
> gnome-schedule is a graphical front end for crontab, which in its self is fairly easy to use. 

normally you'd use root's crontab to issue the shutdown command, as you talk about. does this not work? or are you looking for a way to shutdown if he's logged on but not if you're logged on?

Yes, I am looking for a way to shutdown when he is logged.

---

### Post by mx32 on 2011-03-02
@wizard10000
This appear to be what I'm looking for. Thanks. I will try it tomorrow. :)

---

### Post by mx32 on 2011-03-04
I did try crontab with the code:

* 22 * * *   root   shutdown -P now

Worked perfectly. Now the computer will shutdown even if my kids forget to turn it off.
Thanks

---

### Post by wizard10000 on 2011-03-04
You're more than welcome.  Glad to be of service  :)

---

