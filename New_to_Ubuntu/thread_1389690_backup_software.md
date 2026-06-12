---
title: "backup software"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by computerguts on 2010-01-24
what is a good backup program for ubuntu linux 9.10?

---

### Post by sisco311 on 2010-01-24
[uhelp]community/BackupYourSystem[/uhelp]
[uhelp]community/BackupYourSystem/SimpleBackupSuite[/uhelp]

---

### Post by cenzorrll on 2010-01-24
if you're willing to do some command line i very much prefer the method that's in my signature, i've used it several times to restore my computer and you don't need to install a special program in order to restore it.

---

### Post by stoogiebuncho on 2010-01-24
I love grsync.

---

### Post by texaswriter on 2010-01-24
I use sbackup [available in repositories] on both my Debian desktop and my Ubuntu laptop.... works great. When you install it it will install a sbackup config [which is where you setup automatic backups and do a manual backup, don't forget to set includes/excludes and other options].. sbackup restore is how you restore some or all of a previous backup.

---

### Post by pablo180 on 2010-01-24
I agree with texaswriter sbackup (Simple Backup) is great, almost like a system restore and has got me out of a few jams when accidentally overwriting or deleting files or folders. Runs everyday in the background and backs up only the files that have changed since yesterday.

If you want a full drive backup, I'd recommend Acronis True Image 2010 if you don't use Ext4 (it doesn't recognise Ext4 file systems - but works with Ext3). But you'll need a Windows PC to create the boot disc. I've tried CloneZilla etc, but Acronis is just simple no nonsense backups in a few clicks.

---

### Post by ikt on 2010-01-24
Back in Time is a great little utility.

---

### Post by doublewitt on 2010-01-25
> **ikt said:**
> Back in Time is a great little utility.
I like this one the best. :D

---

### Post by crjackson on 2010-01-25
> **pablo180 said:**
> I agree with texaswriter sbackup (Simple Backup) is great, almost like a system restore and has got me out of a few jams when accidentally overwriting or deleting files or folders. Runs everyday in the background and backs up only the files that have changed since yesterday.

If you want a full drive backup, I'd recommend Acronis True Image 2010 if you don't use Ext4 (it doesn't recognise Ext4 file systems - but works with Ext3). But you'll need a Windows PC to create the boot disc. I've tried CloneZilla etc, but Acronis is just simple no nonsense backups in a few clicks.

It should still work by dropping back to a sector copy.  It's much slower though.  I haven't actually tried it on an ext4 partition but I'll do so this weekend just for kicks.  I use Acronis TI 9.1 WS.

---

### Post by jtellerelsberg on 2010-02-20
An absolute beginner here... following a couple of the recommendations in this thread, I've installed grsync through the synaptic package manager. However, I can't find it through my Applications to run it. The info page on grsync [https://help.ubuntu.com/community/rsync#grsync](https://help.ubuntu.com/community/rsync#grsync) says "To start up grsync go through the following menus: Applications --> System Tools --> grsync." But "System Tools" isn't an option for me through my Applications. Does this mean my computer has some deeper problem if all the system tools are missing/hiding? (Btw, running 8.04 Hardy Heron preinstalled on a Dell XPS M1330, if that matters.) Many thanks for any help you can offer.

---

### Post by pablo180 on 2010-02-21
> **jtellerelsberg said:**
> An absolute beginner here... following a couple of the recommendations in this thread, I've installed grsync through the synaptic package manager. However, I can't find it through my Applications to run it. The info page on grsync [https://help.ubuntu.com/community/rsync#grsync](https://help.ubuntu.com/community/rsync#grsync) says "To start up grsync go through the following menus: Applications --> System Tools --> grsync." But "System Tools" isn't an option for me through my Applications. Does this mean my computer has some deeper problem if all the system tools are missing/hiding? (Btw, running 8.04 Hardy Heron preinstalled on a Dell XPS M1330, if that matters.) Many thanks for any help you can offer.

Not sure if it is the same on Hardy but you should be able to show the System Tools menu by clicking System > Preferences > Main Menu. If you click on Applications in the left hand panel, you should be able to place a tick in the box next to System Tools in the right panel so that it shows.

---

### Post by jtellerelsberg on 2010-02-21
Hi Pablo, yep, that did the trick, thank you! Curiously, that seems like it might not have been necessary after all (though I do appreciate learning how to control what shows up through Applications.) It turns out that my grsync is showing up in the Applications > Internet submenu. But I just tried and figured out that through System > Preferences, I can drag-and-drop grsnc from the Internet submenu to the System Tools submenu, so now it's where it ought to be. Again, thank you!

---

