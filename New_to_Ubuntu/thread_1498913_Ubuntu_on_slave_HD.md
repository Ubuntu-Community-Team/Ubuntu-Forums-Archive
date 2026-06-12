---
title: "Ubuntu on slave HD"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by pauligit on 2010-06-01
I've got a totally newbie question.

Can the most recent versions of Ubuntu be installed at a primary partition in a slave HD?

I've got to buy a new computerand, since I have the old one's HD, I thought it would be a good idea to use this one for Ubuntu only, and the new HD for Windows.

Is it possible to boot Ubuntu from a primary partition at a slave HD? Or should I create a primary partition at the master HD for /boot in which to store the kernel image? If so, how much space should I reasonably reserve at the new HD before the Windows partition?

I haven't used GNU/Linux for quite a while, but I recall that in past times, I had difficulties to boot an image stored in a slave HD.

Cheers,

Paul

---

### Post by egalvan on 2010-06-01
Linux can boot from almost any drive.

main drive, slave drive, primary partition, logical partition,
network drive, etc...

Exactly HOW it is set set up is more a personal preference...

GRUB can be set up on the main boot drive, or you can even set up GRUB with it's own partition...

here is a link to a how-to on that...

[http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

### Post by pauligit on 2010-06-02
> **egalvan said:**
> Linux can boot from almost any drive.

main drive, slave drive, primary partition, logical partition,
network drive, etc...

Exactly HOW it is set set up is more a personal preference...

GRUB can be set up on the main boot drive, or you can even set up GRUB with it's own partition...

here is a link to a how-to on that...

[http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

Thank you!

---

