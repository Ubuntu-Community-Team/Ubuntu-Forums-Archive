---
title: "Installed WUBI-can't change screen resolution?"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by musiclover01 on 2011-01-04
Hello folks,
 
I have windows 7 and also windows xp on my computer but as i have a lot of free drive space I thought I would have a go with linux and was told to give WUBI a try.
 
I installed WUBI in windows xp and ubuntu 10.10 boots fine but screen resolution is so small I can't see anything and there is no preferences in my system at top left of screen to change it.
 
I'm so disapointed with this experience that I'm ready to give it up as a bad job.
 
Any help appreciated.
 
Musiclover

---

### Post by lukeiamyourfather on 2011-01-04
Sounds like something went wrong during the install. I'd probably try installing Ubuntu again in this case. If it happens twice then its worth investigating further.

---

### Post by anystupidname1 on 2011-01-04
See if you're able to pick a resolution that better suits you here:
System > Preferences > Monitors

If no other resolution options are available, try CTRL-ALT-F1, log in and run "sudo lshw -C video" and  and give us the output.

---

### Post by musiclover01 on 2011-01-04
> **anystupidname1 said:**
> See if you're able to pick a resolution that better suits you here:
System > Preferences > Monitors
 
If no other resolution options are available, try CTRL-ALT-F1, log in and run "sudo lshw -C video" and and give us the output.
 
Thanks for replies. The problem is there is no preferences in system. I will have a go at installing WUBI again to see what happens.
 
musiclover

---

