---
title: "Help can't view files in a folder"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by serije on 2009-10-11
Hi,
I have an old hard drive that I hooked up with a usb drive adapter and I could copy most of my files over but there's one important folder that whenever I try to open it nautilus freezes and I have to close it. I tried "gksudo nautilus" and it still freezes. 

Is there any way I can get into this folder or at least view the contents of it so I can write down what's in it?

Thanks, 
Serije.

---

### Post by Boondoklife on 2009-10-11
have you tried getting to it via commandline? There might be some wierd naming or more likely an oddly formated file that ubuntu is trying to cache and display and is locking it.

---

### Post by serije on 2009-10-11
How do I view it via commandline?

---

### Post by CharlesA on 2009-10-11
Mount the drive and run ls -l on it.

If it's automatically mounted, it's in /media

---

### Post by macabrem on 2009-10-11
> **CharlesA said:**
> Mount the drive and run ls -l on it.

If it's automatically mounted, it's in /media

Of course you need to "cd" (change directory) before doing the ls -l.

From there, if I were you, I would be looking at the naming scheme as well as the file and folder permissions.

---

### Post by serije on 2009-10-11
Just tried it and it didn't work. It just displayed nothing. But I tested it on another folder on the drive and it worked fine. The drive is pretty old, could the folder be corrupted or something?

---

### Post by oldos2er on 2009-10-11
> **serije said:**
> Just tried it and it didn't work. It just displayed nothing. But I tested it on another folder on the drive and it worked fine. The drive is pretty old, could the folder be corrupted or something?

 What file system is on the drive? Running fsck (or chkdsk) on it wouldn't hurt.

---

### Post by serije on 2009-10-11
> **oldos2er said:**
> What file system is on the drive? Running fsck (or chkdsk) on it wouldn't hurt.

I ran chkdsk (It took five hours! Haha..) and it fixed it everything works great now, thank you!

---

