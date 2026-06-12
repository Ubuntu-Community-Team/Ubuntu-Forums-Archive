---
title: "partition problem"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by vnpifhf on 2011-02-11
Hello, I want to install a dual boot on my computer along with win 7 and ubuntu 10.10 but when I insert the CD and it asks me for install, so I go into the partition list and its really complicated unlike earlier versions of ubuntu, it won't let me add partitions without formatting everything and there is no option to partition anything on the hard drive and says 320gb but can't detect how much is used or anything,

Help!

---

### Post by jerrrys on 2011-02-11
yes, i understand things changed in 10.10.   10o4 is still the same

---

### Post by vnpifhf on 2011-02-11
[IMG]http://i52.tinypic.com/2nao8eb.png[/IMG]
Any instructions/help on what to do to make a 100gb ubuntu partition?

---

### Post by robgraves on 2011-02-11
i just set up a dual boot on my laptop a couple weeks ago with windows 7 and ubuntu 10.10. 
             i followed this guide:
[http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by vnpifhf on 2011-02-11
but the problem is that it does not recognise the used aspect of the drive so in turn I cannot add the partition, this isn't on older versions on ubuntu so why is it being like this!

---

### Post by srs5694 on 2011-02-11
Just a hunch, but: If an NTFS partition is not cleanly unmounted, Linux won't normally touch it. It could be this is what's happening -- if /dev/sda3 wasn't cleanly unmounted, the drivers are refusing to do anything with it, so you're having this problem. If I'm right, the solution is to boot into Windows, run CHKDSK on the partition, and then shut down or reboot cleanly (by using the appropriate shutdown or reboot menu option, not by just hitting the power switch).

---

### Post by vnpifhf on 2011-02-12
I've run CHKDSK in command prompt, it shut down, then booted into ubuntu cd and it says dev line 7 can't be found, don't know what that means, and then the hard drive space is still unknown so can't allocate space for partition and can't do it in windows 7 as well,

Thank you!

---

### Post by vnpifhf on 2011-02-12
bump

---

### Post by aaryansh on 2011-02-12
From the image you provided,
I can tell that you have a 320GB HDD having 3 NTFS partitions.
The 3 partitions take up all the space in your drive,
so before you can make a new 100GB partition for ubuntu [ext type], you have to delete a partition to create some unallocated space in your drive.
or use an existing partition by clicking "change".

I recommend you use [GParted]("http://gparted.sourceforge.net/livecd.php") to resize your partition to create some space.

My First post here,
Hope it is helpful.

---

### Post by vnpifhf on 2011-02-12
yes but the used space is unknown so I can't split the partition.

---

### Post by Sidewinder1 on 2011-02-12
I am not speaking from experience, but, from what I've read starting with Vista and including "7", you should be using the partition mgr. that comes with those OSs. I think that you need to defrag, probably twice, and then use the Microsoft partitioning tool to shrink one of the NTFS partitions to allow room for the reformatting (ext3 or 4) of the remaining space. Make certain that you've backed up any critical data, etc.
HTH,
Side

---

### Post by aaryansh on 2011-02-12
you'll be able to do it in GParted.
[Download]("http://gparted.sourceforge.net/livecd.php")
[Read This]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

---

