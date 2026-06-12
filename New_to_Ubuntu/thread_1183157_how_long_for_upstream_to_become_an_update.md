---
title: "how long for upstream to become an update?"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by PGScooter on 2009-06-09
Hi,

I am affected by a bug, which is documented here: [http://www.anythingbutipod.com/forum/showthread.php?t=42442](http://www.anythingbutipod.com/forum/showthread.php?t=42442)

It was apparently fixed in an upstream about a month ago. I do not really understand what an upstream is, and am wondering if it will make its way into a normal ubuntu upgrade anytime soon.

Can someone please explain the process of going from an upstream to an update? Is there a chance that I would have to wait until 9.10 to get it automatically fixed?

Thanks

---

### Post by 123456789123456789123456 on 2009-06-09
I was reading the thread, and got tired and extreamly confused, what are they talking about, what bug are you refering to.  updtream usually refers to a program update, as far as I understand it.  It is usually something like having a program update itself.  This may or may not be included in the ubuntu updates.  I would try and have apt-get install update ran in terminal, then go to update manager and search/check for updates, see then.  If not, and they are refering to a certian program, completely remove the program in question, and reinstall it.

---

### Post by PGScooter on 2009-06-09
glad to know I wasn't the only one confused. Thanks for taking a look though.

The bug is that a certain type of mp3 player that used to connect in 8.04 with no problem at all now does not connect correctly by usb.

---

### Post by chrisod on 2009-06-09
Compare the version number of the program that contains the fix with the version number available in the repositories. If the repository number is lower you aren't getting the fix from the Ubuntu update. You'll have to either wait, or download the update directly from the source, which may require compiling from source if they don't offer a .deb package.

---

