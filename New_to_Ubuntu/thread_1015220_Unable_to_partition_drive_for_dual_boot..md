---
title: "Unable to partition drive for dual boot."
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Schwartz421 on 2008-12-18
I am attempting to install ubuntu 8.10 on my gateway M-series.  I want partition my hardrive to allow both ubuntu and windows vista OS.  However, the installer will not give me the option to manual partition. Please help!!!

Thanks,
James

---

### Post by Duck2006 on 2008-12-18
Use the partitioning tool with in vista to partition the drive for ubuntu.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by jimmy the saint on 2008-12-18
shrink the main partition from wihin vista first.  This will create a large area of freespace on the disk.  Then just tell the installer to use that free space.  It should be the default option.

---

### Post by xjcannonx on 2008-12-18
Defrag before you do any partitioning

---

### Post by x0prah_Winfr3yx on 2008-12-18
sometimes Vista won't allow you to shrink the volume on your partition, so make sure to defrag thoroughly and try again. 

i personally had to download a couple different defragers in order to be able to shrink my volume considerably.

---

### Post by Captain_tux on 2008-12-18
Check out my post with a similar issue... I had to run a few different tools in order to partition the disk on my desktop.

[http://ubuntuforums.org/showthread.php?t=996303](http://ubuntuforums.org/showthread.php?t=996303)

Buena suerte!

---

### Post by Duck2006 on 2008-12-18
> **Captain_tux said:**
> Check out my post with a similar issue... I had to run a few different tools in order to partition the disk on my desktop.

[http://ubuntuforums.org/showthread.php?t=996303](http://ubuntuforums.org/showthread.php?t=996303)

Buena suerte!

Your running win xp he is running win vista. There is a different way to partitions the win drive.
ie you can partition the drive with gparted for xp as vista needs to be partitioned from with in vista to get the space to linux.

---

### Post by Schwartz421 on 2008-12-18
thanks fall all the help, I shrank the main partition, it wasn't big enough ro ubuntu. So I am currently defragging.  Why can't I just do it w/ the installer?

---

### Post by Duck2006 on 2008-12-18
> **Schwartz421 said:**
> thanks fall all the help, I shrank the main partition, it wasn't big enough ro ubuntu. So I am currently defragging.  Why can't I just do it w/ the installer?

Not sure it got some thing to do with the way vista it set up.

---

### Post by blampars on 2008-12-18
I put 8.04 on my girlfriends Sony Vaio that was preloaded with vista, using the 8.04 installer.  I had no problems and did not have to shrink partitions or anything of the sort through Vista.  It all went perfectly fine and I pretty much just walked away and came back to a nice new ubuntu install.. It seems strange to me that using Vista would have to be the process for him to get Ubuntu up and running.

I talked to James on the phone earlier and the best he could get his partition to shrink is 3% using whatever methods are available in Vista. Yet he's got a 120gb hard drive with only 54gb in use.

Is there something "weird" going on with gateway setups that we (James and I) might not know about?

---

