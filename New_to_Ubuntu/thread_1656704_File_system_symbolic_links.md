---
title: "File system symbolic links"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by AlphaTwentyEight on 2010-12-31
I made my /root directory partition too small.  Can I link important system files outside of the /root directory?

I found the (shift + ctrl ) feature, but my question is, should I move the contents of the moved file to the new file and then make a link to the file where the original was located?

How does that work?

---

### Post by TeoBigusGeekus on 2010-12-31
Instead of that, boot up with a live cd and expand your root partition with gparted.

---

### Post by AlphaTwentyEight on 2010-12-31
OK, if I have files on the partitions that are not root will I lose those files when I expand the root partition?

I figured out / stumbled upon a different workaround to the greater problem.  Which was getting my sound to work, for some reason it wasn't.  I purged the games, deleted the default kernel and upgraded to the newest kernel image and everything works now, so I wont need those other programs to make my sound work.  

But I am sure that I will want to download more packages.  sometime,  

I should leave 20% empty drive space for fdsk (or whatever its called) right?  If thats true then I will need to expand the partition.

---

