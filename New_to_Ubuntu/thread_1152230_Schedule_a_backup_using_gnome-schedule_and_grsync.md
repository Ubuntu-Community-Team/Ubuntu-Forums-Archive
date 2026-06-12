---
title: "Schedule a backup using gnome-schedule and grsync?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-05-07
Quick and easy question hopefully.

I have been using grsync to synch and backup my media library. Ideally I'd like to automate this task. Is it possible using the gnome-scheduler? 

The task scheduler asks for a command to run at the scheduled time. I dont know where to start...

---

### Post by coffeeaddict22 on 2009-05-07
Haven't used grsync but...
If you right click on Applications, choose Edit Menus, then work your way down to grsync, and choose properties, you'll see the command used to start the program.  That'll be the one to give to the scheduler, along with the information it needs to automatically back up.

---

### Post by badrunner on 2009-05-07
> **aquascrotum said:**
> Quick and easy question hopefully.

I have been using grsync to synch and backup my media library. Ideally I'd like to automate this task. Is it possible using the gnome-scheduler? 

The task scheduler asks for a command to run at the scheduled time. I dont know where to start...

By the name, i would assume grsync is a front-end to the command line rsync tool. If you could somehow weasel out the actual rsync command your backup uses, or, with more patience learn how to reconstruct the same command by reading the rsync man page ("man rsync" at a terminal), you could then schedule it using the gnome-scheduler as you asked, or using the cron daemon, again this would require a bit of research and learning some command line on your part, but would be a very good solution, and work well even if you transferred to a headless media server. 

Heck with a bit of programming research, you could probably take the output from rsync and generate dbus events that could be tied to a little gui (status icons in pygtk are pretty easy) to show you progress/history of backups when you are logged in to a desktop, but using that solution your backups would continue even when not logged in.

---

### Post by MrWES on 2009-05-07
> **aquascrotum said:**
> Quick and easy question hopefully.

I have been using grsync to synch and backup my media library. Ideally I'd like to automate this task. Is it possible using the gnome-scheduler? 

The task scheduler asks for a command to run at the scheduled time. I dont know where to start...

Not sure on the ownership on your media files, I'm assuming you the user owns them. So I would setup a cron job to use rsync to back it up. So first let's set your default text editor to nano, instead of vi:
From a terminal type:
```
sudo update-alternatives --config editor
```
Chooose option 3 for nano.

Now, if the media files are owned by you, from a terminal type:
```
crontab -e
```
and enter something similar to this, edit according to your needs:
```
# Weekly backup of Documents on external drive to /data/backup
30 3 * * 0 rsync -av --delete --progress  /media/external/Documents /data/backup

```
Exit the file with a ctrl + X and Y to to save.

This cron job will backup my /media/external/Documents every week, on Sunday, at 3:30am to /data/backup 

Now if you need root permissions on the files you are backing up, type:
```
sudo crontab -e
```
to edit root's cron and use the same procedures as above.

Good Luck!

~Bill

---

