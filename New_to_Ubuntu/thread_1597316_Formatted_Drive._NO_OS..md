---
title: "Formatted Drive. NO OS."
date: 2010-10-15
forum: New to Ubuntu
---

### Post by CowCrop on 2010-10-15
I decided to get Ubuntu one day so i installed it using the cd and .iso. I formally was on Windows XP SP3 32bit and I successfully dual-booted Ubuntu & XP (XP installed first) but, then my partition was all messed up. So I accidently formated my whole drive :(. I lost a few important items....
So when i turned on my computer, the screen showed the startup, but then just a black screen. No booting of Ubuntu or XP. So I put in the CD for Ubuntu (that I used to dualboot) and rebooted the computer. I successfully managed to get 10.10 Ubuntu into my system. However, I want to make a clean install of XP using my Windows Install CD. Is this possible? 
And if so, can I have some instructions?

Thanks for anything who replies, you really saved me a burden :)!

---

### Post by nothingspecial on 2010-10-15
Hi, it`s usually recommended to install windows first, however it`s perfectly possible the other way around. Here are the instructions....

[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

### Post by coffeecat on 2010-10-15
> **CowCrop said:**
> I successfully managed to get 10.10 Ubuntu into my system. However, I want to make a clean install of XP using my Windows Install CD. Is this possible? 

Yes. :)

If you mean that you installed Ubuntu 10.10 to the whole of the hard drive you could use Gparted on the live CD to shrink the Ubuntu partition and create an NTFS partition for XP, and then install XP to the NTFS partition.

**But.....**

Shrinking the Ubuntu partition could take a l-o-n-g time and you'd have to repair grub after the Windows installer overwrites the mbr. If you are prepared to reinstall Ubuntu, this is the way I would go:

Boot up with the live CD and use System > Administration > Gparted to reformat the whole drive. You need to right-click on the swap partition and choose 'swapoff' and then delete all the partitions. Now create just one NTFS partition for Windows as big or as small as you need. Leave the rest of the drive unallocated.

Now boot up with the Windows CD and install it to the NTFS partition you have made. Make sure Windows is working happily and then reboot the Ubuntu live CD. You can do one of two things:

1 Open Gparted, create the Linux partitions you need and then use the Manual option at the partitioning stage of the installer.

2 Simpler: start the installer and choose 'use continuous free space' (or words to that effect) at the partitioning stage.

---

### Post by mastablasta on 2010-10-15
have you ever heard about google - the internet search engine?
 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by CowCrop on 2010-10-15
wow, thanks for the quick replies. hope it works:) thanks.

---

