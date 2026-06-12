---
title: "Disk Space Usage"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Scy7he on 2009-10-10
Hiya everyone,

I'm about a week in to my first experiences with Linux and so far so good:)

Problem though: Is disk space usage in Linux/Ubuntu seperated and calculated differently from windows? I have a 250Gig hard drive... but I'm only listed as having 220Gig available!

When I used sudo fdisk -l to try to solve the problem I came up with the following:

> ed@ed-laptop:~$ sudo fdisk -l
[sudo] password for ed: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39602ed2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29286   235239763+  83  Linux
/dev/sda2           29287       30401     8956237+   5  Extended
/dev/sda5           29287       30401     8956206   82  Linux swap / Solaris
ed@ed-laptop:~$ 
So I clearly do have 250 gig to start with, some is taken by sda2&5, but then why is Ubuntu still only listing 220gig unless the memory is calculated differently. Surely it should be showing 235gig for sda1 in disk usage analyser?

Question1: What are sda2 and sda5?
Question2: Where is my missing 15gig?

Any and all help would be greatly appreciated:)

---

### Post by Rocket2DMn on 2009-10-10
According to disk manufactueres, a GB is measured as 1000MB, and a MB is 1000 KB, and a KB is 1000 bytes.  In reality all these numbers are 1024 (2^10).  1GB = 2^30 bytes.  That differences, plus the overhead of the filesystem in place is the difference you are seeing.

---

### Post by Scy7he on 2009-10-10
Embarrassingly obvious... damn:)

Cheers Rocket2DMn

---

