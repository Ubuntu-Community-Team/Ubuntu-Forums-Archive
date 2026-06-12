---
title: "System Requirements for Ubuntu 10.04.2"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by Paul Roberts on 2011-05-26
When I boot Ubuntu 10.04.2 from the iso on CD on a Toshiba laptop with Vista Home Premium SP2, AMD Athion X2 QL-62 CPU and 2 GB DDR2 @ 333 MHz, the Desktop appears. However, when I try to boot from the same CD on a DELL machine with XP Home SP3, Intel Pentium III EB (Coppermine), and 512 MB SDRAM at 132 MHz, my monitor displays the message "Input not supported".

What are the minimum OS and hardware requirements for the Ubuntu 10.04.2 CD to work?

---

### Post by sanderd17 on 2011-05-26
512 MB RAM is a bit low for Ubuntu, you could try Lubuntu.

But the error message is probably because your disk is a 64-bit version and a pentium iii is only a 32-bit processor.

[s]and is 132 MHz really true? According to wikipedia, Pentium iii clockrates go from 400 MHz to 1.3 GHz[/s]
Sorry, you weren't talking about the clockrate

EDIT: in fact, 512 MB should do well, if you don't run very heavy applications

---

### Post by Paul Roberts on 2011-05-26
Thanks for looking at my posting.  If I read your reply correctly though, you do not see any obstacle in my current OS or hardware that would produce the behaviour I am observing.?.?

---

### Post by sanderd17 on 2011-05-27
Well, did you download a 64-bit iso? in that case, it's normal that Ubuntu won't boot on a pentium iii. And you should download a 32-bit version.

---

### Post by 3rdalbum on 2011-05-27
The "Input not supported" message comes from the monitor itself. It appears that Ubuntu is sending an image to your monitor at a different resolution to what the monitor can deal with.

I don't know how to troubleshoot this problem in the more recent versions of Ubuntu. What sort of monitor is it? If it has a DVI input, try using that instead of VGA. Also, when you initially boot the CD it should bring up a screen that shows a four-armed man and a keyboard at the bottom of the screen - hitting the space bar here will take you to a menu where you can add various boot options that might allow you to boot in low graphics mode.

As far as I can see, your computer should be supported by Ubuntu.

---

### Post by Frogs Hair on 2011-05-27
ttps://help.ubuntu.com/community/Installation/SystemRequirements

---

