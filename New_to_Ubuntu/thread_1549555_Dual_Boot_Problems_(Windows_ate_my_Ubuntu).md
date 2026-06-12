---
title: "Dual Boot Problems (Windows ate my Ubuntu)"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by dirtynorth on 2010-08-09
I have been running 10.04 64bit on my desktop for a couple months, and loving it.  I recently got a digital camera that had essential software on a windows only CD.  SO I tried installing Windows on a separate partition.

The partitioning went fine

then...

during the Windows install it mentioned something about making my ubuntu partition inactive.  

Now When I turn my computer on I cant figure out how to boot Ubuntu, out skips right through to Windows

Thanks

PS Im new to this so you may have to hold my hand through the explanations

---

### Post by Jmih on 2010-08-09
hey dude have u installed the windows on a seperate  hdd? u can install easy bcd in windows and double boot windows and ubuntu

---

### Post by wilee-nilee on 2010-08-09
You can reload grub2 to handle both OS, here is a link that defaults to doing this from a live karmic or later cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If this is confusing or doesn't get it working post the bootscript in my signature in code tags as described.

---

### Post by azertyh on 2010-08-09
hi,
read [this documentation]("https://help.ubuntu.com/community/Grub2"), especially "the method 2 copy grub2 from the installed partition".

---

### Post by dirtynorth on 2010-08-09
Excellent!!

That worked perfectly.  Thanks for the quick slove

---

