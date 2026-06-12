---
title: "ipw3945 with a kernel recompilation"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by airmind on 2007-01-28
I use Edgy and just recompiled my kernel to version 2.6.19 with beyond2 patches, but now my wireless card stopped working. I have a Intel 3945ABG card (part of Centrino). I check my modules and ipw3945 is gone.
Apparently, the kernel I compiled dont even comes with ipw3945. I'm trying to compile it by hand and I'm having a lot of troubles with ieee80211 module.
I think the easiest way would be to include it in my current kernel source and recompile it (it would be the third time! It's been quite fun actually), but I don't know how to do it, other then try to copy the files from the generic Edgy kernel. 
Any ideas to get it working again?

By the way, why copying compiled modules from an earlier kernel doesnt work? I tried to do some hacks but none worked, until I gave up, but shouldnt a module from 2.6.17 work with kernel 2.6.19? Just asking because I'm quite a newbie to Linux.

---

### Post by mlissner on 2007-01-28
Hey, I just posted a nearly identical thread about this. I just upgrade to 2.6.19, and it's working great (especially with suspend), but my 3945abg doesn't work, and ipw3945 seems to be gone.

I'm on my fourth kernel compilation on this end.

---

### Post by airmind on 2007-01-28
I was checking the driver, and it needs a binary-only daemon with a firmware, which proably means the driver is not included in the vanilla kernel (from kernel.org). It is probably included only with Ubuntu's kernel. 
But how can I include it with my kernel source and enable it through xconfig? Could I just extract it there?

Edit: I found [http://ipw3945.sourceforge.net/INSTALL]("http://ipw3945.sourceforge.net/INSTALL") which has extensive instructions to install ipw3945. It might help, but it seems too much trouble. I would like to build it with my kernel, just like the edgy kernel does.

---

