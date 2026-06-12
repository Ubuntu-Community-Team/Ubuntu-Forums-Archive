---
title: "Partition size"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by allenbradley on 2009-04-30
I'm planning on finally kicking out windows from the hard disk. I wanted to create 2 partitions ( namely / and /home ) in my 250 gig hard disk. Considering that I plan to run virtualbox, etc. what would you say is the best way to split the partition ie / and /home?

---

### Post by Paqman on 2009-04-30
You'll need three actually: swap, /, /home.

Swap should equal RAM if you intended to hibernate the machine, otherwise 1GB.

Root needs to be at least about 6-8GB, you might want more if you intend to do anything that makes big temp files (like authoring a DVD). You shouldn't ever need any more than 20GB though.

Home can be as big as you like. If you were going to store your data there i'd have it take up most of the disk. Virtualbox stores it's .vdi virtual drives in a folder in /home by default, so it needs to be able to fit those virtual machines inside.

---

### Post by allenbradley on 2009-04-30
Oh nice to 20( for root ) + 4 ( RAM swap ) + 225 ( /home ), though 225 gb for home seems like overkill since I usually give something like 30gb... Anyways thanks for the quick reply :D Windows is coming down tonight!

---

