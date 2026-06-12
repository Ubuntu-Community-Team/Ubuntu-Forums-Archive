---
title: "How to use samba share with Simple Backup"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by DrScum on 2009-09-20
I am trying to schedule backup using Simple Backup. I am unable to select a samba share folder as destination. It's not visible although it's mounted.

What am I missing?

Using Ubuntu 9.04 on a Dell Laptop. The Samba share is located on a Linux machine using Ubuntu 8.04. I can access the samba share using a file manager.

---

### Post by Liolikas on 2009-09-20
I think it is feature request for devs.

---

### Post by DrScum on 2009-09-20
In case Liolikas is right does anyone know a backup utility which lets me define which folders to back up automatically at a set time on a set samba share?

Thanks

---

### Post by mathfeel on 2009-09-20
use cifs to mount a SMB somewhere, then use cron??

---

### Post by DrScum on 2009-09-20
Thanks for the reply. I have no idea what you are talking about. I haven't heard about neither one cifs and cron. You must know that I am one of those mouse clicking GUI corrupted former Redwood disciples which somehow got washed ashore at the Linus paradize. In my case the downadup worm gave the last push to abandon the XP ship and install Ubuntu for good [wihtout the dual boot life-belt].
This happened a week ago and I have reached a point now where I have all the software I need running, where I have all the data, e-mails, calendars, bookmarks and so forth recovered and now I am dealing with the fine tuning.
I do know my way around computers and I have been using Ubuntu on my desktop for a while but I can't handle the command line very well and I don't know cifs and cron. But am willing to learn.

---

### Post by mathfeel on 2009-09-22
> **DrScum said:**
> ...

MY BAD. CIFS (common internet file system) is the file system used in SAMBA. Suppose you have a SAMBA share at \\REMOTECOMPUTERNAME\SHARENAME, then you can issue the command:
```
mount -t cifs -o user=luke,password=ifpasswordisneeded //REMOTECOMPUTERNAME/SHARENAME /mnt/mount_point
``` And you can access it as if it's just living under /mnt/mount_point. Using an actual mount command is the most solid way to get access in my experience.

There are some GUI things that worked and failed for me before. For example, if you are using KDE and in your file manager (called Konqueror), you can simply type in the address
```
smb://HOST/SHARENAME
```
and (hopefully) will be able to browse your subnet for other computer. Similar thing is available in GNOME's file manager Nautilus. Have you try going to Places->Network? For the computer I am looking at right now, it found two other SAMBA share in the network.

With GUI, you are usually limited to the featured provided by that particular GUI frontend. So automatically scheduled copy would be hard if not impossible. This is where cron come in.

cron is a scheduling software that allow you to run any command periodically. So in this context, you can ask it to copy file from/to the mount point. gnome-crontab is a GUI for adding/removing jobs in cron.

---

