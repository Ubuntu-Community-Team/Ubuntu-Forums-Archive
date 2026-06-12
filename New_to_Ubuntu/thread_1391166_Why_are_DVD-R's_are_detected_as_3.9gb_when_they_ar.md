---
title: "Why are DVD-R's are detected as 3.9gb when they are 4.7gb"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Boslow on 2010-01-26
Hi There
Iv been using Ubuntu for nearly a year now and im still a n00b.

Im having problems where my computer detects DVD-Rs as 3.9gb discs, which they are not, they're 4.7gb. Sometimes they will come up as 4.7gb or 4.3gb or some other random number. Whats going on here?

Most of the time im not bothered as most of the isos im burning are less than 3.9gb.

However as always, its the important things that dont work properly. How/where/are there settings to force the drive to read them as 4.7gb, as sometimes they will detect that?

The overburn system wont work as it just spits the disc back out.

 Im using Datawrite Red 4.7gb 8x discs.
The drive is a TSSTcorp CDDVDW SH-S223B


Many Thanks

---

### Post by blazemore on 2010-01-27
From [another forum]("http://club.myce.com/f33/actual-size-dvd-r-4-7gb-139256/#post2126288")...
>        This "mystery" is part of an old  marketing game in the disk and media business.
 
In order to make their products seem as large as possible, disk drive  and media manufacturers have traditionally stated their GB using the  measure of "1 Billion Bytes."  But when you actually try to use the  space on the disk or media, your computer will be addressing the space  in binary, not decimal addresses.
 
Two to the 30th power is 1,073,741,824 ... not 1,000,000,000 ... so the  disk or media will seem about 7% smaller than what you thought you  bought.  It's sort of a reverse baker's dozen.  So a 4.7 GB disk only  has 4.3772 GB of total file capacity.
 
This gets even trickier when the disk or media uses a file system with  sectors, like NTFS.  The sector size and file system structure adds a  bit of overhead and guarantees some wasted bytes -- sometimes another  10% of the stated capacity.  This effect is minimal on DVDs, as they are  optimized for a few very large files that are expected to stream.
 

---

