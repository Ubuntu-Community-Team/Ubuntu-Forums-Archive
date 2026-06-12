---
title: "reverting back to the old kernel version"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by launchy on 2010-07-30
how do i revert back to the old kernel version if i deleted it already? because i have a feeling that the latest kernel version messed up my monitor after upgrading it. thanks!

---

### Post by S.R on 2010-07-30
Found this thread here [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by clhsharky on 2010-07-31
launchy

Don't know if you can revert back if cache has been removed also, if not you can force version in package manager.

I would look here to see if your kernel version is listed.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Sharky

---

### Post by launchy on 2010-07-31
the thing is when i upgraded, i was playing this game and the monitor just goes black for no reason. after that i rebooted and it goes to login screen and the monitor turns black again. so i cant use synaptics

---

### Post by soldier1st on 2010-08-03
you can revert back if the new kernel is having problems if it shows more than 1 entry for say 24 and 23 and 24 is causing problems you will need to boot into 23 and you have 2 choices. either remove the newest kernel or when you boot you would need to select the previous kernel but if you only have the 1 kernel you might be able to install the older one.

---

### Post by rbw888 on 2011-02-23
vi /boot/grub/menu.lst
 
change "defalut 0" to "default x"  where x = the kernel you want.
 
when counting kernels down dont forget to include the recovery kernels

---

### Post by dlee2654 on 2012-09-04
where do I identify the number for the kernel that I want? do I just change this to 1?  I dont see anything that shows what number it should be...
thanks

---

### Post by YannBuntu on 2012-09-05
Please indicate your Boot-Info URL
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Elfy on 2012-09-05
Old thread closed.

---

