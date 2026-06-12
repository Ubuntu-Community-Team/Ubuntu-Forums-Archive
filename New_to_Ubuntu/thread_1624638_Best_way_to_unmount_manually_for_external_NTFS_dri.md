---
title: "Best way to unmount manually for external NTFS drive"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by Orographic on 2010-11-18
Hi all,

I had a problem copyng my wife's Windows XP files to Maverick, which made my external NTFS drives stop copying ( I had failures with both of them) and disappear from Nautilus. I then could not shut Maverick down. I have been doing this for two years with no problems until the other day but then both of my external drives would not finish copying her 8GB MyDocuments file.

[http://ubuntuforums.org/showthread.php?p=10130489#post10130489](http://ubuntuforums.org/showthread.php?p=10130489#post10130489)

I'm just wanting to know the best way to unmount an external drive from terminal? If this problem indeed, happens again. 

sudo unmount /media/external   ?

---

### Post by Mark Phelps on 2010-11-18
I don't know about "best" way ... but using the mount/unmount commands is much the same as doing it through Places -- except that in Places, you get the option to specifically choose Safe Removal -- which, for an external drive that is this touchy, would be what I would recommend.

---

### Post by Orographic on 2010-11-18
Hi there, thanks for your reply.

You might have missed my comments that I have been doing this exact same form of copying with the same drives for two years with no problems so the drives are not touchy at all. It was only a problem for the first time, the other day.

I've just noticed an update in 10.10 for Nautilus today that is for a bug where drives crash and also wont unmount properly, this could be very much related to my problem.

I've also found that by doing:

sudo fdisk -l

I can get a list of my attached external drives and then do:

sudo umount /dev/sdg1 (my USB stick in this example)

and could also use a similar entry for my external USB hard drives after getting their correct name.

When this problem occured earlier this week (a crash, whilst copying from an external NTFS drive) I may have been able to do the above, that is, unmount manually, as Maverick was still working fine. Maverick only crashed on shutdown.

I hope my research so far may help others.

---

