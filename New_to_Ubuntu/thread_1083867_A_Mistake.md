---
title: "A Mistake"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by mkjp on 2009-03-01
Hello,
I have a laptop that runs windows that has a broken hard drive. Instead of me springing to buy a new hard drive, I got the bright idea to install linux on a thumb drive. The only problem was when I went to install the thumb drive using the laptop it took too long to read the partitions. So I thought i would install linux Ubuntu on my thumb drive using my Windows Vista Desktop. Bad Idea!!! After the installation was done I went to boot my computer back up into Windows and it came up with a GRUB load error. I desperately need a windows operating system and I def. don't want Linux Ubuntu anymore on my desktop.

---

### Post by ptn107 on 2009-03-01
[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/254009228831](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/254009228831)

---

### Post by mkjp on 2009-03-01
This doesn't really apply to me, I was dumb and didn't dual partition my Vista and the linux System. I was just trying to install linux on my thumb drive so I could load it on the laptop each time without using a CD. Instead of that happening I didnt something to my computer. I dont even have the option to boot into windows, it goes straight into the GRUB Error. I am done with linux after this.

---

### Post by ptn107 on 2009-03-01
You can still restore the MBR with that tutorial.  The problem is that when you install to a flash drive it automatically chooses to install the bootloader onto a local disk, regardless of what is on it.  It will show you how to remove GRUB and restore Vista's bootloader.  It doesn't matter that your not dual booting.

---

### Post by bapoumba on 2009-03-01
Have you installed ubuntu on your computer hard drive? Did you format it?

---

### Post by mkjp on 2009-03-01
No I have not installed it on my hard drive. I installed asked it in the installation partition editor part, to do a guided partition and selected the thumb drive, or at least I thought.

---

### Post by mkjp on 2009-03-01
REPLYING TO ptn107:
Okay, but i don't have the VISTA disk, it never came with my computer, is there some way to download it

---

### Post by taurus on 2009-03-01
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by bapoumba on 2009-03-01
> **mkjp said:**
> REPLYING TO ptn107:
Okay, but i don't have the VISTA disk, it never came with my computer, is there some way to download it
We will not answer this question here.

---

### Post by ptn107 on 2009-03-01
> **mkjp said:**
> REPLYING TO ptn107:
Okay, but i don't have the VISTA disk, it never came with my computer, is there some way to download it

I can't tell you how to obtain a Vista DVD, but I can tell you that it may not be necessary.  There is a program called EasyBCD that will help you:
_[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)_

It actually will let you download part of Vista that contains ONLY the 'Repair your computer' section of the DVD.  Just follow the steps.

---

### Post by mkjp on 2009-03-01
Okay, new development I dont know if this ruins any chances I got. My dad was laying around with my computer and deleted the partition named RECOVERY. does this mean that There is no way to actually bring VISTA back?

---

### Post by perlluver on 2009-03-01
> **mkjp said:**
> Okay, new development I dont know if this ruins any chances I got. My dad was laying around with my computer and deleted the partition named RECOVERY. does this mean that There is no way to actually bring VISTA back?

Unless you can get a Vista CD legitimately or call Microsoft and ask them if there is a way you can get Vista, yeah that basically means that the drive holding Vista is gone.

---

### Post by mkjp on 2009-03-01
Dang,
Okay I just put in a XP disc to try and install that, but the computer didnt boot from that, instead it went straight to the GRUB error screen. What can I do easy or hard to fix this problem.

---

### Post by chamber on 2009-03-01
Make sure that the settings are changed in the BIOS to boot from the CD first.

---

### Post by perlluver on 2009-03-01
First make sure your bios is set to boot from a CD.  It will either be F1 F2 or delete to get into the bios.  Most new computer will allow you to press F9 or F12 to select the boot device.  Just make sure you are booting from the CD.

---

### Post by mkjp on 2009-03-01
I tried that already, but it did the same thing. Would it work if i just installed Linux totally on my computer and then tried to run the Windows Setup, or would that be bad news bears?

---

### Post by perlluver on 2009-03-01
You could install Linux on it, but if the Windows XP CD won't boot when the computer is first starting that means that it won't boot off the CD.  Is this CD burned?  If so it is most likely a bad burn, and it won't boot off of it.  In any case I would make sure that it is set to boot off of the CD, and make sure that the Windows CD is working correctly.

---

### Post by mkjp on 2009-03-02
Okay, So I got the XP cd and put it in, it went through the beginning part of its setup. The part at the partitioning menu though was where I am having trouble. I now dont see my harddrive as a entity to be partitioned. Could this be because Vista is on it? How can I make it available to partition.

---

### Post by mkjp on 2009-03-02
Okay, So I got the XP cd and put it in, it went through the beginning part of its setup. The part at the partitioning menu though was where I am having trouble. I now dont see my harddrive as a entity to be partitioned. Could this be because Vista is on it? How can I make it available to partition.

I tried to install the Ubuntu Operating system on my jump drive, and the install must have put the GRUB thing on my computer. I need to get my vista back it won't let me. Help Please

---

### Post by overdrank on 2009-03-02
Please do not make multiple threads on the same issue. Threads merged. :)

---

