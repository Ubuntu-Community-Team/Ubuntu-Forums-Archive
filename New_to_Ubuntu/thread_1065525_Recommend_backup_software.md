---
title: "Recommend backup software?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by pmooney78 on 2009-02-10
Can anyone recommend a decent piece of backup software?

What I'd really like to do is to define directories that are to be backed up, then kick back with a book and pop another blank DVD into the burner after each one finishes. Or, failing that, have a series of 4.7 GB .iso images created. 

My strong preference would be to have the DVDs contain just files that are being backed up, not compressed or encoded archives ... and definitely not in some unusual format that requires major effort to extract. I want to be able to just drag-and-drop the backed-up files back onto my hard drive if necessary, preferably from any computer, regardless of OS.

I've been burning data DVDs manually with Brasero since switching to Linux, but my music collection has grown out of control, and it's just too much work anymore to guess at combined files sizes of folders for the forty DVD-ROMs that would be required.

Any suggestions?

---

### Post by lazyart on 2009-02-10
I'd suggest an external hard drive formatted as FAT32.  Then use nightly or weekly rsync to keep data syncrhonized.  I've always thought the best backup system need only to be monitored, not actively initiated.  You'll quickly get tired of burning discs.

---

### Post by Temposs on 2009-02-10
I second lazyart's recommendation. DVDs are relatively fragile and much less flexible in terms of functionality. You can automate your backup with a number of programs so you never have to think about it.

Alternatively to rsync, you could use a program called "Simple Backup" which I use for all my backup. It's in the repositories(Applications->Add/Remove...)

---

### Post by hyper_ch on 2009-02-10
why fat32? I'd use a linux filesystem and make incremental snapshot-style backups.

---

### Post by pmooney78 on 2009-02-10
> **lazyart said:**
> I'd suggest an external hard drive formatted as FAT32.  Then use nightly or weekly rsync to keep data syncrhonized.  I've always thought the best backup system need only to be monitored, not actively initiated.  You'll quickly get tired of burning discs.

Amen to that ... already tired of burning discs. What a good idea! I'll have to pick up an inexpensive external drive on my next payday.

I hate to admit this, but the rsync man page makes my eyes glaze over. Can you point me to a tutorial somewhere that might show me how to set up what you're suggesting?

Many thanks.

---

### Post by hyper_ch on 2009-02-10
> **pmooney78 said:**
> I hate to admit this, but the rsync man page makes my eyes glaze over. Can you point me to a tutorial somewhere that might show me how to set up what you're suggesting
there are many howtos on rsync out there. you might want to fire up google and do a search ;)

---

### Post by Kobalt on 2009-02-10
And you can use it with a graphical interface with Grsync (from the repositories).

---

### Post by mikechant on 2009-02-10
I use the following command:
```
rsync -av --progress --delete /mnt/data1 /media/usba
```
All my music, videos etc. are in various folders under 'data1'.
The backup partition on my external drive is labelled as usba so it mounts automatically at /media/usba.
When first run, this will do a full backup; subsequent runs just apply the necessary changes.
-a = copy file attributes unchanged, as you normally want for backups (more to it than that but that's the basic idea)
-v = verbose = extra output
--progress = progress bars for each file
--delete = any file you delete will also be removed from the backup.
I also backup /home in the same way.
I always keep my external drive disconnected and powered down when not in use so if my PC blows up (like my last one did - flames and all!) there's no chance of it frying the backup drive.
I'm thinking of getting a small fire-proof media safe to keep it in.

If you've got a lot of data and it can't be recreated easily, I'd still do ocassional backups to DVD-R or similar. If your main hard drive gets corrupt and you don't notice, you might copy the corruption to the external backup.
In the past I've used a tool called 'dar' (disk archive) - this can split the backup into DVD size chunks. I think it's in the Ubuntu repositories (I haven't used it recently - I'm not currently practicing what I preach on the DVD front, but I have bought a pack of 50 for when I get round to it!).

---

### Post by ushills on 2009-02-10
Try junglebackup (admittedly it is not free), however, I use it and can access from any pc either through a web interface or mounted drive.

Seems to be quite cheap for server storage a couple of $ per month for my 7Gb.

---

### Post by lazyart on 2009-02-11
> **hyper_ch said:**
> why fat32? I'd use a linux filesystem and make incremental snapshot-style backups.

OP wants to drag and drop from any OS.

---

### Post by pmooney78 on 2010-08-04
I followed the advice and used simplebackup for a long time, but am now doing nightly cron-based rsyncs to external hard drives following the tutorial at this address: [http://www.linuxbasement.com/content/backups-using-rsync-bash-cron](http://www.linuxbasement.com/content/backups-using-rsync-bash-cron)

---

### Post by surfer on 2010-08-04
[backintime]("http://backintime.le-web.org/") is also simple and works well with ubuntu.

---

