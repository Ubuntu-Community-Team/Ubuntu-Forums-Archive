---
title: "accidentally  installed ubuntu twice"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by bobbyxmacefight on 2009-01-30
I had some problems following my original install of ubuntu where computer would not boot (no idea how this happened, also this is a brand new machine), so I reinstalled ubuntu, and found that i had lost windows vista, with the exception of the recovery utility.  I ran the recovery utility, and reinstalled vista.  After that, I was no longer able to use ubuntu (vista booted automatically without giving me any choice).  So I reinstalled ubuntu, only to find out, upon using it for the first time after installing, that I still had the previous ubuntu installation on my computer.

so anyway, I really only need one and would like to figure out how to delete this very small partition that contains the additional ubuntu installation.

thanks so much!

---

### Post by halovivek on 2009-01-30
how did you installed the Ubuntu. from the windows using WUBI or from the boot up?

---

### Post by bobbyxmacefight on 2009-01-30
from the boot up

---

### Post by halovivek on 2009-01-30
Have you selected the same partition or different one, while installing?

---

### Post by HittingSmoke on 2009-01-30
If my understanding of your problem is correct, you can just use a Gparted Live CD to delete the extra install partition then reallocate the newly freed space to the install you want to keep.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

