---
title: "Hard eject doesn't unmount CD/DVD"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by klemperal on 2009-11-08
My problem is that when I do a hard eject for a CD or DVD (ejecting via the actual eject button on the drive), the CD/DVD doesn't unmount.  This isn't to say that it doesn't eject, it does.  What I'm saying is that after I hard eject DVD or CD X, DVD or CD X acts as though it were never ejected and stays mounted on the desktop, nautilus side pane--I end up having to manually un-mount DVDs and CDs after I do a hard eject.  I don't have this problem when I right click a volume and choose 'eject.'  Also, I never had this problem in Jaunty--only now that I'm using Karmic.  Please let me know if there is a solution to this.

---

### Post by LewRockwell on 2009-11-08
it is a good habit to unmount stuff before removing

for thumb drives and SD cards you should give them a ten-count before removal to let them finish any activity

.

---

### Post by laluz on 2009-11-08
> **klemperal said:**
> My problem ...  Please let me know if there is a solution to this.
Previously was actually a feature. Especially for the read-write media one should let the OS finish the cached write operations before ejecting the media. The best way is to do the the ejection through the software unmount. 
I actually had a few bad problems with the Zip drives in the old days, where Windows would rewrite the FAT if one ejected the disc through the hardware button. (Just to put this into a context.)

---

### Post by LewRockwell on 2009-11-08
> **laluz said:**
> I actually had a few bad problems with the Zip drives in the old days, where Windows would rewrite the FAT if one ejected the disc through the hardware button.

Zip Drives...lol

the old days(don't know how "good" they were though)

.

---

### Post by klemperal on 2009-11-08
I'm not talking about flash drives or external hard drives--just cd/dvd roms.  There is no reason why a cd/dvd should remain mounted after it has been physically ejected and removed.  Does anyone know a fix for this?

---

### Post by maubarra on 2009-11-18
I'm having the same issue. I think the eject button should unmount the disc sice we are not talking of read/write media and well, that's why that button is there for. Also, that's how it used to work un Jaunty. Did they change it on purpose or is this a bug?

Anyone know how fix this?

---

### Post by kquinnell on 2011-01-15
Having the same problem in Maverick Meerkat.  Did anybody decide if this was a bug or a feature ?  Any work around for automatically unmounting when eject button is pressed ?  I can do it manually but I'm using the computer to play movies.  It would be nice to just be able to eject one movie, put in the next and have it auto play without having to manually unmount the disk.

---

### Post by vancouverite on 2011-01-19
Hi kquinnell,
I have the same problem (in Maverick) and found this:
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/476654](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/476654)

But the link seems to suggest that this shouldn't be a broblem in Maverick.

---

### Post by EgoGratis on 2011-03-14
This is a bug reported here:

[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/727197](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/727197)

---

### Post by EgoGratis on 2011-04-15
I upgraded to Ubuntu 11.04 today and it works like it should. Hard eject does unmount CD/DVD!

---

