---
title: "How do I access files on Linux partition from Windows?"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by Old *ix Geek on 2007-06-23
I've never needed to do this before, but now I do: On my laptop, which dual boots Feisty and Vista (which I never use!), how the heck do I access the Linux partition from Vista?  I've looked through everything that seemed likely [which, on windoze, is a convoluted, nonintuitive waste of effort] but am finding no way to tell it to connect to the Linux partition.  (Vista's "Network" shows all OTHER computers on the network, but not the other partition on the same computer it's on.)

---

### Post by Swab on 2007-06-23
You need a third part app in Windows..  

Try this [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Old *ix Geek on 2007-06-23
Thanks...but I just tried it and it failed with an error modal that it only runs on versions blah blah blah...but I have Vista.  Any other ideas?

ETA:  I just found [explore2fs](http://www.chrysocome.net/explore2fs) (which, despite its name, also explores ext3 partitions--which is what I have), and I THINK it's going to work.

---

### Post by Swab on 2007-06-23
> **Old *ix Geek said:**
> 
ETA:  I just found [explore2fs](http://www.chrysocome.net/explore2fs) (which, despite its name, also explores ext3 partitions--which is what I have), and I THINK it's going to work.

Excellent!

---

### Post by Old *ix Geek on 2007-06-23
Update: Explore2fs is REALLY good!  Right now I'm furiously copying directories from my Linux partition over to the 'doze partition with it.  I highly recommend it!

---

### Post by StGeorge on 2007-06-23
That a good idea.
But how do I do it from 98SE.
Any ideas.
I keep having to restart into Ubuntu at the moment when I forget to save files from Ubuntu on my D: Drive.

---

### Post by StGeorge on 2007-06-23
Silly me should have gone to your link.
Of now into Winblows to try it.

---

### Post by StGeorge on 2007-06-23
Brilliant.
[explore2fs]("http://www.chrysocome.net/explore2fs")
This works great.

---

