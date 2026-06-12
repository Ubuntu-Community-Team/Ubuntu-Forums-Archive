---
title: "Restore points and Backups"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Uubnewb on 2009-01-31
Is there a way to create restore points, or to backup my applications in Ubuntu 8.10?

That way I don't have to download everything again if I need to re-install Ubuntu.

---

### Post by gn2 on 2009-01-31
Yes, you can use various tools to create images of your system, one such is [Partimage]("http://www.partimage.org/Main_Page") which can be installed using Add/Remove or Synaptic.

Another option is [Back In Time]("http://www.le-web.org/back-in-time/").

---

### Post by kaibob on 2009-01-31
> **gn2 said:**
> Yes, you can use various tools to create images of your system, one such is [Partimage]("http://www.partimage.org/Main_Page") which can be installed using Add/Remove or Synaptic....

As noted, no restore. In addition to Partimage, you may want to have a look at the following disk imaging utilties:

Clonezillla
[http://www.clonezilla.org/](http://www.clonezilla.org/)

Ghost for Linux
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

I have personally used Clonezilla, and it works well, although grub issued error messages after a restore. I have used Acronis True Image for many years, and it also works well, but you have to pay for it.

---

### Post by Uubnewb on 2009-02-01
Thanks guys, this is great!

I've only skimmed through those four sites but I think these will do nicely.  Correct me if I'm wrong but it looks like these programs save your settings, programs etc to a file which you can then backup.  If this is true it will be much more flexible than Window's System Restore.

Again, thanks, I really appreciate this.

---

### Post by HotShotDJ on 2009-02-01
> **kaibob said:**
> I have personally used Clonezilla, and it works well, although grub issued error messages after a restore.My bet is that the UUID's for your partitions changed between your backup and your restore.  That will cause grub problems.  Its pretty easy to fix.  You just need boot using the Ubuntu installation CD -- then run the following to determine the new UUID:```
blkid
```You want the UUID for your / partition (and possibly other partitions if you dual-boot).  Now, mount the / partition for Linux, and edit /boot/grub/menu.lst and fix all the UUID entries.

---

### Post by kaibob on 2009-02-01
> **Uubnewb said:**
> ...Correct me if I'm wrong but it looks like these programs save your settings, programs etc to a file which you can then backup....
I've only used Clonezilla and True Image, and they both create one file as you note. I believe that the other programs do the same thing.

Each file contains an exact image of the partition or drive. If you restore this file image, it gets you back to exactly where you were when the file was made. 

Initially, I save these file images to an external hard drive, and about once a month save a copy for archival purposes to a DVD. And, I always create a file before making any major changes to my system.

You have to spend a bit of time to become familiar with these programs, but it is time well spent in the long run.

---

### Post by kaibob on 2009-02-01
> **HotShotDJ said:**
> My bet is that the UUID's for your partitions changed between your backup and your restore....
Thanks, I've been meaning to give Clonezilla another try; I'll check the UUID's as you suggest.

---

### Post by sanemanmad on 2009-02-01
I dont see anyone mention the best tools of all.

[Tar]("http://man.he.net/?topic=tar&section=all"), [DD]("http://man.he.net/?topic=dd&section=all"), [CPIO]("http://man.he.net/?topic=CPIO&section=all")

You can google example of these uses or look here at some other free ideas...
[Other examples that work]("http://www.linux-backup.net/Example/")

these are very handy tools and a simple crontab, ssh etc can go a long way.

While you can easily choose some software to do this, I only suggest these other methods; knowing myself, I use an Open-Source Os because of the endless possibilities and flexibility to create my own custom script... That's all

---

### Post by Uubnewb on 2009-02-01
As always I am amazed by the amount of options.  That'a one thing I absolutely LOVE about open source.  It's sometimes a little difficult to get used to, but sertainly worth one's while.

Thanks once more for the help.

---

### Post by hyper_ch on 2009-02-01
well, the downloaded and installed packges (through synaptic, adept, apt-get, ....) are in /var/cache/apt/archive
So you can backup the .debs in there

computer-wide config stuff is in /etc

personal files are normally in /home

If you have mysql you also want to save /var/lib/mysql - only make copies of the binarie database files when mysql is not running, use mysqldump to create .sql files while mysql is running

You can also create a simple list of installed packages and then use that list to re-install the applications.

So that will get you quite quickly back on track.

---

### Post by MrKlean on 2009-02-01
I like remastersys the best.  It makes a live cd of yer system, which you can then install !!

---

