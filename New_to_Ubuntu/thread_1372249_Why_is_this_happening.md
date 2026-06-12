---
title: "Why is this happening???"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by TheMustangZone on 2010-01-04
I've been using Ubuntu for quite a while now and love it, except for this one thing.  I'm using version 9.04 on my machine and I'm NOT dual booting.  I completely removed the dreaded windows.  Here's what keeps happening, though.  Everytime I use the Add/Remove feature in applications to install a new app. and restart my machine, I lose my GRUB and it will not load Ubuntu.  I've been through the forums and have successfully reinstalled GRUB several times now, but why does this keep happening?  Do I have to just expect to have to do this everytime I want to use a new app.?  Is there a way to shield or protect the GRUB file to prevent this?  Thanks for any help.
 
Rob

---

### Post by J V on 2010-01-04
ehh...

Which grub file is it deleting?

Sounds like you need a full system reinstall... md5 the disc next time...

---

### Post by TheMustangZone on 2010-01-04
> **J V said:**
> ehh...
 
Which grub file is it deleting?
 
Sounds like you need a full system reinstall... md5 the disc next time...
 
Thanks for the reply.  I get the error that says "unable to load GRUB" with various error numbers 15, 17, 27, etc.  I was wondering if I needed to just start over and reinstall everything.  What do you mean by "md5 the disc"?

---

### Post by J V on 2010-01-04
Its possible the disc you got was corrupted during download or burning, I would suggest making a new one and doing a fresh install, what you are getting isn't normal...

Get karmic while you're at it, new version of grub altogether...

---

### Post by TheMustangZone on 2010-01-04
> **J V said:**
> Its possible the disc you got was corrupted during download or burning, I would suggest making a new one and doing a fresh install, what you are getting isn't normal...
 
Get karmic while you're at it, new version of grub altogether...
 
Thanks a lot for the help.  I recently downloaded 9.10, so I might just go ahead and do a fresh intstall with it.  I've been hesitant to use 9.10 because of what I've been reading about it on the forums.  It seems there are quite a few bugs.  What do you think about 9.10?  Should I be concerned?

---

### Post by philinux on 2010-01-04
Been running 9.10 for ages. No crashes or anything unexpected. It's rock solid here.

---

### Post by CharlesA on 2010-01-04
> **philinux said:**
> Been running 9.10 for ages. No crashes or anything unexpected. It's rock solid here.

Same here. Works fine so far. (Just make sure it's compatible with yer hardware, by booting off the liveCD first)

---

### Post by TheMustangZone on 2010-01-04
Thanks again for all of the input.  Sounds like I will be upgrading after I back up all of my stuff.  :)  9.10 it is.  It's this type of support that makes me love using Ubuntu so much.  I really appreciate it.

---

### Post by warfacegod on 2010-01-04
> Thanks a lot for the help. I recently downloaded 9.10, so I might just go ahead and do a fresh intstall with it. I've been hesitant to use 9.10 because of what I've been reading about it on the forums. It seems there are quite a few bugs. What do you think about 9.10? Should I be concerned?

Sure there are bugs but all OS's have them. 9.10's real issue, in my opinion, is that many of the default utilities lost allot of functionality. Login Manager, for instance, now has only three or for options and no way to change splash screens. Or, Ubuntu Software Center was put into service way too soon, at least, if it works, you can use it to install Add/Remove.

This sort of thing is typical of .10 releases. The .10's tend to get used as stepping stones for .04's.

---

### Post by 3rdalbum on 2010-01-04
It sounds to me like the problem is that the package management system is running something to do with GRUB - either it's always attempting to configure a GRUB package, or there's a post-installation trigger that's causing something to happen to GRUB.

Installing 9.10 should probably fix this, as it's probably started happening in response to something.

---

### Post by TheMustangZone on 2010-01-04
> **3rdalbum said:**
> It sounds to me like the problem is that the package management system is running something to do with GRUB - either it's always attempting to configure a GRUB package, or there's a post-installation trigger that's causing something to happen to GRUB.
 
Installing 9.10 should probably fix this, as it's probably started happening in response to something.
 
Thanks again for the help.  It sounds like everyone has confirmed what I was hoping I wouldn't have to do, reload the OS.  Oh well, it's not the first time and I'm sure it will not be the last. :)

---

