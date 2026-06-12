---
title: "Remount CD/DVD Drive"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Cola_Cartel on 2009-11-29
Hey all,

I accidentally unmounted my CD/DVD drive because I'm a moron. How do I get it back? I'm running Karmic on a Dell Latitude D520.

Thanks!

---

### Post by yeats on 2009-11-29
Have you tried just rebooting?

---

### Post by gregsmith_to on 2009-11-29
My system gets into a state sometimes where it won't autoload a CD/DVD, I have to do it on the command line (which means the unmount also has to be done on the command line). Rebooting works too, but this isn't W95, there should be a way to fix it. The disk even pops up in the 'Places' pane of the file browser, but it doesn't mount and right-clicking on 'mount' doesn't do anything.

---

### Post by Cola_Cartel on 2009-11-29
Yeah I've tried rebooting, the CD drive still won't autoload and I don't know how to find it otherwise

---

### Post by Cola_Cartel on 2009-11-29
Also nothing appears in the/media/cdrom drive or the /cdrom drive

---

### Post by gregsmith_to on 2009-11-29
(1) when you say you 'accidentally unmounted the drive', what exactly do you mean? normally you unmount the disk, not the drive. 
(2) Is this just one particular disk? Some CDR formats (UFS?) are only readable by quite recent linux versions.

You might find a useful line appearing in /var/log/messages. put the disk in, then do 'ls -lrt /var/log' to see if one of the files has a fresh timestamp, then you can do 'sudo tail /var/log/message' (or whatever file) to see what's there. This can help with all kinds of problems.

---

