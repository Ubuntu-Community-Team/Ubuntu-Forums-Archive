---
title: "how to recover deleted files"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by godsmAsh on 2009-11-18
hi,
 is there anyway to recover a deleted file.  i had accidentally deleted a word document.

---

### Post by ukripper on 2009-11-18
> **godsmAsh said:**
> hi,
 is there anyway to recover a deleted file.  i had accidentally deleted a word document.

If you are using 9.10 check in your "deleted items" (if using 9.04 or lower then "Trash") first. Go to Places-->Home--> and on the left hand side you can see deleted items.

---

### Post by godsmAsh on 2009-11-18
i'm using ubuntu 9.10 and if deleteditems refers to trash.. i've emptied the trash. is there a way to recover it.

---

### Post by ukripper on 2009-11-18
> **godsmAsh said:**
> i'm using ubuntu 9.10 and if deleteditems refers to trash.. i've emptied the trash. is there a way to recover it.

I am afraid in that case there is no easy way.

you can try this [http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

---

### Post by r.mariappan on 2009-11-18
You can use partimage to recover files..
It will be in repositry only,
So install using apt-get

---

### Post by godsmAsh on 2009-11-18
thanks....

---

### Post by decoherence on 2009-11-18
Unusually, the Ubuntugeek article is TERRIBLE for one specific reason. It doesn't advise you to immediately stop using the system, yank the power cable out the back and boot from a LiveCD.

All data recovery should happen from a LiveCD or booted from a partition that DOES NOT contain the data you want to retrieve.

When you delete a file, it doesn't get erased but it does get marked as "overwritable." The more you use that disk, the more likely it is the data you want will be overwritten. That is why it is important to stop using it. Ideally, rip the power out of the wall (too late now, but for future reference) and don't even bother shutting down.

Boot from a LiveCD... from there you should be able to follow the UbuntuGeek instructions. Shame, though, that they don't say at the top in big, bold, red, blinking letters "STOP USING THE DRIVE THAT CONTAINS THE DELETED DATA!!!!!!11one"

---

### Post by ukripper on 2009-11-18
> **decoherence said:**
> Unusually, the Ubuntugeek article is TERRIBLE for one specific reason. It doesn't advise you to immediately stop using the system, yank the power cable out the back and boot from a LiveCD.

All data recovery should happen from a LiveCD or booted from a partition that DOES NOT contain the data you want to retrieve.

When you delete a file, it doesn't get erased but it does get marked as "overwritable." The more you use that disk, the more likely it is the data you want will be overwritten. That is why it is important to stop using it. Ideally, rip the power out of the wall (too late now, but for future reference) and don't even bother shutting down.

Boot from a LiveCD... from there you should be able to follow the UbuntuGeek instructions. Shame, though, that they don't say at the top in big, bold, red, blinking letters "STOP USING THE DRIVE THAT CONTAINS THE DELETED DATA!!!!!!11one"

very good point! Didn't notice it at first.

---

### Post by indytim on 2009-11-18
> 
You can use partimage to recover files..


Only **IF** you did a partition image **BEFORE** going into delete mode...

IndyTim

---

