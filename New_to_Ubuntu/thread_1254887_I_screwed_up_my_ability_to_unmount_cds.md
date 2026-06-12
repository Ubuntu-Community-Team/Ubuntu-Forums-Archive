---
title: "I screwed up my ability to unmount cds"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by samh785 on 2009-08-31
I was messing with some terminal commands that I found that had to do with forcing my cd to eject while installing call of duty 1 in wine, and now I get this message when I try to eject the cd that's in the drive:

[IMG]http://img402.imageshack.us/img402/692/window.png[/IMG]

Please help me!

---

### Post by gsocker on 2009-08-31
Simple fix: run the unmount as root.
Fire up Terminal, and run 
```
sudo umount /media/cdrom0
```
This will take care of it. It should not be a problem afterwards
as long as you only mount CDs using the gui.
In general, if you mount from the command line,as root you must be root to unmount.
Also, with the standard mount/unmount commands, you will normally have to use sudo for both unless you tinker with configuration settings best left unmentioned in this particular forum...

---

### Post by samh785 on 2009-08-31
Thanks, that fixed it. The ability of this forum to fix my problems I run into has never ceased to amaze me.

---

