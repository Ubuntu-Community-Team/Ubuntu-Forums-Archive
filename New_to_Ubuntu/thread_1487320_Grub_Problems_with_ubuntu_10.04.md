---
title: "Grub Problems with ubuntu 10.04"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by Jeff.Smith on 2010-05-18
So, I'm trying to install Ubuntu 10.04 within windows 7 using wubi. I successfully make it through the entire installation process but then when my computer reboots and I try to boot into ubuntu it brings me to the command prompt and at the top of the screen says Grub 1.97 beta 4. I was under the impression that Ubuntu 10 was supposed to be using grub 2. I think this may be the root of my problems, I cannot get away from the command prompt and I don't know where to go from here. Can someone inform me on how to update my grub or perhaps shed some light on where I should try from here? I've already tried uninstalling and reinstalling(several times) with the same error. I've even deleted the file and re-downloaded it. 

I am currently trying to intall it on an ASUS UL30A-X5 and I am trying to install the 64bit version of ubuntu.

Please help.

---

### Post by -humanaut- on 2010-05-18
Grub 1.97 is Grub 2. Grub2 isn't complete yet and still in beta hence the .97 vs 2.0 naming convention.

---

### Post by pizza-is-good on 2010-05-18
To back up what -humanaut- said. Yes, 1.97beta4 is grub 2.

As a side note, grub 1 was way better than grub 2. There is a whole thread on this forum about [grub 2 complaints]("http://ubuntuforums.org/showthread.php?t=1299270"). Fell free to join us when you get tired of it.:lolflag:
~pizza

---

### Post by bcbc on 2010-05-18
I thought the version of grub with 10.04 was 1.98 (not 1.97 beta4).  Make sure you have downloaded a 10.04 image - there was a bug with the wubildr in  9.10 that had a similar symptom (end at grub rescue). It's fixable but if you want 10.04 then might as well get that.

---

### Post by QIII on 2010-05-18
There is a human tendency to perceive that with is new or different as somehow wrong or defective.

GRUB2 is certainly different.

It is also substantially more configurable than GRUB was.  The metaphor (I use that term in the Computer Science context) has evolved.

---

### Post by bapoumba on 2010-05-19
Changed prefix to [wubi].

---

