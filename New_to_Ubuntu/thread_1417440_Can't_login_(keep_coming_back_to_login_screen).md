---
title: "Can't login (keep coming back to login screen)"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Isyaltut on 2010-02-27
Hello there, I need your help.

I can't login to my ubuntu karmic. The weird thing is that after the splash screen, it prompted to login screen (I have disable those and choose to login automatically instead before, and works there is no problem until now).
"Ok, that's weird", I thought. I type my password anyway. And then the screen goes blank, followed with "reloading postfix configuration" on it. Then, the login screen coming back. I don't know why, i type my password again (followed with another "reloading postfix configuration) and it keeps me back to login screen. 

After browsing to find more about postfix using my ubuntu live cd, it look like it is part of evolution (I don't really understand what its function though). And I suddenly remember, the last time I use my computer, I remove all evolution-related package from synaptic. I did it because I want to switch to Thunderbird instead. 

Please help me what should I do..

---

### Post by DeadSuperHero on 2010-02-27
Try changing your log-in session at the GDM splash from GNOME to an Xterm session. 

From the xterm, you can make things easier for yourself by running "sudo synaptic"

look for the evolution files you removed, try reinstalling the files and see if that doesn't allow for you to log into GNOME.

---

### Post by Gone fishing on 2010-02-27
Second time we've had this problem in a few days 

[http://ubuntuforums.org/showthread.php?t=1415097](http://ubuntuforums.org/showthread.php?t=1415097)

Postfix is a mail server - I'm not sure what it does in karmic, I installed  mdadm a raid program and postfix was a dependency odd?

---

