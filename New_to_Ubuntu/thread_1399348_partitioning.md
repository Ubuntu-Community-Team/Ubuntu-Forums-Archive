---
title: "partitioning?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Brandon_oma#692 on 2010-02-05
where should i ask about partitioning?

---

### Post by jrandolph on 2010-02-05
that all depends on what you are trying to get accomplished 
need to supply more information as to what you want

---

### Post by nhasian on 2010-02-05
partitioning is a personal preference, theres lots of different ways to do it.  the most popular way seems to be:

Root Parition (10-15 gigs)
Home Partition (majority of your hard disk)
Swap partition (1 or 1.5x the amount of ram in your system)

---

### Post by Brandon_oma#692 on 2010-02-05
I installed ubuntu on a machine that already has windows. c is much larger than d. windows on c ubuntu on d. Iplan to copy files from c to d get a little more comfortanle on ubuntu then remove windows. I would like to make them more 50/50. I am am unsure if these drives are even one partitioned or two seperate drives.

---

### Post by Sir Jasper on 2010-02-05
Hi,

I really like ´buntu; however Windows is the favoured the OS in business, so I would suggest you retain it (even if you rarely use it).

My regards

As regards your other thread; which version of Excel do they use at Work?

---

### Post by nhasian on 2010-02-05
That's easy enough.  just enter in a terminal:

```
sudo fdisk -l
```

you could also view the data with System->Administration->Gparted (Partition Editor)

if you need to install it you can do so with:

```
sudo apt-get install gparted
``` 

> **Brandon_oma#692 said:**
> I am am unsure if these drives are even one partitioned or two seperate drives.

---

### Post by lidex on 2010-02-05
> **Brandon_oma#692 said:**
> I installed ubuntu on a machine that already has windows. c is much larger than d. windows on c ubuntu on d. Iplan to copy files from c to d get a little more comfortanle on ubuntu then remove windows. I would like to make them more 50/50. I am am unsure if these drives are even one partitioned or two seperate drives.

If it is only one HDD that requires resizing your windows partition, something not for the uninitiated. Have a look here:
[http://ubuntuguide.org/wiki/Multiple_OS_Installation]("http://ubuntuguide.org/wiki/Multiple_OS_Installation")

---

