---
title: "Increase cache Size?"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by thaumielx72 on 2010-10-03
I am running a Distributed Computing project pretty much letting it race along on it's own.  

It is reading from the disk almost non-stop.  My panel applet tells me 18% of my 12GB of RAM is in use by programs and another 4% is in use as cache.

Is there any way to force it to use more memory for the cache or is there a way to move my BOINC folder and perhaps some libraries to a RAM disk drive?

Appreciate any suggestions...

---

### Post by thaumielx72 on 2010-10-03
Wow!  I appear to have thrown the Ubuntu community a decent curve ball!

LOL Just kidding guys....:guitar:

---

### Post by psusi on 2010-10-03
No, the cache is automatic.  It uses all free memory.  What does free -m say when this is going on?

---

### Post by thaumielx72 on 2010-10-04
It says:

             total       used       free     shared    buffers     cached
Mem:          7995       2283       5712          0         95        397
-/+ buffers/cache:       1790       6204
Swap:        35257          0      35257

---

### Post by NightwishFan on 2010-10-04
If the program reads data from a folder owned by a normal user (you, under /home/yourusername). Close the program then you can move the directory it reads to a ram disk (in /dev/shm/), and link from /dev/shm (with the exact same name!) back to your home folder. Note if you do this, it will be deleted on shutdown, so ensure you close the program and copy the data back out of /dev/shm before you shut down!

This should not require root access, so if have to do anything as root, do not use this suggestion.

**Do not just do this, do some homework first so nothing messes up!**

---

### Post by psusi on 2010-10-04
You only appear to have 8gb of ram, not 12, but yea, not a whole lot of it is being used for cache.  The application must be bypassing the cache.

---

