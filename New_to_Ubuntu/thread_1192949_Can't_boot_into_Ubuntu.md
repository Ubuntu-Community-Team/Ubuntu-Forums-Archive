---
title: "Can't boot into Ubuntu"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by sideffects on 2009-06-20
I'm dual-booting Ubuntu and Windows Vista. Recently, I was notified that my Ubuntu disk may be full. Now, I can't boot into Ubuntu at all, and I can't seem to find the files in Windows Explorer. (I am showing all hidden files/folders.) Does anyone know how to fix this?

---

### Post by powel212 on 2009-06-20
Windows can't read the Linux file format.

But, you can boot from a live CD and then find your Ubuntu disk and installed files and delete some files to make some space.

Hope that works for you.

Please let us know if after making room you are again able to boot into ubuntu.

Powel

---

### Post by sideffects on 2009-06-21
Good thinkin'! Thanks, will give it a shot.

---

### Post by raymondh on 2009-06-21
Hope this helps you as well when you get to boot into ubuntu.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

Good luck.

---

### Post by sideffects on 2009-06-21
Okay then, followup question: Can I resize my Ubuntu partition without reinstalling Ubuntu? (Don't worry, I'm not getting my hopes up.)

---

### Post by raymondh on 2009-06-21
> **sideffects said:**
> Okay then, followup question: Can I resize my Ubuntu partition without reinstalling Ubuntu? (Don't worry, I'm not getting my hopes up.)

Yes.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Note, you need to use the liveCD or a CD of gparted and not from your Ubuntu install.  Gparted will not work on a partition if it is mounted.  When using the liveCD and you get a greyed-out re-size option, right click the swap partition and swapoff ... as it is being used.

If able, save your files someplace else first.

Good luck.

---

### Post by sideffects on 2009-06-21
Awesome! Thanks a ton!

---

### Post by LewRockwell on 2009-06-21
if you like that then you've got to have this:

[http://www.partedmagic.com/](http://www.partedmagic.com/)

---

### Post by raymondh on 2009-06-21
> **sideffects said:**
> Awesome! Thanks a ton!

And you are most welcome :)

Happy Ubuntu-ing.

---

