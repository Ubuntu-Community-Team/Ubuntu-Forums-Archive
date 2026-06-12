---
title: "Problems with reading an extranal HDD"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by hannulan on 2009-10-25
I have a hdd which I try to copy data from to my laptop. The hdd was previuolsy used in the laptop, but due to some strange sounds I decided to buy a new one. Now I want to copy the data from one out of three partitions on the old hdd to the new hdd (which I have put into the laptop). 

I put the hdd in the hard drive enclosure and connect it to the laptop. I can now see the three partions in the file browser and in the terminal. But I can not copy or list what is inside them. Since there is alot if data I have tried to wait a long time (during the night) before ending the "ls"-command. But it never works.

Anyone that have a suggestion to what I shall do?

---

### Post by earthpigg on 2009-10-25
> But I can not copy or list what is inside them.

can you be more specific?

have you ruled out this being a software problem by booting your computer using a LiveCD and plugging the hard drives in then? will take 5 minutes, and tell us with near certainty if we need to look with a critical eye at your ubuntu install or at the hard drive itself.

should also try different USB ports for the same reasons.

---

### Post by mapes12 on 2009-10-26
If it's a permission issue you could try launching Nautilus with root permission and see if you can then move them: Applications>Terminal ```
gksudo nautilus
```OR you could try copying the entire partition to a partition on your new HDD. For example ```
dd if=/dev/sdb1 of=/dev/sda1
```will copy the partition called sdb1 to sda1.

It will overwrite everything in the destination partition so be careful.

---

### Post by LewRockwell on 2009-10-26
yes, that dd stuff will get you into trouble if you goof up

we just use the Puppy Linux LiveCD to mount partitions and manipulate directories, files, and data

(boots faster than other LiveCDs and runs in root)

.

---

### Post by ext3 on 2009-10-26
What is the file system on the hard drive that you placed into an external enclosure?

---

