---
title: "HELP PLEASE! Startup Disk (UBUNTU)"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by tusharsingal on 2010-11-11
Hello, when I want to create a startup disk in Ubuntu, I can't select the extra space option! :confused:
As you see (attached) it is grayed out.
Please help. I'm sure you pros know what to do. Just quick reply.

---

### Post by psusi on 2010-11-11
What?  Click the make startup disk button.

---

### Post by psusi on 2010-11-11
Ohh, you mean the persistent storage?  I think that was a known bug in lucid... click the button to choose the iso, browse to it, and select it.  When it comes up with the right one by default for some reason, it doesn't enable the persistent storage.

---

### Post by tusharsingal on 2010-11-11
> **psusi said:**
> Ohh, you mean the persistent storage?  I think that was a known bug in lucid... click the button to choose the iso, browse to it, and select it.  When it comes up with the right one by default for some reason, it doesn't enable the persistent storage.

So no fix? *cries in a corner*

---

### Post by toekneewood on 2010-11-11
I have seen this in the past.  I did something like, umount, then erase and then select the partition/drive (one or the other).  If you pick the wrong one it will appear greyed out.  The other thing I have down is erase the drive in gparted and then launch the Startup Disk Creator and try again

---

### Post by toekneewood on 2010-11-11
Just done a test run, I had to select my /dev/sdf1 not the /dev/sdf

---

### Post by bubbapete on 2010-12-30
So I had this same problem. After I selected the iso and the drive, I erased the drive with the "Erase" button, and the "Make Startup Disk" button returned. If you need the data on the drive, you can always back it up first.

---

