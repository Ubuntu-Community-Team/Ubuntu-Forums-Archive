---
title: "Backup Programs"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-09-16
I have tried about every backup program in Ubuntu. They all have a problem some won't find the external drive (yes it is mounted) and several never show up anywhere in menus, others don't run or stop with an error message. I even tried my windows backup programs under wine and they stop with an error. Currently I downloaded grsync but can't find it anywhere. Any hint? I tried add to menu and typed in it's name, but don't know the path as I can't find it! I did copy my home folder to the external drive but I sure would like to do incremental backups rather than copy 80GB every week.

---

### Post by Joshua Lückers on 2009-09-16
Maybe you can take a look at the [rsync](https://help.ubuntu.com/community/rsync) page on help.ubuntu.com. It will also explain how to use Grsync.

---

### Post by Paqman on 2009-09-16
> **cmcanulty said:**
> I tried add to menu and typed in it's name, but don't know the path as I can't find it!

YOu don't actually need to know the full path on Linux, the package name is good enough. So to launch grsync you just need:
```

grsync

```

You can also launch any app by hitting Alt-F2 and typing it in.

---

### Post by vanadium on 2009-09-16
Suppose your documents are in "/home/cmcanulty/Documents"

Suppose your backup copy is on the drive mounted on "/media/100 GB Media", in a folder Documents.

All you need is

```

rsync -av "/home/cmcanulty/Documents/" "/media/100 GB Media/Documents/"

```

to mirror your data. Add the --delete option for true mirrorring: this deletes files in the destination that do not anymore exist in the source (be carefull with that option).

---

### Post by ubongo2008 on 2009-09-16
an very nice backup disk is clonezilla it also supports ext4 and you will be able to use it also if you box won't boot any more. Oh and it is for free have a look at: [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by cmcanulty on 2009-09-16
Well now I have wasted 2 hours with GRsync trying to backup 80GB and it completes in seconds with a few KB copied and won't let me delete the garbage file it created!

---

### Post by mapes12 on 2009-09-16
> **cmcanulty said:**
> Well now I have wasted 2 hours with GRsync trying to backup 80GB and it completes in seconds with a few KB copied and won't let me delete the garbage file it created!Hi 

can you post a screen shot please with the Grsync screen showing how you have set it up?

[http://mag.mypclinuxos.com/html/Issues/200708/page04.html](http://mag.mypclinuxos.com/html/Issues/200708/page04.html)

---

### Post by cmcanulty on 2009-09-16
Here it is, thanks

---

### Post by jonaskarlsson on 2009-09-16
Are you sure you haven't switched your source and destination?

---

### Post by cmcanulty on 2009-09-16
Oh I did that on the  screenshot but the backup was done correctly like this attachment, sorry

---

### Post by cmcanulty on 2009-09-16
I tried it again and am posting the errors

---

### Post by jonaskarlsson on 2009-09-16
There seem to be some problems when you write to your external disk. Is there enough space? What file system is it? You can try to google the error message you get.

---

### Post by cmcanulty on 2009-09-16
It is 500GB and writes  fine when I copy to it. I only need about 100GB of it for now, but backups don't work. I want to do incremental backups like I did on XP.

---

### Post by mapes12 on 2009-09-17
In my case I have a second (removable caddy) HDD on which I have a directory called Grsync. So to backup to it I create a directory to mount the HDD to like this:

```
sudo mkdir /HDD2
```
# creates a folder in the filesystem folder called HDD2

I then mount my second HDD to it which is called sdb1 in my HDD configuration like this:

```
sudo mount /dev/sdb1 /HDD2
```
# mounts the 2nd HDD Linux partition to the file system via the above directory

I launch Grsync with root permission like this:

```
gksudo grsync
``` (Although I have now edited my menu icon to launch like this).

I then set up Grsync as per the attached screenshots. Notice the boxes I have ticked and also note the excludes. The hidden file .thumbnails doesn't need to be backed up so this saves a bit of space and .gvfs is a virtual file system that is recreated at boot up. Trying to backup .gvfs screws up the backup. 

Once the first backup is done then Grsync only takes a few seconds the next time around because it only backs up new / changed files.

To restore I switch the source and destination after having first re-mouted the second HDD of course.

In the event of a total system crash or hardware failure I would carry out a fresh install of UBU, fetch all the current updates and then restore whatever I needed from the backup. In my case the most critical data are my digital photographs. All the rest of the configuration stuff is easy to recreate.

---

