---
title: "How do I autorun a shell script?"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by ironic.demise on 2010-10-21
How can I set a shell script i.e. backup.sh at certain times, such as... 8:00 every day?

---

### Post by AngusH on 2010-10-21
I believe you would need to look into cron and crontab (or maybe anacron instead depending on your needs). However I personally am not exactly an expert in these so I will let someone else post to explain how you use them. Sorry.
Angus

---

### Post by CharlesA on 2010-10-21
Cron would get the job done. :)

See [here]("http://adminschoice.com/crontab-quick-reference") for some info.

---

### Post by ironic.demise on 2010-10-21
Thanks AngusH and CharlesA.
Looking into Cron, Crontab and Anacron and looks like what I need.
 
Will these all run as root or as the logged in user (i.e. me)
Will they also take user input
so:
```

echo backupdir
read backupdir
cp -r /home/user $backupdir

```
 
Will produce a terminal window that asks for a backup directory?
I also want this command to NEVER run under any user other than my own, (symlink to shell script in my home directory with r/w/x permissions set to only myself? or set cron to go into my user directory, if it IS run as root... though root would ignor file perms? maybe edit the file to contain an IF $USER=myself)

---

### Post by CharlesA on 2010-10-21
If you are just backing up your own files, it can run as your user.

Do you want it to prompt for the user to enter a backup directory?

---

### Post by ironic.demise on 2010-10-21
Something similar to that.
I want it to backup only my files and to only run if it is me that is logged in.
I do need it to prompt for somethings, that script was just a quickie but I intend the real one to allow backing up, but to ask me to name a new directory.
 
:edit:
If I just run cron without sudo and as myself, will I be able to add my script only for me?
 
(can't test right now, I'm at a public computer running WinXP)

---

### Post by CharlesA on 2010-10-21
You can just add it using ***crontab -e***  without using sudo.

I'm not sure if it'll prompt you for a directory or not, unfortunately.

The way I have mine setup, it does a backup to the same folder nightly, but then I don't have it set to prompt for me to enter what directory I want it to use.

---

### Post by ironic.demise on 2010-10-21
> **CharlesA said:**
> You can just add it using ***crontab -e*** without using sudo.
 
I'm not sure if it'll prompt you for a directory or not, unfortunately.
 
The way I have mine setup, it does a backup to the same folder nightly, but then I don't have it set to prompt for me to enter what directory I want it to use.
 I think I have everything I need now, With this I'm confident I'll be able to get it to prompt daily to me and only me.
 
Your advice was much appreciated, Seriously I don't know how some of the guys around here manage to have such a broad knowledge.

---

### Post by CharlesA on 2010-10-21
Being curious and bashing yer head into the desk a few times when stuff isn't working.. kinda helps. :P

---

### Post by ironic.demise on 2010-10-21
Aha yeah, well I think I've suffered from curiosity as much as any new 'buntu user.
I think most people have had that moment where they realize that maybe they should have just left it aha.
 
Thanks for the help.

---

### Post by sgosnell on 2010-10-21
Constantly breaking stuff, then fixing it, is a pretty good teacher.  One of the things you learn doing this is to have multiple backups of everything.  :)

I'm not sure why you want to have a prompt for a directory every time.  It would seem to be easy enough to back up to a temp directory, then move the tar whenever it's convenient.  But it's your system, so do it however you like.

---

### Post by trikster_x on 2010-10-21
Because crontab runs everything silently, you would need to develop a GUI script that would open a window to ask for user input if you want to specify a directory.

---

### Post by AngusH on 2010-10-21
GUI isn't that difficult if your running in ubuntu. Just use zenity for simple programs. Check the manpage for info (it's all pretty simple).

---

### Post by ironic.demise on 2010-10-21
It's not specifically backupdirectories that I need prompting for, that was just a hypothetical thing.

And yeah I think a lot of people learn to keep backups the hard way.

---

