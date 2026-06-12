---
title: "Where is the menu.lst file?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by P235 on 2010-02-28
I wish to change the order of OS on grub.  I cannot find it under "/boot/grub/menu.lst".  I tried to grep it without success.  Does anyone know where it is?

---

### Post by spiky001 on 2010-02-28
If your using grub 2 i think this is what you need
grep menuentry /boot/grub/grub.cfg

found it [here]("https://help.ubuntu.com/community/Grub2") hope this is what you want

---

### Post by rixtr66 on 2010-02-28
try this link; [http://ubuntuforums.org/showthread.php?t=1305399&highlight=grub2-menu.lst](http://ubuntuforums.org/showthread.php?t=1305399&highlight=grub2-menu.lst)
its got some useful information.
hope this helps!
Rick :guitar:

---

### Post by oldfred on 2010-02-28
Changing the order is not paricularly easy in grub2.

See this thread for several alternaives:
[http://ubuntuforums.org/showthread.php?t=1417587](http://ubuntuforums.org/showthread.php?t=1417587)

More info on grub2

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by P235 on 2010-02-28
Thank you all for the replies!  I agree that changing the order under grub2 is not as easy as it was before.  I will hold off on playing with grub.  Such a shame!  Grub was so simple to use and required a minimal time commitment to learn.  I hope the same in grub2's future.

---

