---
title: "Help with initial installation"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by tebucky on 2009-01-29
I'm trying to install a fresh version of the latest version of ubuntu over an old linux OS on a relatively old machine.  I can boot from the dvd, and begin the install without problem (I can set the time, login info, hostname etc).

At the point when it tries to format the drive it gets about 5% done then it loops back to the drive partition selection view and I start steps 4-7 all over again.  

I'm puzzled and can't understand what is happening.  I'm pretty much a newbie and would appreciate some help. 

TIA

---

### Post by taurus on 2009-01-29
Why not use gparted in System -> Administration and delete all the partitions on your harddrive.  Then, create one large partition that takes up the whole space of your harddrive and format it to ext3 filesystem.  Now, tell the installer when you get to the partition part to use the whole harddrive unless you want to partitions it first, creating something like /, /home, & swap.

---

### Post by tebucky on 2009-01-29
So I think I know what you're saying here.  I am trying to make one new partition on the entire drive and select that option when presented.  It starts to format it to ext3 and gets roughly 5% done the loop back to the previous steps.  Does this make sense?

---

### Post by Idaho Dan on 2009-01-29
tebucky,
I could not use gparted properly when I tried with my old machine.
I upped the ram from 64MB to 768MB [maxed it out] and then I could use gparted just fine.
I guess what I'm trying to say is do you have a decent amount of ram? [Only thing I could think of.]

Dan.

---

### Post by tebucky on 2009-01-29
I have 512 memory installed, do you think I need more?

---

### Post by smothpocket on 2009-01-29
512 should be more than enough. I just recently ran it from a computer with just 256.

---

### Post by egalvan on 2009-01-29
> **tebucky said:**
> I have 512 memory installed, do you think I need more?

512m is more than enough.

But your hard drive may have problems.

Go to the manufacturer's web site and download test software.

Run it and check the hard drive.

Then run the memcheck option from the LiveCD.

---

