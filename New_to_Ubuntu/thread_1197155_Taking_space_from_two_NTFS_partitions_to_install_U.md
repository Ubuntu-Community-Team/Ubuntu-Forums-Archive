---
title: "Taking space from two NTFS partitions to install Ubuntu"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by kickwin on 2009-06-25
I recently installed Ubuntu on my office computer and I have been very satisfied with it. Now I would like to install it on to my Dell Laptop with the following configuration, which already has Windows XP and two partitions (NTFS) each about 18GB.

Intel® Celeron® M Processor 380
1.60GHz/1MB Cache/400MHz FSB
40GB 5400rpm Hard Drive
512 MB RAM

I would like to allot 15 GB of my hard disk to Ubuntu. 3 GB taken from C drive, which has Windows installed and 12 GB from D drive. I believe this is possible using GParted tool but I do not know how to do it. When I installed Ubuntu on my office computer, I just took all the space that is needed from C drive and used the regular option instead of custom install in GParted. 

Also I would like to know if Ubuntu 9.04 would be suitable or it would be heavy for my [COLOR=#000000][FONT=Verdana,Arial,Tahoma] laptop.[/FONT][/COLOR] Thanks and I appreciate you help.

---

### Post by LewRockwell on 2009-06-25
sounds like you've got everything planned out pretty much already

get your partitions how you want them(don't forget a swap partition) and then if you don't like ubuntu on the machine you can always go to xubuntu

notes:

as always, back-up any data you can't afford to lose

defrag your windows at least twice while running in safe mode BEFORE you resize the partition it is on

(typically pressing F8 about twice per second during initial start-up will give you the menu to boot into safe mode)

let us know how it turns out

---

### Post by nhasian on 2009-06-25
Ubuntu should run fine on your laptop.  test it out by running the liveCD first.  you can use gparted from th liveCD from System->Administration->Parition Editor (or it may be called gparted)

> **kickwin said:**
> 
I would like to allot 15 GB of my hard disk to Ubuntu. 3 GB taken from C drive, which has Windows installed and 12 GB from D drive. I believe this is possible using GParted tool but I do not know how to do it. When I installed Ubuntu on my office computer, I just took all the space that is needed from C drive and used the regular option instead of custom install in GParted. 


---

