---
title: "What's wrong with my bootchart?"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by .nedberg on 2010-04-24
Hi

I installed bootchart and pybootchartgui today. I had a feeling my machine was booting a bit slower than it should. The boot time was 1:01.77. Over a minute! This is on a Intel i5 CPU with 8GB RAM.

Now, I don't understand the bootchart to much, but it looks like it is just sitting there for 25 seconds (from 20 - 45).

My bootchart is attached, could someone have a look at it? What could I do to make it faster?

EDIT: Bootchart is [here]("http://www.nedberg.net/images/amidala-karmic-20100424-4.png") (better quality)

---

### Post by Silent Warrior on 2010-04-24
Just over a minute, eh? Well, you should just see my XP-desktop with 7 Transformation Pack installed, then! :) (Uninstalling that mother improved boot by a good two minutes, at least. 3 GHz CPU, 3 Gb RAM.)

I don't have any of those bootcharting things installed, so I can't help you. One thing that stands out to my untrained eyes, though, is that kdm appears to be launched twice.
All I can think of that might actually have any degree of significance, though, is that it's doing some hardware-detection. (udev-glitch?) Just do NOT assume I know what I'm talking about. 'Cuz I don't.

By the way, I'm currently on a laptop taking just over 40s to boot.
And, well, since Lucid's release is just around the corner - schedule says next week - you could consider just letting this slide and see what the new release brings.

---

### Post by .nedberg on 2010-05-26
*bump*

I have now upgraded to Lucid, but the situation is the same. The machine boots a bit faster, but only about 2-3 seconds. Same problem with about 25 seconds where it is doing nothing.

Could it be mounting NFS and SAMBA shares?

---

