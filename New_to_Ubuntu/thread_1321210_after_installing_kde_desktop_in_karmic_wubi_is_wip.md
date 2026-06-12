---
title: "after installing kde desktop in karmic wubi is wiped away and can't reboot karmic"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by headmower on 2009-11-09
Hello, I have Vista and Ubuntu and windows 7 triple booted. Ubuntu is installed inside Vista with wubi. I recently upgraded from 9.04 to 9.10. Everything was ok untill I installed kde desktop


. When I went to restart my pc there was no grub for ubuntu. My 2 windows op's booted fine. Tried using super grub and ended up doing clean reinstall for ubuntu 9.10. Why is grub being wiped away after kde installed???:mrgreen::confused::???:         

THANKS    IN ADVANCE  for advice or correction or whatever as I would like to try kde on karmic.

Actually the problem starts after using the upgrade manager'
                                             
                      GNU GRUB version 1.97~beta4
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possilbe device/dile completions.
sh: grub>    

The above is what shows up when rebooting karmic. I have no clue except to make a clean reinstall of karmic.  Thanks for any help.  9.04(Jaunty) worked better.

---

### Post by garvinrick4 on 2009-11-09
Wubi uses Windows dos4grub to boot with it does not use Ubuntu's.
KDE is a GUI or Kubuntu. Do not know any reason or why a different
Graphic user interface would mess with dos4grub. You should have
had a Kubuntu log in screen if you installed KDE after Ubuntu installation. And a choice to log into ubuntu or kubuntu. In boot-up
7,Vista and ubuntu. Kubuntu would not be a boot choice. A selection
after your Ubuntu boot. 
 WUBI is a folder inside of your Vista install right next to Users.
Will even be in your add and remove programs in Vista. 

When you install KDE you can see all the different and many they are files that are installed. Do not believe grub is affected. Next
time you install KDE check what it is going to install.

---

### Post by headmower on 2009-11-15
I have tried to install karmic 5 to 6 times and it works fine with wubi as a dualboot, until I try to upgrade software packages or add the kde desktop. When I go to reboot after these changes, wubi is all messed up. I never had this problem with ubuntu 9.04 and the kde desktop feature. I currently have dual boot with wubi &-the linux-mint7Gloria package and all seem fine. I may go back to karmic after some bugs are worked out.
LINUX rules.):PBut windows 7 is the best microsoft system yet.  Make linux eaiser to draw more people from microsoft.:D:guitar:

---

