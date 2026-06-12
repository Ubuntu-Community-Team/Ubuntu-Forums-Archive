---
title: "Reducing Windows XP partition"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by Night_Heron on 2009-12-23
Recently the random idea to introduce myself to the world of Linux struck my head, so I bought some magazine containing the CD for Ubuntu 9.10. I got the installation process to work fine up to a point and I think I understand the manual installation process based on what I've read from the magazine and 2 or 3 online tutorials, but there is one thing that I am not sure of.

It says that my free space is 8 **M**B.....kinda a bit too....low...
What would happen if I selected the Windows XP partition and reduced it by, say, 25 GB (that would be a decent amount for Ubuntu, right?). How safe is this to XP? There would still be 30 GB free space left under the XP partition. I really do not want to be spending time reinstalling my PC and most likely conversing with tech support over the phone if my computer ends up getting corrupted over my experimentation. 

Also, what exactly happens if I just select the first option? Would this be better for someone with null experience like me? Would both operating systems still function the same as if I did it manually? Are there any risks specifically associated with the automatic? :confused:

---

### Post by spiderbatdad on 2009-12-23
In my opinion the safest way for a beginner (like me) is to use gparted live cd. I would burn a copy of that. Then defrag windows, even if it says it doesnt need it. Shutdown and fire up gparted live. Pretty simple user interface, should be self explanatory. Shrink one and grow the other...within reason.

---

### Post by viper250 on 2009-12-23
windows xp has a storage manager that may let you resize your partition but I highly  recommend backing up your data first.  
second do you have your setup disks or the option to create them?
make sure you have these on hand so you can restore your system.

---

### Post by raymondh on 2009-12-23
> **Night_Heron said:**
> Recently the random idea to introduce myself to the world of Linux struck my head, so I bought some magazine containing the CD for Ubuntu 9.10. I got the installation process to work fine up to a point and I think I understand the manual installation process based on what I've read from the magazine and 2 or 3 online tutorials, but there is one thing that I am not sure of.

It says that my free space is 8 **M**B.....kinda a bit too....low...
What would happen if I selected the Windows XP partition and reduced it by, say, 25 GB (that would be a decent amount for Ubuntu, right?). How safe is this to XP? There would still be 30 GB free space left under the XP partition. I really do not want to be spending time reinstalling my PC and most likely conversing with tech support over the phone if my computer ends up getting corrupted over my experimentation. 

Also, what exactly happens if I just select the first option? Would this be better for someone with null experience like me? Would both operating systems still function the same as if I did it manually? Are there any risks specifically associated with the automatic? :confused:

See this thread, particularly presence1960's post (#3)

[http://ubuntuforums.org/showthread.php?t=1356282](http://ubuntuforums.org/showthread.php?t=1356282)

Before installing ubuntu, run/boot into XP and make sure all is ok.  Also, in XP, turn page file and system restore on again.

Have a working/tested back-up of your files.

Regards,

---

