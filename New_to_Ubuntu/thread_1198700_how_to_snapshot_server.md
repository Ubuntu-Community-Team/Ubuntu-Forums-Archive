---
title: "how to snapshot server"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by 007casper on 2009-06-27
Since I have server I would like to back up my whole system every two hours via snapshot.  I have checked several threads and cant decide on what is the best way to do this.

I have looked here for [backup]("http://ubuntuforums.org/showthread.php?t=1180122") but it isnt for mirror back up.

I need a mirror backup that can quickly be brought up, since it is important for the server stay on line. 

How can I create a snaphot of the whole system? And then use the snapshot for recovery if the hard drive fails.

There is sbackup, and then Grsync available via synaptic...

I also came across this for backuping files every three hours... but it isnt for the whole system [http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html](http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html)

any ideas?  Thank you so much!

---

### Post by philcamlin on 2009-06-27
> **007casper said:**
> Since I have server I would like to back up my whole system every two hours via snapshot.  I have checked several threads and cant decide on what is the best way to do this.

I have looked here for [backup]("http://ubuntuforums.org/showthread.php?t=1180122") but it isnt for mirror back up.

I need a mirror backup that can quickly be brought up, since it is important for the server stay on line. 

How can I create a snaphot of the whole system? And then use the snapshot for recovery if the hard drive fails.

There is sbackup, and then Grsync available via synaptic...

I also came across this for backuping files every three hours... but it isnt for the whole system [http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html](http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html)

any ideas?  Thank you so much!

id use rsync to backup

---

### Post by 007casper on 2009-06-27
I found this thread.  It discusses various backup options.  [http://ubuntuforums.org/showthread.php?t=868244&highlight=rsync]("http://ubuntuforums.org/showthread.php?t=868244&highlight=rsync")

clonezilla seems to be a good option also for cloning the server initially.

storebackup.org is that the same one as the one in synaptic... because they are different versions?  is storebackup have any gui?

I will appreciate if anyone will update this thread that discusses the best solutions to clone/backup your system in order to revert it back to the original state during emergencies for a server. Thank you.

---

### Post by 007casper on 2009-06-27
I was trying grsync.  I hooked up an external hard drive (hard drive is NTFS format)... picked the file system, and hit simulation.  I am getting bunch of errors... here is a short list 

> rsync: opendir "/etc/chatscripts" failed: Permission denied (13)
rsync: opendir "/etc/cups/ssl" failed: Permission denied (13)
rsync: opendir "/etc/ppp/peers" failed: Permission denied (13)
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(544) [sender=3.0.5]
rsync: writefd_unbuffered failed to write 78 bytes [generator]: Broken pipe (32)

I closed grsync, and then in terminal I did sudo su... and tried again. No luck. I was wondering if I could just do copy, paste.  I just wanted to back up the whole system before it went online for emergencies.

---

### Post by 007casper on 2009-06-27
All the errors I tried with grsync gives me permission errors.  How do I fix the permission errors? 

In this [thread]("http://ubuntuforums.org/showthread.php?t=868244&highlight=rsync") it is backing up without using grsync... since I am getting errors during simulation, I guess I could use root and apply the steps down below.  However, I prefer not use root unless I have to... any help will be appreciate it.  Thank you.

> cd /

create a file called exclude, and in this file put

tmp
proc
mnt
lost+found
sys
usr/backup

cd /usr && mkdir backup

cd /

rsync --delete-after -avz --exclude-from=exclude / /usr/backup/

your entire root filesystem EXCLUDING whats in the file exclude will be copied to /usr/backup/

The NEXT time you run this command, ONLY the changed files from / will be copied over, so the process takes a FRACTION of the time. Also, changes in the / filesystem will be deleted in /usr/backup (thats what --delete-after) does. In short, /usr/backup is a mirror of /

I would run this is rescue mode/root shell to minimize changes in the filesystem during the rysnc

then, cd /usr && tar cvpf backup.tar backup/ && gzip -9 backup.tar

Then move the backup.tar.gz to a safe place. Leave /usr/backup so you can run the command above to get only the changes to the system. Then tar and gzip once a week, delete old files, replace the new backup.tar.gz

Also, if you run rsync with the -n flag included it will MIMICK what it is going to do without doing it.

Then, you can play with your system, and run the above rsync command with -n to see what changes were made to the system BEFORE you started playing and reverse engineer everything.

Also, if you ever have to re-install after something horrible, re-install Ubuntu, grab the backup.tar.gz, place it in /usr and untar it. Then in /usr/backup run:

rsync --delete-after -avz --exclude-from=exclude /usr/backup/ /

and the system will be put back in place.

---

