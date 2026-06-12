---
title: "Scheduled updates?"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-07
[FONT=Arial]Can I schedule my updates to be downloaded (and installed) at a certain time (i.e., 3am during my ISP 'off peak' download time)?[/FONT]
 
Can anybody tell me how?

I'm using 9.04

---

### Post by nothingspecial on 2009-10-07
Have a look at [[COLOR="Magenta"]crontab[/COLOR]]("https://help.ubuntu.com/community/CronHowto")

---

### Post by smileyguy on 2009-10-07
so no gui for dumb Windows users?

---

### Post by Cheezespread on 2009-10-07
May be [this]("http://gnome-schedule.sourceforge.net/") would help you.

```
sudo apt-get install gnome-schedule
```

[Ubuntu-geek's]("http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html") how to on the same.

---

### Post by 3rdalbum on 2009-10-07
> **smileyguy said:**
> so no gui for dumb Windows users?

```
sudo apt-get install gcrontab
```

You still need to get it to run the commands:

```
sudo apt-get update && sudo apt-get dist-upgrade -y
```

As you can tell by the look of it, it's not the most friendly program, but it gets the job done.

Alternately your ISP might run a free Ubuntu mirror - mine does, so as long as my Software Sources is set to the location of my ISP's Ubuntu mirror, all Ubuntu updates are free and unmetered.

---

### Post by smileyguy on 2009-10-07
Thanks 3rd album & cheesy.

Installed the scheduler and yes my isp provides a free mirror (forgot about that from last time i played around with ubuntu).

I'll give both methods a go just for the fun of it:)

---

### Post by smileyguy on 2009-10-07
This seems to be working

[http://bigtrev.blogsome.com/2009/01/10/iinet-ubuntu-mirrors/](http://bigtrev.blogsome.com/2009/01/10/iinet-ubuntu-mirrors/)

---

### Post by smileyguy on 2009-10-07
Thanks 3rdalbum - One question - If I do set it to schedued tasks, won't it still ask me for the root password?

---

