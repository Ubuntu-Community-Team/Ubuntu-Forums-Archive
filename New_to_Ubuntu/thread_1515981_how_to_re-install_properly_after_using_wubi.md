---
title: "how to re-install properly after using wubi?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by ruslanoid on 2010-06-23
first of all i must admit i did a pretty stupid thing - i installed the lynx using wubi from my existing vista :oops:

now i want to do it again - properly this time.

p.s. don't care about the current home folder, but if someone knows how to preserve that too - it would be great for future reference.

thanks in advance ):P

---

### Post by Paqman on 2010-06-23
> **ruslanoid said:**
> first of all i must admit i did a pretty stupid thing - i installed the lynx using wubi from my existing vista :oops:


Nothing stupid about that.

> 
now i want to do it again - properly this time.

p.s. don't care about the current home folder, but if someone knows how to preserve that too - it would be great for future reference.


There's a couple of ways to go about this. You can use [LVPM]("https://wiki.ubuntu.com/WubiGuide#How do I migrate to a real partition, and/or get rid of Windows entirely?") to migrate your Wubi-installed system to a partition. Or you can nuke Wubi by booting into Windows and removing it from the standard Windows uninstall tool, then install Ubuntu from scratch.

To preserve your home folder in the latter case, just back it up somewhere (make sure you get all the hidden .folders, press Ctrl-H to make them visisble). Then after you've reinstalled, paste them back in. If you have/had multiple users on either system you may need to make sure you get the permissions right on the files when you paste them back in. Make sure they're all owned by you.

---

### Post by ruslanoid on 2010-06-23
thanks, paqman
will look into that

---

