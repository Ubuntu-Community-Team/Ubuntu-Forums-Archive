---
title: "[SOLVED] 120+ GB Missing Disk Space"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Pollik on 2009-01-06
Still very much a newbie, but trying to read round the problem, so please bear with me. :)

Using the Disk Usage Analyser shows me I have 241.0 GB total capacity, 195.1 used, 46.3 available.

A file system scan in Disk Usage Analyser shows me as using 63 GB

My Wastebasket is empty.

In the terminal window I have run: sudo apt-get clean.

Partition /dev/sda6 (Ext3) shows total size 222.3 GB (available 27.2 GB)
Partition /dev/sdf1 (vfat) shows total size 19.1 GB (available 19.1 GB)

I have run: df -h

Output:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             223G  196G   16G  93% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  628K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.9M  249M   2% /dev
tmpfs                 252M  372K  251M   1% /dev/shm
lrm                   252M  2.0M  250M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdf1              20G  256K   20G   1% /media/NEW VOLUME
```


Also:

```
polly@Adie:~$ du -sh *
8.0K	Desktop
112K	DiskUsage
16G	Documents
0	Examples
45G	Music
12M	Music2
4.0K	Pictures
4.0K	Public
4.0K	Templates
4.0K	Videos

```

If it is relevant, my Ubuntu box sits on a wireless LAN with a WinXP laptop and a Win Vista Laptop, both of which have written to the Ubuntu box largish back up files which have since been deleted, using Windows Explorer on the laptops.  I have this nagging feeling that the problem has been caused by remotely deleting the large back up files, but I can't figure out how to check or what to do next.

I have screengrab of Disk Usage Analyser, if it is helpful.

Again, not sure if this is relevant, but I am finding that file/folders are being 'randomly' locked.  At the moment "File System" displays a padlock, as do a couple of folders within my "Home Folder".  I can deal with these with Nautilus, but it is a pain in the backside!

---

### Post by birddog165 on 2009-01-06
Could you show us a screenshot of gparted [the partition editor]?

---

### Post by Pollik on 2009-01-06
Of the 198 GB shown as being used, I can only account for 61 GB, or thereabouts.

---

### Post by birddog165 on 2009-01-06
And this is supposed to be a 360 GiB HDD?

---

### Post by Pollik on 2009-01-07
I think it is either 240 or 250 GB.

The issue is that Gparted shows 225GB on the main partition with 198GB used, leaving 27GB free.  But "du -sh *" shows that I have only used about 61GB, so I should have in excess of 160 GB free?

In the File Browser, clicking on Properties, I have only 15GB showing as free.

When I tried to write a back up to the Ubuntu box, it failed at around 15GB, telling me I had run out of disk space.

Something is blocking/using a very large part of my HDD.

I think it might be relevant that I have previously (2 weeks ago) written backups to the HHD (which would have been about the same kind of size as the disk space now lost), but they were deleted using an XP laptop across a wireless LAN.  The deleted backups are not visible to the XP machine, or via the File Browser or in the Wastebasket.  My guess is that, when the backup files were deleted, the disk space was not released, but I have no idea of how or why that should be.

Part of me is tempted to reformat the drive and start over, but I am always a little uncomfortable working at that level.

Thanks for your continued help. :)

Polly

---

### Post by drs305 on 2009-01-07
It is possible you have a large amount of trash in your root's trash bin. It shouldn't be there if you deleted the files in windows but it would be worth checking your disk regardless. 

Besides trash, large misplaced backup files and numerous or a large number of log files are also often causes. 

The howto linked below discusses how to find files and delete in trash bins (deleted but still taking up space) as well as other ways of freeing up disk space.

[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

Also in your computations remember that ubuntu will reserve 5% of the disk space for system use.

---

### Post by sdowney717 on 2009-01-07
you can backup your home, reinstall and restore your home folder.
I once had a problem when I restored an install to a larger partition using windows xp and ghost. The reinstalled image remembered the old smaller size. I finally just did a reinstall. found out how to backup and restore my home folder was easy.

for example 'test' is your home folder

sudo chown -R test:test /home/test works fine to restore your home

you can log in as test and even the menu adjustments are there.
SO,
If I wanted to backup my home I would do this.

Login as another user to make sure my home files are not in use for copying (not sure if needed)
run gksudo Nautilus
select the home folder to backup
select hidden files options
copy the files and folders somewhere

To restore

create a login user 'test'
copy the backed up home files and folders into /home/test
run the command
sudo chown -R test:test /home/test

and everything is back like it was. (test is just a test name)

---

### Post by Pollik on 2009-01-07
> **drs305 said:**
> It is possible you have a large amount of trash in your root's trash bin. It shouldn't be there if you deleted the files in windows but it would be worth checking your disk regardless.

The answer was/is in trash...thank you!!

Ubuntu seems to be deleting them now.

One day I will get the measure of Ubuntu, but for the moment, it seems a tortuous way to empty the trash.


I feel quite confident about this now (famous last words!!)

I love support forums. :)


Polly

---

