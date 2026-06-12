---
title: "No dist space error but 445g free disk space"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by pachiko-ichiro on 2009-05-13
I Have Ubuntu installed after I had Opensuse installed. The Hard drive has 445G of free space. 

When I try to install things on Ubuntu it says there is not enough disk space. 

What how is this possible and how do I fix it?

---

### Post by Cornbreadly on 2009-05-13
Can you you provide more info? At what point do you get the error?

Step 4 in the install from the live cd is done with a partition editor.  Here you can review how much space and where to install ubuntu. 

If you do not have anything to save... go with the clean install by wiping it all.

---

### Post by Ericyzfr1 on 2009-05-13
How did you partition your drive?

---

### Post by 123456789123456789123456 on 2009-05-13
I'm wondering the same thing, If you did not tell the partition editor to use the entire disk, then it would have placed Ubuntu, and the swap partitons at the end of the disk, and still have opensusi installed in the first partition.  Does it give you a boot menu, to choose the OS?

Ubuntu should only be using about 4gb for a full install, even with all the files you can possible download and install, 445gb should be more than enough space for the OS.

The only thing I can think of is that the Ubuntu partion is not the 445g
But we need more information, Go to partition or disk editor in Gnome, and give us the inforamtion it has listed, or at the very least, go to the properites of the file system, and give us the detales, about when it says, total disk space, space used, and space available.

---

### Post by pachiko-ichiro on 2009-05-13
I let the system install itself, when I got the partition editor I selected the first option "side by side"

I didn't think anything of it. 

Now I'm looking at it and it is telling me I only have 2.3g for the ubuntu, would I have to reinstall the system?

I really don't want to do a clean wipe and re-install both Distros

---

### Post by 123456789123456789123456 on 2009-05-13
Should not need to, I don't know how it slid back the other distribution to make room for Ubuntu.
Try reinstalling Ubuntu.  when given the partitioner, tell it, manually configure.
there resize the first distributions space, as much as the partioner will allow you, giving ubuntu as much space as you can, you will note that you will have to remove the Ubuntu partition first.

---

