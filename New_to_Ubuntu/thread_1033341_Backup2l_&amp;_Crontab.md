---
title: "Backup2l &amp; Crontab"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Adam AFC on 2009-01-07
Hi All,

right, i'm a complete novice, but have managed to setup backup2l, which is working a treat, however I just cant get my head around this crontab feature.

All I want is for my backup to run each night at 23:30, please could somebody point me in the right direction.

This what I have in my crontab -e
30 23 * * * backup2l --backup

Thanks in advance

---

### Post by unutbu on 2009-01-07
It might be the case that the crontab entry is failing because cron didn't know where to look to find backup2l. The solution is to set the PATH variable. 

cron runs commands in an environment with very few environment variables set by default.
The instructions below will give your cron jobs the basic environment variables.

Type 
```

crontab -e
```

and put something like this at the top of the file:
```

USER=adam
HOME=/home/adam
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/adam/bin
DISPLAY=:0.0
MAILTO=adam
```

Change 'adam' to your actual username.

For testing purposes, you might want to add an entry like this:
```

* * * * * backup2l --backup
```

so you don't have to wait until 11:30pm to see if it works.
Then type
```

watch -n 3 tail -n 10 /var/log/syslog
```

This will show you the last ten lines of /var/log/syslog, updated every 3 seconds.
Wait for the cron job to run and see what output you get. You should see something like this:
```

Jan  7 09:58:01 adam-desktop /USR/SBIN/CRON[10369]: (adam) CMD (backup2l --backup)
```

At least this would confirm that cron is running your job. 
If you are using Intrepid Ibex (8.10), then by default your system should be setup to receive mail from cron. If the backup2l job spits out any error messages, those messages will be mailed to the MAILTO user account. So once you confirm that cron is running your backup2l job, then if you still experience problems, look in your mail for error messages.

PS. Are you sure you can run backup2l as a normal user? If you are backing up system files, you might have to run the command as root, in which case you'd want to edit root's crontab, or /etc/crontab.

---

### Post by hyper_ch on 2009-01-07
I'd advice to put in the crontab only the path to a shell script and that shell script then hess the necessary infos to do the actual backup.

e.g. make a file:

/root/backup.sh

with the content
```

#!/bin/bash
backup2l --backup

```

and make it executable
```

sudo chmod 0755 /root/backup.sh

```

or if you run this as user, put it in an according directory and set path and chmod correctly.

---

