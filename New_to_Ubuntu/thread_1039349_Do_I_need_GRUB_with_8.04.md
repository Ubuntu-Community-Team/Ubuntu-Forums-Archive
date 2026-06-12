---
title: "Do I need GRUB with 8.04?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by edzell on 2009-01-14
I'm having many problems reformatting HDs, getting rid of remnants of previous OS installations and installing Ubuntu 8.04 by itself. GRUB frequently seems to be involved (sometimes an error with the number 15 has come up.)

First I need to understand - Is GRUB necessary to boot up 8.04; ie is it part of the process or is it - as I believed - only needed to  install more than one OS? And if it's not necessary, how do I get rid of any hangover from previous instances? I've reiteratively written zeroes, re-partitioned, re-re-downloaded to fresh CDs, installed and reinstalled choosing the options to install or not install GRUB, all without success.

Got lots more questions but I need to get past this. There are other parts to my life! Thanks for all responses but please keep them as simple as practical :(

---

### Post by SushiR on 2009-01-14
You will need GRUB to boot Ubuntu. Have a look: [http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

---

### Post by oldos2er on 2009-01-14
It's necessary to have a bootloader, but it doesn't especially need to be grub.

---

### Post by edzell on 2009-01-14
Thanks, SushiR and oldos2er, for the replies - simple enough that even I could understand!

---

### Post by achase79 on 2009-01-14
To fix your error 15 you may have to change the boot order of hd in the BIOS.  I had the same problem and this worked for me.

---

