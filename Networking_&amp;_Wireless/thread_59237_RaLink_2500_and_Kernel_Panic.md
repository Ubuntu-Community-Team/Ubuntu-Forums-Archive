---
title: "RaLink 2500 and Kernel Panic"
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by Mr_J_ on 2005-08-23
Hi!

I folowed a howto on installing a Ralink based card.
The problem was revealed when I tried to configure the card.
That is one of the last steps on the howto.

My "System>Administration>Networking" showed the card, and I clicked Configure, but the entire computer froze.
Tried it 2 more times just for good measure.

Finally I did a Dmesg and it said kernel panic all over the place.

I folowed the error and it comes all the way from the "make" step.

So I can only get stuff into a USB pen and get them unto ubuntu, no downloading.

Which means I did not get the package with Wget, and also no Raconfig step.

What should I do?

---

### Post by macgyver2 on 2005-08-23
[QUOTE=Mr_J_]Hi!

I folowed a howto on installing a Ralink based card.
The problem was revealed when I tried to configure the card.
That is one of the last steps on the howto.

My "System>Administration>Networking" showed the card, and I clicked Configure, but the entire computer froze.
Tried it 2 more times just for good measure.

Finally I did a Dmesg and it said kernel panic all over the place.

I folowed the error and it comes all the way from the "make" step.

So I can only get stuff into a USB pen and get them unto ubuntu, no downloading.

Which means I did not get the package with Wget, and also no Raconfig step.

What should I do?[/QUOTE]
From [this]("http://www.ubuntuforums.org/showthread.php?t=53035") thread:
[QUOTE=jdong]The kernel panics have been associated to PREEMPT (they're working on fixing it), and some issues with sending data before association have been solved in CVS, too. I highly recommend running nightly snapshots as opposed to the beta releases :)[/QUOTE]

---

