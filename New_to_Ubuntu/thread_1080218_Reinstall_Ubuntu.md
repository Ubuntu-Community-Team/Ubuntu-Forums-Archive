---
title: "Reinstall Ubuntu"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by gkraju on 2009-02-25
hi i have installed ubuntu 8.04 inside xp in the same drive(C:)
i allocated only 5GB but it is not enough now 
so i want to reinstall in some other drive 
i have installed many softwares in ubuntu i dont want to start from scratch is their any way i can have the same settings and installed software
thanks in advance

---

### Post by MrWES on 2009-02-25
> **gkraju said:**
> hi i have installed ubuntu 8.04 inside xp in the same drive(C:)
i allocated only 5GB but it is not enough now 
so i want to reinstall in some other drive 
i have installed many softwares in ubuntu i dont want to start from scratch is their any way i can have the same settings and installed software
thanks in advance

Check out this thread; you can get a list of installed packages and save it and then use it after your reinstallation to install the packages you had originally installed. Remember to save the file onto a flash drive; otherwise you might loose it during the reinstall.

[http://ubuntuforums.org/showthread.php?t=261366]("http://ubuntuforums.org/showthread.php?t=261366")

Bill

---

### Post by gkraju on 2009-02-25
> **MrWES said:**
> Check out this thread; you can get a list of installed packages and save it and then use it after your reinstallation to install the packages you had originally installed. Remember to save the file onto a flash drive; otherwise you might loose it during the reinstall.

[http://ubuntuforums.org/showthread.php?t=261366]("http://ubuntuforums.org/showthread.php?t=261366")

Bill
thanks for your reply but
that thing will again download the softwares from net and install it 
but i want to copy the old installation is their any way

---

### Post by caljohnsmith on 2009-02-25
If you boot your Live CD, run gparted (System > Admin > Partition Editor), you can use gparted to simply copy/paste your Ubuntu partition to the new drive. Once you've done that, you can enlarge the partition with gparted so it has more room. It would be good to also copy over the swap partition to the new drive, rather than create it, so that it retains its same UUID; if you don't do that, you will have to reassign the swap UUID of the old partition to whichever new swap partition you create. After you are done, you will also need to reinstall Grub to the MBR of that drive so you can boot Ubuntu from that drive. But first try copying your partitions over and resizing the Ubuntu drive as desired, and then post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by gkraju on 2009-02-25
> **caljohnsmith said:**
> If you boot your Live CD, run gparted (System > Admin > Partition Editor), you can use gparted to simply copy/paste your Ubuntu partition to the new drive. Once you've done that, you can enlarge the partition with gparted so it has more room. It would be good to also copy over the swap partition to the new drive, rather than create it, so that it retains its same UUID; if you don't do that, you will have to reassign the swap UUID of the old partition to whichever new swap partition you create. After you are done, you will also need to reinstall Grub to the MBR of that drive so you can boot Ubuntu from that drive. But first try copying your partitions over and resizing the Ubuntu drive as desired, and then post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

i tried to do that yesterday 
but i couldnt it should show ubuntu partition seperately it only showed host (I installed ubuntu 8.04 inside Xp)
i am new to linux can you tell me briefly what to do in gparted

---

### Post by handy on 2009-02-25
I'd just boot with the Ubuntu LiveCD & use it to resize the partitions, it does the job brilliantly.

If you have a more complicated job than that, then please forgive my intrusion into your thought processes?

---

### Post by caljohnsmith on 2009-02-25
Since you installed Ubuntu inside Windows (a Wubi install) and did not install Ubuntu to its own dedicated partition, to transfer your Ubuntu Wubi install to its own partition you can use LVPM:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Let me know how that goes.

---

