---
title: "I made a boo-boo! Help!"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by sixthwheel on 2010-05-09
Went to the book store and picked up a copy of Linux Magazine.
There was a CD of Debian 5.0.4 in there, which I just had to try out.:confused:

I wanted to try it live and see what it looked like.
So I pop in the CD and did not see any option to run it without installing.

So I figure since I have time,(I'm on vacation this week) I might as well make some space for it and install the thing.

Well, when the partitioner thing came up (yes, I can see that you know where this is going):P instead of telling it to just use 20% of my Karmic partition, I guess I told it to just leave 20% of it and reformat the rest.

By the time I realized this, it was too late, so I went ahead and installed Debian on the 80% size.

Then I made another boo-boo.
At the end of the install, something happened to grub.

Now when I boot, it doesn't see Debian, just sees my 2 other OS's. (Karmic, and Lucid), However my Karmic is now 80% smaller.

Is there anyway, that I can uninstall debian, and get back the lost space on Karmic?

Thanks in advance.

---

### Post by -humanaut- on 2010-05-09
Load the Debian CD go to options expert install and just install grub should fix it up.

---

### Post by sixthwheel on 2010-05-09
I did that, thanks.
How do I get rid of it and get my space back on Karmic?

---

### Post by -humanaut- on 2010-05-09
Load up Karmic and use Gparted ( sudo apt-get install gparted ) If its ext2,3,4 you should be able to expand it with no problems.

---

### Post by sebastianabate on 2010-05-09
> **-humanaut- said:**
> Load up Karmic and use Gparted ( sudo apt-get install gparted ) If its ext2,3,4 you should be able to expand it with no problems.

But this only works if the partition is not the root one, becouse you must unmount the partition to expand it. If it is the root partition you can use the Ubuntu livecd to do that.

---

### Post by sixthwheel on 2010-05-09
Thanks I got it done...Playing with Fedora 12 now.:P
This may be a long week of vacation.:)

---

