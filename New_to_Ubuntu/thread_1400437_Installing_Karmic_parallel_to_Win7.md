---
title: "Installing Karmic parallel to Win7"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-02-06
I have Win 7 and have "shrunk" the MS partitions leaving about 300gig for Karmic. Using GParted (LiveCD) I have made 3 partitions on the space Win7 doesn't use, that is, the unallocated to Win7 was set to 12 gig (for /), 271 gig (for /home), and 7.5 gig (for Swap). Actually the Win7 install offered to change partition size as this was/is a self-installed Win7. So I shrunk my 400 gig drive to about 100 meg for the Win7 "Loader" partition and about 40 gig for the "user" partition.

When I tried to use Karmic-Desktop-CD, the video was larger than my screen, I couldn't tell what I was doing. The prompts were "off screen" so to speak. 

P.S. I have both a 400 gig SATA and a 320 gig IDE. When I tried to install Karmic (Desktop-CD), it added partitions to the IDE drive. That's not what I'm trying to do. The 320gig was all Linux-Karmic, NO windows. The 400 gig drive is to be about 40 gig for Win7 and the remainder (360 gig) for Karmic. But I want Karmic to have a separate /, /home/ and /swap partitions. 

I want to install Karmic, as above with a separate /home, root and swap partition(s) and be able to have Grub2 offer the choice of win7 or Karmic. How do I do that?

---

### Post by Paqman on 2010-02-06
You'll need to select Manual Partitioning in the installer to do that. Just select the partitions, format them as EXT4 for / and /home (swap is just formatted as swap), then assign them the correct mount points ie: / and /home. It's pretty straightforward when you see it on the screen.

7.5GB is pretty big for swap. If you've got more than 1-2GB of RAM I wouldn't bother with any more than 1GB swap, as you're unlikely to use it much (or at all). The only exception to this is if you want to use hibernation, in which case you swap must be at least the same size as your RAM.

---

### Post by NCLI on 2010-02-06
Sounds like the default graphics drivers don't like your system. If I were you, I'd use the Alternate CD to install in text mode.

---

### Post by Paqman on 2010-02-06
You can also drag windows about by holding down alt while clicking on any part of the window. Very handy if the buttons are off the screen.

---

