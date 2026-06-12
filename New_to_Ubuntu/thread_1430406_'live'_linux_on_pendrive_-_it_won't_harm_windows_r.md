---
title: "'live' linux on pendrive - it won't harm windows right?"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by annoluce on 2010-03-15
am i correct in thinking if i run linux 'live' from a pendrive, this will not effect my windows OS /data on my hardrive in any way whatsoever? it is 'temporary'? Also am i correct in thinking that linux will function independantly from windows, use it's own drivers etc.
Thank you!

---

### Post by leorolla on 2010-03-15
Unless there is already some problem with your hard disk, just booting from an Ubuntu Live USB doesn't cause any change to your system.

---

### Post by J V on 2010-03-15
If you want to change your original system you will have to

Install on that system
OR
Mount that hard drive then mess with files

So in short, no.

---

### Post by coffeecat on 2010-03-15
Simply running Ubuntu from a pendrive doesn't affect your hard drive in any way...

UNLESS..

...you mount any of your hard drive partitions from the Places menu. This is easily done and, since Ubuntu can write to a NTFS filesystem, it is possible to write to your Windows C: partition. If you write in the wrong place you could, in theory, do some damage.

This is no reason not to use Ubuntu from a pendrive because of this. Just be aware that **if** you mount internal NTFS partitions you have full read-write capability. Just mounting the partition does not do any damage. Doing something unwise after mounting might.

---

### Post by Directive 4 on 2010-03-22
yes, it would be a good idea not to downlaod any codecs., new programs etc onto the ubuntu system (usb) drive while the windows hdd is mounted. 

i did, it wasn't pretty.

---

### Post by gadolinio on 2010-03-22
> **coffeecat said:**
> Simply running Ubuntu from a pendrive doesn't affect your hard drive in any way...

UNLESS..

...you mount any of your hard drive partitions from the Places menu. This is easily done and, since Ubuntu can write to a NTFS filesystem, it is possible to write to your Windows C: partition. If you write in the wrong place you could, in theory, do some damage.

This is no reason not to use Ubuntu from a pendrive because of this. Just be aware that **if** you mount internal NTFS partitions you have full read-write capability. Just mounting the partition does not do any damage. Doing something unwise after mounting might.

**[SIZE=1]*Primum Non Nocere* — Above all, do no harm. [/SIZE]**


Exactly. Nothing will be modified in your windows nor files, unless you manually do it.
And the liveusb has its own selection of drivers.
Once you restart the computer without the usb stick, it will all work as if you had never used it at all.

---

