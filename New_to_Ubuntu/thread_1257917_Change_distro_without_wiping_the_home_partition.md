---
title: "Change distro without wiping the home partition"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by OllieGab on 2009-09-04
My very first Linux OS (Ubuntu 8.10) I installed simply by putting everything on one partition.
My second installation (on another machine: 9.04) I set up with 3 different partitions; root, home and swap.
From what I can understand this will make it possible to try out another distro without affecting/removing the home folder...so how do I do it?:?

Cheers Ollie

---

### Post by LowSky on 2009-09-04
when you install the other Linux OS, just tell the computer that you will use the home partion as the home partition in the new OS, simple as that. Is it a good idea, not really, as different versions of Linux might have different versions of software that dont do well with others.

but SWAP can be used by whatever, it wont matter at all.

---

### Post by philinux on 2009-09-04
Yep as lowsky says. When the partitioner starts up choose manual and mark the partitions as / /home swap but when you do the /home partition just **dont tick the box marked format**.

---

### Post by OllieGab on 2009-09-04
So if this isn't the ideal way to try another distro, what is the best way?
I can of course try out as many distros as I like on another machine (which is what I do) but to really give it go I think you need to test it with your own documents etc.

---

### Post by philinux on 2009-09-04
> **OllieGab said:**
> So if this isn't the ideal way to try another distro, what is the best way?
I can of course try out as many distros as I like on another machine (which is what I do) but to really give it go I think you need to test it with your own documents etc.

I'd just copy your home folder to the "other" machine and play away. This way you dont risk anything.

---

### Post by LewRockwell on 2009-09-04
Mega Multi Booting Tutorial!

[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

.

---

### Post by eriktheblu on 2009-09-04
> **OllieGab said:**
> So if this isn't the ideal way to try another distro, what is the best way?

If you just want to try it out, I'd recommend Virtualbox or a live CD.

---

