---
title: "Best application to backup ubuntu system"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by eshant_engineer on 2010-07-23
I have searched for the same but found very old threads that too very confusing.

I have tries Back in time, but it doesn't compress the backup product and take too much space, also I am confused about to select directories which will return the same system on restore after fresh installation.

I was looking for an application which is similar to built-in "Backup & Restore" tool of Windows 7.

Thanks in advance for replying...

---

### Post by mikechant on 2010-07-23
> I have tries Back in time, but it doesn't compress the backup product and take too much space,

These days 95%+ of most people's data (by size, not necessarily by number of files) consists of audio/video/picture files in formats which are already compressed and typically can't be compressed any further by any backup compression mechanisms.

What file types make up the bulk of the data you are backing up?

---

### Post by clhsharky on 2010-07-23
eshant_engineer

> I was looking for an application which is similar to built-in "Backup & Restore" tool of Windows 7.
Then you want Windows 7.

Linux is close to this style of backup with the next new Btrfs file system.
Linux has many fine and even more powerful backup app for the system admin , but the two click desktop tool you want I would say next year.

Sharky

---

### Post by eshant_engineer on 2010-07-23
Thanks for replying,

But what for now? :)

---

### Post by mapes12 on 2010-07-23
I approach this from two different angles:-

1. Backing up my Ubu OS system
2. Backing up all my data and personal settings for the system to personlise my log on experience.

This involves having /(root) and /home on their own partitions. If you haven't done this already then try this HowTo - [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866) I don't do the tar bit at the end of the HowTo.

Now, to backing up:-

1. For my Filesystem I image it using [Partimage]("http://www.partimage.org/Main_Page")
2. For my /home directory I use Grsync. It's in synaptic. After the first backup run it only backs up new or modified files. Therefore, backups take about a couple of minutes.

There are some tweaks in setting up Partimage and Grsync (or at least I find there are) and if you want some more info then post back.

---

### Post by da burger on 2010-07-23
A script that runs rsync on the desired files? That will just copy over the files to a backup location. Alternatively we could use tar to archive and compress them.

---

### Post by eshant_engineer on 2010-07-23
> **mapes12 said:**
> 

1. For my Filesystem I image it using [Partimage]("http://www.partimage.org/Main_Page")

There are some tweaks in setting up Partimage and Grsync (or at least I find there are) and if you want some more info then post back.

But, It is clearly mentioned on that page that it doesn't work for ext4 file-system.

---

### Post by mapes12 on 2010-07-23
> But, It is clearly mentioned on that page that it doesn't work for ext4 file-system.

Sorry, only trying to help you. There is no mention in your post of an ext4 requirement. I'm out of here..........

---

### Post by eshant_engineer on 2010-07-24
> **mapes12 said:**
> Sorry, only trying to help you. There is no mention in your post of an ext4 requirement. I'm out of here..........

oh ya, sorry and thanks for your help...

---

### Post by Mark Phelps on 2010-07-24
Take a look into Clonezilla.  I was using PING to backup older Ubuntu systems, but when the filesystem switched to Ext4, that ruled it out because, as you found out, Partimage does NOT work with Ext4 filesystems (despite the fact that folks STILL recommend using it!)

Clonezilla will allow you to backup partitions or the entire drive, so it provides a complete backup and restore solution.

---

### Post by eshant_engineer on 2010-07-24
Thx Mark...will go for it

---

### Post by tipra.wicked on 2010-07-24
> **eshant_engineer said:**
> But, It is clearly mentioned on that page that it doesn't work for ext4 file-system.

The Only Program that supports ext4 Drive Imaging is R-Drive Image .. it can create a bootable USB-Key or an ISO to Image Systems and can be installed in windows to image on the fly . it supports incremental and all the bells and whistles ... check it out.

---

### Post by Yleeyas on 2010-07-24
Have a look at FSArchiver, it handles ext4, plus others;

[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

I got it with the SystemRescueCd and used it after my fresh LL install :)

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

It's a command line interface but easy to use.

---

### Post by Mark Phelps on 2010-07-24
> **tipra.wicked said:**
> The Only Program that supports ext4 Drive Imaging is R-Drive Image ..
If you're talking about Linux programs, you're wrong -- there are several Linux programs that support Ext4 drive imaging.  Clonezilla is one of them.

Also, I think the OP was asking about Linux programs to do drive imageing, not MS Windows programs.

---

