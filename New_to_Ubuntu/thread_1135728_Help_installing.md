---
title: "Help installing"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by natman on 2009-04-24
I have a toshiba laptop with 147 gb of unpartitioned space. I was thinking 12gb for / ext4 primary
2gb for swap
the rest for /home ext4 primary?

Is that ok, i have never used ext4 before and not sure about the primary bit

---

### Post by Hospadar on 2009-04-24
That sounds fine to me, you might even consider shrinking your root partition a little more.  I generally install with only a 5GB root partition (on my dual boot lappy), but if you've got the space, growing it to ~10GB is perfectly resonable I would think.

Same thing with swap, if you've got plenty of ram, you'll probably never use all of it, but if you've got the space to spare, you might as well make it comfortably large.

As for ext4 in general, I think you'll be just fine using it, but keep in mind that most server administrator types probably wouldn't consider it "production ready" although I suspect for a home machine you'll have absolutely no problems with it.  Just keep an eye out for bugs so you can report them in the unlikely instance that they might occur.

---

### Post by MyR on 2009-04-24
Anyone you ask might have different preferences for partioning but ext4 shouldn't have any different size requirements than ext3.

peace

---

### Post by bodhi.zazen on 2009-04-24
For "primary" see : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

In terms of root size, I agree 5-10 Gb is all you "need"

In general , swap = RAM X 2 , max 1 Gb (som say mak 512 kb).

The only exception is with laptops. If you wish to use sleep or hibernation you need swap = RAM plus a wee bit more (128-256 Kb).

HTH

---

