---
title: "Triple Boot Question"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by KBD47 on 2011-08-19
What I'd like to do may be above my pay grade, but thought I'd ask:
I have Win7 and Mint 11 as a dual boot on my netbook. It has a 250 gig hard drive, so it has room for another system. I would like to add Ubuntu 11.04 as a back up Linux system and make my computer a triple boot system. My question is this: If I install Ubuntu and tell it to install alongside my other operating systems, will it automatically set itself up and will this work, or will I need to delete partitions and create new ones manually for this to work? 
Thanks.
KBD47

---

### Post by critin on 2011-08-19
It has automatically set itself for me a few times.  Usually though, I divide the disk into smaller partitions and choose one.  But to answer your question--it has for me with no problems.
critin

---

### Post by KBD47 on 2011-08-19
Thanks critin!
  I wonder whether or not it is worth waiting for 11.10 or if there will not be much difference from 11.04?
KBD47

---

### Post by critin on 2011-08-19
I wouldn't wait.  lol  You can always upgrade if you want to from synaptic updates or clear the partition and do a clean install of the newer.  Probably won't be a lot of difference between them, but I don't know.
critin

---

### Post by KBD47 on 2011-08-19
Thanks again!
KBD47

---

### Post by scruffyeagle on 2011-08-19
> **KBD47 said:**
> What I'd like to do may be above my pay grade, but thought I'd ask:
I have Win7 and Mint 11 as a dual boot on my netbook. It has a 250 gig hard drive, so it has room for another system. I would like to add Ubuntu 11.04 as a back up Linux system and make my computer a triple boot system. My question is this: If I install Ubuntu and tell it to install alongside my other operating systems, will it automatically set itself up and will this work, or will I need to delete partitions and create new ones manually for this to work? 
Thanks.
KBD47

Hi! Just thought I'd pause here to state the obvious, that before attempting this you should backup your data files onto a separate storage device.

In order to set up Ubuntu as a completely separate OS (not using Wubi & Windows), you'll need to put it somewhere that's separate at a basic level. So, you'll need a partition for it. Gaining the space for that partition will probably require repartitioning to subdivide your data storage area into 2 partitions. (I'm assuming your data storage area got the lion's share of that 250 GB.) I'd suggest using the 1st 20 GB as the Ubuntu partition. That's an overly generous allocation, but w/ 250 GB you can afford it for the sake of making it guaranteed it will never run out of space for programs. Then, the remainder not used by Ubuntu could be allocated to a data storage partition.

Of course, given that you seem to like experimenting, you might want to leave a 2nd 20GB area after the Ubuntu system partition unallocated. That would leave room for adding a 4th OS later if you find yourself feeling ambitious.

So, yes, I would say that repartitioning is a necessity for what you're trying to do. Begin by making a backup of your data files, because the most likely case is that the repartitioning will wipe them out and you'll need to import them back onto the drive when you're done. I don't know for a fact, but it's my expectation that Ubuntu's use of Grub should have no problems setting up the 3-OS boot options.

Good luck!

---

### Post by KBD47 on 2011-08-19
Well I took the plunge and did it, and it worked great. I let Ubuntu automatically set up the partition. If I knew more about it I would have done it myself, but just let it default. It had the partition at 60 gig for Mint and set 40 gig for Ubuntu. I've booted up a couple of times now and once in Mint and everything seems to be fine. I will go ahead and mark this question solved.
Thanks guys!
KBD47

---

### Post by critin on 2011-08-19
Great!  It was pretty easy, right?

critin

---

### Post by KBD47 on 2011-08-19
Yes, It was quite painless, but just in case I had burned win7 backup dvds and rescue disc and have my files backed up with dropbox. Also should note I had played around a bit with Natty on usb to make sure she worked well on my computer before deciding to install it. Now have win7 (never use it but just in case) Mint 11 (great for windows users converting to Linux) and Ubuntu 11.04 (which is a strange creature that I'm just starting to get used to). Thanks again for the encouragement!
KBD47

---

