---
title: "Cannot access the drive in which I installed Ubuntu using Wubi"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by snigam3112 on 2011-05-20
I had drives c(Windows), d(recovery) , f and g. I had loads of multimdeia files in g. That was also the only drive with space. So installed ubuntu 11.04 using Wubi on it. Now i can't access that drive. Without reinstallking ubuntu how can i access that drive?

p.s. just moved from windows to ubuntu - so basically a ubuntu noob

Note: Worked out the problem thx to Rubi1200's advice to access \host

---

### Post by mastablasta on 2011-05-20
what do you mean you can't access that drive? you can't access it in windows? Do you get an error message or something like that? or it simply doesn't show up?

---

### Post by Rubi1200 on 2011-05-20
As mastablasta pointed out, can you please be more specific about what you are doing and how you are trying to access drives/files etc.

If you are in Ubuntu, you can access Windows files like this:
Places > Computer > File System > Host

If you cannot start Ubuntu at all, please explain what is going on and any error messages you might be seeing.

If you are trying to access the Ubuntu install from Windows, that is not possible since Windows does not natively recognize Linux file-systems.

---

### Post by grahammechanical on 2011-05-20
I have never installed Ubuntu using wubi. So, I cannot speak about that. But I do know that in Ubuntu we do not see drives/partitions as C: or D: The partition that I have installed Ubuntu in is listed as File System. In Ubuntu do you see anything that is listed as File System? If so, then that is the drive or area that Ubuntu is stored in.

Regards.

---

### Post by IlhamUwais on 2011-05-28
hi, 

Go to Places->Computer->File System->Host

That's the drive that you installed Ubuntu using Wubi. 

Regards,

---

