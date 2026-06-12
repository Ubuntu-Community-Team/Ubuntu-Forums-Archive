---
title: "Intel to Nvidia upgrade; quick driver question"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by DOS4dinner on 2009-07-29
Ubuntu 9.04

I followed the integrated Intel driver howto thread over in multimedia/video (The safe configuration). Do I need to undo those changes, or can I just put my new card in and follow that "latest Nvidia driver thread" over in the community cafe? 

Thanks in advance!

edit: Everything works. Thanks!
END OF THREAD

---

### Post by Arup on 2009-07-29
Shouldn't effect nvidia but just for safety, I would undo all the changes and also remove Intel driver and disable Intel card in BIOS.

---

### Post by DOS4dinner on 2009-07-29
I will undo the changes then. Thanks!

---

### Post by DOS4dinner on 2009-07-29
I'm following the undo guide for the intel drivers; however, a couple of the commands aren't quite working.

The downgrade package command wants to downgrade 15, and remove 9. 

the "sudo dpkg-reconfigure xorg-xserver" gives me this:

```
Package `xorg-xserver' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg-xserver is not installed
```

Should I ignore this, and just put in the new Nvidia?

---

### Post by theozzlives on 2009-07-29
You'll have to activate the Nvidia drivers in system > administration > hardware drivers

---

### Post by DOS4dinner on 2009-07-29
> **theozzlives said:**
> You'll have to activate the Nvidia drivers in system > administration > hardware drivers

I was planning on doing it the "Latest Nvidia driver thread" way, unless activating them like that works just well (And gets the latest proprietary drivers)
edit: I'm gonna put the card in--I'll be back.

---

