---
title: "Ubunto Studio not recognizing HD, can't install"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by Tyler Zambori on 2009-06-28
hi all,

The hard drive is a western digital 500gb, 32mb cache Sata 
drive.  There is no driver for it; it doesn't need one.
It is working just fine under Windows 7. 

I want to install ubuntu studio 8.04 because that is the one
with the non-broken realtime kernel. But it won't recongize
the HD.  I can't even tell it:  Sata-generic because it doesn't
have a sata category.

It's a new computer, with a q6600 cpu, nvidia 8800 gt graphics,
and 4gb ram.  

Help! What can I do?  I've already been to Western Digital's 
web page, and there is no driver!

---

### Post by LewRockwell on 2009-06-28
[http://ubuntuforums.org/showthread.php?t=768859](http://ubuntuforums.org/showthread.php?t=768859)

might give you some ideas

---

### Post by egalvan on 2009-06-28
> **Tyler Zambori said:**
> ,

The hard drive is a wd 500gb, 32mb cache Sata 
drive. 

hardy won't recongize the HD.   


Exactly HOW is Hardy not seeing the drive?

At what point in the boot process or install process?

I've installed Hardy on pure IDE, pure SATA, and mixed IDE-SATA...
never a problem..)

---

### Post by Tyler Zambori on 2009-06-28
LewRockwell:  Oh thank you that really helped.
I could not boot from the CD without installing, 
but what I could do was choose: 

ide-generic

from the driver list. so it was worded differently
from that thread, but I did it and it worked. 
Thank you!

egalvan:  it was happening right after I would
choose the time zone.

Thanks guys!

---

### Post by Tyler Zambori on 2009-06-29
Well I spoke too soon.  The install went through
the whole thing.  It seemed to be succesful, but when it goes 
to actually boot, it hangs on the "ubuntu studio" screen.

I can't see how to boot from the DVD so I can install gparted.
But I was able to successfully partition the drive anyway,
so I don't know if it matters. 

What could be the problem?

---

### Post by Tyler Zambori on 2009-06-30
never mind, I gave up on it.  this is just too
much hassle.  I reformatted the HD and started over
with no form of Linux.

Thanks anyway everybody.

---

