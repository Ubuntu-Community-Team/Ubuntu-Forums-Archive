---
title: "Modify the partitions of a bootable Ubuntu drive?"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by MatthewWilliams on 2011-07-06
I have Ubuntu 10.10 installed on an 8 GB drive. Since space is low from the start, I would like to have the actual OS take as little space as possible. Here's a picture of what it looks like in GParted, with annotations for your convenience:

_[THIS IS MY LINK. THERE ARE MANY LIKE IT, BUT THIS ONE IS MINE.]("http://i.imgur.com/RhwkN.png")_

I would like to have it look more like this:

_[LINK THE SECOND]("http://i.imgur.com/MBesE.png")_

My questions are:

[LIST][*]Can I do this without breaking the OS?[*]If I can, how would I go about doing it? GParted just gives me an error.


[/LIST]

---

### Post by mikewhatever on 2011-07-06
Yes, as far as Gparted is concerned, it will probably work and the system will remain bootable.
That said, leaving nearly zero of free space on the root partition may make the system unbootable or less functional. You might want to consider a custome installation with only the programs you need, or, if you must have the full blown desktop, get a bigger flash drive.

---

### Post by MatthewWilliams on 2011-07-06
So it will still work, but it's probably a bad idea? Alright.

I don't plan on using it too much anyway, mostly just on computers I'm not used to. I don't think it would be worth it to go to the trouble to put together a custom installation.

I suppose I can cut back on what I have, if I'm not using it that much anyway. :3

Thanks.

---

### Post by mikewhatever on 2011-07-06
If the computers you use it on have 1GB or more of RAM, the swap partition isn't really needed. You might want to first check if swap ever gets used.

---

### Post by Miljet on 2011-07-07
What you have marked as Unnecessary Space is actually needed for temp files, log files, updates and so forth.

I would consider eliminating the separate /home. The unused space could then be used either by the system or to hold personal data.

---

