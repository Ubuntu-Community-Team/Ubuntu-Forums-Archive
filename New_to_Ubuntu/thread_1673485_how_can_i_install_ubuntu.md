---
title: "how can i install ubuntu"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Mr Areef on 2011-01-22
hello everyone!!!
i have a desktop with 2 hard drives 500GB each the master has 3 partitions and the slave has no partition, im running on windows 7 and i want to install ubuntu 10.10, im asking is`t possible to be seeing the other partitions from ubuntu? and which place is better for me to install it, at the same partition together with windows 7 or separately in a different partition? 
im looking for a suggestion please

---

### Post by dirghrabadia on 2011-01-22
You can access files on your Windows partition from Ubuntu. As for the installation part, you need to have a separate partition on your disk, as the file systems for both are different.

---

### Post by akand074 on 2011-01-22
Ubuntu will have to be on it's own partition. It's up to you whether you want to install it on the same hard drive or the other hard drive. Personally I would probably install Ubuntu on the same hard drive as Windows and use the slave hard drive as a data partition. If you use Windows often you can have your slave as a shared data partition for both Ubuntu and Windows. But it's all what you prefer/what your needs are.

---

### Post by eflix on 2011-01-22
> **Mr Areef said:**
> im asking is`t possible to be seeing the other partitions from ubuntu? 
im looking for a suggestion please
Yes, it's possible to see (read) and even write to other partitions from ubuntu. If you have windows 7 installed you have an NTFS file system, which is supported by ubuntu.
> and which place is better for me to install it, at the same partition together with windows 7 or separately in a different partition? 
You must install ubuntu in a diferent partition, this is other than where you have windows installed, be careful, you will erase your windows install if you select their partition.
Assuming the slave 500gb disk is not partitioned (as in not used) I suggest you to install ubuntu there. But if it has one big partition (the entire disk) you should move your data someplace else before the install

---

