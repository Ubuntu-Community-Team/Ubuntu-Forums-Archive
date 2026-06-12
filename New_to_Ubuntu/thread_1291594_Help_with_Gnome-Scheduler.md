---
title: "Help with Gnome-Scheduler"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-14
I've created a crontab with Gnome scheduler.

The command works fine in Terminal.

Nothing happens at the set time in Gnome-Scheduler.

If I go in Gnome-Scheduler and run the task manually, it works fine (although asks me for a couple of prompts first "*Are you sure you want to run this task now"* and 

[I]Note about working directory of executed tasks:

Recurrent tasks will be run from the home directory, one-time tasks from the directory where Gnome schedule was run from at the time of task creation (normally the home directory).[/I]

I click OK & it runs fine.

Does anyone know what's happening?

The task is **cd /home/username/torrents;btdownloadgui.bittornado movie.torrent**

---

### Post by smileyguy on 2009-10-14
I should add that although the task doesn't appear to run, it disappears from the list of scheduled tasks in Gnome-Schedule!

---

### Post by Insperatus on 2009-12-02
Exactly the same problem here.

---

### Post by Kruptein on 2009-12-03
Same problem here,
I even tried it with sudo crontab
instead of gnome schedudler,
but none of them is working AAAH!!!

---

### Post by atoztoa on 2009-12-04
First, don't use *sudo* for *crontab*...

Second, check the deny and allow files

```
/etc/cron.allow 
/etc/cron.deny
```
Third, use ```
crontab -e
```Fourth, for running GUI applications, use something like this...

```
00 06 * * * env DISPLAY=:0 gui_appname
```
...the *env DISPLAY=:0* tells cron to run on top of the current desktop...

Fifth, for running GUI applications in Karmic, enable X ACL also...

```
 ~$ xhost +local:
non-network local connections being added to access control list
 ~$ xhost
access control enabled, only authorized clients can connect
LOCAL:
...
```

Reference: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

_ATOzTOA
[www.atoztoa.com](www.atoztoa.com)

---

