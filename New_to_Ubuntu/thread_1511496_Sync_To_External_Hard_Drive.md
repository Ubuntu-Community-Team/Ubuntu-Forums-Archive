---
title: "Sync To External Hard Drive"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by wingrider78 on 2010-06-16
I would like to know if there is a way to have files sync'd between two locations.  I just purchased a 1TB external usb drive and want to backup my pics, vids, music, etc to it from my home folders.  Is there a program that will automatically keep the external drive updated with the newest versions of whatever files I have in my home directory???  I have the external formatted to FAT32 (needs to be used in windows too) and I am running Lucid on the pc.  Any help is appreciated.

---

### Post by Chesamo on 2010-06-16
You can set a cron entry to ```
cp ~/ /media/externaldrive
```

---

### Post by anglican on 2010-06-17
> **wingrider78 said:**
> I would like to know if there is a way to have files sync'd between two locations.  I just purchased a 1TB external usb drive and want to backup my pics, vids, music, etc to it from my home folders.  Is there a program that will automatically keep the external drive updated with the newest versions of whatever files I have in my home directory???  I have the external formatted to FAT32 (needs to be used in windows too) and I am running Lucid on the pc.  Any help is appreciated.
Using cp is horribly inefficient as everything gets copied - whether it's changed or not. Instead use rsync and cron. To edit your crontab file:

```
crontab -e
```then add an entry:
```
# backup everything in my home directory everyday at 5 past midnight
5 0 * * * /usr/bin/rsync -az /home/myname/ /media/externaldrive

```You can run this command more frequently if you like, rsync only backs up changed files and then only the bit of the file that's changed, so after the first run it shouldn't take much time.

H

---

### Post by mapes12 on 2010-06-17
> Instead use rsync+1

I use Grsync as it's a GUI interface for rsync. It's in Synaptic and loads the rsync as a dependancy. I do a manual backup with it once a week to an external HDD. After the initial backup Grsync runs in less than 2 minutes on my machine.

For the partitioning my choice would be to have FAT (or whatever you want for windoze) one one partition and another partion with EXT (Version that suits your hardware. I use 3 cos this is old) for the Ubu backup.

---

### Post by wingrider78 on 2010-06-17
Thank you for the quick responses.  I just played around with grsync and like the tool very much.  I will have to look into the crontab lingo to tweak when I want things to happen.  I'm sure I will be able to make it happen more often or less often depending on the folders.  Also, when I enter the code into the crontab file as anglican has suggested, can I just add more lines underneath for more directories to backup???

Also, what would be the best filesystem to have on this drive to share the data between windows/linux machines.  I use linux on all my pcs, but have winxp in a virtualbox on them, but also take my files with me when I travel and sometimes need to use windows pcs elsewhere...

---

### Post by mike555 on 2010-06-17
You might want to try "Lucky Backup " .

---

### Post by roger_1960 on 2010-06-17
Hi

Also look at sbackup in the repos.  It has a GUI and can be scheduled to backup whatever folders you want whenever you like - very flexible and easy to use.  FAT32 for partition format gives the most flexibility across platforms.

---

### Post by anglican on 2010-06-17
> **wingrider78 said:**
> Thank you for the quick responses.  I just played around with grsync and like the tool very much.  
Grsync is a nice gui for rsync which has some useful features and does simplify its use. Personally I prefer CLI, probably because I'm an old-dog that can't learn new tricks. 
> **wingrider78 said:**
> I will have to look into the crontab lingo to tweak when I want things to happen.  I'm sure I will be able to make it happen more often or less often depending on the folders.  Also, when I enter the code into the crontab file as anglican has suggested, can I just add more lines underneath for more directories to backup???
Yes, you can have as many crontab entries as you like, though it's best to change the time for each so they don't all try to run at once. The crontab format is really very simple, it's just:

```
field          allowed values
-----          --------------
minute         0-59
hour           0-23
day of month   1-31
month          1-12 (or names, see below)
day of week    0-7 (0 or 7 is Sun, or use names)
```

an "*" means "every" so in my example of "5 0 * * *" it's 5 minutes after 0 (midnight) on every day of every month.

> **wingrider78 said:**
> Also, what would be the best filesystem to have on this drive to share the data between windows/linux machines.  I use linux on all my pcs, but have winxp in a virtualbox on them, but also take my files with me when I travel and sometimes need to use windows pcs elsewhere...
Personally, when I'm using a portable hard-drive (I have a couple) I usually use ntfs if I'm going to be using it with Windows machines also.

H

---

### Post by wingrider78 on 2010-06-17
Anglican, thank you for your help.  I have set up a test with the crontab file and it worked beautifully.  My only issue is that when I entered

crontab -e

to edit the file, it said that there wasn't a crontab file and was creating one.  when I entered my instructions and saved, it is saving in a /tmp directory.  is there a better place for this to be stored and have it still run when i want it to.

---

### Post by anglican on 2010-06-18
> **wingrider78 said:**
> Anglican, thank you for your help.  I have set up a test with the crontab file and it worked beautifully.  My only issue is that when I entered

crontab -e

to edit the file, it said that there wasn't a crontab file and was creating one.  when I entered my instructions and saved, it is saving in a /tmp directory.  is there a better place for this to be stored and have it still run when i want it to.
No, it's actually stored in /var/spool/cron/crontabs/myusername which is in a directory (crontabs) that has drwx-wx--T permissions and owner/group: root/crontab to prevent you editing it by any means other than "crontab -e". The copy in /tmp is made when you run "crontab -e" to enable you to edit the file but is not the version used by cron. You can use "crontab -l" to list the contents of your crontab.

H

---

### Post by wingrider78 on 2010-06-18
Okay, I found it.  I was just worried that I would lose the file if I cleared the /tmp files out.  Thanks for all of your help.  I will be marking the thread as solved.

---

### Post by rewyllys on 2010-06-18
> **mike555 said:**
> You might want to try "Lucky Backup " .

I also recommend Lucky Backup. It's very easy to set up, and can be set to do scheduled synchronizings (i.e., backups) at times and intervals of your choosing.

For 2 months now I've been using it to back up my /home directory to an external hard drive, each morning at 01:00. It has worked just fine.

It's available via the Synaptic Package Manager.

---

