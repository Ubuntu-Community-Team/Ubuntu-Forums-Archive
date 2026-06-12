---
title: "[SOLVED] Backing up Jpilot data"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by zaivala on 2009-01-01
Every time I do an uninstall, I forget that all my calendar/schedule data is in Jpilot.  I don't have a way of backing this up first... that I know of.  Does anyone have any hints here?

Most of my data (documents, music, etc.) is on my external hard drive.  I've had enough virtual crashes that I've learned to do this to save my data.  Is there a way to move Jpilot data, or maybe Jpilot itself, to that drive?

---

### Post by blueridgedog on 2009-01-01
There is a plugin for jpilot called jpilot-backup...google jpilot-backup and that shoudl get you down the right road.

Alternatively you can take a look at ~/.jpilot, the data may be there and could be copied prior to re-installing.

---

### Post by zaivala on 2009-01-01
> **blueridgedog said:**
> There is a plugin for jpilot called jpilot-backup...google jpilot-backup and that shoudl get you down the right road.

Alternatively you can take a look at ~/.jpilot, the data may be there and could be copied prior to re-installing.

I opened up Synaptic and looked for it.  Sure enough, it was there waiting to be downloaded and installed.  Thanks so much!

---

### Post by zaivala on 2009-01-04
New problem.  I downloaded and installed JPilot Backup.  But I can't find it in my menus.  Do I have to manually add it to them, or what?  Sorry to sound so much like a Windoze user, but I'm still getting used to this.

---

### Post by blueridgedog on 2009-01-04
I think it is a pluggin for jpilot, so perhaps you can find it inside there...I don't have jpilot, so I can verify.

---

### Post by zaivala on 2009-01-04
> **blueridgedog said:**
> I think it is a pluggin for jpilot, so perhaps you can find it inside there...I don't have jpilot, so I can verify.

You're right, it's in the plugin menu.  Thanks for the tip.  However, I can't find anything that lets me set where the backup is done TO.  I appreciate that you're not a Jpilot user; thanks for your help.

---

### Post by blueridgedog on 2009-01-04
If you enable the plugin, which may be enabled by default, you should get to some menu.

Take a look at the instructions for the plugin:

[http://jasonday.home.att.net/code/backup/README](http://jasonday.home.att.net/code/backup/README)

(read the entire thing...it may prevent you from an opps).

Particularly:

USAGE

Usage is pretty straightforward.  After installing jpilot-backup you should
have a new menu item in the "Plugins" menu called "Backup".  Selecting this
menu item will display the Backup preferences.  From here, you can configure
which Palm apps/databases to backup, how often to backup, how many archives
to keep, and whether to backup new databases or not.  Changes take place
immediately and are saved automatically.

TIP: The first time you use jpilot-backup, it will by default backup every
application and database on your Palm.  Depending on what you have installed
on your Palm, this can take quite a long time.  To avoid this, uncheck the
"Backup new databases" checkbox before your first sync; this will store all
of your Palm apps and databases in the inactive list without actually
retrieving them.  You can then decide which databases you want to backup
and which to ignore, then sync again.

---

### Post by zaivala on 2009-01-04
> **blueridgedog said:**
> If you enable the plugin, which may be enabled by default, you should get to some menu.

Take a look at the instructions for the plugin:

[http://jasonday.home.att.net/code/backup/README](http://jasonday.home.att.net/code/backup/README)

(read the entire thing...it may prevent you from an opps).

Particularly:

USAGE

Usage is pretty straightforward.  After installing jpilot-backup you should
have a new menu item in the "Plugins" menu called "Backup".  Selecting this
menu item will display the Backup preferences.  From here, you can configure
which Palm apps/databases to backup, how often to backup, how many archives
to keep, and whether to backup new databases or not.  Changes take place
immediately and are saved automatically.

TIP: The first time you use jpilot-backup, it will by default backup every
application and database on your Palm.  Depending on what you have installed
on your Palm, this can take quite a long time.  To avoid this, uncheck the
"Backup new databases" checkbox before your first sync; this will store all
of your Palm apps and databases in the inactive list without actually
retrieving them.  You can then decide which databases you want to backup
and which to ignore, then sync again.

OK.  What this shows is that this function is not what I need.

Jpilot Backup apparently backs up my PalmPilot to my computer.  I don't HAVE a PalmPilot -- I'm using Jpilot because it is the best organizer I've found yet for Ubuntu.  I'm trying to back up my data which is already on my computer, to an external hard drive (so I don't have to enter all the data on a reinstall of Ubuntu -- you would have seen this if you had read the earlier posts in this thread).

When I run Jpilot and select Backup, it brings up a box of "Databases To Backup" (and another of "Databases To Ignore").  Since the database I want to back up is already on the computer, the box is blank.  I am left with no further options.

---

### Post by blueridgedog on 2009-01-04
Ok, then the simple approach would be to backup the files in the jpilot directory.  In your home directory, you shoudl have a directory called .jpilot (the dot in the front makes it hidden).  You can view it by running your file browser (nautilus) and then selecting view and show hidden files.  You should see it then and you can simply copy it and past it to a location that suits you for a backup.

---

### Post by zaivala on 2009-01-04
> **blueridgedog said:**
> Ok, then the simple approach would be to backup the files in the jpilot directory.  In your home directory, you shoudl have a directory called .jpilot (the dot in the front makes it hidden).  You can view it by running your file browser (nautilus) and then selecting view and show hidden files.  You should see it then and you can simply copy it and past it to a location that suits you for a backup.

I was wondering how those hidden files were hidden.  Yup, it's there.  Thank you...

---

### Post by blueridgedog on 2009-01-04
Sorry for making this so complex, but many paths lead to "incidental learning" and that is not such a bad thing.

---

