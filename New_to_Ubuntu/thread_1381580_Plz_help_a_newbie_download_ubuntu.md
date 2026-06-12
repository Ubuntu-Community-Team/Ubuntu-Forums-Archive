---
title: "Plz help a newbie download ubuntu"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by vvfrn on 2010-01-14
I already messed up 2 computers trying to dual boot. I know how to download it by itself .I am trying to dual boot on a 40gb hard drive with win xp. I just mostly need help partitioning on ibm thinkpad r50.:KS

---

### Post by Sef on 2010-01-15
1) What version are you trying to dual boot with?

2) Have you checked out the[ Illustrated dual boot]("http://members.iinet.net/%7Eherman546/index.html")?

---

### Post by egalvan on 2010-01-15
To add to sef's questions...

How much free space is on that 40GB drive?

Do you have at least 10GB to give to Ubuntu?

OK, just realized it's a R50... 
how much RAM do it have?

---

### Post by Sef on 2010-01-15
Another question:  Have you checked the disk for errors?  Instead of installing, go down to "Check Disk for Errors."

---

### Post by vvfrn on 2010-01-15
sp3 xp with 9.10 ubuntu
I have like 17gb free
I want to give 11gbs to ubuntu
the disk does not have errors
I have 1gb of ram
^Bump^

---

### Post by audiomick on 2010-01-15
The first thing to do is defragment your windows partition, maybe even twice. Then boot into the live CD using the option "try ubuntu without changing the computer".
got to
system> administration> gparted

use that to shrink the windows partition as much as you want to.

boot into windows and make sure it is happy. Let it do any file checks  or whatever that it might want to do.

boot into the ubuntu installer and install into the empty space.

---

### Post by JimInLakeland on 2010-01-15
Did you burn a CD from the Ubuntu ISO? You will need to boot to the CD to be able to install Ubuntu on your system for a dual boot configuration.

---

### Post by CCBalla10 on 2010-01-16
A great tool for beginners is Wubi. Makes an automatic dual boot.  Do a YouTube search for Wubi to see if it will accomplish what you need. I recommend this because it is so easy to remove and recover the disk space for Windows.

Cheers!
Austin

---

### Post by Paqman on 2010-01-16
> **CCBalla10 said:**
> A great tool for beginners is Wubi.

+1

If you're struggling with partitioning then Wubi is for you. It'll get Ubuntu installed without any need to do any partitioning.

---

### Post by kenuf on 2010-01-16
> **audiomick said:**
> The first thing to do is defragment your windows partition, maybe even twice. Then boot into the live CD using the option "try ubuntu without changing the computer".
got to
system> administration> gparted

use that to shrink the windows partition as much as you want to.

boot into windows and make sure it is happy. Let it do any file checks  or whatever that it might want to do.

boot into the ubuntu installer and install into the empty space.

YES defrag **_twice_**.
and in the partitioner to shrink the Windows partition, right-click on the partition and the option is "Resize/Move"

---

