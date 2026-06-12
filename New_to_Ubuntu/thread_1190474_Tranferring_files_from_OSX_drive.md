---
title: "Tranferring files from OSX drive"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by poubelle on 2009-06-17
Hi all,

I posted over in the Networking board yesterday, but my thread has already been pushed back to page 6 with no replies (and only 19 views!), as most people over there seem to be interested in their Internet connection, as opposed to networking two computers. I thought I'd post here because I am new to Ubuntu so... who knows.

My thread is over here:
[http://ubuntuforums.org/showthread.php?p=7470366](http://ubuntuforums.org/showthread.php?p=7470366)

Is short, I have an OSX hard drive and I'd like to transfer my files from it over to my Ubuntu desktop, but my desktop hardware is fairly limited, and I can't boot the Mac. Any advice would be really helpful.

Thanks!

---

### Post by treesurf on 2009-06-17
You could try putting the mac hard drive in your desktop, boot from the Ubuntu LiveCD and then transfer the files you want to move onto a USB flash drive, if you have one.


Is it possible to put the mac hard drive as a slave drive in your desktop?

---

### Post by DGortze380 on 2009-06-17
The hard drive from your Mac is likely formatted HFS+ and Journaled.

Just plug the drive into the Ubuntu computer and you should be able to mount it Read Only without a problem and copy your files off.

---

### Post by mikechant on 2009-06-18
You could buy an external USB casing for it (not very expensive) and when you've finished transferring the files, reformat it as ext3 (or other filesystem of choice) and use it as a plug in backup drive.

---

