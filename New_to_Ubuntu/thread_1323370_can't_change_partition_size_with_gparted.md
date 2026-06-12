---
title: "can't change partition size with gparted"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by coasat on 2009-11-11
Hello. I'm trying to increase the size of my partition for Xubuntu and decrease for XP. I boot into a gparted live CD, re-size the partitions, press apply and then get this error:

Unnamed
An error occurred while applying the operations.
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm)

I defraged my windows partition and I have plenty of free space partitioned for windows.

I can't think where I'm going wrong. Any ideas?

Thanks,

coa

---

### Post by laidback on 2009-11-11
Have you tried doing the operations one at a time, i.e. decrease the Windows partition then increase the other one.

No idea why this should be better than what you did but it could be worth a try.

---

### Post by laidback on 2009-11-11
Might also be worth trying the Gparted that's on the Live cd if you have it, just in case there's a fault with you bootable version.

---

### Post by coasat on 2009-11-11
Laidback, I have tried changing the partition sizes one at time and got the same error. I'm not sure what you mean by using the Gparted on the live CD as opposed to using the bootable version.

thanks,
coa

---

### Post by laidback on 2009-11-11
I mean the Ubuntu Live CD rather than the individual bootable version of Gparted which you can get off the web. I assumed you were using the later, maybe my mistake.

---

### Post by wilee-nilee on 2009-11-11
You also have to turn off the swap in Linux to do some things with gparted. Once you turn off swap you can do much more such as moving whole partitions from side to side.

---

### Post by mkvnmtr on 2009-11-11
I may have trouble explaining this but I will try. I have had erros in Gparted when the partitions overlaped on a block. I have to make the partitions smaller a little at a time until I got them far enough apart to work, I try to do this a little at a time to keep from having unallocated space on the disk. Maybe someone with more knolage can explain this better.

---

### Post by wilee-nilee on 2009-11-11
> **mkvnmtr said:**
> I may have trouble explaining this but I will try. I have had erros in Gparted when the partitions overlaped on a block. I have to make the partitions smaller a little at a time until I got them far enough apart to work, I try to do this a little at a time to keep from having unallocated space on the disk. Maybe someone with more knolage can explain this better.

Take a screen shot of the gparted image and post it that may help others tp help you. There is also a command from the terminal that I don't remember that will tell all the partition sizes, somebody will post that.

Also the idea that partitions are overlapping; a direct read of that is that this is not possible. So you may want to wait for a little more advice if you think you need it so you don't waste your time or lose your setup. I hope you have everything backed up, whenever you mess with partitioning there is always the chance of losing stuff.

So the one sreen shot of gparted is covered by the root terminal window we want to see the actual gparted read.

---

### Post by laidback on 2009-11-12
I'v just noticed this bug report on the Gparted web site. It might be relevant:-

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

