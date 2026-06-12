---
title: "Cannot unmount a local secondary harddrive"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by pbateman on 2009-09-20
I need a bit of help unmounting a local disk. This is a secondary harddrive formatted in NTFS. It shows up in my desktop as Local Disk, but when I right click and choose 'unmount volume' I get an error saying 'You are not privileged to unmount the volume 'Local Disk'"
I could swear that I was able to do this before but who knows I might be confused.
I went into Terminal and tried using the umount command and I get a message saying "umount: Local is not mounted (according to mtab)"
Is there something I am doing wrong? and why would it say Local is not mounted...when the drive name is Local Disk...could it be somehting with the name thats causing an issue? I am able to unmount other drives such as USB external harddrives and flash drives with no problem.
Thanks!!

---

### Post by erilidon on 2009-09-20
Have you tired to unmount it with gksu nautilus?

Also I have heard that linux has problems with drive names that have a space in them (though I have never tried)... you could try using tune2fs to rename it

OR if you have windows installed rename it from there.

---

### Post by pbateman on 2009-09-20
Thanks! That worked, tried tru gksu nautilus and was able to unmount it that way. Guess not as easy as just right clicking but at least there's a way around it.
Thanks again!

---

