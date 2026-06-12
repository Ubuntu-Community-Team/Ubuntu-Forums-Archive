---
title: "Memory and DVD burning problem"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by jcslzr on 2010-01-14
Supposly I do not have enough memory in my disk to burn a dvd in DeVeDe, but I just install it in a 11 GB partition, and have not saved much. When I check it with disk usage analyzer its says i have 18 gbs in the partition and have used 13.

Devede tells me that i need 75000 mbytes to burn the dvd and that i only have 3641 mbytes available.

By the way God bless everybody that makes Ubuntu possible, thanks its pretty fast and awesome.

Regards
Carlos

---

### Post by lisati on 2010-01-14
Video & DVD production software commonly needs more disk space than the size of the the final "product" needs. At least the software I have used does. One reason is that it doesn't always do a direct "translation" from the source material to the target, but sometimes needs to do some kind of work on it first.

---

### Post by jcslzr on 2010-01-15
Thank you Lisati,

But its seems to me that I must have a problem on how my ubuntu sees memory space because i just install it on 11 gb and just have a 700 mb file and the standard original files, and everywhere i check gives me different numbers

its there a way to find out real memory usage or why the different tools in ubuntu give me wrong information, its there like a defragmenter for ubuntu?

it may be i used wubi and have windows on the same pc?

regards,
carlos

---

### Post by Mark Phelps on 2010-01-15
Just passing along a few comments ...

Memory and disk space are entirely different -- sometimes difficult to grasp at first.  Your machine probable has something like 1GB (gigabyte) of system memory, while your hard drive has available disk space, not memory.  Furthermore, a hard drive is organized into chunks know as partitions, and the available disk space is measured within a particular partition.

I find it hard to believe that you need 75000MBytes of disk space for anything; it's probably more like 7500 -- which would be roughly 7.5GB of disk space -- which is not entirely unusual given that DVD creation programs often need more than the capacity of a DVD to store the files used to create the DVD.

But, there is also the possibility that you will need that much space on a DVD -- which presents a problem in that standard DVDs max out at 4.5GB.  So, if you really need 7.5GB of DVD, you will need to use a dual-layer DVD (which has 9GB capacity), and you will need a dual-layer DVD burner for that.

Finally, if you DID install using Wubi, you will have additional problems doing what you want because (1) the default Wubi install is really small (like 2.5GB), not leaving anywhere enough room for large files, (2) the Ubuntu space is really a special file contained INSIDE an MS Windows NTFS partition -- and can not easily be increased, (3) the remainder of that same partition that is in use by MS Windows limits how much you could grow the Ubuntu space.

---

### Post by jcslzr on 2010-01-16
Thanks for the info Mark

I will probably reinstall Ubuntu, I did it with Wubi because the Ubuntu disk did not recognise my partition or free space. But I have been hearing bad things about Wubi, and thought it was a problem related to it.

I will make a partition of 20 GB so I have plenty of room to burn a dvd. The file I am talking about its the standard 700 MB and my original partition its 11 GB.

Thanks again for the help.

---

