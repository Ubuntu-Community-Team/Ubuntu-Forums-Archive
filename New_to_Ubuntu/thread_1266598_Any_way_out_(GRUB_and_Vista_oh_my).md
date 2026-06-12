---
title: "Any way out (GRUB and Vista oh my)"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by Arla on 2009-09-14
So, wanting to play with Ubuntu before I really went ahead (and wanting to wait for my Windows 7 CD to arrive) I installed Ubuntu on my USB hard Drive so I could boot to that to use Ubuntu, and just boot my laptop to get to Vista.

Seems logical right? Well unfortunately I forgot to check the advanced options, so now have GRUB installed on the Vista MBR, but it's expecting the USB hard Drive to be there (I get some rescue mode for GRUB if the USB Hard Drive isn't connected) this, in a word, sucks.

I've tried SuperGrub but it doesn't seem to let me get the Vista MBR back (it says something about suslinux as the prior OS?) I'm thinking two options, one is actually re-install with Ubuntu on the machine, alternatively remove GRUB (if that's in any way possible without a Vista CD?) or fully install GRUB into the Vista drive and have GRUB run before Vista (is that even possible?)

Any advice for a newbie?

---

### Post by earthpigg on 2009-09-14
hi,

see if this is of use to you:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

i'm not aware of an equivelant for win7 - but you will need to use Windows tools to restore the Windows bootloader.

---

### Post by Redundant Username on 2009-09-14
After burning the recovery disc, boot it and go to the recovery console.
Enter: 
```
bootrec/fixmbr
```

And then,
```
bootrec/fixboot 
```

The Windows mbr should now work.

---

