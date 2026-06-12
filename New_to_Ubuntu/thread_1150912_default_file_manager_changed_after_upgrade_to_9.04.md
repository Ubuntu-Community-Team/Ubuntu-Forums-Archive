---
title: "default file manager changed after upgrade to 9.04"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by steeny124 on 2009-05-06
So, aside from all the sound problems I've been having since my upgrade to 9.04, my default file manager somehow got changed to Dolphin. 

I played around with Kubuntu a while back so I still had it on. 

I tried removing Dolphin, but that didn't work.

I can access Nautilus by going to Applications > System Tools > File Manager , but when I try to access it through Places > Home Folder it gives me this error message: 

Could not open location 'file:///home/steeny124'
No application is registered as handling this file

I just need a way to get the Places/Home Folder to point to Nautilus.  

I've tried restoring default settings, which did not work. 

I've also looked around for many other tutorials, but to no avail. 

By the way, any word on all the sound problems? I hear a lot of people have been having trouble.  I, myself, don't even have log in sounds.  It's rather frustrating.

---

### Post by Niniel on 2009-05-06
That's easy - just right-click on any folder and go to the Open With tab.
There either pick Nautilus as the default application, or if it isn't in there, enter it as a custom command and it will show up. You may have to specify it as the default application again though, for me, the first time it just opened the folder and added an entry in the list of available applications.

---

### Post by steeny124 on 2009-05-06
> **Niniel said:**
> That's easy - just right-click on any folder and go to the Open With tab.
There either pick Nautilus as the default application, or if it isn't in there, enter it as a custom command and it will show up. You may have to specify it as the default application again though, for me, the first time it just opened the folder and added an entry in the list of available applications.

Well, it appears that folders will open in Nautilus, but if I try to go to my Home Folder via Places > Home Folder, it brings up the error message I posted earlier.

---

### Post by Niniel on 2009-05-06
That's what fixed it for me.
[I had the same issue, except with PCMan from LXDE]("http://ubuntuforums.org/showthread.php?t=1126678").

---

### Post by steeny124 on 2009-05-06
Thanks so much!

Had to do a little more finagling with it than what I did before. 

Now that THAT'S out of the way, I can start tackling the sound problem again.

---

