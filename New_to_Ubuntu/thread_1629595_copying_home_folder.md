---
title: "copying home folder"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by crew51m on 2010-11-23
My home folder is 30 gigs, I want to do a fresh load of 10.10, can I copy all the folders onto dvd;s or an ext hd then copy back into the new home folder and have everything work ? I know in windows if you do this it wont work, windosws will crash due to the fact that windows scatters files throughout the system and if you move a folder it will crash

---

### Post by bug67 on 2010-11-23
This is exactly what I do prior to a full re-install.  Not saying everything will be an exact clone of your previous system but, all the files will be there.  As an example, I replace the .mozilla file that is in the new install with the .mozilla file that is from my home folder back up and everything, all add-ons, bookmarks, settings, window sizes...EVERYthing was just like I left it.

---

### Post by blazemore on 2010-11-24
Indeed, you can do this.
When reinstalling, why not set up a separate /home partition so you won't ever have to do this again?

---

### Post by crew51m on 2010-11-24
Not to sound like a smart a$$, setting up a home partition will allow me to copy stuff into it so I can do a fresh install on the new partition and copy the home folder into the new os?

---

### Post by onaridge on 2010-11-24
From what I understand when you reinstall or upgrade the home partition is untouched. The install goes into the root so you don't have to copy anything as nothing changes in the home folder as long as you install into a separate root partition. An upgrade knows where to go and all your stuff in home stays there unchanged. When I upgraded from 10.04 to 10.10, all my stuff was still there. I have a separate home partition.

---

### Post by crew51m on 2010-11-24
Thanks.

---

### Post by C.S.Cameron on 2010-11-25
Copying home folder is not quite so simple. If the folder is mounted you can not get an exact copy.
Permissions etc are not automatically copied.
Check this:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

