---
title: "Partitions"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by fl_tom on 2010-07-12
I have xp and ms 7 installed on 2 seperate drives. I plan on installing another internal 500gig hard drive for ubuntu 9.1 since I can't get the latest version to run on Live CD (hangs up) I want to manually partition the drive for all the various partitions, / , usr , home , and so on.
I also do not want to have any ubuntu files installed on my other drives only on the new one and plan to boot ubuntu from that drive using bios. Any helpfull tips would be appreciated.
 
Thanks,
fl_tom     :)

---

### Post by audiomick on 2010-07-12
Hallo.

All you have to do is point the installer at the right drive, really.

If you want to set up partitions before you start,
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

You really only need
one for the system of around 10 - 15 GB
one for swap, a bit bigger than your RAM if you want suspend to work, otherwise about 1GB

and it is useful to have your /home on its own partition so you can remount it if you have to re-install.

If you want to determine the boot order via BIOS, then you should install Grub to the same drive that Ubuntu is on, as far as I know. I think there is an option for that towards the end of the installation, but I am not an expert on that matter.

---

