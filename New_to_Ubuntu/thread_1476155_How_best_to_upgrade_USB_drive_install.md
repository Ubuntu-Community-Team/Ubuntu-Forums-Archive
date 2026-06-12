---
title: "How best to upgrade USB drive install?"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by DocWu on 2010-05-07
I've got Ubuntu NBR 9.10 running on a USB stick and working the way I want. I'd like to upgrade to 10.04, but before I do, what is the best way to go? I'd like to preserve all my settings - password, wireless settings, Firefox customizations, etc. Is there a way to do this?

I don't know if I can use the update manager with the USB install. I don't think there is enough room.

It's easy enough to redo the whole thing with the USB creator, but then I'm starting from square one again as far as all my customizations. It's not a lot of work at this point, but the more I use it and the more time I invest in it, the more work it gets to be.

I wonder if there is an easy way to back up those things?

---

### Post by narendraD on 2010-05-07
Best bet is to do a Fresh install AFTER you back up all your Personal Data as well as Personalised settings. Copy all the dot folders and files you can see in your /home directory to somewhere safe (meaning other than the USB) then do a fresh install

---

### Post by DocWu on 2010-05-07
> **narendraD said:**
> Best bet is to do a Fresh install AFTER you back up all your Personal Data as well as Personalised settings. Copy all the dot folders and files you can see in your /home directory to somewhere safe (meaning other than the USB) then do a fresh install

Thanks. That's what I needed to know. Just one more thing, what do you mean by "dot folders?" Do they begin with a "." ?

---

### Post by Vined Adobo on 2010-05-07
[QUOTE=DocWu;9256646]I've got Ubuntu NBR 9.10 running on a USB stick and working the way I want. I'd like to upgrade to 10.04, but before I do, what is the best way to go? I'd like to preserve all my settings - password, wireless settings, Firefox customizations, etc. Is there a way to do this?


Back up, back up, and just in case you forget to back up, back up!  Now is a good time to make a separate partition for your home directory.  There are very good tutorials to do this.

My wife hated the cluttered ReMix desktop.  Since about the only difference between regular desktop and remix is the cluttered remix desktop, just install (or upgrade to Lucid.)  You can use Synaptic Package Manager and add the cluttered desktop used on netbooks.  My wife didn't like it and I don't like it, but I don't use her netbook.

To get Remix screen, go to synaptics and add remix-launcher (along with dependencies.) You can remove later if you don't like it.

---

### Post by narendraD on 2010-05-07
Just one more thing, what do you mean by "dot folders?" Do they begin  with a "." ?

YES. They do begin with a "."

---

### Post by narendraD on 2010-05-07
Now is a good time to make a separate partition for your home directory.   There are very good tutorials to do this.

This is the best advice. Pl consider this seriously.

---

### Post by cuberts on 2010-05-07
> **DocWu said:**
> I've got Ubuntu NBR 9.10 running on a USB stick and working the way I want. I'd like to upgrade to 10.04, but before I do, what is the best way to go? I'd like to preserve all my settings - password, wireless settings, Firefox customizations, etc. Is there a way to do this?

I don't know if I can use the update manager with the USB install. I don't think there is enough room.

It's easy enough to redo the whole thing with the USB creator, but then I'm starting from square one again as far as all my customizations. It's not a lot of work at this point, but the more I use it and the more time I invest in it, the more work it gets to be.

I wonder if there is an easy way to back up those things?The easiest way to do this is by using pendrive linux, which basically installs the whole distro by itself. Click [here ]("http://www.pendrivelinux.com/")to go to pendrive linux

---

### Post by DocWu on 2010-05-08
> **cuberts said:**
> The easiest way to do this is by using pendrive linux, which basically installs the whole distro by itself. Click [here ]("http://www.pendrivelinux.com/")to go to pendrive linux

Yes, that's what I'm doing. My question is what and how do I back up the settings I customized in the old version so that I can import them into the new version.

As far as my home directory, I can't find a thing. /home has one subdir, ubuntu (the default user) and contains subdirs like Desktop, Music, Pictures, etc. All are empty at this point. I don't see any thing that could be configuration.

At this point, somewhow the 9.10 stick got corrupted, so I went ahead and created the new 10.04 installation. But I'd like to find out how to save things for future reinstallations. Apparently the installation using the pendrive linux installer is different enough from a standard install to a partition, that traditional advice doesn't apply. 

I'm happy at least, that at last I can get perisistence to work...

---

### Post by Vined Adobo on 2010-05-08
> **DocWu said:**
> Yes, that's what I'm doing. My question is what and how do I back up the settings I customized in the old version so that I can import them into the new version.

As far as my home directory, I can't find a thing. /home has one subdir, ubuntu (the default user) and contains subdirs like Desktop, Music, Pictures, etc. All are empty at this point. I don't see any thing that could be configuration.

At this point, somewhow the 9.10 stick got corrupted, so I went ahead and created the new 10.04 installation. But I'd like to find out how to save things for future reinstallations. Apparently the installation using the pendrive linux installer is different enough from a standard install to a partition, that traditional advice doesn't apply. 

I'm happy at least, that at last I can get perisistence to work...


Click on places > Home Folder.  Click on View > Show Hidden Files.  You will be greeted with a whole bunch of files preceded by a dot (the UNIX way to hide a file.)  Select and copy everything and paste to a memory stick or write to a CD.  Make sure they actually get there.  Home directory is now backed up.  If you want to compress the files or back up the whole system, see this excellent post:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I normally just back up the home directory.  When you do a clean install, partition manually.  Make a swap partition of at *least* twice the size of your RAM.  I use 3 GB.  Make a partition of about 20-40 GB for your root directory and give it a mount point of /  .  Use the rest of the drive (if you want) to make a home partition and give it a mount point of /home .  In future upgrades, do NOT format this partition.  In case of problems, of course, always back up BEFORE you do anything else.

When you do clean installs, your / partition can be formatted or not.  If you don't format every time, the information in the directories will be lost anyway.

I like to format my / partition and not format my /home partition.  Some of your special apps will be lost, but your configs will be just fine as they are in /home.  Just re-install the apps with Synaptic as you need them 

This works well for me.  your and other's results may be different.

Dave

---

### Post by DocWu on 2010-05-08
> **Vined Adobo said:**
> Click on places > Home Folder.  Click on View > Show Hidden Files.  You will be greeted with a whole bunch of files preceded by a dot (the UNIX way to hide a file.)  Select and copy everything and paste to a memory stick or write to a CD.  Make sure they actually get there.  Home directory is now backed up.  If you want to compress the files or back up the whole system, see this excellent post:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Thanks. I'll try that to see the hidden folders.

> I normally just back up the home directory.  When you do a clean install, partition manually.  Make a swap partition of at *least* twice the size of your RAM.  I use 3 GB.  Make a partition of about 20-40 GB for your root directory and give it a mount point of /  .  Use the rest of the drive (if you want) to make a home partition and give it a mount point of /home .  In future upgrades, do NOT format this partition.  In case of problems, of course, always back up BEFORE you do anything else.

When you do clean installs, your / partition can be formatted or not.  If you don't format every time, the information in the directories will be lost anyway.

I like to format my / partition and not format my /home partition.  Some of your special apps will be lost, but your configs will be just fine as they are in /home.  Just re-install the apps with Synaptic as you need them 

This works well for me.  your and other's results may be different.

Dave

Bear in mind, I'm talking about a USB stick install and I don't do any partitioning/formatting, the installer does all that. I really think it's going to be hard to make 20-40GB partition on a 2GB USB stick.

What I can do and should be enough, if it works, is to back up the /home folder on the main disk drive.

---

