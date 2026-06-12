---
title: "How do I install another hardrive and install windows on it and have a boot option?"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by arce on 2009-03-30
I currenty am using Ubuntu on my only Harddrive.

I would like to buy another HD and install XP on it. How would I be able to allow my my computer to give me a choice between booting between the 1st HD Ubuntu and the 2nd HD XP ??

---

### Post by supersonicdarky on 2009-03-30
Just add the appropriate lines to grub. It supports multiple drives. You just have to make sure that the pc boot of the drive with grub.

---

### Post by Michaelg14 on 2009-03-30
When you install XP it will set the MBR to only boot windows.  After it is installed you will have to reactivate GRUB and tell it where to locate windows.  You will have to add something like:


> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

Changing (hd0,1) to match your setup it will probably be (hd1,0).

---

### Post by arce on 2009-03-30
To get XP on the other HD should I just unplug the Primary HD with Unbuntu? I think this would be the only way in the beginning.

Also is there a step by step guide on how to do this with GRUB? I'm 2 weeks new into Unbuntu. So things are very different for me coming from an Windows backround.

---

### Post by lindsay7 on 2009-03-31
There is an option that I just learned about this past week. You can set up you system with two hard drives, one with Ubuntu and one with windows. Ubuntu will start with the grub file and windows will start with its MBR. Either drive can be removed and the system will still boot to the other. The two systems are independent of each other. There are just a few lines of code to enter in the Ubuntu grub file to make this work. Here is the forum link on this subject. Please note that there is another link to look at listed on the very last post in the link that I show.


[http://ubuntuforums.org/showthread.php?t=1107546](http://ubuntuforums.org/showthread.php?t=1107546)

---

