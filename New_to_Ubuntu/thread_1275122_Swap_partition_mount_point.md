---
title: "Swap partition mount point"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by paynek716 on 2009-09-25
I am manually partitioning my hard drive for a dual boot installation with Windows Vista.

What is the mount point for the swap partition? I have my root partition mounted at / and home partition mounted at /home.

---

### Post by drs305 on 2009-09-25
In fstab, your swap should look something like this:
> 
UUID=ced74554-9ae2-470c-9da9-84d86cefddbc none  swap    sw    0 0


If you format it as swap, you don't need to make a specific swap mount point.

---

### Post by paynek716 on 2009-09-25
Thanks. I overlooked the "use as swap area" when creating the partition.

---

