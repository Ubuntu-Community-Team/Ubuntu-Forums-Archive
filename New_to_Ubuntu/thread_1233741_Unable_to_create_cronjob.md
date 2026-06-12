---
title: "Unable to create cronjob"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by AncientPC on 2009-08-07
I try `crontab -e` it opens an empty file that I cannot save the file.

When I run `crontab -l` I already have something in my crontab (Ubuntuzilla checking for Firefox updates).  I ran `crontab -r` to remove it successfully.

I try to edit my crontab again but can't.  I then create /etc/cron.allow and add my username in there.  I still can't create a crontab.  Any more ideas?

---

### Post by credobyte on 2009-08-07
Can you create a crontab for root ( [COLOR=DimGray]sudo crontab -e[/COLOR] ) ?

---

### Post by wizard10000 on 2009-08-07
> **AncientPC said:**
> I try `crontab -e` it opens an empty file that I cannot save the file.

When I run `crontab -l` I already have something in my crontab (Ubuntuzilla checking for Firefox updates).  I ran `crontab -r` to remove it successfully.

I try to edit my crontab again but can't.  I then create /etc/cron.allow and add my username in there.  I still can't create a crontab.  Any more ideas?

JMO but I never use a user's crontab for systemwide actions - I put everything in /etc/crontab - you might find that a little easier.  Format is exactly the same except you have to add the name of the user who's running the job.

```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# default Ubuntu stuff

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

# Usenet stuff

#
0 1 * * * wizard pan --no-gui headers:alt.dbs.echostar >> /var/log/cron-output.log 2>&1
15 1 * * * wizard pan --no-gui headers:alt.os.linux.ubuntu >> /var/log/cron-output.log 2>&1
30 1 * * * wizard pan --no-gui headers:alt.binaries.sounds.mp3.jazz >> /var/log/cron-output.log 2>&1
45 1 * * * wizard pan --no-gui headers:alt.binaries.sounds.mp3.complete_cd >> /var/log/cron-output.log 2>&1

# backup stuff

#
0 0 * * * wizard dpkg --get-selections > /home/wizard/Documents/installed-programs.log 
15 0 * * * wizard sh /home/wizard/scripts/grab-forum-archive.sh >> /var/log/cron-output.log 2>&1
0 2 * * * root mount -t smbfs -o username=wizard,password=xxxxxxxx //192.168.1.103/documents$ /home/wizard/mrs-wiz-pc >> /var/log/cron-output.log 2>&1
15 2 * * * wizard sh /home/wizard/scripts/rsync_backup.sh >> /var/log/cron-output.log 2>&1
0 4 * * * root umount /home/wizard/mrs-wiz-pc >> /var/log/cron-output.log 2>&1
```

---

### Post by nanotube on 2009-08-07
> **AncientPC said:**
> I try `crontab -e` it opens an empty file that I cannot save the file.

When I run `crontab -l` I already have something in my crontab (Ubuntuzilla checking for Firefox updates).  I ran `crontab -r` to remove it successfully.

I try to edit my crontab again but can't.  I then create /etc/cron.allow and add my username in there.  I still can't create a crontab.  Any more ideas?

hi, couple of things to check:

is there a /etc/cron.deny? 

what are the permissions on /var/spool/cron/crontabs/yourusername ? (need to be root to check on that). should be owned by yourusername:crontab, and have 600 permissions.

---

### Post by AncientPC on 2009-08-07
I'm at work so I can't check everything.

- There is no /etc/cron.deny.
- I can create a cronjob as root.

Once I get home I'll double check permissions and look into editting /etc/crontab directly.

---

### Post by unutbu on 2009-08-07
There is another way to edit the crontab:

Just save the crontab in a plain text file, say, ~/mycrontab

Then run
```

crontab ~/mycrontab
crontab -l
```

Either it will work, or it perhaps spit out an error message which might be helpful.

---

### Post by AncientPC on 2009-08-08
I went home and restarted my laptop.  Without changing anything, I was able to write / save to the crontab, go figure. -_-

---

### Post by nanotube on 2009-08-08
> **AncientPC said:**
> I went home and restarted my laptop.  Without changing anything, I was able to write / save to the crontab, go figure. -_-

just love it when a problem solves itself. :)

---

### Post by AncientPC on 2009-09-11
> **unutbu said:**
> There is another way to edit the crontab:

Just save the crontab in a plain text file, say, ~/mycrontab

Then run
```

crontab ~/mycrontab
crontab -l
```

Either it will work, or it perhaps spit out an error message which might be helpful.
I was running into this problem on another machine and this workaround solved the issue.

---

### Post by xyepblra on 2011-01-28
I have a problem editing the crontab, and it doesn't solve itself, unfortunately...
I press Ctrl+Alt+F1, enter user name, enter password, successfully log into shell, enter "crontab -e" and enter my current version of crontab. What's wrong (at least unexpected) is that when I press Backspace trying to erase a number or a symbol, the cursor moves left, but nothing is being actually erased. Precise instructions (fool-proof preferrably) will be highly appreciated.

---

