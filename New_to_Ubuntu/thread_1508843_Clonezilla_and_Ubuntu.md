---
title: "Clonezilla and Ubuntu"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by kenb12 on 2010-06-13
Using Clonezilla, cloned a drive of about 114Gb to a drive of 250Gb which was previously formatted with Windows NTFS, I find that the cloned drive shows up as 114Gb.
What is the position of installing more programs to exceed this 114Gb.Can this be done.
Is the reality that the 114Gb is the full size available and no increase is possible.

---

### Post by howefield on 2010-06-13
Why not do it again, only properly this time ?

By default Clonezilla will make the clone the same size as the original disk. You need to enter expert mode and tell it what you want to do.

There are some good documents on the Clonezilla website eg,

[http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone](http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone)

---

### Post by kenb12 on 2010-06-14
Thanks for your reply.
Being a Novice, I did not want to attempt the Expert way, in fact never gave it a thought.
Will also go to the Clonezilla site as you suggested.
Thanks for your help much appreciated.
Kb

---

### Post by Mark Phelps on 2010-06-14
> **kenb12 said:**
> Using Clonezilla, cloned a drive of about 114Gb to a drive of 250Gb which was previously formatted with Windows NTFS, I find that the cloned drive shows up as 114Gb.
What is the position of installing more programs to exceed this 114Gb.Can this be done.
Is the reality that the 114Gb is the full size available and no increase is possible.
That's what "cloned" means -- an exact copy of your original partition -- not drive.  Drive is a physical thing; partition is a logical thing.

But, you can use3 GParted to expand the size of the partition if you wish.

---

