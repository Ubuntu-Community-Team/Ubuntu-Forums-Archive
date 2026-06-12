---
title: "How to Edit GRUB to see my Windows XP Drive"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by TygerTung on 2009-08-12
I have a new second hand computer now as my other one expired.

Anyway, it only came with a 40GB hard drive as it is an Ex-Lease one.

I plugged my 120GB windows drive into the hard drive after I had installed Ubuntu onto the 40gb drive but the windows doesn't come up in the grub menu, and I can't seem to work out how to add it. Any idea's?

---

### Post by Mark Phelps on 2009-08-12
You will need to manually add an entry to the menu.lst file.

To figure out the info needed, please post the results of "sudo fdisk -lu" (that's a lowercase L, not a one).

---

### Post by kansasnoob on 2009-08-12
> **Mark Phelps said:**
> You will need to manually add an entry to the menu.lst file.

To figure out the info needed, please post the results of "sudo fdisk -lu" (that's a lowercase L, not a one).

+1!

The output from terminal of:

```
sudo fdisk -lu
```

will tell us how Ubuntu recognizes the Win drive.

---

### Post by TygerTung on 2009-08-13
Thanks for your help chaps but I plugged in my old ubuntu drive from my old computer and that worked fine, even though it was a different computer. I was able to transfer all of the data over from the XP drive, reformated and re-installed that, transferred all the files from the ubuntu drive, re-installed and re-formatted that, and now it is all rosy, so I do not need to worry about the grub now!

Thhanks anyway.

---

