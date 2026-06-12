---
title: "Back in Time questions"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by Charlie Chick on 2010-10-20
Hello Everybody,

I've just discovered Back in Time and I have a few questions that the documentation doesn't appear to answer.

I notice that, in the System Tools menu, there are 2 Back in Times. One is called Back in Time and the other is called Back in Time (root). Which one do I use?

Secondly, I want to back up the whole computer - everything - and the instructions don't say how. They simply say back up what folders you want. How do I select the entire computer?

Thirdly, I have a second, internal hard drive which I want to use to back up to and have selected it in the preferences menu. However, I notice that the program doesn't always remember the destination, which is quite serious. It sometimes self selects 'media', where ever that might be! How can I get it to remember my second internal drive?

Many thanks,

Charlie

---

### Post by -kg- on 2010-10-20
By what I've read and what I (think I) understand, Back In Time is basically like Windows "Restore Points" more than actually creating a backup.  I'm not sure that you can back up your whole computer, especially if you have more than one OS on it, or want to back up the MBR.

> I notice that, in the System Tools menu, there are 2 Back in Times. One is called Back in Time and the other is called Back in Time (root). Which one do I use?

From the [Back In Time documentation]("http://backintime.le-web.org/documentation/"):

> Back In Time acts as a “user mode” backup system. This means that you can backup/restore only folders you have write access to (actually you can backup read-only folders, but you can’t restore them).

If you want to run it as root you need to use “su” (command line), “gksu” (Gnome) or “kdesudo” (KDE).

This tells me that the only reason you absolutely need to run BIT as root is during a restore, when you have read-only documents that need to be restored.  The user might have read-only access, but root will normally have all privileges.

> I have a second, internal hard drive which I want to use to back up to and have selected it in the preferences menu. However, I notice that the program doesn't always remember the destination, which is quite serious. It sometimes self selects 'media', where ever that might be!

Does your second hard drive have more than one partition on it?  I'm assuming it doesn't here, but what label, if any, is applied to that partition (your second hard drive)?  What is its mount point?  If you have that hard drive mounted to "media", that's what the BIT software is showing...the mount point.

BIT seems a good software if you want to keep things on an even keel and up to date as far as backups of data, but really, if you want to back up your whole computer, I would suggest a [Clonezilla Live CD]("http://clonezilla.org/").  That will back up any or all of your partitions and everything in them to another location (your second hard drive, if you prefer) and is restorable from those images.

A very good tutorial on its use is [here.]("http://www.dedoimedo.com/computers/free_imaging_software.html")

---

### Post by SlugSlug on 2010-10-20
from the GUI menu use back in time as root

I use this as my backup -- it's only really to be used as a file backup (home dir /etc /usr /var etc..)

A full system restore from it is not recommended I tend to reinstall and then restore my configs etc..

---

### Post by Charlie Chick on 2010-10-20
Thank you both for your replies. I read somewhere that you can back up your entire computer with BIT, hence the question. I already use Clonezilla, but it takes 5 hours to do each backup and has to be run manually. BIT works quietly in the background. My second hard drive has just one partition and I backup into a folder called 'back in time'. 

So is BIT really for just backing up your Home Folder? Surely a much better way of keeping your Home Folder data safe is to have it on a separate partition from Ubuntu, but the installer doesn't allow for that - well, it probably does, but only if you go into 'advanced' and I'm not brave enough to go there!

Thanks,

Charlie

---

### Post by SlugSlug on 2010-10-20
it's not just for home  I backup most of my folders from / -- the most useful one being /etc

I back up the whole system & once tried to do a full restore which lead to a lot of bother and wasted time as i ended up just reinstalling and restoring selected bits from /etc and /usr

---

