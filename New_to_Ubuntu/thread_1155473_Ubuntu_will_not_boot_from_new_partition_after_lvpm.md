---
title: "Ubuntu will not boot from new partition after lvpm"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by terrybennett on 2009-05-10
I ran Ubuntu for two weeks with Wubi and then decided to run with Windows Vista,

I set up the partitions successfully and then ran LVPM.  Everything seemed to run fine.

I get the Grub loader with lots of choices.  Window. Windows Loader ubuntu. etc.

Windows Vista boots fine.  The only way to boot Ubuntu is through Wubi still.  it will not boot from the new partition.  I get the error.

Error 17  Cannot mount selected partition.  Any key to continue.

i am then back to Grub.   When i get into ubuntu through wubi i can see the new partions and all the file there.  I think it is something small that needs changing but do not know how to fix.

Thanks for any help.

---

### Post by terrybennett on 2009-05-11
Okay after further research I think I solved my own problem.

I used the UUID to point toward the correct partition.  At least I think I have it pointing to the right place now.  I will find out when I uninstall WUBI in Vista.

---

