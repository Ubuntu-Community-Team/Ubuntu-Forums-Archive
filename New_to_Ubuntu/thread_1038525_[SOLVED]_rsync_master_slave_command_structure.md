---
title: "[SOLVED] rsync master slave command structure"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-01-12
I want to make Ibex (v. 8.10) call (re-name?) an internally mounted hard drive (20 gig) something other than 'disk' when I look in /media (identified as 20.0 GB Media in Gnome file manager). This 20gig disk is jumpered as cable-select.

I want to use rsync to back up the /home from the primary master (or OS) to /media/disk (a rose by any other name would smell sweeter). I used GParted in LiveCD to format (technically reformat the 20gig as Primary Partition, ext3).

Can someone give me the basic command line structure for rsync for copying my /home from the primary master to the primary slave? I don't want to use sudo, if possible.

Also, do I have to mount the primary slave **every time** I run rsync?

I tried:

mark@Lexington-19:~$ rsync -var /home/mark /media/disk
sending incremental file list
mark/
rsync: recv_generator: mkdir "/media/disk/mark" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***

sent 831577 bytes  received 2645 bytes  111229.60 bytes/sec
total size is 8625672860  speedup is 10339.78
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]
mark@Lexington-19:~$

---

### Post by Mark_in_Hollywood on 2009-01-12
Never mind, in the intermim I found Grsync. I'll play with that for a while. Sheesh, I didn't find Grsync searching any of rsync via google or the ubuntuforums.org .. I think that quite odd.

---

### Post by lswb on 2009-01-12
There are all kinds of options. First, you can give the disk a label and gnome will use that instead of "20GB Media" or other generic descriptor. For an ext2 or ext3 filesystem use the "e2label" command, as in 

sudo e2label /dev/sda1

substituting the correct device name where I used sda1. There is an "mlabel" command to make msdos labels for fat/vfat disks.

Since this is a permanently installed, internal drive, my own preference would be to give it a mount point and an /etc/fstab entry s that it mounts automatically on boot. On my system, for instance, I have a separate partition that is mounted as /data. See man mount and man fstab for details. You can check the exisiting lines in /etc/fstab for some idea of how to structure the entry. 

For the sake of illustration lets assume that you have mounted the disk at /data. You will need a directory on the disk that you have rw permissions on as a regular user. (This is likely why you are getting the error message from rsync) What you could do is for instance
```

sudo mkdir /data/backupmark
sudo chown username:username /data/backupmark
sudo chmod 700 /data/backupmark

```

Then you should be able to use the rsync command like

rsync -a home/mark/* /data/backup

If you named the directory on the backup drive "mark" I believe you could just use the command

rsync -a /home/mark /data.

Decide on the exact directory structure you would like to use and then post again with specific questions if you need help with the commands.

---

