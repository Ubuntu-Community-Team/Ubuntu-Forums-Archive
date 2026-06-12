---
title: "Need a viable way to back up and restore"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by occams_beard on 2009-05-17
I'm trying to figure out the best, SAFEST, way to backup my user's home directory, and restore it easily if need be.

I have about 1 ~ 2 GB of irreplaceable data that changes daily, and right now I'm backing it up to a USB flash drive every night, which is a real pain.

I've researched this and everyone seems to have a different opinion like making a tarball, using rsync, etc. There are also a lot of different programs like simple backup, time vault, homeuserbackup.  But most of these seem outdated, or I read about problems users have with them when restoring. Also a lot of the how-tos do a good job of explaining how to do a back up, but make no mention of restoring!

There are so many options and opinions, I just don't know where to begin. I need something that is going to 100% reliable and work well. Preferably I would like to have a cron job or something to do the backup every night to an external hard drive, and then maybe weekly upload the backup to an off-site server. 

There must be some kind of standard fool-proof way to do this. I cannot afford to mess around with half-baked programs.

Please help, I'm getting extremely nervous not having a good backup solution!

---

### Post by NHArticleTen on 2009-05-17
[http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)

---

### Post by The Cog on 2009-05-17
I would recommend using rsync. There is a graphical front-end called grsync if you prefer.

Use ext2 on the pen drive if preserving permissions is important. Also, use two different pen drives, on alternate days. Maybe also keep another drive that you only update every week or two so you have a change to recover if you discover that you overwrote something important last week.

I use rsync to an external usb drive. Because rsync only writes the changed data, it's reasonably fast and painless.

---

### Post by rcayea on 2009-05-17
I second a vote for rsync. I find it easy to use and has a lot of options.

---

### Post by keithweddell on 2009-05-17
This is a good read. [The Tao of Backup]("http://www.taobackup.com/sanctuary.html")

---

### Post by HermanAB on 2009-05-17
Hmm, take it from an old-timer that the backbone of backup is tar and rsync and has always been tar and rsync.

The reason for the proliferation of half baked GUIs is because they are not all that useful.  It is far better to put a two line script in /etc/cron.daily that uses rsync and the newcomers that write the little GUis eventually clue in and abandon their GUIs, leaving behind yet another half baked program for other newcomers to stumble upon.

A proper backup system should be automatic and without any user intervention, otherwise, it will eventually be ignored and once it has been ignored for a while, disaster will strike.

So, make your own little rsync script and put it in cron.daily and then forget about it and let it do its thing.  Note that if the backup script has more than about 3 lines, then you are doing it wrong!

Tip: Don't include millions of directories to backup, exclude the ones you don't want backed up, then your script will be zero maintenance.

---

### Post by RedSingularity on 2009-05-17
I personally like Simple Backup.  Very easy to use.  Comes with GUI if you like.

---

### Post by occams_beard on 2009-05-17
Wow, thanks for all the replies.

I've been experimenting with rsync, and it seems to work well, although I'm not sure which options I'd need.  Symlinks and hardlinks and such, to compress or not compress?

The scenario I'm imagining is this:

I have a 'work' directory in my home dir containing about 2 GB of critical data that I'd like to back up each and every night. This directory is ever increasing in size. 

I have the rest of my home dir, which contains all the .settings files and other not as critical (but still important) stuff.  I'd like to back this up at least once a week so that I can restore and get back up and running quickly with all application settings if I ever need to. I would need to preserve permissions for this.

As for a backup medium, I'm thinking of getting a [Western Digital USB hard drive]("http://www.amazon.com/Western-Digital-Passport-Essential-WDME3200TN/dp/B0012GQZZU/ref=sr_1_1?ie=UTF8&s=electronics&qid=1242590270&sr=8-1"). However, I wonder if you can leave these running all the time, how reliable they are, or if they can be partitioned and reformatted to ext3 so I can keep file permissions?

---

