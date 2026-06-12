---
title: "Dual Partitioning"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by IMpeccable on 2011-06-16
Hello everyone!

I am a newbie to Linux and Ubuntu, mainly because I have not been able to figure out how to dual partition my hard disk and therefore have resigned myself to having to use just the Live CD. I have attempted to use both the GPartEd live CD and the GPartEd application on an Ubuntu Live CD which both did not allow me to make changes to the size of my partition (I want to keep Windows XP Professional). 

If anyone could help me, it would be a great favour!
Keep in mind though, I don't think I have admin/su/root access, but I could be wrong.

Thanks and cheers,

IMpeccable

---

### Post by TerribleLIar on 2011-06-16
You don't need to do anything yourself. The installation process will guide you along effortlessly. Just select install alongisde Windows and it'll ask you how much space to allocate to the Ubuntu partition. Although Gparted on LiveCD should allow you to change partitions around. Not sure why it wouldn't let you.

---

### Post by manzdagratiano on 2011-06-16
The GParted program should allow you to resize your drive - the windows partition probably needed to be unmounted before you tried that.

I would suggest going about it thus:

1>Boot up the Ubuntu Live CD and open GParted.
2>Right click the Windows partition and unmount it, if it is mounted, in which case the unmount option will not be greyed out. If it is mounted, the partition will have a key before it, meaning it is locked because it is mounted.
3>Then you can resize the partition. This will proceed without hassle.
4> DO NOT install Ubuntu yet.
5> Reboot the system with the LiveCD removed, and try to boot Windows. If all went WELL, booting will FAIL.
6> Get your Windows installation CD, and boot your machine with it. Choose Repair/Recovery. At the prompts, first type:
FIXMBR
and then type
FIXBOOT
which will fix Windows. You can now boot into Windows.
7> Now that the partition has been resized and Windows works, boot up using the Ubuntu LiveCD and install it, choosing "Install them side by side" or whatever works for you.

If you do not have a Windows XP CD, you can also fix your boot partition from an Ubuntu LiveCD:

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

A little more involved, but hey! It does the job!

I hope this helps you out.

**EDIT:** By the way this is the old-fashioned way - I am not aware if the new Ubuntu installer can resize the Windows partition and still manage to not corrupt the Windows bootloader (I haven't used Windows in three years). But this method will certainly work!

---

### Post by nzjethro on 2011-06-16
How about booting into Windows, defragmenting your Windows partition a couple of times (it'll take a while, maybe go make a sandwich while you wait), then go to open the start menu, right click your Computer icon, and select Manage (or something along those lines). Go to Disk management, and choose Shrink Volume, which will reduce the size of your Windows partition, and thus create another partition to install Ubuntu on. It'll come up with something like Querying Disk For Available Space, then select the sizes that you want (probably at least 20GB or so for Ubuntu). Then create the disk, label it if you want, chuck in the Ubuntu disk and reboot. In the install Ubuntu menu, choose Specify Partition Manually, then select the partition you created (choose / as a mount point, and format as ext4). It'll ask you if you want to produce a swap partition, but if you've got more than 2GB or so of RAM, no need.

These steps worked for me a few months ago, and it's nice you do most of the actual mucking around within Windows, which may make you feel a bit more comfortable. Only problem is that if your C: drive is too fragmented, you may not be able to shrink much. If this is the case, try one of the above ways.

[This]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") link may help, I found it a really useful way to get my Win 7, Ubuntu 10.10 dual boot set up, especially if you want to share files between tho two OSes.

---

### Post by IMpeccable on 2011-06-16
Thank you guys! I'll try to get it working, if not, then I'll just run wubi.

Cheers!

---

### Post by IMpeccable on 2011-06-16
BTW jethro, your version, sadly, does not work on XP

---

### Post by wildmanne39 on 2011-06-17
> **IMpeccable said:**
> BTW jethro, your version, sadly, does not work on XPHi,if you are installing 11.04 then after you select install you will have the option to install along side windows,choose that one and ubuntu will split the drive in half and it will create the partitions for you. I like to create my own because I do not like the way ubuntu creates them but it will work good doing it the easy way. The only time you will not have the option to install a long side windows is if windows is using dynamic partitioning. If you have more questions I will give you a guide.

---

### Post by IMpeccable on 2011-06-17
Wildmanne39,

Is that the same thing Wubi does?

---

### Post by wildmanne39 on 2011-06-17
> **IMpeccable said:**
> Wildmanne39,

Is that the same thing Wubi does?
Hi, no it is not here is a link that will explain the difference. 
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Window](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Window)
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Differences+between+Wubi+vs+dual-booting&as_qdr=all&sa=Google+Search&lang=en#911](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Differences+between+Wubi+vs+dual-booting&as_qdr=all&sa=Google+Search&lang=en#911)

---

