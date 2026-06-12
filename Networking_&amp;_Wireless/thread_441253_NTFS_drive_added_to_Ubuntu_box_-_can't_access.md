---
title: "NTFS drive added to Ubuntu box - can't access"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by webecho on 2007-05-12
Hi Guys
First off, I'm very new to Ubuntu and linux in general, so please bear with the stupid questions.

My Aim:
To get an NTFS drive full of music and stuff to sit in my Ubuntu box which should act as a basic file server. Once I can access it from my XP computer, I don't need it to do anything but serve.

My problems:
I (think) I have managed to get the second hard disk mounted in Ubuntu 6.06.1 - fstab has 
/dev/hdb1 /mnt/ntfs ntfs ro,user, umask=0000

I managed to add a /myfiles directory to the hda1 and could access that from XP, but how do I add the myfiles directory to hdb1 and use that instead?

I don't really understand how you access hdb1 from the command prompt.

would I be better off installing a GNOME destop and trying to do it from there?

Any ideas would be great  - it's been a long day!

thanks in advance

webecho

---

### Post by sudo_nym on 2007-05-13
> **webecho said:**
> Hi Guys
First off, I'm very new to Ubuntu and linux in general, so please bear with the stupid questions.

My Aim:
To get an NTFS drive full of music and stuff to sit in my Ubuntu box which should act as a basic file server. Once I can access it from my XP computer, I don't need it to do anything but serve.

My problems:
I (think) I have managed to get the second hard disk mounted in Ubuntu 6.06.1 - fstab has 
/dev/hdb1 /mnt/ntfs ntfs ro,user, umask=0000
I've only played around with FAT32 filesystems in Ubuntu, and can't say how well NTFS is supported.  It might only be able to access these partitions as read-only.  That was the case with Linux and NTFS a while ago, don't know if things have changed since.  And if I'm not mistaken, the `ro' up there stands for read-only [rw = read-write, by the way].

So you might have to transfer the files from one machine to the other, if you want read-write access from within Linux.  [Don't know how you're doing for disk space right now, but another possibility is to copy the files off your NTFS HD, reformat it as FAT32, ext3 or something, and then put them back.]

> I managed to add a /myfiles directory to the hda1 and could access that from XP, but how do I add the myfiles directory to hdb1 and use that instead?

Do you need to add one, or can you just reconfigure the server to share files found in /mnt/ntfs instead?  That would save you some hassles with a read-only filesystem, if it can just use a directory that already exists.

> I don't really understand how you access hdb1 from the command prompt.

would I be better off installing a GNOME destop and trying to do it from there?
Would make it easier to see what you're doing, yes.

I don't know if you can install the GNOME desktop without having it load automatically though.  No, sorry; I'm sure it's possible, just don't know if it's easy to do.

Since you don't need a GUI loaded all the time for this, it would be nice to have the thing boot into console mode by default, and then if you do need one, just type **startx** at the prompt.

> Any ideas would be great  - it's been a long day!

thanks in advance

webecho

Well, that's the best I could come up with.  Hope it helps.



Cheers,

Patrick.

---

