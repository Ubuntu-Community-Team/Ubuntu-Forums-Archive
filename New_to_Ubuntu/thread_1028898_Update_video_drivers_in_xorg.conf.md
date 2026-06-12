---
title: "Update video drivers in xorg.conf?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by bsmith52 on 2009-01-02
I have problems with my video driver on my d201dly2 intel motherboard.  I believe that I have found a solution here:


[http://ubuntuforums.org/showthread.php?t=966450&highlight=d201gly2+video](http://ubuntuforums.org/showthread.php?t=966450&highlight=d201gly2+video)

The problem is: What file do I need to modify in order to get these commands (given by mgol) to work?  He says that he has to modify xorg.  Is that the file in /etc/X11/xorg.conf?  I tried, but I wasn't able to save them (a security feature so that a novice such as myself couldn't distroy my system?).

He said that the cost was a 25% CPU usage overhead. It would be worth it, as the lines are driving me yaya.  Thanks.

---

### Post by adult swim on 2009-01-02
to edit files owned by root, such as /etc/X11/xorg.conf, you need to have root priveleges.  you can do this by running ```
gksudo gedit /etc/X11/xorg.conf
``` now you can save the settings you make.

you may want to back up your old file so if when you restart and your system is bricked you can fix.  an easy way to do this would be to first run ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```  now if you find your computer wont start up, boot the recovery mode from grub and then choose to drop to a root terminal.  from there you can enter in ```
cp /etc/X11/xorg.backup /etc/X11/xorg.conf
``` then you can type exit and continue normal boot.  hopefully it will work for you and you wont need this last little bit.

---

### Post by bsmith52 on 2009-01-02
Thanks for the proceedure.  I knew about sudo.  It just didn't occur to me that sudo could fix my not-being-able-to-write-the-file problem. Ubuntu lesson learned. Thanks. Bill

---

