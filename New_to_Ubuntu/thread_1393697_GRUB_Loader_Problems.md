---
title: "GRUB Loader Problems"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by hawaiian1der on 2010-01-29
When I booted my computer and it tried to go to the GRUB loader, it says:

GRUB loading
error: unknown filesystem
grub rescue>_

At the ">_" what do I need to put in order to fix it with out having to reinstall it?

---

### Post by kansasnoob on 2010-01-29
I'd be lying if I said I understand all of this:

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

I would rather like to have a look at the output of the Boot Info Script as described here though:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by hawaiian1der on 2010-01-30
I went to this site: [http://tolearnfree.blogspot.com/2009/12/how-to-fix-grub2-on-ubuntu-910.html](http://tolearnfree.blogspot.com/2009/12/how-to-fix-grub2-on-ubuntu-910.html)

I tried the first step and it says:

FATAL ERROR: Bad primary partition 3: Partition ends in the final partial cylinder

What does that mean? I can't even put the Windows Vista disk in and  erase the partitions and just start the computer from scratch! What do I do?

---

### Post by kansasnoob on 2010-01-31
> **hawaiian1der said:**
> I went to this site: [http://tolearnfree.blogspot.com/2009/12/how-to-fix-grub2-on-ubuntu-910.html](http://tolearnfree.blogspot.com/2009/12/how-to-fix-grub2-on-ubuntu-910.html)

I tried the first step and it says:

FATAL ERROR: Bad primary partition 3: Partition ends in the final partial cylinder

What does that mean? I can't even put the Windows Vista disk in and  erase the partitions and just start the computer from scratch! What do I do?

When you say you tried the first step I'm not sure what you mean??????

I see #1 being, "# Boot from USB or live cd of ubuntu 9.10, then select Run without change."

Or was it running "sudo cfdisk"?

I really don't care for that guide anyway.

So back to your original post:

> When I booted my computer and it tried to go to the GRUB loader, it says:

GRUB loading
error: unknown filesystem
grub rescue>_

At the ">_" what do I need to put in order to fix it with out having to reinstall it? 

I'm really unsure just when the problem began, had you just installed Ubuntu?

Please provide more info. The results of the Boot Info Script would be very helpful (it can be run using the Live CD):

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by hawaiian1der on 2010-04-06
Well, all this happened again. This time it happened after I tried to delete the partition that Ubuntu was on. I says the same thing it did before and I can't remember what I did to fix it last time.

---

