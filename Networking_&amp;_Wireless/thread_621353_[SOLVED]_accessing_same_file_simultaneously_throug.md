---
title: "[SOLVED] accessing same file simultaneously through samba"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by dave37 on 2007-11-23
Can more than one user or application access a file on an ext3 drive at the same time?  I have a machine in our soho, set up on dapper desktop, sharing one directory using samba with a number of files in it.  If a user was to write to a file in that directory while, in my case it was being backed up (using sbackup), would it potentially cause a problem?

Thanks

---

### Post by kidders on 2007-11-25
Hi there,

> **dave37 said:**
> Can more than one user or application access a file on an ext3 drive at the same time? Yes. The filesystem makes no difference ... all of them allow the same file to be opened simultaneously by more than one process.

> **dave37 said:**
> If a user was to write to a file in that directory while, in my case it was being backed up (using sbackup), would it potentially cause a problem?In theory, it can. The worst case scenario might be...
[LIST=1]
[*]The backup starts.
[*]A user (local or remote ... it doesn't matter) hits "Save".
[*]The application doing the saving empties the file being saved.
[*]The backup processes the empty file.
[*]The user's application writes out the file's new data.[/LIST]Some files are more likely to produce corrupted backups than others. For instance, anything database-like (eg email or music caches) is high-risk, because databases rely on concepts (like atomicity & serialisability) that no longer exist at the raw disk I/O level, and they tend to be written to relatively frequently. In theory, were a database to be backed up while a write operation is in progress, the backup will more than likely be unusable.

Normal practice in environments where file writes are frequent & unpredictable is to take *some* measures to improve the quality of a backup, without going overboard. In other words, unless you *realllly* can't afford to take even a theoretical risk, you should be prepared to tolerate some small degree of probability that any backup you take may not be completely perfect. For example:
[LIST]
[*]You could simply try to perform backups at quiet times.
[*]You might consider disabling remote access to files during a backup.
[*]You could make all shared files read only for the duration of a backup.
[*]You could back up file servers user by user, locking out one person at a time.[/LIST]Unless your network is very high-volume, the probability of a screw-up is not significant, especially if you have enough resources to store more than one backup at the same time. It's not likely that you need be concerned about this issue, but just to be 100% sure ...
[LIST]
[*][SIZE=1]What ballpark is the number of user accounts in? (100 ... 1,000 ... 100,000)[/SIZE]
[*][SIZE=1]How many tend to be accessing shared data at any given moment in time?[/SIZE]
[*][SIZE=1]Does that number vary significantly, depending on the time of day?[/SIZE]
[*][SIZE=1]What kind of data is being stored? (Images, SQL databases, music...)[/SIZE]
[*][SIZE=1]How much data is involved? (Megabytes? Gigabytes? Terabytes?)[/SIZE]
[*][SIZE=1]Is the data _critically_ important, or just very important? (ie: Are you taking precautions against fire, natural disasters, hardware failure, etc?)[/SIZE]
[*][SIZE=1]How frequent are write operations? (ie: Are your users software developers, for example? What is your policy on opening large files directly off the server, as opposed to making local copies first?)[/SIZE][/LIST]As you might imagine, only a tiny number of people will give the "wrong" answer to enough of these questions to cause a problem.

---

### Post by dave37 on 2007-11-25
Thank you so much for the insight.  It is only a small soho network, only 1 user will ever be accessing the files , and the only potential problem is the backup, if the user executes a save while it is backing up.  I have scheduled the backup, which is being done offsite in case of disaster or break in, for what should be an off hours period.  However, just to be safe, I would like to try your suggestion "You could make all shared files read only for the duration of a backup." 

This would probably work best as the user could still work on files in question, but would not be able to save them if a backup were underway, and could save the file to their local machine.  Could you provide info on how to do that?

Thank you

---

### Post by kidders on 2007-11-25
Hey again,

Ahh... I get the picture. :-) In your case, I would suggest two options:

**I - Simply switch off file sharing**[LIST]
[*]Your user opens a file.
[*]The backup starts.
[*]The user tries to save his file & fails.
[*]The backup finishes.
[*]The user says "Oh crap... what happened there?" and tries again.
[*]A second attempt at saving the file succeeds.
[/LIST]Naturally, that only works well if you're backing up something relatively small (ie 100s of megabytes, not 1,000s).

**II - What you suggested**
Since you're using Samba, you could extend your plan slightly, if you wanted to...[LIST=1]
[*]The backup starts by checking for open files. If it finds any, it sends messages to the remote user, asking him to save his work & go away.
[*]The backup script waits for up to 5 minutes for the user to release his files, before "chmod -r"-ing them.
[*]The script performs the backup, and returns the permissions to their original state. Alternatively, you could reconfigure the share to be read only (rather than the files themselves), by rewriting smb.conf, but since you'd have to restart Samba for such a change to take effect anyway, you might as well just leave it off for the duration of the backup, imo.
[/LIST]

Technically, ideas like these don't actually *prevent* bad things from happening, but can at least help. Does any of this help *you* though?

---

### Post by dave37 on 2007-11-25
As the files in question are relatively small (the entire directory that is being backed up compresses to an 8G file, your method** I ** sounds like it would be the easiest, however with Sbackup I don't know of any way other than cron to run a command prior to and after the backup.  (Prior to wouldn't be a problem, but since the run time for the backup always varies I couldn't schedule a post backup command).

Any tips?

Thank you.

---

### Post by kidders on 2007-11-26
Hmm...

I've never used sbackup, but if you poke around, you *may* find a config file, shell script or cron job you can alter to execute a post-backup command. I can imagine having problems executing things as root safely though.

Your idea of configuring a separate cron job seems like a nice solution. From what I've been able to gather about sbackup (from other peoples' posts on the subject), it seems to store a lock file (presumably in /var), which you could probably use as a way of monitoring the progress of a backup. Your cron job could work something like this...```
/etc/init.d/samba stop
while [ [COLOR="DarkOrchid"]... something ...[/COLOR] ]; do
     sleep 60
done
/etc/init.d/samba start
```

