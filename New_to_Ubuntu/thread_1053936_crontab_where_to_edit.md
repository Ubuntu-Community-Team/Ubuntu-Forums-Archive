---
title: "crontab where to edit"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by SBFree on 2009-01-29
I need to set a cron command to have a wiki program send email once a day. I have the command but I am not sure where to place the crontab file. There is a crontab owned by root in /etc and an empty folder called crontabs in /var/spool/cron/. Almost all the wiki files are owned by apache rather than me as the user. Are there multiple crontab files, like one for each user or just one system crontab file owned by root that does whatever it needs to be done? I tried creating a test command with the gui interface, Schedule, but the crontab file at /etc didn't seem to change.
Thanks in advance for any replies.
Scott

---

### Post by ptviperz on 2009-01-29
sudo crontab -e will choose the root crontab, there are separate crons for each user.

---

### Post by SBFree on 2009-01-29
If I edit the root crontab will that carry out commands for any user?
Thanks!

---

### Post by hyper_ch on 2009-01-29
it will carry them out as root user.

I don't like to edit the crontab file directly. I prefer making a cron.txt file, save the commands in there and add that file to cron:
```

crontab cron.txt

```
or a specific user:
```

sudo crontab -u USER cron.txt

```

and list it:
```

crontab -l

```
or for any user:
```

sudo crontab -u USER -l

```

---

### Post by larry007 on 2009-01-29
> **ptviperz said:**
> sudo crontab -e will choose the root crontab, there are separate crons for each user.

Hi, its never a good idea to edit the cron file directly.  Use the commands intended!

*crontab -l *   lists cron jobs for user
*crontab -e *   allows editing/add new cron jobs

If you want the root user to perform the task, simply put '*sudo*' prior to either command.

---

### Post by SBFree on 2009-01-29
Thank you all for the help.
The process I want to run is a perl script called **mailnotify**. It exists in  **/var/www/twiki/tools** and is **owned by user www-data**. How do I figure out where to put a crontab file for this user? 
Thanks, Scott

---

