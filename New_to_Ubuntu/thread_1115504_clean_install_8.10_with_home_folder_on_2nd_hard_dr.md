---
title: "clean install 8.10 with home folder on 2nd hard drive"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by DarinB on 2009-04-03
i just got a new computer 3 hard drives.
i have vista on half of the primary drive. i already shrunk the primary in vista
now i have 1/2 a primary drive and two other drives,
i want to clean install 8.10 with the home folder on the 2nd drive. 
now i am not sure what to do????
should i use gparted and format the other 2 drives. they are unformated???
also don't know how to get through the install ie guided manual etc. set up the separate home and root????

---

### Post by taurus on 2009-04-03
So you want to install Ubuntu on a second partition of the first harddrive (vista is on the first partition of that drive) and you want to use the second harddrive for /home?  

You need to use the Manual option and mount the second partition, probably /dev/sda2, to / and the second harddrive, probably /dev/sdb1, to /home.  Format both to ext3 filesystem.

What do you plan to do with the third harddrive?

---

### Post by DarinB on 2009-04-03
hi Taurus 
i finally got that computer, so i couldn't figure out how to install with a separate home folder, so how do i do it after the fact. i did successfully get the dual boot. should i wipe it out and try again or move it now?

---

