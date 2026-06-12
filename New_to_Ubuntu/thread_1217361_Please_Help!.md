---
title: "Please Help!"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by daniell59 on 2009-07-19
I don't have a clue what to do.

Thanks

---

### Post by halitech on 2009-07-19
run
```
fsck /dev/sdb5
```and allow it to fix any errors

---

### Post by philinux on 2009-07-19
type this in

fsck /dev/sdb5 -v

press enter, if the check offers to fix any errors press the y key.

---

### Post by daniell59 on 2009-07-19
> **halitech said:**
> run
```
fsck /dev/sdb5
```and allow it to fix any errors

Thanks, but how do I run it?

---

### Post by halitech on 2009-07-19
from the prompt you are at currently, type in the command in the code box

---

### Post by daniell59 on 2009-07-19
> **halitech said:**
> from the prompt you are at currently, type in the command in the code box

Thanks, I will try it later and get back to you.

---

### Post by Elep.Repu on 2009-07-19
Yes, running fsck is a little scary looking. ;)

---

### Post by Vined Adobo on 2009-07-19
Click on Applications > Accessories > Terminal.  You may have to type sudo (super user do) first and may need to enter your password.
Hope I helped a little
Dave

---

### Post by philinux on 2009-07-19
> **Vined Adobo said:**
> Click on Applications > Accessories > Terminal.  You may have to type sudo (super user do) first and may need to enter your password.
Hope I helped a little
Dave

I'm afraid if he did that it would mean running fsck on possibly a mounted file system. Very dangerous. From his monitor you can see that the system has mounted the partition as read only. Also when he's dropped to the shell when the fsck failed he is root so no sudo needed.

---

### Post by daniell59 on 2009-07-19
I typed fsck /dev/sdb5

It is now working normally. What I did, I do not know.
I wish that I understood what I did.

Thanks

---

### Post by halitech on 2009-07-19
basically when the system started, it did a check on the filesystem of the drive and detected errors and it gave you the command to run. when you ran the command, it fixed the errors and allowed you to start

---

### Post by philinux on 2009-07-19
+1 

Also if you did a hard reboot by pressing the power button can result if fsck failure.

---

