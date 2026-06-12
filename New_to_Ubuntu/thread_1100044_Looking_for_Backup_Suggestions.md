---
title: "Looking for Backup Suggestions"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by LenWynne on 2009-03-18
Hi,

I just spend the afternoon doing a complete reinstall of Ubuntu (intrepid).

Since the install is still new, with only a few added applications etc, I would like to back it up now as this would be the best place to return if I have another problem.  What would be the best method for backing up?

I have a secondary internal HD that I use to store most of my big files (music etc.) and it has plenty of room if I can place a backup there. Or perhaps creating an image file for a CD?

any suggestions would be appreciated

---

### Post by Linux000 on 2009-03-18
There is a backup option under System/Administration to back up specific files, of course you would back-up the file /.;)(This would back up the drive)

---

### Post by lovinglinux on 2009-03-18
If you want to have a pristine installation backup, why don't you simply install Ubuntu with a separate /home partition, so whenever you need you just have to reinstall from the CD, without formatting the /home partition?

With this method you won't need to configure personal stuff again. You can even run a script to save a list with installed applications and use it to download and install all of them automatically after reinstalling the OS.

---

### Post by Helios1276 on 2009-03-18
> **lovinglinux said:**
> If you want to have a pristine installation backup, why don't you simply install Ubuntu with a separate /home partition, so whenever you need you just have to reinstall from the CD, without formatting the /home partition?

With this method you won't need to configure personal stuff again. You can even run a script to save a list with installed applications and use it to download and install all of them automatically after reinstalling the OS.

+1 Also, if your feeling adventurous, you could try Remastersys and create an iso of your install.

---

### Post by LenWynne on 2009-03-18
Thank you all for the suggestions

Since I did not think about making home on a separate partition I will look at what I can best do to save my current fresh install :)

---

### Post by drs305 on 2009-03-18
You can make an image of the partition with Partimage. It will make an exact copy of the partition but will not include empty space to limit the size of the file.

You can save the image on any other partition and, when restored, will put the system back exactly the way it was when you made the image. It takes a bit to get comfortable with making the backup but once you have done it a few times it's pretty straightforward.

Here are two links on how to use it:
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")
[http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html]("http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html")

---

### Post by LenWynne on 2009-03-18
Thank You :)

---

### Post by phantom3113 on 2009-03-18
> **lovinglinux said:**
> If you want to have a pristine installation backup, why don't you simply install Ubuntu with a separate /home partition, so whenever you need you just have to reinstall from the CD, without formatting the /home partition?


I don't mean to threadjack, but how would one do this? I have this setup for that exact reason, but how to actually do this eludes me.

---

### Post by stoogiebuncho on 2009-03-18
If you want to move your home folder to it's own partition without resizing, there's instructions here:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

I haven't tried it but it looks pretty straightforward.

---

### Post by antmenj on 2009-03-19
Theres always Gparted.  Simply copy your whole partition to the other drive.

---

### Post by lovinglinux on 2009-03-19
> **phantom3113 said:**
> I don't mean to threadjack, but how would one do this? I have this setup for that exact reason, but how to actually do this eludes me.

Most of your personal configurations are saved into hidden folders and files under your home directory. When you have a separate partition for /home you can reinstall the OS without formatting the /home partition, so the OS will use the existing /home directory for your user. I don't want to extend this discussion and don't remember all the steps, but there are plenty of tutorials in the forums about this. Anyways, it basically works like this.

1 - you insert the Live CD and proceed to the partitioning step using the same username as you had before.

2 - instead of using the automatic partitioning method you have to select the manual method.

3 - then you create the partitions for the root directory and for the swap, but you just select the mounting point for the /home, using the existing one, without selecting the option to format this partition.

So, when you proceed, the partitioner will format and create root and swap, but will just mount the /home partition under root, using the existing partition.

When you start the fresh OS installation, your /home partition will be intact with all your config and personal files. Almost everything will look the same as before reinstalling, because your personal configurations will be there (like themes, panel positions, desktop background, menus and so on), but the core files of the OS will be new.

---

### Post by phantom3113 on 2009-03-19
Thank you for clearing that up for me. This option always enticed me because having to restore things after switching versions (or OSes for that matter) was always a pain in my behind. The first time I try this I'll make an "in case" backup, in case I do it wrong. :D Ok, you may resume your regular thread broadcasting now. :)

---

### Post by lovinglinux on 2009-03-19
> **phantom3113 said:**
> Thank you for clearing that up for me. This option always enticed me because having to restore things after switching versions (or OSes for that matter) was always a pain in my behind. The first time I try this I'll make an "in case" backup, in case I do it wrong. :D Ok, you may resume your regular thread broadcasting now. :)

Yep, a backup is really a good idea, specially the first time you do this. But once you do, you will see that is not complicated. I have done this after trying Intrepid. I didn't liked, so I installed Hardy again and everything worked just like before. It's really a nice feature.

---

