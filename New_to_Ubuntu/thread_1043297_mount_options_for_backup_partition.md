---
title: "mount options for backup partition?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Chris Hansen on 2009-01-18
Hello,

I recently re-installed Ubuntu on my desktop and got rid of windows. I put the system and everyting on sda2. I re-formatted sda1 and left it blank with the intention of using it as a backup drive.

This is the line I put in /etc/fstab:

/dev/sda1 /mnt/backup ext3 rw 0  0

It seems to mount and work ok but are there any particular options you should choose for backups?

Thanks.

---

### Post by cdtech on 2009-01-18
None at all, that should work for ya...........

---

### Post by Chris Hansen on 2009-01-18
> **cdtech said:**
> None at all, that should work for ya...........

Thank you much!

---

### Post by Ptero-4 on 2009-01-18
You might want (if sda1 is bigger than sda2) to change the first "0" with a "1" in the sda2 line, this makes linux automatically back-up the contents of sda2 into sda1.

---

### Post by cdtech on 2009-01-18
If you check the man page (man fstab):
> The sixth field, (fs_passno), is used by the fsck(8) program to
       determine the order in which  filesystem  checks  are  done  at
       reboot  time.   The  root filesystem should be specified with a
       fs_passno of 1, and other filesystems should have  a  fs_passno
       of 2.  Filesystems within a drive will be checked sequentially,
       but filesystems on different drives will be checked at the same
       time  to utilize parallelism available in the hardware.  If the
       sixth field is not present or zero, a value of zero is returned
       and  fsck  will  assume that the filesystem does not need to be
       checked.

---

### Post by Chris Hansen on 2009-01-18
> **Ptero-4 said:**
> You might want (if sda1 is bigger than sda2) to change the first "0" with a "1" in the sda2 line, this makes linux automatically back-up the contents of sda2 into sda1.

I think I made a typo, I don't actually have an sda2, the system is entirely on sdb. Sdb5, where I keep my data, is a little bigger than the sda1 partition I reserved to store backups.

I'm using simple backup right now, did I read correctly that it compresses the files so it doesn't need as much space?

---

### Post by Chris Hansen on 2009-01-18
> **cdtech said:**
> If you check the man page (man fstab):
Thanks for pointing that out.

Would this be a better entry in fstab?

/dev/sda1 /mnt/backup ext3 rw 0 2

---

### Post by HotShotDJ on 2009-01-18
I would also tell the system NOT to automatically mount the partition when you boot the system.  You only need it mounted when you are backing up data.  Just add noauto after rw option, like this:```
rw,noauto
```Notice no spaces there.  You'll need to make sure that your backup script includes a mount command before executing the backup and then umount after the backup completes.  Doing this helps prevent corruption of your backups.

---

### Post by Chris Hansen on 2009-01-18
> **HotShotDJ said:**
> I would also tell the system NOT to automatically mount the partition when you boot the system.  You only need it mounted when you are backing up data.  Just add noauto after rw option, like this:```
rw,noauto
```Notice no spaces there.  You'll need to make sure that your backup script includes a mount command before executing the backup and then umount after the backup completes.  Doing this helps prevent corruption of your backups.

Thanks for the tip, it brings up a couple of questions I'm afraid. How is this for fstab?

/dev/sda1 /mnt/backup ext3 rw,noauto 0 2

Is there a particular backup program you recommend? I've been playing with Simple Backup and I didn't see a way to set up scripts like that.

---

### Post by HotShotDJ on 2009-01-18
> **Chris Hansen said:**
> Is there a particular backup program you recommend? I've been playing with Simple Backup and I didn't see a way to set up scripts like that.I use a simple [rsync]("http://www.enterprisenetworkingplanet.com/netos/article.php/1573881") script to backup my home directory.  There are many, many ways to use rsync to accomplish your goals.  For me, I just want to backup to an external drive, but it can be used on internal partitions and even across networks.  You can set your script up to run automatically at specified times quite easily by using [Cron]("https://help.ubuntu.com/community/CronHowto")

Here is a simple sample script that you could adapt to your needs:
```
#!/bin/bash
mount /dev/sda1
rsync -ap --delete-excluded --delete /home /mnt/backup
umount /dev/sda1
```
I have my script stored as /home/hotshotdj/bin/backup

It is also possible to use it to backup your entire system, but that requires a more complex (but not prohibitively so) set of options.  Read that article I linked to regarding rsync backups to see how you might like to use it.  Personally, I'm happy having my /home directory backed up.  I can always reinstall the OS from Ubuntu installation CD. (although I do use a liveCD with [Partimage]("http://www.partimage.org/Main_Page") to make occasional full system backups).

---

### Post by cdtech on 2009-01-19
I use "tar" to backup my system. I made a directory "/backup" then mount my drive to read only through "/etc/fstab" and then using a script, I mount to read/write when I run the backup, using:
```

   echo -n "Mounting backup partition to read-write...."
if ( mount ${backuppart} -o remount,rw &> /dev/null ) then
   echo "done"
   **# be sure to reset the partition to read-only**
   echo -n "Mounting backup partition read-only...."
if ( mount ${backuppart} -o remount,ro &> /dev/null ) then
   echo "Done"

```
Hope this helps ya...........

---

### Post by theozzlives on 2009-01-19
> **Chris Hansen said:**
> Hello,

I recently re-installed Ubuntu on my desktop and got rid of windows. I put the system and everyting on sda2. I re-formatted sda1 and left it blank with the intention of using it as a backup drive.

This is the line I put in /etc/fstab:

/dev/sda1 /mnt/backup ext3 rw 0  0

It seems to mount and work ok but are there any particular options you should choose for backups?

Thanks.

It's not a good idea to backup to the same drive, if it fails, your backups are gone.

---

