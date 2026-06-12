---
title: "quick question"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by flintman on 2009-12-05
I haven't noticed this before on update,  maybe i just didn't notice but under the new kernel 2.6.31.16 it says (new install)

What does that mean?  I new piece of software is getting installed not updated?

Pre thanks

---

### Post by MelDJ on 2009-12-05
updated kernel i suppose

---

### Post by balaknair on 2009-12-05
> **flintman said:**
> I haven't noticed this before on update,  maybe i just didn't notice but under the new kernel 2.6.31.16 it says (new install)

What does that mean?  I new piece of software is getting installed not updated?

Pre thanks

The older kernel versions(*-15 and *-14) are not overwritten by the new one(*-16), and are still available in the GRUB menu when you boot up. So rather than just an update to *.15, *.16 is installed alongside the older versions.
This is presumably done so that in case there is a regression or bug in the new kernel version(like incompatibility with some hardware or application you use), you can still boot using the older  version(s). Also for critical packages like the kernel this is actually a good idea just in case something goes wrong during the install. You can revert to the older version and try to fix the update without having to resort to a recovery console or rescue disc.

You can manually remove the older kernel versions in case you want to free up some space on your hard drive, but IMO in most cases it's better to just leave them be.

---

### Post by lotharmat on 2009-12-05
> **balaknair said:**
> ....

You can manually remove the older kernel versions in case you want to free up some space on your hard drive, but IMO in most cases it's better to just leave them be.


Until you get so many of them that they are just sitting there using HD space.

I tend just to keep the last two or three - That way you can be guarantee nothing is seriously borked!

---

