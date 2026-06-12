---
title: "Need Help Reinstalling Vista on One Partition while Ubuntu runs on other Partition"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by viper3ez on 2009-09-10
i installed ubunto 9.04 on a partition on my hard drive. before tha, my windows vista magically deleted all my only user account so i could not get in but the vista OS is still on a partitio on my system. now i'm trying to do a clean install of vista on the vista partition, will the vista install give me the option to choose what partition i want to install or would it override everything including my ubuntu OS? can iinstall vista without hurting ubuntu?

thanks
Nuvie

---

### Post by bodhi.zazen on 2009-09-10
> **viper3ez said:**
> i installed ubunto 9.04 on a partition on my hard drive. before tha, my windows vista magically deleted all my only user account so i could not get in but the vista OS is still on a partitio on my system. now i'm trying to do a clean install of vista on the vista partition, will the vista install give me the option to choose what partition i want to install or would it override everything including my ubuntu OS? can iinstall vista without hurting ubuntu?

thanks
Nuvie

Yes you can install Vista, just take care NOT to install over the top of Ubuntu.

After you will need to restore GRUB to be able to boot ubuntu, which is fairly easy :

[Recovering Ubuntu after installing Windows - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by LewRockwell on 2009-09-10
SOME oem operating system recovery/reinstallation disks refuse to do anything else besides using the whole hard drive

if it says all data will be lost, overwritten, and/or destroyed...

then that is what it will do...

.

---

### Post by corncob on 2009-09-10
> **LewRockwell said:**
> SOME oem operating system recovery/reinstallation disks refuse to do anything else besides using the whole hard drive

if it says all data will be lost, overwritten, and/or destroyed...

then that is what it will do...

.

Yes, I tried to install XP on an external USB hard drive but it would not install unless I okayed it to repartition and format my internal drive along with the USB drive.  It just didn't want to see an "unallocated" or non-DOS partition anywhere on the computer.  I finally conceded, thinking I'd just reinstall Linux on the internal drive afterwards.  XP wiped out the Linux HD alright but never did install -- just went round and round in an endless loop of formatting one drive and then the other.  I finally reinstalled Ubuntu and put XP into VirtualBox and put the USB drive to use elsewhere.

---

