---
title: "/boot is full !!!!"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by jfreak_ on 2010-07-30
I got this error message now.What to do? My /boot is 75mb. 
 Recently I always get a error message near the end of installation of a package, something related to the non-creation of linux-generic image but package is installed.

---

### Post by davidmohammed on 2010-07-30
75Mb is tiny for /boot.

I would recommend you install "Ubuntu Tweak" - use is to clean up the oldest kernel.

---

### Post by jfreak_ on 2010-07-30
> **davidmohammed said:**
> 75Mb is tiny for /boot.

I would recommend you install "Ubuntu Tweak" - use is to clean up the oldest kernel.
   yeah but I have used 75mb as /boot since 8.04, this is the first time I am seeing this . 
Will try ubuntu-tweak.

---

### Post by mbsullivan on 2010-07-30
What kind of filesystem is on it? If you want to avoid running out of space again, you could always expand your /boot partition. Most filesystems are growable, and many new ones are shrinkable.

You should be able to fix this by just deleting old kernels, though... After all, you really only ever use one, and perhaps an older one in case something gets borked.

I used to run with a 100MB boot, and it was fine UNTIL I started rolling my own kernels... The kernel images in the Ubuntu repositories are very small.

Mike

---

### Post by jtarin on 2010-07-30
I would suggest using Syaptic and removing any older kernels you are not using.

---

