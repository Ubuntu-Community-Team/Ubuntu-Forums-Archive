---
title: "Backup of entire system."
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-03-15
If I wanted to make a backup of my entire system, could I use 
```
sudo cp / /media/backup
sudo grub-install --root-directory=/media/backup /dev/sdb1

```

Assuming of course I want to back it up to /dev/sdb1 mounted at /media/backup ;)

Edit: As I think about it more... This would end up copying itself, to itself over and over... so maybe copy everything EXCEPT /media and then make it manually?

---

### Post by ndefontenay on 2010-03-15
```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

There's a whole thread there:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by lyall on 2010-03-15
here is a link for backing of your system
[https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

when or if you have the time look over the TitleIndex Ubuntu documentation
[https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")

there is a lot info there and will help you along your way

good luck and have fun learning

---

### Post by oldefoxx on 2010-03-16
Backing up a partition to itself is not the best thing to try.
There are ways to do it, but it is easy to mess up.  And having both backup and system on the same partition is not good, if the problem effects the partition.  In fact it is not even good to backup one partition onto another partition on the same drive.  Best have a second drive for this.

A System Backup could either relate to one partition or to everything on the one or two drives in the PC.  It makes a difference as to what method or approach might be best.  For instance, you could be just backing up folders and files, and sort of forget that the partitions have to be allocated and formatted in order to restore by the same process.  Or you can look for a product that handles the necessary partitioning and formatting for you automatically.

I consider it better to backup everything to an external drive in a compressed format so that I can store more than one backup on it, and with it being an external drive, I can treat it separately, mean store it somewhere where a fire or flood will not damage both the PC and my surviving backup.  After such an occurance, I might need a new PC, but the surviving backup would then allow me to put everything back on it.

So now maybe you ought to explain yourself.  What is your idea of a system backup, because it is only once that is known can anyone really give you the most fitting advice.

---

### Post by ndefontenay on 2010-03-16
If a fire or flood is damaging my house I have far more concerning problems than my data x)

Still, storing outside of the computer itself is a very important point.

---

### Post by Barriehie on 2010-03-16
I use rsync to copy, recursively, my home dir and /etc to another drive and then use tar to compress the backups to a USB drive.  I also use ```
dpkg --get-selections | gawk '{ print $1 }' > ~/MyInstalledApps
``` to save a list of what's installed.  As oldefoxx says it's a good/better idea to backup to another device.  Check out rsync.

---

### Post by Ozymandias_117 on 2010-03-16
@oldefoxx I have a computer my school lets me use, But they are about to change their policy and force people to run windows, I want to make an exact copy of it's hard drive onto another (external) hard drive (The other hard drive has a larger partition) So I can boot to it rather than their OS.

edit: I already have the hard drive formatted to ext4 with an extended partition and a linux-swap. And yes, I know an external HDD will be somewhat slow.

---

