---
title: "Install graphics driver on Win 98 in VirtualBox"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by Prince Valiant on 2010-09-13
Hey-

I've installed Windows 98 using VirtualBox within a fresh install of Ubuntu 10.04.  Computer: DELL Inspiron B120.  

Anyway, my problem lies in my difficulty in installing graphics drivers to the Win 98 installation.  Before you redirect me to a windows or VB forum, though, let me explain that 98 doesn't even detect the graphics chip type; I think this is a fault of VB, not Windows.  

Any help?  I'm trying to get decent graphics on here to run Rosetta Stone, and 16 bit colors doesn't cut it.  (It won't work under Wine; for one thing, I have a different version with a different language already installed.)

Thanks a lot!

-Val

---

### Post by bodhi.zazen on 2010-09-13
Virtualbox does not use your hardware directly, so installing the windows graphics drivers will not help.

You install the Virtualbox Guest Additions. Not sure if that will work with Window 98

---

### Post by Prince Valiant on 2010-09-13
Thanks!  I'll try it.

---

### Post by Prince Valiant on 2010-09-13
Not working yet in 98.  Do you know if the Virtualbox Guest Additions work in Win 2000?  Thanks a whole lot.

-Val

---

### Post by migs73 on 2010-09-13
Check this out

[http://ubuntuforums.org/showthread.php?t=653165](http://ubuntuforums.org/showthread.php?t=653165)

Think the VESA bit may be of interest

---

### Post by bodhi.zazen on 2010-09-13
> **Prince Valiant said:**
> Not working yet in 98.  Do you know if the Virtualbox Guest Additions work in Win 2000?  Thanks a whole lot.

-Val

Supported OS are listed here :

[http://www.virtualbox.org/wiki/Guest_OSes](http://www.virtualbox.org/wiki/Guest_OSes)

Win 2000 is listed as supported, inc guest additions.

---

### Post by eriktheblu on 2010-09-13
98 is not supported, but 2000 works very well with guest additions (probably wouldn't use if for intense 3D gaming though)

---

### Post by Jazzy_Jeff on 2010-09-13
I would have went with 2000 before even thinking of 98. I had so many problems with 98 in the past.

---

### Post by Prince Valiant on 2010-09-13
Win 2000 worked! Thanks a bunch!

-Val

---

### Post by Jazzy_Jeff on 2010-09-13
Glad to hear it. Make sure you mark this thread as solved. Go to the top of the thread and click on thread tools.

---

