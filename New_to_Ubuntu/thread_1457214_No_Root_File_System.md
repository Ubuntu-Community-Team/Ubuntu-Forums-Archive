---
title: "No Root File System"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by namealreadytaken on 2010-04-18
Hello,

I am a complete beginner to ubuntu. I am trying to install version 9.10, iso on Microsoft Virtual Machine 2007.

I am encountering a problem on step 4 of the installation process.

The message "No root file system" displays; click the Partition menu to fix the problem.

I am unable to find the partition menu. How do I fix this error?

Thanks,
namealreadytaken

---

### Post by Jeanke on 2010-04-18
Hi,

Which option did you choose in step 4?
"Erase and use entire disk" or are you trying to install Ubuntu together with another OS on the same virtual disk?
I would recommend to install Ubuntu on a dedicated new Virtual disk.

If this is what you did and already choose "Erase and use entire disk" after which you received this message, you can choose "Specify Partitions manually" instead.

The partition editor will start up and you will have to create a new Partition table with at least 2 partitions:
1 root partition (/) -> used by system, recommended size 8gb or more
1 swap partition -> recommended size at least same as your physical RAM

Additionally you can also create a home partition (/home) where your personal data will  be stored (if no home partition is created ubuntu will use the root partition to store personal data).

---

