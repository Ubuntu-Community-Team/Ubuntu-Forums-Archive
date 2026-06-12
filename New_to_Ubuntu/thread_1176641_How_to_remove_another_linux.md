---
title: "How to remove another linux?"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by blasmolero on 2009-06-02
Hello!,
New at all in Linux.
I have a new PC machine where I have two partitions: 500 GB for Windows XP and another 500 GB where I have installed another Linux flavour. 
 
When I boot the computer I see a GRUB screen where I can choose between Windows or the oher Linux flavour.
 
But I want to try UBUNTU x64 and then I want to get rid of the other Linux flavour -- How to do it?. How to remove a Linux installation without risk to remove the WinXP installation?
 
Please inform -- thanks!.;)
 
Best regards,
Blas.

---

### Post by philinux on 2009-06-02
The 64 bit live cd will show you your existing partitions. You would need to use the manual partitioning to install the new distro over the old.

In your distro thats installed can you post the output of 

```
sudo fdisk -l
```

---

### Post by dje on 2009-06-02
Boot the ubuntu live cd and start the install. At the partitioning stage select manual and delete the other linux partition and use the free space to setup your own partitioning scheme. Ubuntu will install it's grub over the old one. **Of course this will remove everything on the old Linux partition so if you need anything on it, do a backup!!**

---

### Post by Therion on 2009-06-02
Since you don't "remove" an operating system from you hard drive like you would an application your only practical option, really, is to reformat the partition that it sits on and then reclaim the space by resizing the partition or partitions you want to keep with the reclaimed space.  Make sense?  To do that you'll need to use something like gParted LiveCD and you'll need to be able to properly identify the individual partitions.  If you can do that, the rest is easy.

---

### Post by blasmolero on 2009-06-02
Thanks to all, I will try!!.
Best regards,
Blas.;)

---

