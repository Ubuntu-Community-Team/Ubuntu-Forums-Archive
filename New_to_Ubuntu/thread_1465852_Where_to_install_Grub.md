---
title: "Where to install Grub"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Opie01 on 2010-04-29
I want to try out Ubuntu on a computer running Windows Vista.  I partitioned my hard drive to make space for Linux but I don't want to let Grub take over my boot.  I downloaded EasyBCD to edit the windows boot sequence.  So where should I tell Ubuntu to intall Grub.  Is it safe to let it install on hd0 or should I install it on the same partition as Linux hd0,1 ?  If I install Grub on the same partition as Linux will I be able to access it?

---

### Post by SkyNet2029 on 2010-04-29
Since you are using the EasyBCD, it is safe (expected) to NOT install it to yoru MBR.
That being said, for what you are expecting to accomplish..
Not have grub be your boot loader, edit vista loader,
then you should install grub into the linux partition and not the MBR (hd0).


Hope that helps.

Cheers!

--> EDIT: FORGOT THIS.... <----

The EasyBCD will allow for you to edit the vista loader allwoing for you to point it at the grub installation for a chainloaded type of boot process.

---

### Post by Opie01 on 2010-05-01
Thanks for the advice.  I struggled with Debian linux for a long time to try and do this.  Then I found Ubuntu which was actually quite easy to install.  The instructions are quite well written and and the user forum is very friendly.

---

