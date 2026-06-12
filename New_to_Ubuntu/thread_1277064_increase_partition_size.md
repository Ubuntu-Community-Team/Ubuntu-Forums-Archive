---
title: "increase partition size"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by albert5 on 2009-09-27
I need to increase my partition size for Ubuntu as I am running out of memory. I tried using the installation disk and edit partition size without any success

---

### Post by lindsay7 on 2009-09-27
The tool you want is Gparted (partition editor).  With this application the partition or drive must be unmounted. You can right click on the partition or drive and unmount it, then you can work on it. You can use the live installation disk to do this.

---

### Post by Diabolis on 2009-09-27
You have to provide more info. What have you tried and what were the results? The Live-CD , Gparted, should work fine.

---

### Post by Paqman on 2009-09-27
What problem did you encounter using the LiveCD?

One common problem is that the LiveCD will automatically mount your swap partition when it boots (to improve performance). If your swap is located within an extended partition then that whole extended partition counts as in use, preventing Gparted from making any changes to it.

The solution is simple, right click your swap partition in Gparted and "swapoff".

---