Hopefully, something obvious about sbackup's lock file will change once a backup finishes (eg it will be deleted). In that case, you could go for something along the lines of **while [ -f /var/lock/sbackup.lock ]**, so Samba would re-enable itself a maximum of 60 seconds after the lock file disappears.

Sorry I don't know the app you're using well enough to give a more definite answer to your question. Hopefully what I've suggested will work! If it were me, I would probably start the extra cron job a few minutes early, and use smbclient to send warning messages to active users, to say "The backup is about to start ... You have 2 minutes to save your work" or something.

Is that any help?

---

### Post by dave37 on 2007-11-26
That is most helpful!  I'm going to tinker around with it and see if I can get it going, and report back.

Thank you very much!
:KS

---

### Post by dave37 on 2007-11-26
Have my notification scripts working, problem is with the script example  provided.  When I run in a bash script:
```

/etc/init.d/samba stop
while -f /var/lock/sbackup.lock; do
     sleep 60
done
/etc/init.d/samba start


   
```  

I get a bash error that -f is not understood.  I've tried finding the correct switch to have it check for the existence of the lock file (that is the correct path, I double checked)  but so far no luck.

---

### Post by JKyleOKC on 2007-11-26
> **dave37 said:**
> Have my notification scripts working, problem is with the script example  provided.  When I run in a bash script:
```

/etc/init.d/samba stop
while -f /var/lock/sbackup.lock; do
     sleep 60
done
/etc/init.d/samba start


   
```  

I get a bash error that -f is not understood.  I've tried finding the correct switch to have it check for the existence of the lock file (that is the correct path, I double checked)  but so far no luck.

You left out the square brackets, which are actually the bash "test" command. Add them as in the original post and it should work.

---

### Post by dave37 on 2007-11-26
Doh!  Thanks!  I've got it all working now, I'll post back the details in case anyone else finds it useful.

---

### Post by dave37 on 2007-11-26
Thank you so much Kidders and JkyleOKC.  It is now all working.  Here is what I did with your suggestions and help, in case it helps anyone else.

Backup job is scheduled to run at 23:00 every night.  I use Sbackup which doesn't have any pre or post command running ability.  My concern is that user will write to file being backed up causing data loss.  So, with Kidder's help I found that sbackup creates a lock file in /var/lock/sbackup.lock.  So I created the following script I named sambawarning:
```

#!/bin/bash
#calls the text file that contains the warning you want to appear on the client machine(s)

cat /*path to file*/userwarning.txt | smbclient -M *insert networkcomputername*
cat /*path to file*/userwarning.txt | smbclient -M *insert networkcomputername*

#interval in seconds between first and final warning
sleep 300

#calls the text file that contains the file warning you want to appear on the client machine(s)

cat /*path to file*/finalwarning.txt | smbclient -M *insert network computername*
cat /*path to file*/finalwarning.txt | smbclient -M *insert network computername*

```

Please modify for your usage.  The text files contain whatever you'd like.  In my case userwarning has something like !!!!WARNING!!!! Backup scheduled in 10 minutes, please save all open files NOW!  That'll get the wife's attention.

The sleep 300 means it waits for 300 seconds and then the user gets a popup which now warns them of imminent disaster if they don't hurry up and save their files.

So we've taken care of getting the user's attention.  I used gnome-schedule, you can use cron at the command line if you'd like, and created a cron job of *bash /path to script/sambawarning* set to run 10 minutes before my backup is scheduled to begin.So we've taken care of getting the user's attention.

Now we want to shut down samba on the machine that is backing itself up.  It's a bit brute force but I'm only running a soho network and it works. I modified Kidder's script  slightly, probably using the wrong way to do it, I'm no programmer, but it works. I named it sambalockout

```

#!/bin/bash
sleep 15
/etc/init.d/samba stop
while [ -f /var/lock/sbackup.lock ]

do     sleep 60

done

/etc/init.d/samba start

```
What this does  is wait 15 seconds (you'll see why later), then stop Samba, then checks to see if the sbackup lockfile is present (if sbackup is running, it will be).  If the sbackup.lock file is present due to sbackup running, it comes back in 60 seconds to check again.  Once sbackup completes it's backup run, the sbackup.lock file is erased, and so then the script starts samba up again.

So having used cron (or gnome-schedule) to issue the warnings to the users now I created a cron job for sambalockout *bash /path to script/sambalockout* and set it to run at the same time as my backup, in this case 23:00.  Now the sleep 15 in the sambalockout script means that it waits 15 seconds to execute itself, which will give time for sbackup to have created the sbackup.lock file,  our script shuts down samba, finds the sbackup.lock file exists, and keeps waiting until sbackup.lock is gone (backup is completed) and then it will start samba again.

So what happens is that at 22:50 my wife gets a popup telling her to hurry up and save her work, 5 minutes later (300 seconds) she gets another more urgent popup, and then at 23:00 she is locked out of the file during the backup.

If you need to send popup messages to a machine running XP read here:
[http://support.microsoft.com/kb/839018](http://support.microsoft.com/kb/839018)

And to allow a Ubuntu machine to receive a popup you need to make sure the following line, without a ; in front of it, is in your /etc/samba/smb.conf

```

message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

```

And you will need to install linpopup to be able to see the warnings from an Ubuntu machine--if anyone can come up with a better messager that will work, please post.

---

