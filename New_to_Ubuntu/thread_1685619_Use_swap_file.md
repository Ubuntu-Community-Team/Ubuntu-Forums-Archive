---
title: "Use swap file"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by Perpetual_noob on 2011-02-11
Hi
 
 I installed Ubuntu 10.10 and I also installed a 2.1 GB swap partition.  However when I type "free" it says that I have no swap. How do I get  Ubuntu to use the swap partition?

---

### Post by lindsay7 on 2011-02-11
You can not use it.  It is there to be used like temp memory if needed.  I most cases it is never used as I understand it.

---

### Post by samacaster on 2011-02-11
You can control, if you really feel the need to, the amount of swap memory that is used. But as lindsay7 stated, it is there if needed. Think of it like windows Virtual Memory. But instead of allocating free space on the main drive for extra memory, linux uses a dedicated partition for that purpose.

---

### Post by Perpetual_noob on 2011-02-11
Thanks for the reply lindsay7.

This is what I get:

total       used       free     shared    buffers     cached
Mem:       2049812    1952540      97272          0     230360    1285352
-/+ buffers/cache:     436828    1612984
Swap:            0          0          0

Is that right? Is it normal to say 0 free if I made a 2.1 GB swap partition?

---

### Post by kerry_s on 2011-02-11
nope, that means you didn't set it to be used.

you can manually add it to /etc/fstab
or
you can try something different, what i do is use dynamic swap.
what it does is create a swap file only when needed.

all you have to do is install "swapspace".

---

### Post by plucky on 2011-02-11
If you want to use your swap partition,please post output of ```
cat /etc/fstab
sudo blkid
```

It appears your swap partition is not being mounted at startup

---

