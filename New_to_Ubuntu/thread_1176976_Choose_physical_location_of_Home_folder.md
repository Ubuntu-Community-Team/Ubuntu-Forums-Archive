---
title: "Choose physical location of Home folder?"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by mwsmedia on 2009-06-02
Hi!

On my desktop machine, currently running Win XP, my "My Documents" folder actually lives on a different drive from my operating system and files, and my music and video files are one a third drive.

I'd love to move over to Ubuntu (already did on my laptop!) but I need to know:  can I "assign" the location of the home folder?  Is this something I would need to do after installing?

Many thanks.

---

### Post by drs305 on 2009-06-02
Welcome to the Ubuntu Forums.

You can designate the location of a separate home partition during the installation. You would choose "mount point" and select "/home" for that partition.


Here is a guide with graphics. It's for Hardy but the install procedure has changed little for the later versions:
[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml")

Here is the official ubuntu wiki installation guide. It also has a "graphical install" link:
[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

---

### Post by lindsay7 on 2009-06-02
You can set up a separate /home partition during the manual install. You can set one up after you install but it a heck of a lot easier to do it when you install Ubuntu. I am not sure you can set on up during installation to put it on a different drive. When you do the manual install you set up a root or / partition and a /home partiton and a swap partition and you choose which type of formatting you want i.e est3, ext4.

---

### Post by mwsmedia on 2009-06-02
drs305 -- thanks for the suggestion... but this is a seperate drive, with data already on it.  I need to make sure Ubuntu simply uses it for documents and personal files and doesn't over-write it.  Will your suggestion work in that case?

---

### Post by mwsmedia on 2009-06-02
lindsay7 -- kind of the same question -- I'm not interested in creating a partition if that will destroy the data already there... is that the case?

Thanks.

---

### Post by presence1960 on 2009-06-02
> **mwsmedia said:**
> drs305 -- thanks for the suggestion... but this is a seperate drive, with data already on it.  I need to make sure Ubuntu simply uses it for documents and personal files and doesn't over-write it.  Will your suggestion work in that case?

You can not make a /home partition from an NTFS or FAT partition that Windows uses. You will be able to access those partitions from Ubuntu. But since /home is part of the Ubuntu install NTFS and FAT are out because Ubuntu can't use those file systems in any of it's partitions. You would have to back those up and change the filesystem to Ubuntu's file system, then move your data back over.

I would suggest creating a separate /home partition or using the default /home when installing. Then copying your documents and files over to Ubuntu. The Ubuntu file system is not prone to fragmentation like the Windows file systems are.

---

### Post by mwsmedia on 2009-06-02
Hi Presence1960,

True, we are dealing with different file systems.  Hm... let's say I work out the storage issues involved with moving my documents over to the primary disk's /home partition... once everything is installed, is it possible to assign the /home folder to one drive and the /videos another and have Ubuntu see it all as if it was in one place?

---

### Post by lindsay7 on 2009-06-02
When you install ubuntu and set up a home partition, it is basically empty. You put what you want in it. The good thing about it is that for future upgrades to new versions you can keep what is there and not over write it. You can also set addition partitions that you can use as you like.

---

### Post by mcduck on 2009-06-03
> **mwsmedia said:**
> Hi Presence1960,

True, we are dealing with different file systems.  Hm... let's say I work out the storage issues involved with moving my documents over to the primary disk's /home partition... once everything is installed, is it possible to assign the /home folder to one drive and the /videos another and have Ubuntu see it all as if it was in one place?

You can have nay directory on any partition (and the other way round, mount any partition in any location in the file system.

So yes, if you want you can have /home on a separate partition, and then if you want you can have a separate video partition and mount that into a video directory inside your home directory.

From user's perspective you'd never even know that the files are on separate disks/partitions, apart from having a different amount of free space available in different directories.

---

