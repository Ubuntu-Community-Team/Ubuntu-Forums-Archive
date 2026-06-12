---
title: "How can I make certain disk partitions completely disappear from Ubuntu?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by manwood on 2010-05-26
I have just setup a dual boot with windows 7 and ubuntu 10.04. The windows partitions appear in the places menu. I want to remove them (hide them from Linux completely) - I definitely don't want to be accidentally tampering with windows partitions outside of windows. 
 
I commented out the entries in the fstab file but on reboot the entries are back and the partitions are still available in places.. any suggestions?
 
thanks

---

### Post by sgosnell on 2010-05-26
You can't.  Linux sees all drives and partitions attached to the machine.  So does every other OS I know of.  That's part of its job.  Just be careful about what you do.  That's part of your job.

---

### Post by mikewhatever on 2010-05-26
sgosnell is right, you can't hide the partitions completely, as long as they are on a connected hdd. That said, there are ways to make partitions not appear on the left panel in Nautilus. If that gives you piece of mind, try the link below.
[http://ubuntuforums.org/showthread.php?t=1305383](http://ubuntuforums.org/showthread.php?t=1305383)

---

### Post by manwood on 2010-05-27
thanks guys

---