### Post by Cheesemill on 2009-05-17
Check out Back in Time
[http://backintime.le-web.org/](http://backintime.le-web.org/)

Cheesemill

---

### Post by HermanAB on 2009-05-17
A USB drive is just a normal drive in a different box.

Format it like this:
Plug it in
$ dmesg
Look for the device name eg. /dev/sdb1
If it automounts, unmount it.

Now make a EXT3 file system:
$ sudo mkfs.ext3 -L volumelabel /dev/sdb1

Now, if you replug it, it should automount under /media/voumelabel

---

### Post by MrWES on 2009-05-17
> **occams_beard said:**
> I'm trying to figure out the best, SAFEST, way to backup my user's home directory, and restore it easily if need be.

I have about 1 ~ 2 GB of irreplaceable data that changes daily, and right now I'm backing it up to a USB flash drive every night, which is a real pain.

I've researched this and everyone seems to have a different opinion like making a tarball, using rsync, etc. There are also a lot of different programs like simple backup, time vault, homeuserbackup.  But most of these seem outdated, or I read about problems users have with them when restoring. Also a lot of the how-tos do a good job of explaining how to do a back up, but make no mention of restoring!

There are so many options and opinions, I just don't know where to begin. I need something that is going to 100% reliable and work well. Preferably I would like to have a cron job or something to do the backup every night to an external hard drive, and then maybe weekly upload the backup to an off-site server. 

There must be some kind of standard fool-proof way to do this. I cannot afford to mess around with half-baked programs.

Please help, I'm getting extremely nervous not having a good backup solution!
+1 for rsync; I used it on my home server to backup my important documents. I run it from the root crontab
```
sudo crontab -e
```
It runs every Sunday at 3:30am:
```
# Weekly backup of Documents on external drive to /data/backup
30 3 * * 0 rsync -av --delete --progress  /media/external/Documents /data/backup

```
I use the delete flag; that is, if I delete the file from the source, rsync will delete the file from the backup destination. It's a matter of choice. You can change the source and destination to suit your needs. Works like a charm.

~Bill

---

### Post by XCan on 2009-05-17
> **occams_beard said:**
> Wow, thanks for all the replies.

I've been experimenting with rsync, and it seems to work well, although I'm not sure which options I'd need.  Symlinks and hardlinks and such, to compress or not compress?

The scenario I'm imagining is this:

I have a 'work' directory in my home dir containing about 2 GB of critical data that I'd like to back up each and every night. This directory is ever increasing in size. 

I have the rest of my home dir, which contains all the .settings files and other not as critical (but still important) stuff.  I'd like to back this up at least once a week so that I can restore and get back up and running quickly with all application settings if I ever need to. I would need to preserve permissions for this.

As for a backup medium, I'm thinking of getting a [Western Digital USB hard drive]("http://www.amazon.com/Western-Digital-Passport-Essential-WDME3200TN/dp/B0012GQZZU/ref=sr_1_1?ie=UTF8&s=electronics&qid=1242590270&sr=8-1"). However, I wonder if you can leave these running all the time, how reliable they are, or if they can be partitioned and reformatted to ext3 so I can keep file permissions?

First of all, I vote for rsync as well. I use it to backup my /home/ dir on the workstation at work to my home computer. Regarding your compression thingie, which are you referring to? rsync supports compression when it transfers the data over the network with the default -z flag, and is mostly to speed up data transfer.

I've restored backups created by rsync by using actually rsync. It was as simple as running basically the same script, but exchanging the source and destination. :)

---

### Post by jimmy the saint on 2009-05-17
I always make a disk image of a good setup just in case something horrible happens.  It is an old windows habit, but I still do it.  If a HD fails, it is nice to be able to just restore the installation, tweak it, and restore the home directory rather than having to start from scratch.  This is not a replacement for incremental backups, but it is a good additional step in my opinion.

I used to use acronis, but now I use Clonezilla.  It is free and operates through a boot cd or USB stick

---

