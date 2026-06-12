---
title: "Triple boot question"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by seekyrr on 2009-01-12
I have a dual boot of XP and backtrack using LILO.

If I add Ubuntu, will it be added to the lilo options or would the grub loader mess things up?

Thanks

seek

---

### Post by Kellemora on 2009-01-12
HI Seek

I have three machines here that are triple boot, but I'm using Grub on all of them.  Because I have NONE of them set up so that they automatically make changes to my bootloader.  

However, I think you can still use LILO, you don't have to use Grub if you don't want to.  You may have to manually add Ubuntu to your bootloader, you can let it write Grub so you can cut and paste from it to LILO, just don't let it write to the MBR when it asks to.

When a new kernel is installed, it always gives several options, and my default setting is DO NOT update menu.lst!
So, after the install, I have to go and copy the info from That Grub over to the working GRUB I keep on the first HD partition.

I don't see why you couldn't do the same thing, regardless of which bootloader you are using.

TTUL
Gary

---

