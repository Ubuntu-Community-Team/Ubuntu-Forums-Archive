---
title: "Unusual Problem After Installing"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by Mossback on 2010-09-29
I installed 10.04 on my Dell laptop as a dual boot with Windows 7 a few months ago and it has worked well until last night. I booted the system and it stopped almost immediately with the message "Name Module not found" and nothing I could do would get beyond that point.

Can I fix the problem by reinstalling 10.04 or is there a way to fix the boot without reinstalling?

Thanks in advance for any help you can give.

---

### Post by attentux on 2010-09-29
Never had this problem myself, and I'm no expert, but you may want to take a look at unetbootin. It creates live USBs, and has a number of live boot loaders and utilities

---

### Post by QIII on 2010-09-29
Take a look at these:

[http://ubuntuforums.org/showthread.php?t=1501591](http://ubuntuforums.org/showthread.php?t=1501591)
[http://ubuntuforums.org/showthread.php?t=1553742](http://ubuntuforums.org/showthread.php?t=1553742)

The "Data Safe" issue is found in both.

Let us know if either of those help.


This is not a "Google it, dummy!" thing, but please take it as a bit of friendly advice and a helpful hint.  It's a great way to see if there are others who have encountered similar problems and solved them on the forum.

I found this by typing the following in Google:

```
site:Ubuntuforums.org "Module not found" Dell
```

I wish I could tell you I was really smart, but I'm not.  Us old farts have to use what we can!

---

### Post by Rubi1200 on 2010-09-29
It seems a lot of users are having issues with the recovery partition installed by Dell. Although it really should not be doing this, it appears that there are cases where it seems to be writing to the MBR, causing all kinds of problems.

My suggestion is to use a CD and backup/clone the partition so you can use it in the future and then delete it completely.

You will then have to almost certainly reinstall GRUB:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Make sure to also check the links provided above by our friend QIII

---

