---
title: "USB recognized, but no permission to mount."
date: 2009-08-16
forum: New to Ubuntu
---

### Post by cscomp3 on 2009-08-16
When I first installed ubuntu, 8.10, usb drives mounted fine.  Then somewhere along the way, I lost permission to mount them.  I upgraded to Jaunty, hoping to fix the problem, but I still don't have permission to mount the usb drive.  The system "sees" it under PLACES -> COMPUTER as "4.1 GB Media", but when I plug it in, I get a dialogue box stating "Cannot mount volume.  You are not privileged to mount this volume."  I get the same dialogue box when I right click and try to mount it from the drop down menu.  My username is an administrator and the "Access external storage devices automatically" box is checked under SYSTEM -> ADMINISTRATION -> USERS & GROUPS.  Help!  I need to do some backups!

---

### Post by rraj.be on 2009-08-16
Try with a sudo command.

Else Open nautilus in root mode
Type the following in window opened by Pressing Alt+F2 or type this in terminal

```
sudo nautilus
```

Now you should be capable of mounting the drive without any problem

---

### Post by cscomp3 on 2009-08-18
This one is solved.  I ran **dmesg** and found where the system was trying to mount the drive.  It was trying to mount the drive to the same locaiton as an old hard drive that was no longer in the system.  I ran **sudo gedit** and took the appropriate line out of **fstab.**  The usb drive mounts just fine now.  Thanks rraj.be.  Your suggestion of using **sudo nautilus** helps get me in the right direction of how to manage this system.
 
How do I mark this as solved?

---

### Post by superprash2003 on 2009-08-18
you currently cant as the feature is disabled , but i think you could try renaming the title and adding a [SOLVED]

---

### Post by Penguin Guy on 2009-08-18
> **cscomp3 said:**
> This one is solved.  I ran **dmesg** and found where the system was trying to mount the drive.  It was trying to mount the drive to the same locaiton as an old hard drive that was no longer in the system.  I ran **sudo gedit** and took the appropriate line out of **fstab.**  The usb drive mounts just fine now.  Thanks rraj.be.  Your suggestion of using **sudo nautilus** helps get me in the right direction of how to manage this system.
 
How do I mark this as solved?
Add [SOLVED] to the start of the title and also add the tag 'solved'.

---

