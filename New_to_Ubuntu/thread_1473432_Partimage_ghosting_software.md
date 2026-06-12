---
title: "Partimage ghosting software"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by asharpham on 2010-05-05
Using synaptic I installed partimage and the documentation that comes with it. But I can't find it. It's not appearing in any of the menus, so where's it gone? I did a file search and got no results. Synaptic still tells me it's installed so I'm stumped!

---

### Post by GSF1200S on 2010-05-05
> **asharpham said:**
> Using synaptic I installed partimage and the documentation that comes with it. But I can't find it. It's not appearing in any of the menus, so where's it gone? I did a file search and got no results. Synaptic still tells me it's installed so I'm stumped!

Try opening a terminal and typing:
```
partimage
```

Remember this (this helps me all the time): When you install something, you can go into Synaptic, right click on the installed package, click properties, and then select Installed Files. Most program binaries are installed to /usr/bin (although there are exceptions). You look through the installed files and see where the program binary is (most importantly what its named), and then launch it. You can do in a terminal:
```
/usr/bin/firefox
```
for example, and firefox will load. Thought you might like to know :)

---

### Post by indytim on 2010-05-05
For Partimage:

```

$sudo partimage

```

A few points as you start to use the application:

1.  You CANNOT backup the actively booted partition (there are workarounds).
2.  Make sure the destination location (partition) has enough available space to accommodate your image file.

-IndyTim / DataMan

---

### Post by Paddy Landau on 2010-05-05
You may find [CloneZilla]("http://clonezilla.org/") easier to use. It uses PartImage to do the actual work. You install it on a CD (or USB flash drive), not on your computer.

---

### Post by asharpham on 2010-05-05
Thanks people. I'm much obliged for your suggestions. I'll try CloneZilla as soon as I can. Sourceforge is currently down for maintenance as I type this. Will try again in the morning.

---

### Post by Mark Phelps on 2010-05-05
FYI ... last time I checked, PartImage did NOT support Ext4 filesystems, and according to what I read, there were no plans to update it ...

Which is the main reason I switched from using PartImage for backups to Clonezilla -- the latter supports Ext4 filesystems.

---

### Post by Paddy Landau on 2010-05-05
> **Mark Phelps said:**
> ... PartImage did NOT support Ext4 filesystems ... switched from using PartImage for backups to Clonezilla -- the latter supports Ext4 filesystems.
I'm glad you pointed that out. I just checked, and you're right.

I had thought that CloneZilla used PartImage, but I see that that's not quite true; instead, it's partly based on PartImage.

*EDIT* Also, PartImage doesn't support NTFS, so you must use CloneZilla to back up Windows partitions.

---

### Post by asharpham on 2010-05-05
I tried CloneZilla this morning but couldn't finish the job. I want to mount the image on my hard drive but after "naming" the file to be created, it gave me an error message which basically said it couldn't find an unmounted drive.

So I decided to use a 16Gb USB drive. This worked fine but unfortunately was not large enough to hold the backup.

How do I select my HD for the destination file? It has more than enough free space to hold the backup. I thought it would not be mounted when booting from the CloneZilla CD I created.

---

### Post by perspectoff on 2010-05-05
My compressed partition image is 6.4 Gb, and I want to store the two split files on 2 separate DVDs.

I split the partition image file using both Partimage and Clonezilla, then stored the split portions on 2 different DVDs.

However, I can not figure out how to restore them with either Partimage or Clonezilla. Both require the split portions to be in a single directory (which kind of defeats the purpose of splitting an image file in the first place).

Anybody know how to do this? I have scoured the docs for both Partimage and Clonezilla and cannot find an answer.

Except for this restore problem, both Partimage and Clonezilla work equally well for me...

---

### Post by Paddy Landau on 2010-05-06
> **asharpham said:**
> How do I select my HD for the destination file?
I need more information. Please be specific:

[LIST]
[*]Are you backing up a partition or an entire drive?
[*]Which drive (e.g. sda) or partition (e.g. sda2) do you want to back up?
[*]On which partition do you want to save the backup (e.g. sdb1)?
[/LIST]
Remember that:

[LIST]
[*]If you're backing up a partition, you need to save it on a different partition or drive.
[*]If you're backing up an entire drive, you need to save it on a different drive.
[/LIST]

---

### Post by Paddy Landau on 2010-05-06
> **perspectoff said:**
> My compressed partition image is 6.4 Gb, and I want to store the two split files on 2 separate DVDs.
As far as I'm aware, neither PartImage nor CloneZilla cater for multi-disk backups. I looked for the solution some time ago, and solved the problem by buying an external hard drive, which proved to be both more convenient and much faster.

> **perspectoff said:**
>  I split the partition image file using both Partimage and Clonezilla, then stored the split portions on 2 different DVDs.
I don't know how you managed to use PartImage and CloneZilla together. I recommend that you use only CloneZilla (PartImage supports neither ext4 nor NTFS).

---

### Post by asharpham on 2010-05-06
Ah, now that's the problem. I want to back up an entire drive.  I have an external drive so I'll try using that.

---

### Post by Paddy Landau on 2010-05-06
> **asharpham said:**
> I want to back up an entire drive.
Yes, if you think about it, you can't back up a partition (or drive) while that same partition (or drive) is in use!

That's why you install CloneZilla on a CD or USB flash drive, so that you boot from it instead of from your source.

---

### Post by CharlesA on 2010-05-06
Random trivia: Clonezilla uses partclone instead of partimage, which is why it works with NTFS and EXT4.

As for imaging, what I usually do is set up a share someone on the network then image it to there. Works like a charm for me.

An external hard drive, or USB key would work too.

---

### Post by asharpham on 2010-05-07
Unfortunately my external drive won't mount any more. Don't know what the problem is but I'm sure it's the drive, not Ubuntu. So it looks like I'm on the market for one!

---

### Post by psusi on 2010-05-07
You might want to check out the parted magic cd and Ghost4Linux that it comes with.  It provides a nice Norton Ghost like UI around partimage or partclone.  It also is a small cd and can boot entirely into ram so you can eject the cd and put in a blank to burn.

I wonder why partimage does not support ext4.  There are no changes that it should care about.  Since partclone seems to be a rewrite of partimage using the e2fslibs instead of using its own code to parse the fs, I get the feeling that they are intentionally refusing to support ext4 on partimage to force people to switch to partclone as a replacement.

This can be handy for transferring to a new hard drive of equal or greater size, but is not a good idea for general backup because:

1)  Doesn't do incremental backups
2)  Can't view or extract files without doing a full restore
3)  Can't restore to a smaller drive, even if the actual used space would fit

---

