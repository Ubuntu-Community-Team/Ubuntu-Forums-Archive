---
title: "automatic backup of evolution settings"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-08-16
Hi Community:

I use Evolution for my email and want to do scheduled backups of its settings each week without opening evolution and going to file > backup settings.

Specifically, I want to set up a shell script that I can run weekly and automatically with crontab that will do the backup.

[COLOR="DarkGreen"]**Can anybody tell me how I might write that script, or how to get started writting it?**[/COLOR]

Thanks! :)
Phil Smith
Duluth, GA

---

### Post by jacob.david on 2010-09-20
When you backup on evolution it actually backs up your complete .evolution folder (usually under the home folder). You can set your crontabs to back up this folder and do whatever you want with it. 

A sample command is given below, which you can add to the cron tabs.

tar zcfv evolution.tar.gz .evolution

Good Luck.

---

### Post by dcsoldschool53 on 2010-09-20
> **Phil Smith said:**
> Hi Community:

I use Evolution for my email and want to do scheduled backups of its settings each week without opening evolution and going to file > backup settings.

Specifically, I want to set up a shell script that I can run weekly and automatically with crontab that will do the backup.

[COLOR="DarkGreen"]**Can anybody tell me how I might write that script, or how to get started writting it?**[/COLOR]

Thanks! :)
Phil Smith
Duluth, GA
There is a program that you can use to schedule backups. It is called gnome-schedule. Just run this command in the terminal:

```
sudo apt-get install gnome-schedule
```

This website has information about it.
[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)

---

### Post by xyepblra on 2011-09-01
I'd like to bump this thread with an idea, which is to write a shell script that would be executed by a crontab task:
```
* 17 1,2,3,4,5,6,7 * 5 ~/.my_custom_scripts/evo-bu/evo-bu.sh
```
meaning that I'd like this script to be executed at 5 pm first Friday of every month.
Content of the ~/.my_custom_scripts/evo-bu/evo-bu.sh shell script is as following:
```
#!/bin/sh
if [ -f "/media/data/backups/mounted" ]
then
$notify-send 'Evolution backup started' 'Do not run Evolution now'
$gconftool-2 --shutdown $evolution –force-shutdown
$cd
$tar -cvzf /media/data/backups/lucid/evolution-backup.tar.gz .evolution .gconf/apps/evolution
else
notify-send 'Evolution backup failed' 'The backup target volume likely unmounted'
fi
exit 0
```Thus, my purpose is to make the script to backup all the Evolution data and settings and send a notification to be displayed on the screen.
Then, in the terminal:
```
sudo a+x ~/.my_custom_scripts/evo-bu/evo-bu.sh
```
Since I'm a newby in this field, I'm not sure my compilation of the script code is correct and executable as supposed. Please correct me where I'm wrong.

---

