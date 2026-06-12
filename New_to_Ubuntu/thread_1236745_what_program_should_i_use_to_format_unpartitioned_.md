---
title: "what program should i use to format unpartitioned space?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-08-10
hey everyone,

i need a program that will format the 200GB of unpartitioned space on my drive into NTFS file system. 

why? because for some weird reason, windows expects your drive to have already been formatted with their FS :confused:

will gparted work? i've heard of some programs but i didnt feel like wasting one of my few blank cd's on a program that won't do the job.

so i need a program that runs on a live cd.

any suggestions?

---

### Post by ibutho on 2009-08-10
Yes gparted should be able to create NTFS partitions. You can use the [Parted Magic]("http://www.partedmagic.com") live cd, because it comes with gparted and other useful partitioning tools.

---

### Post by halitech on 2009-08-10
if you already have the Ubuntu live cd, you can boot from that and use the partition editor to make the partition you need

---

### Post by mapes12 on 2009-08-10
I've heard that if you have Vista or Win 7 then you have to use the MS partitioner with those OS's otherwise everything falls apart. GParted is fine with XP and backwards.

How are you planning your Ubu installation cos that would help us comment further please?

---

### Post by lidex on 2009-08-10
asuastrophysics, 
What is it you intend to do - install Windows on a linux only drive? Much less hassle to install Windows first, then Ubuntu and allow grub to handle the boot options. Windows install disk can partition and format ntfs for it's own needs. The Ubuntu Live Disk can handle the rest.

---

### Post by Jerry N on 2009-08-10
[I]"I've heard that if you have Vista or Win 7 then you have to use the MS partitioner with those OS's otherwise everything falls apart. GParted is fine with XP and backwards."
[/I]

I don't know anything about Vista but I have done several Win 7 Beta and RC installs and I always use Parted Magic.  The last one was a triple boot experiment - Win XP, Win 7 RC, and Ubuntu 9.04.  I partitioned the disk into two NTFS partitions, one Ext3 partition, and one Linux swap partition before I installed anything.  Everything works just fine.

Jerry

---

### Post by LewRockwell on 2009-08-10
Parted Magic LiveCD

.

---

### Post by razorboy5 on 2009-08-10
i've used gparted to format unpartitioned to NTFS

---

### Post by Mark Phelps on 2009-08-12
> **mapes12 said:**
> I've heard that if you have Vista or Win 7 then you have to use the MS partitioner with those OS's otherwise everything falls apart.

This is only a problem if you're trying to resize, move, or otherwise tamper with the Vista OS volume. There's a problem with how Vista manages its OS volume that can confuse GParted at times.

GParted works fine with data NTFS partitions. I know, I use it all the time.

---

### Post by colau on 2009-08-12
> **asuastrophysics said:**
> hey everyone,

i need a program that will format the 200GB of unpartitioned space on my drive into NTFS file system. 

why? because for some weird reason, windows expects your drive to have already been formatted with their FS :confused:

will gparted work? i've heard of some programs but i didnt feel like wasting one of my few blank cd's on a program that won't do the job.

so i need a program that runs on a live cd.

any suggestions?

[http://partedmagic.com/](http://partedmagic.com/)

Or gparted

---

### Post by mapes12 on 2009-08-12
> GParted works fine with data NTFS partitions. I know, I use it all the time.Me too!! 

I only mentioned it cos I was chastised the other day by another poster who has Vista / Win7:confused: I have better things to do with my money than to buy yet more licenses for Vista / Win7 / Whatever. XP is as far as I'm going with MS. UBU is now on all my machines except one (cos of TomTom sat nav app). Even my 75 year old Dad is singing Ubu praises for the installation I recently setup for him :)

---

