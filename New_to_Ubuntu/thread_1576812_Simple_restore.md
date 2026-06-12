---
title: "Simple restore?"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by mmcl on 2010-09-17
Barely-technically-agressive grandma here.  I've been wading through a re-install, upgrading to 10.04.1.  It's been slow, but most things are working (It was so easy the first time in, with 7.04!).  I stored a bunch of ffolders on a thumb drive, and have moved them back to the desk top.  Is there any quick way to restore them to their original configurations (documents within folders within folders, etc.)?

Thanks,

Martha

---

### Post by Paddy Landau on 2010-09-19
Your post is not entirely clear.

You say you saved your folders onto a thumb drive? In that case, what stops you from simply copying those folders back again?

*For future note:* If you take care to make two separate partitions, one for your root (/) and one for your home (/home), then you can upgrade or even reinstall your Ubuntu without overwriting your home partition. (There are plenty of threads on doing this in the forum, and how to convert an existing installation to two partitions. And do a backup anyway, in case of an error while upgrading or reinstalling.)

---

### Post by dcsoldschool53 on 2010-09-19
You can write a script that tar.gz or copys these files back to their orginal locations.

---

### Post by mmcl on 2010-09-20
Okay, I've finally found your replies.  Thanks to both.  


In answer to Paddy L, the folders were saved in the tar.gz format; I've moved those folders back to my desktop, but don't know how to easily restore them to their original condition in which docs are contained within folders, within folders. I have to admit that your "for future note" is almost unintelligible to me -- I have only the vaguest idea of what you're talking about.

In answer to dcsoldschools, at this point I've no idea how to write such a script.

Martha

---

### Post by Kenneth Fox on 2010-09-20
You have the folders on your desktop?

Why not just move them into your home folder?

---

### Post by Paul820 on 2010-09-20
@mmcl
> I have to admit that your "for future note" is almost unintelligible to me -- I have only the vaguest idea of what you're talking about.
Take a look at this: [http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by mmcl on 2010-09-20
"Why not just move them into your home folder? "

My concern is getting them back into the original format, rather than tar.gz. Would moving them accomplish this?

Re the link:  Thanx!

m.

---

### Post by lbrty on 2010-09-20
> **mmcl said:**
> "Why not just move them into your home folder? "

My concern is getting them back into the original format, rather than tar.gz. Would moving them accomplish this?

Re the link:  Thanx!

m.

tar.gz is a compressed file. If I understand you correctly you would like to see the actually file in the original format. Move the compressed file(s) to your home directory, right click the file(s) and click 'Extract Here' or right click and click 'Open with Archive Manager' and extract the files from there.

---

### Post by mmcl on 2010-09-21
AAAAAHHHHHH!!:KS  I KNEW there must be an easy way.  THANK YOU!!

---

### Post by Paddy Landau on 2010-09-21
Once you have *successfully* extracted the tar.gz files, you can delete the tar.gz files.

Using tar.gz is hardly the easiest way to back up. You may want to  consider alternative backup methods. (You realise, I hope, that you need  a regular backup in case your computer breaks down.)

I use [SpiderOak]("https://spideroak.com/"), which is cheap, secure and easy, cross-platform and flexible. However, you need broadband for this.

Another alternative is to use an external USB drive, which is more reliable than a USB stick and can take more data. If you go this route, you may want to check out [grsync]("apt:grsync"). grsync allows you to do a fast daily backup.

(If you prefer the command line, check out rsync and rdiff-backup for further options.)

There are more complex solutions, but these two should be a good start.

---

### Post by Dex73 on 2010-09-21
> **Paddy Landau said:**
> Once you have *successfully* extracted the tar.gz files, you can delete the tar.gz files.

Using tar.gz is hardly the easiest way to back up. You may want to  consider alternative backup methods. (You realise, I hope, that you need  a regular backup in case your computer breaks down.)

I use [SpiderOak]("https://spideroak.com/"), which is cheap, secure and easy, cross-platform and flexible. However, you need broadband for this.

Another alternative is to use an external USB drive, which is more reliable than a USB stick and can take more data. If you go this route, you may want to check out [grsync]("apt:grsync"). grsync allows you to do a fast daily backup.

(If you prefer the command line, check out rsync and rdiff-backup for further options.)

There are more complex solutions, but these two should be a good start.

Don't forget LuckyBackup. It allows you to use rsync with a simple interface instead of the command line, which I fond much easier, especially for beginners. You can download from Ubuntu Software Center or Synaptic Package Manager for free making really easy!

---

### Post by mmcl on 2010-09-21
Many thanks for all the helpful info.  Incremental progress in expanding understanding is happening....

m.

---

### Post by candtalan on 2010-09-21
grsync is a flexible, pretty simple, and basic method of doing similar to what you have just done. 

I tend to use just rsync, but grsync has a rather nice simple graphical interface.

---

### Post by mmcl on 2010-09-21
Thanks!  More  useful info.

---

