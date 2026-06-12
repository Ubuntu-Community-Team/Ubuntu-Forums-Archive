---
title: "Need help setting up new home partition"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by cyan on 2009-01-18
Hello, everyone.  I'm a Linux noob and have managed to set up a dual book Asus EEE pc with Ubuntu 8.04 and WindowsXP without too much heartache.

Now I want to set up a separate home partition.  In part so I always have my home files preserved even if I screw up my install but also so that I can test new distros or upgrades without losing my stable set up or settings.

Here is a screenshot of my current partitions:

[IMG]http://copilyanez.com/images/Screenshot3.png[/IMG]

I have three questions.  First, does it matter that all my Linux partitions are in one extended partition?

Two, I was unable to put the small unallocated amount of space into any other partition.  sda5 couldn't be extended to take it and when I tried to extend the swap partition to take it, it erred out before completion.  Should I just extend this small unallocated space to become the new home partition?

Finally, to set up a new partition for home, does it matter if it's under sda2, the extended partition?  Or should it be on it's own?

Thanks for everyone's help!

---

### Post by laurielegit on 2009-01-18
1. If it's been working so far, I can't see why it should stop working. Ask a expert though.

2. I suggest using it as a /boot partition, as it is just about the right size, and having a /boot partition is a good habit. As for a /home partition, I would move all your current /home files to an external hard drive, then delete them in the ubuntu partition, making it (probably) about 1/2 the size. Then make the ubuntu partition 20-30 gig or so, and make another 50 gig partition for /home. Copy your files back into the new /home partition. Leave the rest unpartitioned (another good habit), so that you can install other operating systems if you want. Also, BACK UP YOUR FILES before you do anything.

3. I doubt it, as your current /home folder is under sda2

Good luck,

Laurie

---

