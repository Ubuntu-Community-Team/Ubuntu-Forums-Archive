---
title: "Is Virtuialization Required"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by DGINSD on 2011-08-20
I'm building a custom kernel for my laptop that's a rather old machine its a Dell Inspiron 1150 with an Intel mobile Pentium 4 and 768M of RAM, I'm trying to, build in support for the hardware, minimize the kernel size and eliminate all the parts I'll never use. The Pentium 4 chip supports virtualization but I read that in order to run, say like a windows VM, you would need at least 1G of RAM for it to even work and more likely 2G to make it functional. I'll likely get a new computer before I upgrade the memory, so I will never be running any type of virtualization on this computer, my question is does Ubuntu 10.10 require this portion of the kernel for it to operate properly (desktop switching) or can I eliminate  it?

My next question is regarding file systems I'm using ext4 for my Linux partitions and my Windows XP is on a NTFS volume. Other than those two is there any reason I need to include support for any other type of file systems, including FUSE and NFS?

I also read in one article that another item to remove support for to drastically reduce the kernel size is debugging, so is debugging required or really needed?

I tried getting help from the Kernelnewbies forum but the sites forum seems to have been spammed to death with ads and what not, and I got no answers (posts likely got lost in the sea of ads). Any help is appreciated.

---

### Post by androssofer on 2011-08-22
> **DGINSD said:**
> I'm building a custom kernel for my laptop that's a rather old machine its a Dell Inspiron 1150 with an Intel mobile Pentium 4 and 768M of RAM, I'm trying to, build in support for the hardware, minimize the kernel size and eliminate all the parts I'll never use. The Pentium 4 chip supports virtualization but I read that in order to run, say like a windows VM, you would need at least 1G of RAM for it to even work and more likely 2G to make it functional. I'll likely get a new computer before I upgrade the memory, so I will never be running any type of virtualization on this computer, my question is does Ubuntu 10.10 require this portion of the kernel for it to operate properly (desktop switching) or can I eliminate  it?

My next question is regarding file systems I'm using ext4 for my Linux partitions and my Windows XP is on a NTFS volume. Other than those two is there any reason I need to include support for any other type of file systems, including FUSE and NFS?

I also read in one article that another item to remove support for to drastically reduce the kernel size is debugging, so is debugging required or really needed?

I tried getting help from the Kernelnewbies forum but the sites forum seems to have been spammed to death with ads and what not, and I got no answers (posts likely got lost in the sea of ads). Any help is appreciated.


think this was perhaps to advanced for absolute beginner talk.. 

not sure about the 1st part. but i could set up an ubuntu vm on my machine with similar specs to ur comp, and take out the same kernel modules u wanna remove and c wot happens...? 

tho i dnt know how.. so any docs/links on removing/recompiling kernel modules? is an area i know little about, so will b funs to learn :-). and wud help u with ur question...

---

