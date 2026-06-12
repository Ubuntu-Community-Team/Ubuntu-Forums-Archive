---
title: "running fsck"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by TCMGO on 2011-04-16
Linux froze up on me and after trying the standard keyboard fixes, I was forced to power down using the button on the front.  Upon reboot, I get a kernel panic error.  The forum suggested that I run fsck on the partiton that Unbuntu is installed on.  I happened to run a memory test first, and after cleaning and reseating my RAM sticks, it passed the test, wherein I am now able to boot into Ubuntu,  This leaves me with three questions:
 
Is it possible that the RAM fix also resolved the kernel panic error?
 
Can I run fsck from within Linux by selecting the unmount option first (or will unmounting cause it to crash, seeing how it is booted up in Linux)?  Or should I do it from the LIVE CD?
 
I noticed in the rescue CD an option to find and repair partition problems, but when I select it I get an "operation is pending" message, but no sign that the operation is running.  Does this message mean that it is running or am I missing something?

---

### Post by K_45 on 2011-04-16
From the live CD. I'd still do it to make sure the HDD is clean. I'd also run Hitachi's Drive Fitness test to make sure your HDD is healthy.

---

### Post by lmarmisa on 2011-04-16
Please, boot into a Ubuntu Live CD, visit the page [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)  run the Boot Info Script and post here its result (follow the instructions of this page).

According with that information, you will receive further help.

---

