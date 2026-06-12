---
title: "Help upgrade to 11 and now it doesn't work!"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by Singcrazy51 on 2011-07-15
:confused: I clicked yes to upgrade
now all I get is a black screen wit the following:
 
ERROR: SYMBOL NOT FOUND: 'GRUB_ENV_EXPORT' 
grub rescue>
 
I am a complete computer nubie so I have no idea what ths means or how to fix it!
can someone please help? I had to use myfriend's  computer to come here and post!
thank you!!

---

### Post by sikander3786 on 2011-07-15
Ubuntu was installed inside Windows using the Wubi installer? If yes, please take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If it was a proper install, please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

And most importantly, did the upgrade process complete successfully?

---

### Post by Singcrazy51 on 2011-07-15
> **sikander3786 said:**
> Ubuntu was installed inside Windows using the Wubi installer? If yes, please take a look at this thread.
 
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
 
If it was a proper install, please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.
 
[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)
 
And most importantly, did the upgrade process complete successfully?
  
It wasn't inside windows- it just popped up, i had to put in my pass word and it said upgrade successful but when it rebooted all i got was the error message
  i down loaded the bootscript info onto a flash drive but it won't read it - I even tried changing the BIOS  to removable drive but it still won't work

---

### Post by adriangzz on 2011-07-15
Never got that problem. I did exactly the same Wubi>10.10 upgraded to 11.04, sorry I cant help that much. But i found this, here's a thread with people with the same problem, some suggestions, maybe it will help you.

[http://ubuntuforums.org/showthread.php?t=1742655](http://ubuntuforums.org/showthread.php?t=1742655)

---

### Post by Singcrazy51 on 2011-07-15
> **adriangzz said:**
> Never got that problem. I did exactly the same Wubi>10.10 upgraded to 11.04, sorry I cant help that much. But i found this, here's a thread with people with the same problem, some suggestions, maybe it will help you.
 
[http://ubuntuforums.org/showthread.php?t=1742655](http://ubuntuforums.org/showthread.php?t=1742655)
 
 
Thanks !

---

### Post by ajgreeny on 2011-07-15
Don't download the boot-info-script onto a USB drive!

You need to boot to a live CD/USB version of ubuntu, then download the script from sourceforge and run it from the folder to which it downloaded.  It will produce a RESULTS.txt file which you should copy back here in code tags (the # in the toolbar at top of reply entry box).  You need to do all this without rebooting after downloading the script or it will be gone, and you'll have to start again.

---

### Post by Singcrazy51 on 2011-07-15
> **ajgreeny said:**
> Don't download the boot-info-script onto a USB drive!
 
You need to boot to a live CD/USB version of ubuntu, then download the script from sourceforge and run it from the folder to which it downloaded. It will produce a RESULTS.txt file which you should copy back here in code tags (the # in the toolbar at top of reply entry box). You need to do all this without rebooting after downloading the script or it will be gone, and you'll have to start again.
 
I have no idea what any of that means!

---

