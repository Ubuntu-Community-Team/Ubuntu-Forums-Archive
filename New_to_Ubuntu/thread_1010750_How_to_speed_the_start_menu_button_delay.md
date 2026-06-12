---
title: "How to speed the start menu button delay?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by jay li on 2008-12-14
It's happening only the first time I'm login the system, and it takes about 10 second to show up.

---

### Post by jay li on 2008-12-14
:confused:

---

### Post by ibizatunes on 2008-12-14
what is the spec of your machine?
To run ubuntu well you need 512mb or RAM or more

---

### Post by jay li on 2008-12-14
Eee PC 701
CPU: Intel Celeron M 900 Hz
Memory: 512 MB
Ubuntu 8.10
SD Card
No swap partition

---

### Post by ibizatunes on 2008-12-14
You will need a swap file that is what is make your machine run slow, 512mb is the recommend, but you need about 1gb of swap file

---

### Post by ibizatunes on 2008-12-14
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by jay li on 2008-12-14
I tried ubuntu with swap partition and I didn't see any changes, and remember I use sd card too.

---

### Post by Doug77 on 2009-03-30
Do you mean that when you boot up, and click on the Ubuntu icon (wherever you have it) to show the menu, it takes a long time to show up?  This is a solution here:  

[http://ubuntuforums.org/showthread.php?t=771955](http://ubuntuforums.org/showthread.php?t=771955)

It's not ideal, since you have to have an extra icon somewhere and I'm really stingy with my screen real estate, but thanks to the OP, because it does work.

---

### Post by earthpigg on 2009-03-30
the menus have a set delay of a few ms.

i have seen a how-to that involves editing something in gconf-editor... changing the number from 500 to zero or something of that nature.

looking around now to see if i can find.

---

