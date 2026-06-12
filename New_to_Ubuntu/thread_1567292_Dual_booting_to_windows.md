---
title: "Dual booting to windows"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Gennn89 on 2010-09-03
Hey, have ubuntu 9.10 only installed, taking up entire hard drive, need to dual install windows so I can run some windows software again. Problem is when I go to setup and run my windows boot disc it goes directly to regular ubuntu startup script. Doesn't even see the boot disc. I know my reader is working fine because it reads the disc and all the files correctly on my ubuntu desktop. Do I need a new install disc for windows or is there something else I should be doing so that my stupid laptop will run the setup?

---

### Post by oldfred on 2010-09-03
You still may have a bad disk. 

Windows will not see you hard drive if it only has Ubuntu on it. Windows cannot resize your Ubuntu. You need to use gparted to either make a primary NTFS partition with the boot flag (active partition) or have unallocated space and an available primary partition.

---

### Post by andrewthomas on 2010-09-03
Change the settings in BIOS to boot the cd/dvd drive first.

---

### Post by Gennn89 on 2010-09-03
thanks I forgot about gparted I should know better but I'm still getting familiar with linux. I think its working now. how do i change the bios??

---

### Post by andrewthomas on 2010-09-03
> **Gennn89 said:**
>  how do i change the bios??I guess you can disregard that advice, since you haven't changed it, the cd is probably first already.

---

### Post by Gennn89 on 2010-09-03
Started partition manager and have 178 gigs available to partition but it does not give me the option to create new partition or resize anything without erasing everything. How can I make a new partition without changing any of my current files? Is that possible?

---

### Post by Gennn89 on 2010-09-03
seems the only other option i have is to unmount but Im not sure if I want to click that yet.. dont know what that does..

---

### Post by Gennn89 on 2010-09-03
Ill try partitioning from ubuntu live disc I believe thats how I did it last time. Thanks for your help.

---

### Post by oldfred on 2010-09-03
Unmount just means the partition is not in use. It will not let you modify partitions in use. Often swap is in an extended partition and then then entire extended partition is in use. You need to use swapoff to unmount swap. Not sure if it was click or right click on swap to be able to choose swapoff.

---

### Post by fbobraga on 2010-09-03
this may help: [https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

