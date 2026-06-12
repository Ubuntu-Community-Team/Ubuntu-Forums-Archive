---
title: "Is there a simpler way to backup"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by Mindswap1 on 2010-12-13
Hi guys! So I was wondering if there was a simpler way to backup all my songs and documents in Ubuntu instead of having to putting everything into a flash drive.I kinda sucks having to backup every six months for when the new Ubuntu release comes out or every time I mess up Ubuntu badly. I always had a nightmare backing up with windows as it sometimes corrupted the files. Oh how I hate windows lol. Anyhow I started all over with only Ubuntu installed ( and will keep it that way forever ), but was wondering if there was an easy to way back up songs and such.

---

### Post by Stunts on 2010-12-13
You might be interested in "rsync". It's a command line program ideal for backups.
If you don't like using the command line, there is always "grsync" which is a front end to rsync, but with a nice looking GUI.
Enjoy!

Edit: You can get rsync and grsync using synaptic package manager or Ubuntu's Software center.

---

### Post by A_M_S on 2010-12-13
+1 for rsync.
I'm using it with udev for [automatically backup my pen]("http://ninetynine.be/blog/category/ubuntu/") when its mounted in the system.

---

### Post by uRock on 2010-12-13
Create a separate /Home partition. I burn important data to disk very often.

---

### Post by rburkartjo on 2010-12-14
yes creating a separate home partition is always a good idea. and if for some reason you have to do a reinstall. all your preferences and important info can be accessed. all you need to do is reinstall all the apps you had installed before. just had to do a reinstall and saved my butt.

---

### Post by Megaptera on 2010-12-14
Some other options reviewed here: [http://www.techdrivein.com/2010/12/top-5-open-source-backup-software-for.html](http://www.techdrivein.com/2010/12/top-5-open-source-backup-software-for.html)

---

### Post by Mark Phelps on 2010-12-15
Actually ... I think what you're really asking is ... How do I save my files and documents so that, when I install a new Ubuntu version, I don't have to reload those files and documents?

A simple answer is ... create a data partition to hold those, migrate the files and documents there, and when you install a new Ubuntu version, that partition does not change.

---

### Post by Mindswap1 on 2010-12-15
The thing is I always do the option in the install that says Install Ubuntu On The Entire Disk Drive, and so it would end up deleting my stuff anyways. I can't go the manually specify partitions option cause I'm not good at that stuff.

---

### Post by Megaptera on 2010-12-16
> **Mindswap1 said:**
> I can't go the manually specify partitions option cause I'm not good at that stuff.

I used to think that too - it seemed way too complicated. However I've used this guide (with screenshots) and it was a breeze:

[http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)  they say "That’s when a fundamental knowledge of disk partitioning on a Linux system comes in handy, and that’s why, for those without that knowledge, this guide has been written."

But if you're not feeling confident about it, go with the external storage method aleady suggested.

---

### Post by mastablasta on 2010-12-16
> **Mindswap1 said:**
> The thing is I always do the option in the install that says Install Ubuntu On The Entire Disk Drive, and so it would end up deleting my stuff anyways. I can't go the manually specify partitions option cause I'm not good at that stuff.
 
 
on a side note here... Linux Mint (based on Ubuntu) is always upgraded by a fresh install. They have a very good guide on how to change your home folder ot a partition. they also developed a good backup tool (can also be used in Ubuntu) so that people "upgrade" easy.

---

### Post by freesitebuilder on 2010-12-16
I only do a clean install when I have to - normally I upgrade. But for backup before either, I use rsync/grsync as previously mentioned. I also use Dropbox to store files that I want to sync between machines, or access from another machine, or that are very important. (Just in case my hard drive and external drive decide to crash on the same day!)

---

