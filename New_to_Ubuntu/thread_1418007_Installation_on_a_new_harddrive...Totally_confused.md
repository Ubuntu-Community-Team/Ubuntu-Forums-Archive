---
title: "Installation on a new harddrive...Totally confused...Need some guidance"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by fromdebal on 2010-02-28
Experts,

I need your guidance here. I am totally confused here. I used to have 20 gb hd...I have been running xp on it for a long time.

Recently I bought a new hd of 320 gb. Today I installed Ubuntu on it (completely formatted during installation and then installed). It installed perfectly fine. Then after installation it asked me to reboot.

I rebooted...Now It is directly loading xp. Not giving me any option to load Ubuntu/XP.

Please help.

Thanks

---

### Post by chewearn on 2010-02-28
Boot into the livecd again, and run this command in a terminal:
```
sudo fdisk -l
```Copy/paste the resulting output.

Note:
The "l" in "-l" above is small alphabet "L".
The command lists the partitions of your system.

---

### Post by spectralblue on 2010-02-28
> **chewearn said:**
> Boot into the livecd again, and run this command in a terminal:
```
sudo fdisk -l
```Copy/paste the resulting output.

Note:
The "l" in "-l" above is small alphabet "L".
The command lists the partitions of your system.


In addition, what did you exactly do in detail? Did you remove the old harddrive and put the new harddrive in? Did you install Ubuntu, then XP? Do you still want the old harddrive in your machine or you throwing that out?

What exactly is your goal, having Ubuntu and Windows on the same 320 GB drive or Ubuntu on one drive and Windows on another?

---

### Post by fromdebal on 2010-02-28
I think I have solved the problem...From BIOS setup I changed the order of harddisk....

Previously, it was :
1) 20 GB hd (XP), 2) 320 GB (Ubuntu)

So, at first it was going to 20 GB xp harddisk and since the Grub is probably installed in the 320 GB one, it was directly going inside xp.

Now, I changed it to :
1) 320 GB (Ubuntu), 2) 20 GB (Xp)
Since Grub is installed in the 1st disk in this order, it is giving me option to choose between xp/Ubuntu.

Now, both of them are working fine (except Xp is not seeing this 320 GB hd).

Thanks for all your help.

Just one quick question : is there anyway from Xp I can see this HD?

Thanks

---

### Post by bpalone on 2010-02-28
I think this will get what you want.  I use it and haven't had any issues, yet any way.

[http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html")

Hope that helps.

---

### Post by sandyd on 2010-02-28
> **bpalone said:**
> I think this will get what you want.  I use it and haven't had any issues, yet any way.

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

Hope that helps.
if your using ubuntu 9.10, thats not gonna work due to the ext4 filesystem

---

### Post by spectralblue on 2010-03-04
It's a little hard to get Windows to recognize an ext partition (Ubuntu's), a lot of them are buggy right now. However, if what you want is Windows to have access to SOME of the space of that hard drive, then you can resize Ubuntu's partition, and have an NTFS or FAT32 partition in that 320 GB hard drive. Simply put, you're going to divide that hard drive, so one part of it is exclusively for Ubuntu, and the other part can be accessed by both Windows and Ubuntu.

Boot from a live CD and run Gparted (System>Administration>Gparted). Resize Ubuntu's partition, and create a new partition that has an NTFS or FAT32 file system. More details on resizing partitions with Gparted are at:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

